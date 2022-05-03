# apps_ssl_exporter

## Description


Deploy [ssl_exporter](https://github.com/ribbybibby/ssl_exporter) to expose ssl metrics to prometheus : 


| Metric                         | Meaning                                                                                                          | Labels                                                                      | Probers    |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------- | ---------- |
| ssl_cert_not_after             | The date after which a peer certificate expires. Expressed as a Unix Epoch Time.                                 | serial_no, issuer_cn, cn, dnsnames, ips, emails, ou                         | tcp, https |
| ssl_cert_not_before            | The date before which a peer certificate is not valid. Expressed as a Unix Epoch Time.                           | serial_no, issuer_cn, cn, dnsnames, ips, emails, ou                         | tcp, https |
| ssl_file_cert_not_after        | The date after which a certificate found by the file prober expires. Expressed as a Unix Epoch Time.             | file, serial_no, issuer_cn, cn, dnsnames, ips, emails, ou                   | file       |
| ssl_file_cert_not_before       | The date before which a certificate found by the file prober is not valid. Expressed as a Unix Epoch Time.       | file, serial_no, issuer_cn, cn, dnsnames, ips, emails, ou                   | file       |
| ssl_kubernetes_cert_not_after  | The date after which a certificate found by the kubernetes prober expires. Expressed as a Unix Epoch Time.       | namespace, secret, key, serial_no, issuer_cn, cn, dnsnames, ips, emails, ou | kubernetes |
| ssl_kubernetes_cert_not_before | The date before which a certificate found by the kubernetes prober is not valid. Expressed as a Unix Epoch Time. | namespace, secret, key, serial_no, issuer_cn, cn, dnsnames, ips, emails, ou | kubernetes |
| ssl_kubeconfig_cert_not_after  | The date after which a certificate found by the kubeconfig prober expires. Expressed as a Unix Epoch Time.       | kubeconfig, name, type, serial_no, issuer_cn, cn, dnsnames, ips, emails, ou | kubeconfig |
| ssl_kubeconfig_cert_not_before | The date before which a certificate found by the kubeconfig prober is not valid. Expressed as a Unix Epoch Time. | kubeconfig, name, type, serial_no, issuer_cn, cn, dnsnames, ips, emails, ou | kubeconfig |
| ssl_ocsp_response_next_update  | The nextUpdate value in the OCSP response. Expressed as a Unix Epoch Time                                        |                                                                             | tcp, https |
| ssl_ocsp_response_produced_at  | The producedAt value in the OCSP response. Expressed as a Unix Epoch Time                                        |                                                                             | tcp, https |
| ssl_ocsp_response_revoked_at   | The revocationTime value in the OCSP response. Expressed as a Unix Epoch Time                                    |                                                                             | tcp, https |
| ssl_ocsp_response_status       | The status in the OCSP response. 0=Good 1=Revoked 2=Unknown                                                      |                                                                             | tcp, https |
| ssl_ocsp_response_stapled      | Does the connection state contain a stapled OCSP response? Boolean.                                              |                                                                             | tcp, https |
| ssl_ocsp_response_this_update  | The thisUpdate value in the OCSP response. Expressed as a Unix Epoch Time                                        |                                                                             | tcp, https |
| ssl_probe_success              | Was the probe successful? Boolean.                                                                               |                                                                             | all        |
| ssl_prober                     | The prober used by the exporter to connect to the target. Boolean.                                               | prober                                                                      | all        |
| ssl_tls_version_info           | The TLS version used. Always 1.                                                                                  | version                                                                     | tcp, https |
| ssl_verified_cert_not_after    | The date after which a certificate in the verified chain expires. Expressed as a Unix Epoch Time.                | chain_no, serial_no, issuer_cn, cn, dnsnames, ips, emails, ou               | tcp, https |
| ssl_verified_cert_not_before   | The date before which a certificate in the verified chain is not valid. Expressed as a Unix Epoch Time.          | chain_no, serial_no, issuer_cn, cn, dnsnames, ips, emails, ou               | tcp, https |


## Requirements

none

## Role variables

See [variables](/defaults/main.yml) for more details.

## Examples

        ---
        - hosts: all
          become: true
          become_method: sudo
          gather_facts: true
          roles:
            - role: apps_ssl_exporter

## Grafana Dashboard

You can find a grafana dashboard [here](https://grafana.com/grafana/dashboards/11279)