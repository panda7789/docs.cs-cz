---
title: Zpracování nulových hodnot ve výrazech dotazu (LINQ v c#)
description: Zjistěte, jak zpracovat hodnoty null ve výrazech dotazu LINQ v c#.
ms.date: 12/01/2016
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: 3da490b72bd518df7be8c14b34655af8c6f84929
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249302"
---
# <a name="handle-null-values-in-query-expressions"></a><span data-ttu-id="e8fc8-103">Zpracování hodnot Null ve výrazech dotazů</span><span class="sxs-lookup"><span data-stu-id="e8fc8-103">Handle null values in query expressions</span></span>

<span data-ttu-id="e8fc8-104">Tento příklad ukazuje, jak zpracovat možné hodnoty null ve zdrojových kolekcích.</span><span class="sxs-lookup"><span data-stu-id="e8fc8-104">This example shows how to handle possible null values in source collections.</span></span> <span data-ttu-id="e8fc8-105">Kolekce objektů, jako <xref:System.Collections.Generic.IEnumerable%601> je například může obsahovat prvky, jejichž hodnota je [null](../language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="e8fc8-105">An object collection such as an <xref:System.Collections.Generic.IEnumerable%601> can contain elements whose value is [null](../language-reference/keywords/null.md).</span></span> <span data-ttu-id="e8fc8-106">Pokud zdrojkolekce je null nebo obsahuje prvek, jehož hodnota je null <xref:System.NullReferenceException> a dotaz nezpracovává hodnoty null, bude vyvolána při spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="e8fc8-106">If a source collection is null or contains an element whose value is null, and your query does not handle null values, a <xref:System.NullReferenceException> will be thrown when you execute the query.</span></span>

## <a name="example"></a><span data-ttu-id="e8fc8-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8fc8-107">Example</span></span>

<span data-ttu-id="e8fc8-108">Můžete kód defenzivně, aby se zabránilo výjimku nulového odkazu, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="e8fc8-108">You can code defensively to avoid a null reference exception as shown in the following example:</span></span>

[!code-csharp[csProgGuideLINQ#82](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]

<span data-ttu-id="e8fc8-109">V předchozím příkladu `where` klauzule filtruje všechny prvky null v pořadí kategorií.</span><span class="sxs-lookup"><span data-stu-id="e8fc8-109">In the previous example, the `where` clause filters out all null elements in the categories sequence.</span></span> <span data-ttu-id="e8fc8-110">Tato technika je nezávislá na nulové kontrole v klauzuli join.</span><span class="sxs-lookup"><span data-stu-id="e8fc8-110">This technique is independent of the null check in the join clause.</span></span> <span data-ttu-id="e8fc8-111">Podmíněný výraz s hodnotou null `Products.CategoryID` v `int?` tomto příkladu `Nullable<int>`funguje, protože je typu, který je zkratka pro .</span><span class="sxs-lookup"><span data-stu-id="e8fc8-111">The conditional expression with null in this example works because `Products.CategoryID` is of type `int?` which is shorthand for `Nullable<int>`.</span></span>

## <a name="example"></a><span data-ttu-id="e8fc8-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8fc8-112">Example</span></span>

<span data-ttu-id="e8fc8-113">V join klauzuli, pokud pouze jeden z porovnávacích klíčů je typ hodnoty s možnou hodnotou s hodnotou, můžete přetypovat druhý na typ hodnoty s hodnotou null ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="e8fc8-113">In a join clause, if only one of the comparison keys is a nullable value type, you can cast the other to a nullable value type in the query expression.</span></span> <span data-ttu-id="e8fc8-114">V následujícím příkladu `EmployeeID` předpokládejme, že se `int?`jedná o sloupec, který obsahuje hodnoty typu :</span><span class="sxs-lookup"><span data-stu-id="e8fc8-114">In the following example, assume that `EmployeeID` is a column that contains values of type `int?`:</span></span>

[!code-csharp[csProgGuideLINQ#83](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]

## <a name="see-also"></a><span data-ttu-id="e8fc8-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="e8fc8-115">See also</span></span>

- <xref:System.Nullable%601>
- [<span data-ttu-id="e8fc8-116">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="e8fc8-116">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="e8fc8-117">Typy hodnot s možnou hodnotou s hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="e8fc8-117">Nullable value types</span></span>](../language-reference/builtin-types/nullable-value-types.md)
