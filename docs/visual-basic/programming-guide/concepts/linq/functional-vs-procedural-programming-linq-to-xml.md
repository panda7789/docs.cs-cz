---
title: Functional vs. Procedural Programming (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: ea1015a5-d4c8-4d79-8e1e-ba17a40a4f39
ms.openlocfilehash: 3d1e3cf01b30454d29836f176afcd39cb2b55b73
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353414"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-visual-basic"></a><span data-ttu-id="ea57a-102">Functional vs. Procedural Programming (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea57a-102">Functional vs. Procedural Programming (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="ea57a-103">There are various types of XML applications:</span><span class="sxs-lookup"><span data-stu-id="ea57a-103">There are various types of XML applications:</span></span>  
  
- <span data-ttu-id="ea57a-104">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span><span class="sxs-lookup"><span data-stu-id="ea57a-104">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span></span>  
  
- <span data-ttu-id="ea57a-105">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span><span class="sxs-lookup"><span data-stu-id="ea57a-105">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span></span>  
  
- <span data-ttu-id="ea57a-106">Some applications take source XML documents, and insert records into a database.</span><span class="sxs-lookup"><span data-stu-id="ea57a-106">Some applications take source XML documents, and insert records into a database.</span></span>  
  
- <span data-ttu-id="ea57a-107">Some applications take data from another source, such as a database, and create XML documents from it.</span><span class="sxs-lookup"><span data-stu-id="ea57a-107">Some applications take data from another source, such as a database, and create XML documents from it.</span></span>  
  
 <span data-ttu-id="ea57a-108">These are not all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span><span class="sxs-lookup"><span data-stu-id="ea57a-108">These are not all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span></span>  
  
 <span data-ttu-id="ea57a-109">With all of these types of applications, there are two contrasting approaches that a developer can take:</span><span class="sxs-lookup"><span data-stu-id="ea57a-109">With all of these types of applications, there are two contrasting approaches that a developer can take:</span></span>  
  
- <span data-ttu-id="ea57a-110">Functional construction using a declarative approach.</span><span class="sxs-lookup"><span data-stu-id="ea57a-110">Functional construction using a declarative approach.</span></span>  
  
- <span data-ttu-id="ea57a-111">In-memory XML tree modification using procedural code.</span><span class="sxs-lookup"><span data-stu-id="ea57a-111">In-memory XML tree modification using procedural code.</span></span>  
  
 <span data-ttu-id="ea57a-112">LINQ to XML supports both approaches.</span><span class="sxs-lookup"><span data-stu-id="ea57a-112">LINQ to XML supports both approaches.</span></span>  
  
 <span data-ttu-id="ea57a-113">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span><span class="sxs-lookup"><span data-stu-id="ea57a-113">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span></span>  
  
 <span data-ttu-id="ea57a-114">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span><span class="sxs-lookup"><span data-stu-id="ea57a-114">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span></span>  
  
 <span data-ttu-id="ea57a-115">You can use LINQ to XML with either approach.</span><span class="sxs-lookup"><span data-stu-id="ea57a-115">You can use LINQ to XML with either approach.</span></span> <span data-ttu-id="ea57a-116">You use the same classes, and in some cases the same methods.</span><span class="sxs-lookup"><span data-stu-id="ea57a-116">You use the same classes, and in some cases the same methods.</span></span> <span data-ttu-id="ea57a-117">However, the structure and goals of the two approaches are very different.</span><span class="sxs-lookup"><span data-stu-id="ea57a-117">However, the structure and goals of the two approaches are very different.</span></span> <span data-ttu-id="ea57a-118">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span><span class="sxs-lookup"><span data-stu-id="ea57a-118">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span></span> <span data-ttu-id="ea57a-119">In addition, one or the other approach will be easier to write and yield more maintainable code.</span><span class="sxs-lookup"><span data-stu-id="ea57a-119">In addition, one or the other approach will be easier to write and yield more maintainable code.</span></span>  
  
 <span data-ttu-id="ea57a-120">To see the two approaches contrasted, see [In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md).</span><span class="sxs-lookup"><span data-stu-id="ea57a-120">To see the two approaches contrasted, see [In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md).</span></span>  
  
 <span data-ttu-id="ea57a-121">For a tutorial on writing functional transformations, see [Pure Functional Transformations of XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ea57a-121">For a tutorial on writing functional transformations, see [Pure Functional Transformations of XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea57a-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ea57a-122">See also</span></span>

- [<span data-ttu-id="ea57a-123">LINQ to XML Programming Overview (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea57a-123">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
