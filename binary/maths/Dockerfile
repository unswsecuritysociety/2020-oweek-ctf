# Basic Xinetd Docker Container
FROM ubuntu:18.04

# Apt-get update
RUN apt-get update && \
    apt-get install -y xinetd python3 && \
    rm -rf /var/lib/apt/lists/*

# Create CTF user
RUN mkdir /home/ctf && \
    chmod 755 /home/ctf && \
    useradd -M -U -d /home/ctf ctf && \
    chown root:root /home/ctf
COPY xinetd.conf /etc/

# Copy binary
COPY ./maths /home/ctf/

# Make the binary
RUN chmod 755 /home/ctf/maths

# Expose container
EXPOSE 9999

# Run script when the container launches
CMD ["script", "-t", "/dev/null", "-c", "xinetd -d -dontfork"]
