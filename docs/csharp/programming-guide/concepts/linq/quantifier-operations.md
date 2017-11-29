---
title: "Operace kvantifikátoru (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d6152cbbd390508a8ffce732f6cbdf1f2e1aa0f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="b7fc9-102">Operace kvantifikátoru (C#)</span><span class="sxs-lookup"><span data-stu-id="b7fc9-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="b7fc9-103">Operace kvantifikátoru vrátit <xref:System.Boolean> hodnotu, která určuje, zda některé nebo všechny elementy v pořadí splňují podmínku.</span><span class="sxs-lookup"><span data-stu-id="b7fc9-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="b7fc9-104">Následující obrázek znázorňuje dvě různé kvantifikátoru operace na dva různé zdroje pořadí.</span><span class="sxs-lookup"><span data-stu-id="b7fc9-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="b7fc9-105">První operace požádá, pokud jedna nebo více elementů je znak "A" a výsledkem je `true`.</span><span class="sxs-lookup"><span data-stu-id="b7fc9-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="b7fc9-106">Druhá operace požádá, pokud jsou všechny prvky znak "A" a výsledkem je `true`.</span><span class="sxs-lookup"><span data-stu-id="b7fc9-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 <span data-ttu-id="b7fc9-107">![Operace kvantifikátoru LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span><span class="sxs-lookup"><span data-stu-id="b7fc9-107">![LINQ Quantifier Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span></span>  
  
 <span data-ttu-id="b7fc9-108">Metody operátor standardní dotazu, které provádějí operace kvantifikátoru jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="b7fc9-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b7fc9-109">Metody</span><span class="sxs-lookup"><span data-stu-id="b7fc9-109">Methods</span></span>  
  
|<span data-ttu-id="b7fc9-110">Název metody</span><span class="sxs-lookup"><span data-stu-id="b7fc9-110">Method Name</span></span>|<span data-ttu-id="b7fc9-111">Popis</span><span class="sxs-lookup"><span data-stu-id="b7fc9-111">Description</span></span>|<span data-ttu-id="b7fc9-112">Syntaxe výrazu dotazu jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b7fc9-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="b7fc9-113">Další informace</span><span class="sxs-lookup"><span data-stu-id="b7fc9-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="b7fc9-114">Všechny</span><span class="sxs-lookup"><span data-stu-id="b7fc9-114">All</span></span>|<span data-ttu-id="b7fc9-115">Určuje, zda všechny elementy v pořadí splňují podmínku.</span><span class="sxs-lookup"><span data-stu-id="b7fc9-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="b7fc9-116">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="b7fc9-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b7fc9-117">všechny</span><span class="sxs-lookup"><span data-stu-id="b7fc9-117">Any</span></span>|<span data-ttu-id="b7fc9-118">Určuje, zda všechny elementy v pořadí splňují podmínku.</span><span class="sxs-lookup"><span data-stu-id="b7fc9-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="b7fc9-119">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="b7fc9-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b7fc9-120">Obsahuje</span><span class="sxs-lookup"><span data-stu-id="b7fc9-120">Contains</span></span>|<span data-ttu-id="b7fc9-121">Určuje, zda sekvence obsahuje zadaný element.</span><span class="sxs-lookup"><span data-stu-id="b7fc9-121">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="b7fc9-122">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="b7fc9-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="b7fc9-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="b7fc9-123">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="b7fc9-124">Přehled standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="b7fc9-124">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="b7fc9-125">Postupy: dynamické určování filtrů predikátů při běhu</span><span class="sxs-lookup"><span data-stu-id="b7fc9-125">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)  
 [<span data-ttu-id="b7fc9-126">Postupy: dotazu na věty obsahující zadanou množinu slov (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="b7fc9-126">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
