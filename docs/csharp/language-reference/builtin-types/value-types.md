---
title: Typy hodnot – odkaz jazyka C#
ms.date: 01/22/2020
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 406e5b8bbe0802146a65bb4b9a053e753a7827ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399579"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="f26d3-102">Typy hodnot (odkaz C# )</span><span class="sxs-lookup"><span data-stu-id="f26d3-102">Value types (C# reference)</span></span>

<span data-ttu-id="f26d3-103">*Typy hodnot* a [typy odkazů](../keywords/reference-types.md) jsou dvě hlavní kategorie c# typy.</span><span class="sxs-lookup"><span data-stu-id="f26d3-103">*Value types* and [reference types](../keywords/reference-types.md) are the two main categories of C# types.</span></span> <span data-ttu-id="f26d3-104">Proměnná typu hodnoty obsahuje instanci typu.</span><span class="sxs-lookup"><span data-stu-id="f26d3-104">A variable of a value type contains an instance of the type.</span></span> <span data-ttu-id="f26d3-105">To se liší od proměnné typu odkazu, který obsahuje odkaz na instanci typu.</span><span class="sxs-lookup"><span data-stu-id="f26d3-105">This differs from a variable of a reference type, which contains a reference to an instance of the type.</span></span> <span data-ttu-id="f26d3-106">Ve výchozím nastavení se při [přiřazení](../operators/assignment-operator.md), předání argumentu metodě a vrácení výsledku metody zkopírují hodnoty proměnných.</span><span class="sxs-lookup"><span data-stu-id="f26d3-106">By default, on [assignment](../operators/assignment-operator.md), passing an argument to a method, and returning a method result, variable values are copied.</span></span> <span data-ttu-id="f26d3-107">V případě proměnných typu hodnoty se zkopírují odpovídající instance typu.</span><span class="sxs-lookup"><span data-stu-id="f26d3-107">In the case of value-type variables, the corresponding type instances are copied.</span></span> <span data-ttu-id="f26d3-108">Následující příklad ukazuje, že chování:</span><span class="sxs-lookup"><span data-stu-id="f26d3-108">The following example demonstrates that behavior:</span></span>

