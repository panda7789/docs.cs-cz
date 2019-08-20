---
title: WHERE (omezení obecného typu) – C# referenční informace
ms.custom: seodec18
ms.date: 04/12/2018
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: 1608cd7b888a67af3ccb98b16323e74a9c5ad4a9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608409"
---
# <a name="where-generic-type-constraint-c-reference"></a><span data-ttu-id="912ca-102">where (omezení obecného typu) (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="912ca-102">where (generic type constraint) (C# Reference)</span></span>

<span data-ttu-id="912ca-103">`where` Klauzule v obecné definici určuje omezení pro typy, které se používají jako argumenty pro parametry typu v obecném typu, metodě, delegátu nebo místní funkci.</span><span class="sxs-lookup"><span data-stu-id="912ca-103">The `where` clause in a generic definition specifies constraints on the types that are used as arguments for type parameters in a generic type, method, delegate, or local function.</span></span> <span data-ttu-id="912ca-104">Omezení mohou určovat rozhraní, základní třídy nebo vyžadovat, aby byl obecný typ odkaz, hodnota nebo nespravovaný typ.</span><span class="sxs-lookup"><span data-stu-id="912ca-104">Constraints can specify interfaces, base classes, or require a generic type to be a reference, value or unmanaged type.</span></span> <span data-ttu-id="912ca-105">Deklaruje možnosti, které musí mít argument typu.</span><span class="sxs-lookup"><span data-stu-id="912ca-105">They declare capabilities that the type argument must possess.</span></span>

