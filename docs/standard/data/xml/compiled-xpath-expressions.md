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
# <a name="compiled-xpath-expressions"></a><span data-ttu-id="ccf82-102">Zkompilované výrazy XPath</span><span class="sxs-lookup"><span data-stu-id="ccf82-102">Compiled XPath Expressions</span></span>
<span data-ttu-id="ccf82-103"><xref:System.Xml.XPath.XPathExpression> <xref:System.Xml.XPath.XPathExpression.Compile%2A> <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathNavigator.Compile%2A> Objekt představuje kompilovaný dotaz XPath vrácený buď statickou metodou třídy, nebo metodou třídy. <xref:System.Xml.XPath.XPathExpression></span><span class="sxs-lookup"><span data-stu-id="ccf82-103">An <xref:System.Xml.XPath.XPathExpression> object represents a compiled XPath query returned from either the static <xref:System.Xml.XPath.XPathExpression.Compile%2A> method of the <xref:System.Xml.XPath.XPathExpression> class or the <xref:System.Xml.XPath.XPathNavigator.Compile%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="the-xpathexpression-class"></a><span data-ttu-id="ccf82-104">Třída XPathExpression</span><span class="sxs-lookup"><span data-stu-id="ccf82-104">The XPathExpression Class</span></span>  
 <span data-ttu-id="ccf82-105">Kompilovaný dotaz XPath reprezentovaný <xref:System.Xml.XPath.XPathExpression> objektem je užitečný, pokud je stejný dotaz XPath použit více než jednou.</span><span class="sxs-lookup"><span data-stu-id="ccf82-105">A compiled XPath query represented by an <xref:System.Xml.XPath.XPathExpression> object is useful if the same XPath query is being used more than once.</span></span>  
  
 <span data-ttu-id="ccf82-106">Například <xref:System.Xml.XPath.XPathNavigator.Select%2A> při volání metody víckrát namísto použití řetězce představujícího dotaz XPath pokaždé, <xref:System.Xml.XPath.XPathExpression> <xref:System.Xml.XPath.XPathExpression.Compile%2A> použijte metodu třídy nebo <xref:System.Xml.XPath.XPathNavigator.Compile%2A> metodu <xref:System.Xml.XPath.XPathNavigator> třídy pro zkompilování a ukládat do mezipaměti dotaz XPath v <xref:System.Xml.XPath.XPathExpression> objektu pro opakované použití a zlepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="ccf82-106">For example, when calling the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method multiple times, instead of using a string representing the XPath query each time, use the <xref:System.Xml.XPath.XPathExpression.Compile%2A> method of the <xref:System.Xml.XPath.XPathExpression> class or the <xref:System.Xml.XPath.XPathNavigator.Compile%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class to compile and cache the XPath query in an <xref:System.Xml.XPath.XPathExpression> object for reuse and improved performance.</span></span>  
  
 <span data-ttu-id="ccf82-107">Po kompilaci <xref:System.Xml.XPath.XPathExpression> lze objekt použít jako vstup do následujících <xref:System.Xml.XPath.XPathNavigator> metod třídy v závislosti na typu vráceném z dotazu XPath.</span><span class="sxs-lookup"><span data-stu-id="ccf82-107">Once compiled, the <xref:System.Xml.XPath.XPathExpression> object may be used as input to the following <xref:System.Xml.XPath.XPathNavigator> class methods depending on the type returned from the XPath query.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Matches%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 <span data-ttu-id="ccf82-108">V následující tabulce jsou popsány všechny návratové typy XPath W3C, jejich Microsoft .NET Framework equivalencies a jaké metody <xref:System.Xml.XPath.XPathExpression> lze použít pro objekt na základě jeho návratového typu.</span><span class="sxs-lookup"><span data-stu-id="ccf82-108">The following table describes each of the W3C XPath return types, their Microsoft .NET Framework equivalencies, and what methods the <xref:System.Xml.XPath.XPathExpression> object may be used with based on its return type.</span></span>  
  
