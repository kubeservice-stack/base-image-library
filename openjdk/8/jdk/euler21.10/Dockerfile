#
# NOTE: THIS DOCKERFILE IS GENERATED VIA "apply-templates.sh"
#
# PLEASE DO NOT EDIT IT DIRECTLY.
#

FROM dongjiang1989/bc-oe:21.10

ENV JAVA_HOME /usr/java/openjdk-8
ENV PATH $JAVA_HOME/bin:$PATH

# Default to UTF-8 file.encoding
ENV LANG en_US.UTF-8

ENV JAVA_VERSION 1.8.0_8u341

RUN set -eux; \
	\
    arch="$(arch)"; arch="${arch##*-}"; \
	case "$arch" in \
		'x86_64') \
			downloadUrl='https://package-1257912602.cos.ap-beijing.myqcloud.com/jdk-8u341-linux-x64.tar.gz'; \
			;; \
		'aarch64') \
			downloadUrl='https://package-1257912602.cos.ap-beijing.myqcloud.com/jdk-8u341-linux-aarch64.tar.gz'; \
			;; \
		*) echo >&2 "error: unsupported architecture: '$arch'"; exit 1 ;; \
	esac; \
	\
	curl -fL -o openjdk.tgz "$downloadUrl"; \
	\
	mkdir -p "$JAVA_HOME"; \
	tar --extract \
		--file openjdk.tgz \
		--directory "$JAVA_HOME" \
		--strip-components 1 \
		--no-same-owner \
	; \
	rm openjdk.tgz*; \
	\
	ln -sfT "$JAVA_HOME" /usr/java/default; \
	ln -sfT "$JAVA_HOME" /usr/java/latest; \
	\
	javac -version; \
	java -version

CMD ["java", "-version"]