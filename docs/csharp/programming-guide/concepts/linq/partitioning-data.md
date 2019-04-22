---
title: Dělení dat (C#)
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: b857c8c6e6b56a7263e6725a747e98ccfe4ff4fc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832460"
---
# <a name="partitioning-data-c"></a><span data-ttu-id="f3f7d-102">Dělení dat (C#)</span><span class="sxs-lookup"><span data-stu-id="f3f7d-102">Partitioning Data (C#)</span></span>
<span data-ttu-id="f3f7d-103">Vytváření oddílů v technologii LINQ odkazuje na operaci dělení vstupní sekvence na dva oddíly bez uspořádání prvků a vrácení jednoho z částí.</span><span class="sxs-lookup"><span data-stu-id="f3f7d-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="f3f7d-104">Následující obrázek znázorňuje výsledky tři různé dělení operace na sekvenci znaků.</span><span class="sxs-lookup"><span data-stu-id="f3f7d-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="f3f7d-105">První operace vrátí první tři prvky v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="f3f7d-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="f3f7d-106">Druhou operaci přeskočí první tři prvky a vrátí zbývající prvky.</span><span class="sxs-lookup"><span data-stu-id="f3f7d-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="f3f7d-107">Třetí operace přeskočí první dva prvky v pořadí a vrátí následující tři elementy.</span><span class="sxs-lookup"><span data-stu-id="f3f7d-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 ![Obrázek, který ukazuje tři operace dělení LINQ.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 <span data-ttu-id="f3f7d-109">V následující části jsou uvedeny standardní metody operátoru dotazu, které oddílu pořadí.</span><span class="sxs-lookup"><span data-stu-id="f3f7d-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="f3f7d-110">Operátory</span><span class="sxs-lookup"><span data-stu-id="f3f7d-110">Operators</span></span>  
  
|<span data-ttu-id="f3f7d-111">Název operátoru</span><span class="sxs-lookup"><span data-stu-id="f3f7d-111">Operator Name</span></span>|<span data-ttu-id="f3f7d-112">Popis</span><span class="sxs-lookup"><span data-stu-id="f3f7d-112">Description</span></span>|<span data-ttu-id="f3f7d-113">Syntaxe výrazu dotazu jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f3f7d-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="f3f7d-114">Další informace</span><span class="sxs-lookup"><span data-stu-id="f3f7d-114">More Information</span></span>|  
|-------------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="f3f7d-115">Skip</span><span class="sxs-lookup"><span data-stu-id="f3f7d-115">Skip</span></span>|<span data-ttu-id="f3f7d-116">Přeskočí elementy až do zadané pozice v pořadí.</span><span class="sxs-lookup"><span data-stu-id="f3f7d-116">Skips elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="f3f7d-117">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="f3f7d-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f3f7d-118">SkipWhile –</span><span class="sxs-lookup"><span data-stu-id="f3f7d-118">SkipWhile</span></span>|<span data-ttu-id="f3f7d-119">Vynechává prvky podle funkce predikátu, dokud element nesplňuje podmínku.</span><span class="sxs-lookup"><span data-stu-id="f3f7d-119">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="f3f7d-120">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="f3f7d-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f3f7d-121">Take</span><span class="sxs-lookup"><span data-stu-id="f3f7d-121">Take</span></span>|<span data-ttu-id="f3f7d-122">Získá prvků až do zadané pozice v pořadí.</span><span class="sxs-lookup"><span data-stu-id="f3f7d-122">Takes elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="f3f7d-123">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="f3f7d-123">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f3f7d-124">TakeWhile –</span><span class="sxs-lookup"><span data-stu-id="f3f7d-124">TakeWhile</span></span>|<span data-ttu-id="f3f7d-125">Přijímá prvky podle funkce predikátu, dokud element nesplňuje podmínku.</span><span class="sxs-lookup"><span data-stu-id="f3f7d-125">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="f3f7d-126">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="f3f7d-126">Not applicable.</span></span>|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="f3f7d-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f3f7d-127">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="f3f7d-128">Přehled standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="f3f7d-128">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
