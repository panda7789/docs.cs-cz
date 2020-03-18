---
title: Pořadívýsledků join klauzule (LINQ v C#)
description: Přečtěte si, jak objednat výsledky klauzule linq spojení v C#.
ms.date: 12/01/2016
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: f60000b83bf378dd8740b7255d421dd4335614c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659862"
---
# <a name="order-the-results-of-a-join-clause"></a><span data-ttu-id="822fa-103">Řazení výsledků klauzule join</span><span class="sxs-lookup"><span data-stu-id="822fa-103">Order the results of a join clause</span></span>

<span data-ttu-id="822fa-104">Tento příklad ukazuje, jak objednat výsledky operace spojení.</span><span class="sxs-lookup"><span data-stu-id="822fa-104">This example shows how to order the results of a join operation.</span></span> <span data-ttu-id="822fa-105">Všimněte si, že řazení se provádí po spojení.</span><span class="sxs-lookup"><span data-stu-id="822fa-105">Note that the ordering is performed after the join.</span></span> <span data-ttu-id="822fa-106">I když můžete `orderby` použít klauzuli s jedním nebo více zdrojových sekvencí před spojením, obecně nedoporučujeme.</span><span class="sxs-lookup"><span data-stu-id="822fa-106">Although you can use an `orderby` clause with one or more of the source sequences before the join, generally we do not recommend it.</span></span> <span data-ttu-id="822fa-107">Někteří zprostředkovatelé LINQ nemusí zachovat toto řazení po spojení.</span><span class="sxs-lookup"><span data-stu-id="822fa-107">Some LINQ providers might not preserve that ordering after the join.</span></span>

## <a name="example"></a><span data-ttu-id="822fa-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="822fa-108">Example</span></span>

<span data-ttu-id="822fa-109">Tento dotaz vytvoří spojení skupiny a potom seřadí skupiny na základě prvku kategorie, který je stále v oboru.</span><span class="sxs-lookup"><span data-stu-id="822fa-109">This query creates a group join, and then sorts the groups based on the category element, which is still in scope.</span></span> <span data-ttu-id="822fa-110">Uvnitř anonymní typ inicializátoru, dílčí dotaz objednávky všechny odpovídající prvky z řady produktů.</span><span class="sxs-lookup"><span data-stu-id="822fa-110">Inside the anonymous type initializer, a sub-query orders all the matching elements from the products sequence.</span></span>

[!code-csharp[csProgGuideLINQ#81](~/samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]

## <a name="see-also"></a><span data-ttu-id="822fa-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="822fa-111">See also</span></span>

- [<span data-ttu-id="822fa-112">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="822fa-112">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="822fa-113">orderby – klauzule</span><span class="sxs-lookup"><span data-stu-id="822fa-113">orderby clause</span></span>](../language-reference/keywords/orderby-clause.md)
- [<span data-ttu-id="822fa-114">spojit klauzuli</span><span class="sxs-lookup"><span data-stu-id="822fa-114">join clause</span></span>](../language-reference/keywords/join-clause.md)
