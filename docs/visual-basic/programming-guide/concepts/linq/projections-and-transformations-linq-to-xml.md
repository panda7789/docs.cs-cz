---
title: Projekce a transformace (technologie LINQ to XML) (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 297de224-b625-44cf-8c00-186b6189aa0e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 92179ce3f1919187038b1bf7be92a82c1b6483ee
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="projections-and-transformations-linq-to-xml-visual-basic"></a><span data-ttu-id="d5a12-102">Projekce a transformace (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5a12-102">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="d5a12-103">Tato část obsahuje příklady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] projekce a transformace.</span><span class="sxs-lookup"><span data-stu-id="d5a12-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] projections and transformations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d5a12-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d5a12-104">In This Section</span></span>  
  
|<span data-ttu-id="d5a12-105">Téma</span><span class="sxs-lookup"><span data-stu-id="d5a12-105">Topic</span></span>|<span data-ttu-id="d5a12-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d5a12-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="d5a12-107">Postupy: práce s slovník pomocí technologie LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5a12-107">How to: Work with Dictionaries Using LINQ to XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-work-with-dictionaries-using-linq-to-xml.md)|<span data-ttu-id="d5a12-108">Ukazuje, jak k transformaci slovník do XML a postup transformace XML do slovník.</span><span class="sxs-lookup"><span data-stu-id="d5a12-108">Shows how to transform dictionaries to XML, and how to transform XML into dictionaries.</span></span>|  
|[<span data-ttu-id="d5a12-109">Postupy: transformace tvaru stromu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5a12-109">How to: Transform the Shape of an XML Tree (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-transform-the-shape-of-an-xml-tree.md)|<span data-ttu-id="d5a12-110">Ukazuje, jak k transformaci obrazec dokument XML.</span><span class="sxs-lookup"><span data-stu-id="d5a12-110">Shows how to transform the shape of an XML document.</span></span>|  
|[<span data-ttu-id="d5a12-111">Postupy: řízení typu projekce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5a12-111">How to: Control the Type of a Projection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-control-the-type-of-a-projection.md)|<span data-ttu-id="d5a12-112">Ukazuje, jak řídit typ [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazu.</span><span class="sxs-lookup"><span data-stu-id="d5a12-112">Shows how to control the type of a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="d5a12-113">Postupy: projektu nový typ (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5a12-113">How to: Project a New Type (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-project-a-new-type-linq-to-xml.md)|<span data-ttu-id="d5a12-114">Ukazuje, jak kolekci uživatelem definovaný typ z projektu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazu.</span><span class="sxs-lookup"><span data-stu-id="d5a12-114">Shows how to project a collection of a user-defined type from a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="d5a12-115">Postupy: projektu grafu objektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5a12-115">How to: Project an Object Graph (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-project-an-object-graph.md)|<span data-ttu-id="d5a12-116">Ukazuje, jak složitější grafu objektu z projektu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazu.</span><span class="sxs-lookup"><span data-stu-id="d5a12-116">Shows how to project a more complex object graph from a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="d5a12-117">Postupy: projektu anonymní typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5a12-117">How to: Project an Anonymous Type (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-project-an-anonymous-type.md)|<span data-ttu-id="d5a12-118">Ukazuje, jak kolekci anonymní objektů z projektu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazu.</span><span class="sxs-lookup"><span data-stu-id="d5a12-118">Shows how to project a collection of anonymous objects from a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="d5a12-119">Postupy: generování textové soubory ze souboru XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5a12-119">How to: Generate Text Files from XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-generate-text-files-from-xml.md)|<span data-ttu-id="d5a12-120">Ukazuje, jak k transformaci souboru XML do textového souboru nejsou XML.</span><span class="sxs-lookup"><span data-stu-id="d5a12-120">Shows how to transform an XML file to a non-XML text file.</span></span>|  
|[<span data-ttu-id="d5a12-121">Postupy: vygenerování XML ze souborů CSV (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5a12-121">How to: Generate XML from CSV Files (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-generate-xml-from-csv-files.md)|<span data-ttu-id="d5a12-122">Ukazuje, jak používat [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] analyzovat soubor CSV a z něj generovat XML.</span><span class="sxs-lookup"><span data-stu-id="d5a12-122">Shows how to use [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to parse a CSV file and generate XML from it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d5a12-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5a12-123">See Also</span></span>  
 [<span data-ttu-id="d5a12-124">Dotazování stromy XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5a12-124">Querying XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md)
