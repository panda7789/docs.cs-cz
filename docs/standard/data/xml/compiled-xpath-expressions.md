---
title: Výrazy kompilované XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e25dd95f-b64c-4d8b-a3a4-379e1aa0ad55
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 80bee210b12c588163a3e11dfdab4dadda9ec0c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573799"
---
# <a name="compiled-xpath-expressions"></a>Výrazy kompilované XPath
<xref:System.Xml.XPath.XPathExpression> Objekt představuje kompilovaném dotazu XPath vrácených buď statických <xref:System.Xml.XPath.XPathExpression.Compile%2A> metodu <xref:System.Xml.XPath.XPathExpression> – třída nebo <xref:System.Xml.XPath.XPathNavigator.Compile%2A> metodu <xref:System.Xml.XPath.XPathNavigator> třídy.  
  
## <a name="the-xpathexpression-class"></a>XPathExpression – třída  
 Dotaz XPath reprezentována zkompilovat A <xref:System.Xml.XPath.XPathExpression> objektu je užitečné, pokud stejný dotaz XPath se používá více než jednou.  
  
 Například při volání metody <xref:System.Xml.XPath.XPathNavigator.Select%2A> metoda vícekrát, místo použití řetězec představující dotaz XPath pokaždé, když, použít <xref:System.Xml.XPath.XPathExpression.Compile%2A> metodu <xref:System.Xml.XPath.XPathExpression> – třída nebo <xref:System.Xml.XPath.XPathNavigator.Compile%2A> metodu <xref:System.Xml.XPath.XPathNavigator> třídy pro kompilaci a dotaz XPath v mezipaměti <xref:System.Xml.XPath.XPathExpression> objekt pro opakované použití a lepší výkon.  
  
 Jednou kompilovat, <xref:System.Xml.XPath.XPathExpression> objektu může být použita jako vstup pro následující <xref:System.Xml.XPath.XPathNavigator> metody třídy v závislosti na typu vrácená z dotazu XPath.  
  
-   <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Matches%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 Následující tabulka popisuje všechny návratové typy W3C XPath, jejich vztahů rozhraní Microsoft .NET Framework a co metody <xref:System.Xml.XPath.XPathExpression> objektu může být použit s podle její návratový typ.  
  
|W3C XPath návratový typ|Ekvivalentní typ rozhraní .NET framework|Popis|Metody|  
|---------------------------|------------------------------------|-----------------|-------------|  
|`Node set`|<xref:System.Xml.XPath.XPathNodeIterator>|Neseřazený kolekce uzlů bez duplicitní položky vytvořené v pořadí dokumentů.|<xref:System.Xml.XPath.XPathNavigator.Select%2A> Nebo <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`Boolean`|<xref:System.Boolean>|A `true` nebo `false` hodnotu.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Nebo<br /><br /> <xref:System.Xml.XPath.XPathNavigator.Matches%2A>|  
|`Number`|<xref:System.Double>|Číslo s plovoucí desetinnou čárkou.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`String`|<xref:System.String>|Posloupnosti znaků UCS.|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator.Matches%2A> Metoda přijímá výraz XPath jako jeho parametr. <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> Metoda vrátí <xref:System.Xml.XPath.XPathNavigator> objektu není jednou z návratové typy W3C XPath.  
  
### <a name="the-returntype-property"></a>Vlastnost ReturnType  
 Po XPath byl zkompilován dotaz do <xref:System.Xml.XPath.XPathExpression> objekt, můžete použít <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> vlastnost <xref:System.Xml.XPath.XPathExpression> objektem pro určení, co vrátí dotaz XPath.  
  
 <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> Vlastnost vrací jednu z následujících <xref:System.Xml.XPath.XPathResultType> hodnot výčtu představující W3C XPath návratové typy.  
  
-   <xref:System.Xml.XPath.XPathResultType.Any>  
  
-   <xref:System.Xml.XPath.XPathResultType.Boolean>  
  
-   <xref:System.Xml.XPath.XPathResultType.Error>  
  
-   <xref:System.Xml.XPath.XPathResultType.Navigator>  
  
-   <xref:System.Xml.XPath.XPathResultType.NodeSet>  
  
-   <xref:System.Xml.XPath.XPathResultType.Number>  
  
-   <xref:System.Xml.XPath.XPathResultType.String>  
  
 Následující příklad používá <xref:System.Xml.XPath.XPathExpression> objekt vrátí číslo a nastavení z uzlu `books.xml` souboru. <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> Vlastnost jednotlivých <xref:System.Xml.XPath.XPathExpression> objektu a také výsledků <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> a <xref:System.Xml.XPath.XPathNavigator.Select%2A> metody se zapisují do konzoly.  
  
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
  
 V příkladu trvá `books.xml` souboru jako vstup.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="higher-performance-xpath-expressions"></a>Vyšší výkon výrazech XPath  
 Pro lepší výkon použijte nejvíce výraz XPath, která je možné v dotazech. Například pokud `book` uzel je podřízený uzel `bookstore` uzlu a `bookstore` uzel je nejvyšší element v dokumentu XML pomocí výraz XPath `/bookstore/book` je rychlejší než při použití `//book`. `//book` Výraz XPath bude kontrolovat každý uzel ve stromové struktuře XML k identifikaci odpovídající uzly.  
  
 Kromě toho pomocí uzlu nastavit navigační metody poskytl <xref:System.Xml.XPath.XPathNavigator> – třída může mít za následek vylepšení výkonu prostřednictvím metody výběru poskytl <xref:System.Xml.XPath.XPathNavigator> třídy v případech, kdy jsou jednoduché kritériím výběru. Například pokud je nutné vybrat prvního podřízeného člena na aktuální uzel, je rychlejší použít <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> než k použijte `child::*[1]` výraz XPath a <xref:System.Xml.XPath.XPathNavigator.Select%2A> metoda.  
  
 Další informace o uzlu nastavit metody navigace <xref:System.Xml.XPath.XPathNavigator> třídy najdete v tématu [uzlu nastavit navigační pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Výběr dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [Vyhodnocení výrazů XPath pomocí XPathNavigator](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [Párování uzlů pomocí XPathNavigator](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [Rozpoznané typy uzlů s dotazy XPath](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [Dotazy XPath a obory názvů](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
