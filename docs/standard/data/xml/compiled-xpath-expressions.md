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
# <a name="compiled-xpath-expressions"></a><span data-ttu-id="85ce7-102">Zkompilované výrazy XPath</span><span class="sxs-lookup"><span data-stu-id="85ce7-102">Compiled XPath Expressions</span></span>
<span data-ttu-id="85ce7-103">Objekt <xref:System.Xml.XPath.XPathExpression> představuje kompilovaný dotaz XPath vrácený buď metodou static <xref:System.Xml.XPath.XPathExpression.Compile%2A> třídy <xref:System.Xml.XPath.XPathExpression>, nebo metodou <xref:System.Xml.XPath.XPathNavigator.Compile%2A> třídy <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="85ce7-103">An <xref:System.Xml.XPath.XPathExpression> object represents a compiled XPath query returned from either the static <xref:System.Xml.XPath.XPathExpression.Compile%2A> method of the <xref:System.Xml.XPath.XPathExpression> class or the <xref:System.Xml.XPath.XPathNavigator.Compile%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="the-xpathexpression-class"></a><span data-ttu-id="85ce7-104">Třída XPathExpression</span><span class="sxs-lookup"><span data-stu-id="85ce7-104">The XPathExpression Class</span></span>  
 <span data-ttu-id="85ce7-105">Kompilovaný dotaz XPath reprezentovaný objektem <xref:System.Xml.XPath.XPathExpression> je užitečný, pokud je stejný dotaz XPath použit více než jednou.</span><span class="sxs-lookup"><span data-stu-id="85ce7-105">A compiled XPath query represented by an <xref:System.Xml.XPath.XPathExpression> object is useful if the same XPath query is being used more than once.</span></span>  
  
 <span data-ttu-id="85ce7-106">Například při volání metody <xref:System.Xml.XPath.XPathNavigator.Select%2A> několikrát, namísto použití řetězce představujícího dotaz XPath pokaždé, použijte metodu <xref:System.Xml.XPath.XPathExpression.Compile%2A> třídy <xref:System.Xml.XPath.XPathExpression> nebo metodu <xref:System.Xml.XPath.XPathNavigator.Compile%2A> třídy <xref:System.Xml.XPath.XPathNavigator> pro zkompilování a ukládání do mezipaměti v objektu <xref:System.Xml.XPath.XPathExpression> pro opakované použití a zlepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="85ce7-106">For example, when calling the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method multiple times, instead of using a string representing the XPath query each time, use the <xref:System.Xml.XPath.XPathExpression.Compile%2A> method of the <xref:System.Xml.XPath.XPathExpression> class or the <xref:System.Xml.XPath.XPathNavigator.Compile%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class to compile and cache the XPath query in an <xref:System.Xml.XPath.XPathExpression> object for reuse and improved performance.</span></span>  
  
 <span data-ttu-id="85ce7-107">Po kompilaci lze objekt <xref:System.Xml.XPath.XPathExpression> použít jako vstup do následujících metod <xref:System.Xml.XPath.XPathNavigator> třídy v závislosti na typu vráceném z dotazu XPath.</span><span class="sxs-lookup"><span data-stu-id="85ce7-107">Once compiled, the <xref:System.Xml.XPath.XPathExpression> object may be used as input to the following <xref:System.Xml.XPath.XPathNavigator> class methods depending on the type returned from the XPath query.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Matches%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 <span data-ttu-id="85ce7-108">Následující tabulka popisuje všechny návratové typy XPath W3C, jejich Microsoft .NET Framework equivalencies a jaké metody lze použít pro <xref:System.Xml.XPath.XPathExpression> objekt v závislosti na jeho návratovém typu.</span><span class="sxs-lookup"><span data-stu-id="85ce7-108">The following table describes each of the W3C XPath return types, their Microsoft .NET Framework equivalencies, and what methods the <xref:System.Xml.XPath.XPathExpression> object may be used with based on its return type.</span></span>  
  
