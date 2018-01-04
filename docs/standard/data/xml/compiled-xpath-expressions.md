---
title: "Výrazy kompilované XPath"
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
ms.assetid: e25dd95f-b64c-4d8b-a3a4-379e1aa0ad55
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e6ff5661a7e78f9b37f16acc86834561fc697bcc
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="compiled-xpath-expressions"></a><span data-ttu-id="07eb5-102">Výrazy kompilované XPath</span><span class="sxs-lookup"><span data-stu-id="07eb5-102">Compiled XPath Expressions</span></span>
<span data-ttu-id="07eb5-103"><xref:System.Xml.XPath.XPathExpression> Objekt představuje kompilovaném dotazu XPath vrácených buď statických <xref:System.Xml.XPath.XPathExpression.Compile%2A> metodu <xref:System.Xml.XPath.XPathExpression> – třída nebo <xref:System.Xml.XPath.XPathNavigator.Compile%2A> metodu <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="07eb5-103">An <xref:System.Xml.XPath.XPathExpression> object represents a compiled XPath query returned from either the static <xref:System.Xml.XPath.XPathExpression.Compile%2A> method of the <xref:System.Xml.XPath.XPathExpression> class or the <xref:System.Xml.XPath.XPathNavigator.Compile%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="the-xpathexpression-class"></a><span data-ttu-id="07eb5-104">XPathExpression – třída</span><span class="sxs-lookup"><span data-stu-id="07eb5-104">The XPathExpression Class</span></span>  
 <span data-ttu-id="07eb5-105">Dotaz XPath reprezentována zkompilovat A <xref:System.Xml.XPath.XPathExpression> objektu je užitečné, pokud stejný dotaz XPath se používá více než jednou.</span><span class="sxs-lookup"><span data-stu-id="07eb5-105">A compiled XPath query represented by an <xref:System.Xml.XPath.XPathExpression> object is useful if the same XPath query is being used more than once.</span></span>  
  
 <span data-ttu-id="07eb5-106">Například při volání metody <xref:System.Xml.XPath.XPathNavigator.Select%2A> metoda vícekrát, místo použití řetězec představující dotaz XPath pokaždé, když, použít <xref:System.Xml.XPath.XPathExpression.Compile%2A> metodu <xref:System.Xml.XPath.XPathExpression> – třída nebo <xref:System.Xml.XPath.XPathNavigator.Compile%2A> metodu <xref:System.Xml.XPath.XPathNavigator> třídy pro kompilaci a dotaz XPath v mezipaměti <xref:System.Xml.XPath.XPathExpression> objekt pro opakované použití a lepší výkon.</span><span class="sxs-lookup"><span data-stu-id="07eb5-106">For example, when calling the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method multiple times, instead of using a string representing the XPath query each time, use the <xref:System.Xml.XPath.XPathExpression.Compile%2A> method of the <xref:System.Xml.XPath.XPathExpression> class or the <xref:System.Xml.XPath.XPathNavigator.Compile%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class to compile and cache the XPath query in an <xref:System.Xml.XPath.XPathExpression> object for reuse and improved performance.</span></span>  
  
 <span data-ttu-id="07eb5-107">Jednou kompilovat, <xref:System.Xml.XPath.XPathExpression> objektu může být použita jako vstup pro následující <xref:System.Xml.XPath.XPathNavigator> metody třídy v závislosti na typu vrácená z dotazu XPath.</span><span class="sxs-lookup"><span data-stu-id="07eb5-107">Once compiled, the <xref:System.Xml.XPath.XPathExpression> object may be used as input to the following <xref:System.Xml.XPath.XPathNavigator> class methods depending on the type returned from the XPath query.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Matches%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 <span data-ttu-id="07eb5-108">Následující tabulka popisuje všechny návratové typy W3C XPath, jejich vztahů rozhraní Microsoft .NET Framework a co metody <xref:System.Xml.XPath.XPathExpression> objektu může být použit s podle její návratový typ.</span><span class="sxs-lookup"><span data-stu-id="07eb5-108">The following table describes each of the W3C XPath return types, their Microsoft .NET Framework equivalencies, and what methods the <xref:System.Xml.XPath.XPathExpression> object may be used with based on its return type.</span></span>  
  
