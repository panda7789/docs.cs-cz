---
title: Typy hodnot – C# referenční informace
ms.date: 01/22/2020
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: a2b9dce3b0ca5e66cfc0fbdbbf8f341abca0b636
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239726"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="4c97b-102">Typy hodnot (C# referenční)</span><span class="sxs-lookup"><span data-stu-id="4c97b-102">Value types (C# reference)</span></span>

<span data-ttu-id="4c97b-103">*Typy hodnot* a [odkazové typy](../keywords/reference-types.md) jsou dvě hlavní kategorie C# typů.</span><span class="sxs-lookup"><span data-stu-id="4c97b-103">*Value types* and [reference types](../keywords/reference-types.md) are the two main categories of C# types.</span></span> <span data-ttu-id="4c97b-104">Proměnná typu hodnoty obsahuje instanci typu.</span><span class="sxs-lookup"><span data-stu-id="4c97b-104">A variable of a value type contains an instance of the type.</span></span> <span data-ttu-id="4c97b-105">To se liší od proměnné typu odkazu, který obsahuje odkaz na instanci typu.</span><span class="sxs-lookup"><span data-stu-id="4c97b-105">This differs from a variable of a reference type, which contains a reference to an instance of the type.</span></span> <span data-ttu-id="4c97b-106">Ve výchozím nastavení, při [přiřazení](../operators/assignment-operator.md), předávání argumentu metodě a vrácení výsledku metody, jsou zkopírovány hodnoty proměnných.</span><span class="sxs-lookup"><span data-stu-id="4c97b-106">By default, on [assignment](../operators/assignment-operator.md), passing an argument to a method, and returning a method result, variable values are copied.</span></span> <span data-ttu-id="4c97b-107">V případě proměnných typu hodnoty jsou zkopírovány odpovídající instance typu.</span><span class="sxs-lookup"><span data-stu-id="4c97b-107">In the case of value-type variables, the corresponding type instances are copied.</span></span> <span data-ttu-id="4c97b-108">Následující příklad ukazuje toto chování:</span><span class="sxs-lookup"><span data-stu-id="4c97b-108">The following example demonstrates that behavior:</span></span>

