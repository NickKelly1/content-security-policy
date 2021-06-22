# Content Security Policy

Content-Security-Policy (CSP) is a browser header that grants some protection against common attack vectors, namely cross site scripting (XSS) and packet sniffing.

CSP restricts resource access giving the developer control over which protocols, domains, attributes and other browser mechanisms are accessible to the page.

```http
GET /my-page HTTP/1.1
Host: my-domain:80
Content-Security-Policy: <CSP-policy>

<http-request-body>
```

CSP can also be put into `<meta>` tag's in within the `<head>` of a html document

```html
<head>
  <meta
    http-equivalent="Content-Security-Policy"
    content="default-src 'self'; img-src https://*; child-src 'none';">
</head>
```

A CSP policy is made up of rules written in key-value pairs. The keys are known as "directives".

- Key and values are separated by whitespace
- Values are separated by whitespace
- Key-value pairs are separated by semicolon;

```http
GET /my-page HTTP/1.1
Host: my-domain:80
Content-Security-Policy: directive1 value11 value12; directive2 value21; directive3 value31;
```

## Directives

Many CSP directives restrict resource sourcing. Resource sourcing directives are postfixed with `-src`, for example `img-src`, `script-src`, `style-src`.

A special directive `default-src` provides a fallback value for ant `*-src` directive not set in the CSP header value.

## Examples

### Restrict resources to same domain

```http
Content-Security-Policy: default-src 'self'
```

### Restrict resources to same and trusted domain

```http
Content-Security-Policy: default-src 'self' trusted.com *trusted.com
```

### Allow only images on any domain

```http
Content-Security-Policy: default-src 'self' trusted.com *trusted.com
```

## Security

### Media

```http
Content-Security-Policy: default-src `self
```


## Usage with ExpressJS

### Middleware

### Helmet

## Other security headers

### Strict-Transport-Security: Packet Sniffing

The HTTP Strict-Transport-Security header (HSTS) ensures that if the page is served over HTTPS, further connections must also use HTTPS.

HSTS aims to stop packet sniffing and man-in-the-middle attacks by ensuring all later traffic is encrypted. If the initial page load is not encrypted, a "man in the middle" could remove the HSTS header, making the header redundant on unencrypted non-https page loads.

's main ad only works

## Further reading

- [MDN Documentation](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP)
