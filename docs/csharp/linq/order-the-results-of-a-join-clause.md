---
title: Řazení výsledků klauzule join (LINQ v JAZYKU C#)
description: Zjistěte, jak řazení výsledků klauzule join LINQ v jazyce C#.
ms.date: 12/1/2016
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: e4a12b6f9b4a99decb1f64524ebe67a196084a04
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404733"
---
# <a name="order-the-results-of-a-join-clause"></a><span data-ttu-id="78846-103">Řazení výsledků klauzule join</span><span class="sxs-lookup"><span data-stu-id="78846-103">Order the results of a join clause</span></span>

<span data-ttu-id="78846-104">Tento příklad ukazuje způsob řazení výsledků operace spojení.</span><span class="sxs-lookup"><span data-stu-id="78846-104">This example shows how to order the results of a join operation.</span></span> <span data-ttu-id="78846-105">Všimněte si, že řazení se provádí po spojení.</span><span class="sxs-lookup"><span data-stu-id="78846-105">Note that the ordering is performed after the join.</span></span> <span data-ttu-id="78846-106">Přestože lze použít `orderby` klauzule s jedním nebo více zdroji pořadí před spojení, obecně nedoporučujeme to.</span><span class="sxs-lookup"><span data-stu-id="78846-106">Although you can use an `orderby` clause with one or more of the source sequences before the join, generally we do not recommend it.</span></span> <span data-ttu-id="78846-107">Někteří poskytovatelé LINQ nemusí zachovávají řazení po spojení.</span><span class="sxs-lookup"><span data-stu-id="78846-107">Some LINQ providers might not preserve that ordering after the join.</span></span>

## <a name="example"></a><span data-ttu-id="78846-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="78846-108">Example</span></span>

<span data-ttu-id="78846-109">Tento dotaz vytvoří spojení skupiny a pak seřadí podle kategorie element, který je stále v oboru skupiny.</span><span class="sxs-lookup"><span data-stu-id="78846-109">This query creates a group join, and then sorts the groups based on the category element, which is still in scope.</span></span> <span data-ttu-id="78846-110">Uvnitř inicializátor anonymního typu orders poddotazu odpovídajících prvků z posloupnosti produktů.</span><span class="sxs-lookup"><span data-stu-id="78846-110">Inside the anonymous type initializer, a sub-query orders all the matching elements from the products sequence.</span></span>

[!code-csharp[csProgGuideLINQ#81](~/samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]

## <a name="see-also"></a><span data-ttu-id="78846-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="78846-111">See also</span></span>

[<span data-ttu-id="78846-112">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="78846-112">Language Integrated Query (LINQ)</span></span>](index.md)  
[<span data-ttu-id="78846-113">orderby – klauzule</span><span class="sxs-lookup"><span data-stu-id="78846-113">orderby clause</span></span>](../language-reference/keywords/orderby-clause.md)  
[<span data-ttu-id="78846-114">join – klauzule</span><span class="sxs-lookup"><span data-stu-id="78846-114">join clause</span></span>](../language-reference/keywords/join-clause.md)  