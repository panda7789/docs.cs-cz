---
title: In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: d91c4ebf-6549-43cc-9961-26d4a82f722b
ms.openlocfilehash: 15c38cdf7ce860b34d8d3e9d59b8f06d80f6edd8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344441"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-visual-basic"></a><span data-ttu-id="ab758-102">In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab758-102">In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="ab758-103">Modifying an XML tree in place is a traditional approach to changing the shape of an XML document.</span><span class="sxs-lookup"><span data-stu-id="ab758-103">Modifying an XML tree in place is a traditional approach to changing the shape of an XML document.</span></span> <span data-ttu-id="ab758-104">A typical application loads a document into a data store such as DOM or [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; uses a programming interface to insert nodes, delete nodes, or change the content of nodes; and then saves the XML to a file or transmits it over a network.</span><span class="sxs-lookup"><span data-stu-id="ab758-104">A typical application loads a document into a data store such as DOM or [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; uses a programming interface to insert nodes, delete nodes, or change the content of nodes; and then saves the XML to a file or transmits it over a network.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="ab758-105">enables another approach that is useful in many scenarios *: functional construction*.</span><span class="sxs-lookup"><span data-stu-id="ab758-105">enables another approach that is useful in many scenarios *: functional construction*.</span></span> <span data-ttu-id="ab758-106">Functional construction treats modifying data as a problem of transformation, rather than as detailed manipulation of a data store.</span><span class="sxs-lookup"><span data-stu-id="ab758-106">Functional construction treats modifying data as a problem of transformation, rather than as detailed manipulation of a data store.</span></span> <span data-ttu-id="ab758-107">If you can take a representation of data and transform it efficiently from one form to another, the result is the same as if you took one data store and manipulated it in some way to take another shape.</span><span class="sxs-lookup"><span data-stu-id="ab758-107">If you can take a representation of data and transform it efficiently from one form to another, the result is the same as if you took one data store and manipulated it in some way to take another shape.</span></span> <span data-ttu-id="ab758-108">A key to the functional construction approach is to pass the results of queries to <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement> constructors.</span><span class="sxs-lookup"><span data-stu-id="ab758-108">A key to the functional construction approach is to pass the results of queries to <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement> constructors.</span></span>  
  
 <span data-ttu-id="ab758-109">In many cases you can write the transformational code in a fraction of the time that it would take to manipulate the data store, and that code is more robust and easier to maintain.</span><span class="sxs-lookup"><span data-stu-id="ab758-109">In many cases you can write the transformational code in a fraction of the time that it would take to manipulate the data store, and that code is more robust and easier to maintain.</span></span> <span data-ttu-id="ab758-110">In these cases, even though the transformational approach can take more processing power, it is a more effective way to modify data.</span><span class="sxs-lookup"><span data-stu-id="ab758-110">In these cases, even though the transformational approach can take more processing power, it is a more effective way to modify data.</span></span> <span data-ttu-id="ab758-111">If a developer is familiar with the functional approach, the resulting code in many cases is easier to understand.</span><span class="sxs-lookup"><span data-stu-id="ab758-111">If a developer is familiar with the functional approach, the resulting code in many cases is easier to understand.</span></span> <span data-ttu-id="ab758-112">It is easy to find the code that modifies each part of the tree.</span><span class="sxs-lookup"><span data-stu-id="ab758-112">It is easy to find the code that modifies each part of the tree.</span></span>  
  
 <span data-ttu-id="ab758-113">The approach where you modify an XML tree in-place is more familiar to many DOM programmers, whereas code written using the functional approach might look unfamiliar to a developer who doesn't yet understand that approach.</span><span class="sxs-lookup"><span data-stu-id="ab758-113">The approach where you modify an XML tree in-place is more familiar to many DOM programmers, whereas code written using the functional approach might look unfamiliar to a developer who doesn't yet understand that approach.</span></span> <span data-ttu-id="ab758-114">If you have to only make a small modification to a large XML tree, the approach where you modify a tree in place in many cases will take less CPU time.</span><span class="sxs-lookup"><span data-stu-id="ab758-114">If you have to only make a small modification to a large XML tree, the approach where you modify a tree in place in many cases will take less CPU time.</span></span>  
  
 <span data-ttu-id="ab758-115">This topic provides an example that is implemented with both approaches.</span><span class="sxs-lookup"><span data-stu-id="ab758-115">This topic provides an example that is implemented with both approaches.</span></span>  
  
## <a name="transforming-attributes-into-elements"></a><span data-ttu-id="ab758-116">Transforming Attributes into Elements</span><span class="sxs-lookup"><span data-stu-id="ab758-116">Transforming Attributes into Elements</span></span>  
 <span data-ttu-id="ab758-117">For this example, suppose you want to modify the following simple XML document so that the attributes become elements.</span><span class="sxs-lookup"><span data-stu-id="ab758-117">For this example, suppose you want to modify the following simple XML document so that the attributes become elements.</span></span> <span data-ttu-id="ab758-118">This topic first presents the traditional in-place modification approach.</span><span class="sxs-lookup"><span data-stu-id="ab758-118">This topic first presents the traditional in-place modification approach.</span></span> <span data-ttu-id="ab758-119">It then shows the functional construction approach.</span><span class="sxs-lookup"><span data-stu-id="ab758-119">It then shows the functional construction approach.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root Data1="123" Data2="456">  
  <Child1>Content</Child1>  
