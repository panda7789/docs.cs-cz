---
title: Párování uzlů pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e6848c47-ee5d-401a-89a5-50b5eed40f30
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 882e92c6c8cb6e638ca299ed4c43b9da8f4bf235
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923330"
---
# <a name="matching-nodes-using-xpathnavigator"></a>Párování uzlů pomocí XPathNavigator
<xref:System.Xml.XPath.XPathNavigator> Třída<xref:System.Xml.XPath.XPathNavigator.Matches%2A> poskytuje metodu pro určení, zda uzel odpovídá výrazu XPath. Metoda přijímá výraz XPath jako vstup a <xref:System.Boolean> vrátí hodnotu, která označuje, zda aktuální uzel odpovídá danému výrazu XPath nebo danému kompilovanému <xref:System.Xml.XPath.XPathExpression> objektu. <xref:System.Xml.XPath.XPathNavigator.Matches%2A>  
  
## <a name="matching-nodes"></a>Vyhovující uzly  
 <xref:System.Xml.XPath.XPathNavigator.Matches%2A> Metoda vrátí`true` , pokud aktuální uzel odpovídá zadanému výrazu XPath. Například <xref:System.Xml.XPath.XPathNavigator.Matches%2A> v následujícím příkladu kódu metoda vrátí `b` `true` , pokud je aktuální uzel element a element `b` má atribut `c`.  
  
> [!NOTE]
> Metoda nemění stav <xref:System.Xml.XPath.XPathNavigator>. <xref:System.Xml.XPath.XPathNavigator.Matches%2A>  
  
```vb  
Dim document as XPathDocument = New XPathDocument("input.xml")  
Dim navigator as XPathNavigator = document.CreateNavigator()  
  
navigator.Matches("b[@c]")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("input.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.Matches("b[@c]");  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Výběr dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [Vyhodnocení výrazů XPath pomocí XPathNavigator](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [Rozpoznané typy uzlů s dotazy XPath](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [Dotazy XPath a obory názvů](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [Zkompilované výrazy XPath](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