|<span data-ttu-id="ccf82-109">Návratový typ XPath W3C</span><span class="sxs-lookup"><span data-stu-id="ccf82-109">W3C XPath Return Type</span></span>|<span data-ttu-id="ccf82-110">.NET Framework ekvivalentní typ</span><span class="sxs-lookup"><span data-stu-id="ccf82-110">.NET Framework Equivalent Type</span></span>|<span data-ttu-id="ccf82-111">Popis</span><span class="sxs-lookup"><span data-stu-id="ccf82-111">Description</span></span>|<span data-ttu-id="ccf82-112">Metody</span><span class="sxs-lookup"><span data-stu-id="ccf82-112">Methods</span></span>|  
|---------------------------|------------------------------------|-----------------|-------------|  
|`Node set`|<xref:System.Xml.XPath.XPathNodeIterator>|<span data-ttu-id="ccf82-113">Neuspořádaná kolekce uzlů bez duplicit vytvořených v pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="ccf82-113">An unordered collection of nodes without duplicates created in document order.</span></span>|<span data-ttu-id="ccf82-114"><xref:System.Xml.XPath.XPathNavigator.Select%2A> Nebo <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A></span><span class="sxs-lookup"><span data-stu-id="ccf82-114"><xref:System.Xml.XPath.XPathNavigator.Select%2A> or <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A></span></span>|  
|`Boolean`|<xref:System.Boolean>|<span data-ttu-id="ccf82-115">Hodnota `true` nebo `false` .</span><span class="sxs-lookup"><span data-stu-id="ccf82-115">A `true` or `false` value.</span></span>|<span data-ttu-id="ccf82-116"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>ani</span><span class="sxs-lookup"><span data-stu-id="ccf82-116"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> or</span></span><br /><br /> <xref:System.Xml.XPath.XPathNavigator.Matches%2A>|  
|`Number`|<xref:System.Double>|<span data-ttu-id="ccf82-117">Číslo s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="ccf82-117">A floating-point number.</span></span>|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`String`|<xref:System.String>|<span data-ttu-id="ccf82-118">Posloupnost znaků UCS.</span><span class="sxs-lookup"><span data-stu-id="ccf82-118">A sequence of UCS characters.</span></span>|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
  
> [!NOTE]
> <span data-ttu-id="ccf82-119"><xref:System.Xml.XPath.XPathNavigator.Matches%2A> Metoda přijímá výraz XPath jako svůj parametr.</span><span class="sxs-lookup"><span data-stu-id="ccf82-119">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method accepts an XPath expression as its parameter.</span></span> <span data-ttu-id="ccf82-120"><xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> Metoda<xref:System.Xml.XPath.XPathNavigator> vrátí objekt, nikoli jeden z návratových typů XPath W3C.</span><span class="sxs-lookup"><span data-stu-id="ccf82-120">The <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> method returns an <xref:System.Xml.XPath.XPathNavigator> object, not one of the W3C XPath return types.</span></span>  
  
### <a name="the-returntype-property"></a><span data-ttu-id="ccf82-121">Vlastnost ReturnType</span><span class="sxs-lookup"><span data-stu-id="ccf82-121">The ReturnType Property</span></span>  
 <span data-ttu-id="ccf82-122">Poté, co byl dotaz XPath zkompilován do <xref:System.Xml.XPath.XPathExpression> objektu, můžete <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> použít vlastnost <xref:System.Xml.XPath.XPathExpression> objektu k určení, co dotaz XPath vrátí.</span><span class="sxs-lookup"><span data-stu-id="ccf82-122">After an XPath query has been compiled into an <xref:System.Xml.XPath.XPathExpression> object, you can use the <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property of the <xref:System.Xml.XPath.XPathExpression> object to determine what the XPath query returns.</span></span>  
  
 <span data-ttu-id="ccf82-123">Vlastnost vrací jednu z následujících <xref:System.Xml.XPath.XPathResultType> hodnot výčtu reprezentujících návratové typy XPath W3C. <xref:System.Xml.XPath.XPathExpression.ReturnType%2A></span><span class="sxs-lookup"><span data-stu-id="ccf82-123">The <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property returns one of the following <xref:System.Xml.XPath.XPathResultType> enumeration values representing the W3C XPath return types.</span></span>  
  
- <xref:System.Xml.XPath.XPathResultType.Any>  
  
- <xref:System.Xml.XPath.XPathResultType.Boolean>  
  
- <xref:System.Xml.XPath.XPathResultType.Error>  
  
- <xref:System.Xml.XPath.XPathResultType.Navigator>  
  
- <xref:System.Xml.XPath.XPathResultType.NodeSet>  
  
- <xref:System.Xml.XPath.XPathResultType.Number>  
  
