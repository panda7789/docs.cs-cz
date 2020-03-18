---
title: where (omezení obecného typu) - C# Reference
ms.date: 04/12/2018
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: d236420c5019f7529b729155b13df50807dc1dab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626708"
---
# <a name="where-generic-type-constraint-c-reference"></a><span data-ttu-id="8b1c7-102">where (omezení obecného typu) (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="8b1c7-102">where (generic type constraint) (C# Reference)</span></span>

<span data-ttu-id="8b1c7-103">Klauzule `where` v obecné definici určuje omezení typů, které se používají jako argumenty pro parametry typu v obecném typu, metodě, delegátovi nebo místní funkci.</span><span class="sxs-lookup"><span data-stu-id="8b1c7-103">The `where` clause in a generic definition specifies constraints on the types that are used as arguments for type parameters in a generic type, method, delegate, or local function.</span></span> <span data-ttu-id="8b1c7-104">Omezení můžete určit rozhraní, základní třídy nebo vyžadovat obecný typ, který má být odkaz, hodnota nebo nespravovaný typ.</span><span class="sxs-lookup"><span data-stu-id="8b1c7-104">Constraints can specify interfaces, base classes, or require a generic type to be a reference, value, or unmanaged type.</span></span> <span data-ttu-id="8b1c7-105">Deklarují schopnosti, které musí mít argument typu.</span><span class="sxs-lookup"><span data-stu-id="8b1c7-105">They declare capabilities that the type argument must possess.</span></span>

<span data-ttu-id="8b1c7-106">Můžete například deklarovat `MyGenericClass`obecnou třídu , `T` tak, <xref:System.IComparable%601> aby parametr type implementoval rozhraní:</span><span class="sxs-lookup"><span data-stu-id="8b1c7-106">For example, you can declare a generic class, `MyGenericClass`, such that the type parameter `T` implements the <xref:System.IComparable%601> interface:</span></span>

