---
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: e2fec2c2e5979b08ed0d832f636b3d0847b9a5dc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915650"
---
# <a name="textmessageencoding"></a>\<textMessageEncoding>
Určuje kódování znaků a verze zprávy používané pro textové zprávy XML.  
  
 \<system.serviceModel>  
\<> vazeb  
\<customBinding >  
\<> vazby  
\<textMessageEncoding>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|maxReadPoolSize|Celé číslo, které určuje, kolik zpráv lze souběžně číst bez přidělení nových čtecích zařízení. Větší velikosti fondů umožňují zvýšit odolnost systému proti špičkám aktivity za cenu větší pracovní sady. Výchozí hodnota je 64.|  
|maxWritePoolSize|Celé číslo, které určuje, kolik zpráv lze souběžně odesílat bez přidělení nových zapisovačů. Větší velikosti fondů umožňují zvýšit odolnost systému proti špičkám aktivity za cenu větší pracovní sady. Výchozí hodnota je 16.|  
|messageVersion|Určuje verzi protokolu SOAP zpráv odeslaných pomocí vazby. Platné hodnoty jsou<br /><br /> - Soap11Addressing10<br />- Soap12Addressing10<br />- Soap11<br />- Soap12<br /><br />Výchozí hodnota je Soap12Addressing10. Tento atribut je typu <xref:System.ServiceModel.Channels.MessageVersion>.|  
|writeEncoding|Určuje kódování znakové sady, které se má použít pro generování zpráv ve vazbě. Platné hodnoty jsou<br /><br /> - UnicodeFffeTextEncoding: Kódování Unicode BigEndian<br />- Utf16TextEncoding: Kódování Unicode<br />- Utf8TextEncoding: 8bitové kódování<br /><br /> Výchozí hodnota je Utf8TextEncoding. Tento atribut je typu <xref:System.Text.Encoding>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou. Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> vazby](../../../misc/binding.md)|Definuje všechny schopnosti vazby vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 Kódování je proces transformace zprávy na sekvenci bajtů. Dekódování je zpětný proces. Windows Communication Foundation (WCF) obsahuje tři typy kódování pro zprávy SOAP: Text, binární a mechanismus optimalizace přenosu zpráv (MTOM).  
  
 Kódování textu reprezentované `textMessageEncoding` prvkem je nejvíce interoperabilní, ale nejméně efektivní kodér pro zprávy XML.  Kodér textu vytváří textovou zprávu na straně kabelu. Zprávy vytvářené v tomto kodéru jsou vhodné pro interoperabilitu WS-*. Webové služby nebo klient webové služby můžou obecně pochopit text XML. Přenos velkých bloků binárních dat jako textu je však nejefektivnější metodou pro kódování zpráv XML.  
  
## <a name="example"></a>Příklad  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [Výběr kodéru zprávy](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [Kódování zpráv](message-encoding.md)
- [Vazby](../../../wcf/bindings.md)
- [Rozšíření vazeb](../../../wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
