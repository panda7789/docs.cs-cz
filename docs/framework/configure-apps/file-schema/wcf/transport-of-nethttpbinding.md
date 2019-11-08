---
title: <transport> z <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 3b180006-1661-43bf-a699-96fd3da469af
ms.openlocfilehash: b975015a9c9a0af53117900c45d917ce1c1a53e9
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732821"
---
# <a name="transport-of-nethttpbinding"></a>> \<přenosů \<netHttpBinding >
Definuje vlastnosti, které řídí parametry ověřování pro přenos HTTP.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netHttpBinding >** ](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zabezpečení >** ](security-of-nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<transport >**  
  
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
|clientCredentialType|– Určuje typ přihlašovacích údajů, které se mají použít při ověřování klientů pomocí ověřování protokolem HTTP.  Výchozí hodnota je `None`. Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType>.|  
|proxyCredentialType|– Určuje typ přihlašovacích údajů, které se mají použít při ověřování klientů v rámci domény pomocí proxy serveru přes protokol HTTP. Tento atribut je použitelný pouze v případě, že atribut `mode` nadřazeného prvku `security` je `Transport` nebo `TransportCredentialsOnly`. Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType>.|  
|sféry|Řetězec určující sféru, která je používána schématem ověřování protokolu HTTP pro ověřování algoritmem Digest nebo základní ověřování. Výchozí hodnota je prázdný řetězec.|  
|Nastavením PolicyEnforcement|Tento výčet Určuje, kdy se má vyhovět <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy>.<br /><br /> 1. nikdy – zásada se nikdy vynutila (Rozšířená ochrana je zakázaná).<br />2. WhenSupported – zásada se vynutila jenom v případě, že klient podporuje rozšířenou ochranu.<br />3. Always – zásada se vždycky vynutila. Nepůjde ověřit klienty, kteří nepodporují rozšířenou ochranu.|  
|protectionScenario|Tento výčet Určuje scénář ochrany, který zásady vynutily.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType – atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Žádné|Zprávy nejsou během přenosu zabezpečeny.|  
|Základní|Určuje základní ověřování.|  
|otisk|Určuje ověřování hodnotou hash.|  
|NTLM|Určuje ověřování NTLM, pokud je to možné, a pokud se ověřování systému Windows nezdařilo.|  
|Windows|Určuje integrované ověřování systému Windows.|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType – atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Žádné|– Zprávy nejsou během přenosu zabezpečeny.|  
|Základní|Určuje základní ověřování definované v dokumentu RFC 2617 – ověřování protokolem HTTP: základní a ověřování hodnotou hash.|  
|otisk|Určuje ověřování hodnotou hash definované v dokumentu RFC 2617 – ověřování protokolem HTTP: základní a ověřování hodnotou hash.|  
|NTLM|Určuje ověřování NTLM, pokud je to možné, a pokud se ověřování systému Windows nezdařilo.|  
|Windows|Určuje integrované ověřování systému Windows.|  
|Certifikát|Provádí ověřování klientů pomocí certifikátu. Tato možnost funguje pouze v případě, že atribut `Mode` nadřazeného elementu `security` je nastaven na hodnotu Transport a nebude fungovat, pokud je nastaven na hodnotu TransportCredentialOnly.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[> zabezpečení \<](security-of-nethttpbinding.md)|Definuje možnosti zabezpečení [\<netHttpBinding >](nethttpbinding.md).|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje použití zabezpečení přenosu SSL se základní vazbou. Základní vazba standardně podporuje komunikaci pomocí protokolu HTTP.  
  
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
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [vazba \<](bindings.md)
