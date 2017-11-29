---
title: Projekce a transformace (technologie LINQ to XML) (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: bb0457ab-1823-47e6-9d2d-c93c958cc913
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 81172ebb440bc2737bbe3f1de0f1dd3cf6e086c4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="projections-and-transformations-linq-to-xml-c"></a><span data-ttu-id="b2469-102">Projekce a transformace (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b2469-102">Projections and Transformations (LINQ to XML) (C#)</span></span>
<span data-ttu-id="b2469-103">Tato část obsahuje příklady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] projekce a transformace.</span><span class="sxs-lookup"><span data-stu-id="b2469-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] projections and transformations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b2469-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b2469-104">In This Section</span></span>  
  
|<span data-ttu-id="b2469-105">Téma</span><span class="sxs-lookup"><span data-stu-id="b2469-105">Topic</span></span>|<span data-ttu-id="b2469-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b2469-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="b2469-107">Postupy: práce s slovník pomocí technologie LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="b2469-107">How to: Work with Dictionaries Using LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-work-with-dictionaries-using-linq-to-xml.md)|<span data-ttu-id="b2469-108">Ukazuje, jak k transformaci slovník do XML a postup transformace XML do slovník.</span><span class="sxs-lookup"><span data-stu-id="b2469-108">Shows how to transform dictionaries to XML, and how to transform XML into dictionaries.</span></span>|  
|[<span data-ttu-id="b2469-109">Postupy: transformace tvaru stromu XML (C#)</span><span class="sxs-lookup"><span data-stu-id="b2469-109">How to: Transform the Shape of an XML Tree (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-transform-the-shape-of-an-xml-tree.md)|<span data-ttu-id="b2469-110">Ukazuje, jak k transformaci obrazec dokument XML.</span><span class="sxs-lookup"><span data-stu-id="b2469-110">Shows how to transform the shape of an XML document.</span></span>|  
|[<span data-ttu-id="b2469-111">Postupy: řízení typu projekce (C#)</span><span class="sxs-lookup"><span data-stu-id="b2469-111">How to: Control the Type of a Projection (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-control-the-type-of-a-projection.md)|<span data-ttu-id="b2469-112">Ukazuje, jak řídit typ [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazu.</span><span class="sxs-lookup"><span data-stu-id="b2469-112">Shows how to control the type of a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="b2469-113">Postupy: projektu nový typ (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b2469-113">How to: Project a New Type (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-project-a-new-type-linq-to-xml.md)|<span data-ttu-id="b2469-114">Ukazuje, jak kolekci uživatelem definovaný typ z projektu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazu.</span><span class="sxs-lookup"><span data-stu-id="b2469-114">Shows how to project a collection of a user-defined type from a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="b2469-115">Postupy: projektu grafu objektu (C#)</span><span class="sxs-lookup"><span data-stu-id="b2469-115">How to: Project an Object Graph (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-project-an-object-graph.md)|<span data-ttu-id="b2469-116">Ukazuje, jak složitější grafu objektu z projektu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazu.</span><span class="sxs-lookup"><span data-stu-id="b2469-116">Shows how to project a more complex object graph from a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="b2469-117">Postupy: projektu anonymní typ (C#)</span><span class="sxs-lookup"><span data-stu-id="b2469-117">How to: Project an Anonymous Type (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-project-an-anonymous-type.md)|<span data-ttu-id="b2469-118">Ukazuje, jak kolekci anonymní objektů z projektu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazu.</span><span class="sxs-lookup"><span data-stu-id="b2469-118">Shows how to project a collection of anonymous objects from a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="b2469-119">Postupy: generování textové soubory ze souboru XML (C#)</span><span class="sxs-lookup"><span data-stu-id="b2469-119">How to: Generate Text Files from XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-generate-text-files-from-xml.md)|<span data-ttu-id="b2469-120">Ukazuje, jak k transformaci souboru XML do textového souboru nejsou XML.</span><span class="sxs-lookup"><span data-stu-id="b2469-120">Shows how to transform an XML file to a non-XML text file.</span></span>|  
|[<span data-ttu-id="b2469-121">Postupy: vygenerování XML ze souborů CSV (C#)</span><span class="sxs-lookup"><span data-stu-id="b2469-121">How to: Generate XML from CSV Files (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-generate-xml-from-csv-files.md)|<span data-ttu-id="b2469-122">Ukazuje, jak používat [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] analyzovat soubor CSV a z něj generovat XML.</span><span class="sxs-lookup"><span data-stu-id="b2469-122">Shows how to use [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to parse a CSV file and generate XML from it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b2469-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="b2469-123">See Also</span></span>  
 [<span data-ttu-id="b2469-124">Dotazování stromy XML (C#)</span><span class="sxs-lookup"><span data-stu-id="b2469-124">Querying XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)
