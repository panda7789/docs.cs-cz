---
title: '&lt;transport&gt; – &lt;ws2007HttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 3be9d4e64e63b32156cb64257f5bed8230cee3aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="lttransportgt-of-ltws2007httpbindinggt"></a>&lt;transport&gt; – &lt;ws2007HttpBinding&gt;
Definuje nastavení ověřování pro přenos HTTP.  
  
 \<system.serviceModel>  
\<vazby >  
\<ws2007HttpBinding>  
\<Vazba >  
\<zabezpečení >  
\<přenos >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
transport clientCredentialType =   
       "Basic/Certificate/Digest/None/Ntlm/Windows"  
       proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
       realm="string"   
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
|`realm`|Sféra ověřování hodnotou hash nebo základní ověřování. Výchozí hodnota je prázdný řetězec.<br /><br /> Sféra ověření určuje alespoň název hostitele, který provádí ověřování. Můžete také specifikovat kolekci uživatelů, kteří mají přístup. Uživatele můžete dotazovat sféry ověřování k určení, který z nich několik možných uživatelská jména a hesla je možné.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Žádné|Zabezpečení je vypnuté.|  
|Základní|Používá základní ověřování.|  
|Ověřování algoritmem Digest|Použití ověřování algoritmem digest.|  
|NTLM|Ověřování protokolem NTLM se používá jako nouzové řešení s doménou systému Windows.|  
|Windows|Používá integrované ověřování systému Windows.|  
|certifikát|K ověření klienta používá certifikáty X.509.|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Žádné|Zabezpečení je vypnuté.|  
|Základní|Používá základní ověřování.|  
|Ověřování algoritmem Digest|Použití ověřování algoritmem digest.|  
|NTLM|Používá protokol NTLM jako nouzové řešení s doménou systému Windows.|  
|Windows|Používá integrované ověřování systému Windows.|  
|certifikát|K ověření klienta používá certifikáty X.509.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-ws2007httpbinding.md)|Představuje možnosti zabezpečení [ \<– ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Vazba >](../../../../../docs/framework/misc/binding.md)
