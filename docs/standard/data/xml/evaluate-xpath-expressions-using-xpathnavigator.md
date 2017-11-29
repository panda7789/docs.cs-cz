---
title: "Vyhodnocení výrazů jazyka XPath pomocí objektem XPathNavigator nastaveným na"
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
ms.assetid: 2913ccf3-f932-4363-8028-9e2d22ce6093
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3d513f48155a582a5158cccdd682f5b8485caefd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="evaluate-xpath-expressions-using-xpathnavigator"></a>Vyhodnocení výrazů jazyka XPath pomocí objektem XPathNavigator nastaveným na
<xref:System.Xml.XPath.XPathNavigator> Třída poskytuje <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metody k vyhodnocení výrazu XPath. <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Metoda přebírá výraz XPath, vyhodnotí ji a vrátí typ W3C XPath logická hodnota, čísla, řetězce nebo sada uzlů na základě výsledku výrazu XPath.  
  
## <a name="the-evaluate-method"></a>Vyhodnocení metody  
 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Metoda přebírá výraz XPath, vyhodnotí ji a vrátí zadaný výsledek logická hodnota (<xref:System.Boolean>), čísla (<xref:System.Double>), řetězec (<xref:System.String>), nebo sada uzlů (<xref:System.Xml.XPath.XPathNodeIterator>). Například <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metodu lze použít v matematickém metoda. Následující příklad kódu vypočítá celková cena všech knih v `books.xml` souboru.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
Dim query As XPathExpression = navigator.Compile("sum(//price/text())")  
Dim total As Double = CType(navigator.Evaluate(query), Double)  
Console.WriteLine(total)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
XPathExpression query = navigator.Compile("sum(//price/text())");  
Double total = (Double)navigator.Evaluate(query);  
Console.WriteLine(total);  
```  
  
 V příkladu trvá `books.xml` souboru jako vstup.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="position-and-last-functions"></a>pozice a poslední funkce  
 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Metoda je přetížena. Jeden z <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> trvá metody <xref:System.Xml.XPath.XPathNodeIterator> objektu jako parametr. Tato konkrétní <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metoda je stejná jako <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metody, která přijímá pouze <xref:System.Xml.XPath.XPathExpression> objektu jako parametr, s tím rozdílem, že umožňuje uzlu nastavit ke specifikaci aktuální kontext k vyhodnocení plnění. Tento kontext se vyžaduje pro cestu XPath `position()` a `last()` funkce, jako jsou relativní vzhledem k uzlu aktuálního kontextu. Není-li použít jako predikát v kroku umístění, `position()` a `last()` funkce vyžadují odkaz na uzlu nastavit, aby se vyhodnotilo, jinak hodnota `position` a `last` funkce vrátí `0`.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Zpracování kódu XML dat pomocí jazyka XPath datový Model](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Vyberte pomocí objektem XPathNavigator nastaveným na Data XML](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [Odpovídající pomocí objektem XPathNavigator nastaveným na uzly](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [Typy uzlů rozpoznána s dotazy XPath](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [Dotazy XPath a obory názvů](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [Výrazy kompilované XPath](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
