# ncdu from Debian's official repository, running as a non-root user.
# See README.md, "Worked example: ncdu from start to finish".
#
#   docker build -t ncdu-slim .
#   docker run --rm -it --network none --cap-drop ALL \
#     --security-opt no-new-privileges --memory 512m --pids-limit 64 \
#     -v ~/sandbox/ncdu/input:/input:ro,Z ncdu-slim
FROM debian:trixie-slim
RUN apt-get update \
 && apt-get install -y --no-install-recommends ncdu \
 && rm -rf /var/lib/apt/lists/*
RUN useradd --create-home appuser
USER appuser
ENTRYPOINT ["ncdu"]
CMD ["-r", "/input"]
