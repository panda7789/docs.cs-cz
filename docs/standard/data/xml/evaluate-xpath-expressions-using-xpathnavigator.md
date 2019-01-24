---
title: Vyhodnocení výrazů XPath pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2913ccf3-f932-4363-8028-9e2d22ce6093
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b8666aa9cb9f0512c600a77891b16f439c46995a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517406"
---
# <a name="evaluate-xpath-expressions-using-xpathnavigator"></a>Vyhodnocení výrazů XPath pomocí XPathNavigator
<xref:System.Xml.XPath.XPathNavigator> Třída poskytuje <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metodu pro vyhodnocení výrazu XPath. <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Metoda má výraz XPath, se vyhodnotí a vrátí W3C XPath typu logická hodnota, číslo, řetězec nebo sada uzlů na základě výsledku výrazu XPath.  
  
## <a name="the-evaluate-method"></a>Vyhodnocení metody  
 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Metoda má výraz XPath, se vyhodnotí a vrátí zadaný výsledek logickou hodnotu (<xref:System.Boolean>), počet (<xref:System.Double>), řetězec (<xref:System.String>), nebo sada uzlů (<xref:System.Xml.XPath.XPathNodeIterator>). Například <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metodu lze použít v matematické metodě. Následující příklad kódu vypočítá celková cena všech knih v `books.xml` souboru.  
  
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
  
 V příkladu přebírá `books.xml` souboru jako vstup.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="position-and-last-functions"></a>pozice a poslední funkce  
 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Přetížené metody. Jeden z <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> přebírá metody <xref:System.Xml.XPath.XPathNodeIterator> objektu jako parametr. Tento konkrétní <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metodou je stejný jako <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metodu, která přebírá pouze <xref:System.Xml.XPath.XPathExpression> objektu jako parametr, s tím rozdílem, že umožňuje uzel nastavení argumentu pro zadání pro provedení vyhodnocení na aktuální kontext. Je vyžadován pro cestu XPath tento kontext `position()` a `last()` funkce jsou relativní vzhledem k aktuální uzel kontextu. Není-li použít jako predikát v kroku umístění, `position()` a `last()` funkce vyžadují odkaz na uzel nastavení, aby se vyhodnotilo, jinak `position` a `last` funkce vrátit `0`.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Výběr dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [Párování uzlů pomocí XPathNavigator](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [Rozpoznané typy uzlů s dotazy XPath](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [Dotazy XPath a obory názvů](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [Zkompilované výrazy XPath](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
