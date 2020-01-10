---
title: WHERE (omezení obecného typu) – C# referenční informace
ms.date: 04/12/2018
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: 19bf7682916336173ed93619fb6f0ff1242a1b30
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712803"
---
# <a name="where-generic-type-constraint-c-reference"></a><span data-ttu-id="aac2a-102">where (omezení obecného typu) (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="aac2a-102">where (generic type constraint) (C# Reference)</span></span>

<span data-ttu-id="aac2a-103">Klauzule `where` v obecné definici určuje omezení pro typy, které se používají jako argumenty parametrů typu v obecném typu, metodě, delegátu nebo místní funkci.</span><span class="sxs-lookup"><span data-stu-id="aac2a-103">The `where` clause in a generic definition specifies constraints on the types that are used as arguments for type parameters in a generic type, method, delegate, or local function.</span></span> <span data-ttu-id="aac2a-104">Omezení mohou určovat rozhraní, základní třídy nebo vyžadovat, aby byl obecný typ odkaz, hodnota nebo nespravovaný typ.</span><span class="sxs-lookup"><span data-stu-id="aac2a-104">Constraints can specify interfaces, base classes, or require a generic type to be a reference, value, or unmanaged type.</span></span> <span data-ttu-id="aac2a-105">Deklaruje možnosti, které musí mít argument typu.</span><span class="sxs-lookup"><span data-stu-id="aac2a-105">They declare capabilities that the type argument must possess.</span></span>

<span data-ttu-id="aac2a-106">Například můžete deklarovat obecnou třídu, `MyGenericClass`, tak, že parametr typu `T` implementuje rozhraní <xref:System.IComparable%601>:</span><span class="sxs-lookup"><span data-stu-id="aac2a-106">For example, you can declare a generic class, `MyGenericClass`, such that the type parameter `T` implements the <xref:System.IComparable%601> interface:</span></span>