[!code-csharp[using an interface constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> <span data-ttu-id="8b1c7-107">Další informace o where klauzule ve výrazu dotazu naleznete v tématu [kde klauzule](where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="8b1c7-107">For more information on the where clause in a query expression, see [where clause](where-clause.md).</span></span>

<span data-ttu-id="8b1c7-108">Klauzule `where` může také obsahovat omezení základní třídy.</span><span class="sxs-lookup"><span data-stu-id="8b1c7-108">The `where` clause can also include a base class constraint.</span></span> <span data-ttu-id="8b1c7-109">Omezení základní třídy uvádí, že typ, který má být použit jako argument typu pro tento obecný typ, má zadanou třídu jako základní třídu (nebo je to základní třída), která má být použita jako argument typu pro tento obecný typ.</span><span class="sxs-lookup"><span data-stu-id="8b1c7-109">The base class constraint states that a type to be used as a type argument for that generic type has the specified class as a base class (or is that base class) to be used as a type argument for that generic type.</span></span> <span data-ttu-id="8b1c7-110">Pokud je použito omezení základní třídy, musí se zobrazit před ostatními omezeními tohoto parametru typu.</span><span class="sxs-lookup"><span data-stu-id="8b1c7-110">If the base class constraint is used, it must appear before any other constraints on that type parameter.</span></span> <span data-ttu-id="8b1c7-111">Některé typy jsou zakázány jako omezení <xref:System.Object> <xref:System.Array>základní <xref:System.ValueType>třídy: , a .</span><span class="sxs-lookup"><span data-stu-id="8b1c7-111">Some types are disallowed as a base class constraint: <xref:System.Object>, <xref:System.Array>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="8b1c7-112">Před C# 7.3 <xref:System.Enum> <xref:System.Delegate>, <xref:System.MulticastDelegate> , a byly také zakázány jako omezení základní třídy.</span><span class="sxs-lookup"><span data-stu-id="8b1c7-112">Prior to C# 7.3, <xref:System.Enum>, <xref:System.Delegate>, and <xref:System.MulticastDelegate> were also disallowed as base class constraints.</span></span> <span data-ttu-id="8b1c7-113">Následující příklad ukazuje typy, které lze nyní zadat jako základní třídu:</span><span class="sxs-lookup"><span data-stu-id="8b1c7-113">The following example shows the types that can now be specified as a base class:</span></span>

[!code-csharp[using an interface constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

<span data-ttu-id="8b1c7-114">Klauzule `where` může určit, že `class` typ `struct`je nebo nebo .</span><span class="sxs-lookup"><span data-stu-id="8b1c7-114">The `where` clause can specify that the type is a `class` or a `struct`.</span></span> <span data-ttu-id="8b1c7-115">Omezení `struct` odebere potřebu určit omezení základní `System.ValueType`třídy .</span><span class="sxs-lookup"><span data-stu-id="8b1c7-115">The `struct` constraint removes the need to specify a base class constraint of `System.ValueType`.</span></span> <span data-ttu-id="8b1c7-116">Typ `System.ValueType` nelze použít jako omezení základní třídy.</span><span class="sxs-lookup"><span data-stu-id="8b1c7-116">The `System.ValueType` type may not be used as a base class constraint.</span></span> <span data-ttu-id="8b1c7-117">Následující příklad ukazuje `class` omezení `struct` a omezení:</span><span class="sxs-lookup"><span data-stu-id="8b1c7-117">The following example shows both the `class` and `struct` constraints:</span></span>

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

<span data-ttu-id="8b1c7-118">Klauzule `where` může `notnull` obsahovat omezení.</span><span class="sxs-lookup"><span data-stu-id="8b1c7-118">The `where` clause may include the `notnull` constraint.</span></span> <span data-ttu-id="8b1c7-119">Omezení `notnull` omezuje parametr typu na typy s možnou nulou.</span><span class="sxs-lookup"><span data-stu-id="8b1c7-119">The `notnull` constraint limits the type parameter to non-nullable types.</span></span> <span data-ttu-id="8b1c7-120">Tento typ může být [typ hodnoty](../builtin-types/value-types.md) nebo typ odkazu s nemožnou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="8b1c7-120">That type may be a [value type](../builtin-types/value-types.md) or a non-nullable reference type.</span></span> <span data-ttu-id="8b1c7-121">Omezení `notnull` je k dispozici počínaje C# 8.0 pro kód zkompilovaný v [ `nullable enable` kontextu](../../nullable-references.md#nullable-contexts).</span><span class="sxs-lookup"><span data-stu-id="8b1c7-121">The `notnull` constraint is available starting in C# 8.0 for code compiled in a [`nullable enable` context](../../nullable-references.md#nullable-contexts).</span></span> <span data-ttu-id="8b1c7-122">Na rozdíl od jiných omezení, pokud `notnull` argument typu porušuje omezení, kompilátor vygeneruje upozornění namísto chyby.</span><span class="sxs-lookup"><span data-stu-id="8b1c7-122">Unlike other constraints, if a type argument violates the `notnull` constraint, the compiler generates a warning instead of an error.</span></span> <span data-ttu-id="8b1c7-123">Upozornění jsou generovány `nullable enable` pouze v kontextu.</span><span class="sxs-lookup"><span data-stu-id="8b1c7-123">Warnings are only generated in a `nullable enable` context.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8b1c7-124">Obecná deklarace, `notnull` které obsahují omezení lze použít v kontextu nevšímat neplatné, ale kompilátor nevynucuje omezení.</span><span class="sxs-lookup"><span data-stu-id="8b1c7-124">Generic declarations that include the `notnull` constraint can be used in a nullable oblivious context, but compiler does not enforce the constraint.</span></span>

[!code-csharp[using the nonnull constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#NotNull)]

<span data-ttu-id="8b1c7-125">Klauzule `where` může také `unmanaged` obsahovat omezení.</span><span class="sxs-lookup"><span data-stu-id="8b1c7-125">The `where` clause may also include an `unmanaged` constraint.</span></span> <span data-ttu-id="8b1c7-126">Omezení `unmanaged` omezuje parametr typu na typy známé jako [nespravované typy](../builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="8b1c7-126">The `unmanaged` constraint limits the type parameter to types known as [unmanaged types](../builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="8b1c7-127">Omezení `unmanaged` usnadňuje zápis kódu meziop nižší úrovně v c#.</span><span class="sxs-lookup"><span data-stu-id="8b1c7-127">The `unmanaged` constraint makes it easier to write low-level interop code in C#.</span></span> <span data-ttu-id="8b1c7-128">Toto omezení umožňuje opakovaně použitelné rutiny ve všech nespravovaných typech.</span><span class="sxs-lookup"><span data-stu-id="8b1c7-128">This constraint enables reusable routines across all unmanaged types.</span></span> <span data-ttu-id="8b1c7-129">Omezení `unmanaged` nelze kombinovat s omezení `class` nebo. `struct`</span><span class="sxs-lookup"><span data-stu-id="8b1c7-129">The `unmanaged` constraint can't be combined with the `class` or `struct` constraint.</span></span> <span data-ttu-id="8b1c7-130">Omezení `unmanaged` vynucuje, že `struct`typ musí být :</span><span class="sxs-lookup"><span data-stu-id="8b1c7-130">The `unmanaged` constraint enforces that the type must be a `struct`:</span></span>

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

<span data-ttu-id="8b1c7-131">Klauzule `where` může také obsahovat `new()`omezení konstruktoru , .</span><span class="sxs-lookup"><span data-stu-id="8b1c7-131">The `where` clause may also include a constructor constraint, `new()`.</span></span> <span data-ttu-id="8b1c7-132">Toto omezení umožňuje vytvořit instanci parametru `new` typu pomocí operátoru.</span><span class="sxs-lookup"><span data-stu-id="8b1c7-132">That constraint makes it possible to create an instance of a type parameter using the `new` operator.</span></span> <span data-ttu-id="8b1c7-133">[New() Constraint](new-constraint.md) umožňuje kompilátoru vědět, že jakýkoli argument typu zadaný musí mít přístupný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="8b1c7-133">The [new() Constraint](new-constraint.md) lets the compiler know that any type argument supplied must have an accessible parameterless constructor.</span></span> <span data-ttu-id="8b1c7-134">Například:</span><span class="sxs-lookup"><span data-stu-id="8b1c7-134">For example:</span></span>

[!code-csharp[using the new constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

<span data-ttu-id="8b1c7-135">Omezení `new()` se zobrazí `where` jako poslední v klauzuli.</span><span class="sxs-lookup"><span data-stu-id="8b1c7-135">The `new()` constraint appears last in the `where` clause.</span></span> <span data-ttu-id="8b1c7-136">Omezení `new()` nelze kombinovat s omezeními `struct` `unmanaged` nebo.</span><span class="sxs-lookup"><span data-stu-id="8b1c7-136">The `new()` constraint can't be combined with the `struct` or `unmanaged` constraints.</span></span> <span data-ttu-id="8b1c7-137">Všechny typy splňující tato omezení musí mít přístupný `new()` konstruktor bez parametrů, což je nadbytečné.</span><span class="sxs-lookup"><span data-stu-id="8b1c7-137">All types satisfying those constraints must have an accessible parameterless constructor, making the `new()` constraint redundant.</span></span>

<span data-ttu-id="8b1c7-138">S více parametry typu `where` použijte jednu klauzuli pro každý parametr typu, například:</span><span class="sxs-lookup"><span data-stu-id="8b1c7-138">With multiple type parameters, use one `where` clause for each type parameter, for example:</span></span>

[!code-csharp[using multiple where constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

<span data-ttu-id="8b1c7-139">Můžete také připojit omezení k parametrům typu obecných metod, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="8b1c7-139">You can also attach constraints to type parameters of generic methods, as shown in the following example:</span></span>

[!code-csharp[where constraints with generic methods](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

<span data-ttu-id="8b1c7-140">Všimněte si, že syntaxe k popisu omezení parametrů typu u delegátů je stejná jako syntaxe metod:</span><span class="sxs-lookup"><span data-stu-id="8b1c7-140">Notice that the syntax to describe type parameter constraints on delegates is the same as that of methods:</span></span>

[!code-csharp[where constraints with generic methods](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

<span data-ttu-id="8b1c7-141">Informace o obecných delegátech naleznete [v tématu Obecné delegáty](../../programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="8b1c7-141">For information on generic delegates, see [Generic Delegates](../../programming-guide/generics/generic-delegates.md).</span></span>

<span data-ttu-id="8b1c7-142">Podrobnosti o syntaxi a použití omezení naleznete v [tématu Omezení parametrů typu](../../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="8b1c7-142">For details on the syntax and use of constraints, see [Constraints on Type Parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8b1c7-143">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8b1c7-143">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="8b1c7-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="8b1c7-144">See also</span></span>

- [<span data-ttu-id="8b1c7-145">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8b1c7-145">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8b1c7-146">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8b1c7-146">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8b1c7-147">Úvod do obecných typů</span><span class="sxs-lookup"><span data-stu-id="8b1c7-147">Introduction to Generics</span></span>](../../programming-guide/generics/index.md)
- [<span data-ttu-id="8b1c7-148">nové omezení</span><span class="sxs-lookup"><span data-stu-id="8b1c7-148">new Constraint</span></span>](./new-constraint.md)
- [<span data-ttu-id="8b1c7-149">Omezení parametrů typů</span><span class="sxs-lookup"><span data-stu-id="8b1c7-149">Constraints on Type Parameters</span></span>](../../programming-guide/generics/constraints-on-type-parameters.md)
