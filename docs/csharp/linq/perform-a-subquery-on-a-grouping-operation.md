---
title: "Provádění poddotazů na skupinách"
description: "Postup provádění poddotazů na skupinách."
keywords: "Rozhraní .NET, rozhraní .NET core, C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
ms.openlocfilehash: f638b8a679a15891d04e02f1597d6bf7934a9e74
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2017
---
# <a name="perform-a-subquery-on-a-grouping-operation"></a><span data-ttu-id="6233e-104">Provádění poddotazů na skupinách</span><span class="sxs-lookup"><span data-stu-id="6233e-104">Perform a subquery on a grouping operation</span></span>

<span data-ttu-id="6233e-105">Toto téma ukazuje dva různé způsoby vytvoření dotaz, který řadí zdrojová data do skupin a potom provede poddotazu přes každou skupinu jednotlivě.</span><span class="sxs-lookup"><span data-stu-id="6233e-105">This topic shows two different ways to create a query that orders the source data into groups, and then performs a subquery over each group individually.</span></span> <span data-ttu-id="6233e-106">Základní technika v obou příkladech je seskupit pomocí zdrojové elementy *pokračování* s názvem `newGroup`a pak generovat nové poddotazu proti `newGroup`.</span><span class="sxs-lookup"><span data-stu-id="6233e-106">The basic technique in each example is to group the source elements by using a *continuation* named `newGroup`, and then generating a new subquery against `newGroup`.</span></span> <span data-ttu-id="6233e-107">Tato poddotazu je spustit pro každou novou skupinu, který byl vytvořený vnější dotazu.</span><span class="sxs-lookup"><span data-stu-id="6233e-107">This subquery is run against each new group that is created by the outer query.</span></span> <span data-ttu-id="6233e-108">Všimněte si, že v tomto konkrétním příkladu finální výstup není skupinu, ale ploché posloupnost anonymní typy.</span><span class="sxs-lookup"><span data-stu-id="6233e-108">Note that in this particular example the final output is not a group, but a flat sequence of anonymous types.</span></span>  
  
 <span data-ttu-id="6233e-109">Další informace o tom, jak skupiny najdete v tématu [group – klauzule](../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="6233e-109">For more information about how to group, see [group clause](../language-reference/keywords/group-clause.md).</span></span>  
  
 <span data-ttu-id="6233e-110">Další informace o pokračování najdete v tématu [do](../language-reference/keywords/into.md).</span><span class="sxs-lookup"><span data-stu-id="6233e-110">For more information about continuations, see [into](../language-reference/keywords/into.md).</span></span> <span data-ttu-id="6233e-111">Následující příklad používá jako zdroj dat pro strukturu dat v paměti, ale stejné zásady platí pro libovolný zdroj dat LINQ.</span><span class="sxs-lookup"><span data-stu-id="6233e-111">The following example uses an in-memory data structure as the data source, but the same principles apply for any kind of LINQ data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6233e-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="6233e-112">Example</span></span> 

 > [!NOTE]
 > <span data-ttu-id="6233e-113">Tento příklad obsahuje odkazy na objekty, které jsou definovány v ukázkovém kódu v [dotazování na kolekci objektů](query-a-collection-of-objects.md).</span><span class="sxs-lookup"><span data-stu-id="6233e-113">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span>

 [!code-csharp[csProgGuideLINQ#23](../../../samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]  
   
## <a name="see-also"></a><span data-ttu-id="6233e-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="6233e-114">See also</span></span>  
 [<span data-ttu-id="6233e-115">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="6233e-115">LINQ Query Expressions</span></span>](index.md)
