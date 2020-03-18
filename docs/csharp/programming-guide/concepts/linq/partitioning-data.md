---
title: Dělení dat (C#)
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: d9330e9973b2f25903e1f81a7296362e2a7c756b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591590"
---
# <a name="partitioning-data-c"></a><span data-ttu-id="83881-102">Dělení dat (C#)</span><span class="sxs-lookup"><span data-stu-id="83881-102">Partitioning Data (C#)</span></span>
<span data-ttu-id="83881-103">Dělení v LINQ odkazuje na operaci rozdělení vstupní sekvence do dvou částí, bez změny uspořádání prvků a potom vrácení jednoho z oddílů.</span><span class="sxs-lookup"><span data-stu-id="83881-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="83881-104">Následující obrázek znázorňuje výsledky tří různých operací dělení na posloupnost znaků.</span><span class="sxs-lookup"><span data-stu-id="83881-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="83881-105">První operace vrátí první tři prvky v pořadí.</span><span class="sxs-lookup"><span data-stu-id="83881-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="83881-106">Druhá operace přeskočí první tři prvky a vrátí zbývající prvky.</span><span class="sxs-lookup"><span data-stu-id="83881-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="83881-107">Třetí operace přeskočí první dva prvky v sekvenci a vrátí další tři prvky.</span><span class="sxs-lookup"><span data-stu-id="83881-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 ![Obrázek, který znázorňuje tři operace dělení LINQ.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 <span data-ttu-id="83881-109">Standardní metody operátoru dotazu, které jsou oddílsekvence jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="83881-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="83881-110">Operátory</span><span class="sxs-lookup"><span data-stu-id="83881-110">Operators</span></span>  
  
|<span data-ttu-id="83881-111">Název operátoru</span><span class="sxs-lookup"><span data-stu-id="83881-111">Operator Name</span></span>|<span data-ttu-id="83881-112">Popis</span><span class="sxs-lookup"><span data-stu-id="83881-112">Description</span></span>|<span data-ttu-id="83881-113">Syntaxe výrazu dotazu jazyka C#</span><span class="sxs-lookup"><span data-stu-id="83881-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="83881-114">Další informace</span><span class="sxs-lookup"><span data-stu-id="83881-114">More Information</span></span>|  
|-------------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="83881-115">Skip</span><span class="sxs-lookup"><span data-stu-id="83881-115">Skip</span></span>|<span data-ttu-id="83881-116">Přeskočí prvky až do zadané pozice v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="83881-116">Skips elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="83881-117">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="83881-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="83881-118">Skipwhile</span><span class="sxs-lookup"><span data-stu-id="83881-118">SkipWhile</span></span>|<span data-ttu-id="83881-119">Přeskočí prvky založené na funkci predikátu, dokud prvek nesplňuje podmínku.</span><span class="sxs-lookup"><span data-stu-id="83881-119">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="83881-120">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="83881-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="83881-121">Take</span><span class="sxs-lookup"><span data-stu-id="83881-121">Take</span></span>|<span data-ttu-id="83881-122">Trvá prvky až do zadané pozice v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="83881-122">Takes elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="83881-123">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="83881-123">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="83881-124">Takewhile</span><span class="sxs-lookup"><span data-stu-id="83881-124">TakeWhile</span></span>|<span data-ttu-id="83881-125">Bere prvky založené na funkci predikátu, dokud prvek nesplňuje podmínku.</span><span class="sxs-lookup"><span data-stu-id="83881-125">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="83881-126">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="83881-126">Not applicable.</span></span>|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="83881-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="83881-127">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="83881-128">Standardní operátory dotazů – přehled (C#)</span><span class="sxs-lookup"><span data-stu-id="83881-128">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
