---
title: Dělení dat (C#)
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: d9330e9973b2f25903e1f81a7296362e2a7c756b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591590"
---
# <a name="partitioning-data-c"></a><span data-ttu-id="4f197-102">Dělení dat (C#)</span><span class="sxs-lookup"><span data-stu-id="4f197-102">Partitioning Data (C#)</span></span>
<span data-ttu-id="4f197-103">Dělení v jazyce LINQ odkazuje na operaci rozdělení vstupní sekvence do dvou oddílů bez přeuspořádání prvků a vrácení jedné z sekcí.</span><span class="sxs-lookup"><span data-stu-id="4f197-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="4f197-104">Následující ilustrace znázorňuje výsledky tří různých operací dělení na sekvenci znaků.</span><span class="sxs-lookup"><span data-stu-id="4f197-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="4f197-105">První operace vrátí první tři prvky v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="4f197-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="4f197-106">Druhá operace přeskočí první tři prvky a vrátí zbývající prvky.</span><span class="sxs-lookup"><span data-stu-id="4f197-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="4f197-107">Třetí operace přeskočí první dva prvky v sekvenci a vrátí další tři prvky.</span><span class="sxs-lookup"><span data-stu-id="4f197-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 ![Obrázek, který ukazuje tři operace dělení na oddíly LINQ.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 <span data-ttu-id="4f197-109">Standardní metody operátoru dotazu, které sekvence oddílů jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="4f197-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="4f197-110">Operátory</span><span class="sxs-lookup"><span data-stu-id="4f197-110">Operators</span></span>  
  
|<span data-ttu-id="4f197-111">Název operátoru</span><span class="sxs-lookup"><span data-stu-id="4f197-111">Operator Name</span></span>|<span data-ttu-id="4f197-112">Popis</span><span class="sxs-lookup"><span data-stu-id="4f197-112">Description</span></span>|<span data-ttu-id="4f197-113">C#Syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="4f197-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="4f197-114">Další informace</span><span class="sxs-lookup"><span data-stu-id="4f197-114">More Information</span></span>|  
|-------------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="4f197-115">Skip</span><span class="sxs-lookup"><span data-stu-id="4f197-115">Skip</span></span>|<span data-ttu-id="4f197-116">Přeskočí prvky až do zadané pozice v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="4f197-116">Skips elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="4f197-117">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="4f197-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="4f197-118">SkipWhile –</span><span class="sxs-lookup"><span data-stu-id="4f197-118">SkipWhile</span></span>|<span data-ttu-id="4f197-119">Přeskočí prvky založené na funkci predikátu, dokud element nesplní podmínku.</span><span class="sxs-lookup"><span data-stu-id="4f197-119">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="4f197-120">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="4f197-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="4f197-121">Take</span><span class="sxs-lookup"><span data-stu-id="4f197-121">Take</span></span>|<span data-ttu-id="4f197-122">Přebírá prvky až do zadané pozice v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="4f197-122">Takes elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="4f197-123">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="4f197-123">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="4f197-124">TakeWhile –</span><span class="sxs-lookup"><span data-stu-id="4f197-124">TakeWhile</span></span>|<span data-ttu-id="4f197-125">Převezme prvky založené na funkci predikátu, dokud element nesplní podmínku.</span><span class="sxs-lookup"><span data-stu-id="4f197-125">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="4f197-126">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="4f197-126">Not applicable.</span></span>|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="4f197-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4f197-127">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="4f197-128">Přehled standardních operátorů dotazůC#()</span><span class="sxs-lookup"><span data-stu-id="4f197-128">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
