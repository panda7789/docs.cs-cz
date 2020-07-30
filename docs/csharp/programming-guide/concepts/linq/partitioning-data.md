---
title: Dělení dat (C#)
description: Naučte se, jak rozdělit data v LINQ. Podívejte se na Obrázek znázorňující výsledky operací dělení.
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: 3c85eaec2dc01b683234a27714750354982be440
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302604"
---
# <a name="partitioning-data-c"></a><span data-ttu-id="ee876-104">Dělení dat (C#)</span><span class="sxs-lookup"><span data-stu-id="ee876-104">Partitioning Data (C#)</span></span>
<span data-ttu-id="ee876-105">Dělení v jazyce LINQ odkazuje na operaci rozdělení vstupní sekvence do dvou oddílů bez přeuspořádání prvků a vrácení jedné z sekcí.</span><span class="sxs-lookup"><span data-stu-id="ee876-105">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="ee876-106">Následující ilustrace znázorňuje výsledky tří různých operací dělení na sekvenci znaků.</span><span class="sxs-lookup"><span data-stu-id="ee876-106">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="ee876-107">První operace vrátí první tři prvky v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="ee876-107">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="ee876-108">Druhá operace přeskočí první tři prvky a vrátí zbývající prvky.</span><span class="sxs-lookup"><span data-stu-id="ee876-108">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="ee876-109">Třetí operace přeskočí první dva prvky v sekvenci a vrátí další tři prvky.</span><span class="sxs-lookup"><span data-stu-id="ee876-109">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 ![Obrázek, který ukazuje tři operace dělení na oddíly LINQ.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 <span data-ttu-id="ee876-111">Standardní metody operátoru dotazu, které sekvence oddílů jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="ee876-111">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="ee876-112">Operátory</span><span class="sxs-lookup"><span data-stu-id="ee876-112">Operators</span></span>  
  
|<span data-ttu-id="ee876-113">Název operátoru</span><span class="sxs-lookup"><span data-stu-id="ee876-113">Operator Name</span></span>|<span data-ttu-id="ee876-114">Popis</span><span class="sxs-lookup"><span data-stu-id="ee876-114">Description</span></span>|<span data-ttu-id="ee876-115">Syntaxe výrazu dotazu v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ee876-115">C# Query Expression Syntax</span></span>|<span data-ttu-id="ee876-116">Další informace</span><span class="sxs-lookup"><span data-stu-id="ee876-116">More Information</span></span>|  
|-------------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="ee876-117">Přeskočit</span><span class="sxs-lookup"><span data-stu-id="ee876-117">Skip</span></span>|<span data-ttu-id="ee876-118">Přeskočí prvky až do zadané pozice v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="ee876-118">Skips elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="ee876-119">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="ee876-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ee876-120">SkipWhile –</span><span class="sxs-lookup"><span data-stu-id="ee876-120">SkipWhile</span></span>|<span data-ttu-id="ee876-121">Přeskočí prvky založené na funkci predikátu, dokud element nesplní podmínku.</span><span class="sxs-lookup"><span data-stu-id="ee876-121">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="ee876-122">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="ee876-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ee876-123">Take</span><span class="sxs-lookup"><span data-stu-id="ee876-123">Take</span></span>|<span data-ttu-id="ee876-124">Přebírá prvky až do zadané pozice v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="ee876-124">Takes elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="ee876-125">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="ee876-125">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ee876-126">TakeWhile –</span><span class="sxs-lookup"><span data-stu-id="ee876-126">TakeWhile</span></span>|<span data-ttu-id="ee876-127">Převezme prvky založené na funkci predikátu, dokud element nesplní podmínku.</span><span class="sxs-lookup"><span data-stu-id="ee876-127">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="ee876-128">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="ee876-128">Not applicable.</span></span>|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="ee876-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ee876-129">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="ee876-130">Přehled standardních operátorů dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="ee876-130">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