[!code-csharp[copy of values](~/samples/snippets/csharp/language-reference/builtin-types/ValueTypes.cs#ValueTypeCopied)]

<span data-ttu-id="4c97b-109">Jak ukazuje předchozí příklad, operace s proměnnou typu hodnoty ovlivňují pouze tuto instanci typu hodnoty, která je uložena v proměnné.</span><span class="sxs-lookup"><span data-stu-id="4c97b-109">As the preceding example shows, operations on a value-type variable affect only that instance of the value type, stored in the variable.</span></span>

<span data-ttu-id="4c97b-110">Pokud typ hodnoty obsahuje datový člen typu odkazu, je při zkopírování instance typu hodnota zkopírován pouze odkaz na instanci typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="4c97b-110">If a value type contains a data member of a reference type, only the reference to the instance of the reference type is copied when a value-type instance is copied.</span></span> <span data-ttu-id="4c97b-111">Kopie i původní instance typu hodnoty mají přístup ke stejné instanci typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="4c97b-111">Both the copy and original value-type instance have access to the same reference-type instance.</span></span> <span data-ttu-id="4c97b-112">Následující příklad ukazuje toto chování:</span><span class="sxs-lookup"><span data-stu-id="4c97b-112">The following example demonstrates that behavior:</span></span>

[!code-csharp[shallow copy](~/samples/snippets/csharp/language-reference/builtin-types/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> <span data-ttu-id="4c97b-113">Aby byl kód méně odolnější a robustnější, definujte a používejte neměnné typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="4c97b-113">To make your code less error-prone and more robust, define and use immutable value types.</span></span> <span data-ttu-id="4c97b-114">Tento článek používá proměnlivé typy hodnot pouze pro demonstrační účely.</span><span class="sxs-lookup"><span data-stu-id="4c97b-114">This article uses mutable value types only for demonstration purposes.</span></span>

## <a name="kinds-of-value-types"></a><span data-ttu-id="4c97b-115">Druhy hodnotových typů</span><span class="sxs-lookup"><span data-stu-id="4c97b-115">Kinds of value types</span></span>

<span data-ttu-id="4c97b-116">Typ hodnoty může být jeden z těchto dvou typů:</span><span class="sxs-lookup"><span data-stu-id="4c97b-116">A value type can be one of the two following kinds:</span></span>

- <span data-ttu-id="4c97b-117">[typ struktury](struct.md), který zapouzdřuje data a související funkce</span><span class="sxs-lookup"><span data-stu-id="4c97b-117">a [structure type](struct.md), which encapsulates data and related functionality</span></span>
- <span data-ttu-id="4c97b-118">[typ výčtu](enum.md), který je definován sadou pojmenovaných konstant a představuje volbu nebo kombinaci voleb</span><span class="sxs-lookup"><span data-stu-id="4c97b-118">an [enumeration type](enum.md), which is defined by a set of named constants and represents a choice or a combination of choices</span></span>

<span data-ttu-id="4c97b-119">[Typ hodnoty s možnou hodnotou null](nullable-value-types.md) `T?` představuje všechny hodnoty svého základního typu hodnoty `T` a další hodnotu [null](../keywords/null.md) .</span><span class="sxs-lookup"><span data-stu-id="4c97b-119">A [nullable value type](nullable-value-types.md) `T?` represents all values of its underlying value type `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="4c97b-120">Nelze přiřadit `null` k proměnné typu hodnoty, pokud se nejedná o typ hodnoty s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="4c97b-120">You cannot assign `null` to a variable of a value type, unless it's a nullable value type.</span></span>

## <a name="built-in-value-types"></a><span data-ttu-id="4c97b-121">Předdefinované typy hodnot</span><span class="sxs-lookup"><span data-stu-id="4c97b-121">Built-in value types</span></span>

<span data-ttu-id="4c97b-122">C#poskytuje následující předdefinované typy hodnot, označované také jako *jednoduché typy*:</span><span class="sxs-lookup"><span data-stu-id="4c97b-122">C# provides the following built-in value types, also known as *simple types*:</span></span>

- [<span data-ttu-id="4c97b-123">Celočíselné číselné typy</span><span class="sxs-lookup"><span data-stu-id="4c97b-123">Integral numeric types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="4c97b-124">Číselné typy s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="4c97b-124">Floating-point numeric types</span></span>](floating-point-numeric-types.md)
- <span data-ttu-id="4c97b-125">[bool](bool.md) , která představuje logickou hodnotu</span><span class="sxs-lookup"><span data-stu-id="4c97b-125">[bool](bool.md) that represents a Boolean value</span></span>
- <span data-ttu-id="4c97b-126">[char](char.md) , který představuje znak Unicode UTF-16</span><span class="sxs-lookup"><span data-stu-id="4c97b-126">[char](char.md) that represents a Unicode UTF-16 character</span></span>

<span data-ttu-id="4c97b-127">Všechny jednoduché typy jsou struktury typy a liší se od jiných typů struktury v tom, že umožňují určité další operace:</span><span class="sxs-lookup"><span data-stu-id="4c97b-127">All simple types are structure types and differ from other structure types in that they permit certain additional operations:</span></span>

- <span data-ttu-id="4c97b-128">Můžete použít literály k poskytnutí hodnoty jednoduchého typu.</span><span class="sxs-lookup"><span data-stu-id="4c97b-128">You can use literals to provide a value of a simple type.</span></span> <span data-ttu-id="4c97b-129">Například `'A'` je literál typu `char` a `2001` je literál typu `int`.</span><span class="sxs-lookup"><span data-stu-id="4c97b-129">For example, `'A'` is a literal of the type `char` and `2001` is a literal of the type `int`.</span></span>

- <span data-ttu-id="4c97b-130">Můžete deklarovat konstanty jednoduchých typů pomocí klíčového slova [const](../keywords/const.md) .</span><span class="sxs-lookup"><span data-stu-id="4c97b-130">You can declare constants of the simple types with the [const](../keywords/const.md) keyword.</span></span> <span data-ttu-id="4c97b-131">Není možné mít konstanty jiných typů struktury.</span><span class="sxs-lookup"><span data-stu-id="4c97b-131">It's not possible to have constants of other structure types.</span></span>

- <span data-ttu-id="4c97b-132">Konstantní výrazy, jejichž operandy jsou všechny konstanty jednoduchých typů, jsou vyhodnocovány v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="4c97b-132">Constant expressions, whose operands are all constants of the simple types, are evaluated at compile time.</span></span>

<span data-ttu-id="4c97b-133">Počínaje C# 7,0 C# podporuje [Tuple hodnot](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="4c97b-133">Beginning with C# 7.0, C# supports [value tuples](../../tuples.md).</span></span> <span data-ttu-id="4c97b-134">Hodnota řazené kolekce členů je hodnotový typ, ale ne jednoduchý typ.</span><span class="sxs-lookup"><span data-stu-id="4c97b-134">A value tuple is a value type, but not a simple type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4c97b-135">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4c97b-135">C# language specification</span></span>

<span data-ttu-id="4c97b-136">Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="4c97b-136">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="4c97b-137">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="4c97b-137">Value types</span></span>](~/_csharplang/spec/types.md#value-types)
- [<span data-ttu-id="4c97b-138">Jednoduché typy</span><span class="sxs-lookup"><span data-stu-id="4c97b-138">Simple types</span></span>](~/_csharplang/spec/types.md#simple-types)
- [<span data-ttu-id="4c97b-139">Proměnné</span><span class="sxs-lookup"><span data-stu-id="4c97b-139">Variables</span></span>](~/_csharplang/spec/variables.md)

## <a name="see-also"></a><span data-ttu-id="4c97b-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="4c97b-140">See also</span></span>

- [<span data-ttu-id="4c97b-141">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="4c97b-141">C# reference</span></span>](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [<span data-ttu-id="4c97b-142">Typy odkazů</span><span class="sxs-lookup"><span data-stu-id="4c97b-142">Reference types</span></span>](../keywords/reference-types.md)
