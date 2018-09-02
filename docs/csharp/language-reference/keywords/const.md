---
title: Const – klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- const_CSharpKeyword
- const
helpviewer_keywords:
- const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
ms.openlocfilehash: f586b6d097a8592fd74e92df7886b519d623e478
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43393002"
---
# <a name="const-c-reference"></a><span data-ttu-id="a8a1c-102">const (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="a8a1c-102">const (C# Reference)</span></span>

<span data-ttu-id="a8a1c-103">Můžete použít `const` – klíčové slovo k deklaraci konstanty pole nebo místního prostředí konstanty.</span><span class="sxs-lookup"><span data-stu-id="a8a1c-103">You use the `const` keyword to declare a constant field or a constant local.</span></span> <span data-ttu-id="a8a1c-104">Konstantní pole a místní hodnoty nejsou proměnné a nejde ho upravit.</span><span class="sxs-lookup"><span data-stu-id="a8a1c-104">Constant fields and locals aren't variables and may not be modified.</span></span> <span data-ttu-id="a8a1c-105">Konstanty mohou obsahovat čísla, logické hodnoty, řetězce nebo odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="a8a1c-105">Constants can be numbers, Boolean values, strings, or a null reference.</span></span> <span data-ttu-id="a8a1c-106">Nevytvářejte konstantu ke znázornění informací, které můžete kdykoli změnit.</span><span class="sxs-lookup"><span data-stu-id="a8a1c-106">Don’t create a constant to represent information that you expect to change at any time.</span></span> <span data-ttu-id="a8a1c-107">Například nepoužívejte pole konstanty pro uložení ceny služby, číslo verze produktu nebo název značky společnosti.</span><span class="sxs-lookup"><span data-stu-id="a8a1c-107">For example, don’t use a constant field to store the price of a service, a product version number, or the brand name of a company.</span></span> <span data-ttu-id="a8a1c-108">Tyto hodnoty můžou časem změnit. a protože kompilátory šířit konstanty, jiný kód zkompilovaný s vaší knihovny bude mít třeba znovu zkompilovat, aby se změny projevily.</span><span class="sxs-lookup"><span data-stu-id="a8a1c-108">These values can change over time, and because compilers propagate constants, other code compiled with your libraries will have to be recompiled to see the changes.</span></span> <span data-ttu-id="a8a1c-109">Viz také [jen pro čtení](../../../csharp/language-reference/keywords/readonly.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="a8a1c-109">See also the [readonly](../../../csharp/language-reference/keywords/readonly.md) keyword.</span></span> <span data-ttu-id="a8a1c-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a8a1c-110">For example:</span></span>

```csharp
const int x = 0;
public const double gravitationalConstant = 6.673e-11;
private const string productName = "Visual C#";
```

## <a name="remarks"></a><span data-ttu-id="a8a1c-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a8a1c-111">Remarks</span></span>

<span data-ttu-id="a8a1c-112">Typ deklarace konstanty Určuje typ členů, které deklarace zavádí.</span><span class="sxs-lookup"><span data-stu-id="a8a1c-112">The type of a constant declaration specifies the type of the members that the declaration introduces.</span></span> <span data-ttu-id="a8a1c-113">Inicializátor místní konstanty nebo pole konstanty musí být konstantní výraz, který lze implicitně převést na typ cíle.</span><span class="sxs-lookup"><span data-stu-id="a8a1c-113">The initializer of a constant local or a constant field must be a constant expression that can be implicitly converted to the target type.</span></span>

<span data-ttu-id="a8a1c-114">Konstantní výraz je výraz, který může být plně vyhodnocen v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="a8a1c-114">A constant expression is an expression that can be fully evaluated at compile time.</span></span> <span data-ttu-id="a8a1c-115">Proto jediné možné hodnoty pro konstanty odkazových typů jsou `string` a odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="a8a1c-115">Therefore, the only possible values for constants of reference types are `string` and a null reference.</span></span>

<span data-ttu-id="a8a1c-116">Deklarace konstanty může deklarovat více konstant, jako například:</span><span class="sxs-lookup"><span data-stu-id="a8a1c-116">The constant declaration can declare multiple constants, such as:</span></span>

```csharp
public const double x = 1.0, y = 2.0, z = 3.0;
```

<span data-ttu-id="a8a1c-117">`static` Modifikátor není povolen v deklarace konstanty.</span><span class="sxs-lookup"><span data-stu-id="a8a1c-117">The `static` modifier is not allowed in a constant declaration.</span></span>

<span data-ttu-id="a8a1c-118">Konstanta můžete zúčastnit konstantního výrazu, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="a8a1c-118">A constant can participate in a constant expression, as follows:</span></span>

```csharp
public const int c1 = 5;
public const int c2 = c1 + 100;
```

> [!NOTE]
> <span data-ttu-id="a8a1c-119">[Jen pro čtení](../../../csharp/language-reference/keywords/readonly.md) – klíčové slovo se liší od `const` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="a8a1c-119">The [readonly](../../../csharp/language-reference/keywords/readonly.md) keyword differs from the `const` keyword.</span></span> <span data-ttu-id="a8a1c-120">A `const` pole mohou být inicializovány pouze v deklaraci pole.</span><span class="sxs-lookup"><span data-stu-id="a8a1c-120">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="a8a1c-121">A `readonly` pole mohou být inicializovány při deklaraci nebo v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="a8a1c-121">A `readonly` field can be initialized either at the declaration or in a constructor.</span></span> <span data-ttu-id="a8a1c-122">Proto `readonly` pole může mít různé hodnoty v závislosti na použitém konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="a8a1c-122">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="a8a1c-123">Také i když `const` pole je konstantu kompilace `readonly` pole můžete použít pro konstanty z doby běhu, jako v tomto řádku: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span><span class="sxs-lookup"><span data-stu-id="a8a1c-123">Also, although a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants, as in this line: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span></span>

## <a name="example"></a><span data-ttu-id="a8a1c-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="a8a1c-124">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#5)]

## <a name="example"></a><span data-ttu-id="a8a1c-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="a8a1c-125">Example</span></span>

<span data-ttu-id="a8a1c-126">Tento příklad ukazuje, jak použít konstanty jako lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="a8a1c-126">This example demonstrates how to use constants as local variables.</span></span>

[!code-csharp[csrefKeywordsModifiers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#6)]

## <a name="c-language-specification"></a><span data-ttu-id="a8a1c-127">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a8a1c-127">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a8a1c-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a8a1c-128">See also</span></span>

- [<span data-ttu-id="a8a1c-129">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a8a1c-129">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="a8a1c-130">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="a8a1c-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="a8a1c-131">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a8a1c-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="a8a1c-132">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="a8a1c-132">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
- [<span data-ttu-id="a8a1c-133">readonly</span><span class="sxs-lookup"><span data-stu-id="a8a1c-133">readonly</span></span>](../../../csharp/language-reference/keywords/readonly.md)
