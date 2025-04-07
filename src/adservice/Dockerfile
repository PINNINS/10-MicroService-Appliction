# Copyright 2020 Google LLC
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

# Stage 1: Builder image
FROM eclipse-temurin:19@sha256:f3fbf1ad599d4b5dbdd7ceb55708d10cb9fafb08e094ef91e92aa63b520a232e as builder

WORKDIR /app

# Copy Gradle files and install dependencies
COPY ["build.gradle", "gradlew", "./"]
COPY gradle gradle
RUN chmod +x gradlew && ./gradlew --no-daemon downloadRepos

# Copy the rest of the application code and build it
COPY . .
RUN chmod +x gradlew && ./gradlew installDist

# Stage 2: Runtime image
FROM eclipse-temurin:19.0.1_10-jre-alpine@sha256:fabe27bd9db502d484a11d3f571c2f4ef7bba4a172527084d939935358fb06c4

# Install required dependencies
RUN apk add --no-cache ca-certificates

# Download and extract Stackdriver Profiler Java agent
RUN mkdir -p /opt/cprof && \
    wget -q -O- https://storage.googleapis.com/cloud-profiler/java/latest/profiler_java_agent_alpine.tar.gz \
    | tar xzv -C /opt/cprof && \
    rm -rf profiler_java_agent.tar.gz

WORKDIR /app

# Copy the built artifacts from the builder stage
COPY --from=builder /app .

# Expose the application port
EXPOSE 9555

# Set the entry point for the application
ENTRYPOINT ["/app/build/install/hipstershop/bin/AdService"]