- <xref:System.Xml.XPath.XPathResultType.String>  
  
 <span data-ttu-id="ccf82-124">Následující příklad používá <xref:System.Xml.XPath.XPathExpression> objekt k vrácení čísla a sady uzlů `books.xml` ze souboru.</span><span class="sxs-lookup"><span data-stu-id="ccf82-124">The following example uses the <xref:System.Xml.XPath.XPathExpression> object to return a number and a node set from the `books.xml` file.</span></span> <span data-ttu-id="ccf82-125">Vlastnost každého <xref:System.Xml.XPath.XPathExpression> objektu i výsledky z <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metod a <xref:System.Xml.XPath.XPathNavigator.Select%2A> jsou zapsány do konzoly. <xref:System.Xml.XPath.XPathExpression.ReturnType%2A></span><span class="sxs-lookup"><span data-stu-id="ccf82-125">The <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property of each <xref:System.Xml.XPath.XPathExpression> object as well as the results from the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> and <xref:System.Xml.XPath.XPathNavigator.Select%2A> methods are written to the console.</span></span>  
  
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
  
 <span data-ttu-id="ccf82-126">Příklad přebírá `books.xml` soubor jako vstup.</span><span class="sxs-lookup"><span data-stu-id="ccf82-126">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="higher-performance-xpath-expressions"></a><span data-ttu-id="ccf82-127">Výrazy XPath s vyšším výkonem</span><span class="sxs-lookup"><span data-stu-id="ccf82-127">Higher Performance XPath Expressions</span></span>  
 <span data-ttu-id="ccf82-128">Pro lepší výkon použijte ve svých dotazech nejvíce konkrétní výraz XPath.</span><span class="sxs-lookup"><span data-stu-id="ccf82-128">For better performance, use the most specific XPath expression possible in your queries.</span></span> <span data-ttu-id="ccf82-129">Například `book` Pokud uzel je podřízený uzel `bookstore` uzlu a `bookstore` uzel je nejvyšší prvek v dokumentu XML, použití výrazu `/bookstore/book` XPath je rychlejší než použití `//book`.</span><span class="sxs-lookup"><span data-stu-id="ccf82-129">For example, if the `book` node is a child node of the `bookstore` node and the `bookstore` node is the top-most element in an XML document, using the XPath expression `/bookstore/book` is faster than using `//book`.</span></span> <span data-ttu-id="ccf82-130">Výraz `//book` XPath zkontroluje každý uzel ve stromu XML a určí tak vyhovující uzly.</span><span class="sxs-lookup"><span data-stu-id="ccf82-130">The `//book` XPath expression will scan every node in the XML tree to identify matching nodes.</span></span>  
  
 <span data-ttu-id="ccf82-131">Kromě toho může použití metod navigace v uzlu, které poskytuje <xref:System.Xml.XPath.XPathNavigator> třída, způsobit lepší výkon přes metody výběru poskytované <xref:System.Xml.XPath.XPathNavigator> třídou v případech, kde jsou kritéria výběru jednoduchá.</span><span class="sxs-lookup"><span data-stu-id="ccf82-131">Additionally, using the node set navigation methods supplied by the <xref:System.Xml.XPath.XPathNavigator> class may result in improved performance over the selection methods supplied by the <xref:System.Xml.XPath.XPathNavigator> class in cases where your selection criteria are simple.</span></span> <span data-ttu-id="ccf82-132">Například pokud potřebujete vybrat první podřízenou položku aktuálního uzlu, je rychlejší použít <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> metodu než pro `child::*[1]` použití výrazu XPath a <xref:System.Xml.XPath.XPathNavigator.Select%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ccf82-132">For example, if you need to select the first child of the current node, it is faster to use the <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> method than to use the `child::*[1]` XPath expression and the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method.</span></span>  
  
 <span data-ttu-id="ccf82-133">Další informace o tom, jak uzel nastavuje navigační metody <xref:System.Xml.XPath.XPathNavigator> třídy, najdete v tématu věnovaném navigaci v uzlech [pomocí XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="ccf82-133">For more information about the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class, see [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccf82-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ccf82-134">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="ccf82-135">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="ccf82-135">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="ccf82-136">Výběr dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ccf82-136">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="ccf82-137">Vyhodnocení výrazů XPath pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ccf82-137">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="ccf82-138">Párování uzlů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ccf82-138">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="ccf82-139">Rozpoznané typy uzlů s dotazy XPath</span><span class="sxs-lookup"><span data-stu-id="ccf82-139">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="ccf82-140">Dotazy XPath a obory názvů</span><span class="sxs-lookup"><span data-stu-id="ccf82-140">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
