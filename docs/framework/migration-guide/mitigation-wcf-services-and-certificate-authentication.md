---
title: 'Omezení rizik: Služby WCF a ověřování pomocí certifikátu'
ms.date: 03/30/2017
ms.assetid: ef19c91a-b9df-4bf0-a28e-eb1e99c4bc95
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fdacf5fc4a5c73fc60df961432089ee65dd0cfaa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079536"
---
# <a name="mitigation-wcf-services-and-certificate-authentication"></a>Omezení rizik: Služby WCF a ověřování pomocí certifikátu
Rozhraní .NET Framework 4.6 přidá do seznamu výchozích protokol WCF SSL TLS 1.1 a TLS 1.2. Když klientských i serverových počítačích mít rozhraní .NET Framework 4.6 nebo novější, použije se pro vyjednávání protokolu TLS 1.2.  
  
## <a name="impact"></a>Dopad  
 Protokol TLS 1.2 nepodporuje ověřování pomocí certifikátu MD5. V důsledku toho pokud zákazník používá třeba certifikát SSL, který se používá pro algoritmus hash MD5, klienta WCF se nepodařilo připojit ke službě WCF. Další informace najdete v tématu [omezení rizik: Služby WCF a ověřování pomocí certifikátu](../../../docs/framework/migration-guide/mitigation-wcf-services-and-certificate-authentication.md).  
  
## <a name="mitigation"></a>Zmírnění  
 Tento problém můžete obejít tak, aby klient WCF můžete připojit k serveru WCF pomocí některého z následujících akcí:  
  
-   Aktualizujte certifikát nechcete použít algoritmus MD5. Toto je doporučené řešení.  
  
-   Pokud se vazba není dynamicky nakonfigurována ve zdrojovém kódu, aktualizujte konfigurační soubor aplikace pro použití protokolu TLS 1.1 nebo starší verzi protokolu. To umožňuje pokračovat v používání certifikátu s algoritmem hash MD5.  
  
    > [!CAUTION]
    >  Toto řešení se nedoporučuje, protože certifikátu s algoritmem hash MD5 se považuje za nezabezpečené.  
  
     Následující konfigurační soubor provede následující:  
  
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
  
-   Pokud je vazba konfigurována dynamicky ve zdrojovém kódu, aktualizujte <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> vlastnost na používání protokolu TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) nebo starší verzi protokolu ve zdrojovém kódu.  
  
    > [!CAUTION]
    >  Toto řešení se nedoporučuje, protože certifikátu s algoritmem hash MD5 se považuje za nezabezpečené.  
  
## <a name="see-also"></a>Viz také:

- [Změny v modulu runtime](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
