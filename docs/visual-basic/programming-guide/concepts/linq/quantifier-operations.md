---
title: "Operace kvantifikátoru (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9bc48c69179b1f8876efaa465295e94a9a0e0fb6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="quantifier-operations-visual-basic"></a><span data-ttu-id="363f1-102">Operace kvantifikátoru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="363f1-102">Quantifier Operations (Visual Basic)</span></span>
<span data-ttu-id="363f1-103">Operace kvantifikátoru vrátit <xref:System.Boolean> hodnotu, která určuje, zda některé nebo všechny elementy v pořadí splňují podmínku.</span><span class="sxs-lookup"><span data-stu-id="363f1-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="363f1-104">Následující obrázek znázorňuje dvě různé kvantifikátoru operace na dva různé zdroje pořadí.</span><span class="sxs-lookup"><span data-stu-id="363f1-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="363f1-105">První operace požádá, pokud jedna nebo více elementů je znak "A" a výsledkem je `true`.</span><span class="sxs-lookup"><span data-stu-id="363f1-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="363f1-106">Druhá operace požádá, pokud jsou všechny prvky znak "A" a výsledkem je `true`.</span><span class="sxs-lookup"><span data-stu-id="363f1-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 <span data-ttu-id="363f1-107">![Operace kvantifikátoru LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span><span class="sxs-lookup"><span data-stu-id="363f1-107">![LINQ Quantifier Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span></span>  
  
 <span data-ttu-id="363f1-108">Metody operátor standardní dotazu, které provádějí operace kvantifikátoru jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="363f1-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="363f1-109">Metody</span><span class="sxs-lookup"><span data-stu-id="363f1-109">Methods</span></span>  
  
|<span data-ttu-id="363f1-110">Název metody</span><span class="sxs-lookup"><span data-stu-id="363f1-110">Method Name</span></span>|<span data-ttu-id="363f1-111">Popis</span><span class="sxs-lookup"><span data-stu-id="363f1-111">Description</span></span>|<span data-ttu-id="363f1-112">Syntaxe výrazu dotazu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="363f1-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="363f1-113">Další informace</span><span class="sxs-lookup"><span data-stu-id="363f1-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="363f1-114">Všechny</span><span class="sxs-lookup"><span data-stu-id="363f1-114">All</span></span>|<span data-ttu-id="363f1-115">Určuje, zda všechny elementy v pořadí splňují podmínku.</span><span class="sxs-lookup"><span data-stu-id="363f1-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="363f1-116">všechny</span><span class="sxs-lookup"><span data-stu-id="363f1-116">Any</span></span>|<span data-ttu-id="363f1-117">Určuje, zda všechny elementy v pořadí splňují podmínku.</span><span class="sxs-lookup"><span data-stu-id="363f1-117">Determines whether any elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="363f1-118">Obsahuje</span><span class="sxs-lookup"><span data-stu-id="363f1-118">Contains</span></span>|<span data-ttu-id="363f1-119">Určuje, zda sekvence obsahuje zadaný element.</span><span class="sxs-lookup"><span data-stu-id="363f1-119">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="363f1-120">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="363f1-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="363f1-121">Příklady syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="363f1-121">Query Expression Syntax Examples</span></span>  
 <span data-ttu-id="363f1-122">Pomocí těchto příkladech `Aggregate` klauzule v jazyce Visual Basic v rámci podmínku filtrování v dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="363f1-122">These examples use the `Aggregate` clause in Visual Basic as part of the filtering condition in a LINQ query.</span></span>  
  
 <span data-ttu-id="363f1-123">Následující příklad používá `Aggregate` klauzule a <xref:System.Linq.Enumerable.All%2A> rozšíření metodu pro návrat z kolekce tyto osoby, jejíž mazlíčků jsou všechny starší než zadaná stáří.</span><span class="sxs-lookup"><span data-stu-id="363f1-123">The following example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.All%2A> extension method to return from a collection those people whose pets are all older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_1.vb)]  
  
 <span data-ttu-id="363f1-124">Další příklad používá `Aggregate` klauzule a <xref:System.Linq.Enumerable.Any%2A> rozšíření metodu pro návrat z kolekce domácími uživatelé, kteří mají alespoň jednu, která je starší než zadaná stáří.</span><span class="sxs-lookup"><span data-stu-id="363f1-124">The next example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.Any%2A> extension method to return from a collection those people who have at least one pet that is older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="363f1-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="363f1-125">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="363f1-126">Přehled standardních operátorů dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="363f1-126">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="363f1-127">AGGREGATE – klauzule</span><span class="sxs-lookup"><span data-stu-id="363f1-127">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="363f1-128">Postupy: dotazu na věty obsahující zadanou množinu slov (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="363f1-128">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)
