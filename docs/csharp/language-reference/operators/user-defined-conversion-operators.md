---
title: Uživatelsky definované operátory převodu – reference jazyka C#
description: Naučte se definovat vlastní implicitní a explicitní převody typů v jazyce C#.
ms.date: 07/09/2019
f1_keywords:
- explicit_CSharpKeyword
- implicit_CSharpKeyword
- explicit
- implicit
helpviewer_keywords:
- explicit keyword [C#]
- implicit keyword [C#]
- conversion operator [C#]
- user-defined conversion [C#]
ms.openlocfilehash: a0eb11d55ad9e9cccde1704ba4c5ae8acb609989
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916631"
---
# <a name="user-defined-conversion-operators-c-reference"></a><span data-ttu-id="e8e60-103">Uživatelsky definované operátory převodu (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e8e60-103">User-defined conversion operators (C# reference)</span></span>

<span data-ttu-id="e8e60-104">Uživatelsky definovaný typ může definovat vlastní implicitní nebo explicitní převod z nebo na jiný typ.</span><span class="sxs-lookup"><span data-stu-id="e8e60-104">A user-defined type can define a custom implicit or explicit conversion from or to another type.</span></span>

<span data-ttu-id="e8e60-105">Implicitní převody nevyžadují, aby se vyvolala speciální syntaxe, která může nastat v různých situacích, například v přiřazení a volání metod.</span><span class="sxs-lookup"><span data-stu-id="e8e60-105">Implicit conversions don't require special syntax to be invoked and can occur in a variety of situations, for example, in assignments and methods invocations.</span></span> <span data-ttu-id="e8e60-106">Předdefinované implicitní převody jazyka C# jsou vždy úspěšné a nikdy nevyvolávají výjimku.</span><span class="sxs-lookup"><span data-stu-id="e8e60-106">Predefined C# implicit conversions always succeed and never throw an exception.</span></span> <span data-ttu-id="e8e60-107">Uživatelem definované implicitní převody by se měly chovat i tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="e8e60-107">User-defined implicit conversions should behave in that way as well.</span></span> <span data-ttu-id="e8e60-108">Pokud vlastní převod může vyvolat výjimku nebo ztratit informace, definujte ji jako explicitní převod.</span><span class="sxs-lookup"><span data-stu-id="e8e60-108">If a custom conversion can throw an exception or lose information, define it as an explicit conversion.</span></span>

<span data-ttu-id="e8e60-109">Uživatelem definované převody nejsou považovány za operátory [is](type-testing-and-cast.md#is-operator) a [as](type-testing-and-cast.md#as-operator) .</span><span class="sxs-lookup"><span data-stu-id="e8e60-109">User-defined conversions are not considered by the [is](type-testing-and-cast.md#is-operator) and [as](type-testing-and-cast.md#as-operator) operators.</span></span> <span data-ttu-id="e8e60-110">Použijte [výraz přetypování](type-testing-and-cast.md#cast-expression) k vyvolání uživatelem definovaného explicitního převodu.</span><span class="sxs-lookup"><span data-stu-id="e8e60-110">Use a [cast expression](type-testing-and-cast.md#cast-expression) to invoke a user-defined explicit conversion.</span></span>

<span data-ttu-id="e8e60-111">Použijte `operator` `implicit` `explicit` klíčová slova a nebo pro definování implicitního nebo explicitního převodu v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="e8e60-111">Use the `operator` and `implicit` or `explicit` keywords to define an implicit or explicit conversion, respectively.</span></span> <span data-ttu-id="e8e60-112">Typ, který definuje převod, musí být buď zdrojový typ, nebo cílový typ převodu.</span><span class="sxs-lookup"><span data-stu-id="e8e60-112">The type that defines a conversion must be either a source type or a target type of that conversion.</span></span> <span data-ttu-id="e8e60-113">Převod mezi dvěma uživatelsky definovanými typy lze definovat v jednom ze dvou typů.</span><span class="sxs-lookup"><span data-stu-id="e8e60-113">A conversion between two user-defined types can be defined in either of the two types.</span></span>

<span data-ttu-id="e8e60-114">Následující příklad ukazuje, jak definovat implicitní a explicitní převod:</span><span class="sxs-lookup"><span data-stu-id="e8e60-114">The following example demonstrates how to define an implicit and explicit conversion:</span></span>

[!code-csharp[implicit an explicit conversions](snippets/shared/UserDefinedConversions.cs)]

<span data-ttu-id="e8e60-115">Klíčové slovo lze použít také `operator` k přetížení předdefinovaného operátoru jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="e8e60-115">You also use the `operator` keyword to overload a predefined C# operator.</span></span> <span data-ttu-id="e8e60-116">Další informace naleznete v tématu [přetížení operátoru](operator-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="e8e60-116">For more information, see [Operator overloading](operator-overloading.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e8e60-117">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e8e60-117">C# language specification</span></span>

<span data-ttu-id="e8e60-118">Další informace naleznete v následujících oddílech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="e8e60-118">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="e8e60-119">Operátory převodu</span><span class="sxs-lookup"><span data-stu-id="e8e60-119">Conversion operators</span></span>](~/_csharplang/spec/classes.md#conversion-operators)
- [<span data-ttu-id="e8e60-120">Uživatelem definované převody</span><span class="sxs-lookup"><span data-stu-id="e8e60-120">User-defined conversions</span></span>](~/_csharplang/spec/conversions.md#user-defined-conversions)
- [<span data-ttu-id="e8e60-121">Implicitní převody</span><span class="sxs-lookup"><span data-stu-id="e8e60-121">Implicit conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-conversions)
- [<span data-ttu-id="e8e60-122">Explicitní převody</span><span class="sxs-lookup"><span data-stu-id="e8e60-122">Explicit conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-conversions)

## <a name="see-also"></a><span data-ttu-id="e8e60-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="e8e60-123">See also</span></span>

- [<span data-ttu-id="e8e60-124">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="e8e60-124">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e8e60-125">Operátory a výrazy v C#</span><span class="sxs-lookup"><span data-stu-id="e8e60-125">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="e8e60-126">Přetěžování operátoru</span><span class="sxs-lookup"><span data-stu-id="e8e60-126">Operator overloading</span></span>](operator-overloading.md)
- [<span data-ttu-id="e8e60-127">Operátory pro testování typů a přetypování</span><span class="sxs-lookup"><span data-stu-id="e8e60-127">Type-testing and cast operators</span></span>](type-testing-and-cast.md)
- [<span data-ttu-id="e8e60-128">Přetypování a převod typu</span><span class="sxs-lookup"><span data-stu-id="e8e60-128">Casting and type conversion</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="e8e60-129">Pokyny pro návrh – operátory převodu</span><span class="sxs-lookup"><span data-stu-id="e8e60-129">Design guidelines - Conversion operators</span></span>](../../../standard/design-guidelines/operator-overloads.md#conversion-operators)
- [<span data-ttu-id="e8e60-130">Zřetězené uživatelem definované explicitní převody v jazyce C #</span><span class="sxs-lookup"><span data-stu-id="e8e60-130">Chained user-defined explicit conversions in C#</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/chained-user-defined-explicit-conversions-in-c)
