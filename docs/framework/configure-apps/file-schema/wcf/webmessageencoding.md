---
title: '&lt;webMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: 892ca485-e21a-4a44-8e40-633161ef6796
ms.openlocfilehash: 90102c25c1c5b83af8f629d18b790af9297fa88c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640248"
---
# <a name="ltwebmessageencodinggt"></a>&lt;webMessageEncoding&gt;
Umožňuje prostého textu XML, zpráv kodovaných zápis JSON (JavaScript Object) a "neupravené" binární obsah ke čtení a zápis v vazby Windows Communication Foundation (WCF).  
  
 \<system.serviceModel>  
\<vazby >  
\<customBinding>  
\<Vytvoření vazby >  
\<webMessageEncoding>  
  
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
|`maxReadPoolSize`|Počet zpráv, které lze souběžně číst bez přidělení nových čtecích zařízení. Větší velikosti fondů byl systém odolnější vůči špičky aktivity za cenu větší pracovní sadu. Výchozí hodnota je 64 čtecí zařízení pro každou z vnitřní kodérů (text JSON a "neupravené").<br /><br /> Zvýšit počet spotřeba paměti zvýší, ale připravuje kodér řešit náhlým nárůstům příchozí zprávy, protože je možné použít čtenáři z fondu, které budou vytvořeny již místo vytvoření nové.|  
|`maxWritePoolSize`|Počet zpráv, které lze souběžně odesílat bez přidělení nových modulů pro zápis. Větší velikosti fondů byl systém odolnější vůči špičky aktivity za cenu větší pracovní sadu. Výchozí hodnota je 16 zapisovače pro každou z vnitřní kodérů (text JSON a "neupravené").<br /><br /> Zvýšit počet spotřeba paměti zvýší, ale připravuje kodér řešit náhlým nárůstům odchozí zprávy, protože je možné použít zapisovače z fondu, které budou vytvořeny již místo vytvoření nové.|  
|`writeEncoding`|Určuje znakovou sadu kódování pro vysílání zpráv z vazby. Platné hodnoty jsou:<br /><br /> -UnicodeFffeTextEncoding: Big Endian kódování Unicode.<br />-Utf16TextEncoding: Kódování Unicode.<br />-Utf8TextEncoding: 8bitové kódování.<br /><br /> Výchozí hodnota je Utf8TextEncoding. Tento atribut je typu <xref:System.Text.Encoding>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<readerQuotas>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovaným s touto vazbou. Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)|Definuje všechny možnosti vázání pro vlastní vazbu.|  
  
## <a name="remarks"></a>Poznámky  
 Kódování je proces transformace zprávu do sekvence bajtů. Dekódování je opačný proces. Tyto procesy vyžadují specifikaci kódování znaků.  
  
 `webMessageEncoding` Element funguje tak, že delegováno na řadu vnitřní kodérů pro zpracování XML a JSON kódování prostého textu a "neupravené" binární data. Složená zpráva Kodér provádí toto delegování.  
  
 Tento element vazby a jeho složené kodér se používají k řízení kódování ve scénářích, které nepoužívají používá zasílání zpráv SOAP `webHttpBinding` elementu. Mezi tyto scénáře patří "Plain Old XML" (POX), Representational State Transfer (REST), syndikace RSS (Really Simple) a Atom syndikace a asynchronní JavaScript a XML (AJAX). Složená zpráva kodér nepodporuje SOAP nebo WS-Addressing.  
  
 Element vazby se dá nakonfigurovat s kódováním znaků zápisu s použitím `writeEncoding` atribut. Zadané <xref:System.Text.Encoding> hodnota určuje chování v zápisu JSON a XML textové případů. Pro čtení je srozumitelný žádné kódování zpráv a kódování textu.  
  
 `maxReadPoolSize` a `maxWritePoolSize` slouží také k nastavení maximálního počtu čtečky a zapisovače, které mají být přiděleny v uvedeném pořadí. Ve výchozím nastavení jsou přiděleny 64 čtečky a zapisovače 16.  
  
 Výchozí omezení složitost jsou také nastavit pomocí [ \<readerQuotas >](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd) útoků, které se pokusí použít složitosti zpráv a jejich zapojení koncového bodu zpracování elementu pro ochranu před třídy s cílem odepření služby (DOS) prostředky.  
  
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
- [Kódování zpráv](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)
- [Výběr kodéru zprávy](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [Vazby](../../../../../docs/framework/wcf/bindings.md)
- [Rozšíření vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
