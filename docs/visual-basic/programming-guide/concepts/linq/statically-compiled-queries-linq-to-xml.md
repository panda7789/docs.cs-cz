---
title: "Staticky kompilované dotazy (technologie LINQ to XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f4825c7-c3b0-48da-ba4e-8e97fb2a2f34
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d74cdb0ef089d59f8c0f6e9ef6656a1d06857633
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="statically-compiled-queries-linq-to-xml-visual-basic"></a><span data-ttu-id="7c7cd-102">Staticky kompilované dotazy (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c7cd-102">Statically Compiled Queries (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="7c7cd-103">Jedním z nejdůležitějších výkonu výhody LINQ to XML, naproti tomu <xref:System.Xml.XmlDocument>, že dotazy v technologii LINQ to XML nejsou staticky kompiluje, zatímco dotazů XPath je nutné interpretovat v době běhu.</span><span class="sxs-lookup"><span data-stu-id="7c7cd-103">One of the most important performance benefits LINQ to XML, as opposed to <xref:System.Xml.XmlDocument>, is that queries in LINQ to XML are statically compiled, whereas XPath queries must be interpreted at run time.</span></span> <span data-ttu-id="7c7cd-104">Tato funkce je založená na technologii LINQ to XML, takže není nutné provést další kroky pro jejich výhod, ale je vhodné pochopit rozdíl při výběru mezi tyto technologie.</span><span class="sxs-lookup"><span data-stu-id="7c7cd-104">This feature is built in to LINQ to XML, so you do not have to perform extra steps to take advantage of it, but it is helpful to understand the distinction when choosing between the two technologies.</span></span> <span data-ttu-id="7c7cd-105">Toto téma vysvětluje rozdíly.</span><span class="sxs-lookup"><span data-stu-id="7c7cd-105">This topic explains the difference.</span></span>  
  
## <a name="statically-compiled-queries-vs-xpath"></a><span data-ttu-id="7c7cd-106">Staticky kompilované dotazy vs. XPath</span><span class="sxs-lookup"><span data-stu-id="7c7cd-106">Statically Compiled Queries vs. XPath</span></span>  
 <span data-ttu-id="7c7cd-107">Následující příklad ukazuje, jak získat následnickým elementům se zadaným názvem a atribut se zadanou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="7c7cd-107">The following example shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>  
  
 <span data-ttu-id="7c7cd-108">Toto je ekvivalentní výraz XPath:</span><span class="sxs-lookup"><span data-stu-id="7c7cd-108">The following is the equivalent XPath expression:</span></span>  
  
```  
//Address[@Type='Shipping']  
```  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 = From el In po.Descendants("Address")  
            Where el.@Type = "Shipping"  
  
For Each el In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="7c7cd-109">Výraz dotazu v tomto příkladu je znovu zapsána ve kompilátor syntaxe dotazu na základě metod.</span><span class="sxs-lookup"><span data-stu-id="7c7cd-109">The query expression in this example is re-written by the compiler to method-based query syntax.</span></span> <span data-ttu-id="7c7cd-110">Následující příklad, který je napsána v syntaxi dotazu na základě metod, vytvoří stejné výsledky jako předchozí:</span><span class="sxs-lookup"><span data-stu-id="7c7cd-110">The following example, which is written in method-based query syntax, produces the same results as the previous one:</span></span>  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 As IEnumerable(Of XElement) = po.Descendants("Address").Where(Function(el) el.@Type = "Shipping")  
  
For Each el In list1  
    Console.WriteLine(el)  
Next   
```  
  
 <span data-ttu-id="7c7cd-111"><xref:System.Linq.Enumerable.Where%2A> Metoda je metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="7c7cd-111">The <xref:System.Linq.Enumerable.Where%2A> method is an extension method.</span></span> <span data-ttu-id="7c7cd-112">Další informace najdete v tématu [rozšiřující metody](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="7c7cd-112">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="7c7cd-113">Protože <xref:System.Linq.Enumerable.Where%2A> je metody rozšíření dotazu výše je kompilovat, jako by byl napsán následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="7c7cd-113">Because <xref:System.Linq.Enumerable.Where%2A> is an extension method, the query above is compiled as though it were written as follows:</span></span>  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 = Enumerable.Where(po.Descendants("Address"), Function(el) el.@Type = "Shipping")  
  
For Each el In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="7c7cd-114">Tento příklad vytvoří stejné výsledky jako předchozí dva příklady.</span><span class="sxs-lookup"><span data-stu-id="7c7cd-114">This example produces exactly the same results as the previous two examples.</span></span> <span data-ttu-id="7c7cd-115">To ukazuje na skutečnost, že dotazy jsou efektivně zkompilovány do volání metod staticky propojený.</span><span class="sxs-lookup"><span data-stu-id="7c7cd-115">This illustrates the fact that queries are effectively compiled into statically linked method calls.</span></span> <span data-ttu-id="7c7cd-116">To, v kombinaci s odložené provedení sémantika iterátory, zvyšuje výkon.</span><span class="sxs-lookup"><span data-stu-id="7c7cd-116">This, combined with the deferred execution semantics of iterators, improves performance.</span></span> <span data-ttu-id="7c7cd-117">Další informace o sémantiku odložené provedení iterátory najdete v tématu [odložené provedení a opožděné vyhodnocení v technologii LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="7c7cd-117">For more information about the deferred execution semantics of iterators, see [Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c7cd-118">Tyto příklady jsou zástupce kód, který může zapisovat do kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="7c7cd-118">These examples are representative of the code that the compiler might write.</span></span> <span data-ttu-id="7c7cd-119">Skutečná implementace může mírně lišit od těchto příkladech, ale výkonu budou stejné nebo podobné tyto příklady.</span><span class="sxs-lookup"><span data-stu-id="7c7cd-119">The actual implementation might differ slightly from these examples, but the performance will be the same or similar to these examples.</span></span>  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a><span data-ttu-id="7c7cd-120">Provádění výrazech XPath s třídou XMLDocument nastavenou na</span><span class="sxs-lookup"><span data-stu-id="7c7cd-120">Executing XPath Expressions with XmlDocument</span></span>  
 <span data-ttu-id="7c7cd-121">Následující příklad používá <xref:System.Xml.XmlDocument> k provádění stejných výsledků jako v předchozích příkladech:</span><span class="sxs-lookup"><span data-stu-id="7c7cd-121">The following example uses <xref:System.Xml.XmlDocument> to accomplish the same results as the previous examples:</span></span>  
  
```vb  
Dim reader = Xml.XmlReader.Create("PurchaseOrders.xml")  
Dim doc As New Xml.XmlDocument()  
doc.Load(reader)  
Dim nl As Xml.XmlNodeList = doc.SelectNodes(".//Address[@Type='Shipping']")  
For Each n As Xml.XmlNode In nl  
    Console.WriteLine(n.OuterXml)  
Next  
reader.Close()  
```  
  
 <span data-ttu-id="7c7cd-122">Tento dotaz vrací stejný výstup jako příklady, které používají technologie LINQ to XML; jediným rozdílem je, že technologie LINQ to XML odsazení tištěných XML, zatímco <xref:System.Xml.XmlDocument> neexistuje.</span><span class="sxs-lookup"><span data-stu-id="7c7cd-122">This query returns the same output as the examples that use LINQ to XML; the only difference is that LINQ to XML indents the printed XML, whereas <xref:System.Xml.XmlDocument> does not.</span></span>  
  
 <span data-ttu-id="7c7cd-123">Ale <xref:System.Xml.XmlDocument> přístup obecně nebude provádět i technologie LINQ to XML, protože <xref:System.Xml.XmlNode.SelectNodes%2A> metoda musí udělejte interně pokaždé, když se označuje jako:</span><span class="sxs-lookup"><span data-stu-id="7c7cd-123">However, the <xref:System.Xml.XmlDocument> approach generally does not perform as well as LINQ to XML, because the <xref:System.Xml.XmlNode.SelectNodes%2A> method must do the following internally every time it is called:</span></span>  
  
-   <span data-ttu-id="7c7cd-124">Analyzuje řetězec, který obsahuje výraz XPath, nejnovější řetězec do tokenů.</span><span class="sxs-lookup"><span data-stu-id="7c7cd-124">It parses the string that contains the XPath expression, breaking the string into tokens.</span></span>  
  
-   <span data-ttu-id="7c7cd-125">Ověřuje tokeny, abyste měli jistotu, že výraz XPath je neplatný.</span><span class="sxs-lookup"><span data-stu-id="7c7cd-125">It validates the tokens to make sure that the XPath expression is valid.</span></span>  
  
-   <span data-ttu-id="7c7cd-126">Převádí výraz do stromu interní výrazů.</span><span class="sxs-lookup"><span data-stu-id="7c7cd-126">It translates the expression into an internal expression tree.</span></span>  
  
-   <span data-ttu-id="7c7cd-127">Iteruje uzly, správně výběr uzlů pro sadu výsledků dotazu na základě vyhodnocení výrazu.</span><span class="sxs-lookup"><span data-stu-id="7c7cd-127">It iterates through the nodes, appropriately selecting the nodes for the result set based on the evaluation of the expression.</span></span>  
  
 <span data-ttu-id="7c7cd-128">Toto je podstatně více, než podle odpovídající dotazu LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="7c7cd-128">This is significantly more than the work done by the corresponding LINQ to XML query.</span></span> <span data-ttu-id="7c7cd-129">Rozdíl konkrétní výkon se liší pro různé typy dotazů, ale v obecné technologie LINQ to XML dotazy menší práci a proto provádět lepší, než zhodnocení výrazech XPath pomocí <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="7c7cd-129">The specific performance difference varies for different types of queries, but in general LINQ to XML queries do less work, and therefore perform better, than evaluating XPath expressions using <xref:System.Xml.XmlDocument>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c7cd-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c7cd-130">See Also</span></span>  
 [<span data-ttu-id="7c7cd-131">Výkon (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c7cd-131">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
