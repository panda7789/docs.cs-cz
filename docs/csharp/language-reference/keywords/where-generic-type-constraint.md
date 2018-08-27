---
title: where (omezení obecného typu) (Referenční dokumentace jazyka C#)
ms.date: 04/12/2018
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: 34246824fb8ff28e47ea424c78eca38e999a30b6
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42931873"
---
# <a name="where-generic-type-constraint-c-reference"></a><span data-ttu-id="2ef1e-102">where (omezení obecného typu) (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="2ef1e-102">where (generic type constraint) (C# Reference)</span></span>

<span data-ttu-id="2ef1e-103">`where` Klauzule v definici obecného určuje omezení na typy, které se používají jako argumenty pro parametry typu v obecného typu, metody, delegáta nebo místní funkce.</span><span class="sxs-lookup"><span data-stu-id="2ef1e-103">The `where` clause in a generic definition specifies constraints on the types that are used as arguments for type parameters in a generic type, method, delegate, or local function.</span></span> <span data-ttu-id="2ef1e-104">Omezení můžete určit základní třídy, rozhraní nebo vyžadují být typu odkaz, hodnota nebo nespravovaný typ obecného typu.</span><span class="sxs-lookup"><span data-stu-id="2ef1e-104">Constraints can specify interfaces, base classes, or require a generic type to be a reference, value or unmanaged type.</span></span> <span data-ttu-id="2ef1e-105">Kterou deklarují funkce, které musí mít argument typu.</span><span class="sxs-lookup"><span data-stu-id="2ef1e-105">They declare capabilities that the type argument must possess.</span></span>

<span data-ttu-id="2ef1e-106">Například je možné deklarovat obecná třída `MyGenericClass`, tak, aby parametr typu `T` implementuje <xref:System.IComparable%601> rozhraní:</span><span class="sxs-lookup"><span data-stu-id="2ef1e-106">For example, you can declare a generic class, `MyGenericClass`, such that the type parameter `T` implements the <xref:System.IComparable%601> interface:</span></span>

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> <span data-ttu-id="2ef1e-107">Další informace o where – klauzule ve výrazu dotazu naleznete v tématu [kde klauzule](where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="2ef1e-107">For more information on the where clause in a query expression, see [where clause](where-clause.md).</span></span>

<span data-ttu-id="2ef1e-108">`where` Klauzule může také obsahovat omezení základní třídy.</span><span class="sxs-lookup"><span data-stu-id="2ef1e-108">The `where` clause can also include a base class constraint.</span></span> <span data-ttu-id="2ef1e-109">Omezení základní třídy uvádí, že typ má být použit jako argument typu pro obecný typu má zadanou třídu jako základní třídu (nebo je, že základní třídy) má být použit jako argument typu pro obecný typu.</span><span class="sxs-lookup"><span data-stu-id="2ef1e-109">The base class constraint states that a type to be used as a type argument for that generic type has the specified class as a base class (or is that base class) to be used as a type argument for that generic type.</span></span> <span data-ttu-id="2ef1e-110">Pokud se používá k omezení základní třídy, musí být uvedena před všemi ostatními omezeními u tohoto parametru typu.</span><span class="sxs-lookup"><span data-stu-id="2ef1e-110">If the base class constraint is used, it must appear before any other constraints on that type parameter.</span></span> <span data-ttu-id="2ef1e-111">Některé typy nejsou povoleny jako základní třída omezení: <xref:System.Object>, <xref:System.Array>, a <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="2ef1e-111">Some types are disallowed as a base class constraint: <xref:System.Object>, <xref:System.Array>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="2ef1e-112">Před C# 7.3 <xref:System.Enum>, <xref:System.Delegate>, a <xref:System.MulticastDelegate> byly také povolena jako omezení základní třídy.</span><span class="sxs-lookup"><span data-stu-id="2ef1e-112">Prior to C# 7.3, <xref:System.Enum>, <xref:System.Delegate>, and <xref:System.MulticastDelegate> were also disallowed as base class constraints.</span></span> <span data-ttu-id="2ef1e-113">Následující příklad ukazuje typy, které teď můžou být specifikované jako základní třídu:</span><span class="sxs-lookup"><span data-stu-id="2ef1e-113">The following example shows the types that can now be specified as a base class:</span></span>

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

<span data-ttu-id="2ef1e-114">`where` Klauzule můžete určit, že je typem `class` nebo `struct`.</span><span class="sxs-lookup"><span data-stu-id="2ef1e-114">The `where` clause can specify that the type is a `class` or a `struct`.</span></span> <span data-ttu-id="2ef1e-115">`struct` Omezení eliminuje nutnost zadat omezení základní třídy `System.ValueType`.</span><span class="sxs-lookup"><span data-stu-id="2ef1e-115">The `struct` constraint removes the need to specify a base class constraint of `System.ValueType`.</span></span> <span data-ttu-id="2ef1e-116">`System.ValueType` Typ nelze použít jako omezení základní třídy.</span><span class="sxs-lookup"><span data-stu-id="2ef1e-116">The `System.ValueType` type may not be used as a base class constraint.</span></span> <span data-ttu-id="2ef1e-117">Následující příklad ukazuje, jak `class` a `struct` omezení:</span><span class="sxs-lookup"><span data-stu-id="2ef1e-117">The following example shows both the `class` and `struct` constraints:</span></span>

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

<span data-ttu-id="2ef1e-118">`where` Může také obsahovat klauzuli `unmanaged` omezení.</span><span class="sxs-lookup"><span data-stu-id="2ef1e-118">The `where` clause may also include an `unmanaged` constraint.</span></span> <span data-ttu-id="2ef1e-119">`unmanaged` Omezení omezuje parametr typu pro typy označované jako **nespravovaného typy**.</span><span class="sxs-lookup"><span data-stu-id="2ef1e-119">The `unmanaged` constraint limits the type parameter to types known as **unmanaged types**.</span></span> <span data-ttu-id="2ef1e-120">**Nespravovaný typ** je typ, který není typem odkazu a neobsahuje pole typu odkazu na libovolné úrovni vnoření.</span><span class="sxs-lookup"><span data-stu-id="2ef1e-120">An **unmanaged type** is a type that isn't a reference type and doesn't contain reference type fields at any level of nesting.</span></span> <span data-ttu-id="2ef1e-121">`unmanaged` Omezení usnadňuje psaní nízké úrovně vzájemné spolupráce kódu v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="2ef1e-121">The `unmanaged` constraint makes it easier to write low-level interop code in C#.</span></span> <span data-ttu-id="2ef1e-122">Toto omezení umožňuje opakovaně použitelných rutin do všech nespravovaných typů.</span><span class="sxs-lookup"><span data-stu-id="2ef1e-122">This constraint enables reusable routines across all unmanaged types.</span></span> <span data-ttu-id="2ef1e-123">`unmanaged` Omezení nelze kombinovat s `class` nebo `struct` omezení.</span><span class="sxs-lookup"><span data-stu-id="2ef1e-123">The `unmanaged` constraint can't be combined with the `class` or `struct` constraint.</span></span> <span data-ttu-id="2ef1e-124">`unmanaged` Vynucuje omezení, musí být typu `struct`:</span><span class="sxs-lookup"><span data-stu-id="2ef1e-124">The `unmanaged` constraint enforces that the type must be a `struct`:</span></span>

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

<span data-ttu-id="2ef1e-125">`where` Klauzule může také obsahovat omezení konstruktoru `new()`.</span><span class="sxs-lookup"><span data-stu-id="2ef1e-125">The `where` clause may also include a constructor constraint, `new()`.</span></span> <span data-ttu-id="2ef1e-126">Že omezení díky tomu je možné vytvořit instanci typu pomocí parametru `new` operátor.</span><span class="sxs-lookup"><span data-stu-id="2ef1e-126">That constraint makes it possible to create an instance of a type parameter using the `new` operator.</span></span> <span data-ttu-id="2ef1e-127">[Omezení new()](new-constraint.md) umožňuje kompilátoru vědět, že všechny zadaný argument typu musí mít k dispozici přístup bez parametrů--nebo--výchozí konstruktor.</span><span class="sxs-lookup"><span data-stu-id="2ef1e-127">The [new() Constraint](new-constraint.md) lets the compiler know that any type argument supplied must have an accessible parameterless--or default-- constructor.</span></span> <span data-ttu-id="2ef1e-128">Příklad:</span><span class="sxs-lookup"><span data-stu-id="2ef1e-128">For example:</span></span>

[!code-csharp[using the new constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

<span data-ttu-id="2ef1e-129">`new()` Omezení, zobrazí se v poslední `where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="2ef1e-129">The `new()` constraint appears last in the `where` clause.</span></span> <span data-ttu-id="2ef1e-130">`new()` Omezení nelze kombinovat s `struct` nebo `unmanaged` omezení.</span><span class="sxs-lookup"><span data-stu-id="2ef1e-130">The `new()` constraint can't be combined with the `struct` or `unmanaged` constraints.</span></span> <span data-ttu-id="2ef1e-131">Všechny typy splňující tato omezení musí mít dostupný konstruktor bez parametrů, takže `new()` omezení redundantní.</span><span class="sxs-lookup"><span data-stu-id="2ef1e-131">All types satisfying those constraints must have an accessible parameterless constructor, making the `new()` constraint redundant.</span></span>

<span data-ttu-id="2ef1e-132">S více typy parametrů, použijte jednu `where` klauzule pro každý z parametrů typu, například:</span><span class="sxs-lookup"><span data-stu-id="2ef1e-132">With multiple type parameters, use one `where` clause for each type parameter, for example:</span></span>

[!code-csharp[using multiple where constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

<span data-ttu-id="2ef1e-133">Můžete také připojit omezení k zadání parametrů Obecné metody, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="2ef1e-133">You can also attach constraints to type parameters of generic methods, as shown in the following example:</span></span>

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

<span data-ttu-id="2ef1e-134">Všimněte si, že syntaxe pro popis omezení parametru typu na delegáty je stejné jako u metod:</span><span class="sxs-lookup"><span data-stu-id="2ef1e-134">Notice that the syntax to describe type parameter constraints on delegates is the same as that of methods:</span></span>

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

<span data-ttu-id="2ef1e-135">Informace o obecných delegátů, naleznete v tématu [obecných delegátů](../../../csharp/programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="2ef1e-135">For information on generic delegates, see [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>

<span data-ttu-id="2ef1e-136">Podrobnosti o syntaxi a použití omezení najdete v tématu [omezení parametrů typů](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="2ef1e-136">For details on the syntax and use of constraints, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2ef1e-137">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2ef1e-137">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="2ef1e-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2ef1e-138">See also</span></span>

- [<span data-ttu-id="2ef1e-139">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2ef1e-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="2ef1e-140">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="2ef1e-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="2ef1e-141">Úvod do obecných typů</span><span class="sxs-lookup"><span data-stu-id="2ef1e-141">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
- [<span data-ttu-id="2ef1e-142">new – omezení</span><span class="sxs-lookup"><span data-stu-id="2ef1e-142">new Constraint</span></span>](../../../csharp/language-reference/keywords/new-constraint.md)  
- [<span data-ttu-id="2ef1e-143">Omezení parametrů typů</span><span class="sxs-lookup"><span data-stu-id="2ef1e-143">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
