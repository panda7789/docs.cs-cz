---
title: var- C# reference
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: ff8348a725f43fa8789c73fa58549da26126369c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712881"
---
# <a name="var-c-reference"></a><span data-ttu-id="5ff70-102">var (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="5ff70-102">var (C# Reference)</span></span>

<span data-ttu-id="5ff70-103">Počínaje jazykem Visual C# 3,0 proměnné, které jsou deklarovány v oboru metody, mohou mít implicitní typ "type" `var`.</span><span class="sxs-lookup"><span data-stu-id="5ff70-103">Beginning in Visual C# 3.0, variables that are declared at method scope can have an implicit "type" `var`.</span></span> <span data-ttu-id="5ff70-104">Implicitní typ lokální proměnné je silného typu, jako by byl typ deklarovaný sami, ale kompilátor určí typ.</span><span class="sxs-lookup"><span data-stu-id="5ff70-104">An implicitly typed local variable is strongly typed just as if you had declared the type yourself, but the compiler determines the type.</span></span> <span data-ttu-id="5ff70-105">Následující dvě deklarace `i` jsou funkčně ekvivalentní:</span><span class="sxs-lookup"><span data-stu-id="5ff70-105">The following two declarations of `i` are functionally equivalent:</span></span>

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

<span data-ttu-id="5ff70-106">Další informace naleznete v tématu [implicitně typované lokální proměnné](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) a [vztahy typů v operacích dotazu LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="5ff70-106">For more information, see [Implicitly Typed Local Variables](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) and [Type Relationships in LINQ Query Operations](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span>

## <a name="example"></a><span data-ttu-id="5ff70-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="5ff70-107">Example</span></span>

<span data-ttu-id="5ff70-108">Následující příklad ukazuje dva výrazy dotazu.</span><span class="sxs-lookup"><span data-stu-id="5ff70-108">The following example shows two query expressions.</span></span> <span data-ttu-id="5ff70-109">V prvním výrazu je použití `var` povoleno, ale není vyžadováno, protože typ výsledku dotazu lze explicitně uvést jako `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="5ff70-109">In the first expression, the use of `var` is permitted but is not required, because the type of the query result can be stated explicitly as an `IEnumerable<string>`.</span></span> <span data-ttu-id="5ff70-110">Ve druhém výrazu ale `var` umožňuje, aby byl výsledek kolekcí anonymních typů, a název tohoto typu není přístupný s výjimkou samotného kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="5ff70-110">However, in the second expression, `var` allows the result to be a collection of anonymous types, and the name of that type is not accessible except to the compiler itself.</span></span> <span data-ttu-id="5ff70-111">Použití `var` eliminuje požadavek na vytvoření nové třídy pro výsledek.</span><span class="sxs-lookup"><span data-stu-id="5ff70-111">Use of `var` eliminates the requirement to create a new class for the result.</span></span> <span data-ttu-id="5ff70-112">Všimněte si, že v příkladu #2 musí být také implicitně typované proměnné `foreach` iterace `item`.</span><span class="sxs-lookup"><span data-stu-id="5ff70-112">Note that in Example #2, the `foreach` iteration variable `item` must also be implicitly typed.</span></span>

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a><span data-ttu-id="5ff70-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5ff70-113">See also</span></span>

- [<span data-ttu-id="5ff70-114">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="5ff70-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5ff70-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="5ff70-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5ff70-116">Implicitně typované lokální proměnné</span><span class="sxs-lookup"><span data-stu-id="5ff70-116">Implicitly Typed Local Variables</span></span>](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
