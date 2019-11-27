---
title: Where – klauzule
ms.date: 07/20/2015
f1_keywords:
- vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
ms.openlocfilehash: 60b7ebe96ce0c4580c36675b2e4aa5f9888732c3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349632"
---
# <a name="where-clause-visual-basic"></a><span data-ttu-id="c3376-102">Where – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3376-102">Where Clause (Visual Basic)</span></span>
<span data-ttu-id="c3376-103">Určuje podmínku filtrování pro dotaz.</span><span class="sxs-lookup"><span data-stu-id="c3376-103">Specifies the filtering condition for a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3376-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3376-104">Syntax</span></span>  
  
```vb  
Where condition  
```  
  
## <a name="parts"></a><span data-ttu-id="c3376-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="c3376-105">Parts</span></span>  
 `condition`  
 <span data-ttu-id="c3376-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="c3376-106">Required.</span></span> <span data-ttu-id="c3376-107">Výraz, který určuje, zda jsou hodnoty pro aktuální položku v kolekci zahrnuty do výstupní kolekce.</span><span class="sxs-lookup"><span data-stu-id="c3376-107">An expression that determines whether the values for the current item in the collection are included in the output collection.</span></span> <span data-ttu-id="c3376-108">Výraz se musí vyhodnotit na `Boolean` hodnotu nebo ekvivalent `Boolean` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c3376-108">The expression must evaluate to a `Boolean` value or the equivalent of a `Boolean` value.</span></span> <span data-ttu-id="c3376-109">Pokud je podmínka vyhodnocena jako `True`, je element zahrnut do výsledku dotazu; v opačném případě je prvek vyloučen z výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="c3376-109">If the condition evaluates to `True`, the element is included in the query result; otherwise, the element is excluded from the query result.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3376-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c3376-110">Remarks</span></span>  
 <span data-ttu-id="c3376-111">Klauzule `Where` umožňuje filtrovat data dotazu výběrem pouze prvků, které splňují určitá kritéria.</span><span class="sxs-lookup"><span data-stu-id="c3376-111">The `Where` clause enables you to filter query data by selecting only elements that meet certain criteria.</span></span> <span data-ttu-id="c3376-112">Elementy, jejichž hodnoty způsobí, že klauzule `Where` má být vyhodnocena jako `True` je obsažena ve výsledku dotazu; ostatní prvky jsou vyloučeny.</span><span class="sxs-lookup"><span data-stu-id="c3376-112">Elements whose values cause the `Where` clause to evaluate to `True` are included in the query result; other elements are excluded.</span></span> <span data-ttu-id="c3376-113">Výraz použitý v klauzuli `Where` se musí vyhodnotit na `Boolean` nebo ekvivalent `Boolean`, jako je například celé číslo, které se vyhodnotí jako `False`, pokud je jeho hodnota nulová.</span><span class="sxs-lookup"><span data-stu-id="c3376-113">The expression that is used in a `Where` clause must evaluate to a `Boolean` or the equivalent of a `Boolean`, such as an Integer that evaluates to `False` when its value is zero.</span></span> <span data-ttu-id="c3376-114">Můžete zkombinovat více výrazů v klauzuli `Where` pomocí logických operátorů, jako jsou `And`, `Or`, `AndAlso`, `OrElse`, `Is`a `IsNot`.</span><span class="sxs-lookup"><span data-stu-id="c3376-114">You can combine multiple expressions in a `Where` clause by using logical operators such as `And`, `Or`, `AndAlso`, `OrElse`, `Is`, and `IsNot`.</span></span>  
  
 <span data-ttu-id="c3376-115">Ve výchozím nastavení nejsou výrazy dotazů vyhodnoceny, dokud nejsou k dispozici, například pokud jsou vázány na data nebo iterované prostřednictvím ve `For` smyčce.</span><span class="sxs-lookup"><span data-stu-id="c3376-115">By default, query expressions are not evaluated until they are accessed—for example, when they are data-bound or iterated through in a `For` loop.</span></span> <span data-ttu-id="c3376-116">V důsledku toho není klauzule `Where` vyhodnocena, dokud není k dotazu k dispozici.</span><span class="sxs-lookup"><span data-stu-id="c3376-116">As a result, the `Where` clause is not evaluated until the query is accessed.</span></span> <span data-ttu-id="c3376-117">Pokud máte externí hodnoty pro dotaz, které jsou použity v klauzuli `Where`, zajistěte, aby se příslušná hodnota používala v klauzuli `Where` v době spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="c3376-117">If you have values external to the query that are used in the `Where` clause, ensure that the appropriate value is used in the `Where` clause at the time the query is executed.</span></span> <span data-ttu-id="c3376-118">Další informace o provádění dotazů naleznete v tématu [zápis prvního dotazu LINQ](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="c3376-118">For more information about query execution, see [Writing Your First LINQ Query](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
 <span data-ttu-id="c3376-119">Můžete volat funkce v rámci klauzule `Where` k provedení výpočtu nebo operace s hodnotou z aktuálního prvku v kolekci.</span><span class="sxs-lookup"><span data-stu-id="c3376-119">You can call functions within a `Where` clause to perform a calculation or operation on a value from the current element in the collection.</span></span> <span data-ttu-id="c3376-120">Volání funkce v klauzuli `Where` může způsobit, že dotaz bude proveden ihned při jeho definování namísto při jeho použití.</span><span class="sxs-lookup"><span data-stu-id="c3376-120">Calling a function in a `Where` clause can cause the query to be executed immediately when it is defined instead of when it is accessed.</span></span> <span data-ttu-id="c3376-121">Další informace o provádění dotazů naleznete v tématu [zápis prvního dotazu LINQ](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="c3376-121">For more information about query execution, see [Writing Your First LINQ Query](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3376-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="c3376-122">Example</span></span>  
 <span data-ttu-id="c3376-123">Následující výraz dotazu používá klauzuli `From` k deklaraci proměnné rozsahu `cust` pro každý objekt `Customer` v kolekci `customers`.</span><span class="sxs-lookup"><span data-stu-id="c3376-123">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="c3376-124">Klauzule `Where` používá proměnnou rozsahu k omezení výstupu na zákazníky ze zadané oblasti.</span><span class="sxs-lookup"><span data-stu-id="c3376-124">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="c3376-125">Smyčka `For Each` zobrazuje název společnosti pro každého zákazníka ve výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="c3376-125">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="example"></a><span data-ttu-id="c3376-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="c3376-126">Example</span></span>  
 <span data-ttu-id="c3376-127">Následující příklad používá `And` a `Or` logické operátory v klauzuli `Where`.</span><span class="sxs-lookup"><span data-stu-id="c3376-127">The following example uses `And` and `Or` logical operators in the `Where` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="c3376-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c3376-128">See also</span></span>

- [<span data-ttu-id="c3376-129">Úvod do jazyka LINQ v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c3376-129">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="c3376-130">Dotazy</span><span class="sxs-lookup"><span data-stu-id="c3376-130">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="c3376-131">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="c3376-131">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="c3376-132">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="c3376-132">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="c3376-133">Příkaz For Each...Next</span><span class="sxs-lookup"><span data-stu-id="c3376-133">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
