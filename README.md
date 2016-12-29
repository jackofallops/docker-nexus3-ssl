# docker-nexus3-ssl
Nexus 3 with SSL enabled

## Notes
Valid keystore and data mount mandatory for starting the container.

ports:

- "8081:8081"
- "5000:5000"
- "8443:8443"

volumes:
- "/somelocalfolder:/nexus-data"


_NB: Create keystore at etc/ssl/keystore.jks inside "somelocalfolder" with passphrase "changeit"_

### Example keystore:
```bash
openssl genrsa -out docker-ca.key 4096
openssl req -x509 -new -nodes -key docker-ca.key -days 7300 -out docker-ca.pem -subj '/CN=cds-docker-registry'
openssl pkcs12 -export -in docker-ca.pem -inkey docker-ca.key -certfile docker-ca.pem -out newkeystore.p12
keytool -importkeystore -srckeystore newkeystore.p12 -srcstoretype pkcs12 -destkeystore /somelocalfolder/keystore.jks -deststoretype JKS
```
