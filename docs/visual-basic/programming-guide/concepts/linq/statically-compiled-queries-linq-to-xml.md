---
title: Staticky kompilované dotazy (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 3f4825c7-c3b0-48da-ba4e-8e97fb2a2f34
ms.openlocfilehash: e9f56366f1566f831f1e0ea5bd5a06775d698c3d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350583"
---
# <a name="statically-compiled-queries-linq-to-xml-visual-basic"></a><span data-ttu-id="75cb8-102">Statically Compiled Queries (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75cb8-102">Statically Compiled Queries (LINQ to XML) (Visual Basic)</span></span>

<span data-ttu-id="75cb8-103">One of the most important performance benefits LINQ to XML, as opposed to <xref:System.Xml.XmlDocument>, is that queries in LINQ to XML are statically compiled, whereas XPath queries must be interpreted at run time.</span><span class="sxs-lookup"><span data-stu-id="75cb8-103">One of the most important performance benefits LINQ to XML, as opposed to <xref:System.Xml.XmlDocument>, is that queries in LINQ to XML are statically compiled, whereas XPath queries must be interpreted at run time.</span></span> <span data-ttu-id="75cb8-104">This feature is built in to LINQ to XML, so you do not have to perform extra steps to take advantage of it, but it is helpful to understand the distinction when choosing between the two technologies.</span><span class="sxs-lookup"><span data-stu-id="75cb8-104">This feature is built in to LINQ to XML, so you do not have to perform extra steps to take advantage of it, but it is helpful to understand the distinction when choosing between the two technologies.</span></span> <span data-ttu-id="75cb8-105">This topic explains the difference.</span><span class="sxs-lookup"><span data-stu-id="75cb8-105">This topic explains the difference.</span></span>

## <a name="statically-compiled-queries-vs-xpath"></a><span data-ttu-id="75cb8-106">Statically Compiled Queries vs. XPath</span><span class="sxs-lookup"><span data-stu-id="75cb8-106">Statically Compiled Queries vs. XPath</span></span>

<span data-ttu-id="75cb8-107">The following example shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span><span class="sxs-lookup"><span data-stu-id="75cb8-107">The following example shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>

<span data-ttu-id="75cb8-108">The following is the equivalent XPath expression:</span><span class="sxs-lookup"><span data-stu-id="75cb8-108">The following is the equivalent XPath expression:</span></span>

```vb
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

<span data-ttu-id="75cb8-109">The query expression in this example is re-written by the compiler to method-based query syntax.</span><span class="sxs-lookup"><span data-stu-id="75cb8-109">The query expression in this example is re-written by the compiler to method-based query syntax.</span></span> <span data-ttu-id="75cb8-110">The following example, which is written in method-based query syntax, produces the same results as the previous one:</span><span class="sxs-lookup"><span data-stu-id="75cb8-110">The following example, which is written in method-based query syntax, produces the same results as the previous one:</span></span>

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 As IEnumerable(Of XElement) = po.Descendants("Address").Where(Function(el) el.@Type = "Shipping")

For Each el In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="75cb8-111">The <xref:System.Linq.Enumerable.Where%2A> method is an extension method.</span><span class="sxs-lookup"><span data-stu-id="75cb8-111">The <xref:System.Linq.Enumerable.Where%2A> method is an extension method.</span></span> <span data-ttu-id="75cb8-112">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="75cb8-112">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="75cb8-113">Because <xref:System.Linq.Enumerable.Where%2A> is an extension method, the query above is compiled as though it were written as follows:</span><span class="sxs-lookup"><span data-stu-id="75cb8-113">Because <xref:System.Linq.Enumerable.Where%2A> is an extension method, the query above is compiled as though it were written as follows:</span></span>

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 = Enumerable.Where(po.Descendants("Address"), Function(el) el.@Type = "Shipping")

For Each el In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="75cb8-114">This example produces exactly the same results as the previous two examples.</span><span class="sxs-lookup"><span data-stu-id="75cb8-114">This example produces exactly the same results as the previous two examples.</span></span> <span data-ttu-id="75cb8-115">This illustrates the fact that queries are effectively compiled into statically linked method calls.</span><span class="sxs-lookup"><span data-stu-id="75cb8-115">This illustrates the fact that queries are effectively compiled into statically linked method calls.</span></span> <span data-ttu-id="75cb8-116">This, combined with the deferred execution semantics of iterators, improves performance.</span><span class="sxs-lookup"><span data-stu-id="75cb8-116">This, combined with the deferred execution semantics of iterators, improves performance.</span></span> <span data-ttu-id="75cb8-117">For more information about the deferred execution semantics of iterators, see [Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="75cb8-117">For more information about the deferred execution semantics of iterators, see [Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>

> [!NOTE]
> <span data-ttu-id="75cb8-118">These examples are representative of the code that the compiler might write.</span><span class="sxs-lookup"><span data-stu-id="75cb8-118">These examples are representative of the code that the compiler might write.</span></span> <span data-ttu-id="75cb8-119">The actual implementation might differ slightly from these examples, but the performance will be the same or similar to these examples.</span><span class="sxs-lookup"><span data-stu-id="75cb8-119">The actual implementation might differ slightly from these examples, but the performance will be the same or similar to these examples.</span></span>

## <a name="executing-xpath-expressions-with-xmldocument"></a><span data-ttu-id="75cb8-120">Executing XPath Expressions with XmlDocument</span><span class="sxs-lookup"><span data-stu-id="75cb8-120">Executing XPath Expressions with XmlDocument</span></span>

<span data-ttu-id="75cb8-121">The following example uses <xref:System.Xml.XmlDocument> to accomplish the same results as the previous examples:</span><span class="sxs-lookup"><span data-stu-id="75cb8-121">The following example uses <xref:System.Xml.XmlDocument> to accomplish the same results as the previous examples:</span></span>

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

<span data-ttu-id="75cb8-122">This query returns the same output as the examples that use LINQ to XML; the only difference is that LINQ to XML indents the printed XML, whereas <xref:System.Xml.XmlDocument> does not.</span><span class="sxs-lookup"><span data-stu-id="75cb8-122">This query returns the same output as the examples that use LINQ to XML; the only difference is that LINQ to XML indents the printed XML, whereas <xref:System.Xml.XmlDocument> does not.</span></span>

<span data-ttu-id="75cb8-123">However, the <xref:System.Xml.XmlDocument> approach generally does not perform as well as LINQ to XML, because the <xref:System.Xml.XmlNode.SelectNodes%2A> method must do the following internally every time it is called:</span><span class="sxs-lookup"><span data-stu-id="75cb8-123">However, the <xref:System.Xml.XmlDocument> approach generally does not perform as well as LINQ to XML, because the <xref:System.Xml.XmlNode.SelectNodes%2A> method must do the following internally every time it is called:</span></span>

- <span data-ttu-id="75cb8-124">It parses the string that contains the XPath expression, breaking the string into tokens.</span><span class="sxs-lookup"><span data-stu-id="75cb8-124">It parses the string that contains the XPath expression, breaking the string into tokens.</span></span>

- <span data-ttu-id="75cb8-125">It validates the tokens to make sure that the XPath expression is valid.</span><span class="sxs-lookup"><span data-stu-id="75cb8-125">It validates the tokens to make sure that the XPath expression is valid.</span></span>

- <span data-ttu-id="75cb8-126">It translates the expression into an internal expression tree.</span><span class="sxs-lookup"><span data-stu-id="75cb8-126">It translates the expression into an internal expression tree.</span></span>

- <span data-ttu-id="75cb8-127">It iterates through the nodes, appropriately selecting the nodes for the result set based on the evaluation of the expression.</span><span class="sxs-lookup"><span data-stu-id="75cb8-127">It iterates through the nodes, appropriately selecting the nodes for the result set based on the evaluation of the expression.</span></span>

<span data-ttu-id="75cb8-128">This is significantly more than the work done by the corresponding LINQ to XML query.</span><span class="sxs-lookup"><span data-stu-id="75cb8-128">This is significantly more than the work done by the corresponding LINQ to XML query.</span></span> <span data-ttu-id="75cb8-129">The specific performance difference varies for different types of queries, but in general LINQ to XML queries do less work, and therefore perform better, than evaluating XPath expressions using <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="75cb8-129">The specific performance difference varies for different types of queries, but in general LINQ to XML queries do less work, and therefore perform better, than evaluating XPath expressions using <xref:System.Xml.XmlDocument>.</span></span>

## <a name="see-also"></a><span data-ttu-id="75cb8-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="75cb8-130">See also</span></span>

- [<span data-ttu-id="75cb8-131">Performance (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75cb8-131">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
