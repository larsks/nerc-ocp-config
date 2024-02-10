all: ca-certificates.crt

fetch: mozilla-ca-certificates.crt

mozilla-ca-certificates.crt:
	curl -LsSf -o $@ https://curl.se/ca/cacert.pem

ca-certificates.crt: mozilla-ca-certificates.crt nerc-root-ca.crt
	cat $^ > $@ || { rm -f $@; exit 1; }

clean:
	rm -f mozilla-ca-certificates.crt
