---
title: Vyhodnocení výrazů jazyka XPath pomocí objektem XPathNavigator nastaveným na
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2913ccf3-f932-4363-8028-9e2d22ce6093
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6dce97fd74b17154925d18bf18a9a8defd2e508e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
 [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Výběr dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [Párování uzlů pomocí XPathNavigator](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [Rozpoznané typy uzlů s dotazy XPath](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [Dotazy XPath a obory názvů](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [Zkompilované výrazy XPath](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
