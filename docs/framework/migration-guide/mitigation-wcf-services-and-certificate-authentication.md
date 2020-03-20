---
title: 'Zmírnění rizik: WCF services a ověřování certifikátů'
ms.date: 03/30/2017
ms.assetid: ef19c91a-b9df-4bf0-a28e-eb1e99c4bc95
ms.openlocfilehash: 8c8493efa2c3223809ad87e01e3faddaea859ca8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457792"
---
# <a name="mitigation-wcf-services-and-certificate-authentication"></a>Zmírnění rizik: WCF services a ověřování certifikátů

Rozhraní .NET Framework 4.6 přidá tls 1.1 a TLS 1.2 do výchozího seznamu protokolu WCF. Pokud jsou klientské i serverové počítače nainstalovány rozhraní .NET Framework 4.6 nebo novější, tls 1.2 se používá pro vyjednávání.

## <a name="impact"></a>Dopad

TLS 1.2 nepodporuje ověřování certifikátu MD5. V důsledku toho pokud zákazník používá certifikát SSL, který používá MD5 pro algoritmus hash, klient WCF se nepodaří připojit ke službě WCF. Další informace naleznete [v tématu Mitigation: WCF Services and Certificate Authentication](mitigation-wcf-services-and-certificate-authentication.md).

## <a name="mitigation"></a>Omezení rizik

Tento problém můžete vyřešit tak, aby se klient WCF mohl připojit k serveru WCF, a to některou z následujících akcí:

- Aktualizujte certifikát tak, aby nepoužíval algoritmus MD5. Toto je doporučené řešení.

- Pokud vazba není dynamicky konfigurována ve zdrojovém kódu, aktualizujte konfigurační soubor aplikace tak, aby používal protokol TLS 1.1 nebo starší verzi protokolu. To umožňuje pokračovat v používání certifikátu s algoritmem hash MD5.

  > [!CAUTION]
  > Toto řešení se nedoporučuje, protože certifikát s algoritmem hash MD5 je považován za nezabezpečený.

  Následující konfigurační soubor provádí toto:

  ```xml
  <configuration>
      <system.serviceModel>
          <bindings>
              <netTcpBinding>
                  <binding>
                      <security mode= "None|Transport|Message|TransportWithMessageCredential" >
                          <transport clientCredentialType="None|Windows|Certificate"
                                              protectionLevel="None|Sign|EncryptAndSign"
                                              sslProtocols="Ssl3|Tls1|Tls11">
                          </transport>
                      </security>
                  </binding>
              </netTcpBinding>
          </bindings>
      </system.serviceModel>
  </configuration>
  ```

- Pokud je vazba dynamicky konfigurována <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> ve zdrojovém kódu, aktualizujte vlastnost tak, aby používala TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) nebo starší verzi protokolu ve zdrojovém kódu.

  > [!CAUTION]
  > Toto řešení se nedoporučuje, protože certifikát s algoritmem hash MD5 je považován za nezabezpečený.

## <a name="see-also"></a>Viz také

- [Kompatibilita aplikací](application-compatibility.md)
