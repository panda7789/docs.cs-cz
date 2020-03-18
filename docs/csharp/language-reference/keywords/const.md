---
title: const klíčové slovo - C# Reference
ms.date: 07/20/2015
f1_keywords:
- const_CSharpKeyword
- const
helpviewer_keywords:
- const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
ms.openlocfilehash: 812aeb331b6dd333075d19076a896246ecc5b374
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713681"
---
# <a name="const-c-reference"></a><span data-ttu-id="3b95a-102">const (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="3b95a-102">const (C# Reference)</span></span>

<span data-ttu-id="3b95a-103">`const` Klíčové slovo slouží k deklarování konstantní pole nebo konstantní místní.</span><span class="sxs-lookup"><span data-stu-id="3b95a-103">You use the `const` keyword to declare a constant field or a constant local.</span></span> <span data-ttu-id="3b95a-104">Konstantní pole a místní jsou proměnné a nemusí být změněny.</span><span class="sxs-lookup"><span data-stu-id="3b95a-104">Constant fields and locals aren't variables and may not be modified.</span></span> <span data-ttu-id="3b95a-105">Konstantami mohou být čísla, logické hodnoty, řetězce nebo nulový odkaz.</span><span class="sxs-lookup"><span data-stu-id="3b95a-105">Constants can be numbers, Boolean values, strings, or a null reference.</span></span> <span data-ttu-id="3b95a-106">Nevytvářejte konstantu představující informace, které očekáváte, že kdykoli změníte.</span><span class="sxs-lookup"><span data-stu-id="3b95a-106">Don’t create a constant to represent information that you expect to change at any time.</span></span> <span data-ttu-id="3b95a-107">Nepoužívejte například konstantní pole k uložení ceny služby, čísla verze produktu nebo názvu značky společnosti.</span><span class="sxs-lookup"><span data-stu-id="3b95a-107">For example, don’t use a constant field to store the price of a service, a product version number, or the brand name of a company.</span></span> <span data-ttu-id="3b95a-108">Tyto hodnoty se mohou v průběhu času měnit a protože kompilátory šíří konstanty, další kód zkompilovaný s knihovnami bude muset být znovu zkompilován, aby se zobcházely změny.</span><span class="sxs-lookup"><span data-stu-id="3b95a-108">These values can change over time, and because compilers propagate constants, other code compiled with your libraries will have to be recompiled to see the changes.</span></span> <span data-ttu-id="3b95a-109">Viz také klíčové slovo [jen pro čtení.](./readonly.md)</span><span class="sxs-lookup"><span data-stu-id="3b95a-109">See also the [readonly](./readonly.md) keyword.</span></span> <span data-ttu-id="3b95a-110">Například:</span><span class="sxs-lookup"><span data-stu-id="3b95a-110">For example:</span></span>

```csharp
const int X = 0;
public const double GravitationalConstant = 6.673e-11;
private const string ProductName = "Visual C#";
```

## <a name="remarks"></a><span data-ttu-id="3b95a-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3b95a-111">Remarks</span></span>

<span data-ttu-id="3b95a-112">Typ konstantní deklarace určuje typ členů, které deklarace zavádí.</span><span class="sxs-lookup"><span data-stu-id="3b95a-112">The type of a constant declaration specifies the type of the members that the declaration introduces.</span></span> <span data-ttu-id="3b95a-113">Inicializátor konstantní místní nebo konstantní pole musí být konstantní výraz, který lze implicitně převést na cílový typ.</span><span class="sxs-lookup"><span data-stu-id="3b95a-113">The initializer of a constant local or a constant field must be a constant expression that can be implicitly converted to the target type.</span></span>

<span data-ttu-id="3b95a-114">Konstantní výraz je výraz, který lze plně vyhodnotit v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="3b95a-114">A constant expression is an expression that can be fully evaluated at compile time.</span></span> <span data-ttu-id="3b95a-115">Proto pouze možné hodnoty pro konstanty `string` typy odkazů jsou a null odkaz.</span><span class="sxs-lookup"><span data-stu-id="3b95a-115">Therefore, the only possible values for constants of reference types are `string` and a null reference.</span></span>

<span data-ttu-id="3b95a-116">Konstantní deklarace může deklarovat více konstant, například:</span><span class="sxs-lookup"><span data-stu-id="3b95a-116">The constant declaration can declare multiple constants, such as:</span></span>

```csharp
public const double X = 1.0, Y = 2.0, Z = 3.0;
```

<span data-ttu-id="3b95a-117">Modifikátor `static` není povolen v konstantní deklaraci.</span><span class="sxs-lookup"><span data-stu-id="3b95a-117">The `static` modifier is not allowed in a constant declaration.</span></span>

<span data-ttu-id="3b95a-118">Konstanta se může účastnit konstantního výrazu takto:</span><span class="sxs-lookup"><span data-stu-id="3b95a-118">A constant can participate in a constant expression, as follows:</span></span>

```csharp
public const int C1 = 5;
public const int C2 = C1 + 100;
```

> [!NOTE]
> <span data-ttu-id="3b95a-119">Klíčové slovo [jen pro](./readonly.md) `const` čtení se liší od klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="3b95a-119">The [readonly](./readonly.md) keyword differs from the `const` keyword.</span></span> <span data-ttu-id="3b95a-120">Pole `const` lze inicializovat pouze při deklaraci tohoto pole.</span><span class="sxs-lookup"><span data-stu-id="3b95a-120">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="3b95a-121">Pole `readonly` lze inicializovat buď v deklaraci, nebo v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="3b95a-121">A `readonly` field can be initialized either at the declaration or in a constructor.</span></span> <span data-ttu-id="3b95a-122">`readonly` Pole proto mohou mít různé hodnoty v závislosti na použitém konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="3b95a-122">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="3b95a-123">I když `const` je pole konstantou v `readonly` době kompilace, lze toto pole použít pro konstanty za běhu, jako v tomto řádku:`public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span><span class="sxs-lookup"><span data-stu-id="3b95a-123">Also, although a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants, as in this line: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span></span>

## <a name="example"></a><span data-ttu-id="3b95a-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="3b95a-124">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#5)]

## <a name="example"></a><span data-ttu-id="3b95a-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="3b95a-125">Example</span></span>

<span data-ttu-id="3b95a-126">Tento příklad ukazuje, jak používat konstanty jako místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="3b95a-126">This example demonstrates how to use constants as local variables.</span></span>

[!code-csharp[csrefKeywordsModifiers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#6)]

## <a name="c-language-specification"></a><span data-ttu-id="3b95a-127">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3b95a-127">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="3b95a-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="3b95a-128">See also</span></span>

- [<span data-ttu-id="3b95a-129">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3b95a-129">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3b95a-130">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3b95a-130">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3b95a-131">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="3b95a-131">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="3b95a-132">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="3b95a-132">Modifiers</span></span>](index.md)
- [<span data-ttu-id="3b95a-133">Readonly</span><span class="sxs-lookup"><span data-stu-id="3b95a-133">readonly</span></span>](./readonly.md)
