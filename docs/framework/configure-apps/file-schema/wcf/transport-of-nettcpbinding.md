---
title: <transport> z <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: de1f87d8074bbf3d85f6092a4ac316f5fd20052c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355585"
---
# <a name="transport-of-nettcpbinding"></a>\<přenos > z \<netTcpBinding >
Definuje typ požadavky zabezpečení na úrovni zpráva koncovým bodem nakonfigurovaným s [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
 \<system.ServiceModel>  
\<vazby >  
\<netTcpBinding>  
\<Vytvoření vazby >  
\<security>  
\<přenos >  
  
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
 Následující části popisují atributy, podřízené prvky a nadřazené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|clientCredentialType|Volitelné. Určuje typ přihlašovacích údajů pro použití při ověřování klientů pomocí zabezpečení přenosu.<br /><br /> – Výchozí hodnota je `Windows`.<br />– Tento atribut je typu <xref:System.ServiceModel.TcpClientCredentialType>.|  
|Třída protectionLevel|Volitelné. Definuje zabezpečení na úrovni přenosu protokolu TCP. Podepisování zpráv snižuje riziko manipulace s zprávy při jejich přenosu od jiných dodavatelů. Šifrování poskytuje data úrovně ochrany osobních údajů při přenosu.<br /><br /> Výchozí hodnota je `EncryptAndSign`.|  
|sslProtocols|SslProtocols příznak hodnotu výčtu, která určuje, které SslProtocols jsou podporovány. Výchozí hodnota je Tls&#124;Tls11&#124;Tls12.|  
|Parametr policyenforcement na hodnotu|Tento výčet Určuje, kdy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> by se měly vynucovat.<br /><br /> 1.  Nikdy – zásady se vynucují nikdy (rozšířené ochrany je zakázáno).<br />2.  WhenSupported – zásady se vynucuje jenom v případě, že klient podporuje rozšířenou ochranu.<br />3.  Vždy – je vždy zásady vynucují. K ověření se nezdaří klientů, kteří nepodporují rozšířenou ochranu.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType Attribute  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Žádná|Klient je anonymní. To vyžaduje certifikát pro službu.|  
|Windows|Určuje ověřování Windows z klienta pomocí vyjednávání SP (vyjednávání protokolu Kerberos).|  
|Certifikát|Klient je ověřený pomocí certifikátu. Využívá vyjednávání protokolu SSL a vyžaduje certifikát pro službu.|  
  
## <a name="protectionlevel-attribute"></a>Třída protectionLevel atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Žádná|Žádná ochrana.|  
|přihlášení|Zprávy jsou podepsané.|  
|EncryptAndSign|-Zprávy jsou zašifrovaná a podepsaná.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádná  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|Určuje schopnosti zabezpečení [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).|  
  
## <a name="remarks"></a>Poznámky  
 Pro integritu a důvěrnost zprávu protokolu SOAP a vzájemné ověřování, použijte zabezpečení přenosu. Pokud u vazby je vybraný tento režim zabezpečení, zásobník kanál je nakonfigurován pomocí zabezpečeného přenosu a zprávy protokolu SOAP jsou zabezpečené pomocí zabezpečení přenosu, jako je například Windows (Negotiate) nebo SSL přes TCP.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.TcpTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Vazby](../../../../../docs/framework/wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)
