---
title: Uživatelsky definované operátory převodu – C# referenční informace
description: Naučte se definovat vlastní implicitní a explicitní převody typu v C#.
ms.date: 07/09/2019
f1_keywords:
- explicit_CSharpKeyword
- implicit_CSharpKeyword
helpviewer_keywords:
- explicit keyword [C#]
- implicit keyword [C#]
- conversion operator [C#]
- user-defined conversion [C#]
ms.openlocfilehash: 379deb20243a13cc608cb7fe119b341065327c1e
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77450671"
---
# <a name="user-defined-conversion-operators-c-reference"></a><span data-ttu-id="c0065-103">Uživatelsky definované operátory převodu (C# referenční)</span><span class="sxs-lookup"><span data-stu-id="c0065-103">User-defined conversion operators (C# reference)</span></span>

<span data-ttu-id="c0065-104">Uživatelsky definovaný typ může definovat vlastní implicitní nebo explicitní převod z nebo na jiný typ.</span><span class="sxs-lookup"><span data-stu-id="c0065-104">A user-defined type can define a custom implicit or explicit conversion from or to another type.</span></span>

<span data-ttu-id="c0065-105">Implicitní převody nevyžadují, aby se vyvolala speciální syntaxe, která může nastat v různých situacích, například v přiřazení a volání metod.</span><span class="sxs-lookup"><span data-stu-id="c0065-105">Implicit conversions don't require special syntax to be invoked and can occur in a variety of situations, for example, in assignments and methods invocations.</span></span> <span data-ttu-id="c0065-106">Předdefinované C# implicitní převody jsou vždy úspěšné a nikdy nevyvolávají výjimku.</span><span class="sxs-lookup"><span data-stu-id="c0065-106">Predefined C# implicit conversions always succeed and never throw an exception.</span></span> <span data-ttu-id="c0065-107">Uživatelem definované implicitní převody by se měly chovat i tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="c0065-107">User-defined implicit conversions should behave in that way as well.</span></span> <span data-ttu-id="c0065-108">Pokud vlastní převod může vyvolat výjimku nebo ztratit informace, definujte ji jako explicitní převod.</span><span class="sxs-lookup"><span data-stu-id="c0065-108">If a custom conversion can throw an exception or lose information, define it as an explicit conversion.</span></span>

<span data-ttu-id="c0065-109">Uživatelem definované převody nejsou považovány za operátory [is](type-testing-and-cast.md#is-operator) a [as](type-testing-and-cast.md#as-operator) .</span><span class="sxs-lookup"><span data-stu-id="c0065-109">User-defined conversions are not considered by the [is](type-testing-and-cast.md#is-operator) and [as](type-testing-and-cast.md#as-operator) operators.</span></span> <span data-ttu-id="c0065-110">Použijte [operátor přetypování ()](type-testing-and-cast.md#cast-operator-) pro vyvolání uživatelem definovaného explicitního převodu.</span><span class="sxs-lookup"><span data-stu-id="c0065-110">Use the [cast operator ()](type-testing-and-cast.md#cast-operator-) to invoke a user-defined explicit conversion.</span></span>

<span data-ttu-id="c0065-111">Použijte klíčová slova `operator` a `implicit` nebo `explicit` k definování implicitního nebo explicitního převodu v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="c0065-111">Use the `operator` and `implicit` or `explicit` keywords to define an implicit or explicit conversion, respectively.</span></span> <span data-ttu-id="c0065-112">Typ, který definuje převod, musí být buď zdrojový typ, nebo cílový typ převodu.</span><span class="sxs-lookup"><span data-stu-id="c0065-112">The type that defines a conversion must be either a source type or a target type of that conversion.</span></span> <span data-ttu-id="c0065-113">Převod mezi dvěma uživatelsky definovanými typy lze definovat v jednom ze dvou typů.</span><span class="sxs-lookup"><span data-stu-id="c0065-113">A conversion between two user-defined types can be defined in either of the two types.</span></span>

<span data-ttu-id="c0065-114">Následující příklad ukazuje, jak definovat implicitní a explicitní převod:</span><span class="sxs-lookup"><span data-stu-id="c0065-114">The following example demonstrates how to define an implicit and explicit conversion:</span></span>

[!code-csharp[implicit an explicit conversions](~/samples/csharp/language-reference/operators/UserDefinedConversions.cs)]

<span data-ttu-id="c0065-115">Také použijte klíčové slovo `operator` k přetížení předdefinovaného C# operátoru.</span><span class="sxs-lookup"><span data-stu-id="c0065-115">You also use the `operator` keyword to overload a predefined C# operator.</span></span> <span data-ttu-id="c0065-116">Další informace naleznete v tématu [přetížení operátoru](operator-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="c0065-116">For more information, see [Operator overloading](operator-overloading.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c0065-117">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c0065-117">C# language specification</span></span>

<span data-ttu-id="c0065-118">Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="c0065-118">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="c0065-119">Operátory převodu</span><span class="sxs-lookup"><span data-stu-id="c0065-119">Conversion operators</span></span>](~/_csharplang/spec/classes.md#conversion-operators)
- [<span data-ttu-id="c0065-120">Uživatelem definované převody</span><span class="sxs-lookup"><span data-stu-id="c0065-120">User-defined conversions</span></span>](~/_csharplang/spec/conversions.md#user-defined-conversions)
- [<span data-ttu-id="c0065-121">Implicitní převody</span><span class="sxs-lookup"><span data-stu-id="c0065-121">Implicit conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-conversions)
- [<span data-ttu-id="c0065-122">Explicitní převody</span><span class="sxs-lookup"><span data-stu-id="c0065-122">Explicit conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-conversions)

## <a name="see-also"></a><span data-ttu-id="c0065-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="c0065-123">See also</span></span>

- [<span data-ttu-id="c0065-124">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="c0065-124">C# reference</span></span>](../index.md)
- [<span data-ttu-id="c0065-125">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c0065-125">C# operators</span></span>](index.md)
- [<span data-ttu-id="c0065-126">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="c0065-126">Operator overloading</span></span>](operator-overloading.md)
- [<span data-ttu-id="c0065-127">Operátory testování typů a přetypování</span><span class="sxs-lookup"><span data-stu-id="c0065-127">Type-testing and cast operators</span></span>](type-testing-and-cast.md)
- [<span data-ttu-id="c0065-128">Přetypování a převod typu</span><span class="sxs-lookup"><span data-stu-id="c0065-128">Casting and type conversion</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="c0065-129">Pokyny pro návrh – operátory převodu</span><span class="sxs-lookup"><span data-stu-id="c0065-129">Design guidelines - Conversion operators</span></span>](../../../standard/design-guidelines/operator-overloads.md#conversion-operators)
- [<span data-ttu-id="c0065-130">Zřetězené uživatelem definované explicitní převody vC#</span><span class="sxs-lookup"><span data-stu-id="c0065-130">Chained user-defined explicit conversions in C#</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/chained-user-defined-explicit-conversions-in-c)
