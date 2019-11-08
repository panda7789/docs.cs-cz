---
title: <webMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 892ca485-e21a-4a44-8e40-633161ef6796
ms.openlocfilehash: 4aa87acaf9080959ba8b53e3ec3216314dc745b6
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732580"
---
# <a name="webmessageencoding"></a>\<webMessageEncoding >
Povoluje čtení a zápis zpráv ve formátu prostého textu XML, JavaScript Object Notation (JSON) a "nezpracovaných" binárních obsahu při použití ve vazbě Windows Communication Foundation (WCF).  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<webMessageEncoding >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<webMessageEncoding maxReadPoolSize="Integer"
                    maxWritePoolSize="Integer"
                    writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`maxReadPoolSize`|Množství zpráv, které lze číst souběžně bez přidělení nových čtecích zařízení. Větší velikosti fondů umožňují zvýšit odolnost systému proti špičkám aktivity za cenu větší pracovní sady. Výchozí hodnota je 64 čtenářů pro každý z vnitřních kodérů (text, JSON a "raw").<br /><br /> Zvýšením tohoto počtu se zvyšuje spotřeba paměti, ale připravuje kodér, aby dokázal řešit náhlé shluky příchozích zpráv, protože umožňuje použít čtenáře z fondu, které jsou už vytvořené, a ne vytvářet nové.|  
|`maxWritePoolSize`|Množství zpráv, které lze odesílat souběžně bez přidělení nových modulů pro zápis. Větší velikosti fondů umožňují zvýšit odolnost systému proti špičkám aktivity za cenu větší pracovní sady. Výchozí hodnota je 16 zapisovačů pro každý z vnitřních kodérů (text, JSON a "raw").<br /><br /> Zvýšením tohoto počtu se zvyšuje spotřeba paměti, ale připravuje kodér, aby dokázal řešit náhlé shluky odchozích zpráv, protože dokáže použít zapisovače z fondu, který je už vytvořený, a ne vytvářet nové.|  
|`writeEncoding`|Určuje kódování znakové sady, které se má použít pro generování zpráv ve vazbě. Platné hodnoty jsou:<br /><br /> -UnicodeFffeTextEncoding: kódování Unicode big endian.<br />-Utf16TextEncoding: kódování Unicode.<br />-Utf8TextEncoding: 8bitové kódování.<br /><br /> Výchozí hodnota je Utf8TextEncoding. Tento atribut je typu <xref:System.Text.Encoding>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou. Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[vazba \<](bindings.md)|Definuje všechny schopnosti vazby vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 Kódování je proces transformace zprávy na sekvenci bajtů. Dekódování je zpětný proces. Tyto procesy vyžadují specifikaci kódování znaků.  
  
 Element `webMessageEncoding` funguje tak, že se přiděluje na řadu vnitřních kodérů pro zpracování XML a kódování JSON a "nezpracované" binární data. Toto delegování provádí složený kodér zpráv.  
  
 Tento prvek vazby a jeho složený kodér slouží k řízení kódování ve scénářích, které nepoužívají zprávy protokolu SOAP používané prvkem `webHttpBinding`. Mezi tyto scénáře patří "obyčejné staré XML" (POX), representational state transfer (REST), Really Simple Syndication (RSS) a syndikace Atom a Asynchronous JavaScript and XML (AJAX). Kodér kompozitní zprávy nepodporuje SOAP ani WS-Addressing.  
  
 Element Binding lze nakonfigurovat s kódováním znaků Write pomocí atributu `writeEncoding`. Zadaná <xref:System.Text.Encoding> hodnota určuje chování při zápisu JSON a textové případy XML. Při čtení se rozumí jakékoli platné kódování zprávy a kódování textu.  
  
 `maxReadPoolSize` a `maxWritePoolSize` lze také použít k nastavení maximálního počtu čtenářů a zapisovačů, které mají být přiděleny. Ve 64 výchozím nastavení jsou přidělována čtecí zařízení a 16 zapisovače.  
  
 Výchozí omezení složitosti se také nastavují pomocí [\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100)) elementu k ochraně před třídou útoků DOS (Denial of Service), které se pokoušejí složitou zprávu zpracování koncových bodů při pokusu o použití složitosti zpráv.  
  
## <a name="example"></a>Příklad  
  
```xml  
<webMessageEncoding maxReadPoolSize="256"
                    maxWritePoolSize="128"
                    messageVersion="None"
                    textEncoding="utf-8" />
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.WebMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>
- [Kódování zpráv](message-encoding.md)
- [Výběr kodéru zprávy](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [Vazby](../../../wcf/bindings.md)
- [Rozšíření vazeb](../../../wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../wcf/extending/custom-bindings.md)
- [\<customBinding >](custombinding.md)
