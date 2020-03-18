---
title: Provedení poddotazu na operaci seskupení (LINQ v c#)
description: Jak provést poddotaz na operaci seskupení pomocí LINQ v C#.
ms.date: 12/01/2016
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
ms.openlocfilehash: fd26f87ad7d5b4892f086bf8c7a34cf19a7f9e02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173364"
---
# <a name="perform-a-subquery-on-a-grouping-operation"></a><span data-ttu-id="819e4-103">Provádění poddotazů na skupinách</span><span class="sxs-lookup"><span data-stu-id="819e4-103">Perform a subquery on a grouping operation</span></span>

<span data-ttu-id="819e4-104">Tento článek ukazuje dva různé způsoby, jak vytvořit dotaz, který seřazuje zdrojová data do skupin a potom provádí poddotaz na každou skupinu jednotlivě.</span><span class="sxs-lookup"><span data-stu-id="819e4-104">This article shows two different ways to create a query that orders the source data into groups, and then performs a subquery over each group individually.</span></span> <span data-ttu-id="819e4-105">Základní technikou v každém příkladu je seskupit zdrojové prvky pomocí `newGroup` *pokračování* s názvem `newGroup`a potom generování nového poddotazu proti .</span><span class="sxs-lookup"><span data-stu-id="819e4-105">The basic technique in each example is to group the source elements by using a *continuation* named `newGroup`, and then generating a new subquery against `newGroup`.</span></span> <span data-ttu-id="819e4-106">Tento poddotaz je spuštěn proti každé nové skupině, která je vytvořena vnějším dotazem.</span><span class="sxs-lookup"><span data-stu-id="819e4-106">This subquery is run against each new group that is created by the outer query.</span></span> <span data-ttu-id="819e4-107">Všimněte si, že v tomto konkrétním příkladu konečný výstup není skupina, ale ploché posloupnosti anonymních typů.</span><span class="sxs-lookup"><span data-stu-id="819e4-107">Note that in this particular example the final output is not a group, but a flat sequence of anonymous types.</span></span>  
  
<span data-ttu-id="819e4-108">Další informace o způsobu seskupení naleznete v [tématu group clause](../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="819e4-108">For more information about how to group, see [group clause](../language-reference/keywords/group-clause.md).</span></span>  
  
<span data-ttu-id="819e4-109">Další informace o pokračování naleznete [v tématu](../language-reference/keywords/into.md).</span><span class="sxs-lookup"><span data-stu-id="819e4-109">For more information about continuations, see [into](../language-reference/keywords/into.md).</span></span> <span data-ttu-id="819e4-110">Následující příklad používá jako zdroj dat strukturu dat v paměti, ale stejné zásady platí pro jakýkoli druh zdroje dat LINQ.</span><span class="sxs-lookup"><span data-stu-id="819e4-110">The following example uses an in-memory data structure as the data source, but the same principles apply for any kind of LINQ data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="819e4-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="819e4-111">Example</span></span>

> [!NOTE]
> <span data-ttu-id="819e4-112">Tento příklad obsahuje odkazy na objekty, které jsou definovány v ukázkovém kódu v [aplikaci Query a collection of objects](query-a-collection-of-objects.md).</span><span class="sxs-lookup"><span data-stu-id="819e4-112">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span>

[!code-csharp[csProgGuideLINQ#23](~/samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]

<span data-ttu-id="819e4-113">Dotaz ve výše uvedeném fragmentu výstřižek lze také zapsat pomocí syntaxe metody.</span><span class="sxs-lookup"><span data-stu-id="819e4-113">The query in the snippet above can also be written using method syntax.</span></span> <span data-ttu-id="819e4-114">Následující fragment kódu má sémanticky ekvivalentní dotaz napsaný pomocí syntaxe metody.</span><span class="sxs-lookup"><span data-stu-id="819e4-114">The following code snippet has a semantically equivalent query written using method syntax.</span></span>

[!code-csharp[csProgGuideLINQ#86](~/samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_2.cs)]

## <a name="see-also"></a><span data-ttu-id="819e4-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="819e4-115">See also</span></span>

- [<span data-ttu-id="819e4-116">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="819e4-116">Language Integrated Query (LINQ)</span></span>](index.md)
