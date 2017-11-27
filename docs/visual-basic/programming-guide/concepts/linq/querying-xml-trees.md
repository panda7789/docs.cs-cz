---
title: "Dotazování stromy XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e35c1ab-08c8-4378-9ca8-8ff344756eda
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1516cdc58effaa3e738210b948b43d7ed170890a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="querying-xml-trees-visual-basic"></a><span data-ttu-id="04db2-102">Dotazování stromy XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04db2-102">Querying XML Trees (Visual Basic)</span></span>
<span data-ttu-id="04db2-103">Tato část obsahuje příklady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="04db2-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
 <span data-ttu-id="04db2-104">Další informace o psaní [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy, najdete v části [Začínáme s dotazy LINQ v jazyku Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="04db2-104">For more information about writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, see [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="04db2-105">Po vytváření instance strom XML zápis dotazů je co nejúčinnější způsob, jak extrahovat data z stromu.</span><span class="sxs-lookup"><span data-stu-id="04db2-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="04db2-106">Navíc dotazování v kombinaci s funkční konstrukce umožňuje vygenerovat nový dokument XML, který má jinou tvaru z původního dokumentu.</span><span class="sxs-lookup"><span data-stu-id="04db2-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="04db2-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="04db2-107">In This Section</span></span>  
  
|<span data-ttu-id="04db2-108">Téma</span><span class="sxs-lookup"><span data-stu-id="04db2-108">Topic</span></span>|<span data-ttu-id="04db2-109">Popis</span><span class="sxs-lookup"><span data-stu-id="04db2-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="04db2-110">Základní dotazy (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04db2-110">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)|<span data-ttu-id="04db2-111">Obsahuje běžné příklady dotazování stromy XML.</span><span class="sxs-lookup"><span data-stu-id="04db2-111">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="04db2-112">Projekce a transformace (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04db2-112">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)|<span data-ttu-id="04db2-113">Poskytuje běžných příkladů projekce z a transformace stromy XML.</span><span class="sxs-lookup"><span data-stu-id="04db2-113">Provides common examples of projecting from and transforming XML trees.</span></span>|  
|[<span data-ttu-id="04db2-114">Pokročilé techniky dotazu (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04db2-114">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)|<span data-ttu-id="04db2-115">Poskytuje techniky dotazu, které jsou užitečné v pokročilejší scénáře.</span><span class="sxs-lookup"><span data-stu-id="04db2-115">Provides query techniques that are useful in more advanced scenarios.</span></span>|  
|[<span data-ttu-id="04db2-116">Technologie LINQ to XML pro uživatele XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04db2-116">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)|<span data-ttu-id="04db2-117">Uvede počet výrazech XPath a jejich [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ekvivalenty.</span><span class="sxs-lookup"><span data-stu-id="04db2-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] equivalents.</span></span>|  
|[<span data-ttu-id="04db2-118">Čistý funkční transformace XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04db2-118">Pure Functional Transformations of XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)|<span data-ttu-id="04db2-119">Uvede malé kurz zápis dotazů ve stylu funkční programování.</span><span class="sxs-lookup"><span data-stu-id="04db2-119">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="04db2-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="04db2-120">See Also</span></span>  
 [<span data-ttu-id="04db2-121">Průvodce programováním (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04db2-121">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)  
 [<span data-ttu-id="04db2-122">Začínáme s dotazy LINQ v jazyku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="04db2-122">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
