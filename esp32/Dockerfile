FROM ubuntu
RUN apt update
RUN apt install -y git curl gcc clang ninja-build libudev-dev unzip xz-utils python3 python3-pip python3-venv libusb-1.0-0 libssl-dev pkg-config libpython2.7 snapd
RUN curl -y --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
RUN git clone https://github.com/esp-rs/rust-build.git && cd rust-build && ./install-rust-toolchain.sh && . ./export-esp.sh
RUN echo 'export LIBCLANG_PATH="/root/.espressif/tools/xtensa-esp32-elf-clang/esp-16.0.0-20230516-x86_64-unknown-linux-gnu/esp-clang/lib/"' >> /root/.bashrc
RUN echo 'export PATH="/root/.espressif/tools/xtensa-esp32-elf-gcc/12.2.0_20230208-x86_64-unknown-linux-gnu/bin/:/root/.espressif/tools/xtensa-esp32s2-elf-gcc/12.2.0_20230208-x86_64-unknown-linux-gnu/bin/:/root/.espressif/tools/xtensa-esp32s3-elf-gcc/12.2.0_20230208-x86_64-unknown-linux-gnu/bin/:$PATH"' >> /root/.bashrc
#RUN rustup component add rust-src --toolchain nightly-x86_64-unknown-linux-gnu
CMD ["/bin/bash"]

# 运行环境：ubuntu 20.04
# 如何运行此容器： docker run -it --privileged -v /run/snapd.socket:/run/snapd.socket <镜像名>
# 为何需要-v /run/snapd.socket:/run/snapd.socket？目前只能宿主机提供snapd服务。多个snapd服务会造成问题
