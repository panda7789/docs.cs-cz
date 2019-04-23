---
title: Hodnota typu – C# odkaz
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 5ff883e541c614832286b4027bc1574952f8fd3d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979908"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="4e6a4-102">Typy hodnot (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="4e6a4-102">Value types (C# Reference)</span></span>

<span data-ttu-id="4e6a4-103">Existují dva druhy typů hodnot:</span><span class="sxs-lookup"><span data-stu-id="4e6a4-103">There are two kinds of value types:</span></span>

- [<span data-ttu-id="4e6a4-104">Struktury</span><span class="sxs-lookup"><span data-stu-id="4e6a4-104">Structs</span></span>](struct.md)

- [<span data-ttu-id="4e6a4-105">Výčty</span><span class="sxs-lookup"><span data-stu-id="4e6a4-105">Enumerations</span></span>](enum.md)

## <a name="main-features-of-value-types"></a><span data-ttu-id="4e6a4-106">Hlavní funkce typů hodnot</span><span class="sxs-lookup"><span data-stu-id="4e6a4-106">Main features of value types</span></span>

<span data-ttu-id="4e6a4-107">Proměnné hodnotového typu obsahuje hodnotu typu.</span><span class="sxs-lookup"><span data-stu-id="4e6a4-107">A variable of a value type contains a value of the type.</span></span> <span data-ttu-id="4e6a4-108">Například proměnná `int` typ může obsahovat hodnotu `42`.</span><span class="sxs-lookup"><span data-stu-id="4e6a4-108">For example, a variable of the `int` type might contain the value `42`.</span></span> <span data-ttu-id="4e6a4-109">Tím se liší od proměnné typu odkazu, který obsahuje odkaz na instanci typu, označované také jako objekt.</span><span class="sxs-lookup"><span data-stu-id="4e6a4-109">This differs from a variable of a reference type, which contains a reference to an instance of the type, also known as an object.</span></span> <span data-ttu-id="4e6a4-110">Když přiřadí novou hodnotu do proměnné typu hodnoty, tato hodnota je zkopírována.</span><span class="sxs-lookup"><span data-stu-id="4e6a4-110">When you assign a new value to a variable of a value type, that value is copied.</span></span> <span data-ttu-id="4e6a4-111">Když se přiřadí novou hodnotu do proměnné typu odkazu, odkaz je zkopírován, nikoli samotného objektu.</span><span class="sxs-lookup"><span data-stu-id="4e6a4-111">When you assign a new value to a variable of a reference type, the reference is copied, not the object itself.</span></span>

<span data-ttu-id="4e6a4-112">Všechny hodnotové typy jsou implicitně odvozena z <xref:System.ValueType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4e6a4-112">All value types are derived implicitly from the <xref:System.ValueType?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="4e6a4-113">Na rozdíl od v případě typů odkazu nelze odvodit nový typ z typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4e6a4-113">Unlike with reference types, you cannot derive a new type from a value type.</span></span> <span data-ttu-id="4e6a4-114">Nicméně, jako jsou typy odkazů, struktury mohou implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4e6a4-114">However, like reference types, structs can implement interfaces.</span></span>

<span data-ttu-id="4e6a4-115">Hodnoty typových proměnných nesmí být `null` ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="4e6a4-115">Value type variables cannot be `null` by default.</span></span> <span data-ttu-id="4e6a4-116">Ale proměnné k odpovídající položce [typy připouštějící hodnotu Null](../../../csharp/programming-guide/nullable-types/index.md) může být `null`.</span><span class="sxs-lookup"><span data-stu-id="4e6a4-116">However, variables of the corresponding [nullable types](../../../csharp/programming-guide/nullable-types/index.md) can be `null`.</span></span>

