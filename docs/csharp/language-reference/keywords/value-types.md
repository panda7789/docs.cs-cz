---
title: Typy hodnot – C# referenční informace
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 8703532ff8551e8bd42128eb9e8cdcf2afd9dad8
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739673"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="be37b-102">Typy hodnot (C# referenční)</span><span class="sxs-lookup"><span data-stu-id="be37b-102">Value types (C# Reference)</span></span>

<span data-ttu-id="be37b-103">Existují dva druhy typů hodnot:</span><span class="sxs-lookup"><span data-stu-id="be37b-103">There are two kinds of value types:</span></span>

- [<span data-ttu-id="be37b-104">Struktury</span><span class="sxs-lookup"><span data-stu-id="be37b-104">Structs</span></span>](struct.md)

- [<span data-ttu-id="be37b-105">Výčty</span><span class="sxs-lookup"><span data-stu-id="be37b-105">Enumerations</span></span>](enum.md)

## <a name="main-features-of-value-types"></a><span data-ttu-id="be37b-106">Hlavní funkce typů hodnot</span><span class="sxs-lookup"><span data-stu-id="be37b-106">Main features of value types</span></span>

<span data-ttu-id="be37b-107">Proměnná typu hodnoty obsahuje hodnotu typu.</span><span class="sxs-lookup"><span data-stu-id="be37b-107">A variable of a value type contains a value of the type.</span></span> <span data-ttu-id="be37b-108">Například proměnná typu `int` může obsahovat hodnotu `42`.</span><span class="sxs-lookup"><span data-stu-id="be37b-108">For example, a variable of the `int` type might contain the value `42`.</span></span> <span data-ttu-id="be37b-109">To se liší od proměnné typu odkazu, který obsahuje odkaz na instanci typu, označovanou také jako objekt.</span><span class="sxs-lookup"><span data-stu-id="be37b-109">This differs from a variable of a reference type, which contains a reference to an instance of the type, also known as an object.</span></span> <span data-ttu-id="be37b-110">Pokud přiřadíte novou hodnotu proměnné typu hodnoty, je tato hodnota zkopírována.</span><span class="sxs-lookup"><span data-stu-id="be37b-110">When you assign a new value to a variable of a value type, that value is copied.</span></span> <span data-ttu-id="be37b-111">Pokud přiřadíte novou hodnotu proměnné typu odkazu, je odkaz zkopírován, nikoli samotný objekt.</span><span class="sxs-lookup"><span data-stu-id="be37b-111">When you assign a new value to a variable of a reference type, the reference is copied, not the object itself.</span></span>

<span data-ttu-id="be37b-112">Všechny typy hodnot jsou implicitně odvozeny z <xref:System.ValueType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="be37b-112">All value types are derived implicitly from the <xref:System.ValueType?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="be37b-113">Na rozdíl od typů odkazů nemůžete odvodit nový typ z hodnotového typu.</span><span class="sxs-lookup"><span data-stu-id="be37b-113">Unlike with reference types, you cannot derive a new type from a value type.</span></span> <span data-ttu-id="be37b-114">Nicméně, podobně jako typy odkazů, struktury mohou implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="be37b-114">However, like reference types, structs can implement interfaces.</span></span>

<span data-ttu-id="be37b-115">Proměnné typu hodnoty nemohou být ve výchozím nastavení `null`.</span><span class="sxs-lookup"><span data-stu-id="be37b-115">Value type variables cannot be `null` by default.</span></span> <span data-ttu-id="be37b-116">Proměnné odpovídající [typy hodnot s možnou hodnotou null](../builtin-types/nullable-value-types.md) ale mohou být `null`.</span><span class="sxs-lookup"><span data-stu-id="be37b-116">However, variables of the corresponding [nullable value types](../builtin-types/nullable-value-types.md) can be `null`.</span></span>