|<span data-ttu-id="85ce7-109">Návratový typ XPath W3C</span><span class="sxs-lookup"><span data-stu-id="85ce7-109">W3C XPath Return Type</span></span>|<span data-ttu-id="85ce7-110">.NET Framework ekvivalentní typ</span><span class="sxs-lookup"><span data-stu-id="85ce7-110">.NET Framework Equivalent Type</span></span>|<span data-ttu-id="85ce7-111">Popis</span><span class="sxs-lookup"><span data-stu-id="85ce7-111">Description</span></span>|<span data-ttu-id="85ce7-112">Metody</span><span class="sxs-lookup"><span data-stu-id="85ce7-112">Methods</span></span>|  
|---------------------------|------------------------------------|-----------------|-------------|  
|`Node set`|<xref:System.Xml.XPath.XPathNodeIterator>|<span data-ttu-id="85ce7-113">Neuspořádaná kolekce uzlů bez duplicit vytvořených v pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="85ce7-113">An unordered collection of nodes without duplicates created in document order.</span></span>|<span data-ttu-id="85ce7-114"><xref:System.Xml.XPath.XPathNavigator.Select%2A> Nebo <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A></span><span class="sxs-lookup"><span data-stu-id="85ce7-114"><xref:System.Xml.XPath.XPathNavigator.Select%2A> or <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A></span></span>|  
|`Boolean`|<xref:System.Boolean>|<span data-ttu-id="85ce7-115">Hodnota `true` nebo `false`</span><span class="sxs-lookup"><span data-stu-id="85ce7-115">A `true` or `false` value.</span></span>|<span data-ttu-id="85ce7-116"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> nebo</span><span class="sxs-lookup"><span data-stu-id="85ce7-116"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> or</span></span><br /><br /> <xref:System.Xml.XPath.XPathNavigator.Matches%2A>|  
|`Number`|<xref:System.Double>|<span data-ttu-id="85ce7-117">Číslo s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="85ce7-117">A floating-point number.</span></span>|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`String`|<xref:System.String>|<span data-ttu-id="85ce7-118">Posloupnost znaků UCS.</span><span class="sxs-lookup"><span data-stu-id="85ce7-118">A sequence of UCS characters.</span></span>|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
  
> [!NOTE]
> <span data-ttu-id="85ce7-119">Metoda <xref:System.Xml.XPath.XPathNavigator.Matches%2A> přijímá jako svůj parametr výraz XPath.</span><span class="sxs-lookup"><span data-stu-id="85ce7-119">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method accepts an XPath expression as its parameter.</span></span> <span data-ttu-id="85ce7-120">Metoda <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> vrátí objekt <xref:System.Xml.XPath.XPathNavigator>, nikoli jeden z návratových typů XPath W3C.</span><span class="sxs-lookup"><span data-stu-id="85ce7-120">The <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> method returns an <xref:System.Xml.XPath.XPathNavigator> object, not one of the W3C XPath return types.</span></span>  
  
### <a name="the-returntype-property"></a><span data-ttu-id="85ce7-121">Vlastnost ReturnType</span><span class="sxs-lookup"><span data-stu-id="85ce7-121">The ReturnType Property</span></span>  
 <span data-ttu-id="85ce7-122">Po zkompilování dotazu XPath do objektu <xref:System.Xml.XPath.XPathExpression> lze pomocí vlastnosti <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> objektu <xref:System.Xml.XPath.XPathExpression> určit, co dotaz XPath vrátí.</span><span class="sxs-lookup"><span data-stu-id="85ce7-122">After an XPath query has been compiled into an <xref:System.Xml.XPath.XPathExpression> object, you can use the <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property of the <xref:System.Xml.XPath.XPathExpression> object to determine what the XPath query returns.</span></span>  
  
 <span data-ttu-id="85ce7-123">Vlastnost <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> vrací jednu z následujících <xref:System.Xml.XPath.XPathResultType> hodnot výčtu představujících návratové typy XPath W3C.</span><span class="sxs-lookup"><span data-stu-id="85ce7-123">The <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property returns one of the following <xref:System.Xml.XPath.XPathResultType> enumeration values representing the W3C XPath return types.</span></span>  
  
- <xref:System.Xml.XPath.XPathResultType.Any>  
  
- <xref:System.Xml.XPath.XPathResultType.Boolean>  
  
- <xref:System.Xml.XPath.XPathResultType.Error>  
  
- <xref:System.Xml.XPath.XPathResultType.Navigator>  
  
- <xref:System.Xml.XPath.XPathResultType.NodeSet>  
  
- <xref:System.Xml.XPath.XPathResultType.Number>  
  
