---
title: Vytvoření vnořené skupiny (LINQ v JAZYKU C#)
description: Informace o vytvoření vnořené skupiny ve výrazu dotazu LINQ v jazyce C#.
ms.date: 12/1/2016
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: c973048d0859f61596c62c294131b8c00d0039f8
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404746"
---
# <a name="create-a-nested-group"></a><span data-ttu-id="a41ae-103">Vytvoření vnořené skupiny</span><span class="sxs-lookup"><span data-stu-id="a41ae-103">Create a nested group</span></span>

<span data-ttu-id="a41ae-104">Následující příklad ukazuje, jak vytvářet vnořené skupiny ve výrazu dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="a41ae-104">The following example shows how to create nested groups in a LINQ query expression.</span></span> <span data-ttu-id="a41ae-105">Každá skupina, která je vytvořena podle úrovně rok nebo na podnikové úrovni student je pak dále rozdělená do skupin na základě názvů pro osob.</span><span class="sxs-lookup"><span data-stu-id="a41ae-105">Each group that is created according to student year or grade level is then further subdivided into groups based on the individuals' names.</span></span>

## <a name="example"></a><span data-ttu-id="a41ae-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="a41ae-106">Example</span></span>

> [!NOTE]
> <span data-ttu-id="a41ae-107">Obsahuje odkazy na objekty, které jsou definovány ve vzorovém kódu v tomto příkladu [dotazování na kolekci objektů](query-a-collection-of-objects.md).</span><span class="sxs-lookup"><span data-stu-id="a41ae-107">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span>

[!code-csharp[csProgGuideLINQ#24](~/samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]

<span data-ttu-id="a41ae-108">Všimněte si, že tři vnořené `foreach` smyčky jsou nutné k iteraci přes vnitřní elementy vnořené skupiny.</span><span class="sxs-lookup"><span data-stu-id="a41ae-108">Note that three nested `foreach` loops are required to iterate over the inner elements of a nested group.</span></span>

## <a name="see-also"></a><span data-ttu-id="a41ae-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a41ae-109">See also</span></span>

[<span data-ttu-id="a41ae-110">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="a41ae-110">Language Integrated Query (LINQ)</span></span>](index.md)
