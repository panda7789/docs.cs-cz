---
title: <transport> z <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 4ef08ad73a03dea21d27217364a7bacb46a3848e
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735930"
---
# <a name="transport-of-nettcpbinding"></a>> \<přenosů \<netTcpBinding >
Definuje typ požadavků zabezpečení na úrovni zprávy pro koncový bod nakonfigurovaný pomocí [\<netTcpBinding >](nettcpbinding.md).  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netTcpBinding >** ](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zabezpečení >** ](security-of-nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<transport >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<netTcpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential">
      <transport clientCredentialType="None|Windows|Certificate"
                 protectionLevel="None|Sign|EncryptAndSign"
                 sslProtocols="Tls|Tls11|Tls12">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</netTcpBinding>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|clientCredentialType|Volitelné. Určuje typ přihlašovacích údajů, které se mají použít při ověřování klientů pomocí zabezpečení přenosu.<br /><br /> -Výchozí hodnota je `Windows`.<br />– Tento atribut je typu <xref:System.ServiceModel.TcpClientCredentialType>.|  
|Platné|Volitelné. Definuje zabezpečení na úrovni přenosu protokolu TCP. Podepisování zpráv snižuje riziko manipulace třetí strany při přenosu zprávy. Šifrování poskytuje během přenosu soukromí na úrovni dat.<br /><br /> Výchozí hodnota je `EncryptAndSign`.|  
|SslProtocols určující|Hodnota příznaku výčtu SslProtocols určující, která určuje, které SslProtocols určující jsou podporovány. Výchozí hodnota je TLS&#124;Tls11&#124;Tls12.|  
|Nastavením PolicyEnforcement|Tento výčet Určuje, kdy se má vyhovět <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy>.<br /><br /> 1. nikdy – zásada se nikdy vynutila (Rozšířená ochrana je zakázaná).<br />2. WhenSupported – zásada se vynutila jenom v případě, že klient podporuje rozšířenou ochranu.<br />3. Always – zásada se vždycky vynutila. Nepůjde ověřit klienty, kteří nepodporují rozšířenou ochranu.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType – atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Žádné|Klient je anonymní. K tomu je potřeba certifikát pro službu.|  
|Windows|Určuje ověřování systému Windows klienta pomocí vyjednávání SP (vyjednávání protokolu Kerberos).|  
|Certifikát|Klient se ověřuje pomocí certifikátu. Používá se vyjednávání SSL a vyžaduje certifikát pro službu.|  
  
## <a name="protectionlevel-attribute"></a>protectionLevel – atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Žádné|Žádná ochrana.|  
|Osobě|Zprávy jsou podepsány.|  
|EncryptAndSign|– Zprávy jsou šifrované a podepsané.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[> zabezpečení \<](security-of-nettcpbinding.md)|Určuje možnosti zabezpečení [\<netTcpBinding >](nettcpbinding.md).|  
  
## <a name="remarks"></a>Poznámky  
 Zabezpečení přenosu použijte pro zajištění integrity a důvěrnosti zprávy SOAP a pro vzájemné ověřování. Pokud je ve vazbě vybraný tento režim zabezpečení, zásobník kanálů se nakonfiguruje pomocí zabezpečeného přenosu a zprávy protokolu SOAP se zabezpečují pomocí zabezpečení přenosu, jako je Windows (Negotiate) nebo SSL přes TCP.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.TcpTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [vazba \<](bindings.md)
