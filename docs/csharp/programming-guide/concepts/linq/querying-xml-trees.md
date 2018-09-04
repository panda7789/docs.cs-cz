---
title: Dotazování na stromy XML (C#)
ms.date: 07/20/2015
ms.assetid: 0913d81b-541a-4fd4-9cbf-7ec89fd817ea
ms.openlocfilehash: 349235689dba125f697d0df5ff90bd10a69432c5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43501048"
---
# <a name="querying-xml-trees-c"></a><span data-ttu-id="d1885-102">Dotazování na stromy XML (C#)</span><span class="sxs-lookup"><span data-stu-id="d1885-102">Querying XML Trees (C#)</span></span>
<span data-ttu-id="d1885-103">Tato část obsahuje příklady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="d1885-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
 <span data-ttu-id="d1885-104">Další informace o psaní [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy, naleznete v tématu [Začínáme s dotazy LINQ v jazyce C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="d1885-104">For more information about writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, see [Getting Started with LINQ in C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="d1885-105">Po instanci stromu XML psaní dotazů je nejúčinnější způsob, jak extrahovat data ze stromu.</span><span class="sxs-lookup"><span data-stu-id="d1885-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="d1885-106">Kromě toho dotazu v kombinaci s funkční konstrukce umožňuje generovat nový dokument XML, který má odlišném tvaru z původního dokumentu.</span><span class="sxs-lookup"><span data-stu-id="d1885-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d1885-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d1885-107">In This Section</span></span>  
  
|<span data-ttu-id="d1885-108">Téma</span><span class="sxs-lookup"><span data-stu-id="d1885-108">Topic</span></span>|<span data-ttu-id="d1885-109">Popis</span><span class="sxs-lookup"><span data-stu-id="d1885-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="d1885-110">Základní dotazy (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d1885-110">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)|<span data-ttu-id="d1885-111">Poskytuje běžné příklady dotazování na stromy XML.</span><span class="sxs-lookup"><span data-stu-id="d1885-111">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="d1885-112">Projekce a transformace (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d1885-112">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)|<span data-ttu-id="d1885-113">Poskytuje běžné příklady z projekce a transformace stromů XML.</span><span class="sxs-lookup"><span data-stu-id="d1885-113">Provides common examples of projecting from and transforming XML trees.</span></span>|  
|[<span data-ttu-id="d1885-114">Pokročilé techniky dotazování (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d1885-114">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)|<span data-ttu-id="d1885-115">Poskytuje technik dotazu, které jsou užitečné v pokročilejších scénářích.</span><span class="sxs-lookup"><span data-stu-id="d1885-115">Provides query techniques that are useful in more advanced scenarios.</span></span>|  
|[<span data-ttu-id="d1885-116">LINQ to XML pro uživatele jazyka XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="d1885-116">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)|<span data-ttu-id="d1885-117">Uvede počet výrazů XPath a jejich [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ekvivalenty.</span><span class="sxs-lookup"><span data-stu-id="d1885-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] equivalents.</span></span>|  
|[<span data-ttu-id="d1885-118">Čistě funkční transformace XML (C#)</span><span class="sxs-lookup"><span data-stu-id="d1885-118">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)|<span data-ttu-id="d1885-119">Uvede počet malých kurzu o psaní dotazů ve stylu funkčního programování.</span><span class="sxs-lookup"><span data-stu-id="d1885-119">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d1885-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1885-120">See Also</span></span>

- [<span data-ttu-id="d1885-121">Průvodce programováním (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d1885-121">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)  
- [<span data-ttu-id="d1885-122">Začínáme s dotazy LINQ v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d1885-122">Getting Started with LINQ in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
