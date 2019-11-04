---
title: Operace kvantifikátoru (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 5899af79799d5b8404e60027d7ba1b005c4b1b79
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423364"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="edf63-102">Operace kvantifikátoru (C#)</span><span class="sxs-lookup"><span data-stu-id="edf63-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="edf63-103">Operace kvantifikátoru vrací <xref:System.Boolean> hodnotu, která označuje, zda některé nebo všechny prvky v sekvenci splní podmínku.</span><span class="sxs-lookup"><span data-stu-id="edf63-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="edf63-104">Následující ilustrace znázorňuje dvě různé operace kvantifikátoru ve dvou různých zdrojových sekvencích.</span><span class="sxs-lookup"><span data-stu-id="edf63-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="edf63-105">První operace se zeptá, zda je jeden nebo více prvků znaku A a výsledek je `true`.</span><span class="sxs-lookup"><span data-stu-id="edf63-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="edf63-106">Druhá operace se zeptá, jestli jsou všechny prvky znakem A a výsledek je `true`.</span><span class="sxs-lookup"><span data-stu-id="edf63-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![Operace kvantifikátoru LINQ](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="edf63-108">Standardní metody operátoru dotazu, které provádějí operace kvantifikátoru, jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="edf63-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="edf63-109">Metody</span><span class="sxs-lookup"><span data-stu-id="edf63-109">Methods</span></span>  
  
|<span data-ttu-id="edf63-110">Název metody</span><span class="sxs-lookup"><span data-stu-id="edf63-110">Method Name</span></span>|<span data-ttu-id="edf63-111">Popis</span><span class="sxs-lookup"><span data-stu-id="edf63-111">Description</span></span>|<span data-ttu-id="edf63-112">C#Syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="edf63-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="edf63-113">Další informace</span><span class="sxs-lookup"><span data-stu-id="edf63-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="edf63-114">Všechny</span><span class="sxs-lookup"><span data-stu-id="edf63-114">All</span></span>|<span data-ttu-id="edf63-115">Určuje, zda všechny prvky v sekvenci splní podmínku.</span><span class="sxs-lookup"><span data-stu-id="edf63-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="edf63-116">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="edf63-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="edf63-117">Jakýmikoli</span><span class="sxs-lookup"><span data-stu-id="edf63-117">Any</span></span>|<span data-ttu-id="edf63-118">Určuje, zda některé prvky v sekvenci splní podmínku.</span><span class="sxs-lookup"><span data-stu-id="edf63-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="edf63-119">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="edf63-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="edf63-120">Obsahuje</span><span class="sxs-lookup"><span data-stu-id="edf63-120">Contains</span></span>|<span data-ttu-id="edf63-121">Určuje, zda sekvence obsahuje zadaný element.</span><span class="sxs-lookup"><span data-stu-id="edf63-121">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="edf63-122">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="edf63-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="edf63-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="edf63-123">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="edf63-124">Přehled standardních operátorů dotazůC#()</span><span class="sxs-lookup"><span data-stu-id="edf63-124">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="edf63-125">Postupy: Dynamické určování filtrů predikátů za běhu</span><span class="sxs-lookup"><span data-stu-id="edf63-125">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="edf63-126">Postupy: vytvoření dotazu na věty obsahující zadanou sadu slov (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="edf63-126">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
