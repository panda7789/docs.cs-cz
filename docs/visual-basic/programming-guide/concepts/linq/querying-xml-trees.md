---
title: Dotazování na stromy XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 2e35c1ab-08c8-4378-9ca8-8ff344756eda
ms.openlocfilehash: 0d3855a562ce5ec43b28fba21b2ab4db0583a2d3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024635"
---
# <a name="querying-xml-trees-visual-basic"></a><span data-ttu-id="3d7c2-102">Dotazování na stromy XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d7c2-102">Querying XML Trees (Visual Basic)</span></span>
<span data-ttu-id="3d7c2-103">Tato část obsahuje příklady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="3d7c2-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
 <span data-ttu-id="3d7c2-104">Další informace o psaní [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy, naleznete v tématu [Začínáme s dotazy LINQ v jazyce Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="3d7c2-104">For more information about writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, see [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="3d7c2-105">Po instanci stromu XML psaní dotazů je nejúčinnější způsob, jak extrahovat data ze stromu.</span><span class="sxs-lookup"><span data-stu-id="3d7c2-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="3d7c2-106">Kromě toho dotazu v kombinaci s funkční konstrukce umožňuje generovat nový dokument XML, který má odlišném tvaru z původního dokumentu.</span><span class="sxs-lookup"><span data-stu-id="3d7c2-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3d7c2-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="3d7c2-107">In This Section</span></span>  
  
|<span data-ttu-id="3d7c2-108">Téma</span><span class="sxs-lookup"><span data-stu-id="3d7c2-108">Topic</span></span>|<span data-ttu-id="3d7c2-109">Popis</span><span class="sxs-lookup"><span data-stu-id="3d7c2-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="3d7c2-110">Základní dotazy (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d7c2-110">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)|<span data-ttu-id="3d7c2-111">Poskytuje běžné příklady dotazování na stromy XML.</span><span class="sxs-lookup"><span data-stu-id="3d7c2-111">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="3d7c2-112">Projekce a transformace (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d7c2-112">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)|<span data-ttu-id="3d7c2-113">Poskytuje běžné příklady z projekce a transformace stromů XML.</span><span class="sxs-lookup"><span data-stu-id="3d7c2-113">Provides common examples of projecting from and transforming XML trees.</span></span>|  
|[<span data-ttu-id="3d7c2-114">Pokročilé techniky dotazování (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d7c2-114">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)|<span data-ttu-id="3d7c2-115">Poskytuje technik dotazu, které jsou užitečné v pokročilejších scénářích.</span><span class="sxs-lookup"><span data-stu-id="3d7c2-115">Provides query techniques that are useful in more advanced scenarios.</span></span>|  
|[<span data-ttu-id="3d7c2-116">LINQ to XML pro uživatele jazyka XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d7c2-116">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)|<span data-ttu-id="3d7c2-117">Uvede počet výrazů XPath a jejich [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ekvivalenty.</span><span class="sxs-lookup"><span data-stu-id="3d7c2-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] equivalents.</span></span>|  
|[<span data-ttu-id="3d7c2-118">Čistě funkční transformace XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d7c2-118">Pure Functional Transformations of XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)|<span data-ttu-id="3d7c2-119">Uvede počet malých kurzu o psaní dotazů ve stylu funkčního programování.</span><span class="sxs-lookup"><span data-stu-id="3d7c2-119">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3d7c2-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3d7c2-120">See also</span></span>

- [<span data-ttu-id="3d7c2-121">Průvodce programováním (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d7c2-121">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
- [<span data-ttu-id="3d7c2-122">Začínáme s dotazy LINQ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3d7c2-122">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