</Root>  
```  
  
### <a name="modifying-the-xml-tree"></a><span data-ttu-id="ab758-120">Modifying the XML Tree</span><span class="sxs-lookup"><span data-stu-id="ab758-120">Modifying the XML Tree</span></span>  
 <span data-ttu-id="ab758-121">You can write some procedural code to create elements from the attributes, and then delete the attributes, as follows:</span><span class="sxs-lookup"><span data-stu-id="ab758-121">You can write some procedural code to create elements from the attributes, and then delete the attributes, as follows:</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
For Each att As XAttribute In root.Attributes()  
    root.Add(New XElement(att.Name, att.Value))  
Next  
root.Attributes().Remove()  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="ab758-122">This code produces the following output:</span><span class="sxs-lookup"><span data-stu-id="ab758-122">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Content</Child1>  
  <Data1>123</Data1>  
  <Data2>456</Data2>  
</Root>  
```  
  
### <a name="functional-construction-approach"></a><span data-ttu-id="ab758-123">Functional Construction Approach</span><span class="sxs-lookup"><span data-stu-id="ab758-123">Functional Construction Approach</span></span>  
 <span data-ttu-id="ab758-124">By contrast, a functional approach consists of code to form a new tree, picking and choosing elements and attributes from the source tree, and transforming them as appropriate as they are added to the new tree.</span><span class="sxs-lookup"><span data-stu-id="ab758-124">By contrast, a functional approach consists of code to form a new tree, picking and choosing elements and attributes from the source tree, and transforming them as appropriate as they are added to the new tree.</span></span> <span data-ttu-id="ab758-125">The functional approach looks like the following:</span><span class="sxs-lookup"><span data-stu-id="ab758-125">The functional approach looks like the following:</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
Dim newTree As XElement = _  
    <Root>  
        <%= root.<Child1> %>  
        <%= From att In root.Attributes() _  
            Select New XElement(att.Name, att.Value) %>  
    </Root>  
Console.WriteLine(newTree)  
```  
  
 <span data-ttu-id="ab758-126">This example outputs the same XML as the first example.</span><span class="sxs-lookup"><span data-stu-id="ab758-126">This example outputs the same XML as the first example.</span></span> <span data-ttu-id="ab758-127">However, notice that you can actually see the resulting structure of the new XML in the functional approach.</span><span class="sxs-lookup"><span data-stu-id="ab758-127">However, notice that you can actually see the resulting structure of the new XML in the functional approach.</span></span> <span data-ttu-id="ab758-128">You can see the creation of the `Root` element, the code that pulls the `Child1` element from the source tree, and the code that transforms the attributes from the source tree to elements in the new tree.</span><span class="sxs-lookup"><span data-stu-id="ab758-128">You can see the creation of the `Root` element, the code that pulls the `Child1` element from the source tree, and the code that transforms the attributes from the source tree to elements in the new tree.</span></span>  
  
 <span data-ttu-id="ab758-129">The functional example in this case is not any shorter than the first example, and it is not really any simpler.</span><span class="sxs-lookup"><span data-stu-id="ab758-129">The functional example in this case is not any shorter than the first example, and it is not really any simpler.</span></span> <span data-ttu-id="ab758-130">However, if you have many changes to make to an XML tree, the non functional approach will become quite complex and somewhat obtuse.</span><span class="sxs-lookup"><span data-stu-id="ab758-130">However, if you have many changes to make to an XML tree, the non functional approach will become quite complex and somewhat obtuse.</span></span> <span data-ttu-id="ab758-131">In contrast, when using the functional approach, you still just form the desired XML, embedding queries and expressions as appropriate, to pull in the desired content.</span><span class="sxs-lookup"><span data-stu-id="ab758-131">In contrast, when using the functional approach, you still just form the desired XML, embedding queries and expressions as appropriate, to pull in the desired content.</span></span> <span data-ttu-id="ab758-132">The functional approach yields code that is easier to maintain.</span><span class="sxs-lookup"><span data-stu-id="ab758-132">The functional approach yields code that is easier to maintain.</span></span>  
  
 <span data-ttu-id="ab758-133">Notice that in this case the functional approach probably would not perform quite as well as the tree manipulation approach.</span><span class="sxs-lookup"><span data-stu-id="ab758-133">Notice that in this case the functional approach probably would not perform quite as well as the tree manipulation approach.</span></span> <span data-ttu-id="ab758-134">The main issue is that the functional approach creates more short lived objects.</span><span class="sxs-lookup"><span data-stu-id="ab758-134">The main issue is that the functional approach creates more short lived objects.</span></span> <span data-ttu-id="ab758-135">However, the tradeoff is an effective one if using the functional approach allows for greater programmer productivity.</span><span class="sxs-lookup"><span data-stu-id="ab758-135">However, the tradeoff is an effective one if using the functional approach allows for greater programmer productivity.</span></span>  
  
 <span data-ttu-id="ab758-136">This is a very simple example, but it serves to show the difference in philosophy between the two approaches.</span><span class="sxs-lookup"><span data-stu-id="ab758-136">This is a very simple example, but it serves to show the difference in philosophy between the two approaches.</span></span> <span data-ttu-id="ab758-137">The functional approach yields greater productivity gains for transforming larger XML documents.</span><span class="sxs-lookup"><span data-stu-id="ab758-137">The functional approach yields greater productivity gains for transforming larger XML documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab758-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ab758-138">See also</span></span>

- [<span data-ttu-id="ab758-139">Modifying XML Trees (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab758-139">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