[!code-csharp[copy of values](snippets/ValueTypes.cs#ValueTypeCopied)]

<span data-ttu-id="f26d3-109">Jak ukazuje předchozí příklad, operace s proměnnou typu hodnoty ovlivňují pouze tuto instanci typu hodnoty uloženou v proměnné.</span><span class="sxs-lookup"><span data-stu-id="f26d3-109">As the preceding example shows, operations on a value-type variable affect only that instance of the value type, stored in the variable.</span></span>

<span data-ttu-id="f26d3-110">Pokud typ hodnoty obsahuje datový člen typu odkazu, zkopíruje se při kopírování instance typu hodnoty pouze odkaz na instanci typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="f26d3-110">If a value type contains a data member of a reference type, only the reference to the instance of the reference type is copied when a value-type instance is copied.</span></span> <span data-ttu-id="f26d3-111">Instance kopie i původní instance typu value mají přístup ke stejné instanci typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="f26d3-111">Both the copy and original value-type instance have access to the same reference-type instance.</span></span> <span data-ttu-id="f26d3-112">Následující příklad ukazuje, že chování:</span><span class="sxs-lookup"><span data-stu-id="f26d3-112">The following example demonstrates that behavior:</span></span>

[!code-csharp[shallow copy](snippets/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> <span data-ttu-id="f26d3-113">Chcete-li, aby váš kód byl méně náchylný k chybám a robustnější, definujte a používejte neměnné typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="f26d3-113">To make your code less error-prone and more robust, define and use immutable value types.</span></span> <span data-ttu-id="f26d3-114">Tento článek používá proměnlivé typy hodnot pouze pro demonstrační účely.</span><span class="sxs-lookup"><span data-stu-id="f26d3-114">This article uses mutable value types only for demonstration purposes.</span></span>

## <a name="kinds-of-value-types"></a><span data-ttu-id="f26d3-115">Druhy typů hodnot</span><span class="sxs-lookup"><span data-stu-id="f26d3-115">Kinds of value types</span></span>

<span data-ttu-id="f26d3-116">Typ hodnoty může být jeden ze dvou následujících typů:</span><span class="sxs-lookup"><span data-stu-id="f26d3-116">A value type can be one of the two following kinds:</span></span>

- <span data-ttu-id="f26d3-117">[typ struktury](struct.md), který zapouzdřuje data a související funkce</span><span class="sxs-lookup"><span data-stu-id="f26d3-117">a [structure type](struct.md), which encapsulates data and related functionality</span></span>
- <span data-ttu-id="f26d3-118">[typ výčtu](enum.md), který je definován sadou pojmenovaných konstant a představuje volbu nebo kombinaci voleb</span><span class="sxs-lookup"><span data-stu-id="f26d3-118">an [enumeration type](enum.md), which is defined by a set of named constants and represents a choice or a combination of choices</span></span>

<span data-ttu-id="f26d3-119">`T?` [Typ hodnoty s možnou hodnotou null](nullable-value-types.md) představuje všechny hodnoty jeho základního typu `T` hodnoty a další [hodnotu null.](../keywords/null.md)</span><span class="sxs-lookup"><span data-stu-id="f26d3-119">A [nullable value type](nullable-value-types.md) `T?` represents all values of its underlying value type `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="f26d3-120">Proměnné typu `null` hodnoty nelze přiřadit, pokud se nejedná o hodnotu s hodnotou s možnou hodnotou s hodnotou s možnou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="f26d3-120">You cannot assign `null` to a variable of a value type, unless it's a nullable value type.</span></span>

## <a name="built-in-value-types"></a><span data-ttu-id="f26d3-121">Předdefinované typy hodnot</span><span class="sxs-lookup"><span data-stu-id="f26d3-121">Built-in value types</span></span>

<span data-ttu-id="f26d3-122">C# poskytuje následující předdefinované typy hodnot, označované také jako *jednoduché typy*:</span><span class="sxs-lookup"><span data-stu-id="f26d3-122">C# provides the following built-in value types, also known as *simple types*:</span></span>

- [<span data-ttu-id="f26d3-123">Celočíselné typy</span><span class="sxs-lookup"><span data-stu-id="f26d3-123">Integral numeric types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="f26d3-124">Číselné typy s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="f26d3-124">Floating-point numeric types</span></span>](floating-point-numeric-types.md)
- <span data-ttu-id="f26d3-125">[bool,](bool.md) který představuje logickou hodnotu</span><span class="sxs-lookup"><span data-stu-id="f26d3-125">[bool](bool.md) that represents a Boolean value</span></span>
- <span data-ttu-id="f26d3-126">[znak,](char.md) který představuje znak Unicode UTF-16</span><span class="sxs-lookup"><span data-stu-id="f26d3-126">[char](char.md) that represents a Unicode UTF-16 character</span></span>

<span data-ttu-id="f26d3-127">Všechny jednoduché typy jsou typy struktur a liší se od jiných typů struktury v tom, že umožňují určité další operace:</span><span class="sxs-lookup"><span data-stu-id="f26d3-127">All simple types are structure types and differ from other structure types in that they permit certain additional operations:</span></span>

- <span data-ttu-id="f26d3-128">Literály můžete použít k zadání hodnoty jednoduchého typu.</span><span class="sxs-lookup"><span data-stu-id="f26d3-128">You can use literals to provide a value of a simple type.</span></span> <span data-ttu-id="f26d3-129">Například `'A'` je literál typu `char` `2001` a je literál `int`typu .</span><span class="sxs-lookup"><span data-stu-id="f26d3-129">For example, `'A'` is a literal of the type `char` and `2001` is a literal of the type `int`.</span></span>

- <span data-ttu-id="f26d3-130">Můžete deklarovat konstanty jednoduchých typů s [const](../keywords/const.md) klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="f26d3-130">You can declare constants of the simple types with the [const](../keywords/const.md) keyword.</span></span> <span data-ttu-id="f26d3-131">Není možné mít konstanty jiných typů struktur.</span><span class="sxs-lookup"><span data-stu-id="f26d3-131">It's not possible to have constants of other structure types.</span></span>

- <span data-ttu-id="f26d3-132">Konstantní výrazy, jejichž operandy jsou všechny konstanty jednoduchých typů, jsou vyhodnocovány v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="f26d3-132">Constant expressions, whose operands are all constants of the simple types, are evaluated at compile time.</span></span>

<span data-ttu-id="f26d3-133">Počínaje C# 7.0, C# podporuje [kolekce členů hodnot](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="f26d3-133">Beginning with C# 7.0, C# supports [value tuples](../../tuples.md).</span></span> <span data-ttu-id="f26d3-134">Řazená kolekce členů s hodnotou je typ hodnoty, ale ne jednoduchý typ.</span><span class="sxs-lookup"><span data-stu-id="f26d3-134">A value tuple is a value type, but not a simple type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f26d3-135">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f26d3-135">C# language specification</span></span>

<span data-ttu-id="f26d3-136">Další informace naleznete v následujících částech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="f26d3-136">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="f26d3-137">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="f26d3-137">Value types</span></span>](~/_csharplang/spec/types.md#value-types)
- [<span data-ttu-id="f26d3-138">Jednoduché typy</span><span class="sxs-lookup"><span data-stu-id="f26d3-138">Simple types</span></span>](~/_csharplang/spec/types.md#simple-types)
- [<span data-ttu-id="f26d3-139">Proměnné</span><span class="sxs-lookup"><span data-stu-id="f26d3-139">Variables</span></span>](~/_csharplang/spec/variables.md)

## <a name="see-also"></a><span data-ttu-id="f26d3-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="f26d3-140">See also</span></span>

- [<span data-ttu-id="f26d3-141">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="f26d3-141">C# reference</span></span>](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [<span data-ttu-id="f26d3-142">Referenční typy</span><span class="sxs-lookup"><span data-stu-id="f26d3-142">Reference types</span></span>](../keywords/reference-types.md)
