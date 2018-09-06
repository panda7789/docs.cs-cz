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
ms.openlocfilehash: 10aff89679d5c8099d5128540521879f10e3e294
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44041194"
---
# <a name="matching-nodes-using-xpathnavigator"></a>Párování uzlů pomocí XPathNavigator
<xref:System.Xml.XPath.XPathNavigator> Třída poskytuje <xref:System.Xml.XPath.XPathNavigator.Matches%2A> metodou ke zjištění, pokud uzel odpovídá výrazu XPath. <xref:System.Xml.XPath.XPathNavigator.Matches%2A> Metoda výraz XPath jako vstup převezme a vrátí <xref:System.Boolean> , která indikuje, jestli aktuální uzel odpovídá dané výraz XPath nebo zadaný kompilované <xref:System.Xml.XPath.XPathExpression> objektu.  
  
## <a name="matching-nodes"></a>Odpovídající uzly  
 <xref:System.Xml.XPath.XPathNavigator.Matches%2A> Vrátí metoda `true` Pokud výraz XPath určeného odpovídá aktuální uzel. Například v následujícím příkladu kódu <xref:System.Xml.XPath.XPathNavigator.Matches%2A> vrátí metoda `true` Pokud je aktuální uzel elementu `b`a element `b` má atribut `c`.  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator.Matches%2A> Metoda nezmění stav <xref:System.Xml.XPath.XPathNavigator>.  
  
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
