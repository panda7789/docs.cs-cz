---
title: Operace kvantifikátoru (Visual Basic)
ms.date: 07/20/2015
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
ms.openlocfilehash: e871a77caf0b7cfe361f11462085180c17bf2057
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816041"
---
# <a name="quantifier-operations-visual-basic"></a><span data-ttu-id="ff8cd-102">Operace kvantifikátoru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff8cd-102">Quantifier Operations (Visual Basic)</span></span>
<span data-ttu-id="ff8cd-103">Operace kvantifikátoru vrátit <xref:System.Boolean> hodnotu, která určuje, jestli některé nebo všechny prvky v sekvenci splňují podmínku.</span><span class="sxs-lookup"><span data-stu-id="ff8cd-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="ff8cd-104">Následující obrázek znázorňuje dvě různé kvantifikátor operace na dvou sekvencí jiného zdroje.</span><span class="sxs-lookup"><span data-stu-id="ff8cd-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="ff8cd-105">První operace požádá, pokud jeden nebo více elementů jsou znaky "A" a výsledkem je `true`.</span><span class="sxs-lookup"><span data-stu-id="ff8cd-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="ff8cd-106">Druhou operaci požádá, pokud jsou všechny prvky znaků "A" a výsledkem je `true`.</span><span class="sxs-lookup"><span data-stu-id="ff8cd-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![Operace kvantifikátoru LINQ](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="ff8cd-108">Standardní metody operátoru dotazu, které provádějí operace kvantifikátoru jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="ff8cd-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ff8cd-109">Metody</span><span class="sxs-lookup"><span data-stu-id="ff8cd-109">Methods</span></span>  
  
|<span data-ttu-id="ff8cd-110">Název metody</span><span class="sxs-lookup"><span data-stu-id="ff8cd-110">Method Name</span></span>|<span data-ttu-id="ff8cd-111">Popis</span><span class="sxs-lookup"><span data-stu-id="ff8cd-111">Description</span></span>|<span data-ttu-id="ff8cd-112">Syntaxe výrazu dotazu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ff8cd-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="ff8cd-113">Další informace</span><span class="sxs-lookup"><span data-stu-id="ff8cd-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="ff8cd-114">Všechny</span><span class="sxs-lookup"><span data-stu-id="ff8cd-114">All</span></span>|<span data-ttu-id="ff8cd-115">Určuje, zda všechny prvky v sekvenci splňují podmínku.</span><span class="sxs-lookup"><span data-stu-id="ff8cd-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ff8cd-116">Jakýkoli</span><span class="sxs-lookup"><span data-stu-id="ff8cd-116">Any</span></span>|<span data-ttu-id="ff8cd-117">Určuje, zda všechny prvky v sekvenci splňují podmínku.</span><span class="sxs-lookup"><span data-stu-id="ff8cd-117">Determines whether any elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ff8cd-118">Obsahuje</span><span class="sxs-lookup"><span data-stu-id="ff8cd-118">Contains</span></span>|<span data-ttu-id="ff8cd-119">Určuje, zda sekvence obsahuje zadaný prvek.</span><span class="sxs-lookup"><span data-stu-id="ff8cd-119">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="ff8cd-120">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="ff8cd-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="ff8cd-121">Příklady syntaxe výrazů dotazů</span><span class="sxs-lookup"><span data-stu-id="ff8cd-121">Query Expression Syntax Examples</span></span>  
 <span data-ttu-id="ff8cd-122">Tyto příklady používají `Aggregate` klauzule v jazyce Visual Basic jako součást podmínku filtrování v dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="ff8cd-122">These examples use the `Aggregate` clause in Visual Basic as part of the filtering condition in a LINQ query.</span></span>  
  
 <span data-ttu-id="ff8cd-123">V následujícím příkladu `Aggregate` klauzule a <xref:System.Linq.Enumerable.All%2A> metodu rozšíření k vrácení z kolekce osoby, jejíž mazlíčci jsou všechny starší než starší než zadaný limit.</span><span class="sxs-lookup"><span data-stu-id="ff8cd-123">The following example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.All%2A> extension method to return from a collection those people whose pets are all older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#1)]  
  
 <span data-ttu-id="ff8cd-124">Následující příklad používá `Aggregate` klauzule a <xref:System.Linq.Enumerable.Any%2A> metodu rozšíření k vrácení z kolekce domácími tito uživatelé, kteří mají alespoň jednu, která je starší než starší než zadaný limit.</span><span class="sxs-lookup"><span data-stu-id="ff8cd-124">The next example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.Any%2A> extension method to return from a collection those people who have at least one pet that is older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="ff8cd-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ff8cd-125">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="ff8cd-126">Přehled standardních operátorů dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff8cd-126">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="ff8cd-127">Klauzule Aggregate</span><span class="sxs-lookup"><span data-stu-id="ff8cd-127">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="ff8cd-128">Postupy: Dotazu na věty obsahující zadanou množinu slov (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff8cd-128">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)
