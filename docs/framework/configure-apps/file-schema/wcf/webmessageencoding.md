---
title: <webMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 892ca485-e21a-4a44-8e40-633161ef6796
ms.openlocfilehash: a1d776730053cd6af3c930a33e13582a8906c4d7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940389"
---
# <a name="webmessageencoding"></a>\<webMessageEncoding >
Povoluje čtení a zápis zpráv ve formátu prostého textu XML, JavaScript Object Notation (JSON) a "nezpracovaných" binárních obsahu při použití ve vazbě Windows Communication Foundation (WCF).  
  
 \<system.serviceModel>  
\<> vazeb  
\<customBinding >  
\<> vazby  
\<webMessageEncoding >  
  
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
|`writeEncoding`|Určuje kódování znakové sady, které se má použít pro generování zpráv ve vazbě. Platné hodnoty jsou:<br /><br /> - UnicodeFffeTextEncoding: Kódování Unicode big endian.<br />- Utf16TextEncoding: Kódování Unicode.<br />- Utf8TextEncoding: 8bitové kódování.<br /><br /> Výchozí hodnota je Utf8TextEncoding. Tento atribut je typu <xref:System.Text.Encoding>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou. Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> vazby](../../../misc/binding.md)|Definuje všechny schopnosti vazby vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 Kódování je proces transformace zprávy na sekvenci bajtů. Dekódování je zpětný proces. Tyto procesy vyžadují specifikaci kódování znaků.  
  
 `webMessageEncoding` Element funguje tak, že se přiděluje na řadu vnitřních kodérů, aby bylo možné zpracovávat kódování ve formátu XML a JSON a "nezpracované" binární data. Toto delegování provádí složený kodér zpráv.  
  
 Tento prvek vazby a jeho složený kodér slouží k řízení kódování ve scénářích, které nepoužívají zprávy protokolu SOAP používané `webHttpBinding` prvkem. Mezi tyto scénáře patří "obyčejné staré XML" (POX), representational state transfer (REST), Really Simple Syndication (RSS) a syndikace Atom a Asynchronous JavaScript and XML (AJAX). Kodér kompozitní zprávy nepodporuje SOAP ani WS-Addressing.  
  
 Element Binding lze nakonfigurovat s kódováním znaků Write pomocí `writeEncoding` atributu. Zadaná <xref:System.Text.Encoding> hodnota určuje chování při zápisu JSON a textové případy XML. Při čtení se rozumí jakékoli platné kódování zprávy a kódování textu.  
  
 `maxReadPoolSize`a `maxWritePoolSize` lze ji také použít k nastavení maximálního počtu čtenářů a zapisovačů, které mají být přiděleny. Ve 64 výchozím nastavení jsou přidělována čtecí zařízení a 16 zapisovače.  
  
 Výchozí omezení složitosti se také nastavují pomocí [ \<elementu readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100)) pro ochranu proti třídě útoků DOS (Denial of Service), které se pokoušejí složitou složitost zpráv použít k propojení prostředků zpracování koncových bodů.  
  
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
- [\<customBinding>](custombinding.md)
