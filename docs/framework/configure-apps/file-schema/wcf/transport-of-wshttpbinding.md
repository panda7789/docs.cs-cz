---
title: "&lt;transport&gt; – &lt;wsHttpBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b73a3810376cf05e8b47e29d3997d6a935c9646
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="lttransportgt-of-ltwshttpbindinggt"></a>&lt;transport&gt; – &lt;wsHttpBinding&gt;
Definuje nastavení ověřování pro přenos HTTP.  
  
 \<system.serviceModel>  
\<vazby >  
\<wsHttpBinding>  
\<Vazba >  
\<zabezpečení >  
\<transport>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<wsHttpBinding>  
    <binding>  
        <security mode="None|Transport|TransportWithMessageCredential|TransportCredentialOnly">  
            <transport  
            clientCredentialType="Basic|Certificate|Digest|None|Ntlm|Windows"  
            proxyCredentialType="Basic|Digest|None|Ntlm|Windows"  
            realm="string" />  
                <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always" protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                </extendedProtecutionPolicy>  
            </transport>  
        </security>  
    </binding>  
</wsHttpBinding>  
```  
  
## <a name="type"></a>Typ  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`clientCredentialType`|Určuje, že pověření použitá k ověření klienta ke službě. Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType>.|  
|`proxyCredentialType`|Určuje, že pověření použitá k ověření klienta pro proxy server domény. Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType>.|  
|`realm`|Řetězec, který určuje sféru ověřování hodnotou hash nebo základní ověřování. Výchozí hodnota je prázdný řetězec.<br /><br /> Sféra ověření určuje alespoň název hostitele, který provádí ověřování. Můžete také specifikovat kolekci uživatelů, který má přístup. Uživatele můžete dotazovat sféry ověření, který z nich několik možných uživatelská jména a hesla je možné zjistit.|  
|`policyEnforcement`|Tento výčet Určuje, kdy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> by se měly vynucovat.<br /><br /> 1.  Nikdy – zásady se vynucují nikdy (rozšířené ochrany je zakázáno).<br />2.  WhenSupported – zásady se vynucují jenom v případě, že klient podporuje rozšířené ochrany.<br />3.  Vždy – je vždy tato zásada vynucená. Klienti, které nepodporují rozšířené ochrany se nepodaří ověřit.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`None`|Zabezpečení je vypnuté.|  
|`Basic`|Používá základní ověřování.|  
|`Digest`|Použití ověřování algoritmem digest.|  
|`Ntlm`|Ověřování protokolem NTLM se používá jako nouzové řešení s doménou systému Windows.|  
|`Windows`|Používá integrované ověřování systému Windows.|  
|`Certificate`|K ověření klienta používá certifikáty X.509.|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`None`|Zabezpečení je vypnuté.|  
|`Basic`|Používá základní ověřování.|  
|`Digest`|Použití ověřování algoritmem digest.|  
|`Ntlm`|Používá protokol NTLM jako nouzové řešení s doménou systému Windows.|  
|`Windows`|Používá integrované ověřování systému Windows.|  
|`Certificate`|K ověření klienta používá certifikáty X.509.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|Představuje možnosti zabezpečení [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Vazba >](../../../../../docs/framework/misc/binding.md)
