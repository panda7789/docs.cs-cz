---
title: Uživatelem definované operátory převodu – odkaz jazyka C#
description: Zjistěte, jak definovat vlastní implicitní a explicitní převody typů v c#.
ms.date: 07/09/2019
f1_keywords:
- explicit_CSharpKeyword
- implicit_CSharpKeyword
helpviewer_keywords:
- explicit keyword [C#]
- implicit keyword [C#]
- conversion operator [C#]
- user-defined conversion [C#]
ms.openlocfilehash: b59fc27be31f1a38e2a6c3cabd82598933b5ed53
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121408"
---
# <a name="user-defined-conversion-operators-c-reference"></a><span data-ttu-id="c8949-103">Uživatelem definované operátory převodu (odkaz C#</span><span class="sxs-lookup"><span data-stu-id="c8949-103">User-defined conversion operators (C# reference)</span></span>

<span data-ttu-id="c8949-104">Uživatelem definovaný typ může definovat vlastní implicitní nebo explicitní převod z nebo na jiný typ.</span><span class="sxs-lookup"><span data-stu-id="c8949-104">A user-defined type can define a custom implicit or explicit conversion from or to another type.</span></span>

<span data-ttu-id="c8949-105">Implicitní převody nevyžadují speciální syntaxi, která má být vyvolána a může dojít v různých situacích, například v přiřazení a volání metod.</span><span class="sxs-lookup"><span data-stu-id="c8949-105">Implicit conversions don't require special syntax to be invoked and can occur in a variety of situations, for example, in assignments and methods invocations.</span></span> <span data-ttu-id="c8949-106">Předdefinované c# implicitní převody vždy úspěšné a nikdy vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="c8949-106">Predefined C# implicit conversions always succeed and never throw an exception.</span></span> <span data-ttu-id="c8949-107">Uživatelem definované implicitní převody by se měly chovat také tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="c8949-107">User-defined implicit conversions should behave in that way as well.</span></span> <span data-ttu-id="c8949-108">Pokud vlastní převod může vyvolat výjimku nebo ztratit informace, definujte ji jako explicitní převod.</span><span class="sxs-lookup"><span data-stu-id="c8949-108">If a custom conversion can throw an exception or lose information, define it as an explicit conversion.</span></span>

<span data-ttu-id="c8949-109">Uživatelem definované převody nejsou považovány za [is](type-testing-and-cast.md#is-operator) a [jako](type-testing-and-cast.md#as-operator) operátory.</span><span class="sxs-lookup"><span data-stu-id="c8949-109">User-defined conversions are not considered by the [is](type-testing-and-cast.md#is-operator) and [as](type-testing-and-cast.md#as-operator) operators.</span></span> <span data-ttu-id="c8949-110">Výraz [přetypování](type-testing-and-cast.md#cast-expression) slouží k vyvolání uživatelem definovaného explicitního převodu.</span><span class="sxs-lookup"><span data-stu-id="c8949-110">Use a [cast expression](type-testing-and-cast.md#cast-expression) to invoke a user-defined explicit conversion.</span></span>

<span data-ttu-id="c8949-111">Pomocí `operator` klíčových slov a `implicit` nebo `explicit` definujte implicitní nebo explicitní převod.</span><span class="sxs-lookup"><span data-stu-id="c8949-111">Use the `operator` and `implicit` or `explicit` keywords to define an implicit or explicit conversion, respectively.</span></span> <span data-ttu-id="c8949-112">Typ, který definuje převod, musí být typ zdroje nebo cílový typ tohoto převodu.</span><span class="sxs-lookup"><span data-stu-id="c8949-112">The type that defines a conversion must be either a source type or a target type of that conversion.</span></span> <span data-ttu-id="c8949-113">Převod mezi dvěma uživatelem definovanými typy lze definovat v jednom z těchto dvou typů.</span><span class="sxs-lookup"><span data-stu-id="c8949-113">A conversion between two user-defined types can be defined in either of the two types.</span></span>

<span data-ttu-id="c8949-114">Následující příklad ukazuje, jak definovat implicitní a explicitní převod:</span><span class="sxs-lookup"><span data-stu-id="c8949-114">The following example demonstrates how to define an implicit and explicit conversion:</span></span>

[!code-csharp[implicit an explicit conversions](snippets/UserDefinedConversions.cs)]

<span data-ttu-id="c8949-115">Můžete také `operator` použít klíčové slovo přetížení předdefinované c# operátor.</span><span class="sxs-lookup"><span data-stu-id="c8949-115">You also use the `operator` keyword to overload a predefined C# operator.</span></span> <span data-ttu-id="c8949-116">Další informace naleznete v tématu [Operator přetížení](operator-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="c8949-116">For more information, see [Operator overloading](operator-overloading.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c8949-117">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c8949-117">C# language specification</span></span>

<span data-ttu-id="c8949-118">Další informace naleznete v následujících částech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="c8949-118">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="c8949-119">Operátory převodu</span><span class="sxs-lookup"><span data-stu-id="c8949-119">Conversion operators</span></span>](~/_csharplang/spec/classes.md#conversion-operators)
- [<span data-ttu-id="c8949-120">Uživatelem definované převody</span><span class="sxs-lookup"><span data-stu-id="c8949-120">User-defined conversions</span></span>](~/_csharplang/spec/conversions.md#user-defined-conversions)
- [<span data-ttu-id="c8949-121">Implicitní převody</span><span class="sxs-lookup"><span data-stu-id="c8949-121">Implicit conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-conversions)
- [<span data-ttu-id="c8949-122">Explicitní převody</span><span class="sxs-lookup"><span data-stu-id="c8949-122">Explicit conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-conversions)

## <a name="see-also"></a><span data-ttu-id="c8949-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="c8949-123">See also</span></span>

- [<span data-ttu-id="c8949-124">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="c8949-124">C# reference</span></span>](../index.md)
- [<span data-ttu-id="c8949-125">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c8949-125">C# operators</span></span>](index.md)
- [<span data-ttu-id="c8949-126">Přetěžování operátoru</span><span class="sxs-lookup"><span data-stu-id="c8949-126">Operator overloading</span></span>](operator-overloading.md)
- [<span data-ttu-id="c8949-127">Operátory pro testování typů a přetypování</span><span class="sxs-lookup"><span data-stu-id="c8949-127">Type-testing and cast operators</span></span>](type-testing-and-cast.md)
- [<span data-ttu-id="c8949-128">Převod odlitků a typů</span><span class="sxs-lookup"><span data-stu-id="c8949-128">Casting and type conversion</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="c8949-129">Pokyny pro návrh - Operátory konverzí</span><span class="sxs-lookup"><span data-stu-id="c8949-129">Design guidelines - Conversion operators</span></span>](../../../standard/design-guidelines/operator-overloads.md#conversion-operators)
- [<span data-ttu-id="c8949-130">Zřetězené uživatelem definované explicitní převody v C #</span><span class="sxs-lookup"><span data-stu-id="c8949-130">Chained user-defined explicit conversions in C#</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/chained-user-defined-explicit-conversions-in-c)