[!code-csharp[using an interface constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> <span data-ttu-id="aac2a-107">Další informace o klauzuli WHERE ve výrazu dotazu naleznete v tématu [Where klauzule](where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="aac2a-107">For more information on the where clause in a query expression, see [where clause](where-clause.md).</span></span>

<span data-ttu-id="aac2a-108">Klauzule `where` může také zahrnovat omezení základní třídy.</span><span class="sxs-lookup"><span data-stu-id="aac2a-108">The `where` clause can also include a base class constraint.</span></span> <span data-ttu-id="aac2a-109">Omezení základní třídy uvádí, že typ, který má být použit jako argument typu pro tento obecný typ, má zadanou třídu jako základní (nebo je základní třída) použitá jako argument typu pro tento obecný typ.</span><span class="sxs-lookup"><span data-stu-id="aac2a-109">The base class constraint states that a type to be used as a type argument for that generic type has the specified class as a base class (or is that base class) to be used as a type argument for that generic type.</span></span> <span data-ttu-id="aac2a-110">Pokud je použito omezení základní třídy, musí být uvedena před všemi ostatními omezeními pro tento parametr typu.</span><span class="sxs-lookup"><span data-stu-id="aac2a-110">If the base class constraint is used, it must appear before any other constraints on that type parameter.</span></span> <span data-ttu-id="aac2a-111">Některé typy nejsou povoleny jako omezení základní třídy: <xref:System.Object>, <xref:System.Array>a <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="aac2a-111">Some types are disallowed as a base class constraint: <xref:System.Object>, <xref:System.Array>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="aac2a-112">Před C# 7,3, <xref:System.Enum>, <xref:System.Delegate>a <xref:System.MulticastDelegate> byly také zakázány jako omezení základní třídy.</span><span class="sxs-lookup"><span data-stu-id="aac2a-112">Prior to C# 7.3, <xref:System.Enum>, <xref:System.Delegate>, and <xref:System.MulticastDelegate> were also disallowed as base class constraints.</span></span> <span data-ttu-id="aac2a-113">Následující příklad ukazuje typy, které lze nyní zadat jako základní třídu:</span><span class="sxs-lookup"><span data-stu-id="aac2a-113">The following example shows the types that can now be specified as a base class:</span></span>

[!code-csharp[using an interface constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

<span data-ttu-id="aac2a-114">Klauzule `where` může určit, že typ je `class` nebo `struct`.</span><span class="sxs-lookup"><span data-stu-id="aac2a-114">The `where` clause can specify that the type is a `class` or a `struct`.</span></span> <span data-ttu-id="aac2a-115">Omezení `struct` eliminuje nutnost zadat omezení základní třídy `System.ValueType`.</span><span class="sxs-lookup"><span data-stu-id="aac2a-115">The `struct` constraint removes the need to specify a base class constraint of `System.ValueType`.</span></span> <span data-ttu-id="aac2a-116">Typ `System.ValueType` nesmí být použit jako omezení základní třídy.</span><span class="sxs-lookup"><span data-stu-id="aac2a-116">The `System.ValueType` type may not be used as a base class constraint.</span></span> <span data-ttu-id="aac2a-117">Následující příklad ukazuje omezení `class` i `struct`:</span><span class="sxs-lookup"><span data-stu-id="aac2a-117">The following example shows both the `class` and `struct` constraints:</span></span>

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

<span data-ttu-id="aac2a-118">Klauzule `where` může zahrnovat omezení `notnull`.</span><span class="sxs-lookup"><span data-stu-id="aac2a-118">The `where` clause may include the `notnull` constraint.</span></span> <span data-ttu-id="aac2a-119">Omezení `notnull` omezuje parametr typu na typy, které neumožňují hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="aac2a-119">The `notnull` constraint limits the type parameter to non-nullable types.</span></span> <span data-ttu-id="aac2a-120">Tento typ může být [typ hodnoty](struct.md) nebo typ odkazu, který neumožňuje hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="aac2a-120">That type may be a [value type](struct.md) or a non-nullable reference type.</span></span> <span data-ttu-id="aac2a-121">Omezení `notnull` je k dispozici počínaje C# verzí 8,0 pro kód zkompilovaný v [kontextu`nullable enable`](../../nullable-references.md#nullable-contexts).</span><span class="sxs-lookup"><span data-stu-id="aac2a-121">The `notnull` constraint is available starting in C# 8.0 for code compiled in a [`nullable enable` context](../../nullable-references.md#nullable-contexts).</span></span> <span data-ttu-id="aac2a-122">Na rozdíl od jiných omezení, pokud argument typu narušuje omezení `notnull`, kompilátor vygeneruje upozornění namísto chyby.</span><span class="sxs-lookup"><span data-stu-id="aac2a-122">Unlike other constraints, if a type argument violates the `notnull` constraint, the compiler generates a warning instead of an error.</span></span> <span data-ttu-id="aac2a-123">Upozornění se generují jenom v kontextu `nullable enable`.</span><span class="sxs-lookup"><span data-stu-id="aac2a-123">Warnings are only generated in a `nullable enable` context.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="aac2a-124">Obecné deklarace, které zahrnují omezení `notnull` lze použít v kontextu s možnou hodnotou null, ale kompilátor neuplatňuje omezení.</span><span class="sxs-lookup"><span data-stu-id="aac2a-124">Generic declarations that include the `notnull` constraint can be used in a nullable oblivious context, but compiler does not enforce the constraint.</span></span>

[!code-csharp[using the nonnull constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#NotNull)]

<span data-ttu-id="aac2a-125">Klauzule `where` může také zahrnovat omezení `unmanaged`.</span><span class="sxs-lookup"><span data-stu-id="aac2a-125">The `where` clause may also include an `unmanaged` constraint.</span></span> <span data-ttu-id="aac2a-126">Omezení `unmanaged` omezuje parametr typu na typy známé jako [nespravované typy](../builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="aac2a-126">The `unmanaged` constraint limits the type parameter to types known as [unmanaged types](../builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="aac2a-127">Omezení `unmanaged` usnadňuje psaní kódu spolupráce na nízké úrovni v C#.</span><span class="sxs-lookup"><span data-stu-id="aac2a-127">The `unmanaged` constraint makes it easier to write low-level interop code in C#.</span></span> <span data-ttu-id="aac2a-128">Toto omezení povoluje opakovaně použitelné rutiny ve všech nespravovaných typech.</span><span class="sxs-lookup"><span data-stu-id="aac2a-128">This constraint enables reusable routines across all unmanaged types.</span></span> <span data-ttu-id="aac2a-129">Omezení `unmanaged` nelze kombinovat s omezením `class` nebo `struct`.</span><span class="sxs-lookup"><span data-stu-id="aac2a-129">The `unmanaged` constraint can't be combined with the `class` or `struct` constraint.</span></span> <span data-ttu-id="aac2a-130">Omezení `unmanaged` vynutilo, že typ musí být `struct`:</span><span class="sxs-lookup"><span data-stu-id="aac2a-130">The `unmanaged` constraint enforces that the type must be a `struct`:</span></span>

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

<span data-ttu-id="aac2a-131">Klauzule `where` může také zahrnovat omezení konstruktoru `new()`.</span><span class="sxs-lookup"><span data-stu-id="aac2a-131">The `where` clause may also include a constructor constraint, `new()`.</span></span> <span data-ttu-id="aac2a-132">Toto omezení umožňuje vytvořit instanci parametru typu pomocí operátoru `new`.</span><span class="sxs-lookup"><span data-stu-id="aac2a-132">That constraint makes it possible to create an instance of a type parameter using the `new` operator.</span></span> <span data-ttu-id="aac2a-133">[Omezení New ()](new-constraint.md) umožňuje kompilátoru zjistit, že libovolný zadaný argument typu musí mít přístupný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="aac2a-133">The [new() Constraint](new-constraint.md) lets the compiler know that any type argument supplied must have an accessible parameterless constructor.</span></span> <span data-ttu-id="aac2a-134">Příklad:</span><span class="sxs-lookup"><span data-stu-id="aac2a-134">For example:</span></span>

[!code-csharp[using the new constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

<span data-ttu-id="aac2a-135">Omezení `new()` se v klauzuli `where` zobrazí jako poslední.</span><span class="sxs-lookup"><span data-stu-id="aac2a-135">The `new()` constraint appears last in the `where` clause.</span></span> <span data-ttu-id="aac2a-136">Omezení `new()` nelze kombinovat s omezeními `struct` nebo `unmanaged`.</span><span class="sxs-lookup"><span data-stu-id="aac2a-136">The `new()` constraint can't be combined with the `struct` or `unmanaged` constraints.</span></span> <span data-ttu-id="aac2a-137">Všechny typy, které by splňovaly tato omezení, musí mít přístupný konstruktor bez parametrů, aby omezení `new()` bylo redundantní.</span><span class="sxs-lookup"><span data-stu-id="aac2a-137">All types satisfying those constraints must have an accessible parameterless constructor, making the `new()` constraint redundant.</span></span>

<span data-ttu-id="aac2a-138">S více parametry typu použijte jednu klauzuli `where` pro každý parametr typu, například:</span><span class="sxs-lookup"><span data-stu-id="aac2a-138">With multiple type parameters, use one `where` clause for each type parameter, for example:</span></span>

[!code-csharp[using multiple where constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

<span data-ttu-id="aac2a-139">Omezení můžete také připojit k parametrům typu obecných metod, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="aac2a-139">You can also attach constraints to type parameters of generic methods, as shown in the following example:</span></span>

[!code-csharp[where constraints with generic methods](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

<span data-ttu-id="aac2a-140">Všimněte si, že syntaxe pro popis omezení parametrů typu na delegátech je stejná jako u metod:</span><span class="sxs-lookup"><span data-stu-id="aac2a-140">Notice that the syntax to describe type parameter constraints on delegates is the same as that of methods:</span></span>

[!code-csharp[where constraints with generic methods](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

<span data-ttu-id="aac2a-141">Informace o obecných delegátech najdete v tématu [Obecné delegáty](../../programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="aac2a-141">For information on generic delegates, see [Generic Delegates](../../programming-guide/generics/generic-delegates.md).</span></span>

<span data-ttu-id="aac2a-142">Podrobnosti o syntaxi a použití omezení naleznete v tématu [omezení u parametrů typu](../../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="aac2a-142">For details on the syntax and use of constraints, see [Constraints on Type Parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="aac2a-143">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="aac2a-143">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="aac2a-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aac2a-144">See also</span></span>

- [<span data-ttu-id="aac2a-145">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="aac2a-145">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="aac2a-146">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="aac2a-146">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="aac2a-147">Úvod do obecných typů</span><span class="sxs-lookup"><span data-stu-id="aac2a-147">Introduction to Generics</span></span>](../../programming-guide/generics/index.md)
- [<span data-ttu-id="aac2a-148">new – omezení</span><span class="sxs-lookup"><span data-stu-id="aac2a-148">new Constraint</span></span>](./new-constraint.md)
- [<span data-ttu-id="aac2a-149">Omezení parametrů typů</span><span class="sxs-lookup"><span data-stu-id="aac2a-149">Constraints on Type Parameters</span></span>](../../programming-guide/generics/constraints-on-type-parameters.md)