- <xref:System.Xml.XPath.XPathResultType.String>  
  
 <span data-ttu-id="85ce7-124">Následující příklad používá objekt <xref:System.Xml.XPath.XPathExpression> k vrácení čísla a sady uzlů ze souboru `books.xml`.</span><span class="sxs-lookup"><span data-stu-id="85ce7-124">The following example uses the <xref:System.Xml.XPath.XPathExpression> object to return a number and a node set from the `books.xml` file.</span></span> <span data-ttu-id="85ce7-125">Do konzoly je zapsána vlastnost <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> každého objektu <xref:System.Xml.XPath.XPathExpression> a výsledky z <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> a metody <xref:System.Xml.XPath.XPathNavigator.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="85ce7-125">The <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property of each <xref:System.Xml.XPath.XPathExpression> object as well as the results from the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> and <xref:System.Xml.XPath.XPathNavigator.Select%2A> methods are written to the console.</span></span>  
  
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
  
 <span data-ttu-id="85ce7-126">V příkladu se jako vstup používá soubor `books.xml`.</span><span class="sxs-lookup"><span data-stu-id="85ce7-126">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="higher-performance-xpath-expressions"></a><span data-ttu-id="85ce7-127">Výrazy XPath s vyšším výkonem</span><span class="sxs-lookup"><span data-stu-id="85ce7-127">Higher Performance XPath Expressions</span></span>  
 <span data-ttu-id="85ce7-128">Pro lepší výkon použijte ve svých dotazech nejvíce konkrétní výraz XPath.</span><span class="sxs-lookup"><span data-stu-id="85ce7-128">For better performance, use the most specific XPath expression possible in your queries.</span></span> <span data-ttu-id="85ce7-129">Například pokud uzel `book` je podřízený uzel uzlu `bookstore` a `bookstore` uzel je nejvyšší prvek v dokumentu XML, použití `/bookstore/book` výrazu XPath je rychlejší než použití `//book`.</span><span class="sxs-lookup"><span data-stu-id="85ce7-129">For example, if the `book` node is a child node of the `bookstore` node and the `bookstore` node is the top-most element in an XML document, using the XPath expression `/bookstore/book` is faster than using `//book`.</span></span> <span data-ttu-id="85ce7-130">`//book` výraz XPath zkontroluje každý uzel ve stromu XML a určí tak vyhovující uzly.</span><span class="sxs-lookup"><span data-stu-id="85ce7-130">The `//book` XPath expression will scan every node in the XML tree to identify matching nodes.</span></span>  
  
 <span data-ttu-id="85ce7-131">Kromě toho může použití metod navigace v uzlu, které poskytuje třída <xref:System.Xml.XPath.XPathNavigator>, způsobit lepší výkon přes metody výběru poskytované <xref:System.Xml.XPath.XPathNavigator> třídy v případech, kdy jsou kritéria výběru jednoduchá.</span><span class="sxs-lookup"><span data-stu-id="85ce7-131">Additionally, using the node set navigation methods supplied by the <xref:System.Xml.XPath.XPathNavigator> class may result in improved performance over the selection methods supplied by the <xref:System.Xml.XPath.XPathNavigator> class in cases where your selection criteria are simple.</span></span> <span data-ttu-id="85ce7-132">Například pokud potřebujete vybrat první podřízenou položku aktuálního uzlu, je rychlejší použít metodu <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> než použití `child::*[1]` výrazu XPath a metody <xref:System.Xml.XPath.XPathNavigator.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="85ce7-132">For example, if you need to select the first child of the current node, it is faster to use the <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> method than to use the `child::*[1]` XPath expression and the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method.</span></span>  
  
 <span data-ttu-id="85ce7-133">Další informace o tom, jak uzel nastavuje navigační metody třídy <xref:System.Xml.XPath.XPathNavigator>, najdete v tématu věnovaném [navigaci v uzlech pomocí XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="85ce7-133">For more information about the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class, see [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85ce7-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85ce7-134">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="85ce7-135">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="85ce7-135">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="85ce7-136">Výběr dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="85ce7-136">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="85ce7-137">Vyhodnocení výrazů XPath pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="85ce7-137">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="85ce7-138">Párování uzlů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="85ce7-138">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="85ce7-139">Rozpoznané typy uzlů s dotazy XPath</span><span class="sxs-lookup"><span data-stu-id="85ce7-139">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="85ce7-140">Dotazy XPath a obory názvů</span><span class="sxs-lookup"><span data-stu-id="85ce7-140">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
