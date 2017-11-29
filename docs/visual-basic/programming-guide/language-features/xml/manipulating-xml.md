---
title: "Zacházení s XML v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- LINQ to XML [Visual Basic], manipulating XML
- Visual Basic code, XML
- XML [Visual Basic], manipulating
ms.assetid: da32cffb-198d-41b1-9af3-260fe32e3b7d
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 061617524659ac2f8793e2030f26a2d6b2724a64
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="manipulating-xml-in-visual-basic"></a><span data-ttu-id="90a0e-102">Zacházení s XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="90a0e-102">Manipulating XML in Visual Basic</span></span>
<span data-ttu-id="90a0e-103">Můžete použít *XML – literály* k načtení XML z externího zdroje například řetězce, souboru nebo datový proud.</span><span class="sxs-lookup"><span data-stu-id="90a0e-103">You can use *XML literals* to load XML from an external source such as a string, file, or stream.</span></span> <span data-ttu-id="90a0e-104">Pak můžete použít [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] k manipulaci s XML a použít [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] dotaz XML.</span><span class="sxs-lookup"><span data-stu-id="90a0e-104">You can then use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to manipulate the XML and use [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] to query the XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="90a0e-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="90a0e-105">In This Section</span></span>  
 [<span data-ttu-id="90a0e-106">Postupy: načtení XML ze souboru, řetězce nebo proudu</span><span class="sxs-lookup"><span data-stu-id="90a0e-106">How to: Load XML from a File, String, or Stream</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)  
 <span data-ttu-id="90a0e-107">Ukazuje, jak načíst XML do <xref:System.Xml.Linq.XDocument> nebo <xref:System.Xml.Linq.XElement> objekt z textového souboru, řetězce nebo proudu.</span><span class="sxs-lookup"><span data-stu-id="90a0e-107">Demonstrates how to load XML into an <xref:System.Xml.Linq.XDocument> or <xref:System.Xml.Linq.XElement> object from a text file, string, or stream.</span></span>  
  
 [<span data-ttu-id="90a0e-108">Postupy: transformace XML pomocí LINQ</span><span class="sxs-lookup"><span data-stu-id="90a0e-108">How to: Transform XML by Using LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-transform-xml-by-using-linq.md)  
 <span data-ttu-id="90a0e-109">Ukazuje, jak k transformaci obsah <xref:System.Xml.Linq.XDocument> objektu do nového dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="90a0e-109">Demonstrates how to transform the contents of an <xref:System.Xml.Linq.XDocument> object into a new XML document.</span></span>  
  
 [<span data-ttu-id="90a0e-110">Postupy: Změna literálů XML</span><span class="sxs-lookup"><span data-stu-id="90a0e-110">How to: Modify XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-modify-xml-literals.md)  
 <span data-ttu-id="90a0e-111">Ukazuje, jak upravit prvky, atributy a hodnoty literál XML.</span><span class="sxs-lookup"><span data-stu-id="90a0e-111">Demonstrates how to modify the elements, attributes, and values in an XML literal.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="90a0e-112">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="90a0e-112">Related Sections</span></span>  
 [<span data-ttu-id="90a0e-113">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="90a0e-113">XML Axis Properties</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 <span data-ttu-id="90a0e-114">Obsahuje odkazy na oddíly, které popisují různé vlastnosti přístupu XML.</span><span class="sxs-lookup"><span data-stu-id="90a0e-114">Provides links to sections that describe the various XML access properties.</span></span>  
  
 [<span data-ttu-id="90a0e-115">Přehled technologie LINQ to XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="90a0e-115">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 <span data-ttu-id="90a0e-116">Obsahuje úvod do používání [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="90a0e-116">Provides an introduction to using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="90a0e-117">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="90a0e-117">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 <span data-ttu-id="90a0e-118">Poskytuje úvod do používání literálů XML v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="90a0e-118">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="90a0e-119">Přístup XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="90a0e-119">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 <span data-ttu-id="90a0e-120">Demonstruje způsob přístupu k části – element XML nebo dokumentu v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="90a0e-120">Demonstrates how to access parts of an XML element or document in Visual Basic.</span></span>  
  
 [<span data-ttu-id="90a0e-121">XML</span><span class="sxs-lookup"><span data-stu-id="90a0e-121">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 <span data-ttu-id="90a0e-122">Obsahuje odkazy na oddíly, které popisují, jak používat [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="90a0e-122">Provides links to sections that describe how to use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90a0e-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="90a0e-123">See Also</span></span>  
 [<span data-ttu-id="90a0e-124">XML</span><span class="sxs-lookup"><span data-stu-id="90a0e-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [<span data-ttu-id="90a0e-125">LINQ</span><span class="sxs-lookup"><span data-stu-id="90a0e-125">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="90a0e-126">Úvod do LINQ v jazyku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="90a0e-126">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