<span data-ttu-id="4e6a4-117">Každý hodnotový typ má implicitní konstruktor bez parametrů, která inicializuje výchozí hodnota tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="4e6a4-117">Each value type has an implicit parameterless constructor that initializes the default value of that type.</span></span> <span data-ttu-id="4e6a4-118">Informace o výchozí hodnoty typů hodnot najdete v tématu [tabulka výchozích hodnot](default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="4e6a4-118">For information about default values of value types, see [Default values table](default-values-table.md).</span></span>

## <a name="simple-types"></a><span data-ttu-id="4e6a4-119">Jednoduché typy</span><span class="sxs-lookup"><span data-stu-id="4e6a4-119">Simple types</span></span>

<span data-ttu-id="4e6a4-120">*Jednoduché typy* představují sadu předdefinovaných struktury typy poskytované C# a zahrnuje následující typy:</span><span class="sxs-lookup"><span data-stu-id="4e6a4-120">The *simple types* are a set of predefined struct types provided by C# and comprise the following types:</span></span>

- <span data-ttu-id="4e6a4-121">[Integrální typy](integral-types-table.md): číselné typy celých čísel a [char](char.md) typu</span><span class="sxs-lookup"><span data-stu-id="4e6a4-121">[Integral types](integral-types-table.md): integer numeric types and the [char](char.md) type</span></span>
- [<span data-ttu-id="4e6a4-122">Typy s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="4e6a4-122">Floating-point types</span></span>](floating-point-types-table.md)
- [<span data-ttu-id="4e6a4-123">bool</span><span class="sxs-lookup"><span data-stu-id="4e6a4-123">bool</span></span>](bool.md)

<span data-ttu-id="4e6a4-124">Jednoduché typy jsou označeny pomocí klíčových slov, ale tato klíčová slova jsou pouze aliasy pro typy předdefinované struktury v <xref:System> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4e6a4-124">The simple types are identified through keywords, but these keywords are simply aliases for predefined struct types in the <xref:System> namespace.</span></span> <span data-ttu-id="4e6a4-125">Například [int](int.md) je alias pro <xref:System.Int32?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4e6a4-125">For example, [int](int.md) is an alias of <xref:System.Int32?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4e6a4-126">Úplný seznam aliasů naleznete v tématu [tabulka předdefinovaných typů](built-in-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="4e6a4-126">For a complete list of aliases, see [Built-in types table](built-in-types-table.md).</span></span>

<span data-ttu-id="4e6a4-127">Jednoduché typy liší od jiné typy struct, že umožňují některé další operace:</span><span class="sxs-lookup"><span data-stu-id="4e6a4-127">The simple types differ from other struct types in that they permit certain additional operations:</span></span>

- <span data-ttu-id="4e6a4-128">Jednoduché typy může být inicializována pomocí literálů.</span><span class="sxs-lookup"><span data-stu-id="4e6a4-128">Simple types can be initialized by using literals.</span></span> <span data-ttu-id="4e6a4-129">Například `'A'` je literál typu `char` a `2001` je literál typu `int`.</span><span class="sxs-lookup"><span data-stu-id="4e6a4-129">For example, `'A'` is a literal of the type `char` and `2001` is a literal of the type `int`.</span></span>

- <span data-ttu-id="4e6a4-130">Je možné deklarovat konstanty jednoduché typy s [const](const.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="4e6a4-130">You can declare constants of the simple types with the [const](const.md) keyword.</span></span> <span data-ttu-id="4e6a4-131">Není možné mít konstanty jiné typy struct.</span><span class="sxs-lookup"><span data-stu-id="4e6a4-131">It's not possible to have constants of other struct types.</span></span>

- <span data-ttu-id="4e6a4-132">Výrazy konstant, jehož operandy jsou všechny jednoduchý typ konstanty, jsou vyhodnocovány v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="4e6a4-132">Constant expressions, whose operands are all simple type constants, are evaluated at compile time.</span></span>

<span data-ttu-id="4e6a4-133">Další informace najdete v tématu [jednoduché typy](~/_csharplang/spec/types.md#simple-types) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="4e6a4-133">For more information, see the [Simple types](~/_csharplang/spec/types.md#simple-types) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="initializing-value-types"></a><span data-ttu-id="4e6a4-134">Inicializace typů hodnot</span><span class="sxs-lookup"><span data-stu-id="4e6a4-134">Initializing value types</span></span>

<span data-ttu-id="4e6a4-135">Lokální proměnné v jazyce C# musí být inicializován před jejich použití.</span><span class="sxs-lookup"><span data-stu-id="4e6a4-135">Local variables in C# must be initialized before they are used.</span></span> <span data-ttu-id="4e6a4-136">Například může prohlásit místní proměnné bez inicializace jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="4e6a4-136">For example, you might declare a local variable without initialization as in the following example:</span></span>

```csharp
int myInt;
```

<span data-ttu-id="4e6a4-137">Nelze ji použít předtím, než ji inicializovat.</span><span class="sxs-lookup"><span data-stu-id="4e6a4-137">You cannot use it before you initialize it.</span></span> <span data-ttu-id="4e6a4-138">Můžete inicializovat pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="4e6a4-138">You can initialize it using the following statement:</span></span>

```csharp
myInt = new int();  // Invoke parameterless constructor for int type.
```

<span data-ttu-id="4e6a4-139">Tento příkaz je ekvivalentem následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="4e6a4-139">This statement is equivalent to the following statement:</span></span>

```csharp
myInt = 0;         // Assign an initial value, 0 in this example.
```

<span data-ttu-id="4e6a4-140">Můžete samozřejmě máte deklaraci a inicializaci ve stejném příkazu jako v následujících příkladech:</span><span class="sxs-lookup"><span data-stu-id="4e6a4-140">You can, of course, have the declaration and the initialization in the same statement as in the following examples:</span></span>

```csharp
int myInt = new int();
```

<span data-ttu-id="4e6a4-141">– nebo –</span><span class="sxs-lookup"><span data-stu-id="4e6a4-141">–or–</span></span>

```csharp
int myInt = 0;
```

<span data-ttu-id="4e6a4-142">Použití [nové](new.md) operátor volá konstruktor určitého typu a přiřadí výchozí hodnotu proměnné.</span><span class="sxs-lookup"><span data-stu-id="4e6a4-142">Using the [new](new.md) operator calls the parameterless constructor of the specific type and assigns the default value to the variable.</span></span> <span data-ttu-id="4e6a4-143">V předchozím příkladu konstruktor bez parametrů přiřazena hodnota `0` k `myInt`.</span><span class="sxs-lookup"><span data-stu-id="4e6a4-143">In the preceding example, the parameterless constructor assigned the value `0` to `myInt`.</span></span> <span data-ttu-id="4e6a4-144">Další informace o hodnoty přiřazené voláním výchozí konstruktory, naleznete v tématu [tabulka výchozích hodnot](default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="4e6a4-144">For more information about values assigned by calling default constructors, see [Default values table](default-values-table.md).</span></span>

<span data-ttu-id="4e6a4-145">Pomocí uživatelem definované typy [nové](new.md) vyvolat konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="4e6a4-145">With user-defined types, use [new](new.md) to invoke the parameterless constructor.</span></span> <span data-ttu-id="4e6a4-146">Například následující příkaz volá konstruktor bez parametrů `Point` struktury:</span><span class="sxs-lookup"><span data-stu-id="4e6a4-146">For example, the following statement invokes the parameterless constructor of the `Point` struct:</span></span>

```csharp
Point p = new Point(); // Invoke parameterless constructor for the struct.
```

<span data-ttu-id="4e6a4-147">Po tomto volání struktury považuje je jednoznačně přiřazovat; To znamená všech jejích členů jsou inicializovány na výchozích hodnotách.</span><span class="sxs-lookup"><span data-stu-id="4e6a4-147">After this call, the struct is considered to be definitely assigned; that is, all its members are initialized to their default values.</span></span>

<span data-ttu-id="4e6a4-148">Další informace o `new` operátoru, naleznete v tématu [nové](new.md).</span><span class="sxs-lookup"><span data-stu-id="4e6a4-148">For more information about the `new` operator, see [new](new.md).</span></span>

<span data-ttu-id="4e6a4-149">Informace o formátování výstupu číselné typy najdete v tématu [tabulka formátování číselných výsledků](formatting-numeric-results-table.md).</span><span class="sxs-lookup"><span data-stu-id="4e6a4-149">For information about formatting the output of numeric types, see [Formatting numeric results table](formatting-numeric-results-table.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4e6a4-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4e6a4-150">See also</span></span>

- [<span data-ttu-id="4e6a4-151">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4e6a4-151">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4e6a4-152">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4e6a4-152">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4e6a4-153">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4e6a4-153">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="4e6a4-154">Typy</span><span class="sxs-lookup"><span data-stu-id="4e6a4-154">Types</span></span>](types.md)
- [<span data-ttu-id="4e6a4-155">Referenční tabulky pro typy</span><span class="sxs-lookup"><span data-stu-id="4e6a4-155">Reference tables for types</span></span>](reference-tables-for-types.md)
- [<span data-ttu-id="4e6a4-156">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="4e6a4-156">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="4e6a4-157">Typy s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="4e6a4-157">Nullable types</span></span>](../../programming-guide/nullable-types/index.md)