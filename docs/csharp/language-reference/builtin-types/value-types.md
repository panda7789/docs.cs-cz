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
ms.openlocfilehash: 76f4a3ed929e3ac8e3e6cc74158e75af7a6c8cf2
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77625944"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="61ecd-102">Typy hodnot (C# referenční)</span><span class="sxs-lookup"><span data-stu-id="61ecd-102">Value types (C# reference)</span></span>

<span data-ttu-id="61ecd-103">*Typy hodnot* a [odkazové typy](../keywords/reference-types.md) jsou dvě hlavní kategorie C# typů.</span><span class="sxs-lookup"><span data-stu-id="61ecd-103">*Value types* and [reference types](../keywords/reference-types.md) are the two main categories of C# types.</span></span> <span data-ttu-id="61ecd-104">Proměnná typu hodnoty obsahuje instanci typu.</span><span class="sxs-lookup"><span data-stu-id="61ecd-104">A variable of a value type contains an instance of the type.</span></span> <span data-ttu-id="61ecd-105">To se liší od proměnné typu odkazu, který obsahuje odkaz na instanci typu.</span><span class="sxs-lookup"><span data-stu-id="61ecd-105">This differs from a variable of a reference type, which contains a reference to an instance of the type.</span></span> <span data-ttu-id="61ecd-106">Ve výchozím nastavení, při [přiřazení](../operators/assignment-operator.md), předávání argumentu metodě a vrácení výsledku metody, jsou zkopírovány hodnoty proměnných.</span><span class="sxs-lookup"><span data-stu-id="61ecd-106">By default, on [assignment](../operators/assignment-operator.md), passing an argument to a method, and returning a method result, variable values are copied.</span></span> <span data-ttu-id="61ecd-107">V případě proměnných typu hodnoty jsou zkopírovány odpovídající instance typu.</span><span class="sxs-lookup"><span data-stu-id="61ecd-107">In the case of value-type variables, the corresponding type instances are copied.</span></span> <span data-ttu-id="61ecd-108">Následující příklad ukazuje toto chování:</span><span class="sxs-lookup"><span data-stu-id="61ecd-108">The following example demonstrates that behavior:</span></span>

