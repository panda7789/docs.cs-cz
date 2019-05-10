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
ms.openlocfilehash: a75534bdfb1eef5902d3cd5071b4f5b4bfba8caa
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647957"
---
# <a name="compiled-xpath-expressions"></a>Zkompilované výrazy XPath
<xref:System.Xml.XPath.XPathExpression> Objekt představuje zkompilovaný dotaz XPath vrácený buď statické <xref:System.Xml.XPath.XPathExpression.Compile%2A> metodu <xref:System.Xml.XPath.XPathExpression> třídy nebo <xref:System.Xml.XPath.XPathNavigator.Compile%2A> metodu <xref:System.Xml.XPath.XPathNavigator> třídy.  
  
## <a name="the-xpathexpression-class"></a>Třída XPathExpression  
 Dotaz XPath reprezentována zkompilován A <xref:System.Xml.XPath.XPathExpression> objektu je užitečné, pokud se stejný dotaz XPath používá více než jednou.  
  
 Například při volání <xref:System.Xml.XPath.XPathNavigator.Select%2A> metoda více než jednou, namísto použití řetězec představující pokaždé, když dotaz XPath, použijte <xref:System.Xml.XPath.XPathExpression.Compile%2A> metodu <xref:System.Xml.XPath.XPathExpression> třídy nebo <xref:System.Xml.XPath.XPathNavigator.Compile%2A> metodu <xref:System.Xml.XPath.XPathNavigator> třídy pro kompilaci a dotaz XPath v mezipaměti <xref:System.Xml.XPath.XPathExpression> objekt pro opakované použití a vylepšení výkonu.  
  
 Po kompilaci, <xref:System.Xml.XPath.XPathExpression> objektu mohou být použity jako vstup pro následující <xref:System.Xml.XPath.XPathNavigator> metody třídy v závislosti na typu vrácená z dotazu XPath.  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Matches%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 Následující tabulka popisuje každý návratové typy W3C XPath, jejich vztahů rozhraní Microsoft .NET Framework a jaké metody <xref:System.Xml.XPath.XPathExpression> objekt může být použit s podle jejího návratového typu.  
  
|XPath návratový typ W3C|Ekvivalentní typ rozhraní .NET framework|Popis|Metody|  
|---------------------------|------------------------------------|-----------------|-------------|  
|`Node set`|<xref:System.Xml.XPath.XPathNodeIterator>|Neseřazený kolekce uzlů bez duplicitní položky vytvořené v pořadí dokumentů.|<xref:System.Xml.XPath.XPathNavigator.Select%2A> Nebo <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`Boolean`|<xref:System.Boolean>|A `true` nebo `false` hodnotu.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Nebo<br /><br /> <xref:System.Xml.XPath.XPathNavigator.Matches%2A>|  
|`Number`|<xref:System.Double>|Číslo s plovoucí desetinnou čárkou.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`String`|<xref:System.String>|Posloupnost znaků UCS.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator.Matches%2A> Metoda přijímá jako svůj parametr pomocí výrazu XPath. <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> Vrátí metoda <xref:System.Xml.XPath.XPathNavigator> objektu, není jednou z návratové typy W3C XPath.  
  
### <a name="the-returntype-property"></a>Vlastnost ReturnType  
 Po XPath byl zkompilován dotaz do <xref:System.Xml.XPath.XPathExpression> objektu, můžete použít <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> vlastnost <xref:System.Xml.XPath.XPathExpression> zjistíte, co vrátí dotaz XPath.  
  
 <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> Vlastnost vrátí jednu z následujících <xref:System.Xml.XPath.XPathResultType> hodnot výčtu představující W3C XPath návratové typy.  
  
- <xref:System.Xml.XPath.XPathResultType.Any>  
  
- <xref:System.Xml.XPath.XPathResultType.Boolean>  
  
- <xref:System.Xml.XPath.XPathResultType.Error>  
  
- <xref:System.Xml.XPath.XPathResultType.Navigator>  
  
- <xref:System.Xml.XPath.XPathResultType.NodeSet>  
  
- <xref:System.Xml.XPath.XPathResultType.Number>  
  
- <xref:System.Xml.XPath.XPathResultType.String>  
  
 V následujícím příkladu <xref:System.Xml.XPath.XPathExpression> objekt vrátí číslo a nastavení z uzlu `books.xml` souboru. <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> Vlastnosti každého <xref:System.Xml.XPath.XPathExpression> objektu a také výsledky z <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> a <xref:System.Xml.XPath.XPathNavigator.Select%2A> metody jsou zapsány do konzoly.  
  
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
  
 V příkladu přebírá `books.xml` souboru jako vstup.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="higher-performance-xpath-expressions"></a>Vyšší výkon výrazy XPath  
 Pro lepší výkon pomocí nejspecifičtější výraz XPath, je to možné v dotazech. Například pokud `book` podřízený uzel je uzel `bookstore` uzlu a `bookstore` je nejvyšší element v dokumentu XML, pomocí výrazu XPath uzel `/bookstore/book` je rychlejší než použití `//book`. `//book` Výraz XPath bude kontrolovat každý uzel ve stromu XML k určení odpovídající uzly.  
  
 Kromě, pomocí uzlu nastavit navigační metody poskytnuté <xref:System.Xml.XPath.XPathNavigator> třída může vést k vylepšení výkonu prostřednictvím výběr metod poskytovaných <xref:System.Xml.XPath.XPathNavigator> třídy v případech, kdy jsou jednoduché kritéria pro výběr. Například, pokud je potřeba vybrat prvního podřízeného člena aktuální uzel, je rychlejší použít <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> metodu než `child::*[1]` výraz XPath a <xref:System.Xml.XPath.XPathNavigator.Select%2A> metoda.  
  
 Další informace o uzlu sady metody navigace <xref:System.Xml.XPath.XPathNavigator> najdete v tématu [uzlu nastavení navigace pomocí XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md).  
  
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
