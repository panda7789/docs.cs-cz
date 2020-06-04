---
title: Dotazování na stromy XML
ms.date: 07/20/2015
ms.assetid: 2e35c1ab-08c8-4378-9ca8-8ff344756eda
ms.openlocfilehash: 22e3dd873e2be8381f3d8da8f7c4284d09e45543
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411867"
---
# <a name="querying-xml-trees-visual-basic"></a><span data-ttu-id="a7da8-102">Dotazování na stromy XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7da8-102">Querying XML Trees (Visual Basic)</span></span>
<span data-ttu-id="a7da8-103">V této části najdete příklady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazů.</span><span class="sxs-lookup"><span data-stu-id="a7da8-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
 <span data-ttu-id="a7da8-104">Další informace o psaní dotazů LINQ naleznete v tématu [Začínáme with LINQ in Visual Basic](getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="a7da8-104">For more information about writing LINQ queries, see [Getting Started with LINQ in Visual Basic](getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="a7da8-105">Po vytvoření instance stromu XML je zápis dotazů nejúčinnějším způsobem, jak extrahovat data ze stromu.</span><span class="sxs-lookup"><span data-stu-id="a7da8-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="a7da8-106">Dotazování v kombinaci se strukturou funkční konstrukce vám také umožňuje vygenerovat nový dokument XML, který má jiný tvar z původního dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a7da8-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a7da8-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a7da8-107">In This Section</span></span>  
  
|<span data-ttu-id="a7da8-108">Téma</span><span class="sxs-lookup"><span data-stu-id="a7da8-108">Topic</span></span>|<span data-ttu-id="a7da8-109">Description</span><span class="sxs-lookup"><span data-stu-id="a7da8-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="a7da8-110">Základní dotazy (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7da8-110">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](basic-queries-linq-to-xml.md)|<span data-ttu-id="a7da8-111">Poskytuje běžné příklady pro dotazování stromů XML.</span><span class="sxs-lookup"><span data-stu-id="a7da8-111">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="a7da8-112">Projekce a transformace (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7da8-112">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](projections-and-transformations-linq-to-xml.md)|<span data-ttu-id="a7da8-113">Poskytuje běžné příklady pro projekci a transformaci stromů XML.</span><span class="sxs-lookup"><span data-stu-id="a7da8-113">Provides common examples of projecting from and transforming XML trees.</span></span>|  
|[<span data-ttu-id="a7da8-114">Pokročilé techniky dotazů (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7da8-114">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](advanced-query-techniques-linq-to-xml.md)|<span data-ttu-id="a7da8-115">Poskytuje techniky dotazů, které jsou užitečné v pokročilejších scénářích.</span><span class="sxs-lookup"><span data-stu-id="a7da8-115">Provides query techniques that are useful in more advanced scenarios.</span></span>|  
|[<span data-ttu-id="a7da8-116">LINQ to XML pro uživatele XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7da8-116">LINQ to XML for XPath Users (Visual Basic)</span></span>](linq-to-xml-for-xpath-users.md)|<span data-ttu-id="a7da8-117">Prezentuje počet výrazů XPath a jejich [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ekvivalenty.</span><span class="sxs-lookup"><span data-stu-id="a7da8-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] equivalents.</span></span>|  
|[<span data-ttu-id="a7da8-118">Čistě funkční transformace jazyka XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7da8-118">Pure Functional Transformations of XML (Visual Basic)</span></span>](pure-functional-transformations-of-xml.md)|<span data-ttu-id="a7da8-119">Prezentuje malý kurz zápisu dotazů ve stylu funkčního programování.</span><span class="sxs-lookup"><span data-stu-id="a7da8-119">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a7da8-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="a7da8-120">See also</span></span>

- [<span data-ttu-id="a7da8-121">Průvodce programováním (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7da8-121">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](programming-guide-linq-to-xml.md)
- [<span data-ttu-id="a7da8-122">Začínáme s dotazy LINQ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a7da8-122">Getting Started with LINQ in Visual Basic</span></span>](getting-started-with-linq.md)
