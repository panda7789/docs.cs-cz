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
ms.openlocfilehash: b80bb047551dee8ab23cfac06b961996992d69b5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359538"
---
# <a name="where-clause-visual-basic"></a><span data-ttu-id="ab39d-102">Where – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab39d-102">Where Clause (Visual Basic)</span></span>
<span data-ttu-id="ab39d-103">Určuje podmínku filtrování pro dotaz.</span><span class="sxs-lookup"><span data-stu-id="ab39d-103">Specifies the filtering condition for a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab39d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab39d-104">Syntax</span></span>  
  
```vb  
Where condition  
```  
  
## <a name="parts"></a><span data-ttu-id="ab39d-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="ab39d-105">Parts</span></span>  
 `condition`  
 <span data-ttu-id="ab39d-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="ab39d-106">Required.</span></span> <span data-ttu-id="ab39d-107">Výraz, který určuje, zda jsou hodnoty pro aktuální položku v kolekci zahrnuty do výstupní kolekce.</span><span class="sxs-lookup"><span data-stu-id="ab39d-107">An expression that determines whether the values for the current item in the collection are included in the output collection.</span></span> <span data-ttu-id="ab39d-108">Výraz se musí vyhodnotit na `Boolean` hodnotu nebo ekvivalent `Boolean` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ab39d-108">The expression must evaluate to a `Boolean` value or the equivalent of a `Boolean` value.</span></span> <span data-ttu-id="ab39d-109">Pokud je podmínka vyhodnocena jako `True` , je prvek zahrnut do výsledku dotazu; v opačném případě je prvek vyloučen z výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="ab39d-109">If the condition evaluates to `True`, the element is included in the query result; otherwise, the element is excluded from the query result.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab39d-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ab39d-110">Remarks</span></span>  
 <span data-ttu-id="ab39d-111">`Where`Klauzule umožňuje filtrovat data dotazu výběrem pouze prvků, které splňují určitá kritéria.</span><span class="sxs-lookup"><span data-stu-id="ab39d-111">The `Where` clause enables you to filter query data by selecting only elements that meet certain criteria.</span></span> <span data-ttu-id="ab39d-112">Prvky, jejichž hodnoty způsobí, že klauzule, která `Where` má být vyhodnocena, `True` je zahrnuta do výsledku dotazu; ostatní prvky jsou vyloučeny.</span><span class="sxs-lookup"><span data-stu-id="ab39d-112">Elements whose values cause the `Where` clause to evaluate to `True` are included in the query result; other elements are excluded.</span></span> <span data-ttu-id="ab39d-113">Výraz použitý v `Where` klauzuli musí vyhodnotit na `Boolean` nebo ekvivalent `Boolean` , jako je například celé číslo, které se vyhodnotí, `False` Pokud je jeho hodnota nulová.</span><span class="sxs-lookup"><span data-stu-id="ab39d-113">The expression that is used in a `Where` clause must evaluate to a `Boolean` or the equivalent of a `Boolean`, such as an Integer that evaluates to `False` when its value is zero.</span></span> <span data-ttu-id="ab39d-114">Můžete zkombinovat více výrazů v `Where` klauzuli pomocí logických operátorů `And` , jako jsou, `Or` , `AndAlso` , `OrElse` , a `Is` `IsNot` .</span><span class="sxs-lookup"><span data-stu-id="ab39d-114">You can combine multiple expressions in a `Where` clause by using logical operators such as `And`, `Or`, `AndAlso`, `OrElse`, `Is`, and `IsNot`.</span></span>  
  
 <span data-ttu-id="ab39d-115">Ve výchozím nastavení nejsou výrazy dotazů vyhodnoceny, dokud nejsou k dispozici, například pokud jsou vázány na data nebo iterované prostřednictvím `For` smyčky.</span><span class="sxs-lookup"><span data-stu-id="ab39d-115">By default, query expressions are not evaluated until they are accessed—for example, when they are data-bound or iterated through in a `For` loop.</span></span> <span data-ttu-id="ab39d-116">V důsledku toho není `Where` klauzule vyhodnocena, dokud není k dotazu k dispozici.</span><span class="sxs-lookup"><span data-stu-id="ab39d-116">As a result, the `Where` clause is not evaluated until the query is accessed.</span></span> <span data-ttu-id="ab39d-117">Pokud máte externí hodnoty pro dotaz, které jsou použity v `Where` klauzuli, zajistěte, aby byla v `Where` klauzuli v okamžiku provedení dotazu použita příslušná hodnota.</span><span class="sxs-lookup"><span data-stu-id="ab39d-117">If you have values external to the query that are used in the `Where` clause, ensure that the appropriate value is used in the `Where` clause at the time the query is executed.</span></span> <span data-ttu-id="ab39d-118">Další informace o provádění dotazů naleznete v tématu [zápis prvního dotazu LINQ](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="ab39d-118">For more information about query execution, see [Writing Your First LINQ Query](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
 <span data-ttu-id="ab39d-119">Můžete volat funkce v rámci `Where` klauzule k provedení výpočtu nebo operace s hodnotou z aktuálního prvku v kolekci.</span><span class="sxs-lookup"><span data-stu-id="ab39d-119">You can call functions within a `Where` clause to perform a calculation or operation on a value from the current element in the collection.</span></span> <span data-ttu-id="ab39d-120">Volání funkce v `Where` klauzuli může způsobit, že dotaz bude proveden ihned při jeho definování namísto při jeho použití.</span><span class="sxs-lookup"><span data-stu-id="ab39d-120">Calling a function in a `Where` clause can cause the query to be executed immediately when it is defined instead of when it is accessed.</span></span> <span data-ttu-id="ab39d-121">Další informace o provádění dotazů naleznete v tématu [zápis prvního dotazu LINQ](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="ab39d-121">For more information about query execution, see [Writing Your First LINQ Query](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab39d-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="ab39d-122">Example</span></span>  
 <span data-ttu-id="ab39d-123">Následující výraz dotazu používá `From` klauzuli pro deklaraci proměnné rozsahu `cust` pro každý `Customer` objekt v `customers` kolekci.</span><span class="sxs-lookup"><span data-stu-id="ab39d-123">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="ab39d-124">`Where`Klauzule používá proměnnou rozsahu k omezení výstupu na zákazníky ze zadané oblasti.</span><span class="sxs-lookup"><span data-stu-id="ab39d-124">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="ab39d-125">`For Each`Smyčka zobrazí název společnosti pro každého zákazníka ve výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="ab39d-125">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="example"></a><span data-ttu-id="ab39d-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="ab39d-126">Example</span></span>  
 <span data-ttu-id="ab39d-127">Následující příklad používá `And` a `Or` logické operátory v `Where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="ab39d-127">The following example uses `And` and `Or` logical operators in the `Where` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="ab39d-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab39d-128">See also</span></span>

- [<span data-ttu-id="ab39d-129">Představení technologie LINQ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ab39d-129">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="ab39d-130">Dotazy</span><span class="sxs-lookup"><span data-stu-id="ab39d-130">Queries</span></span>](index.md)
- [<span data-ttu-id="ab39d-131">Klauzule FROM</span><span class="sxs-lookup"><span data-stu-id="ab39d-131">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="ab39d-132">Klauzule SELECT</span><span class="sxs-lookup"><span data-stu-id="ab39d-132">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="ab39d-133">For Each...Next – příkaz</span><span class="sxs-lookup"><span data-stu-id="ab39d-133">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
