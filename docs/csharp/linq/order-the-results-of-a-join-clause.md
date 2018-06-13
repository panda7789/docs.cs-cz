---
title: Řazení výsledků klauzule join
description: Postup řazení výsledků klauzule join.
ms.date: 12/1/2016
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: f426152e614ed9a9c4aa41d7ba7cb8ddf1cd3063
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269697"
---
# <a name="order-the-results-of-a-join-clause"></a><span data-ttu-id="0c839-103">Řazení výsledků klauzule join</span><span class="sxs-lookup"><span data-stu-id="0c839-103">Order the results of a join clause</span></span>
<span data-ttu-id="0c839-104">Tento příklad ukazuje postup řazení výsledků operace spojení.</span><span class="sxs-lookup"><span data-stu-id="0c839-104">This example shows how to order the results of a join operation.</span></span> <span data-ttu-id="0c839-105">Všimněte si, že je po spojení provést řazení.</span><span class="sxs-lookup"><span data-stu-id="0c839-105">Note that the ordering is performed after the join.</span></span> <span data-ttu-id="0c839-106">Přestože je možné použít `orderby` klauzule s jedním nebo více zdroje pořadí před spojení, obecně nedoporučujeme ji.</span><span class="sxs-lookup"><span data-stu-id="0c839-106">Although you can use an `orderby` clause with one or more of the source sequences before the join, generally we do not recommend it.</span></span> <span data-ttu-id="0c839-107">Někteří poskytovatelé LINQ nemusí zachovat řazení po spojení.</span><span class="sxs-lookup"><span data-stu-id="0c839-107">Some LINQ providers might not preserve that ordering after the join.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c839-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="0c839-108">Example</span></span>  
 <span data-ttu-id="0c839-109">Tento dotaz vytvoří spojení skupiny a potom seřadí skupiny založené na kategorii element, který je stále v oboru.</span><span class="sxs-lookup"><span data-stu-id="0c839-109">This query creates a group join, and then sorts the groups based on the category element, which is still in scope.</span></span> <span data-ttu-id="0c839-110">Uvnitř inicializátoru anonymního typu poddotazu řadí všechny odpovídající elementy z produktů pořadí.</span><span class="sxs-lookup"><span data-stu-id="0c839-110">Inside the anonymous type initializer, a sub-query orders all the matching elements from the products sequence.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#81](../../../samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]  
 
## <a name="see-also"></a><span data-ttu-id="0c839-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="0c839-111">See also</span></span>  
 [<span data-ttu-id="0c839-112">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="0c839-112">LINQ query expressions</span></span>](index.md)  
 [<span data-ttu-id="0c839-113">orderby – klauzule</span><span class="sxs-lookup"><span data-stu-id="0c839-113">orderby clause</span></span>](../language-reference/keywords/orderby-clause.md)  
 [<span data-ttu-id="0c839-114">join – klauzule</span><span class="sxs-lookup"><span data-stu-id="0c839-114">join clause</span></span>](../language-reference/keywords/join-clause.md) 
