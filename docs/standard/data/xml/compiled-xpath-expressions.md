---
title: Zkompilované výrazy XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e25dd95f-b64c-4d8b-a3a4-379e1aa0ad55
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fb6e3677d79f3131432c3daebeee4d166b5450b2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916664"
---
# <a name="compiled-xpath-expressions"></a>Zkompilované výrazy XPath
<xref:System.Xml.XPath.XPathExpression> <xref:System.Xml.XPath.XPathExpression.Compile%2A> <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathNavigator.Compile%2A> Objekt představuje kompilovaný dotaz XPath vrácený buď statickou metodou třídy, nebo metodou třídy. <xref:System.Xml.XPath.XPathExpression>  
  
## <a name="the-xpathexpression-class"></a>Třída XPathExpression  
 Kompilovaný dotaz XPath reprezentovaný <xref:System.Xml.XPath.XPathExpression> objektem je užitečný, pokud je stejný dotaz XPath použit více než jednou.  
  
 Například <xref:System.Xml.XPath.XPathNavigator.Select%2A> při volání metody víckrát namísto použití řetězce představujícího dotaz XPath pokaždé, <xref:System.Xml.XPath.XPathExpression> <xref:System.Xml.XPath.XPathExpression.Compile%2A> použijte metodu třídy nebo <xref:System.Xml.XPath.XPathNavigator.Compile%2A> metodu <xref:System.Xml.XPath.XPathNavigator> třídy pro zkompilování a ukládat do mezipaměti dotaz XPath v <xref:System.Xml.XPath.XPathExpression> objektu pro opakované použití a zlepšení výkonu.  
  
 Po kompilaci <xref:System.Xml.XPath.XPathExpression> lze objekt použít jako vstup do následujících <xref:System.Xml.XPath.XPathNavigator> metod třídy v závislosti na typu vráceném z dotazu XPath.  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Matches%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 V následující tabulce jsou popsány všechny návratové typy XPath W3C, jejich Microsoft .NET Framework equivalencies a jaké metody <xref:System.Xml.XPath.XPathExpression> lze použít pro objekt na základě jeho návratového typu.  
  
|Návratový typ XPath W3C|.NET Framework ekvivalentní typ|Popis|Metody|  
|---------------------------|------------------------------------|-----------------|-------------|  
|`Node set`|<xref:System.Xml.XPath.XPathNodeIterator>|Neuspořádaná kolekce uzlů bez duplicit vytvořených v pořadí dokumentů.|<xref:System.Xml.XPath.XPathNavigator.Select%2A> Nebo <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`Boolean`|<xref:System.Boolean>|Hodnota `true` nebo `false` .|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>ani<br /><br /> <xref:System.Xml.XPath.XPathNavigator.Matches%2A>|  
|`Number`|<xref:System.Double>|Číslo s plovoucí desetinnou čárkou.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`String`|<xref:System.String>|Posloupnost znaků UCS.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator.Matches%2A> Metoda přijímá výraz XPath jako svůj parametr. <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> Metoda<xref:System.Xml.XPath.XPathNavigator> vrátí objekt, nikoli jeden z návratových typů XPath W3C.  
  
### <a name="the-returntype-property"></a>Vlastnost ReturnType  
 Poté, co byl dotaz XPath zkompilován do <xref:System.Xml.XPath.XPathExpression> objektu, můžete <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> použít vlastnost <xref:System.Xml.XPath.XPathExpression> objektu k určení, co dotaz XPath vrátí.  
  
 Vlastnost vrací jednu z následujících <xref:System.Xml.XPath.XPathResultType> hodnot výčtu reprezentujících návratové typy XPath W3C. <xref:System.Xml.XPath.XPathExpression.ReturnType%2A>  
  
- <xref:System.Xml.XPath.XPathResultType.Any>  
  
- <xref:System.Xml.XPath.XPathResultType.Boolean>  
  
- <xref:System.Xml.XPath.XPathResultType.Error>  
  
- <xref:System.Xml.XPath.XPathResultType.Navigator>  
  
- <xref:System.Xml.XPath.XPathResultType.NodeSet>  
  
- <xref:System.Xml.XPath.XPathResultType.Number>  
  
- <xref:System.Xml.XPath.XPathResultType.String>  
  
 Následující příklad používá <xref:System.Xml.XPath.XPathExpression> objekt k vrácení čísla a sady uzlů `books.xml` ze souboru. Vlastnost každého <xref:System.Xml.XPath.XPathExpression> objektu i výsledky z <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metod a <xref:System.Xml.XPath.XPathNavigator.Select%2A> jsou zapsány do konzoly. <xref:System.Xml.XPath.XPathExpression.ReturnType%2A>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Returns a number.  
Dim query1 As XPathExpression = navigator.Compile("bookstore/book/price/text()*10")  
Console.WriteLine(query1.ReturnType)  
  
Dim number As Double = CType(navigator.Evaluate(query1), Double)  
Console.WriteLine(number)  
  
' Returns a node set.  
Dim query2 As XPathExpression = navigator.Compile("bookstore/book/price")  
Console.WriteLine(query2.ReturnType)  
  
Dim nodes As XPathNodeIterator = navigator.Select(query2)  
nodes.MoveNext()  
Console.WriteLine(nodes.Current.Value)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Returns a number.  
XPathExpression query1 = navigator.Compile("bookstore/book/price/text()*10");  
Console.WriteLine(query1.ReturnType);  
  
Double number = (Double)navigator.Evaluate(query1);  
Console.WriteLine(number);  
  
// Returns a node set.  
XPathExpression query2 = navigator.Compile("bookstore/book/price");  
Console.WriteLine(query2.ReturnType);  
  
XPathNodeIterator nodes = navigator.Select(query2);  
nodes.MoveNext();  
Console.WriteLine(nodes.Current.Value);  
```  
  
 Příklad přebírá `books.xml` soubor jako vstup.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="higher-performance-xpath-expressions"></a>Výrazy XPath s vyšším výkonem  
 Pro lepší výkon použijte ve svých dotazech nejvíce konkrétní výraz XPath. Například `book` Pokud uzel je podřízený uzel `bookstore` uzlu a `bookstore` uzel je nejvyšší prvek v dokumentu XML, použití výrazu `/bookstore/book` XPath je rychlejší než použití `//book`. Výraz `//book` XPath zkontroluje každý uzel ve stromu XML a určí tak vyhovující uzly.  
  
 Kromě toho může použití metod navigace v uzlu, které poskytuje <xref:System.Xml.XPath.XPathNavigator> třída, způsobit lepší výkon přes metody výběru poskytované <xref:System.Xml.XPath.XPathNavigator> třídou v případech, kde jsou kritéria výběru jednoduchá. Například pokud potřebujete vybrat první podřízenou položku aktuálního uzlu, je rychlejší použít <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> metodu než pro `child::*[1]` použití výrazu XPath a <xref:System.Xml.XPath.XPathNavigator.Select%2A> metody.  
  
 Další informace o tom, jak uzel nastavuje navigační metody <xref:System.Xml.XPath.XPathNavigator> třídy, najdete v tématu věnovaném navigaci v uzlech [pomocí XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Výběr dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [Vyhodnocení výrazů XPath pomocí XPathNavigator](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [Párování uzlů pomocí XPathNavigator](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [Rozpoznané typy uzlů s dotazy XPath](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [Dotazy XPath a obory názvů](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
