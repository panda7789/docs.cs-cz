---
title: <byteStreamMessageEncoding>
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: 1d4109bde9c1668bc0832689b05e5d1dc3b198e9
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739060"
---
# <a name="bytestreammessageencoding"></a>\<byteStreamMessageEncoding >
Určuje kódování zprávy jako datový proud bajtů s možností určení kódování znaků.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<byteStreamMessageEncoding >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<byteStreamMessageEncoding />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|messageVersion|Určuje verzi protokolu SOAP zpráv odeslaných pomocí vazby. Tato vlastnost může být nastavena pouze na hodnotu verze zprávy <xref:System.ServiceModel.Channels.MessageVersion.None%2A>. Kodér zpráv datového proudu bajtů nepodporuje žádné jiné verze zprávy.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.Channels.MessageVersion>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou. Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[vazba \<](bindings.md)|Definuje všechny schopnosti vazby vlastní vazby.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>
- [Kódování zpráv](message-encoding.md)
- [Výběr kodéru zprávy](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [Vazby](../../../wcf/bindings.md)
- [Rozšíření vazeb](../../../wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../wcf/extending/custom-bindings.md)
- [\<customBinding >](custombinding.md)
