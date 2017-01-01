# PEM certificate formattting #
### String to 'Base64 encoded' format ###

```
#!javascript

    // removing certicate's existing header & footer for proper alignment
    certificate = certificate.replace(/-----BEGIN CERTIFICATE-----/g, "");
    certificate = certificate.replace(/-----END CERTIFICATE-----/g, "");

    // removing linebreaks
    certificate = certificate.replace(/\r?\n|\r/g, "");

    // add new line after every 64 characters
    certificate = certificate.replace(/(.{64})/g, "$1\n");

    // adding header
    if (certificate.indexOf("-----BEGIN CERTIFICATE-----") == -1) {
        certificate = "-----BEGIN CERTIFICATE-----\n" + certificate;
    }

    // adding footer
    if (certificate.indexOf("-----END CERTIFICATE-----") == -1) {
        certificate = certificate + "\n-----END CERTIFICATE-----";
    }
    return certificate;
```

### 'Base64 encoded' format to normal string ###

```
#!javascript

    // removinglinebreaks
    certificate = certificate.replace(/\r?\n|\r/g, "");

    // removing header
    if (certificate.indexOf("-----BEGIN CERTIFICATE-----") > -1) {
        certificate = certificate.substr("-----BEGIN CERTIFICATE-----".length, certificate.length);
    }

    // removing footer
    if (certificate.indexOf("-----END CERTIFICATE-----") > -1) {
        certificate = certificate.substr(0, certificate.indexOf("-----END CERTIFICATE-----"));
    }
    return certificate;
```

Contact me: [ChAliUzair](https://www.freelancer.com/u/ChAliUzair.html)