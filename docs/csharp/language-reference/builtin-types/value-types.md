---
description: 'Seznamte se s typy hodnot, jejich druhy a integrovanými v jazyce C. #'
title: Hodnotové typy – reference jazyka C#
ms.date: 01/22/2020
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 7826e71fee235d32655ccfbc9060c3bbb48d76c5
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134767"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="a97f0-103">Typy hodnot (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="a97f0-103">Value types (C# reference)</span></span>

<span data-ttu-id="a97f0-104">*Typy hodnot* a [odkazové typy](../keywords/reference-types.md) jsou dvě hlavní kategorie typů C#.</span><span class="sxs-lookup"><span data-stu-id="a97f0-104">*Value types* and [reference types](../keywords/reference-types.md) are the two main categories of C# types.</span></span> <span data-ttu-id="a97f0-105">Proměnná typu hodnoty obsahuje instanci typu.</span><span class="sxs-lookup"><span data-stu-id="a97f0-105">A variable of a value type contains an instance of the type.</span></span> <span data-ttu-id="a97f0-106">To se liší od proměnné typu odkazu, který obsahuje odkaz na instanci typu.</span><span class="sxs-lookup"><span data-stu-id="a97f0-106">This differs from a variable of a reference type, which contains a reference to an instance of the type.</span></span> <span data-ttu-id="a97f0-107">Ve výchozím nastavení, při [přiřazení](../operators/assignment-operator.md), předávání argumentu metodě a vrácení výsledku metody, jsou zkopírovány hodnoty proměnných.</span><span class="sxs-lookup"><span data-stu-id="a97f0-107">By default, on [assignment](../operators/assignment-operator.md), passing an argument to a method, and returning a method result, variable values are copied.</span></span> <span data-ttu-id="a97f0-108">V případě proměnných typu hodnoty jsou zkopírovány odpovídající instance typu.</span><span class="sxs-lookup"><span data-stu-id="a97f0-108">In the case of value-type variables, the corresponding type instances are copied.</span></span> <span data-ttu-id="a97f0-109">Následující příklad ukazuje toto chování:</span><span class="sxs-lookup"><span data-stu-id="a97f0-109">The following example demonstrates that behavior:</span></span>

