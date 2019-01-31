---
title: <transport> z <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 3b180006-1661-43bf-a699-96fd3da469af
ms.openlocfilehash: 4d84d99660e4804a5eff2e343ba01c2983520b8f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55280992"
---
# <a name="transport-of-nethttpbinding"></a>\<přenos > z \<netHttpBinding >
Definuje vlastnosti, které řídí parametry ověřování pro přenos pomocí protokolu HTTP.  
  
\<system.serviceModel>  
\<vazby >  
\<netHttpBinding>  
\<Vytvoření vazby >  
\<security>  
\<přenos >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<netHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="string">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</netHttpBinding>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|clientCredentialType|: Určuje typ pověření pro použití při ověřování klientů pomocí ověřování protokolu HTTP.  Výchozí hodnota je `None`. Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType>.|  
|proxyCredentialType|: Určuje typ pověření pro použití při ověřování klienta z v rámci domény pomocí proxy serveru prostřednictvím protokolu HTTP. Tento atribut je použitelné pouze tehdy, když `mode` atributu nadřazeného elementu `security` element je `Transport` nebo `TransportCredentialsOnly`. Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType>.|  
|Sféra|Řetězec určující sféru, který používá schéma ověřování protokolu HTTP pro ověřování algoritmem digest nebo základní ověřování. Výchozí hodnota je prázdný řetězec.|  
|Parametr policyenforcement na hodnotu|Tento výčet Určuje, kdy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> by se měly vynucovat.<br /><br /> 1.  Nikdy – zásady se vynucují nikdy (rozšířené ochrany je zakázáno).<br />2.  WhenSupported – zásady se vynucuje jenom v případě, že klient podporuje rozšířenou ochranu.<br />3.  Vždy – je vždy zásady vynucují. K ověření se nezdaří klientů, kteří nepodporují rozšířenou ochranu.|  
|protectionScenario|Tento výčet určuje scénář ochrany vynucuje daná zásada.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType Attribute  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Žádná|Zprávy nejsou zabezpečená při přenosu.|  
|Základní|Určuje základní ověřování.|  
|ověřování algoritmem Digest|Určuje, ověřování hodnotou hash.|  
|Ntlm|Určuje ověřování protokolem NTLM, pokud je to možné a pokud se nezdaří ověřování Windows.|  
|Windows|Určuje integrované ověřování Windows.|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType Attribute  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Žádná|-Zprávy nejsou zabezpečená při přenosu.|  
|Základní|Základní ověřování určuje, jak jsou definovány v dokumentu RFC 2617 – ověřování pomocí protokolu HTTP: Základní a ověřování algoritmem Digest.|  
|ověřování algoritmem Digest|Ověřování algoritmem digest Určuje, jak jsou definovány v dokumentu RFC 2617 – ověřování pomocí protokolu HTTP: Základní a ověřování algoritmem Digest.|  
|Ntlm|Určuje ověřování protokolem NTLM, pokud je to možné a pokud se nezdaří ověřování Windows.|  
|Windows|Určuje integrované ověřování Windows.|  
|Certifikát|Provádí pomocí certifikátu ověřování klienta. Tato možnost funguje jenom v případě, `Mode` atributu nadřazeného elementu `security` element je nastavena na přenos a nebude fungovat, pokud je nastaveno na TransportCredentialOnly.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádná  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nethttpbinding.md)|Definuje možnosti zabezpečení pro [ \<netHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nethttpbinding.md).|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje použití zabezpečení přenosu SSL s základní vazby. Základní vazby ve výchozím nastavení podporuje komunikaci pomocí protokolu HTTP.  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="netHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <netHttpBinding>
      <!-- Configure basicHttpBinding with Transport security -->
      <!-- mode and clientCredentialType set to None. -->
      <binding name="Binding1">
        <security mode="Transport">
          <transport clientCredentialType="None"
                     proxyCredentialType="None">
            <extendedProtectionPolicy policyEnforcement="WhenSupported"
                                      protectionScenario="TransportSelected">
              <customServiceNames>
              </customServiceNames>
            </extendedProtectionPolicy>
          </transport>
        </security>
      </binding>
    </netHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Vazby](../../../../../docs/framework/wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)