[!code-csharp[copy of values](~/samples/csharp/language-reference/builtin-types/ValueTypes.cs#ValueTypeCopied)]

<span data-ttu-id="61ecd-109">Jak ukazuje předchozí příklad, operace s proměnnou typu hodnoty ovlivňují pouze tuto instanci typu hodnoty, která je uložena v proměnné.</span><span class="sxs-lookup"><span data-stu-id="61ecd-109">As the preceding example shows, operations on a value-type variable affect only that instance of the value type, stored in the variable.</span></span>

<span data-ttu-id="61ecd-110">Pokud typ hodnoty obsahuje datový člen typu odkazu, je při zkopírování instance typu hodnota zkopírován pouze odkaz na instanci typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="61ecd-110">If a value type contains a data member of a reference type, only the reference to the instance of the reference type is copied when a value-type instance is copied.</span></span> <span data-ttu-id="61ecd-111">Kopie i původní instance typu hodnoty mají přístup ke stejné instanci typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="61ecd-111">Both the copy and original value-type instance have access to the same reference-type instance.</span></span> <span data-ttu-id="61ecd-112">Následující příklad ukazuje toto chování:</span><span class="sxs-lookup"><span data-stu-id="61ecd-112">The following example demonstrates that behavior:</span></span>

[!code-csharp[shallow copy](~/samples/csharp/language-reference/builtin-types/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> <span data-ttu-id="61ecd-113">Aby byl kód méně odolnější a robustnější, definujte a používejte neměnné typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="61ecd-113">To make your code less error-prone and more robust, define and use immutable value types.</span></span> <span data-ttu-id="61ecd-114">Tento článek používá proměnlivé typy hodnot pouze pro demonstrační účely.</span><span class="sxs-lookup"><span data-stu-id="61ecd-114">This article uses mutable value types only for demonstration purposes.</span></span>

## <a name="kinds-of-value-types"></a><span data-ttu-id="61ecd-115">Druhy hodnotových typů</span><span class="sxs-lookup"><span data-stu-id="61ecd-115">Kinds of value types</span></span>

<span data-ttu-id="61ecd-116">Typ hodnoty může být jeden z těchto dvou typů:</span><span class="sxs-lookup"><span data-stu-id="61ecd-116">A value type can be one of the two following kinds:</span></span>

- <span data-ttu-id="61ecd-117">[typ struktury](struct.md), který zapouzdřuje data a související funkce</span><span class="sxs-lookup"><span data-stu-id="61ecd-117">a [structure type](struct.md), which encapsulates data and related functionality</span></span>
- <span data-ttu-id="61ecd-118">[typ výčtu](enum.md), který je definován sadou pojmenovaných konstant a představuje volbu nebo kombinaci voleb</span><span class="sxs-lookup"><span data-stu-id="61ecd-118">an [enumeration type](enum.md), which is defined by a set of named constants and represents a choice or a combination of choices</span></span>

<span data-ttu-id="61ecd-119">[Typ hodnoty s možnou hodnotou null](nullable-value-types.md) `T?` představuje všechny hodnoty svého základního typu hodnoty `T` a další hodnotu [null](../keywords/null.md) .</span><span class="sxs-lookup"><span data-stu-id="61ecd-119">A [nullable value type](nullable-value-types.md) `T?` represents all values of its underlying value type `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="61ecd-120">Nelze přiřadit `null` k proměnné typu hodnoty, pokud se nejedná o typ hodnoty s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="61ecd-120">You cannot assign `null` to a variable of a value type, unless it's a nullable value type.</span></span>

## <a name="built-in-value-types"></a><span data-ttu-id="61ecd-121">Předdefinované typy hodnot</span><span class="sxs-lookup"><span data-stu-id="61ecd-121">Built-in value types</span></span>

<span data-ttu-id="61ecd-122">C#poskytuje následující předdefinované typy hodnot, označované také jako *jednoduché typy*:</span><span class="sxs-lookup"><span data-stu-id="61ecd-122">C# provides the following built-in value types, also known as *simple types*:</span></span>

- [<span data-ttu-id="61ecd-123">Celočíselné číselné typy</span><span class="sxs-lookup"><span data-stu-id="61ecd-123">Integral numeric types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="61ecd-124">Číselné typy s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="61ecd-124">Floating-point numeric types</span></span>](floating-point-numeric-types.md)
- <span data-ttu-id="61ecd-125">[bool](bool.md) , která představuje logickou hodnotu</span><span class="sxs-lookup"><span data-stu-id="61ecd-125">[bool](bool.md) that represents a Boolean value</span></span>
- <span data-ttu-id="61ecd-126">[char](char.md) , který představuje znak Unicode UTF-16</span><span class="sxs-lookup"><span data-stu-id="61ecd-126">[char](char.md) that represents a Unicode UTF-16 character</span></span>

<span data-ttu-id="61ecd-127">Všechny jednoduché typy jsou struktury typy a liší se od jiných typů struktury v tom, že umožňují určité další operace:</span><span class="sxs-lookup"><span data-stu-id="61ecd-127">All simple types are structure types and differ from other structure types in that they permit certain additional operations:</span></span>

- <span data-ttu-id="61ecd-128">Můžete použít literály k poskytnutí hodnoty jednoduchého typu.</span><span class="sxs-lookup"><span data-stu-id="61ecd-128">You can use literals to provide a value of a simple type.</span></span> <span data-ttu-id="61ecd-129">Například `'A'` je literál typu `char` a `2001` je literál typu `int`.</span><span class="sxs-lookup"><span data-stu-id="61ecd-129">For example, `'A'` is a literal of the type `char` and `2001` is a literal of the type `int`.</span></span>

- <span data-ttu-id="61ecd-130">Můžete deklarovat konstanty jednoduchých typů pomocí klíčového slova [const](../keywords/const.md) .</span><span class="sxs-lookup"><span data-stu-id="61ecd-130">You can declare constants of the simple types with the [const](../keywords/const.md) keyword.</span></span> <span data-ttu-id="61ecd-131">Není možné mít konstanty jiných typů struktury.</span><span class="sxs-lookup"><span data-stu-id="61ecd-131">It's not possible to have constants of other structure types.</span></span>

- <span data-ttu-id="61ecd-132">Konstantní výrazy, jejichž operandy jsou všechny konstanty jednoduchých typů, jsou vyhodnocovány v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="61ecd-132">Constant expressions, whose operands are all constants of the simple types, are evaluated at compile time.</span></span>

<span data-ttu-id="61ecd-133">Počínaje C# 7,0 C# podporuje [Tuple hodnot](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="61ecd-133">Beginning with C# 7.0, C# supports [value tuples](../../tuples.md).</span></span> <span data-ttu-id="61ecd-134">Hodnota řazené kolekce členů je hodnotový typ, ale ne jednoduchý typ.</span><span class="sxs-lookup"><span data-stu-id="61ecd-134">A value tuple is a value type, but not a simple type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="61ecd-135">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="61ecd-135">C# language specification</span></span>

<span data-ttu-id="61ecd-136">Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="61ecd-136">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="61ecd-137">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="61ecd-137">Value types</span></span>](~/_csharplang/spec/types.md#value-types)
- [<span data-ttu-id="61ecd-138">Jednoduché typy</span><span class="sxs-lookup"><span data-stu-id="61ecd-138">Simple types</span></span>](~/_csharplang/spec/types.md#simple-types)
- [<span data-ttu-id="61ecd-139">Proměnné</span><span class="sxs-lookup"><span data-stu-id="61ecd-139">Variables</span></span>](~/_csharplang/spec/variables.md)

## <a name="see-also"></a><span data-ttu-id="61ecd-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="61ecd-140">See also</span></span>

- [<span data-ttu-id="61ecd-141">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="61ecd-141">C# reference</span></span>](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [<span data-ttu-id="61ecd-142">Typy odkazů</span><span class="sxs-lookup"><span data-stu-id="61ecd-142">Reference types</span></span>](../keywords/reference-types.md)
