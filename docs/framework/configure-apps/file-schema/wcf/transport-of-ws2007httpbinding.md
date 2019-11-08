---
title: <transport> z <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 0cd20c607b0c4ddd3ecfd806d38ba63b4a5c5a25
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732759"
---
# <a name="transport-of-ws2007httpbinding"></a>> \<přenosů \<ws2007HttpBinding >
Definuje nastavení ověřování pro přenos HTTP.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ws2007HttpBinding >** ](ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zabezpečení >** ](security-of-ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<transport >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a>Typ  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`clientCredentialType`|Určuje přihlašovací údaje, které se používají k ověření klienta ke službě. Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType>.|  
|`proxyCredentialType`|Určuje přihlašovací údaje, které se používají k ověření klienta na proxy doméně. Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType>.|  
|`realm`|Sféra ověření pro ověřování algoritmem Digest nebo základního ověřování. Výchozí hodnota je prázdný řetězec.<br /><br /> Sféra ověřování určuje alespoň název hostitele, který provádí ověřování. Může také určit kolekci uživatelů, kteří mají přístup. Uživatel může zadat dotaz na sféru ověření, aby mohl zjistit, který z několika možných uživatelských jmen a hesel lze použít.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType – atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Žádné|Zabezpečení je zakázané.|  
|Základní|Používá základní ověřování.|  
|otisk|Používá ověřování hodnotou hash.|  
|NTLM|Používá ověřování NTLM jako zálohu v doméně systému Windows.|  
|Windows|Používá integrované ověřování systému Windows.|  
|Certifikát|Pomocí certifikátů X. 509 ověří klienta.|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType – atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Žádné|Zabezpečení je zakázané.|  
|Základní|Používá základní ověřování.|  
|otisk|Používá ověřování hodnotou hash.|  
|NTLM|Používá protokol NTLM jako zálohu s doménou systému Windows.|  
|Windows|Používá integrované ověřování systému Windows.|  
|Certifikát|Pomocí certifikátů X. 509 ověří klienta.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[> zabezpečení \<](security-of-ws2007httpbinding.md)|Představuje možnosti zabezpečení [\<ws2007HttpBinding >](ws2007httpbinding.md) elementu.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [vazba \<](bindings.md)
