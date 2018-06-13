---
title: Dotazování stromy XML (C#)
ms.date: 07/20/2015
ms.assetid: 0913d81b-541a-4fd4-9cbf-7ec89fd817ea
ms.openlocfilehash: 5d2e40da26f30a0ece570acf2fd25684d1cba40f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331084"
---
# <a name="querying-xml-trees-c"></a><span data-ttu-id="52149-102">Dotazování stromy XML (C#)</span><span class="sxs-lookup"><span data-stu-id="52149-102">Querying XML Trees (C#)</span></span>
<span data-ttu-id="52149-103">Tato část obsahuje příklady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="52149-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
 <span data-ttu-id="52149-104">Další informace o psaní [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy, najdete v části [Začínáme s dotazy LINQ v jazyku C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="52149-104">For more information about writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, see [Getting Started with LINQ in C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="52149-105">Po vytváření instance strom XML zápis dotazů je co nejúčinnější způsob, jak extrahovat data z stromu.</span><span class="sxs-lookup"><span data-stu-id="52149-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="52149-106">Navíc dotazování v kombinaci s funkční konstrukce umožňuje vygenerovat nový dokument XML, který má jinou tvaru z původního dokumentu.</span><span class="sxs-lookup"><span data-stu-id="52149-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="52149-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="52149-107">In This Section</span></span>  
  
|<span data-ttu-id="52149-108">Téma</span><span class="sxs-lookup"><span data-stu-id="52149-108">Topic</span></span>|<span data-ttu-id="52149-109">Popis</span><span class="sxs-lookup"><span data-stu-id="52149-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="52149-110">Základní dotazy (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="52149-110">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)|<span data-ttu-id="52149-111">Obsahuje běžné příklady dotazování stromy XML.</span><span class="sxs-lookup"><span data-stu-id="52149-111">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="52149-112">Projekce a transformace (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="52149-112">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)|<span data-ttu-id="52149-113">Poskytuje běžných příkladů projekce z a transformace stromy XML.</span><span class="sxs-lookup"><span data-stu-id="52149-113">Provides common examples of projecting from and transforming XML trees.</span></span>|  
|[<span data-ttu-id="52149-114">Pokročilé techniky dotazu (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="52149-114">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)|<span data-ttu-id="52149-115">Poskytuje techniky dotazu, které jsou užitečné v pokročilejší scénáře.</span><span class="sxs-lookup"><span data-stu-id="52149-115">Provides query techniques that are useful in more advanced scenarios.</span></span>|  
|[<span data-ttu-id="52149-116">Technologie LINQ to XML pro uživatele XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="52149-116">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)|<span data-ttu-id="52149-117">Uvede počet výrazech XPath a jejich [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ekvivalenty.</span><span class="sxs-lookup"><span data-stu-id="52149-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] equivalents.</span></span>|  
|[<span data-ttu-id="52149-118">Čistý funkční transformace XML (C#)</span><span class="sxs-lookup"><span data-stu-id="52149-118">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)|<span data-ttu-id="52149-119">Uvede malé kurz zápis dotazů ve stylu funkční programování.</span><span class="sxs-lookup"><span data-stu-id="52149-119">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="52149-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="52149-120">See Also</span></span>  
 [<span data-ttu-id="52149-121">Průvodce programováním (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="52149-121">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)  
 [<span data-ttu-id="52149-122">Začínáme s dotazy LINQ v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="52149-122">Getting Started with LINQ in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
