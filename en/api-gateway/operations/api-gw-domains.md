# Connecting a domain

You can connect your own domain to access the API gateway. You can connect multiple domains to a single API gateway. In this case, the domain is identified by the `Host` header.

{% note warning %}

It must be a third-level domain or lower. For example, you can connect the www.example.com domain but not example.com. This has to do with how CNAME records are processed on DNS hosting. Learn more in [RFC 1912, Section 2.4.](https://www.ietf.org/rfc/rfc1912.txt)

{% endnote %}

To connect a domain to an API gateway:

{% list tabs %}

- Management console

   1. Host a CNAME record with your DNS provider or on your own DNS server:

      ```
      <domain> IN CNAME <API gateway service domain>
      ```

      To find out an API gateway's service domain:

      1. Go to the [management console]({{ link-console-main }}).
      1. Select the folder where the API gateway is located, and in the service list, select **API Gateway**.
      1. Select the API gateway.
      1. You can see the service domain under **General information**.

      Domain names must end in a dot.

   1. In the [management console]({{ link-console-main }}), select the folder containing the API gateway.

   1. In the list of services, select **Certificate Manager** and:

      1. [Create](../../certificate-manager/operations/managed/cert-create.md) a certificate from Let's Encrypt<sup>®</sup>.
      1. [Confirm](../../certificate-manager/operations/managed/cert-validate.md) your domain privileges.
      1. When the certificate status changes to `Issued`, [create](../../certificate-manager/operations/domain/domain-create.md) your domain. In the **Certificate** field, select the certificate that you created in Step 3.1.

      {% note info %}

      The Let's Encrypt<sup>®</sup> certificate is valid for 90 days. You need to [update](../../certificate-manager/concepts/managed-certificate.md#renew). In some cases, domain rights checks are performed [automatically](../../certificate-manager/concepts/challenges.md#auto).

      {% endnote %}

   1. Go back to the folder page.

   1. In the list of services, select **API Gateway** and:

      1. Select the API gateway.
      1. In the window that opens, go to **Domains**.
      1. Click **Connect** and select the domain.

{% endlist %}
