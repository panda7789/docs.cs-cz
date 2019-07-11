---
title: Uživatelem definovaný převod operators – C# odkaz
description: Další informace o definování vlastního typu implicitní a explicitní převody v C#.
ms.date: 07/09/2019
f1_keywords:
- explicit_CSharpKeyword
- implicit_CSharpKeyword
helpviewer_keywords:
- explicit keyword [C#]
- implicit keyword [C#]
- conversion operator [C#]
- user-defined conversion [C#]
ms.openlocfilehash: 5d1882048b2af12c29a3771055cbeba9565b7dab
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67788498"
---
# <a name="user-defined-conversion-operators-c-reference"></a><span data-ttu-id="d2b77-103">Uživatelem definovaný převod operátorů (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="d2b77-103">User-defined conversion operators (C# reference)</span></span>

<span data-ttu-id="d2b77-104">Uživatelem definovaný typ, můžete definovat vlastní explicitní nebo implicitní převod z nebo do jiného typu.</span><span class="sxs-lookup"><span data-stu-id="d2b77-104">A user-defined type can define a custom implicit or explicit conversion from or to another type.</span></span>

<span data-ttu-id="d2b77-105">Implicitní převody nevyžadují speciální syntaxe má být vyvolána a může dojít v různých situacích, například v přiřazení a metody volání.</span><span class="sxs-lookup"><span data-stu-id="d2b77-105">Implicit conversions don't require special syntax to be invoked and can occur in a variety of situations, for example, in assignments and methods invocations.</span></span> <span data-ttu-id="d2b77-106">Předdefinované C# implicitních převodů vždy úspěšné a nikdy vyvolat výjimku nebo dojít ke ztrátě informací.</span><span class="sxs-lookup"><span data-stu-id="d2b77-106">Predefined C# implicit conversions always succeed and never throw an exception or lose information.</span></span> <span data-ttu-id="d2b77-107">Uživatelem definované implicitní převody by měla chovat i tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="d2b77-107">User-defined implicit conversions should behave in that way as well.</span></span> <span data-ttu-id="d2b77-108">Pokud vlastní převod může vyvolat výjimku nebo dojít ke ztrátě informací, můžete jej definují jako explicitní převod.</span><span class="sxs-lookup"><span data-stu-id="d2b77-108">If a custom conversion can throw an exception or lose information, define it as an explicit conversion.</span></span>

<span data-ttu-id="d2b77-109">Uživatelem definované převody nejsou považovány za podle [je](type-testing-and-conversion-operators.md#is-operator) a [jako](type-testing-and-conversion-operators.md#as-operator) operátory.</span><span class="sxs-lookup"><span data-stu-id="d2b77-109">User-defined conversions are not considered by the [is](type-testing-and-conversion-operators.md#is-operator) and [as](type-testing-and-conversion-operators.md#as-operator) operators.</span></span> <span data-ttu-id="d2b77-110">Použití [přetypování () operátor](type-testing-and-conversion-operators.md#cast-operator-) vyvolat explicitní převod definovaný uživatelem.</span><span class="sxs-lookup"><span data-stu-id="d2b77-110">Use the [cast operator ()](type-testing-and-conversion-operators.md#cast-operator-) to invoke a user-defined explicit conversion.</span></span>

<span data-ttu-id="d2b77-111">Použití `operator` a `implicit` nebo `explicit` klíčová slova k definování implicitní nebo explicitní převod, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="d2b77-111">Use the `operator` and `implicit` or `explicit` keywords to define an implicit or explicit conversion, respectively.</span></span> <span data-ttu-id="d2b77-112">Typ, který definuje převod musí být typu zdrojový nebo cílový typ převodu.</span><span class="sxs-lookup"><span data-stu-id="d2b77-112">The type that defines a conversion must be either a source type or a target type of that conversion.</span></span> <span data-ttu-id="d2b77-113">Převod mezi dvěma uživatelem definované typy lze definovat v některém ze dvou typů.</span><span class="sxs-lookup"><span data-stu-id="d2b77-113">A conversion between two user-defined types can be defined in either of the two types.</span></span>

<span data-ttu-id="d2b77-114">Následující příklad ukazuje, jak definovat implicitní a explicitní převod:</span><span class="sxs-lookup"><span data-stu-id="d2b77-114">The following example demonstrates how to define an implicit and explicit conversion:</span></span>

[!code-csharp[implicit an explicit conversions](~/samples/csharp/language-reference/operators/UserDefinedConversions.cs)]

<span data-ttu-id="d2b77-115">Můžete také použít `operator` – klíčové slovo přetížení i předdefinovanou C# operátor.</span><span class="sxs-lookup"><span data-stu-id="d2b77-115">You also use the `operator` keyword to overload a predefined C# operator.</span></span> <span data-ttu-id="d2b77-116">Další informace najdete v tématu [přetížení operátoru](operator-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="d2b77-116">For more information, see [Operator overloading](operator-overloading.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d2b77-117">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d2b77-117">C# language specification</span></span>

<span data-ttu-id="d2b77-118">Další informace najdete v následující částech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="d2b77-118">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="d2b77-119">operátory převodu</span><span class="sxs-lookup"><span data-stu-id="d2b77-119">Conversion operators</span></span>](~/_csharplang/spec/classes.md#conversion-operators)
- [<span data-ttu-id="d2b77-120">Uživatelem definované převody</span><span class="sxs-lookup"><span data-stu-id="d2b77-120">User-defined conversions</span></span>](~/_csharplang/spec/conversions.md#user-defined-conversions)
- [<span data-ttu-id="d2b77-121">Implicitní převody</span><span class="sxs-lookup"><span data-stu-id="d2b77-121">Implicit conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-conversions)
- [<span data-ttu-id="d2b77-122">Explicitní převody</span><span class="sxs-lookup"><span data-stu-id="d2b77-122">Explicit conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-conversions)

## <a name="see-also"></a><span data-ttu-id="d2b77-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d2b77-123">See also</span></span>

- [<span data-ttu-id="d2b77-124">C#referenční dokumentace</span><span class="sxs-lookup"><span data-stu-id="d2b77-124">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d2b77-125">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d2b77-125">C# operators</span></span>](index.md)
- [<span data-ttu-id="d2b77-126">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="d2b77-126">Operator overloading</span></span>](operator-overloading.md)
- [<span data-ttu-id="d2b77-127">Typové zkoušky a převod operátorů</span><span class="sxs-lookup"><span data-stu-id="d2b77-127">Type-testing and conversion operators</span></span>](type-testing-and-conversion-operators.md)
- [<span data-ttu-id="d2b77-128">Přetypování a typ převodu</span><span class="sxs-lookup"><span data-stu-id="d2b77-128">Casting and type conversion</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="d2b77-129">Zřetězit uživatelem definované explicitní převody v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d2b77-129">Chained user-defined explicit conversions in C#</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
