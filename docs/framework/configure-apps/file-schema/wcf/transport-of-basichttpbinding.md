---
title: <transport> z <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 4c5ba293-3d7e-47a6-b84e-e9022857b7e5
ms.openlocfilehash: af5852c3c7850f91686d50294c8846f85574e909
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918636"
---
# <a name="transport-of-basichttpbinding"></a>\<> přenosu > \<BasicHttpBinding
Definuje vlastnosti, které řídí parametry ověřování pro přenos HTTP.  
  
 \<system.ServiceModel>  
\<> vazeb  
\<basicHttpBinding>  
\<> vazby  
\<> zabezpečení  
\<> přenosu  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<basicHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="String">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|clientCredentialType|– Určuje typ přihlašovacích údajů, které se mají použít při ověřování klientů pomocí ověřování protokolem HTTP.  Výchozí hodnota je `None`. Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType>.|  
|proxyCredentialType|– Určuje typ přihlašovacích údajů, které se mají použít při ověřování klientů v rámci domény pomocí proxy serveru přes protokol HTTP. Tento atribut je použitelný pouze v případě `mode` , že je `Transport` atribut `security` nadřazeného prvku nebo `TransportCredentialsOnly`. Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType>.|  
|sféry|Řetězec určující sféru, která je používána schématem ověřování protokolu HTTP pro ověřování algoritmem Digest nebo základní ověřování. Výchozí hodnota je prázdný řetězec.|  
|Nastavením PolicyEnforcement|Tento výčet Určuje, kdy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> se má vyhovět.<br /><br /> 1.  Nikdy – zásada se nikdy vynutila (Rozšířená ochrana je zakázaná).<br />2.  WhenSupported – zásada se vynutila jenom v případě, že klient podporuje rozšířenou ochranu.<br />3.  Always – zásada se vždycky vynutila. Nepůjde ověřit klienty, kteří nepodporují rozšířenou ochranu.|  
|protectionScenario|Tento výčet Určuje scénář ochrany, který zásady vynutily.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType – atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|Žádné|Zprávy nejsou během přenosu zabezpečeny.|  
|Základní|Určuje základní ověřování.|  
|Otisk|Určuje ověřování hodnotou hash.|  
|NTLM|Určuje ověřování NTLM, pokud je to možné, a pokud se ověřování systému Windows nezdařilo.|  
|Windows|Určuje integrované ověřování systému Windows.|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType – atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|Žádné|– Zprávy nejsou během přenosu zabezpečeny.|  
|Základní|Určuje základní ověřování definované v dokumentu RFC 2617 – ověřování protokolem HTTP: Základní ověřování a ověřování algoritmem Digest.|  
|Otisk|Určuje ověřování hodnotou hash definované v dokumentu RFC 2617 – ověřování protokolem HTTP: Základní ověřování a ověřování algoritmem Digest.|  
|NTLM|Určuje ověřování NTLM, pokud je to možné, a pokud se ověřování systému Windows nezdařilo.|  
|Windows|Určuje integrované ověřování systému Windows.|  
|Certifikát|Provádí ověřování klientů pomocí certifikátu. Tato možnost funguje pouze v `Mode` případě, že atribut nadřazeného `security` elementu je nastaven na hodnotu Transport a nebude fungovat, pokud je nastaven na TransportCredentialOnly.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> zabezpečení](security-of-basichttpbinding.md)|Definuje možnosti [ \<zabezpečení BasicHttpBinding >](basichttpbinding.md).|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje použití zabezpečení přenosu SSL se základní vazbou. Základní vazba standardně podporuje komunikaci pomocí protokolu HTTP.  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
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
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<> vazby](../../../misc/binding.md)