<span data-ttu-id="912ca-106">Můžete například deklarovat obecnou třídu `MyGenericClass`, například parametr `T` typu implementuje <xref:System.IComparable%601> rozhraní:</span><span class="sxs-lookup"><span data-stu-id="912ca-106">For example, you can declare a generic class, `MyGenericClass`, such that the type parameter `T` implements the <xref:System.IComparable%601> interface:</span></span>

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> <span data-ttu-id="912ca-107">Další informace o klauzuli WHERE ve výrazu dotazu naleznete v tématu [Where klauzule](where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="912ca-107">For more information on the where clause in a query expression, see [where clause](where-clause.md).</span></span>

<span data-ttu-id="912ca-108">`where` Klauzule může také zahrnovat omezení základní třídy.</span><span class="sxs-lookup"><span data-stu-id="912ca-108">The `where` clause can also include a base class constraint.</span></span> <span data-ttu-id="912ca-109">Omezení základní třídy uvádí, že typ, který má být použit jako argument typu pro tento obecný typ, má zadanou třídu jako základní (nebo je základní třída) použitá jako argument typu pro tento obecný typ.</span><span class="sxs-lookup"><span data-stu-id="912ca-109">The base class constraint states that a type to be used as a type argument for that generic type has the specified class as a base class (or is that base class) to be used as a type argument for that generic type.</span></span> <span data-ttu-id="912ca-110">Pokud je použito omezení základní třídy, musí být uvedena před všemi ostatními omezeními pro tento parametr typu.</span><span class="sxs-lookup"><span data-stu-id="912ca-110">If the base class constraint is used, it must appear before any other constraints on that type parameter.</span></span> <span data-ttu-id="912ca-111">Některé typy nejsou povoleny jako omezení základní třídy: <xref:System.Object>, <xref:System.Array>a <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="912ca-111">Some types are disallowed as a base class constraint: <xref:System.Object>, <xref:System.Array>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="912ca-112">Před C# 7,3 <xref:System.Enum>,, <xref:System.Delegate>a bylytakézakázányjakoomezenízákladnítřídy.<xref:System.MulticastDelegate></span><span class="sxs-lookup"><span data-stu-id="912ca-112">Prior to C# 7.3, <xref:System.Enum>, <xref:System.Delegate>, and <xref:System.MulticastDelegate> were also disallowed as base class constraints.</span></span> <span data-ttu-id="912ca-113">Následující příklad ukazuje typy, které lze nyní zadat jako základní třídu:</span><span class="sxs-lookup"><span data-stu-id="912ca-113">The following example shows the types that can now be specified as a base class:</span></span>

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

<span data-ttu-id="912ca-114">Klauzule může určit, že typ `class` je nebo `struct`. `where`</span><span class="sxs-lookup"><span data-stu-id="912ca-114">The `where` clause can specify that the type is a `class` or a `struct`.</span></span> <span data-ttu-id="912ca-115">Omezení eliminuje nutnost zadat `System.ValueType`omezení základní třídy. `struct`</span><span class="sxs-lookup"><span data-stu-id="912ca-115">The `struct` constraint removes the need to specify a base class constraint of `System.ValueType`.</span></span> <span data-ttu-id="912ca-116">`System.ValueType` Typ nelze použít jako omezení základní třídy.</span><span class="sxs-lookup"><span data-stu-id="912ca-116">The `System.ValueType` type may not be used as a base class constraint.</span></span> <span data-ttu-id="912ca-117">Následující příklad ukazuje obě `class` omezení a: `struct`</span><span class="sxs-lookup"><span data-stu-id="912ca-117">The following example shows both the `class` and `struct` constraints:</span></span>

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

<span data-ttu-id="912ca-118">Klauzule může také `unmanaged` obsahovat omezení. `where`</span><span class="sxs-lookup"><span data-stu-id="912ca-118">The `where` clause may also include an `unmanaged` constraint.</span></span> <span data-ttu-id="912ca-119">Omezení omezuje parametr typu na typy známé jako nespravované [typy.](../builtin-types/unmanaged-types.md) `unmanaged`</span><span class="sxs-lookup"><span data-stu-id="912ca-119">The `unmanaged` constraint limits the type parameter to types known as [unmanaged types](../builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="912ca-120">Omezení usnadňuje psaní kódu spolupráce na nízké úrovni v C# `unmanaged`</span><span class="sxs-lookup"><span data-stu-id="912ca-120">The `unmanaged` constraint makes it easier to write low-level interop code in C#.</span></span> <span data-ttu-id="912ca-121">Toto omezení povoluje opakovaně použitelné rutiny ve všech nespravovaných typech.</span><span class="sxs-lookup"><span data-stu-id="912ca-121">This constraint enables reusable routines across all unmanaged types.</span></span> <span data-ttu-id="912ca-122">Omezení nelze kombinovat `class` s omezením or `struct`. `unmanaged`</span><span class="sxs-lookup"><span data-stu-id="912ca-122">The `unmanaged` constraint can't be combined with the `class` or `struct` constraint.</span></span> <span data-ttu-id="912ca-123">Omezení vynutilo, že typ musí `struct`být: `unmanaged`</span><span class="sxs-lookup"><span data-stu-id="912ca-123">The `unmanaged` constraint enforces that the type must be a `struct`:</span></span>

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

<span data-ttu-id="912ca-124">Klauzule může také zahrnovat `new()`omezení konstruktoru. `where`</span><span class="sxs-lookup"><span data-stu-id="912ca-124">The `where` clause may also include a constructor constraint, `new()`.</span></span> <span data-ttu-id="912ca-125">Toto omezení umožňuje vytvořit instanci parametru typu pomocí `new` operátoru.</span><span class="sxs-lookup"><span data-stu-id="912ca-125">That constraint makes it possible to create an instance of a type parameter using the `new` operator.</span></span> <span data-ttu-id="912ca-126">[Omezení New ()](new-constraint.md) umožňuje, aby kompilátor věděl, že libovolný zadaný argument typu musí mít přístupný parametr bez parametrů, nebo konstruktor default--.</span><span class="sxs-lookup"><span data-stu-id="912ca-126">The [new() Constraint](new-constraint.md) lets the compiler know that any type argument supplied must have an accessible parameterless--or default-- constructor.</span></span> <span data-ttu-id="912ca-127">Příklad:</span><span class="sxs-lookup"><span data-stu-id="912ca-127">For example:</span></span>

[!code-csharp[using the new constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

<span data-ttu-id="912ca-128">Omezení `new()` se`where` v klauzuli zobrazí jako poslední.</span><span class="sxs-lookup"><span data-stu-id="912ca-128">The `new()` constraint appears last in the `where` clause.</span></span> <span data-ttu-id="912ca-129">Omezení nelze kombinovat `struct` s omezeními nebo `unmanaged`. `new()`</span><span class="sxs-lookup"><span data-stu-id="912ca-129">The `new()` constraint can't be combined with the `struct` or `unmanaged` constraints.</span></span> <span data-ttu-id="912ca-130">Všechny typy vyhovující těmto omezením musí mít přístupný konstruktor bez parametrů, což omezení je `new()` redundantní.</span><span class="sxs-lookup"><span data-stu-id="912ca-130">All types satisfying those constraints must have an accessible parameterless constructor, making the `new()` constraint redundant.</span></span>

<span data-ttu-id="912ca-131">S více parametry typu použijte jednu `where` klauzuli pro každý parametr typu, například:</span><span class="sxs-lookup"><span data-stu-id="912ca-131">With multiple type parameters, use one `where` clause for each type parameter, for example:</span></span>

[!code-csharp[using multiple where constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

<span data-ttu-id="912ca-132">Omezení můžete také připojit k parametrům typu obecných metod, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="912ca-132">You can also attach constraints to type parameters of generic methods, as shown in the following example:</span></span>

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

<span data-ttu-id="912ca-133">Všimněte si, že syntaxe pro popis omezení parametrů typu na delegátech je stejná jako u metod:</span><span class="sxs-lookup"><span data-stu-id="912ca-133">Notice that the syntax to describe type parameter constraints on delegates is the same as that of methods:</span></span>

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

<span data-ttu-id="912ca-134">Informace o obecných delegátech najdete v tématu [Obecné delegáty](../../programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="912ca-134">For information on generic delegates, see [Generic Delegates](../../programming-guide/generics/generic-delegates.md).</span></span>

<span data-ttu-id="912ca-135">Podrobnosti o syntaxi a použití omezení naleznete v tématu [omezení u parametrů typu](../../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="912ca-135">For details on the syntax and use of constraints, see [Constraints on Type Parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="912ca-136">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="912ca-136">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="912ca-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="912ca-137">See also</span></span>

- [<span data-ttu-id="912ca-138">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="912ca-138">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="912ca-139">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="912ca-139">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="912ca-140">Úvod do obecných typů</span><span class="sxs-lookup"><span data-stu-id="912ca-140">Introduction to Generics</span></span>](../../programming-guide/generics/index.md)
- [<span data-ttu-id="912ca-141">new – omezení</span><span class="sxs-lookup"><span data-stu-id="912ca-141">new Constraint</span></span>](./new-constraint.md)
- [<span data-ttu-id="912ca-142">Omezení parametrů typů</span><span class="sxs-lookup"><span data-stu-id="912ca-142">Constraints on Type Parameters</span></span>](../../programming-guide/generics/constraints-on-type-parameters.md)
