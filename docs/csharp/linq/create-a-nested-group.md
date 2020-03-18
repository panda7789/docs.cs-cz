---
title: Vytvoření vnořené skupiny (LINQ v C#)
description: Zjistěte, jak vytvořit vnořenou skupinu ve výrazu dotazu LINQ v c#.
ms.date: 12/01/2016
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: 7d056c9e215ccc7ca24d621b64e2328bed79f22e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "61688615"
---
# <a name="create-a-nested-group"></a><span data-ttu-id="5c865-103">Vytvoření vnořené skupiny</span><span class="sxs-lookup"><span data-stu-id="5c865-103">Create a nested group</span></span>

<span data-ttu-id="5c865-104">Následující příklad ukazuje, jak vytvořit vnořené skupiny ve výrazu dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="5c865-104">The following example shows how to create nested groups in a LINQ query expression.</span></span> <span data-ttu-id="5c865-105">Každá skupina, která je vytvořena podle studentského roku nebo stupně úrovně je pak dále rozdělena do skupin na základě jmen jednotlivců .</span><span class="sxs-lookup"><span data-stu-id="5c865-105">Each group that is created according to student year or grade level is then further subdivided into groups based on the individuals' names.</span></span>

## <a name="example"></a><span data-ttu-id="5c865-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="5c865-106">Example</span></span>

> [!NOTE]
> <span data-ttu-id="5c865-107">Tento příklad obsahuje odkazy na objekty, které jsou definovány v ukázkovém kódu v [aplikaci Query a collection of objects](query-a-collection-of-objects.md).</span><span class="sxs-lookup"><span data-stu-id="5c865-107">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span>

[!code-csharp[csProgGuideLINQ#24](~/samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]

<span data-ttu-id="5c865-108">Všimněte si, `foreach` že tři vnořené smyčky jsou vyžadovány k iteraci přes vnitřní prvky vnořené skupiny.</span><span class="sxs-lookup"><span data-stu-id="5c865-108">Note that three nested `foreach` loops are required to iterate over the inner elements of a nested group.</span></span>

## <a name="see-also"></a><span data-ttu-id="5c865-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="5c865-109">See also</span></span>

- [<span data-ttu-id="5c865-110">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="5c865-110">Language Integrated Query (LINQ)</span></span>](index.md)
