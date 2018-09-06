---
title: Zpracování hodnot null ve výrazech dotazů (LINQ v JAZYKU C#)
description: Zjistěte, jak zpracování hodnot null ve výrazech dotazů LINQ v jazyce C#.
ms.date: 12/1/2016
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: 2c477ef371dbb424c72fb9d34948760b7e3f5609
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43797754"
---
# <a name="handle-null-values-in-query-expressions"></a><span data-ttu-id="70ab5-103">Zpracování hodnot null ve výrazech dotazů</span><span class="sxs-lookup"><span data-stu-id="70ab5-103">Handle null values in query expressions</span></span>

<span data-ttu-id="70ab5-104">Tento příklad ukazuje, jak zpracování možných hodnot null ve zdrojové kolekce.</span><span class="sxs-lookup"><span data-stu-id="70ab5-104">This example shows how to handle possible null values in source collections.</span></span> <span data-ttu-id="70ab5-105">Kolekci objektů, jako <xref:System.Collections.Generic.IEnumerable%601> může obsahovat elementy, jejichž hodnota je [null](../language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="70ab5-105">An object collection such as an <xref:System.Collections.Generic.IEnumerable%601> can contain elements whose value is [null](../language-reference/keywords/null.md).</span></span> <span data-ttu-id="70ab5-106">Pokud zdrojová kolekce má hodnotu null nebo obsahuje prvek, jehož hodnota je null a dotaz ke zpracování hodnot null <xref:System.NullReferenceException> bude vyvolána výjimka při spouštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="70ab5-106">If a source collection is null or contains an element whose value is null, and your query does not handle null values, a <xref:System.NullReferenceException> will be thrown when you execute the query.</span></span>

## <a name="example"></a><span data-ttu-id="70ab5-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="70ab5-107">Example</span></span>

<span data-ttu-id="70ab5-108">Vám umožní kódování defenzivně, aby výjimka nulového odkazu, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="70ab5-108">You can code defensively to avoid a null reference exception as shown in the following example:</span></span>

[!code-csharp[csProgGuideLINQ#82](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]

<span data-ttu-id="70ab5-109">V předchozím příkladu `where` klauzule vyfiltruje všechny prázdné prvky v sekvenci kategorií.</span><span class="sxs-lookup"><span data-stu-id="70ab5-109">In the previous example, the `where` clause filters out all null elements in the categories sequence.</span></span> <span data-ttu-id="70ab5-110">Tato technika je nezávislé na kontrolu hodnot null v klauzuli join.</span><span class="sxs-lookup"><span data-stu-id="70ab5-110">This technique is independent of the null check in the join clause.</span></span> <span data-ttu-id="70ab5-111">Podmíněný výraz s hodnotou null v tomto příkladu funguje, protože `Products.CategoryID` je typu `int?` což je zkratka pro `Nullable<int>`.</span><span class="sxs-lookup"><span data-stu-id="70ab5-111">The conditional expression with null in this example works because `Products.CategoryID` is of type `int?` which is shorthand for `Nullable<int>`.</span></span>

## <a name="example"></a><span data-ttu-id="70ab5-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="70ab5-112">Example</span></span>

<span data-ttu-id="70ab5-113">V klauzuli join Pokud pouze jeden z klíčů porovnání je typ s možnou hodnotou Null, můžete přetypovat jiné na typ připouštějící hodnotu Null ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="70ab5-113">In a join clause, if only one of the comparison keys is a nullable value type, you can cast the other to a nullable type in the query expression.</span></span> <span data-ttu-id="70ab5-114">V následujícím příkladu se předpokládá, že `EmployeeID` je sloupec, který obsahuje hodnoty typu `int?`:</span><span class="sxs-lookup"><span data-stu-id="70ab5-114">In the following example, assume that `EmployeeID` is a column that contains values of type `int?`:</span></span>

[!code-csharp[csProgGuideLINQ#83](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]

## <a name="see-also"></a><span data-ttu-id="70ab5-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70ab5-115">See also</span></span>

- <xref:System.Nullable%601>  
- [<span data-ttu-id="70ab5-116">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="70ab5-116">Language Integrated Query (LINQ)</span></span>](index.md)  
- [<span data-ttu-id="70ab5-117">Typy s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="70ab5-117">Nullable types</span></span>](../programming-guide/nullable-types/index.md)  
