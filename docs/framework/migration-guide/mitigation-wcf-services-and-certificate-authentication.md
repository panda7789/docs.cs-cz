---
title: 'Omezení rizik: Služby WCF a ověřování pomocí certifikátu'
ms.date: 03/30/2017
ms.assetid: ef19c91a-b9df-4bf0-a28e-eb1e99c4bc95
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4f05dfab89fa5f811769687c467b2186745ecd5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="mitigation-wcf-services-and-certificate-authentication"></a>Omezení rizik: Služby WCF a ověřování pomocí certifikátu
Rozhraní .NET Framework 4.6 přidá do seznamu výchozích protokol WCF SSL protokoly TLS 1.1 a TLS 1.2. Když klientské a serverové počítače nainstalována rozhraní .NET Framework 4.6 nebo vyšší, použije se pro vyjednávání protokolu TLS 1.2.  
  
## <a name="impact"></a>Dopad  
 Protokol TLS 1.2 nepodporuje ověřování pomocí certifikátu MD5. Výsledkem je, pokud zákazník používá certifikát SSL, který je používán pro algoritmus hash MD5, WCF klientovi nepodaří připojit ke službě WCF. Další informace najdete v tématu [omezení rizik: služby WCF a ověřování pomocí certifikátu](../../../docs/framework/migration-guide/mitigation-wcf-services-and-certificate-authentication.md).  
  
## <a name="mitigation"></a>Zmírnění  
 Tento problém můžete vyřešit tak, aby klienta WCF můžete připojit k serveru WCF pomocí některého z následujících akcí:  
  
-   Aktualizujte certifikát nechcete použít algoritmus MD5. Toto je doporučená řešení.  
  
-   Pokud vazba není nakonfigurováno dynamicky ve zdrojovém kódu, aktualizujte soubor konfigurace aplikace k použití protokolu TLS 1.1 nebo starší verzi protokolu. Umožňuje pokračovat v používání certifikátu s algoritmem hash MD5.  
  
    > [!CAUTION]
    >  Toto řešení se nedoporučuje, protože certifikát se algoritmus hash MD5 považuje za nezabezpečené.  
  
     Následující konfigurační soubor nemá toto:  
  
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
  
-   Pokud je vazba dynamicky konfigurována ve zdrojovém kódu, aktualizovat <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> vlastnost na používání protokolu TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) nebo starší verzi protokolu ve zdrojovém kódu.  
  
    > [!CAUTION]
    >  Toto řešení se nedoporučuje, protože certifikát se algoritmus hash MD5 považuje za nezabezpečené.  
  
## <a name="see-also"></a>Viz také  
 [Změny v modulu runtime](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
