# Basic Xinetd Docker Container
FROM ubuntu:18.04

# Apt-get update
RUN apt-get update && \
    apt-get install -y xinetd && \
    rm -rf /var/lib/apt/lists/*

# Create CTF user
RUN mkdir /home/ctf && \
    chmod 755 /home/ctf && \
    useradd -M -U -d /home/ctf ctf && \
    chown ctf:ctf /home/ctf
COPY xinetd.conf /etc/

# Copy binary
COPY ./buf /home/ctf/

# Make the binary
RUN chmod 755 /home/ctf/buf && \
    chown -R ctf: /home/ctf

# Expose container
EXPOSE 9999

# Run script when the container launches
CMD ["script", "-c", "xinetd -d -dontfork"]