|<span data-ttu-id="07eb5-109">W3C XPath návratový typ</span><span class="sxs-lookup"><span data-stu-id="07eb5-109">W3C XPath Return Type</span></span>|<span data-ttu-id="07eb5-110">Ekvivalentní typ rozhraní .NET framework</span><span class="sxs-lookup"><span data-stu-id="07eb5-110">.NET Framework Equivalent Type</span></span>|<span data-ttu-id="07eb5-111">Popis</span><span class="sxs-lookup"><span data-stu-id="07eb5-111">Description</span></span>|<span data-ttu-id="07eb5-112">Metody</span><span class="sxs-lookup"><span data-stu-id="07eb5-112">Methods</span></span>|  
|---------------------------|------------------------------------|-----------------|-------------|  
|`Node set`|<xref:System.Xml.XPath.XPathNodeIterator>|<span data-ttu-id="07eb5-113">Neseřazený kolekce uzlů bez duplicitní položky vytvořené v pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="07eb5-113">An unordered collection of nodes without duplicates created in document order.</span></span>|<span data-ttu-id="07eb5-114"><xref:System.Xml.XPath.XPathNavigator.Select%2A>nebo<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A></span><span class="sxs-lookup"><span data-stu-id="07eb5-114"><xref:System.Xml.XPath.XPathNavigator.Select%2A> or <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A></span></span>|  
|`Boolean`|<xref:System.Boolean>|<span data-ttu-id="07eb5-115">A `true` nebo `false` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="07eb5-115">A `true` or `false` value.</span></span>|<span data-ttu-id="07eb5-116"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>nebo</span><span class="sxs-lookup"><span data-stu-id="07eb5-116"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> or</span></span><br /><br /> <xref:System.Xml.XPath.XPathNavigator.Matches%2A>|  
|`Number`|<xref:System.Double>|<span data-ttu-id="07eb5-117">Číslo s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="07eb5-117">A floating-point number.</span></span>|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`String`|<xref:System.String>|<span data-ttu-id="07eb5-118">Posloupnosti znaků UCS.</span><span class="sxs-lookup"><span data-stu-id="07eb5-118">A sequence of UCS characters.</span></span>|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
  
> [!NOTE]
>  <span data-ttu-id="07eb5-119"><xref:System.Xml.XPath.XPathNavigator.Matches%2A> Metoda přijímá výraz XPath jako jeho parametr.</span><span class="sxs-lookup"><span data-stu-id="07eb5-119">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method accepts an XPath expression as its parameter.</span></span> <span data-ttu-id="07eb5-120"><xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> Metoda vrátí <xref:System.Xml.XPath.XPathNavigator> objektu není jednou z návratové typy W3C XPath.</span><span class="sxs-lookup"><span data-stu-id="07eb5-120">The <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> method returns an <xref:System.Xml.XPath.XPathNavigator> object, not one of the W3C XPath return types.</span></span>  
  
### <a name="the-returntype-property"></a><span data-ttu-id="07eb5-121">Vlastnost ReturnType</span><span class="sxs-lookup"><span data-stu-id="07eb5-121">The ReturnType Property</span></span>  
 <span data-ttu-id="07eb5-122">Po XPath byl zkompilován dotaz do <xref:System.Xml.XPath.XPathExpression> objekt, můžete použít <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> vlastnost <xref:System.Xml.XPath.XPathExpression> objektem pro určení, co vrátí dotaz XPath.</span><span class="sxs-lookup"><span data-stu-id="07eb5-122">After an XPath query has been compiled into an <xref:System.Xml.XPath.XPathExpression> object, you can use the <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property of the <xref:System.Xml.XPath.XPathExpression> object to determine what the XPath query returns.</span></span>  
  
 <span data-ttu-id="07eb5-123"><xref:System.Xml.XPath.XPathExpression.ReturnType%2A> Vlastnost vrací jednu z následujících <xref:System.Xml.XPath.XPathResultType> hodnot výčtu představující W3C XPath návratové typy.</span><span class="sxs-lookup"><span data-stu-id="07eb5-123">The <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property returns one of the following <xref:System.Xml.XPath.XPathResultType> enumeration values representing the W3C XPath return types.</span></span>  
  
-   <xref:System.Xml.XPath.XPathResultType.Any>  
  
-   <xref:System.Xml.XPath.XPathResultType.Boolean>  
  
-   <xref:System.Xml.XPath.XPathResultType.Error>  
  
-   <xref:System.Xml.XPath.XPathResultType.Navigator>  
  
-   <xref:System.Xml.XPath.XPathResultType.NodeSet>  
  
-   <xref:System.Xml.XPath.XPathResultType.Number>  
  
