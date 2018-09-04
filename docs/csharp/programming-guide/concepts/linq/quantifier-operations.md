---
title: Operace kvantifikátoru (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 24c8f9a6b589592c26c8a514bc44ff9623a82d2f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43523102"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="91051-102">Operace kvantifikátoru (C#)</span><span class="sxs-lookup"><span data-stu-id="91051-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="91051-103">Operace kvantifikátoru vrátit <xref:System.Boolean> hodnotu, která určuje, jestli některé nebo všechny prvky v sekvenci splňují podmínku.</span><span class="sxs-lookup"><span data-stu-id="91051-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="91051-104">Následující obrázek znázorňuje dvě různé kvantifikátor operace na dvou sekvencí jiného zdroje.</span><span class="sxs-lookup"><span data-stu-id="91051-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="91051-105">První operace požádá, pokud jeden nebo více elementů jsou znaky "A" a výsledkem je `true`.</span><span class="sxs-lookup"><span data-stu-id="91051-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="91051-106">Druhou operaci požádá, pokud jsou všechny prvky znaků "A" a výsledkem je `true`.</span><span class="sxs-lookup"><span data-stu-id="91051-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 <span data-ttu-id="91051-107">![Operace kvantifikátoru LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span><span class="sxs-lookup"><span data-stu-id="91051-107">![LINQ Quantifier Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span></span>  
  
 <span data-ttu-id="91051-108">Standardní metody operátoru dotazu, které provádějí operace kvantifikátoru jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="91051-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="91051-109">Metody</span><span class="sxs-lookup"><span data-stu-id="91051-109">Methods</span></span>  
  
|<span data-ttu-id="91051-110">Název metody</span><span class="sxs-lookup"><span data-stu-id="91051-110">Method Name</span></span>|<span data-ttu-id="91051-111">Popis</span><span class="sxs-lookup"><span data-stu-id="91051-111">Description</span></span>|<span data-ttu-id="91051-112">Syntaxe výrazu dotazu jazyka C#</span><span class="sxs-lookup"><span data-stu-id="91051-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="91051-113">Další informace</span><span class="sxs-lookup"><span data-stu-id="91051-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="91051-114">Všechny</span><span class="sxs-lookup"><span data-stu-id="91051-114">All</span></span>|<span data-ttu-id="91051-115">Určuje, zda všechny prvky v sekvenci splňují podmínku.</span><span class="sxs-lookup"><span data-stu-id="91051-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="91051-116">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="91051-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="91051-117">Všechny</span><span class="sxs-lookup"><span data-stu-id="91051-117">Any</span></span>|<span data-ttu-id="91051-118">Určuje, zda všechny prvky v sekvenci splňují podmínku.</span><span class="sxs-lookup"><span data-stu-id="91051-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="91051-119">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="91051-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="91051-120">Obsahuje</span><span class="sxs-lookup"><span data-stu-id="91051-120">Contains</span></span>|<span data-ttu-id="91051-121">Určuje, zda sekvence obsahuje zadaný prvek.</span><span class="sxs-lookup"><span data-stu-id="91051-121">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="91051-122">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="91051-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="91051-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="91051-123">See Also</span></span>

- <xref:System.Linq>  
- [<span data-ttu-id="91051-124">Přehled standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="91051-124">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
- [<span data-ttu-id="91051-125">Postupy: dynamické určování filtrů predikátů při běhu</span><span class="sxs-lookup"><span data-stu-id="91051-125">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)  
- [<span data-ttu-id="91051-126">Postupy: dotaz na věty obsahující zadanou množinu slov (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="91051-126">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