<span data-ttu-id="be37b-117">Každý typ hodnoty má implicitní konstruktor bez parametrů, který inicializuje výchozí hodnotu tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="be37b-117">Each value type has an implicit parameterless constructor that initializes the default value of that type.</span></span> <span data-ttu-id="be37b-118">Informace o výchozích hodnotách hodnotových typů najdete v [tabulce s výchozími hodnotami](default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="be37b-118">For information about default values of value types, see [Default values table](default-values-table.md).</span></span>

## <a name="simple-types"></a><span data-ttu-id="be37b-119">Jednoduché typy</span><span class="sxs-lookup"><span data-stu-id="be37b-119">Simple types</span></span>

<span data-ttu-id="be37b-120">*Jednoduché typy* jsou množinou předdefinovaných typů struktury poskytovaných C# a tvořené následujícími typy:</span><span class="sxs-lookup"><span data-stu-id="be37b-120">The *simple types* are a set of predefined struct types provided by C# and comprise the following types:</span></span>

- <span data-ttu-id="be37b-121">[Integrální typy](../builtin-types/integral-numeric-types.md): číselné typy integer a typ [znaku](char.md)</span><span class="sxs-lookup"><span data-stu-id="be37b-121">[Integral types](../builtin-types/integral-numeric-types.md): integer numeric types and the [char](char.md) type</span></span>
- [<span data-ttu-id="be37b-122">Typy s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="be37b-122">Floating-point types</span></span>](../builtin-types/floating-point-numeric-types.md)
- [<span data-ttu-id="be37b-123">bool</span><span class="sxs-lookup"><span data-stu-id="be37b-123">bool</span></span>](bool.md)

<span data-ttu-id="be37b-124">Jednoduché typy jsou identifikovány pomocí klíčových slov, ale tato klíčová slova jsou jednoduše aliasy pro předdefinované typy struktury v oboru názvů <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="be37b-124">The simple types are identified through keywords, but these keywords are simply aliases for predefined struct types in the <xref:System> namespace.</span></span> <span data-ttu-id="be37b-125">Například [int](../builtin-types/integral-numeric-types.md) je alias <xref:System.Int32?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="be37b-125">For example, [int](../builtin-types/integral-numeric-types.md) is an alias of <xref:System.Int32?displayProperty=nameWithType>.</span></span> <span data-ttu-id="be37b-126">Úplný seznam aliasů najdete v tématu [tabulka předdefinovaných typů](built-in-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="be37b-126">For a complete list of aliases, see [Built-in types table](built-in-types-table.md).</span></span>

<span data-ttu-id="be37b-127">Jednoduché typy se liší od jiných typů struktury v tom, že umožňují určité další operace:</span><span class="sxs-lookup"><span data-stu-id="be37b-127">The simple types differ from other struct types in that they permit certain additional operations:</span></span>

- <span data-ttu-id="be37b-128">Jednoduché typy lze inicializovat pomocí literálů.</span><span class="sxs-lookup"><span data-stu-id="be37b-128">Simple types can be initialized by using literals.</span></span> <span data-ttu-id="be37b-129">Například `'A'` je literál typu `char` a `2001` je literál typu `int`.</span><span class="sxs-lookup"><span data-stu-id="be37b-129">For example, `'A'` is a literal of the type `char` and `2001` is a literal of the type `int`.</span></span>

- <span data-ttu-id="be37b-130">Můžete deklarovat konstanty jednoduchých typů pomocí klíčového slova [const](const.md) .</span><span class="sxs-lookup"><span data-stu-id="be37b-130">You can declare constants of the simple types with the [const](const.md) keyword.</span></span> <span data-ttu-id="be37b-131">Není možné mít konstanty jiných typů struktury.</span><span class="sxs-lookup"><span data-stu-id="be37b-131">It's not possible to have constants of other struct types.</span></span>

- <span data-ttu-id="be37b-132">Výrazy konstant, jejichž operandy jsou všechny jednoduché konstanty typu, jsou vyhodnocovány v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="be37b-132">Constant expressions, whose operands are all simple type constants, are evaluated at compile time.</span></span>

<span data-ttu-id="be37b-133">Další informace naleznete v části [jednoduché typy](~/_csharplang/spec/types.md#simple-types) [ C# specifikace jazyka](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="be37b-133">For more information, see the [Simple types](~/_csharplang/spec/types.md#simple-types) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="initializing-value-types"></a><span data-ttu-id="be37b-134">Inicializace typů hodnot</span><span class="sxs-lookup"><span data-stu-id="be37b-134">Initializing value types</span></span>

<span data-ttu-id="be37b-135">Místní proměnné v C# nástroji musí být před použitím inicializovány.</span><span class="sxs-lookup"><span data-stu-id="be37b-135">Local variables in C# must be initialized before they are used.</span></span> <span data-ttu-id="be37b-136">Například je možné deklarovat místní proměnnou bez inicializace jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="be37b-136">For example, you might declare a local variable without initialization as in the following example:</span></span>

```csharp
int myInt;
```

<span data-ttu-id="be37b-137">Nemůžete ho použít před inicializací.</span><span class="sxs-lookup"><span data-stu-id="be37b-137">You cannot use it before you initialize it.</span></span> <span data-ttu-id="be37b-138">Můžete ji inicializovat pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="be37b-138">You can initialize it using the following statement:</span></span>

```csharp
myInt = new int();  // Invoke parameterless constructor for int type.
```

<span data-ttu-id="be37b-139">Tento příkaz je ekvivalentní následujícímu příkazu:</span><span class="sxs-lookup"><span data-stu-id="be37b-139">This statement is equivalent to the following statement:</span></span>

```csharp
myInt = 0;         // Assign an initial value, 0 in this example.
```

<span data-ttu-id="be37b-140">Můžete samozřejmě mít deklaraci a inicializaci ve stejném příkazu jako v následujících příkladech:</span><span class="sxs-lookup"><span data-stu-id="be37b-140">You can, of course, have the declaration and the initialization in the same statement as in the following examples:</span></span>

```csharp
int myInt = new int();
```

<span data-ttu-id="be37b-141">ani</span><span class="sxs-lookup"><span data-stu-id="be37b-141">–or–</span></span>

```csharp
int myInt = 0;
```

<span data-ttu-id="be37b-142">Použití operátoru [New](../operators/new-operator.md) volá konstruktor bez parametrů konkrétního typu a přiřadí výchozí hodnotu proměnné.</span><span class="sxs-lookup"><span data-stu-id="be37b-142">Using the [new](../operators/new-operator.md) operator calls the parameterless constructor of the specific type and assigns the default value to the variable.</span></span> <span data-ttu-id="be37b-143">V předchozím příkladu konstruktor bez parametrů přiřadil hodnotu `0` k `myInt`.</span><span class="sxs-lookup"><span data-stu-id="be37b-143">In the preceding example, the parameterless constructor assigned the value `0` to `myInt`.</span></span> <span data-ttu-id="be37b-144">Další informace o hodnotách, které jsou přiřazeny voláním konstruktorů bez parametrů, naleznete v [tabulce Default Values](default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="be37b-144">For more information about values assigned by calling parameterless constructors, see [Default values table](default-values-table.md).</span></span>

<span data-ttu-id="be37b-145">S uživatelsky definovanými typy použijte [Nový](../operators/new-operator.md) k vyvolání konstruktoru bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="be37b-145">With user-defined types, use [new](../operators/new-operator.md) to invoke the parameterless constructor.</span></span> <span data-ttu-id="be37b-146">Například následující příkaz vyvolá konstruktor bez parametrů `Point` struktury:</span><span class="sxs-lookup"><span data-stu-id="be37b-146">For example, the following statement invokes the parameterless constructor of the `Point` struct:</span></span>

```csharp
var p = new Point(); // Invoke parameterless constructor for the struct.
```

<span data-ttu-id="be37b-147">Po tomto volání se struktura považuje za jednoznačně přiřazenou; To znamená, že všichni její členové jsou inicializováni na jejich výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="be37b-147">After this call, the struct is considered to be definitely assigned; that is, all its members are initialized to their default values.</span></span>

<span data-ttu-id="be37b-148">Další informace o operátoru `new` naleznete v tématu [New](../operators/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="be37b-148">For more information about the `new` operator, see [new](../operators/new-operator.md).</span></span>

<span data-ttu-id="be37b-149">Informace o formátování výstupu číselných typů najdete v tématu [formátování tabulky číselných výsledků](formatting-numeric-results-table.md).</span><span class="sxs-lookup"><span data-stu-id="be37b-149">For information about formatting the output of numeric types, see [Formatting numeric results table](formatting-numeric-results-table.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="be37b-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="be37b-150">See also</span></span>

- [<span data-ttu-id="be37b-151">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="be37b-151">C# reference</span></span>](../index.md)
- [<span data-ttu-id="be37b-152">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="be37b-152">C# keywords</span></span>](index.md)
- [<span data-ttu-id="be37b-153">Typy odkazů</span><span class="sxs-lookup"><span data-stu-id="be37b-153">Reference types</span></span>](reference-types.md)
- [<span data-ttu-id="be37b-154">Typy hodnot s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="be37b-154">Nullable value types</span></span>](../builtin-types/nullable-value-types.md)