-   <xref:System.Xml.XPath.XPathResultType.String>  
  
 <span data-ttu-id="07eb5-124">Následující příklad používá <xref:System.Xml.XPath.XPathExpression> objekt vrátí číslo a nastavení z uzlu `books.xml` souboru.</span><span class="sxs-lookup"><span data-stu-id="07eb5-124">The following example uses the <xref:System.Xml.XPath.XPathExpression> object to return a number and a node set from the `books.xml` file.</span></span> <span data-ttu-id="07eb5-125"><xref:System.Xml.XPath.XPathExpression.ReturnType%2A> Vlastnost jednotlivých <xref:System.Xml.XPath.XPathExpression> objektu a také výsledků <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> a <xref:System.Xml.XPath.XPathNavigator.Select%2A> metody se zapisují do konzoly.</span><span class="sxs-lookup"><span data-stu-id="07eb5-125">The <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property of each <xref:System.Xml.XPath.XPathExpression> object as well as the results from the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> and <xref:System.Xml.XPath.XPathNavigator.Select%2A> methods are written to the console.</span></span>  
  
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
  
 <span data-ttu-id="07eb5-126">V příkladu trvá `books.xml` souboru jako vstup.</span><span class="sxs-lookup"><span data-stu-id="07eb5-126">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="higher-performance-xpath-expressions"></a><span data-ttu-id="07eb5-127">Vyšší výkon výrazech XPath</span><span class="sxs-lookup"><span data-stu-id="07eb5-127">Higher Performance XPath Expressions</span></span>  
 <span data-ttu-id="07eb5-128">Pro lepší výkon použijte nejvíce výraz XPath, která je možné v dotazech.</span><span class="sxs-lookup"><span data-stu-id="07eb5-128">For better performance, use the most specific XPath expression possible in your queries.</span></span> <span data-ttu-id="07eb5-129">Například pokud `book` uzel je podřízený uzel `bookstore` uzlu a `bookstore` uzel je nejvyšší element v dokumentu XML pomocí výraz XPath `/bookstore/book` je rychlejší než při použití `//book`.</span><span class="sxs-lookup"><span data-stu-id="07eb5-129">For example, if the `book` node is a child node of the `bookstore` node and the `bookstore` node is the top-most element in an XML document, using the XPath expression `/bookstore/book` is faster than using `//book`.</span></span> <span data-ttu-id="07eb5-130">`//book` Výraz XPath bude kontrolovat každý uzel ve stromové struktuře XML k identifikaci odpovídající uzly.</span><span class="sxs-lookup"><span data-stu-id="07eb5-130">The `//book` XPath expression will scan every node in the XML tree to identify matching nodes.</span></span>  
  
 <span data-ttu-id="07eb5-131">Kromě toho pomocí uzlu nastavit navigační metody poskytl <xref:System.Xml.XPath.XPathNavigator> – třída může mít za následek vylepšení výkonu prostřednictvím metody výběru poskytl <xref:System.Xml.XPath.XPathNavigator> třídy v případech, kdy jsou jednoduché kritériím výběru.</span><span class="sxs-lookup"><span data-stu-id="07eb5-131">Additionally, using the node set navigation methods supplied by the <xref:System.Xml.XPath.XPathNavigator> class may result in improved performance over the selection methods supplied by the <xref:System.Xml.XPath.XPathNavigator> class in cases where your selection criteria are simple.</span></span> <span data-ttu-id="07eb5-132">Například pokud je nutné vybrat prvního podřízeného člena na aktuální uzel, je rychlejší použít <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> než k použijte `child::*[1]` výraz XPath a <xref:System.Xml.XPath.XPathNavigator.Select%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="07eb5-132">For example, if you need to select the first child of the current node, it is faster to use the <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> method than to use the `child::*[1]` XPath expression and the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method.</span></span>  
  
 <span data-ttu-id="07eb5-133">Další informace o uzlu nastavit metody navigace <xref:System.Xml.XPath.XPathNavigator> třídy najdete v tématu [uzlu nastavit navigační pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="07eb5-133">For more information about the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class, see [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07eb5-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="07eb5-134">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="07eb5-135">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="07eb5-135">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="07eb5-136">Výběr dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="07eb5-136">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="07eb5-137">Vyhodnocení výrazů XPath pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="07eb5-137">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [<span data-ttu-id="07eb5-138">Párování uzlů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="07eb5-138">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [<span data-ttu-id="07eb5-139">Rozpoznané typy uzlů s dotazy XPath</span><span class="sxs-lookup"><span data-stu-id="07eb5-139">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [<span data-ttu-id="07eb5-140">Dotazy XPath a obory názvů</span><span class="sxs-lookup"><span data-stu-id="07eb5-140">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
