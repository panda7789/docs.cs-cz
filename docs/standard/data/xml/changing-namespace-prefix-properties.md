---
title: Změna vlastností předpony oboru názvů
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: d5c87cbe-4d69-429f-aad5-3103c2ca2770
ms.openlocfilehash: b1df520d00d3a98b2e518092d4eff51b5d0b7741
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78158022"
---
# <a name="changing-namespace-prefix-properties"></a>Změna vlastností předpony oboru názvů
Třída **XmlNode** umožňuje změnit předponu oboru názvů přidružené k danému uzlu. Například následující kód ukazuje předponu měněného prvku.  
  
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
  
 Změna předpony uzlu nemění jeho obor názvů. Obor názvů lze nastavit pouze v případě, že je uzel vytvořen. Když zachová strom, mohou být nové atributy oboru názvů trvale nastaveny pro splnění nastavené předpony. Pokud nový obor názvů nelze vytvořit, předpona je změněna, takže uzel zachovává svůj místní název a obor názvů. Následující příklad ukazuje přidávaného atributu oboru názvů.  
  
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
  
 V případě, že byl strom uložen do řetězce v důsledku volání metody **doc. InnerXml**, byl přidán atribut `xmlns:a='123'`, který zachovává obor názvů `test` elementu. Bylo `'123'`a zůstalo `'123'`.  
  
## <a name="see-also"></a>Viz také

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
