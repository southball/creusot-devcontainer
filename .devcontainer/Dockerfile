# rustlang/rust:nightly-bookworm on 2024/04/14
FROM rustlang/rust@sha256:f020bfb009ee511dc7472bf9efa724349241096dffb9ab5572351187b4683a91
WORKDIR /creusot
RUN git clone https://github.com/creusot-rs/creusot .
RUN apt-get update && apt-get install -y opam
# https://github.com/ocaml/opam/issues/4327#issuecomment-678630182
RUN opam init --disable-sandboxing
RUN apt-get install -y libexpat1-dev libgtk-3-dev libgtksourceview-3.0-dev
RUN opam switch create -y . 4.14.1
RUN cargo install --path creusot-rustc
RUN cargo install --path cargo-creusot
RUN eval $(opam env) && cargo creusot setup install
RUN apt-get install -y x11-apps openbox tightvncserver novnc
COPY .bashrc /root/.bashrc
COPY .xstartup /root/.vnc/xstartup
RUN chmod +x /root/.vnc/xstartup