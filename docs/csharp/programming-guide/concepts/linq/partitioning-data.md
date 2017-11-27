---
title: Segmentace dat (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 32b95887e05767513dd818743dd1726149503b0f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="partitioning-data-c"></a><span data-ttu-id="d361d-102">Segmentace dat (C#)</span><span class="sxs-lookup"><span data-stu-id="d361d-102">Partitioning Data (C#)</span></span>
<span data-ttu-id="d361d-103">Vytváření oddílů v technologii LINQ odkazuje na operaci dělení vstupní pořadí na dva oddíly bez Změna uspořádání elementy a potom vrátí jeden z oddílů.</span><span class="sxs-lookup"><span data-stu-id="d361d-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="d361d-104">Následující obrázek znázorňuje výsledky tři různé rozdělení operace na posloupnost znaků.</span><span class="sxs-lookup"><span data-stu-id="d361d-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="d361d-105">První operace vrátí první tři elementy v pořadí.</span><span class="sxs-lookup"><span data-stu-id="d361d-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="d361d-106">Druhá operace přeskočí první tři elementy a vrátí zbývající elementy.</span><span class="sxs-lookup"><span data-stu-id="d361d-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="d361d-107">Třetí operaci přeskočí první dva elementy v pořadí a vrátí následující tři elementy.</span><span class="sxs-lookup"><span data-stu-id="d361d-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 <span data-ttu-id="d361d-108">![LINQ dělení Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span><span class="sxs-lookup"><span data-stu-id="d361d-108">![LINQ Partitioning Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span></span>  
  
 <span data-ttu-id="d361d-109">V následující části jsou uvedené metody operátor standardní dotazů, které oddílu pořadí.</span><span class="sxs-lookup"><span data-stu-id="d361d-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="d361d-110">Operátory</span><span class="sxs-lookup"><span data-stu-id="d361d-110">Operators</span></span>  
  
|<span data-ttu-id="d361d-111">Název operátoru</span><span class="sxs-lookup"><span data-stu-id="d361d-111">Operator Name</span></span>|<span data-ttu-id="d361d-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d361d-112">Description</span></span>|<span data-ttu-id="d361d-113">Syntaxe výrazu dotazu jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d361d-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="d361d-114">Další informace</span><span class="sxs-lookup"><span data-stu-id="d361d-114">More Information</span></span>|  
|-------------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="d361d-115">Skip</span><span class="sxs-lookup"><span data-stu-id="d361d-115">Skip</span></span>|<span data-ttu-id="d361d-116">Přeskočí elementy až zadané pozici v pořadí.</span><span class="sxs-lookup"><span data-stu-id="d361d-116">Skips elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="d361d-117">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="d361d-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d361d-118">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="d361d-118">SkipWhile</span></span>|<span data-ttu-id="d361d-119">Vynechá prvky podle funkce predikátu, dokud element nesplňuje podmínky.</span><span class="sxs-lookup"><span data-stu-id="d361d-119">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="d361d-120">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="d361d-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d361d-121">Take</span><span class="sxs-lookup"><span data-stu-id="d361d-121">Take</span></span>|<span data-ttu-id="d361d-122">Získá prvků až zadané pozici v pořadí.</span><span class="sxs-lookup"><span data-stu-id="d361d-122">Takes elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="d361d-123">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="d361d-123">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d361d-124">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="d361d-124">TakeWhile</span></span>|<span data-ttu-id="d361d-125">Získá prvků podle funkce predikátu, dokud element nesplňuje podmínky.</span><span class="sxs-lookup"><span data-stu-id="d361d-125">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="d361d-126">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="d361d-126">Not applicable.</span></span>|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="d361d-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="d361d-127">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="d361d-128">Přehled standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="d361d-128">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
