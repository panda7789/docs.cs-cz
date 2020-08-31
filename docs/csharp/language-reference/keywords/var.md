---
title: var – reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: d944cde932b5c1f5ef1439ee46a1447e107e6ac9
ms.sourcegitcommit: 2560a355c76b0a04cba0d34da870df9ad94ceca3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2020
ms.locfileid: "89053072"
---
# <a name="var-c-reference"></a><span data-ttu-id="b86b3-102">var (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b86b3-102">var (C# Reference)</span></span>

<span data-ttu-id="b86b3-103">Počínaje jazykem Visual C# 3,0 proměnné, které jsou deklarovány v oboru metody, mohou mít implicitní "typ" `var` .</span><span class="sxs-lookup"><span data-stu-id="b86b3-103">Beginning in Visual C# 3.0, variables that are declared at method scope can have an implicit "type" `var`.</span></span> <span data-ttu-id="b86b3-104">Implicitní typ lokální proměnné je silného typu, jako by byl typ deklarovaný sami, ale kompilátor určí typ.</span><span class="sxs-lookup"><span data-stu-id="b86b3-104">An implicitly typed local variable is strongly typed just as if you had declared the type yourself, but the compiler determines the type.</span></span> <span data-ttu-id="b86b3-105">Následující dvě deklarace `i` jsou funkčně ekvivalentní:</span><span class="sxs-lookup"><span data-stu-id="b86b3-105">The following two declarations of `i` are functionally equivalent:</span></span>

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

<span data-ttu-id="b86b3-106">Další informace naleznete v tématu [implicitně typované lokální proměnné](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) a [vztahy typů v operacích dotazu LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="b86b3-106">For more information, see [Implicitly Typed Local Variables](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) and [Type Relationships in LINQ Query Operations](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b86b3-107">Při `var` použití s povolenými typy odkazů s možnou hodnotou null vždy implikuje typ odkazu s možnou hodnotou null i v případě, že typ výrazu nemá hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="b86b3-107">When `var` is used with nullable reference types enabled, it always implies a nullable reference type even if the expression type isn't nullable.</span></span>

## <a name="example"></a><span data-ttu-id="b86b3-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="b86b3-108">Example</span></span>

<span data-ttu-id="b86b3-109">Následující příklad ukazuje dva výrazy dotazu.</span><span class="sxs-lookup"><span data-stu-id="b86b3-109">The following example shows two query expressions.</span></span> <span data-ttu-id="b86b3-110">V prvním výrazu je použití `var` povoleno, ale není vyžadováno, protože typ výsledku dotazu lze explicitně uvést jako `IEnumerable<string>` .</span><span class="sxs-lookup"><span data-stu-id="b86b3-110">In the first expression, the use of `var` is permitted but is not required, because the type of the query result can be stated explicitly as an `IEnumerable<string>`.</span></span> <span data-ttu-id="b86b3-111">Ve druhém výrazu však může `var` být výsledkem kolekce anonymních typů a název tohoto typu není přístupný s výjimkou samotného kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="b86b3-111">However, in the second expression, `var` allows the result to be a collection of anonymous types, and the name of that type is not accessible except to the compiler itself.</span></span> <span data-ttu-id="b86b3-112">Použití `var` eliminuje požadavek na vytvoření nové třídy pro výsledek.</span><span class="sxs-lookup"><span data-stu-id="b86b3-112">Use of `var` eliminates the requirement to create a new class for the result.</span></span> <span data-ttu-id="b86b3-113">Všimněte si, že v příkladu #2 `foreach` musí být proměnná iterace `item` také implicitně typu.</span><span class="sxs-lookup"><span data-stu-id="b86b3-113">Note that in Example #2, the `foreach` iteration variable `item` must also be implicitly typed.</span></span>

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a><span data-ttu-id="b86b3-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="b86b3-114">See also</span></span>

- [<span data-ttu-id="b86b3-115">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b86b3-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b86b3-116">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="b86b3-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b86b3-117">Implicitně typované lokální proměnné</span><span class="sxs-lookup"><span data-stu-id="b86b3-117">Implicitly Typed Local Variables</span></span>](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
