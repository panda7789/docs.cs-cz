---
title: Vyhodnocení výrazů XPath pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2913ccf3-f932-4363-8028-9e2d22ce6093
ms.openlocfilehash: b6e18fe02a828ae307ac7ade15650d3303f2600c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287802"
---
# <a name="evaluate-xpath-expressions-using-xpathnavigator"></a>Vyhodnocení výrazů XPath pomocí XPathNavigator
<xref:System.Xml.XPath.XPathNavigator>Třída poskytuje <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metodu pro vyhodnocení výrazu XPath. <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>Metoda přebírá výraz XPath, vyhodnocuje ho a vrací typ XPath typu Boolean, Number, String nebo Node v závislosti na výsledku výrazu XPath.  
  
## <a name="the-evaluate-method"></a>Metoda Evaluate  
 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>Metoda přebírá výraz XPath, vyhodnocuje ho a vrátí typový výsledek Boolean ( <xref:System.Boolean> ), Number ( <xref:System.Double> ), String ( <xref:System.String> ) nebo set Node ( <xref:System.Xml.XPath.XPathNodeIterator> ). Například <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metoda může být použita v matematické metodě. Následující příklad kódu vypočítá celkovou cenu ze všech knih v `books.xml` souboru.  
  
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
  
 Příklad přebírá `books.xml` soubor jako vstup.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="position-and-last-functions"></a>pozice a poslední funkce  
 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>Metoda je přetížena. Jedna z <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metod přebírá <xref:System.Xml.XPath.XPathNodeIterator> objekt jako parametr. Tato konkrétní <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Metoda je shodná s <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metodou, která <xref:System.Xml.XPath.XPathExpression> jako parametr přijímá pouze objekt, s tím rozdílem, že umožňuje argumentu sady uzlů určit aktuální kontext k provedení vyhodnocení. Tento kontext je vyžadován pro výraz XPath `position()` a `last()` funkce, protože jsou relativní vzhledem k aktuálnímu uzlu kontextu. Pokud není použit jako predikát v kroku umístění, `position()` `last()` funkce a vyžadují odkaz na uzel sady, aby bylo možné je vyhodnotit jinak, `position` `last` funkce a vrátí `0` .  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Zpracování dat XML pomocí modelu dat XPath](process-xml-data-using-the-xpath-data-model.md)
- [Výběr dat XML pomocí XPathNavigator](select-xml-data-using-xpathnavigator.md)
- [Párování uzlů pomocí XPathNavigator](matching-nodes-using-xpathnavigator.md)
- [Rozpoznané typy uzlů s dotazy XPath](node-types-recognized-with-xpath-queries.md)
- [Dotazy a obory názvů XPath](xpath-queries-and-namespaces.md)
- [Zkompilované výrazy XPath](compiled-xpath-expressions.md)
