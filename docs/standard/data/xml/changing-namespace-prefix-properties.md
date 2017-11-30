---
title: "Změna vlastností Namespace předpony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d5c87cbe-4d69-429f-aad5-3103c2ca2770
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7ce6e4b705188b9c1d0949703991633e3f450689
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="changing-namespace-prefix-properties"></a>Změna vlastností Namespace předpony
**XmlNode** třída umožňuje změnit Předpona oboru názvů, které jsou přidružené k danému uzlu. Například následující kód ukazuje předponu elementu mění.  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.LoadXml("<a:test xmlns:a='123' xmlns:b='456'/>")  
Dim e as XmlElement = doc.DocumentElement  
e.Prefix = "b"  
Console.WriteLine(doc.InnerXml)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.LoadXml("<a:test xmlns:a='123' xmlns:b='456'/>");  
XmlElement e = doc.DocumentElement;         
e.Prefix = "b";  
Console.WriteLine(doc.InnerXml);  
```  
  
 **Výstup**  
  
```xml  
<b:test xmlns:a="123" xmlns:b="456" />  
```  
  
 Změna předponu uzlu nedojde ke změně jeho obor názvů. Obor názvů lze nastavit pouze při vytváření uzlu. Při můžete zachovat stromu, může se vyhovět předponu, která nastavíte nové atributy oboru názvů trvalé. Pokud nelze vytvořit nový obor názvů, se změní předponu, takže uzlu zachovává svůj místní názvem a oborem názvů. Následující příklad ukazuje, obor názvů atribut, který chcete přidat.  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.LoadXml("<test xmlns='123'/>")  
Dim e as XmlElement = doc.DocumentElement  
e.Prefix = "a"  
Console.WriteLine(doc.InnerXml)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.LoadXml("<test xmlns='123'/>");  
XmlElement e = doc.DocumentElement;         
e.Prefix = "a";  
Console.WriteLine(doc.InnerXml);  
```  
  
 **Výstup**  
  
```xml  
<a:test xmlns="123" xmlns:a="123" />  
```  
  
 Pokud byl stromu trvalé na řetězec v důsledku volání **dokumentů. InnerXml**, `xmlns:a='123'` atribut byla přidána do zachovat obor názvů `test` elementu. Byl `'123'`, a přesto zůstala `'123'`.  
  
## <a name="see-also"></a>Viz také  
 [XML Document Object Model (DOM).](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
