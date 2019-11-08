---
title: Zpracování hodnot null ve výrazech dotazů (LINQ C#in)
description: Naučte se zpracovávat hodnoty null ve výrazech dotazů LINQ C#v.
ms.date: 12/01/2016
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: c9a3aaec05fa029a8db66826bdcb4a1d106176e3
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736857"
---
# <a name="handle-null-values-in-query-expressions"></a><span data-ttu-id="a96cc-103">Zpracování hodnot Null ve výrazech dotazů</span><span class="sxs-lookup"><span data-stu-id="a96cc-103">Handle null values in query expressions</span></span>

<span data-ttu-id="a96cc-104">Tento příklad ukazuje, jak zpracovat možné hodnoty null ve zdrojových kolekcích.</span><span class="sxs-lookup"><span data-stu-id="a96cc-104">This example shows how to handle possible null values in source collections.</span></span> <span data-ttu-id="a96cc-105">Kolekce objektů, jako je například <xref:System.Collections.Generic.IEnumerable%601> může obsahovat elementy, jejichž hodnota je [null](../language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="a96cc-105">An object collection such as an <xref:System.Collections.Generic.IEnumerable%601> can contain elements whose value is [null](../language-reference/keywords/null.md).</span></span> <span data-ttu-id="a96cc-106">Pokud zdrojová kolekce má hodnotu null nebo obsahuje element, jehož hodnota je null, a dotaz nezpracovává hodnoty null, bude při spuštění dotazu vyvolána <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="a96cc-106">If a source collection is null or contains an element whose value is null, and your query does not handle null values, a <xref:System.NullReferenceException> will be thrown when you execute the query.</span></span>

## <a name="example"></a><span data-ttu-id="a96cc-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="a96cc-107">Example</span></span>

<span data-ttu-id="a96cc-108">Můžete kódovat defensively, aby se předešlo výjimce odkazu s hodnotou null, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="a96cc-108">You can code defensively to avoid a null reference exception as shown in the following example:</span></span>

[!code-csharp[csProgGuideLINQ#82](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]

<span data-ttu-id="a96cc-109">Klauzule `where` v předchozím příkladu vyfiltruje všechny prvky null v pořadí kategorií.</span><span class="sxs-lookup"><span data-stu-id="a96cc-109">In the previous example, the `where` clause filters out all null elements in the categories sequence.</span></span> <span data-ttu-id="a96cc-110">Tato technika je nezávislá na vrácení hodnoty null v klauzuli JOIN.</span><span class="sxs-lookup"><span data-stu-id="a96cc-110">This technique is independent of the null check in the join clause.</span></span> <span data-ttu-id="a96cc-111">Podmíněný výraz s hodnotou null v tomto příkladu funguje, protože `Products.CategoryID` je typu `int?`, který je zkrácený pro `Nullable<int>`.</span><span class="sxs-lookup"><span data-stu-id="a96cc-111">The conditional expression with null in this example works because `Products.CategoryID` is of type `int?` which is shorthand for `Nullable<int>`.</span></span>

## <a name="example"></a><span data-ttu-id="a96cc-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="a96cc-112">Example</span></span>

<span data-ttu-id="a96cc-113">Pokud je v klauzuli JOIN pouze jeden z porovnávacích klíčů, lze typ hodnoty s možnou hodnotou null přetypovat na typ s možnou hodnotou null ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="a96cc-113">In a join clause, if only one of the comparison keys is a nullable value type, you can cast the other to a nullable type in the query expression.</span></span> <span data-ttu-id="a96cc-114">V následujícím příkladu Předpokládejme, že `EmployeeID` je sloupec, který obsahuje hodnoty typu `int?`:</span><span class="sxs-lookup"><span data-stu-id="a96cc-114">In the following example, assume that `EmployeeID` is a column that contains values of type `int?`:</span></span>

[!code-csharp[csProgGuideLINQ#83](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]

## <a name="see-also"></a><span data-ttu-id="a96cc-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a96cc-115">See also</span></span>

- <xref:System.Nullable%601>
- [<span data-ttu-id="a96cc-116">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="a96cc-116">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="a96cc-117">Typy hodnot s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="a96cc-117">Nullable value types</span></span>](../language-reference/builtin-types/nullable-value-types.md)
