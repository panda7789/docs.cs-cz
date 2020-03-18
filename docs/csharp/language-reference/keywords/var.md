---
title: var - C# Odkaz
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: ff8348a725f43fa8789c73fa58549da26126369c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712881"
---
# <a name="var-c-reference"></a><span data-ttu-id="08742-102">var (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="08742-102">var (C# Reference)</span></span>

<span data-ttu-id="08742-103">Počínaje Visual C# 3.0 proměnné, které jsou deklarovány v `var`oboru metody může mít implicitní "typ" .</span><span class="sxs-lookup"><span data-stu-id="08742-103">Beginning in Visual C# 3.0, variables that are declared at method scope can have an implicit "type" `var`.</span></span> <span data-ttu-id="08742-104">Implicitně zadaný místní proměnná je silně zadaný, stejně jako kdybyste deklarovali typ sami, ale kompilátor určuje typ.</span><span class="sxs-lookup"><span data-stu-id="08742-104">An implicitly typed local variable is strongly typed just as if you had declared the type yourself, but the compiler determines the type.</span></span> <span data-ttu-id="08742-105">Následující dvě prohlášení `i` jsou funkčně rovnocenná:</span><span class="sxs-lookup"><span data-stu-id="08742-105">The following two declarations of `i` are functionally equivalent:</span></span>

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

<span data-ttu-id="08742-106">Další informace naleznete [v tématu Implicitně zadané místní proměnné](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) a vztahy typu v [operacích dotazů LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="08742-106">For more information, see [Implicitly Typed Local Variables](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) and [Type Relationships in LINQ Query Operations](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span>

## <a name="example"></a><span data-ttu-id="08742-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="08742-107">Example</span></span>

<span data-ttu-id="08742-108">Následující příklad ukazuje dva výrazy dotazu.</span><span class="sxs-lookup"><span data-stu-id="08742-108">The following example shows two query expressions.</span></span> <span data-ttu-id="08742-109">V prvním výrazu `var` je použití povoleno, ale není vyžadováno, protože typ výsledku `IEnumerable<string>`dotazu lze explicitně uvést jako .</span><span class="sxs-lookup"><span data-stu-id="08742-109">In the first expression, the use of `var` is permitted but is not required, because the type of the query result can be stated explicitly as an `IEnumerable<string>`.</span></span> <span data-ttu-id="08742-110">Však ve druhém `var` výrazu umožňuje výsledek je kolekce anonymní chod a název tohoto typu není přístupný s výjimkou kompilátoru samotného.</span><span class="sxs-lookup"><span data-stu-id="08742-110">However, in the second expression, `var` allows the result to be a collection of anonymous types, and the name of that type is not accessible except to the compiler itself.</span></span> <span data-ttu-id="08742-111">Použití `var` eliminuje požadavek na vytvoření nové třídy pro výsledek.</span><span class="sxs-lookup"><span data-stu-id="08742-111">Use of `var` eliminates the requirement to create a new class for the result.</span></span> <span data-ttu-id="08742-112">Všimněte si, že `foreach` v `item` příkladu #2 musí být implicitně zadána také proměnná iterace.</span><span class="sxs-lookup"><span data-stu-id="08742-112">Note that in Example #2, the `foreach` iteration variable `item` must also be implicitly typed.</span></span>

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a><span data-ttu-id="08742-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="08742-113">See also</span></span>

- [<span data-ttu-id="08742-114">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="08742-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="08742-115">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="08742-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="08742-116">Implicitně typované lokální proměnné</span><span class="sxs-lookup"><span data-stu-id="08742-116">Implicitly Typed Local Variables</span></span>](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
