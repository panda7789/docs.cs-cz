---
title: "Řazení výsledků klauzule join"
description: "Postup řazení výsledků klauzule join."
keywords: "Rozhraní .NET, rozhraní .NET core, C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: f948c18fb16a4f3ac02945b4a63583f1b01cad40
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="order-the-results-of-a-join-clause"></a><span data-ttu-id="2019c-104">Řazení výsledků klauzule join</span><span class="sxs-lookup"><span data-stu-id="2019c-104">Order the results of a join clause</span></span>
<span data-ttu-id="2019c-105">Tento příklad ukazuje postup řazení výsledků operace spojení.</span><span class="sxs-lookup"><span data-stu-id="2019c-105">This example shows how to order the results of a join operation.</span></span> <span data-ttu-id="2019c-106">Všimněte si, že je po spojení provést řazení.</span><span class="sxs-lookup"><span data-stu-id="2019c-106">Note that the ordering is performed after the join.</span></span> <span data-ttu-id="2019c-107">Přestože je možné použít `orderby` klauzule s jedním nebo více zdroje pořadí před spojení, obecně nedoporučujeme ji.</span><span class="sxs-lookup"><span data-stu-id="2019c-107">Although you can use an `orderby` clause with one or more of the source sequences before the join, generally we do not recommend it.</span></span> <span data-ttu-id="2019c-108">Někteří poskytovatelé LINQ nemusí zachovat řazení po spojení.</span><span class="sxs-lookup"><span data-stu-id="2019c-108">Some LINQ providers might not preserve that ordering after the join.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2019c-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="2019c-109">Example</span></span>  
 <span data-ttu-id="2019c-110">Tento dotaz vytvoří spojení skupiny a potom seřadí skupiny založené na kategorii element, který je stále v oboru.</span><span class="sxs-lookup"><span data-stu-id="2019c-110">This query creates a group join, and then sorts the groups based on the category element, which is still in scope.</span></span> <span data-ttu-id="2019c-111">Uvnitř inicializátoru anonymního typu poddotazu řadí všechny odpovídající elementy z produktů pořadí.</span><span class="sxs-lookup"><span data-stu-id="2019c-111">Inside the anonymous type initializer, a sub-query orders all the matching elements from the products sequence.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#81](../../../samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]  
 
## <a name="see-also"></a><span data-ttu-id="2019c-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="2019c-112">See also</span></span>  
 [<span data-ttu-id="2019c-113">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="2019c-113">LINQ query expressions</span></span>](index.md)  
 [<span data-ttu-id="2019c-114">OrderBy – klauzule</span><span class="sxs-lookup"><span data-stu-id="2019c-114">orderby clause</span></span>](../language-reference/keywords/orderby-clause.md)  
 [<span data-ttu-id="2019c-115">JOIN – klauzule</span><span class="sxs-lookup"><span data-stu-id="2019c-115">join clause</span></span>](../language-reference/keywords/join-clause.md) 
