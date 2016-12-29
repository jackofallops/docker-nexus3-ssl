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