---
title: '&lt;webMessageEncoding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 892ca485-e21a-4a44-8e40-633161ef6796
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e6257721f8b85296d4da28cc036c946f6357c11b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltwebmessageencodinggt"></a>&lt;webMessageEncoding&gt;
Umožňuje prostého textu XML, kódování zpráv JavaScript Object Notation (JSON) a "nezpracovaných" binární obsah čtení a zápis při použití v [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] vazby.  
  
 \<system.serviceModel >  
\<vazby >  
\<customBinding >  
\<Vazba >  
\<webMessageEncoding >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<webMessageEncoding   
      maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
  
writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`maxReadPoolSize`|Velikost zprávy, které lze číst souběžně bez přidělení nového čtečky. Větší velikosti fondu se systém odolnější vůči špičky aktivity za cenu větší pracovní sady. Výchozí hodnota je 64 čtečky pro každou z vnitřní kodéry (text, JSON a "nezpracovaných").<br /><br /> Zvýšit číslo spotřeba paměti zvýší, ale připraví kodér jak nakládat s nečekané shluky příchozí zprávy, protože je možné používat čtečky z fondu, které jsou již vytvořeny místo vytvoření nové.|  
|`maxWritePoolSize`|Velikost zprávy, které lze najednou odeslat bez přidělení nového zapisovače. Větší velikosti fondu se systém odolnější vůči špičky aktivity za cenu větší pracovní sady. Výchozí hodnota je 16 zapisovače pro každou z vnitřní kodéry (text, JSON a "nezpracovaných").<br /><br /> Zvýšit číslo spotřeba paměti zvýší, ale připraví kodér jak nakládat s nečekané shluky odchozích zpráv, protože je možné použít zapisovače z fondu, které jsou již vytvořeny místo vytvoření nové.|  
|`writeEncoding`|Určuje znakovou sadu kódování má být použit pro generování zpráv v rámci vazby. Platné hodnoty jsou:<br /><br /> -UnicodeFffeTextEncoding: Big Endian kódování Unicode.<br />-Utf16TextEncoding: Kódování Unicode.<br />-Utf8TextEncoding: 8bitové kódování.<br /><br /> Výchozí hodnota je Utf8TextEncoding. Tento atribut je typu <xref:System.Text.Encoding>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<readerQuotas >](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definuje omezení na složitosti protokolu SOAP zprávy, které lze zpracovat koncovými body, které jsou konfigurovány pomocí této vazby. Tento element je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Vazba >](../../../../../docs/framework/misc/binding.md)|Definuje všechny možnosti vazba vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 Proces transformace zprávu do pořadí bajtů kódování je. Dekódování je zpětné proces. Tyto procesy vyžadují specifikaci kódování znaků.  
  
 `webMessageEncoding` Element funguje tak, že delegování na řadu vnitřní kodéry pro zpracování formátu prostého textu XML a JSON kódování a "nezpracovaná" binární data. Toto delegování je potřeba kodéru složené zprávy.  
  
 Tento element vazby a jeho složené kodér slouží k řízení kódování ve scénářích, které nepoužívají SOAP zasílání zpráv používané `webHttpBinding` elementu. Mezi tyto scénáře patří "Prostý formát XML" (POX), přenos REST (Representational State), skutečně jednoduché syndikace (RSS) a Atom syndikace a asynchronní JavaScript a XML (AJAX). Kodér složené zpráv nepodporuje SOAP nebo WS-Addressing.  
  
 Můžete nakonfigurovat prvku vazby kódování znaků zápis pomocí `writeEncoding` atribut. Zadaných <xref:System.Text.Encoding> hodnota určuje chování v zápisu JSON a XML textovou případech. Na čtení se rozumí všechny platné zprávy kódování a kódování textu.  
  
 `maxReadPoolSize`a `maxWritePoolSize` lze také nastavit maximální počet čtení a zápis, která bude přidělena v uvedeném pořadí. Ve výchozím nastavení jsou přiděleny 64 čtení a zápis 16.  
  
 Výchozí omezení složitost jsou nastaveny také, pomocí [ \<readerQuotas >](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd) elementu, který chcete chránit proti třídu odepření služby (DOS) před útoky tento pokus pomocí zpráv složitost vytížit zpracování koncového bodu prostředky.  
  
## <a name="example"></a>Příklad  
  
```xml  
<webMessageEncoding   
    maxReadPoolSize="256"  
    maxWritePoolSize="128"  
    messageVersion="None"  
    textEncoding="utf-8"   
/>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.WebMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>  
 [Kódování zpráv](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [Výběr kodéru zprávy](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Rozšiřování vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
