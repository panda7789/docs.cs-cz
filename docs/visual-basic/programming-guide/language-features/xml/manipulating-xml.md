---
title: Manipulace s XML
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], manipulating XML
- Visual Basic code, XML
- XML [Visual Basic], manipulating
ms.assetid: da32cffb-198d-41b1-9af3-260fe32e3b7d
ms.openlocfilehash: 2565f43c1014bf0fa9fab1618fedfd1bd6bdb7ca
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330444"
---
# <a name="manipulating-xml-in-visual-basic"></a><span data-ttu-id="9ec5a-102">Zacházení s XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9ec5a-102">Manipulating XML in Visual Basic</span></span>
<span data-ttu-id="9ec5a-103">You can use *XML literals* to load XML from an external source such as a string, file, or stream.</span><span class="sxs-lookup"><span data-stu-id="9ec5a-103">You can use *XML literals* to load XML from an external source such as a string, file, or stream.</span></span> <span data-ttu-id="9ec5a-104">You can then use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to manipulate the XML and use [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] to query the XML.</span><span class="sxs-lookup"><span data-stu-id="9ec5a-104">You can then use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to manipulate the XML and use [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] to query the XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9ec5a-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="9ec5a-105">In This Section</span></span>  
 [<span data-ttu-id="9ec5a-106">Postupy: Načtení XML ze souboru, řetězce nebo streamu</span><span class="sxs-lookup"><span data-stu-id="9ec5a-106">How to: Load XML from a File, String, or Stream</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)  
 <span data-ttu-id="9ec5a-107">Demonstrates how to load XML into an <xref:System.Xml.Linq.XDocument> or <xref:System.Xml.Linq.XElement> object from a text file, string, or stream.</span><span class="sxs-lookup"><span data-stu-id="9ec5a-107">Demonstrates how to load XML into an <xref:System.Xml.Linq.XDocument> or <xref:System.Xml.Linq.XElement> object from a text file, string, or stream.</span></span>  
  
 [<span data-ttu-id="9ec5a-108">Postupy: Transformace XML pomocí jazyka LINQ</span><span class="sxs-lookup"><span data-stu-id="9ec5a-108">How to: Transform XML by Using LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-transform-xml-by-using-linq.md)  
 <span data-ttu-id="9ec5a-109">Demonstrates how to transform the contents of an <xref:System.Xml.Linq.XDocument> object into a new XML document.</span><span class="sxs-lookup"><span data-stu-id="9ec5a-109">Demonstrates how to transform the contents of an <xref:System.Xml.Linq.XDocument> object into a new XML document.</span></span>  
  
 [<span data-ttu-id="9ec5a-110">Postupy: Změna literálů XML</span><span class="sxs-lookup"><span data-stu-id="9ec5a-110">How to: Modify XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-modify-xml-literals.md)  
 <span data-ttu-id="9ec5a-111">Demonstrates how to modify the elements, attributes, and values in an XML literal.</span><span class="sxs-lookup"><span data-stu-id="9ec5a-111">Demonstrates how to modify the elements, attributes, and values in an XML literal.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9ec5a-112">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="9ec5a-112">Related Sections</span></span>  
 [<span data-ttu-id="9ec5a-113">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="9ec5a-113">XML Axis Properties</span></span>](../../../../visual-basic/language-reference/xml-axis/index.md)  
 <span data-ttu-id="9ec5a-114">Provides links to sections that describe the various XML access properties.</span><span class="sxs-lookup"><span data-stu-id="9ec5a-114">Provides links to sections that describe the various XML access properties.</span></span>  
  
 [<span data-ttu-id="9ec5a-115">Overview of LINQ to XML in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9ec5a-115">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 <span data-ttu-id="9ec5a-116">Provides an introduction to using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9ec5a-116">Provides an introduction to using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="9ec5a-117">Creating XML in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9ec5a-117">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 <span data-ttu-id="9ec5a-118">Provides an introduction to using XML literals in Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9ec5a-118">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="9ec5a-119">Accessing XML in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9ec5a-119">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 <span data-ttu-id="9ec5a-120">Demonstrates how to access parts of an XML element or document in Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9ec5a-120">Demonstrates how to access parts of an XML element or document in Visual Basic.</span></span>  
  
 [<span data-ttu-id="9ec5a-121">XML</span><span class="sxs-lookup"><span data-stu-id="9ec5a-121">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 <span data-ttu-id="9ec5a-122">Provides links to sections that describe how to use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9ec5a-122">Provides links to sections that describe how to use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ec5a-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ec5a-123">See also</span></span>

- [<span data-ttu-id="9ec5a-124">XML</span><span class="sxs-lookup"><span data-stu-id="9ec5a-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="9ec5a-125">LINQ</span><span class="sxs-lookup"><span data-stu-id="9ec5a-125">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="9ec5a-126">Introduction to LINQ in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9ec5a-126">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
