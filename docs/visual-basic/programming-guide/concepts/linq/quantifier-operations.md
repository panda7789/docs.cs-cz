---
title: Operace kvantifikátoru
ms.date: 07/20/2015
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
ms.openlocfilehash: 9a2e35e0511915cb17b99550a8bf382bd9d46526
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396308"
---
# <a name="quantifier-operations-visual-basic"></a><span data-ttu-id="a3883-102">Operace kvantifikátoru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3883-102">Quantifier Operations (Visual Basic)</span></span>
<span data-ttu-id="a3883-103">Operace kvantifikátoru vrací <xref:System.Boolean> hodnotu, která označuje, zda některé nebo všechny prvky v sekvenci splní podmínku.</span><span class="sxs-lookup"><span data-stu-id="a3883-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="a3883-104">Následující ilustrace znázorňuje dvě různé operace kvantifikátoru ve dvou různých zdrojových sekvencích.</span><span class="sxs-lookup"><span data-stu-id="a3883-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="a3883-105">První operace se zeptá, zda je jeden nebo více prvků znaku A a výsledek je `true` .</span><span class="sxs-lookup"><span data-stu-id="a3883-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="a3883-106">Druhá operace se zeptá, jestli jsou všechny prvky znakem A a výsledek je `true` .</span><span class="sxs-lookup"><span data-stu-id="a3883-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![Operace kvantifikátoru LINQ](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="a3883-108">Standardní metody operátoru dotazu, které provádějí operace kvantifikátoru, jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="a3883-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a3883-109">Metody</span><span class="sxs-lookup"><span data-stu-id="a3883-109">Methods</span></span>  
  
|<span data-ttu-id="a3883-110">Název metody</span><span class="sxs-lookup"><span data-stu-id="a3883-110">Method Name</span></span>|<span data-ttu-id="a3883-111">Description</span><span class="sxs-lookup"><span data-stu-id="a3883-111">Description</span></span>|<span data-ttu-id="a3883-112">Visual Basic syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="a3883-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="a3883-113">Další informace</span><span class="sxs-lookup"><span data-stu-id="a3883-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="a3883-114">Vše</span><span class="sxs-lookup"><span data-stu-id="a3883-114">All</span></span>|<span data-ttu-id="a3883-115">Určuje, zda všechny prvky v sekvenci splní podmínku.</span><span class="sxs-lookup"><span data-stu-id="a3883-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a3883-116">Všechny</span><span class="sxs-lookup"><span data-stu-id="a3883-116">Any</span></span>|<span data-ttu-id="a3883-117">Určuje, zda některé prvky v sekvenci splní podmínku.</span><span class="sxs-lookup"><span data-stu-id="a3883-117">Determines whether any elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a3883-118">Contains</span><span class="sxs-lookup"><span data-stu-id="a3883-118">Contains</span></span>|<span data-ttu-id="a3883-119">Určuje, zda sekvence obsahuje zadaný element.</span><span class="sxs-lookup"><span data-stu-id="a3883-119">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="a3883-120">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="a3883-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="a3883-121">Příklady syntaxe výrazů dotazů</span><span class="sxs-lookup"><span data-stu-id="a3883-121">Query Expression Syntax Examples</span></span>  
 <span data-ttu-id="a3883-122">Tyto příklady používají `Aggregate` klauzuli v Visual Basic jako součást podmínky filtrování v dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="a3883-122">These examples use the `Aggregate` clause in Visual Basic as part of the filtering condition in a LINQ query.</span></span>  
  
 <span data-ttu-id="a3883-123">V následujícím příkladu je použita `Aggregate` klauzule a <xref:System.Linq.Enumerable.All%2A> metoda rozšíření pro návrat z kolekce, které jsou pro uživatele, jejichž domácí skupina jsou starší než zadané stáří.</span><span class="sxs-lookup"><span data-stu-id="a3883-123">The following example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.All%2A> extension method to return from a collection those people whose pets are all older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#1)]  
  
 <span data-ttu-id="a3883-124">V dalším příkladu se používá `Aggregate` klauzule a <xref:System.Linq.Enumerable.Any%2A> metoda rozšíření pro návrat z kolekce pro uživatele, kteří mají alespoň jednu PET, která je starší než zadané stáří.</span><span class="sxs-lookup"><span data-stu-id="a3883-124">The next example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.Any%2A> extension method to return from a collection those people who have at least one pet that is older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="a3883-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="a3883-125">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="a3883-126">Přehled standardních operátorů dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3883-126">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="a3883-127">Aggregate – klauzule</span><span class="sxs-lookup"><span data-stu-id="a3883-127">Aggregate Clause</span></span>](../../../language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="a3883-128">Postupy: vytvoření dotazu na věty obsahující zadanou množinu slov (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3883-128">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)
