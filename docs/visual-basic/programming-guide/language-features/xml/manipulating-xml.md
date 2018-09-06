---
title: Zacházení s XML v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], manipulating XML
- Visual Basic code, XML
- XML [Visual Basic], manipulating
ms.assetid: da32cffb-198d-41b1-9af3-260fe32e3b7d
ms.openlocfilehash: 7fd111f5e885de3389b8f93002db22b48c4edd45
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43805426"
---
# <a name="manipulating-xml-in-visual-basic"></a><span data-ttu-id="cc067-102">Zacházení s XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cc067-102">Manipulating XML in Visual Basic</span></span>
<span data-ttu-id="cc067-103">Můžete použít *literály XML* načtení z externího zdroje, například řetězce, soubor nebo datový proud XML.</span><span class="sxs-lookup"><span data-stu-id="cc067-103">You can use *XML literals* to load XML from an external source such as a string, file, or stream.</span></span> <span data-ttu-id="cc067-104">Pak můžete použít [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] manipulaci s XML a použití [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] dotaz XML.</span><span class="sxs-lookup"><span data-stu-id="cc067-104">You can then use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to manipulate the XML and use [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] to query the XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cc067-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="cc067-105">In This Section</span></span>  
 [<span data-ttu-id="cc067-106">Postupy: Načtení XML ze souboru, řetězce nebo streamu</span><span class="sxs-lookup"><span data-stu-id="cc067-106">How to: Load XML from a File, String, or Stream</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)  
 <span data-ttu-id="cc067-107">Ukazuje, jak načíst data XML <xref:System.Xml.Linq.XDocument> nebo <xref:System.Xml.Linq.XElement> objekt z textového souboru, řetězce nebo proudu.</span><span class="sxs-lookup"><span data-stu-id="cc067-107">Demonstrates how to load XML into an <xref:System.Xml.Linq.XDocument> or <xref:System.Xml.Linq.XElement> object from a text file, string, or stream.</span></span>  
  
 [<span data-ttu-id="cc067-108">Postupy: Transformace XML pomocí jazyka LINQ</span><span class="sxs-lookup"><span data-stu-id="cc067-108">How to: Transform XML by Using LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-transform-xml-by-using-linq.md)  
 <span data-ttu-id="cc067-109">Ukazuje, jak transformovat obsah <xref:System.Xml.Linq.XDocument> objekt do nového dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="cc067-109">Demonstrates how to transform the contents of an <xref:System.Xml.Linq.XDocument> object into a new XML document.</span></span>  
  
 [<span data-ttu-id="cc067-110">Postupy: Změna literálů XML</span><span class="sxs-lookup"><span data-stu-id="cc067-110">How to: Modify XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-modify-xml-literals.md)  
 <span data-ttu-id="cc067-111">Ukazuje, jak upravit prvky, atributy a hodnoty literál XML.</span><span class="sxs-lookup"><span data-stu-id="cc067-111">Demonstrates how to modify the elements, attributes, and values in an XML literal.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="cc067-112">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="cc067-112">Related Sections</span></span>  
 [<span data-ttu-id="cc067-113">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="cc067-113">XML Axis Properties</span></span>](../../../../visual-basic/language-reference/xml-axis/index.md)  
 <span data-ttu-id="cc067-114">Obsahuje odkazy na oddíly, které popisují různé vlastnosti přístupu XML.</span><span class="sxs-lookup"><span data-stu-id="cc067-114">Provides links to sections that describe the various XML access properties.</span></span>  
  
 [<span data-ttu-id="cc067-115">Přehled technologie LINQ to XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cc067-115">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 <span data-ttu-id="cc067-116">Poskytuje úvod do používání [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="cc067-116">Provides an introduction to using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="cc067-117">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cc067-117">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 <span data-ttu-id="cc067-118">Poskytuje úvod do používání literály XML v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="cc067-118">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="cc067-119">Přístup ke XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cc067-119">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 <span data-ttu-id="cc067-120">Ukazuje, jak získat přístup k části elementu XML nebo dokumentu v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="cc067-120">Demonstrates how to access parts of an XML element or document in Visual Basic.</span></span>  
  
 [<span data-ttu-id="cc067-121">XML</span><span class="sxs-lookup"><span data-stu-id="cc067-121">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 <span data-ttu-id="cc067-122">Obsahuje odkazy na oddíly, které popisují způsob použití [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="cc067-122">Provides links to sections that describe how to use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc067-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc067-123">See Also</span></span>  
 [<span data-ttu-id="cc067-124">XML</span><span class="sxs-lookup"><span data-stu-id="cc067-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [<span data-ttu-id="cc067-125">LINQ</span><span class="sxs-lookup"><span data-stu-id="cc067-125">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="cc067-126">Úvod do LINQ v JAZYKU Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cc067-126">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
