---
title: "&lt;transport&gt; – &lt;webHttpBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 44397edf2d2c5e2f99a255789452b08d91484b81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="lttransportgt-of-ltwebhttpbindinggt"></a>&lt;transport&gt; – &lt;webHttpBinding&gt;
Definuje nastavení zabezpečení na úrovni přenosu pro koncového bodu služby nastavena k přijímání požadavků HTTP.  
  
 \<systém. ServiceModel >  
\<vazby >  
\<webHttpBinding >  
\<Vazba >  
\<zabezpečení >  
\<přenos >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<webHttpBinding>  
    <binding>  
        <security  
        mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">  
            <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"  
             proxyCredentialType="None|Basic|Digest|Ntlm|Windows" realm="string" >  
                <extendedProtectionPolicy  
                     policyEnforcement="Never|WhenSupported|Always"  
                     protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                        </extendedProtectionPolicy>  
            </transport>  
        </security>  
    </binding>  
</WebHttpBinding>  
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
|`Certificate`|K ověření klienta používá certifikáty X.509.|  
|`Digest`|Použití ověřování algoritmem digest.|  
|`Ntlm`|Ověřování protokolem NTLM se používá jako nouzové řešení s doménou systému Windows.|  
|`Windows`|Používá integrované ověřování systému Windows.|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`None`|Zabezpečení je vypnuté.|  
|`Basic`|Používá základní ověřování.|  
|`Digest`|Použití ověřování algoritmem digest.|  
|`Ntlm`|Používá protokol NTLM jako nouzové řešení s doménou systému Windows.|  
|`Windows`|Používá integrované ověřování systému Windows.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-webhttpbinding.md)|Představuje možnosti zabezpečení [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Vazba >](../../../../../docs/framework/misc/binding.md)  
 [Model programování webových služeb HTTP WCF](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
