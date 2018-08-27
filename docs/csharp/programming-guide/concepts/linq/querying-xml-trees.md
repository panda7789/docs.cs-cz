---
title: Dotazování na stromy XML (C#)
ms.date: 07/20/2015
ms.assetid: 0913d81b-541a-4fd4-9cbf-7ec89fd817ea
ms.openlocfilehash: 5d2e40da26f30a0ece570acf2fd25684d1cba40f
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925582"
---
# <a name="querying-xml-trees-c"></a><span data-ttu-id="5ff0c-102">Dotazování na stromy XML (C#)</span><span class="sxs-lookup"><span data-stu-id="5ff0c-102">Querying XML Trees (C#)</span></span>
<span data-ttu-id="5ff0c-103">Tato část obsahuje příklady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="5ff0c-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
 <span data-ttu-id="5ff0c-104">Další informace o psaní [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy, naleznete v tématu [Začínáme s dotazy LINQ v jazyce C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="5ff0c-104">For more information about writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, see [Getting Started with LINQ in C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="5ff0c-105">Po instanci stromu XML psaní dotazů je nejúčinnější způsob, jak extrahovat data ze stromu.</span><span class="sxs-lookup"><span data-stu-id="5ff0c-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="5ff0c-106">Kromě toho dotazu v kombinaci s funkční konstrukce umožňuje generovat nový dokument XML, který má odlišném tvaru z původního dokumentu.</span><span class="sxs-lookup"><span data-stu-id="5ff0c-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5ff0c-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="5ff0c-107">In This Section</span></span>  
  
|<span data-ttu-id="5ff0c-108">Téma</span><span class="sxs-lookup"><span data-stu-id="5ff0c-108">Topic</span></span>|<span data-ttu-id="5ff0c-109">Popis</span><span class="sxs-lookup"><span data-stu-id="5ff0c-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="5ff0c-110">Základní dotazy (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="5ff0c-110">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)|<span data-ttu-id="5ff0c-111">Poskytuje běžné příklady dotazování na stromy XML.</span><span class="sxs-lookup"><span data-stu-id="5ff0c-111">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="5ff0c-112">Projekce a transformace (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="5ff0c-112">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)|<span data-ttu-id="5ff0c-113">Poskytuje běžné příklady z projekce a transformace stromů XML.</span><span class="sxs-lookup"><span data-stu-id="5ff0c-113">Provides common examples of projecting from and transforming XML trees.</span></span>|  
|[<span data-ttu-id="5ff0c-114">Pokročilé techniky dotazování (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="5ff0c-114">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)|<span data-ttu-id="5ff0c-115">Poskytuje technik dotazu, které jsou užitečné v pokročilejších scénářích.</span><span class="sxs-lookup"><span data-stu-id="5ff0c-115">Provides query techniques that are useful in more advanced scenarios.</span></span>|  
|[<span data-ttu-id="5ff0c-116">LINQ to XML pro uživatele jazyka XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="5ff0c-116">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)|<span data-ttu-id="5ff0c-117">Uvede počet výrazů XPath a jejich [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ekvivalenty.</span><span class="sxs-lookup"><span data-stu-id="5ff0c-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] equivalents.</span></span>|  
|[<span data-ttu-id="5ff0c-118">Čistě funkční transformace XML (C#)</span><span class="sxs-lookup"><span data-stu-id="5ff0c-118">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)|<span data-ttu-id="5ff0c-119">Uvede počet malých kurzu o psaní dotazů ve stylu funkčního programování.</span><span class="sxs-lookup"><span data-stu-id="5ff0c-119">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5ff0c-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ff0c-120">See Also</span></span>  
 [<span data-ttu-id="5ff0c-121">Průvodce programováním (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="5ff0c-121">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)  
 [<span data-ttu-id="5ff0c-122">Začínáme s dotazy LINQ v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="5ff0c-122">Getting Started with LINQ in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
