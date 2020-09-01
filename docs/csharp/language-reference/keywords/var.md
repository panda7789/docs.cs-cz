---
description: var – reference jazyka C#
title: var – reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: 303a880a54a79e50515060e0ea28e8d021fa1b76
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141709"
---
# <a name="var-c-reference"></a><span data-ttu-id="ad57d-103">var (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ad57d-103">var (C# Reference)</span></span>

<span data-ttu-id="ad57d-104">Počínaje jazykem Visual C# 3,0 proměnné, které jsou deklarovány v oboru metody, mohou mít implicitní "typ" `var` .</span><span class="sxs-lookup"><span data-stu-id="ad57d-104">Beginning in Visual C# 3.0, variables that are declared at method scope can have an implicit "type" `var`.</span></span> <span data-ttu-id="ad57d-105">Implicitní typ lokální proměnné je silného typu, jako by byl typ deklarovaný sami, ale kompilátor určí typ.</span><span class="sxs-lookup"><span data-stu-id="ad57d-105">An implicitly typed local variable is strongly typed just as if you had declared the type yourself, but the compiler determines the type.</span></span> <span data-ttu-id="ad57d-106">Následující dvě deklarace `i` jsou funkčně ekvivalentní:</span><span class="sxs-lookup"><span data-stu-id="ad57d-106">The following two declarations of `i` are functionally equivalent:</span></span>

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

<span data-ttu-id="ad57d-107">Další informace naleznete v tématu [implicitně typované lokální proměnné](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) a [vztahy typů v operacích dotazu LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="ad57d-107">For more information, see [Implicitly Typed Local Variables](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) and [Type Relationships in LINQ Query Operations](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ad57d-108">Při `var` použití s povolenými typy odkazů s možnou hodnotou null vždy implikuje typ odkazu s možnou hodnotou null i v případě, že typ výrazu nemá hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="ad57d-108">When `var` is used with nullable reference types enabled, it always implies a nullable reference type even if the expression type isn't nullable.</span></span>

## <a name="example"></a><span data-ttu-id="ad57d-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="ad57d-109">Example</span></span>

<span data-ttu-id="ad57d-110">Následující příklad ukazuje dva výrazy dotazu.</span><span class="sxs-lookup"><span data-stu-id="ad57d-110">The following example shows two query expressions.</span></span> <span data-ttu-id="ad57d-111">V prvním výrazu je použití `var` povoleno, ale není vyžadováno, protože typ výsledku dotazu lze explicitně uvést jako `IEnumerable<string>` .</span><span class="sxs-lookup"><span data-stu-id="ad57d-111">In the first expression, the use of `var` is permitted but is not required, because the type of the query result can be stated explicitly as an `IEnumerable<string>`.</span></span> <span data-ttu-id="ad57d-112">Ve druhém výrazu však může `var` být výsledkem kolekce anonymních typů a název tohoto typu není přístupný s výjimkou samotného kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="ad57d-112">However, in the second expression, `var` allows the result to be a collection of anonymous types, and the name of that type is not accessible except to the compiler itself.</span></span> <span data-ttu-id="ad57d-113">Použití `var` eliminuje požadavek na vytvoření nové třídy pro výsledek.</span><span class="sxs-lookup"><span data-stu-id="ad57d-113">Use of `var` eliminates the requirement to create a new class for the result.</span></span> <span data-ttu-id="ad57d-114">Všimněte si, že v příkladu #2 `foreach` musí být proměnná iterace `item` také implicitně typu.</span><span class="sxs-lookup"><span data-stu-id="ad57d-114">Note that in Example #2, the `foreach` iteration variable `item` must also be implicitly typed.</span></span>

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a><span data-ttu-id="ad57d-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="ad57d-115">See also</span></span>

- [<span data-ttu-id="ad57d-116">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ad57d-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ad57d-117">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="ad57d-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ad57d-118">Implicitně typované lokální proměnné</span><span class="sxs-lookup"><span data-stu-id="ad57d-118">Implicitly Typed Local Variables</span></span>](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
