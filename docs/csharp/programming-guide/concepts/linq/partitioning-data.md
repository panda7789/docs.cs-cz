---
title: Dělení dat (C#)
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: 2e719b3a61b7c42d8ec6afe5fffe88a5bf83f82e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43523458"
---
# <a name="partitioning-data-c"></a><span data-ttu-id="74cb0-102">Dělení dat (C#)</span><span class="sxs-lookup"><span data-stu-id="74cb0-102">Partitioning Data (C#)</span></span>
<span data-ttu-id="74cb0-103">Vytváření oddílů v technologii LINQ odkazuje na operaci dělení vstupní sekvence na dva oddíly bez uspořádání prvků a vrácení jednoho z částí.</span><span class="sxs-lookup"><span data-stu-id="74cb0-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="74cb0-104">Následující obrázek znázorňuje výsledky tři různé dělení operace na sekvenci znaků.</span><span class="sxs-lookup"><span data-stu-id="74cb0-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="74cb0-105">První operace vrátí první tři prvky v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="74cb0-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="74cb0-106">Druhou operaci přeskočí první tři prvky a vrátí zbývající prvky.</span><span class="sxs-lookup"><span data-stu-id="74cb0-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="74cb0-107">Třetí operace přeskočí první dva prvky v pořadí a vrátí následující tři elementy.</span><span class="sxs-lookup"><span data-stu-id="74cb0-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 <span data-ttu-id="74cb0-108">![Dělení operace LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span><span class="sxs-lookup"><span data-stu-id="74cb0-108">![LINQ Partitioning Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span></span>  
  
 <span data-ttu-id="74cb0-109">V následující části jsou uvedeny standardní metody operátoru dotazu, které oddílu pořadí.</span><span class="sxs-lookup"><span data-stu-id="74cb0-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="74cb0-110">Operátory</span><span class="sxs-lookup"><span data-stu-id="74cb0-110">Operators</span></span>  
  
|<span data-ttu-id="74cb0-111">Název operátoru</span><span class="sxs-lookup"><span data-stu-id="74cb0-111">Operator Name</span></span>|<span data-ttu-id="74cb0-112">Popis</span><span class="sxs-lookup"><span data-stu-id="74cb0-112">Description</span></span>|<span data-ttu-id="74cb0-113">Syntaxe výrazu dotazu jazyka C#</span><span class="sxs-lookup"><span data-stu-id="74cb0-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="74cb0-114">Další informace</span><span class="sxs-lookup"><span data-stu-id="74cb0-114">More Information</span></span>|  
|-------------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="74cb0-115">Skip</span><span class="sxs-lookup"><span data-stu-id="74cb0-115">Skip</span></span>|<span data-ttu-id="74cb0-116">Přeskočí elementy až do zadané pozice v pořadí.</span><span class="sxs-lookup"><span data-stu-id="74cb0-116">Skips elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="74cb0-117">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="74cb0-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="74cb0-118">SkipWhile –</span><span class="sxs-lookup"><span data-stu-id="74cb0-118">SkipWhile</span></span>|<span data-ttu-id="74cb0-119">Vynechává prvky podle funkce predikátu, dokud element nesplňuje podmínku.</span><span class="sxs-lookup"><span data-stu-id="74cb0-119">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="74cb0-120">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="74cb0-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="74cb0-121">Take</span><span class="sxs-lookup"><span data-stu-id="74cb0-121">Take</span></span>|<span data-ttu-id="74cb0-122">Získá prvků až do zadané pozice v pořadí.</span><span class="sxs-lookup"><span data-stu-id="74cb0-122">Takes elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="74cb0-123">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="74cb0-123">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="74cb0-124">TakeWhile –</span><span class="sxs-lookup"><span data-stu-id="74cb0-124">TakeWhile</span></span>|<span data-ttu-id="74cb0-125">Přijímá prvky podle funkce predikátu, dokud element nesplňuje podmínku.</span><span class="sxs-lookup"><span data-stu-id="74cb0-125">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="74cb0-126">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="74cb0-126">Not applicable.</span></span>|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="74cb0-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="74cb0-127">See Also</span></span>

- <xref:System.Linq>  
- [<span data-ttu-id="74cb0-128">Přehled standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="74cb0-128">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
