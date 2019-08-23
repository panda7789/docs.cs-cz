---
title: Staticky kompilované dotazy (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 3f4825c7-c3b0-48da-ba4e-8e97fb2a2f34
ms.openlocfilehash: f9e703e65b333c0fd0c2a3219d537466c686af10
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961903"
---
# <a name="statically-compiled-queries-linq-to-xml-visual-basic"></a><span data-ttu-id="50119-102">Staticky kompilované dotazy (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50119-102">Statically Compiled Queries (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="50119-103">Jedna z nejdůležitějších výhod výkonu LINQ to XML, na rozdíl od <xref:System.Xml.XmlDocument>, je, že dotazy v LINQ to XML jsou staticky kompilovány, zatímco dotazy XPath musí být interpretovány za běhu.</span><span class="sxs-lookup"><span data-stu-id="50119-103">One of the most important performance benefits LINQ to XML, as opposed to <xref:System.Xml.XmlDocument>, is that queries in LINQ to XML are statically compiled, whereas XPath queries must be interpreted at run time.</span></span> <span data-ttu-id="50119-104">Tato funkce je integrovaná do LINQ to XML, takže není nutné provádět další kroky, abyste je mohli využít, ale je užitečné pochopit rozdíl mezi těmito dvěma technologiemi.</span><span class="sxs-lookup"><span data-stu-id="50119-104">This feature is built in to LINQ to XML, so you do not have to perform extra steps to take advantage of it, but it is helpful to understand the distinction when choosing between the two technologies.</span></span> <span data-ttu-id="50119-105">Toto téma popisuje rozdíl.</span><span class="sxs-lookup"><span data-stu-id="50119-105">This topic explains the difference.</span></span>  
  
## <a name="statically-compiled-queries-vs-xpath"></a><span data-ttu-id="50119-106">Staticky kompilované dotazy vs. XPath</span><span class="sxs-lookup"><span data-stu-id="50119-106">Statically Compiled Queries vs. XPath</span></span>  
 <span data-ttu-id="50119-107">Následující příklad ukazuje, jak získat odvozené prvky se zadaným názvem a s atributem se zadanou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="50119-107">The following example shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>  
  
 <span data-ttu-id="50119-108">Následuje ekvivalentní výraz XPath:</span><span class="sxs-lookup"><span data-stu-id="50119-108">The following is the equivalent XPath expression:</span></span>  
  
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
  
 <span data-ttu-id="50119-109">Výraz dotazu v tomto příkladu je znovu napsán kompilátorem do syntaxe dotazu založeného na metodě.</span><span class="sxs-lookup"><span data-stu-id="50119-109">The query expression in this example is re-written by the compiler to method-based query syntax.</span></span> <span data-ttu-id="50119-110">Následující příklad, který je napsán v syntaxi dotazu založeného na metodách, vytváří stejné výsledky jako předchozí:</span><span class="sxs-lookup"><span data-stu-id="50119-110">The following example, which is written in method-based query syntax, produces the same results as the previous one:</span></span>  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 As IEnumerable(Of XElement) = po.Descendants("Address").Where(Function(el) el.@Type = "Shipping")  
  
For Each el In list1  
    Console.WriteLine(el)  
Next   
```  
  
 <span data-ttu-id="50119-111"><xref:System.Linq.Enumerable.Where%2A> Metoda je rozšiřující metoda.</span><span class="sxs-lookup"><span data-stu-id="50119-111">The <xref:System.Linq.Enumerable.Where%2A> method is an extension method.</span></span> <span data-ttu-id="50119-112">Další informace naleznete v tématu [metody rozšíření](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="50119-112">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="50119-113">Vzhledem <xref:System.Linq.Enumerable.Where%2A> k tomu, že je metoda rozšíření, je dotaz výše zkompilován, jako by byl napsán takto:</span><span class="sxs-lookup"><span data-stu-id="50119-113">Because <xref:System.Linq.Enumerable.Where%2A> is an extension method, the query above is compiled as though it were written as follows:</span></span>  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 = Enumerable.Where(po.Descendants("Address"), Function(el) el.@Type = "Shipping")  
  
For Each el In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="50119-114">Tento příklad vytváří přesně stejné výsledky jako v předchozích dvou příkladech.</span><span class="sxs-lookup"><span data-stu-id="50119-114">This example produces exactly the same results as the previous two examples.</span></span> <span data-ttu-id="50119-115">To ukazuje fakt, že dotazy jsou efektivně zkompilovány do staticky propojených volání metody.</span><span class="sxs-lookup"><span data-stu-id="50119-115">This illustrates the fact that queries are effectively compiled into statically linked method calls.</span></span> <span data-ttu-id="50119-116">V kombinaci s sémantikou pro odložené provádění iterátorů zvyšuje výkon.</span><span class="sxs-lookup"><span data-stu-id="50119-116">This, combined with the deferred execution semantics of iterators, improves performance.</span></span> <span data-ttu-id="50119-117">Další informace o devodit sémantikě iterátorů naleznete [v tématu Odložené provádění a opožděné vyhodnocení v LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="50119-117">For more information about the deferred execution semantics of iterators, see [Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="50119-118">Tyto příklady jsou zástupci kódu, který kompilátor může zapisovat.</span><span class="sxs-lookup"><span data-stu-id="50119-118">These examples are representative of the code that the compiler might write.</span></span> <span data-ttu-id="50119-119">Skutečná implementace se může mírně lišit od těchto příkladů, ale výkon bude stejný nebo podobný jako v těchto příkladech.</span><span class="sxs-lookup"><span data-stu-id="50119-119">The actual implementation might differ slightly from these examples, but the performance will be the same or similar to these examples.</span></span>  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a><span data-ttu-id="50119-120">Provádění výrazů XPath s XmlDocument</span><span class="sxs-lookup"><span data-stu-id="50119-120">Executing XPath Expressions with XmlDocument</span></span>  
 <span data-ttu-id="50119-121">Následující příklad používá <xref:System.Xml.XmlDocument> k dosažení stejných výsledků jako předchozí příklady:</span><span class="sxs-lookup"><span data-stu-id="50119-121">The following example uses <xref:System.Xml.XmlDocument> to accomplish the same results as the previous examples:</span></span>  
  
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
  
 <span data-ttu-id="50119-122">Tento dotaz vrátí stejný výstup jako příklady, které používají LINQ to XML; Jediným rozdílem je, že LINQ to XML odsadí vytištěný XML, <xref:System.Xml.XmlDocument> zatímco ne.</span><span class="sxs-lookup"><span data-stu-id="50119-122">This query returns the same output as the examples that use LINQ to XML; the only difference is that LINQ to XML indents the printed XML, whereas <xref:System.Xml.XmlDocument> does not.</span></span>  
  
 <span data-ttu-id="50119-123">Obecně se ale neprovádí ani LINQ to XML, <xref:System.Xml.XmlNode.SelectNodes%2A> protože metoda musí provést následující interně při každém volání: <xref:System.Xml.XmlDocument></span><span class="sxs-lookup"><span data-stu-id="50119-123">However, the <xref:System.Xml.XmlDocument> approach generally does not perform as well as LINQ to XML, because the <xref:System.Xml.XmlNode.SelectNodes%2A> method must do the following internally every time it is called:</span></span>  
  
-   <span data-ttu-id="50119-124">Analyzuje řetězec, který obsahuje výraz XPath a přerušuje řetězec na tokeny.</span><span class="sxs-lookup"><span data-stu-id="50119-124">It parses the string that contains the XPath expression, breaking the string into tokens.</span></span>  
  
-   <span data-ttu-id="50119-125">Ověřuje tokeny, aby bylo zajištěno, že je výraz XPath platný.</span><span class="sxs-lookup"><span data-stu-id="50119-125">It validates the tokens to make sure that the XPath expression is valid.</span></span>  
  
-   <span data-ttu-id="50119-126">Převede výraz do vnitřního stromu výrazu.</span><span class="sxs-lookup"><span data-stu-id="50119-126">It translates the expression into an internal expression tree.</span></span>  
  
-   <span data-ttu-id="50119-127">Projde uzly a odpovídajícím způsobem vybere uzly sady výsledků na základě vyhodnocení výrazu.</span><span class="sxs-lookup"><span data-stu-id="50119-127">It iterates through the nodes, appropriately selecting the nodes for the result set based on the evaluation of the expression.</span></span>  
  
 <span data-ttu-id="50119-128">To je podstatně větší než práce prováděná odpovídajícím dotazem LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="50119-128">This is significantly more than the work done by the corresponding LINQ to XML query.</span></span> <span data-ttu-id="50119-129">Konkrétní rozdíl mezi výkonem se liší v různých typech dotazů, ale obecně LINQ to XML dotazy méně fungují, a proto je lepší, než vyhodnocování výrazů XPath pomocí <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="50119-129">The specific performance difference varies for different types of queries, but in general LINQ to XML queries do less work, and therefore perform better, than evaluating XPath expressions using <xref:System.Xml.XmlDocument>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50119-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50119-130">See also</span></span>

- [<span data-ttu-id="50119-131">Výkon (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50119-131">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
