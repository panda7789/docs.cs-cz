---
title: C# výčty - přehled používání jazyka C#
description: Další informace o výčty, diskrétní s názvem konstanty v jazyku C#
ms.date: 08/10/2016
ms.assetid: 7faba1cc-6ea9-4a19-adb9-0335e4b132e5
ms.openlocfilehash: 7fe2626381cb90e55842e3be17dd450eb73d5a5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353351"
---
# <a name="enums"></a><span data-ttu-id="af7c3-103">Výčty</span><span class="sxs-lookup"><span data-stu-id="af7c3-103">Enums</span></span>

<span data-ttu-id="af7c3-104">***Typ výčtu*** je typ odlišné hodnoty sadu pojmenované konstanty.</span><span class="sxs-lookup"><span data-stu-id="af7c3-104">An ***enum type*** is a distinct value type with a set of named constants.</span></span> <span data-ttu-id="af7c3-105">Pokud potřebujete definovat typ, který může mít sadu diskrétních hodnot definujete výčty.</span><span class="sxs-lookup"><span data-stu-id="af7c3-105">You define enums when you need to define a type that can have a set of discrete values.</span></span> <span data-ttu-id="af7c3-106">Používají jeden z typů celočíselné hodnoty jako svoje základní úložiště.</span><span class="sxs-lookup"><span data-stu-id="af7c3-106">They use one of the integral value types as their underlying storage.</span></span> <span data-ttu-id="af7c3-107">Poskytují význam sémantického diskrétní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="af7c3-107">They provide semantic meaning to the discrete values.</span></span>

<span data-ttu-id="af7c3-108">Následující příklad deklaruje a používá `enum` typ s názvem `Color` s tři konstantní hodnoty, `Red`, `Green`, a `Blue`.</span><span class="sxs-lookup"><span data-stu-id="af7c3-108">The following example declares and uses an `enum` type named `Color` with three constant values, `Red`, `Green`, and `Blue`.</span></span>

[!code-csharp[EnumExample](../../../samples/snippets/csharp/tour/enums/Program.cs#L3-L36)]

<span data-ttu-id="af7c3-109">Každý `enum` typ má odpovídající integrální typu s názvem ***základní typ*** z `enum` typu.</span><span class="sxs-lookup"><span data-stu-id="af7c3-109">Each `enum` type has a corresponding integral type called the ***underlying type*** of the `enum` type.</span></span> <span data-ttu-id="af7c3-110">`enum` Typ, který nedeklaruje základní typ explicitně má základní typ `int`.</span><span class="sxs-lookup"><span data-stu-id="af7c3-110">An `enum` type that does not explicitly declare an underlying type has an underlying type of `int`.</span></span> <span data-ttu-id="af7c3-111">`enum` Formát úložiště typu a rozsahu možných hodnot určuje jeho zdrojovým typem.</span><span class="sxs-lookup"><span data-stu-id="af7c3-111">An `enum` type’s storage format and range of possible values are determined by its underlying type.</span></span> <span data-ttu-id="af7c3-112">Sada hodnoty, které `enum` typ může trvat na není omezený jeho `enum` členy.</span><span class="sxs-lookup"><span data-stu-id="af7c3-112">The set of values that an `enum` type can take on is not limited by its `enum` members.</span></span> <span data-ttu-id="af7c3-113">Konkrétně žádnou hodnotu základní typ `enum` lze převést na `enum` zadejte a odlišné platná hodnota této `enum` typu.</span><span class="sxs-lookup"><span data-stu-id="af7c3-113">In particular, any value of the underlying type of an `enum` can be cast to the `enum` type and is a distinct valid value of that `enum` type.</span></span>

<span data-ttu-id="af7c3-114">Následující příklad deklaruje `enum` typ s názvem `Alignment` s podkladovým typem `sbyte`.</span><span class="sxs-lookup"><span data-stu-id="af7c3-114">The following example declares an `enum` type named `Alignment` with an underlying type of `sbyte`.</span></span>

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L38-L43)]

<span data-ttu-id="af7c3-115">Jak ukazuje předchozí příklad, `enum` deklarace členů může zahrnovat konstantní výraz, který určuje hodnotu člena.</span><span class="sxs-lookup"><span data-stu-id="af7c3-115">As shown by the previous example, an `enum` member declaration can include a constant expression that specifies the value of the member.</span></span> <span data-ttu-id="af7c3-116">Konstantní hodnota pro každé `enum` člena musí být v rozsahu základní typ `enum`.</span><span class="sxs-lookup"><span data-stu-id="af7c3-116">The constant value for each `enum` member must be in the range of the underlying type of the `enum`.</span></span> <span data-ttu-id="af7c3-117">Při `enum` deklarace členů neurčuje explicitně hodnotu, člen je zadána hodnota nula (Pokud je první člen v `enum` typu) nebo hodnotu textový předchozí `enum` člen plus jedna.</span><span class="sxs-lookup"><span data-stu-id="af7c3-117">When an `enum` member declaration does not explicitly specify a value, the member is given the value zero (if it is the first member in the `enum` type) or the value of the textually preceding `enum` member plus one.</span></span>

<span data-ttu-id="af7c3-118">`Enum` hodnoty mohou být převeden na celočíselné hodnoty a naopak pomocí typ přetypování.</span><span class="sxs-lookup"><span data-stu-id="af7c3-118">`Enum` values can be converted to integral values and vice versa using type casts.</span></span> <span data-ttu-id="af7c3-119">Příklad:</span><span class="sxs-lookup"><span data-stu-id="af7c3-119">For example:</span></span>

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L49-L50)]

<span data-ttu-id="af7c3-120">Výchozí hodnota všech `enum` je integrální hodnota nula převést na typ `enum` typu.</span><span class="sxs-lookup"><span data-stu-id="af7c3-120">The default value of any `enum` type is the integral value zero converted to the `enum` type.</span></span> <span data-ttu-id="af7c3-121">V případech, kde jsou automaticky inicializovány proměnné na výchozí hodnotu, je to hodnota zadané proměnné `enum` typy.</span><span class="sxs-lookup"><span data-stu-id="af7c3-121">In cases where variables are automatically initialized to a default value, this is the value given to variables of `enum` types.</span></span> <span data-ttu-id="af7c3-122">V pořadí pro výchozí hodnotu `enum` typ, který má být snadno dostupné, skutečné `0` implicitně převede do jakéhokoli `enum` typu.</span><span class="sxs-lookup"><span data-stu-id="af7c3-122">In order for the default value of an `enum` type to be easily available, the literal `0` implicitly converts to any `enum` type.</span></span> <span data-ttu-id="af7c3-123">Proto následující je povolená.</span><span class="sxs-lookup"><span data-stu-id="af7c3-123">Thus, the following is permitted.</span></span>

[!code-csharp[EnumZero](../../../samples/snippets/csharp/tour/enums/Program.cs#L58-L58)]

>[!div class="step-by-step"]
<span data-ttu-id="af7c3-124">[Předchozí](interfaces.md)
[další](delegates.md)</span><span class="sxs-lookup"><span data-stu-id="af7c3-124">[Previous](interfaces.md)
[Next](delegates.md)</span></span>
