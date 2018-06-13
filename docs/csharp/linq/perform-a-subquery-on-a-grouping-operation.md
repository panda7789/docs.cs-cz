---
title: Provádění poddotazů na skupinách
description: Postup provádění poddotazů na skupinách.
ms.date: 12/1/2016
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
ms.openlocfilehash: 209d05c2fe8719fa9116061d199272366146f465
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277326"
---
# <a name="perform-a-subquery-on-a-grouping-operation"></a><span data-ttu-id="c8242-103">Provádění poddotazů na skupinách</span><span class="sxs-lookup"><span data-stu-id="c8242-103">Perform a subquery on a grouping operation</span></span>

<span data-ttu-id="c8242-104">Toto téma ukazuje dva různé způsoby vytvoření dotaz, který řadí zdrojová data do skupin a potom provede poddotazu přes každou skupinu jednotlivě.</span><span class="sxs-lookup"><span data-stu-id="c8242-104">This topic shows two different ways to create a query that orders the source data into groups, and then performs a subquery over each group individually.</span></span> <span data-ttu-id="c8242-105">Základní technika v obou příkladech je seskupit pomocí zdrojové elementy *pokračování* s názvem `newGroup`a pak generovat nové poddotazu proti `newGroup`.</span><span class="sxs-lookup"><span data-stu-id="c8242-105">The basic technique in each example is to group the source elements by using a *continuation* named `newGroup`, and then generating a new subquery against `newGroup`.</span></span> <span data-ttu-id="c8242-106">Tato poddotazu je spustit pro každou novou skupinu, který byl vytvořený vnější dotazu.</span><span class="sxs-lookup"><span data-stu-id="c8242-106">This subquery is run against each new group that is created by the outer query.</span></span> <span data-ttu-id="c8242-107">Všimněte si, že v tomto konkrétním příkladu finální výstup není skupinu, ale ploché posloupnost anonymní typy.</span><span class="sxs-lookup"><span data-stu-id="c8242-107">Note that in this particular example the final output is not a group, but a flat sequence of anonymous types.</span></span>  
  
 <span data-ttu-id="c8242-108">Další informace o tom, jak skupiny najdete v tématu [group – klauzule](../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="c8242-108">For more information about how to group, see [group clause](../language-reference/keywords/group-clause.md).</span></span>  
  
 <span data-ttu-id="c8242-109">Další informace o pokračování najdete v tématu [do](../language-reference/keywords/into.md).</span><span class="sxs-lookup"><span data-stu-id="c8242-109">For more information about continuations, see [into](../language-reference/keywords/into.md).</span></span> <span data-ttu-id="c8242-110">Následující příklad používá jako zdroj dat pro strukturu dat v paměti, ale stejné zásady platí pro libovolný zdroj dat LINQ.</span><span class="sxs-lookup"><span data-stu-id="c8242-110">The following example uses an in-memory data structure as the data source, but the same principles apply for any kind of LINQ data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8242-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="c8242-111">Example</span></span> 

 > [!NOTE]
 > <span data-ttu-id="c8242-112">Tento příklad obsahuje odkazy na objekty, které jsou definovány v ukázkovém kódu v [dotazování na kolekci objektů](query-a-collection-of-objects.md).</span><span class="sxs-lookup"><span data-stu-id="c8242-112">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span>

 [!code-csharp[csProgGuideLINQ#23](../../../samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]  
   
## <a name="see-also"></a><span data-ttu-id="c8242-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="c8242-113">See also</span></span>  
 [<span data-ttu-id="c8242-114">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="c8242-114">LINQ Query Expressions</span></span>](index.md)
