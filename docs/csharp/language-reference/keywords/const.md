---
description: const – klíčové slovo – Reference jazyka C#
title: const – klíčové slovo – Reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- const_CSharpKeyword
- const
helpviewer_keywords:
- const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
ms.openlocfilehash: 312725c3a231f0ca766d5b99bf7d9308ddd634c4
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142086"
---
# <a name="const-c-reference"></a><span data-ttu-id="5fa54-103">const (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="5fa54-103">const (C# Reference)</span></span>

<span data-ttu-id="5fa54-104">`const`Klíčové slovo lze použít k deklarování konstantního pole nebo konstanty místní.</span><span class="sxs-lookup"><span data-stu-id="5fa54-104">You use the `const` keyword to declare a constant field or a constant local.</span></span> <span data-ttu-id="5fa54-105">Konstantní pole a místní hodnoty nejsou proměnné a nelze je upravovat.</span><span class="sxs-lookup"><span data-stu-id="5fa54-105">Constant fields and locals aren't variables and may not be modified.</span></span> <span data-ttu-id="5fa54-106">Konstanty můžou být čísla, logické hodnoty, řetězce nebo odkazy s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="5fa54-106">Constants can be numbers, Boolean values, strings, or a null reference.</span></span> <span data-ttu-id="5fa54-107">Nevytvářejte konstantu, která bude představovat informace, které byste měli kdykoli změnit.</span><span class="sxs-lookup"><span data-stu-id="5fa54-107">Don’t create a constant to represent information that you expect to change at any time.</span></span> <span data-ttu-id="5fa54-108">Například nepoužívejte pole konstanty k uložení ceny služby, čísla verze produktu nebo značky společnosti.</span><span class="sxs-lookup"><span data-stu-id="5fa54-108">For example, don’t use a constant field to store the price of a service, a product version number, or the brand name of a company.</span></span> <span data-ttu-id="5fa54-109">Tyto hodnoty se mohou v průběhu času měnit a vzhledem k tomu, že kompilátory šíří konstanty, je nutné znovu zkompilovat další kód kompilovaný s vašimi knihovnami, aby se změny projevily.</span><span class="sxs-lookup"><span data-stu-id="5fa54-109">These values can change over time, and because compilers propagate constants, other code compiled with your libraries will have to be recompiled to see the changes.</span></span> <span data-ttu-id="5fa54-110">Viz také klíčové slovo [ReadOnly](./readonly.md) .</span><span class="sxs-lookup"><span data-stu-id="5fa54-110">See also the [readonly](./readonly.md) keyword.</span></span> <span data-ttu-id="5fa54-111">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5fa54-111">For example:</span></span>

```csharp
const int X = 0;
public const double GravitationalConstant = 6.673e-11;
private const string ProductName = "Visual C#";
```

## <a name="remarks"></a><span data-ttu-id="5fa54-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5fa54-112">Remarks</span></span>

<span data-ttu-id="5fa54-113">Typ deklarace konstanty určuje typ členů, které deklarace zavádí.</span><span class="sxs-lookup"><span data-stu-id="5fa54-113">The type of a constant declaration specifies the type of the members that the declaration introduces.</span></span> <span data-ttu-id="5fa54-114">Inicializátor konstantního místního nebo konstantního pole musí být konstantní výraz, který lze implicitně převést na cílový typ.</span><span class="sxs-lookup"><span data-stu-id="5fa54-114">The initializer of a constant local or a constant field must be a constant expression that can be implicitly converted to the target type.</span></span>

<span data-ttu-id="5fa54-115">Konstantní výraz je výraz, který lze plně vyhodnotit v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="5fa54-115">A constant expression is an expression that can be fully evaluated at compile time.</span></span> <span data-ttu-id="5fa54-116">Proto jsou jedinou možnou hodnotou konstanty typu odkazu `string` a odkazem s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="5fa54-116">Therefore, the only possible values for constants of reference types are `string` and a null reference.</span></span>

<span data-ttu-id="5fa54-117">Deklarace konstanty může deklarovat více konstant, například:</span><span class="sxs-lookup"><span data-stu-id="5fa54-117">The constant declaration can declare multiple constants, such as:</span></span>

```csharp
public const double X = 1.0, Y = 2.0, Z = 3.0;
```

<span data-ttu-id="5fa54-118">`static`Modifikátor není v deklaraci konstanty povolen.</span><span class="sxs-lookup"><span data-stu-id="5fa54-118">The `static` modifier is not allowed in a constant declaration.</span></span>

<span data-ttu-id="5fa54-119">Konstanta se může účastnit konstantního výrazu, a to následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="5fa54-119">A constant can participate in a constant expression, as follows:</span></span>

```csharp
public const int C1 = 5;
public const int C2 = C1 + 100;
```

> [!NOTE]
> <span data-ttu-id="5fa54-120">Klíčové slovo [ReadOnly](./readonly.md) se liší od `const` klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="5fa54-120">The [readonly](./readonly.md) keyword differs from the `const` keyword.</span></span> <span data-ttu-id="5fa54-121">`const`Pole lze inicializovat pouze v deklaraci pole.</span><span class="sxs-lookup"><span data-stu-id="5fa54-121">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="5fa54-122">`readonly`Pole lze inicializovat buď v deklaraci, nebo v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="5fa54-122">A `readonly` field can be initialized either at the declaration or in a constructor.</span></span> <span data-ttu-id="5fa54-123">Proto `readonly` pole mohou mít různé hodnoty v závislosti na použitém konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="5fa54-123">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="5fa54-124">I když `const` je pole konstanta při kompilaci, `readonly` pole lze použít pro konstanty run-time, jako v tomto řádku: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span><span class="sxs-lookup"><span data-stu-id="5fa54-124">Also, although a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants, as in this line: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span></span>

## <a name="example"></a><span data-ttu-id="5fa54-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="5fa54-125">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#5)]

## <a name="example"></a><span data-ttu-id="5fa54-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="5fa54-126">Example</span></span>

<span data-ttu-id="5fa54-127">Tento příklad ukazuje, jak použít konstanty jako lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="5fa54-127">This example demonstrates how to use constants as local variables.</span></span>

[!code-csharp[csrefKeywordsModifiers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#6)]

## <a name="c-language-specification"></a><span data-ttu-id="5fa54-128">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5fa54-128">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="5fa54-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="5fa54-129">See also</span></span>

- [<span data-ttu-id="5fa54-130">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5fa54-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5fa54-131">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="5fa54-131">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5fa54-132">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5fa54-132">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="5fa54-133">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="5fa54-133">Modifiers</span></span>](index.md)
- [<span data-ttu-id="5fa54-134">readonly</span><span class="sxs-lookup"><span data-stu-id="5fa54-134">readonly</span></span>](./readonly.md)
