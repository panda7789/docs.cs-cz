---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: c5c7ec2b18143ff4d71540a60e24b8225ca4db16
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738589"
---
# \<sslStreamSecurity>
Představuje vlastní prvek vazby, který podporuje zabezpečení kanálu pomocí datového proudu SSL.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sslStreamSecurity>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|requireClientCertificate|Logická hodnota určující, zda je klientský certifikát pro tuto vazbu vyžadován. Výchozí formát je `false`.|  
|SslProtocols určující|Hodnota příznaku výčtu SslProtocols určující, která určuje, které SslProtocols určující jsou podporovány. Výchozí hodnota je SSL3&#124;TLS&#124;Tls11&#124;Tls12.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|Definuje všechny schopnosti vazby vlastní vazby.|  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [Vazby](../../../wcf/bindings.md)
- [Rozšíření vazeb](../../../wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
