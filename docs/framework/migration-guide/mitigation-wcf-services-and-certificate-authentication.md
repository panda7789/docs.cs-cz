---
title: Zmírnění Služby WCF a ověřování certifikátů
ms.date: 03/30/2017
ms.assetid: ef19c91a-b9df-4bf0-a28e-eb1e99c4bc95
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b6ad11d4295be3a5bfd590d9cef1926f6676f2b1
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70043230"
---
# <a name="mitigation-wcf-services-and-certificate-authentication"></a>Zmírnění Služby WCF a ověřování certifikátů

.NET Framework 4,6 přidá do seznamu výchozí seznam protokolu WCF SSL protokol TLS 1,1 a TLS 1,2. Pokud jsou v klientské i serverové počítače nainstalované .NET Framework 4,6 nebo novější, pro vyjednávání se používá TLS 1,2.

## <a name="impact"></a>Dopad

TLS 1,2 nepodporuje ověřování certifikátu MD5. Výsledkem je, že pokud zákazník používá certifikát SSL, který používá MD5 pro algoritmus hash, klient služby WCF se nemůže připojit ke službě WCF. Další informace najdete v tématu [zmírnění rizika: Služby WCF a ověřování](../../../docs/framework/migration-guide/mitigation-wcf-services-and-certificate-authentication.md)certifikátů.

## <a name="mitigation"></a>Zmírnění

Tento problém můžete obejít tak, aby se klient WCF mohl připojit k serveru WCF pomocí kterékoli z následujících možností:

- Aktualizujte certifikát, aby nepoužíval algoritmus MD5. Toto je doporučené řešení.

- Pokud není vazba dynamicky nakonfigurovaná ve zdrojovém kódu, aktualizujte konfigurační soubor aplikace tak, aby používal protokol TLS 1,1 nebo dřívější verzi protokolu. To vám umožní pokračovat v používání certifikátu s algoritmem hash MD5.

  > [!CAUTION]
  > Toto řešení se nedoporučuje, protože certifikát s algoritmem hash MD5 je považován za nezabezpečený.

  Následující konfigurační soubor provede toto:

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
      </system.ServiceModel>
  </configuration>
  ```

- Pokud je vazba dynamicky nakonfigurovaná ve zdrojovém kódu, aktualizujte <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> vlastnost na použití TLS 1,1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) nebo starší verze protokolu ve zdrojovém kódu.

  > [!CAUTION]
  > Toto řešení se nedoporučuje, protože certifikát s algoritmem hash MD5 je považován za nezabezpečený.

## <a name="see-also"></a>Viz také:

- [Změny v modulu runtime](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
