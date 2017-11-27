---
title: "&lt;transport&gt; – &lt;netHttpBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b180006-1661-43bf-a699-96fd3da469af
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 67bacedb9a2e46903b97ea0747880bbb1af24a68
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="lttransportgt-of-ltnethttpbindinggt"></a>&lt;transport&gt; – &lt;netHttpBinding&gt;
Definuje vlastnosti, které řídí parametry ověřování pro přenos HTTP.  
  
\<system.serviceModel >  
\<vazby >  
\<netHttpBinding >  
\<Vazba >  
\<zabezpečení >  
\<přenos >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml
<netHttpBinding>  
  <binding>  
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">  
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"  
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows" realm="string">  
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"  
                                  protectionScenario="TransportSelected|TrustedProxy">  
          <customServiceNames></customServiceNames>  
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
|clientCredentialType|-Určuje typ pověření, který se má použít při ověřování klienta pomocí ověřování protokolu HTTP.  Výchozí hodnota je `None`. Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType>.|  
|proxyCredentialType|-Určuje typ pověření, který se má použít při ověřování klienta z v rámci domény použitím proxy serveru pomocí protokolu HTTP. Tento atribut je platí pouze tehdy, když `mode` atribut nadřazené `security` element je `Transport` nebo `TransportCredentialsOnly`. Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType>.|  
|sféry|Řetězec, který určuje sféry, který je používán schéma HTTP ověřování hodnotou hash nebo základní ověřování. Výchozí hodnota je prázdný řetězec.|  
|policyEnforcement|Tento výčet Určuje, kdy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> by se měly vynucovat.<br /><br /> 1.  Nikdy – zásady se vynucují nikdy (rozšířené ochrany je zakázáno).<br />2.  WhenSupported – zásady se vynucují jenom v případě, že klient podporuje rozšířené ochrany.<br />3.  Vždy – je vždy tato zásada vynucená. Klienti, které nepodporují rozšířené ochrany se nepodaří ověřit.|  
|protectionScenario|Tento výčet určuje scénář ochrany vynucují zásady.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Žádné|Zprávy není zabezpečená při přenosu.|  
|Základní|Určuje základní ověřování.|  
|Ověřování algoritmem Digest|Určuje, ověřování hodnotou hash.|  
|NTLM|Určuje ověřování NTLM, pokud je to možné, a pokud ověřování systému Windows selže.|  
|Windows|Určuje integrované ověřování systému Windows.|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Žádné|-Zprávy není zabezpečená při přenosu.|  
|Základní|Určuje základní ověřování podle definice dokumentu RFC 2617 – ověřování pomocí protokolu HTTP: Basic a ověřování algoritmem Digest.|  
|Ověřování algoritmem Digest|Ověřování hodnotou hash podle určuje RFC 2617 – ověřování pomocí protokolu HTTP: Basic a ověřování algoritmem Digest.|  
|NTLM|Určuje ověřování NTLM, pokud je to možné, a pokud ověřování systému Windows selže.|  
|Windows|Určuje integrované ověřování systému Windows.|  
|certifikát|Provede používá certifikát ověření klienta. Tato možnost funguje jenom v případě `Mode` atribut nadřazené `security` elementu je nastaven na přenos a nebude fungovat, pokud je nastavena na možnost TransportCredentialOnly.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nethttpbinding.md)|Definuje možnosti zabezpečení pro [ \<netHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nethttpbinding.md).|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje použití protokolu SSL zabezpečení přenosu s základní vazby. Základní vazby ve výchozím nastavení podporuje komunikaci prostřednictvím protokolu HTTP.  
  
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
      <!-- Configure basicHttpBinding with Transport security -- >  
      <!-- mode and clientCredentialType set to None.-->  
      <binding name="Binding1">  
        <security mode="Transport">  
          <transport clientCredentialType="None"  
                     proxyCredentialType="None">  
            <extendedProtectionPolicy policyEnforcement="WhenSupported"  
                                      protectionScenario="TransportSelected">  
              <customServiceNames></customServiceNames>  
            </extendedProtectionPolicy>
          </transport> 
        </security>  
      </binding>  
    </netHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.BasicHttpSecurityMode.Transport><xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Vazba >](../../../../../docs/framework/misc/binding.md)
