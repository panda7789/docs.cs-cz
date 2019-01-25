---
title: Řazení výsledků klauzule join (LINQ v JAZYKU C#)
description: Zjistěte, jak řazení výsledků klauzule join LINQ v jazyce C#.
ms.date: 12/01/2016
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: f60000b83bf378dd8740b7255d421dd4335614c4
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857885"
---
# <a name="order-the-results-of-a-join-clause"></a><span data-ttu-id="d423a-103">Řazení výsledků klauzule join</span><span class="sxs-lookup"><span data-stu-id="d423a-103">Order the results of a join clause</span></span>

<span data-ttu-id="d423a-104">Tento příklad ukazuje způsob řazení výsledků operace spojení.</span><span class="sxs-lookup"><span data-stu-id="d423a-104">This example shows how to order the results of a join operation.</span></span> <span data-ttu-id="d423a-105">Všimněte si, že řazení se provádí po spojení.</span><span class="sxs-lookup"><span data-stu-id="d423a-105">Note that the ordering is performed after the join.</span></span> <span data-ttu-id="d423a-106">Přestože lze použít `orderby` klauzule s jedním nebo více zdroji pořadí před spojení, obecně nedoporučujeme to.</span><span class="sxs-lookup"><span data-stu-id="d423a-106">Although you can use an `orderby` clause with one or more of the source sequences before the join, generally we do not recommend it.</span></span> <span data-ttu-id="d423a-107">Někteří poskytovatelé LINQ nemusí zachovávají řazení po spojení.</span><span class="sxs-lookup"><span data-stu-id="d423a-107">Some LINQ providers might not preserve that ordering after the join.</span></span>

## <a name="example"></a><span data-ttu-id="d423a-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="d423a-108">Example</span></span>

<span data-ttu-id="d423a-109">Tento dotaz vytvoří spojení skupiny a pak seřadí podle kategorie element, který je stále v oboru skupiny.</span><span class="sxs-lookup"><span data-stu-id="d423a-109">This query creates a group join, and then sorts the groups based on the category element, which is still in scope.</span></span> <span data-ttu-id="d423a-110">Uvnitř inicializátor anonymního typu orders poddotazu odpovídajících prvků z posloupnosti produktů.</span><span class="sxs-lookup"><span data-stu-id="d423a-110">Inside the anonymous type initializer, a sub-query orders all the matching elements from the products sequence.</span></span>

[!code-csharp[csProgGuideLINQ#81](~/samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]

## <a name="see-also"></a><span data-ttu-id="d423a-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d423a-111">See also</span></span>

- [<span data-ttu-id="d423a-112">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="d423a-112">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="d423a-113">orderby – klauzule</span><span class="sxs-lookup"><span data-stu-id="d423a-113">orderby clause</span></span>](../language-reference/keywords/orderby-clause.md)
- [<span data-ttu-id="d423a-114">join – klauzule</span><span class="sxs-lookup"><span data-stu-id="d423a-114">join clause</span></span>](../language-reference/keywords/join-clause.md)
