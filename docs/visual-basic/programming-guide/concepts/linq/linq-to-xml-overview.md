---
title: Přehled LINQ to XML
ms.date: 07/20/2015
ms.assetid: 502661e0-bc5d-438d-94c2-7efb63bb6fbd
ms.openlocfilehash: ef3fca844dc98440eb4816110a5a78482cfa4f4e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346797"
---
# <a name="linq-to-xml-overview-visual-basic"></a><span data-ttu-id="197e0-102">LINQ to XML Overview (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="197e0-102">LINQ to XML Overview (Visual Basic)</span></span>
<span data-ttu-id="197e0-103">XML has been widely adopted as a way to format data in many contexts.</span><span class="sxs-lookup"><span data-stu-id="197e0-103">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="197e0-104">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span><span class="sxs-lookup"><span data-stu-id="197e0-104">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="197e0-105">is an up-to-date, redesigned approach to programming with XML.</span><span class="sxs-lookup"><span data-stu-id="197e0-105">is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="197e0-106">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span><span class="sxs-lookup"><span data-stu-id="197e0-106">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="197e0-107">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span><span class="sxs-lookup"><span data-stu-id="197e0-107">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>  
  
## <a name="linq-to-xml-developers"></a><span data-ttu-id="197e0-108">LINQ to XML Developers</span><span class="sxs-lookup"><span data-stu-id="197e0-108">LINQ to XML Developers</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="197e0-109">targets a variety of developers.</span><span class="sxs-lookup"><span data-stu-id="197e0-109">targets a variety of developers.</span></span> <span data-ttu-id="197e0-110">For an average developer who just wants to get something done, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] makes XML easier by providing a query experience that is similar to SQL.</span><span class="sxs-lookup"><span data-stu-id="197e0-110">For an average developer who just wants to get something done, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] makes XML easier by providing a query experience that is similar to SQL.</span></span> <span data-ttu-id="197e0-111">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span><span class="sxs-lookup"><span data-stu-id="197e0-111">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>  
  
 <span data-ttu-id="197e0-112">Professional developers can use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to greatly increase their productivity.</span><span class="sxs-lookup"><span data-stu-id="197e0-112">Professional developers can use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to greatly increase their productivity.</span></span> <span data-ttu-id="197e0-113">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], they can write less code that is more expressive, more compact, and more powerful.</span><span class="sxs-lookup"><span data-stu-id="197e0-113">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], they can write less code that is more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="197e0-114">They can use query expressions from multiple data domains at the same time.</span><span class="sxs-lookup"><span data-stu-id="197e0-114">They can use query expressions from multiple data domains at the same time.</span></span>  
  
