---
title: "Pokročilé techniky dotazu (technologie LINQ to XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 79be877c-fadc-4dfb-9f03-426082b13656
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 21a12ba1929b0e8fd24ae9e12404691222e397cf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="advanced-query-techniques-linq-to-xml-visual-basic"></a><span data-ttu-id="9cb5e-102">Pokročilé techniky dotazu (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9cb5e-102">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="9cb5e-103">Tato část obsahuje příklady pokročilejší [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] techniky dotazu.</span><span class="sxs-lookup"><span data-stu-id="9cb5e-103">This section provides examples of more advanced [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query techniques.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9cb5e-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="9cb5e-104">In This Section</span></span>  
  
|<span data-ttu-id="9cb5e-105">Téma</span><span class="sxs-lookup"><span data-stu-id="9cb5e-105">Topic</span></span>|<span data-ttu-id="9cb5e-106">Popis</span><span class="sxs-lookup"><span data-stu-id="9cb5e-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="9cb5e-107">Postupy: připojení dvě kolekce (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9cb5e-107">How to: Join Two Collections (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-two-collections-linq-to-xml.md)|<span data-ttu-id="9cb5e-108">Ukazuje, jak používat `Join` klauzule využívat výhod vztahy v datech XML.</span><span class="sxs-lookup"><span data-stu-id="9cb5e-108">Shows how to use the `Join` clause to take advantage of relationships in XML data.</span></span>|  
|[<span data-ttu-id="9cb5e-109">Postupy: vytvoření hierarchii pomocí seskupení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9cb5e-109">How to: Create Hierarchy Using Grouping (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-hierarchy-using-grouping.md)|<span data-ttu-id="9cb5e-110">Ukazuje, jak k seskupení dat a pak generování XML podle seskupení.</span><span class="sxs-lookup"><span data-stu-id="9cb5e-110">Shows how to group data, and then generate XML based on the grouping.</span></span>|  
|[<span data-ttu-id="9cb5e-111">Postupy: dotazování technologie LINQ to XML s použitím XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9cb5e-111">How to: Query LINQ to XML Using XPath (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-linq-to-xml-using-xpath.md)|<span data-ttu-id="9cb5e-112">Ukazuje, jak načíst kolekce založené na dotazy XPath.</span><span class="sxs-lookup"><span data-stu-id="9cb5e-112">Shows how to retrieve collections based on XPath queries.</span></span>|  
|[<span data-ttu-id="9cb5e-113">Postupy: zápis LINQ metodě osy XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9cb5e-113">How to: Write a LINQ to XML Axis Method (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md)|<span data-ttu-id="9cb5e-114">Ukazuje, jak k zápisu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] metoda osy.</span><span class="sxs-lookup"><span data-stu-id="9cb5e-114">Shows how to write a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axis method.</span></span>|  
|[<span data-ttu-id="9cb5e-115">Postupy: seznam všech uzlů ve stromu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9cb5e-115">How to: List All Nodes in a Tree (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-list-all-nodes-in-a-tree.md)|<span data-ttu-id="9cb5e-116">Uvede nástroj metodu, která uvádí všechny uzly ve stromu XML.</span><span class="sxs-lookup"><span data-stu-id="9cb5e-116">Presents a utility method that lists all nodes in an XML tree.</span></span> <span data-ttu-id="9cb5e-117">To je užitečné pro ladění kódu, která upraví strom XML.</span><span class="sxs-lookup"><span data-stu-id="9cb5e-117">This is useful for debugging code that modifies an XML tree.</span></span>|  
|[<span data-ttu-id="9cb5e-118">Postupy: načtení odstavců z dokumentu Office Open XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9cb5e-118">How to: Retrieve Paragraphs from an Office Open XML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-paragraphs-from-an-office-open-xml-document.md)|<span data-ttu-id="9cb5e-119">Uvede kód, který otevře dokument Office Open XML, načte odstavců v kolekci objektů XElement, text odstavce a styl odstavce.</span><span class="sxs-lookup"><span data-stu-id="9cb5e-119">Presents code that opens an Office Open XML Document, retrieves the paragraphs in a collection of XElement objects, the text of the paragraphs, and the style of the paragraphs.</span></span>|  
|[<span data-ttu-id="9cb5e-120">Postupy: Úprava dokumentu systému Office Open XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9cb5e-120">How to: Modify an Office Open XML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-modify-an-office-open-xml-document.md)|<span data-ttu-id="9cb5e-121">Uvede kód, který otevře, upraví a uloží dokument Office Open XML.</span><span class="sxs-lookup"><span data-stu-id="9cb5e-121">Presents code that opens, modifies, and saves an Office Open XML Document.</span></span>|  
|[<span data-ttu-id="9cb5e-122">Postupy: naplnění strom XML ze systému souborů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9cb5e-122">How to: Populate an XML Tree from the File System (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-an-xml-tree-from-the-file-system.md)|<span data-ttu-id="9cb5e-123">Uvede kód, který vytvoří strom XML ze systému souborů.</span><span class="sxs-lookup"><span data-stu-id="9cb5e-123">Presents code that creates an XML tree from the file system.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9cb5e-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="9cb5e-124">See Also</span></span>  
 [<span data-ttu-id="9cb5e-125">Dotazování stromy XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9cb5e-125">Querying XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md)
