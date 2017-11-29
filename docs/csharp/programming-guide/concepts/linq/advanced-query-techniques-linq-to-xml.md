---
title: "Pokročilé techniky dotazu (technologie LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 028d978e-215b-4d50-ba70-adce0659386d
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5898813d5773f13fa2c969b065e5ab1412726e9e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="advanced-query-techniques-linq-to-xml-c"></a><span data-ttu-id="f50f7-102">Pokročilé techniky dotazu (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f50f7-102">Advanced Query Techniques (LINQ to XML) (C#)</span></span>
<span data-ttu-id="f50f7-103">Tato část obsahuje příklady pokročilejší [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] techniky dotazu.</span><span class="sxs-lookup"><span data-stu-id="f50f7-103">This section provides examples of more advanced [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query techniques.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f50f7-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f50f7-104">In This Section</span></span>  
  
|<span data-ttu-id="f50f7-105">Téma</span><span class="sxs-lookup"><span data-stu-id="f50f7-105">Topic</span></span>|<span data-ttu-id="f50f7-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f50f7-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="f50f7-107">Postupy: připojení dvě kolekce (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f50f7-107">How to: Join Two Collections (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-join-two-collections-linq-to-xml.md)|<span data-ttu-id="f50f7-108">Ukazuje, jak používat `Join` klauzule využívat výhod vztahy v datech XML.</span><span class="sxs-lookup"><span data-stu-id="f50f7-108">Shows how to use the `Join` clause to take advantage of relationships in XML data.</span></span>|  
|[<span data-ttu-id="f50f7-109">Postupy: vytvoření hierarchii pomocí seskupení (C#)</span><span class="sxs-lookup"><span data-stu-id="f50f7-109">How to: Create Hierarchy Using Grouping (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-create-hierarchy-using-grouping.md)|<span data-ttu-id="f50f7-110">Ukazuje, jak k seskupení dat a pak generování XML podle seskupení.</span><span class="sxs-lookup"><span data-stu-id="f50f7-110">Shows how to group data, and then generate XML based on the grouping.</span></span>|  
|[<span data-ttu-id="f50f7-111">Postupy: dotazování technologie LINQ to XML s použitím XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="f50f7-111">How to: Query LINQ to XML Using XPath (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-linq-to-xml-using-xpath.md)|<span data-ttu-id="f50f7-112">Ukazuje, jak načíst kolekce založené na dotazy XPath.</span><span class="sxs-lookup"><span data-stu-id="f50f7-112">Shows how to retrieve collections based on XPath queries.</span></span>|  
|[<span data-ttu-id="f50f7-113">Postupy: zápis LINQ metodě osy XML (C#)</span><span class="sxs-lookup"><span data-stu-id="f50f7-113">How to: Write a LINQ to XML Axis Method (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md)|<span data-ttu-id="f50f7-114">Ukazuje, jak k zápisu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] metoda osy.</span><span class="sxs-lookup"><span data-stu-id="f50f7-114">Shows how to write a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axis method.</span></span>|  
|[<span data-ttu-id="f50f7-115">Postupy: provádění streamování transformací textu do formátu XML (C#)</span><span class="sxs-lookup"><span data-stu-id="f50f7-115">How to: Perform Streaming Transformations of Text to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-perform-streaming-transformations-of-text-to-xml.md)|<span data-ttu-id="f50f7-116">Ukazuje, jak na transformaci velmi velkých souborů na XML při zachování nároků paměti.</span><span class="sxs-lookup"><span data-stu-id="f50f7-116">Shows how to transform very large text files into XML while maintaining a small memory footprint.</span></span>|  
|[<span data-ttu-id="f50f7-117">Postupy: seznam všech uzlů ve stromu (C#)</span><span class="sxs-lookup"><span data-stu-id="f50f7-117">How to: List All Nodes in a Tree (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-list-all-nodes-in-a-tree.md)|<span data-ttu-id="f50f7-118">Uvede nástroj metodu, která uvádí všechny uzly ve stromu XML.</span><span class="sxs-lookup"><span data-stu-id="f50f7-118">Presents a utility method that lists all nodes in an XML tree.</span></span> <span data-ttu-id="f50f7-119">To je užitečné pro ladění kódu, která upraví strom XML.</span><span class="sxs-lookup"><span data-stu-id="f50f7-119">This is useful for debugging code that modifies an XML tree.</span></span>|  
|[<span data-ttu-id="f50f7-120">Postupy: načtení odstavců z dokumentu Office Open XML (C#)</span><span class="sxs-lookup"><span data-stu-id="f50f7-120">How to: Retrieve Paragraphs from an Office Open XML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-paragraphs-from-an-office-open-xml-document.md)|<span data-ttu-id="f50f7-121">Uvede kód, který otevře dokument Office Open XML, načte odstavců v kolekci objektů XElement, text odstavce a styl odstavce.</span><span class="sxs-lookup"><span data-stu-id="f50f7-121">Presents code that opens an Office Open XML Document, retrieves the paragraphs in a collection of XElement objects, the text of the paragraphs, and the style of the paragraphs.</span></span>|  
|[<span data-ttu-id="f50f7-122">Postupy: Úprava dokument Office Open XML (C#)</span><span class="sxs-lookup"><span data-stu-id="f50f7-122">How to: Modify an Office Open XML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-modify-an-office-open-xml-document.md)|<span data-ttu-id="f50f7-123">Uvede kód, který otevře, upraví a uloží dokument Office Open XML.</span><span class="sxs-lookup"><span data-stu-id="f50f7-123">Presents code that opens, modifies, and saves an Office Open XML Document.</span></span>|  
|[<span data-ttu-id="f50f7-124">Postupy: naplnění strom XML ze systému souborů (C#)</span><span class="sxs-lookup"><span data-stu-id="f50f7-124">How to: Populate an XML Tree from the File System (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-populate-an-xml-tree-from-the-file-system.md)|<span data-ttu-id="f50f7-125">Uvede kód, který vytvoří strom XML ze systému souborů.</span><span class="sxs-lookup"><span data-stu-id="f50f7-125">Presents code that creates an XML tree from the file system.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f50f7-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="f50f7-126">See Also</span></span>  
 [<span data-ttu-id="f50f7-127">Dotazování stromy XML (C#)</span><span class="sxs-lookup"><span data-stu-id="f50f7-127">Querying XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)