## <a name="what-is-linq-to-xml"></a><span data-ttu-id="197e0-115">What Is LINQ to XML?</span><span class="sxs-lookup"><span data-stu-id="197e0-115">What Is LINQ to XML?</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="197e0-116">is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the .NET Framework programming languages.</span><span class="sxs-lookup"><span data-stu-id="197e0-116">is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the .NET Framework programming languages.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="197e0-117">is like the Document Object Model (DOM) in that it brings the XML document into memory.</span><span class="sxs-lookup"><span data-stu-id="197e0-117">is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="197e0-118">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span><span class="sxs-lookup"><span data-stu-id="197e0-118">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="197e0-119">However, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] differs from DOM: It provides a new object model that is lighter weight and easier to work with, and that takes advantage of language features in Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="197e0-119">However, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] differs from DOM: It provides a new object model that is lighter weight and easier to work with, and that takes advantage of language features in Visual Basic.</span></span>  
  
 <span data-ttu-id="197e0-120">The most important advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is its integration with [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="197e0-120">The most important advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is its integration with [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span></span> <span data-ttu-id="197e0-121">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span><span class="sxs-lookup"><span data-stu-id="197e0-121">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="197e0-122">The query capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is comparable in functionality (although not in syntax) to XPath and XQuery.</span><span class="sxs-lookup"><span data-stu-id="197e0-122">The query capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="197e0-123">The integration of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] in Visual Basic provides stronger typing, compile-time checking, and improved debugger support.</span><span class="sxs-lookup"><span data-stu-id="197e0-123">The integration of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] in Visual Basic provides stronger typing, compile-time checking, and improved debugger support.</span></span>  
  
 <span data-ttu-id="197e0-124">Another advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span><span class="sxs-lookup"><span data-stu-id="197e0-124">Another advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="197e0-125">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span><span class="sxs-lookup"><span data-stu-id="197e0-125">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>  
  
 <span data-ttu-id="197e0-126">For example, you might have a typical XML purchase order as described in [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="197e0-126">For example, you might have a typical XML purchase order as described in [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span> <span data-ttu-id="197e0-127">By using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span><span class="sxs-lookup"><span data-stu-id="197e0-127">By using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>  
  
```vb  
Dim partNos = _  
    From item In purchaseOrder...<Item> _  
    Select item.@PartNumber  
```  
  
 <span data-ttu-id="197e0-128">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span><span class="sxs-lookup"><span data-stu-id="197e0-128">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="197e0-129">To obtain this information, you could run the following query:</span><span class="sxs-lookup"><span data-stu-id="197e0-129">To obtain this information, you could run the following query:</span></span>  
  
```vb  
Dim partNos = _  
From item In purchaseOrder...<Item> _  
Where (item.<Quantity>.Value * _  
       item.<USPrice>.Value) > 100 _  
Order By item.<PartNumber>.Value _  
Select item  
```  
  
 <span data-ttu-id="197e0-130">In addition to these [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] capabilities, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides an improved XML programming interface.</span><span class="sxs-lookup"><span data-stu-id="197e0-130">In addition to these [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] capabilities, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides an improved XML programming interface.</span></span> <span data-ttu-id="197e0-131">Using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can:</span><span class="sxs-lookup"><span data-stu-id="197e0-131">Using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can:</span></span>  
  
- <span data-ttu-id="197e0-132">Load XML from files or streams.</span><span class="sxs-lookup"><span data-stu-id="197e0-132">Load XML from files or streams.</span></span>  
  
- <span data-ttu-id="197e0-133">Serialize XML to files or streams.</span><span class="sxs-lookup"><span data-stu-id="197e0-133">Serialize XML to files or streams.</span></span>  
  
- <span data-ttu-id="197e0-134">Create XML from scratch by using functional construction.</span><span class="sxs-lookup"><span data-stu-id="197e0-134">Create XML from scratch by using functional construction.</span></span>  
  
- <span data-ttu-id="197e0-135">Query XML using XPath-like axes.</span><span class="sxs-lookup"><span data-stu-id="197e0-135">Query XML using XPath-like axes.</span></span>  
  
- <span data-ttu-id="197e0-136">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="197e0-136">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>  
  
- <span data-ttu-id="197e0-137">Validate XML trees using XSD.</span><span class="sxs-lookup"><span data-stu-id="197e0-137">Validate XML trees using XSD.</span></span>  
  
- <span data-ttu-id="197e0-138">Use a combination of these features to transform XML trees from one shape into another.</span><span class="sxs-lookup"><span data-stu-id="197e0-138">Use a combination of these features to transform XML trees from one shape into another.</span></span>  
  
## <a name="creating-xml-trees"></a><span data-ttu-id="197e0-139">Vytváření stromů XML</span><span class="sxs-lookup"><span data-stu-id="197e0-139">Creating XML Trees</span></span>  
 <span data-ttu-id="197e0-140">IOne of the most significant advantages of programming with [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is that it is easy to create XML trees.</span><span class="sxs-lookup"><span data-stu-id="197e0-140">IOne of the most significant advantages of programming with [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is that it is easy to create XML trees.</span></span> <span data-ttu-id="197e0-141">For example, to create a small XML tree, you can write  code as follows:</span><span class="sxs-lookup"><span data-stu-id="197e0-141">For example, to create a small XML tree, you can write  code as follows:</span></span>  
  
```vb  
Dim contacts = _  
<Contacts>  
    <Contact>  
        <Name>Patrick Hines</Name>  
        <Phone Type="Home">206-555-0144</Phone>  
        <Phone Type="Work">425-555-0145</Phone>  
        <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
        </Address>  
    </Contact>  
</Contacts>  
```  
  
 <span data-ttu-id="197e0-142">The Visual Basic compiler translates XML literals into [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] method calls.</span><span class="sxs-lookup"><span data-stu-id="197e0-142">The Visual Basic compiler translates XML literals into [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] method calls.</span></span>  
  
 <span data-ttu-id="197e0-143">For more information, see [Creating XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="197e0-143">For more information, see [Creating XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="197e0-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="197e0-144">See also</span></span>

- <xref:System.Xml.Linq>
- [<span data-ttu-id="197e0-145">Začínáme (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="197e0-145">Getting Started (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
- [<span data-ttu-id="197e0-146">Overview of LINQ to XML in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="197e0-146">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)
- [<span data-ttu-id="197e0-147">XML</span><span class="sxs-lookup"><span data-stu-id="197e0-147">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
