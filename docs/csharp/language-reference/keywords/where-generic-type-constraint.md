---
title: where (omezení obecného typu) (Referenční dokumentace jazyka C#)
ms.date: 04/12/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 16be19e342016becd100e2c21434393c3f36f815
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="where-generic-type-constraint-c-reference"></a><span data-ttu-id="c5986-102">where (omezení obecného typu) (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c5986-102">where (generic type constraint) (C# Reference)</span></span>

<span data-ttu-id="c5986-103">`where` Klauzule v definici obecného určuje omezení typy, které se používají jako argumenty pro typ parametry obecného typu, metoda, delegát nebo místní funkce.</span><span class="sxs-lookup"><span data-stu-id="c5986-103">The `where` clause in a generic definition specifies constraints on the types that are used as arguments for type parameters in a generic type, method, delegate, or local function.</span></span> <span data-ttu-id="c5986-104">Omezení můžete určit rozhraní, základní třídy, nebo vyžadovat obecného typu odkaz, hodnota nebo nespravovaný typ.</span><span class="sxs-lookup"><span data-stu-id="c5986-104">Constraints can specify interfaces, base classes, or require a generic type to be a reference, value or unmanaged type.</span></span> <span data-ttu-id="c5986-105">Jejich deklarovat možnosti, které musí mít argument typu.</span><span class="sxs-lookup"><span data-stu-id="c5986-105">They declare capabilities that the type argument must possess.</span></span>

<span data-ttu-id="c5986-106">Můžou například deklarovat obecná třída `MyGenericClass`, tak, že parametr typu `T` implementuje <xref:System.IComparable%601> rozhraní:</span><span class="sxs-lookup"><span data-stu-id="c5986-106">For example, you can declare a generic class, `MyGenericClass`, such that the type parameter `T` implements the <xref:System.IComparable%601> interface:</span></span>

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> <span data-ttu-id="c5986-107">Další informace o where klauzule ve výrazu dotazu, najdete v části [kde klauzule](where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="c5986-107">For more information on the where clause in a query expression, see [where clause](where-clause.md).</span></span>

<span data-ttu-id="c5986-108">`where` Klauzule může také obsahovat omezení základní třídy.</span><span class="sxs-lookup"><span data-stu-id="c5986-108">The `where` clause can also include a base class constraint.</span></span> <span data-ttu-id="c5986-109">Základní třída omezení stavy, že typ má být použit jako typ argumentu pro tento obecný typ má jako základní třída pro zadanou třídu (nebo je, že základní třída) má být použit jako typ argumentu pro obecného typu.</span><span class="sxs-lookup"><span data-stu-id="c5986-109">The base class constraint states that a type to be used as a type argument for that generic type has the specified class as a base class (or is that base class) to be used as a type argument for that generic type.</span></span> <span data-ttu-id="c5986-110">Pokud se používá k omezení základní třídy, musí být před jiná omezení u tohoto typu parametru.</span><span class="sxs-lookup"><span data-stu-id="c5986-110">If the base class constraint is used, it must appear before any other constraints on that type parameter.</span></span> <span data-ttu-id="c5986-111">Některé typy nejsou povoleny jako základní třída omezení: <xref:System.Object>, <xref:System.Array>, a <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="c5986-111">Some types are disallowed as a base class constraint: <xref:System.Object>, <xref:System.Array>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="c5986-112">Před C# 7.3 <xref:System.Enum>, <xref:System.Delegate>, a <xref:System.MulticastDelegate> byly také nepovolené jako základní třída omezení.</span><span class="sxs-lookup"><span data-stu-id="c5986-112">Prior to C# 7.3, <xref:System.Enum>, <xref:System.Delegate>, and <xref:System.MulticastDelegate> were also disallowed as base class constraints.</span></span> <span data-ttu-id="c5986-113">Následující příklad ukazuje typy, které nyní je možné zadat jako základní třída:</span><span class="sxs-lookup"><span data-stu-id="c5986-113">The following example shows the types that can now be specified as a base class:</span></span>

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

<span data-ttu-id="c5986-114">`where` Klauzule můžete určit, zda je typ `class` nebo `struct`.</span><span class="sxs-lookup"><span data-stu-id="c5986-114">The `where` clause can specify that the type is a `class` or a `struct`.</span></span> <span data-ttu-id="c5986-115">`struct` Omezení eliminuje nutnost zadejte základní třídu omezení `System.ValueType`.</span><span class="sxs-lookup"><span data-stu-id="c5986-115">The `struct` constraint removes the need to specify a base class constraint of `System.ValueType`.</span></span> <span data-ttu-id="c5986-116">`System.ValueType` Typ nemusí použít jako základní třída omezení.</span><span class="sxs-lookup"><span data-stu-id="c5986-116">The `System.ValueType` type may not be used as a base class constraint.</span></span> <span data-ttu-id="c5986-117">Následující příklad ukazuje, jak `class` a `struct` omezení:</span><span class="sxs-lookup"><span data-stu-id="c5986-117">The following example shows both the `class` and `struct` constraints:</span></span>

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

<span data-ttu-id="c5986-118">`where` Klauzule může také zahrnovat `unmanaged` omezení.</span><span class="sxs-lookup"><span data-stu-id="c5986-118">The `where` clause may also include an `unmanaged` constraint.</span></span> <span data-ttu-id="c5986-119">`unmanaged` Omezení omezuje parametr typu pro typy, které jsou známé jako **nespravované typy**.</span><span class="sxs-lookup"><span data-stu-id="c5986-119">The `unmanaged` constraint limits the type parameter to types known as **unmanaged types**.</span></span> <span data-ttu-id="c5986-120">**Nespravované typu** je typ, který není typu odkazu a neobsahuje pole typu odkaz na libovolnou úroveň vnoření.</span><span class="sxs-lookup"><span data-stu-id="c5986-120">An **unmanaged type** is a type that isn't a reference type and doesn't contain reference type fields at any level of nesting.</span></span> <span data-ttu-id="c5986-121">`unmanaged` Omezení usnadňuje psaní nízké úrovně spolupráce kódu v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="c5986-121">The `unmanaged` constraint makes it easier to write low-level interop code in C#.</span></span> <span data-ttu-id="c5986-122">Toto omezení umožňuje opakovaně použitelné rutiny všech nespravované typů.</span><span class="sxs-lookup"><span data-stu-id="c5986-122">This constraint enables reusable routines across all unmanaged types.</span></span> <span data-ttu-id="c5986-123">`unmanaged` Omezení nelze kombinovat s `class` nebo `struct` omezení.</span><span class="sxs-lookup"><span data-stu-id="c5986-123">The `unmanaged` constraint can't be combined with the `class` or `struct` constraint.</span></span> <span data-ttu-id="c5986-124">`unmanaged` Vynucuje omezení, musí být typ `struct`:</span><span class="sxs-lookup"><span data-stu-id="c5986-124">The `unmanaged` constraint enforces that the type must be a `struct`:</span></span>

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

<span data-ttu-id="c5986-125">`where` Klauzule může také zahrnovat konstruktor omezení, `new()`.</span><span class="sxs-lookup"><span data-stu-id="c5986-125">The `where` clause may also include a constructor constraint, `new()`.</span></span> <span data-ttu-id="c5986-126">Aby omezení umožňuje vytvořit instanci typu parametr pomocí `new` operátor.</span><span class="sxs-lookup"><span data-stu-id="c5986-126">That constraint makes it possible to create an instance of a type parameter using the `new` operator.</span></span> <span data-ttu-id="c5986-127">[New() omezení](new-constraint.md) umožňuje kompilátoru vědět, že musí mít přístupné některý typ argument zadaný bez parametrů--nebo--výchozí konstruktor.</span><span class="sxs-lookup"><span data-stu-id="c5986-127">The [new() Constraint](new-constraint.md) lets the compiler know that any type argument supplied must have an accessible parameterless--or default-- constructor.</span></span> <span data-ttu-id="c5986-128">Příklad:</span><span class="sxs-lookup"><span data-stu-id="c5986-128">For example:</span></span>

[!code-csharp[using the new constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

<span data-ttu-id="c5986-129">`new()` Omezení, zobrazí se v poslední `where` klauzule.</span><span class="sxs-lookup"><span data-stu-id="c5986-129">The `new()` constraint appears last in the `where` clause.</span></span> <span data-ttu-id="c5986-130">`new()` Omezení nelze kombinovat s `struct` nebo `unmanaged` omezení.</span><span class="sxs-lookup"><span data-stu-id="c5986-130">The `new()` constraint can't be combined with the `struct` or `unmanaged` constraints.</span></span> <span data-ttu-id="c5986-131">Všechny typy, které splňují tato omezení musí mít k dostupný konstruktor bez parametrů, což `new()` redundantní omezení.</span><span class="sxs-lookup"><span data-stu-id="c5986-131">All types satisfying those constraints must have an accessible parameterless constructor, making the `new()` constraint redundant.</span></span>

<span data-ttu-id="c5986-132">S více typů parametrů, použijte jednu `where` klauzuli pro každý parametr typu, například:</span><span class="sxs-lookup"><span data-stu-id="c5986-132">With multiple type parameters, use one `where` clause for each type parameter, for example:</span></span>

[!code-csharp[using multiple where constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

<span data-ttu-id="c5986-133">Můžete také připojit omezení zadání parametrů Obecné metody, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c5986-133">You can also attach constraints to type parameters of generic methods, as shown in the following example:</span></span>

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

<span data-ttu-id="c5986-134">Všimněte si, že syntaxe pro popis typu parametru omezení delegáti je stejná jako u metody:</span><span class="sxs-lookup"><span data-stu-id="c5986-134">Notice that the syntax to describe type parameter constraints on delegates is the same as that of methods:</span></span>

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

<span data-ttu-id="c5986-135">Informace pro obecné delegáty najdete v tématu [obecní delegáti](../../../csharp/programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="c5986-135">For information on generic delegates, see [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>

<span data-ttu-id="c5986-136">Podrobnosti o syntaxi a použití omezení najdete v tématu [omezení parametrů typů](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="c5986-136">For details on the syntax and use of constraints, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c5986-137">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c5986-137">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c5986-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="c5986-138">See also</span></span>

 [<span data-ttu-id="c5986-139">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c5986-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c5986-140">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="c5986-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c5986-141">Úvod do obecných typů</span><span class="sxs-lookup"><span data-stu-id="c5986-141">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [<span data-ttu-id="c5986-142">new – omezení</span><span class="sxs-lookup"><span data-stu-id="c5986-142">new Constraint</span></span>](../../../csharp/language-reference/keywords/new-constraint.md)  
 [<span data-ttu-id="c5986-143">Omezení parametrů typů</span><span class="sxs-lookup"><span data-stu-id="c5986-143">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
