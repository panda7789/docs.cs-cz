---
title: Provádění poddotazů na operace seskupení (LINQ v JAZYKU C#)
description: Jak k provádění poddotazů na operace seskupení pomocí jazyka LINQ v jazyce C#.
ms.date: 12/1/2016
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
ms.openlocfilehash: 514db81b80557a3026589f00177910cc9446c0f4
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45971236"
---
# <a name="perform-a-subquery-on-a-grouping-operation"></a><span data-ttu-id="d9e14-103">Provádění poddotazů na operace seskupení</span><span class="sxs-lookup"><span data-stu-id="d9e14-103">Perform a subquery on a grouping operation</span></span>

<span data-ttu-id="d9e14-104">Tento článek popisuje dva různé způsoby vytvoření dotazu, který seřadí zdroj dat do skupin a potom provede poddotaz v každé skupině jednotlivě.</span><span class="sxs-lookup"><span data-stu-id="d9e14-104">This article shows two different ways to create a query that orders the source data into groups, and then performs a subquery over each group individually.</span></span> <span data-ttu-id="d9e14-105">Základní postup v obou příkladech je seskupení zdrojové prvky pomocí *pokračování* s názvem `newGroup`a potom generovat nové poddotaz proti `newGroup`.</span><span class="sxs-lookup"><span data-stu-id="d9e14-105">The basic technique in each example is to group the source elements by using a *continuation* named `newGroup`, and then generating a new subquery against `newGroup`.</span></span> <span data-ttu-id="d9e14-106">Tato poddotaz spustí pro každou novou skupinu, která se vytvořila vnější dotaz.</span><span class="sxs-lookup"><span data-stu-id="d9e14-106">This subquery is run against each new group that is created by the outer query.</span></span> <span data-ttu-id="d9e14-107">Všimněte si, že v tomto konkrétním příkladu závěrečný výstup skupinu, ale plochý sekvence anonymních typů.</span><span class="sxs-lookup"><span data-stu-id="d9e14-107">Note that in this particular example the final output is not a group, but a flat sequence of anonymous types.</span></span>  
  
<span data-ttu-id="d9e14-108">Další informace o tom, jak skupiny, najdete v části [group – klauzule](../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d9e14-108">For more information about how to group, see [group clause](../language-reference/keywords/group-clause.md).</span></span>  
  
<span data-ttu-id="d9e14-109">Další informace o pokračování naleznete v tématu [do](../language-reference/keywords/into.md).</span><span class="sxs-lookup"><span data-stu-id="d9e14-109">For more information about continuations, see [into](../language-reference/keywords/into.md).</span></span> <span data-ttu-id="d9e14-110">Následující příklad používá jako zdroj dat pro strukturu dat v paměti, ale stejné zásady platí i pro jakýkoli druh zdroje dat LINQ.</span><span class="sxs-lookup"><span data-stu-id="d9e14-110">The following example uses an in-memory data structure as the data source, but the same principles apply for any kind of LINQ data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9e14-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="d9e14-111">Example</span></span>

> [!NOTE]
> <span data-ttu-id="d9e14-112">Obsahuje odkazy na objekty, které jsou definovány ve vzorovém kódu v tomto příkladu [dotazování na kolekci objektů](query-a-collection-of-objects.md).</span><span class="sxs-lookup"><span data-stu-id="d9e14-112">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span>

[!code-csharp[csProgGuideLINQ#23](~/samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]  

## <a name="see-also"></a><span data-ttu-id="d9e14-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d9e14-113">See also</span></span>

- [<span data-ttu-id="d9e14-114">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="d9e14-114">Language Integrated Query (LINQ)</span></span>](index.md)
