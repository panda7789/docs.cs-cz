---
title: "Odpovídající pomocí objektem XPathNavigator nastaveným na uzly"
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
ms.assetid: e6848c47-ee5d-401a-89a5-50b5eed40f30
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a51c358ecb50c94ccde9f86ba80fc8f0670f82d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="matching-nodes-using-xpathnavigator"></a>Odpovídající pomocí objektem XPathNavigator nastaveným na uzly
<xref:System.Xml.XPath.XPathNavigator> Třída poskytuje <xref:System.Xml.XPath.XPathNavigator.Matches%2A> metoda k určení, jestli odpovídá uzlu výraz XPath. <xref:System.Xml.XPath.XPathNavigator.Matches%2A> Metoda přebírá výraz XPath jako vstup a vrátí <xref:System.Boolean> určující, jestli aktuální uzel odpovídá dané výraz XPath nebo zadané kompilované <xref:System.Xml.XPath.XPathExpression> objektu.  
  
## <a name="matching-nodes"></a>Odpovídající uzly  
 <xref:System.Xml.XPath.XPathNavigator.Matches%2A> Metoda vrátí `true` Pokud aktuálního uzlu odpovídá zadán výraz XPath. Například v příkladu kódu, který následuje <xref:System.Xml.XPath.XPathNavigator.Matches%2A> metoda vrátí `true` Pokud je aktuální uzel elementu `b`a element `b` má atribut `c`.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Zpracování kódu XML dat pomocí jazyka XPath datový Model](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Vyberte pomocí objektem XPathNavigator nastaveným na Data XML](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [Vyhodnocení výrazů jazyka XPath pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [Typy uzlů rozpoznána s dotazy XPath](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [Dotazy XPath a obory názvů](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [Výrazy kompilované XPath](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