[!code-csharp[copy of values](snippets/ValueTypes.cs#ValueTypeCopied)]

<span data-ttu-id="a97f0-110">Jak ukazuje předchozí příklad, operace s proměnnou typu hodnoty ovlivňují pouze tuto instanci typu hodnoty, která je uložena v proměnné.</span><span class="sxs-lookup"><span data-stu-id="a97f0-110">As the preceding example shows, operations on a value-type variable affect only that instance of the value type, stored in the variable.</span></span>

<span data-ttu-id="a97f0-111">Pokud typ hodnoty obsahuje datový člen typu odkazu, je při zkopírování instance typu hodnota zkopírován pouze odkaz na instanci typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="a97f0-111">If a value type contains a data member of a reference type, only the reference to the instance of the reference type is copied when a value-type instance is copied.</span></span> <span data-ttu-id="a97f0-112">Kopie i původní instance typu hodnoty mají přístup ke stejné instanci typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="a97f0-112">Both the copy and original value-type instance have access to the same reference-type instance.</span></span> <span data-ttu-id="a97f0-113">Následující příklad ukazuje toto chování:</span><span class="sxs-lookup"><span data-stu-id="a97f0-113">The following example demonstrates that behavior:</span></span>

[!code-csharp[shallow copy](snippets/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> <span data-ttu-id="a97f0-114">Aby byl kód méně odolnější a robustnější, definujte a používejte neměnné typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="a97f0-114">To make your code less error-prone and more robust, define and use immutable value types.</span></span> <span data-ttu-id="a97f0-115">Tento článek používá proměnlivé typy hodnot pouze pro demonstrační účely.</span><span class="sxs-lookup"><span data-stu-id="a97f0-115">This article uses mutable value types only for demonstration purposes.</span></span>

## <a name="kinds-of-value-types"></a><span data-ttu-id="a97f0-116">Druhy hodnotových typů</span><span class="sxs-lookup"><span data-stu-id="a97f0-116">Kinds of value types</span></span>

<span data-ttu-id="a97f0-117">Typ hodnoty může být jeden z těchto dvou typů:</span><span class="sxs-lookup"><span data-stu-id="a97f0-117">A value type can be one of the two following kinds:</span></span>

- <span data-ttu-id="a97f0-118">[typ struktury](struct.md), který zapouzdřuje data a související funkce</span><span class="sxs-lookup"><span data-stu-id="a97f0-118">a [structure type](struct.md), which encapsulates data and related functionality</span></span>
- <span data-ttu-id="a97f0-119">[typ výčtu](enum.md), který je definován sadou pojmenovaných konstant a představuje volbu nebo kombinaci voleb</span><span class="sxs-lookup"><span data-stu-id="a97f0-119">an [enumeration type](enum.md), which is defined by a set of named constants and represents a choice or a combination of choices</span></span>

<span data-ttu-id="a97f0-120">[Typ hodnoty s možnou hodnotou](nullable-value-types.md) null `T?` reprezentuje všechny hodnoty svého základního typu hodnoty `T` a další hodnotu [null](../keywords/null.md) .</span><span class="sxs-lookup"><span data-stu-id="a97f0-120">A [nullable value type](nullable-value-types.md) `T?` represents all values of its underlying value type `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="a97f0-121">Nemůžete přiřadit `null` proměnné typu hodnoty, pokud se nejedná o typ hodnoty s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="a97f0-121">You cannot assign `null` to a variable of a value type, unless it's a nullable value type.</span></span>

## <a name="built-in-value-types"></a><span data-ttu-id="a97f0-122">Předdefinované typy hodnot</span><span class="sxs-lookup"><span data-stu-id="a97f0-122">Built-in value types</span></span>

<span data-ttu-id="a97f0-123">Jazyk C# poskytuje následující předdefinované typy hodnot, označované také jako *jednoduché typy*:</span><span class="sxs-lookup"><span data-stu-id="a97f0-123">C# provides the following built-in value types, also known as *simple types*:</span></span>

- [<span data-ttu-id="a97f0-124">Celočíselné typy</span><span class="sxs-lookup"><span data-stu-id="a97f0-124">Integral numeric types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="a97f0-125">Číselné typy s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="a97f0-125">Floating-point numeric types</span></span>](floating-point-numeric-types.md)
- <span data-ttu-id="a97f0-126">[bool](bool.md) , která představuje logickou hodnotu</span><span class="sxs-lookup"><span data-stu-id="a97f0-126">[bool](bool.md) that represents a Boolean value</span></span>
- <span data-ttu-id="a97f0-127">[char](char.md) , který představuje znak Unicode UTF-16</span><span class="sxs-lookup"><span data-stu-id="a97f0-127">[char](char.md) that represents a Unicode UTF-16 character</span></span>

<span data-ttu-id="a97f0-128">Všechny jednoduché typy jsou struktury typy a liší se od jiných typů struktury v tom, že umožňují určité další operace:</span><span class="sxs-lookup"><span data-stu-id="a97f0-128">All simple types are structure types and differ from other structure types in that they permit certain additional operations:</span></span>

- <span data-ttu-id="a97f0-129">Můžete použít literály k poskytnutí hodnoty jednoduchého typu.</span><span class="sxs-lookup"><span data-stu-id="a97f0-129">You can use literals to provide a value of a simple type.</span></span> <span data-ttu-id="a97f0-130">Například `'A'` je literál typu, který `char` `2001` je literálem typu `int` .</span><span class="sxs-lookup"><span data-stu-id="a97f0-130">For example, `'A'` is a literal of the type `char` and `2001` is a literal of the type `int`.</span></span>

- <span data-ttu-id="a97f0-131">Můžete deklarovat konstanty jednoduchých typů pomocí klíčového slova [const](../keywords/const.md) .</span><span class="sxs-lookup"><span data-stu-id="a97f0-131">You can declare constants of the simple types with the [const](../keywords/const.md) keyword.</span></span> <span data-ttu-id="a97f0-132">Není možné mít konstanty jiných typů struktury.</span><span class="sxs-lookup"><span data-stu-id="a97f0-132">It's not possible to have constants of other structure types.</span></span>

- <span data-ttu-id="a97f0-133">Konstantní výrazy, jejichž operandy jsou všechny konstanty jednoduchých typů, jsou vyhodnocovány v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="a97f0-133">Constant expressions, whose operands are all constants of the simple types, are evaluated at compile time.</span></span>

<span data-ttu-id="a97f0-134">Počínaje jazykem C# 7,0 podporuje C# [n-tice hodnot](value-tuples.md).</span><span class="sxs-lookup"><span data-stu-id="a97f0-134">Beginning with C# 7.0, C# supports [value tuples](value-tuples.md).</span></span> <span data-ttu-id="a97f0-135">Hodnota řazené kolekce členů je hodnotový typ, ale ne jednoduchý typ.</span><span class="sxs-lookup"><span data-stu-id="a97f0-135">A value tuple is a value type, but not a simple type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a97f0-136">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a97f0-136">C# language specification</span></span>

<span data-ttu-id="a97f0-137">Další informace naleznete v následujících oddílech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="a97f0-137">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="a97f0-138">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="a97f0-138">Value types</span></span>](~/_csharplang/spec/types.md#value-types)
- [<span data-ttu-id="a97f0-139">Jednoduché typy</span><span class="sxs-lookup"><span data-stu-id="a97f0-139">Simple types</span></span>](~/_csharplang/spec/types.md#simple-types)
- [<span data-ttu-id="a97f0-140">Proměnné</span><span class="sxs-lookup"><span data-stu-id="a97f0-140">Variables</span></span>](~/_csharplang/spec/variables.md)

## <a name="see-also"></a><span data-ttu-id="a97f0-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="a97f0-141">See also</span></span>

- [<span data-ttu-id="a97f0-142">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="a97f0-142">C# reference</span></span>](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [<span data-ttu-id="a97f0-143">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="a97f0-143">Reference types</span></span>](../keywords/reference-types.md)
