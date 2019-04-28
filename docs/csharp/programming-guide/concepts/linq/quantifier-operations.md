---
title: Operace kvantifikátoru (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 090bc53c3dcedc82972ab7d16fa2968011a7db65
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61681778"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="58bf1-102">Operace kvantifikátoru (C#)</span><span class="sxs-lookup"><span data-stu-id="58bf1-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="58bf1-103">Operace kvantifikátoru vrátit <xref:System.Boolean> hodnotu, která určuje, jestli některé nebo všechny prvky v sekvenci splňují podmínku.</span><span class="sxs-lookup"><span data-stu-id="58bf1-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="58bf1-104">Následující obrázek znázorňuje dvě různé kvantifikátor operace na dvou sekvencí jiného zdroje.</span><span class="sxs-lookup"><span data-stu-id="58bf1-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="58bf1-105">První operace požádá, pokud jeden nebo více elementů jsou znaky "A" a výsledkem je `true`.</span><span class="sxs-lookup"><span data-stu-id="58bf1-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="58bf1-106">Druhou operaci požádá, pokud jsou všechny prvky znaků "A" a výsledkem je `true`.</span><span class="sxs-lookup"><span data-stu-id="58bf1-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![Operace kvantifikátoru LINQ](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="58bf1-108">Standardní metody operátoru dotazu, které provádějí operace kvantifikátoru jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="58bf1-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="58bf1-109">Metody</span><span class="sxs-lookup"><span data-stu-id="58bf1-109">Methods</span></span>  
  
|<span data-ttu-id="58bf1-110">Název metody</span><span class="sxs-lookup"><span data-stu-id="58bf1-110">Method Name</span></span>|<span data-ttu-id="58bf1-111">Popis</span><span class="sxs-lookup"><span data-stu-id="58bf1-111">Description</span></span>|<span data-ttu-id="58bf1-112">Syntaxe výrazu dotazu jazyka C#</span><span class="sxs-lookup"><span data-stu-id="58bf1-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="58bf1-113">Další informace</span><span class="sxs-lookup"><span data-stu-id="58bf1-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="58bf1-114">Všechny</span><span class="sxs-lookup"><span data-stu-id="58bf1-114">All</span></span>|<span data-ttu-id="58bf1-115">Určuje, zda všechny prvky v sekvenci splňují podmínku.</span><span class="sxs-lookup"><span data-stu-id="58bf1-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="58bf1-116">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="58bf1-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="58bf1-117">Jakýkoli</span><span class="sxs-lookup"><span data-stu-id="58bf1-117">Any</span></span>|<span data-ttu-id="58bf1-118">Určuje, zda všechny prvky v sekvenci splňují podmínku.</span><span class="sxs-lookup"><span data-stu-id="58bf1-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="58bf1-119">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="58bf1-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="58bf1-120">Obsahuje</span><span class="sxs-lookup"><span data-stu-id="58bf1-120">Contains</span></span>|<span data-ttu-id="58bf1-121">Určuje, zda sekvence obsahuje zadaný prvek.</span><span class="sxs-lookup"><span data-stu-id="58bf1-121">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="58bf1-122">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="58bf1-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="58bf1-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="58bf1-123">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="58bf1-124">Přehled standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="58bf1-124">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="58bf1-125">Postupy: Dynamické určování filtrů predikátů při běhu</span><span class="sxs-lookup"><span data-stu-id="58bf1-125">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="58bf1-126">Postupy: Dotazu na věty obsahující zadanou množinu slov (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="58bf1-126">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
