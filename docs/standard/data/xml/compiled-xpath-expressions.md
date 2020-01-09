---
title: Zkompilované výrazy XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e25dd95f-b64c-4d8b-a3a4-379e1aa0ad55
ms.openlocfilehash: b4675765849299050eb6cddeaaa497bc6cdc620a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711100"
---
# <a name="compiled-xpath-expressions"></a>Zkompilované výrazy XPath
Objekt <xref:System.Xml.XPath.XPathExpression> představuje kompilovaný dotaz XPath vrácený buď metodou static <xref:System.Xml.XPath.XPathExpression.Compile%2A> třídy <xref:System.Xml.XPath.XPathExpression>, nebo metodou <xref:System.Xml.XPath.XPathNavigator.Compile%2A> třídy <xref:System.Xml.XPath.XPathNavigator>.  
  
## <a name="the-xpathexpression-class"></a>Třída XPathExpression  
 Kompilovaný dotaz XPath reprezentovaný objektem <xref:System.Xml.XPath.XPathExpression> je užitečný, pokud je stejný dotaz XPath použit více než jednou.  
  
 Například při volání metody <xref:System.Xml.XPath.XPathNavigator.Select%2A> několikrát, namísto použití řetězce představujícího dotaz XPath pokaždé, použijte metodu <xref:System.Xml.XPath.XPathExpression.Compile%2A> třídy <xref:System.Xml.XPath.XPathExpression> nebo metodu <xref:System.Xml.XPath.XPathNavigator.Compile%2A> třídy <xref:System.Xml.XPath.XPathNavigator> pro zkompilování a ukládání do mezipaměti v objektu <xref:System.Xml.XPath.XPathExpression> pro opakované použití a zlepšení výkonu.  
  
 Po kompilaci lze objekt <xref:System.Xml.XPath.XPathExpression> použít jako vstup do následujících metod <xref:System.Xml.XPath.XPathNavigator> třídy v závislosti na typu vráceném z dotazu XPath.  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Matches%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 Následující tabulka popisuje všechny návratové typy XPath W3C, jejich Microsoft .NET Framework equivalencies a jaké metody lze použít pro <xref:System.Xml.XPath.XPathExpression> objekt v závislosti na jeho návratovém typu.  
  
|Návratový typ XPath W3C|.NET Framework ekvivalentní typ|Popis|Metody|  
|---------------------------|------------------------------------|-----------------|-------------|  
|`Node set`|<xref:System.Xml.XPath.XPathNodeIterator>|Neuspořádaná kolekce uzlů bez duplicit vytvořených v pořadí dokumentů.|<xref:System.Xml.XPath.XPathNavigator.Select%2A> Nebo <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`Boolean`|<xref:System.Boolean>|Hodnota `true` nebo `false`|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> nebo<br /><br /> <xref:System.Xml.XPath.XPathNavigator.Matches%2A>|  
|`Number`|<xref:System.Double>|Číslo s plovoucí desetinnou čárkou.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`String`|<xref:System.String>|Posloupnost znaků UCS.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
  
> [!NOTE]
> Metoda <xref:System.Xml.XPath.XPathNavigator.Matches%2A> přijímá jako svůj parametr výraz XPath. Metoda <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> vrátí objekt <xref:System.Xml.XPath.XPathNavigator>, nikoli jeden z návratových typů XPath W3C.  
  
### <a name="the-returntype-property"></a>Vlastnost ReturnType  
 Po zkompilování dotazu XPath do objektu <xref:System.Xml.XPath.XPathExpression> lze pomocí vlastnosti <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> objektu <xref:System.Xml.XPath.XPathExpression> určit, co dotaz XPath vrátí.  
  
 Vlastnost <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> vrací jednu z následujících <xref:System.Xml.XPath.XPathResultType> hodnot výčtu představujících návratové typy XPath W3C.  
  
- <xref:System.Xml.XPath.XPathResultType.Any>  
  
- <xref:System.Xml.XPath.XPathResultType.Boolean>  
  
- <xref:System.Xml.XPath.XPathResultType.Error>  
  
- <xref:System.Xml.XPath.XPathResultType.Navigator>  
  
- <xref:System.Xml.XPath.XPathResultType.NodeSet>  
  
- <xref:System.Xml.XPath.XPathResultType.Number>  
  
- <xref:System.Xml.XPath.XPathResultType.String>  
  
 Následující příklad používá objekt <xref:System.Xml.XPath.XPathExpression> k vrácení čísla a sady uzlů ze souboru `books.xml`. Do konzoly je zapsána vlastnost <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> každého objektu <xref:System.Xml.XPath.XPathExpression> a výsledky z <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> a metody <xref:System.Xml.XPath.XPathNavigator.Select%2A>.  
  
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
  
 V příkladu se jako vstup používá soubor `books.xml`.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="higher-performance-xpath-expressions"></a>Výrazy XPath s vyšším výkonem  
 Pro lepší výkon použijte ve svých dotazech nejvíce konkrétní výraz XPath. Například pokud uzel `book` je podřízený uzel uzlu `bookstore` a `bookstore` uzel je nejvyšší prvek v dokumentu XML, použití `/bookstore/book` výrazu XPath je rychlejší než použití `//book`. `//book` výraz XPath zkontroluje každý uzel ve stromu XML a určí tak vyhovující uzly.  
  
 Kromě toho může použití metod navigace v uzlu, které poskytuje třída <xref:System.Xml.XPath.XPathNavigator>, způsobit lepší výkon přes metody výběru poskytované <xref:System.Xml.XPath.XPathNavigator> třídy v případech, kdy jsou kritéria výběru jednoduchá. Například pokud potřebujete vybrat první podřízenou položku aktuálního uzlu, je rychlejší použít metodu <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> než použití `child::*[1]` výrazu XPath a metody <xref:System.Xml.XPath.XPathNavigator.Select%2A>.  
  
 Další informace o tom, jak uzel nastavuje navigační metody třídy <xref:System.Xml.XPath.XPathNavigator>, najdete v tématu věnovaném [navigaci v uzlech pomocí XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md).  
  
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
