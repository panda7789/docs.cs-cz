---
title: Změna vlastností předpony Namespace
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: d5c87cbe-4d69-429f-aad5-3103c2ca2770
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4a6597a3a57cd68c4dd17c4fbae882590f373709
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44174117"
---
# <a name="changing-namespace-prefix-properties"></a>Změna vlastností předpony Namespace
**XmlNode** třída umožňuje změnit předponu oboru názvů, který je přidružený k daném uzlu. Například následující kód ukazuje předponu element mění.  
  
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
  
 **Output**  
  
```xml  
<b:test xmlns:a="123" xmlns:b="456" />  
```  
  
 Změna předponu uzel nezmění svůj obor názvů. Obor názvů lze nastavit pouze při vytvoření uzlu. Když vyskytovat i dál stromu, nové atributy oboru názvů může nastavit jako trvalý, si tím se uspokojí předpony, které nastavíte. Pokud nelze vytvořit nový obor názvů, předpona, která se změní tak, že uzel zachová svůj místní název a obor názvů. Následující příklad ukazuje obor názvů atribut přidávaný.  
  
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
  
 **Output**  
  
```xml  
<a:test xmlns="123" xmlns:a="123" />  
```  
  
 Když stromu byl trvale uložen na řetězec v důsledku volání **dokumentu. InnerXml**, `xmlns:a='123'` atributu byl přidán k zachování obor názvů `test` elementu. Bylo `'123'`, a zůstal `'123'`.  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
