---
title: Operace kvantifikátoru
ms.date: 07/20/2015
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
ms.openlocfilehash: f5b98ec09405ca4b8c715dc7da342e66a5d434d8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346585"
---
# <a name="quantifier-operations-visual-basic"></a><span data-ttu-id="55eb8-102">Operace kvantifikátoru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55eb8-102">Quantifier Operations (Visual Basic)</span></span>
<span data-ttu-id="55eb8-103">Operace kvantifikátoru vrací <xref:System.Boolean> hodnotu, která označuje, zda některé nebo všechny prvky v sekvenci splní podmínku.</span><span class="sxs-lookup"><span data-stu-id="55eb8-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="55eb8-104">Následující ilustrace znázorňuje dvě různé operace kvantifikátoru ve dvou různých zdrojových sekvencích.</span><span class="sxs-lookup"><span data-stu-id="55eb8-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="55eb8-105">První operace se zeptá, zda je jeden nebo více prvků znaku A a výsledek je `true`.</span><span class="sxs-lookup"><span data-stu-id="55eb8-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="55eb8-106">Druhá operace se zeptá, jestli jsou všechny prvky znakem A a výsledek je `true`.</span><span class="sxs-lookup"><span data-stu-id="55eb8-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![Operace kvantifikátoru LINQ](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="55eb8-108">Standardní metody operátoru dotazu, které provádějí operace kvantifikátoru, jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="55eb8-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="55eb8-109">Metody</span><span class="sxs-lookup"><span data-stu-id="55eb8-109">Methods</span></span>  
  
|<span data-ttu-id="55eb8-110">Název metody</span><span class="sxs-lookup"><span data-stu-id="55eb8-110">Method Name</span></span>|<span data-ttu-id="55eb8-111">Popis</span><span class="sxs-lookup"><span data-stu-id="55eb8-111">Description</span></span>|<span data-ttu-id="55eb8-112">Visual Basic syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="55eb8-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="55eb8-113">Další informace</span><span class="sxs-lookup"><span data-stu-id="55eb8-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="55eb8-114">Všechny</span><span class="sxs-lookup"><span data-stu-id="55eb8-114">All</span></span>|<span data-ttu-id="55eb8-115">Určuje, zda všechny prvky v sekvenci splní podmínku.</span><span class="sxs-lookup"><span data-stu-id="55eb8-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="55eb8-116">Vše</span><span class="sxs-lookup"><span data-stu-id="55eb8-116">Any</span></span>|<span data-ttu-id="55eb8-117">Určuje, zda některé prvky v sekvenci splní podmínku.</span><span class="sxs-lookup"><span data-stu-id="55eb8-117">Determines whether any elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="55eb8-118">Obsahuje</span><span class="sxs-lookup"><span data-stu-id="55eb8-118">Contains</span></span>|<span data-ttu-id="55eb8-119">Určuje, zda sekvence obsahuje zadaný element.</span><span class="sxs-lookup"><span data-stu-id="55eb8-119">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="55eb8-120">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="55eb8-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="55eb8-121">Příklady syntaxe výrazů dotazů</span><span class="sxs-lookup"><span data-stu-id="55eb8-121">Query Expression Syntax Examples</span></span>  
 <span data-ttu-id="55eb8-122">Tyto příklady používají klauzuli `Aggregate` v Visual Basic jako součást podmínky filtrování v dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="55eb8-122">These examples use the `Aggregate` clause in Visual Basic as part of the filtering condition in a LINQ query.</span></span>  
  
 <span data-ttu-id="55eb8-123">V následujícím příkladu je použita klauzule `Aggregate` a metoda rozšíření <xref:System.Linq.Enumerable.All%2A>, která se má vrátit z kolekce, které jsou všichni lidé, jejichž domácí skupina je starší než zadané stáří.</span><span class="sxs-lookup"><span data-stu-id="55eb8-123">The following example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.All%2A> extension method to return from a collection those people whose pets are all older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#1)]  
  
 <span data-ttu-id="55eb8-124">V dalším příkladu se používá klauzule `Aggregate` a metoda rozšíření <xref:System.Linq.Enumerable.Any%2A>, která se má vrátit z kolekce pro uživatele, kteří mají alespoň jednu PET, která je starší než určený věk.</span><span class="sxs-lookup"><span data-stu-id="55eb8-124">The next example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.Any%2A> extension method to return from a collection those people who have at least one pet that is older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="55eb8-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="55eb8-125">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="55eb8-126">Přehled standardních operátorů dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55eb8-126">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="55eb8-127">Klauzule Aggregate</span><span class="sxs-lookup"><span data-stu-id="55eb8-127">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="55eb8-128">Postupy: vytvoření dotazu na věty obsahující zadanou množinu slov (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55eb8-128">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)
