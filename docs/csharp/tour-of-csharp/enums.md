---
title: C#Výčty – připravuje C# jazyka
description: Další informace o výčtů diskrétní pojmenované konstanty vC#
ms.date: 08/10/2016
ms.assetid: 7faba1cc-6ea9-4a19-adb9-0335e4b132e5
ms.openlocfilehash: 8c1c29c3c06829da81a9c9be8bb5bd99f1c9e395
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57843121"
---
# <a name="enums"></a><span data-ttu-id="daa35-103">Výčty</span><span class="sxs-lookup"><span data-stu-id="daa35-103">Enums</span></span>

<span data-ttu-id="daa35-104">***Typ výčtu*** je typ odlišné hodnoty se sadou pojmenovaných konstant.</span><span class="sxs-lookup"><span data-stu-id="daa35-104">An ***enum type*** is a distinct value type with a set of named constants.</span></span> <span data-ttu-id="daa35-105">Můžete definovat výčty, pro které je třeba definovat typ, který může mít sady jednotlivých hodnot.</span><span class="sxs-lookup"><span data-stu-id="daa35-105">You define enums when you need to define a type that can have a set of discrete values.</span></span> <span data-ttu-id="daa35-106">Používají jeden z typů celočíselné hodnoty jako svoje základní úložiště.</span><span class="sxs-lookup"><span data-stu-id="daa35-106">They use one of the integral value types as their underlying storage.</span></span> <span data-ttu-id="daa35-107">Poskytují sémantický význam jednotlivých hodnot.</span><span class="sxs-lookup"><span data-stu-id="daa35-107">They provide semantic meaning to the discrete values.</span></span>

<span data-ttu-id="daa35-108">Následující příklad deklaruje a používá `enum` typ s názvem `Color` pomocí tří hodnot konstanty `Red`, `Green`, a `Blue`.</span><span class="sxs-lookup"><span data-stu-id="daa35-108">The following example declares and uses an `enum` type named `Color` with three constant values, `Red`, `Green`, and `Blue`.</span></span>

[!code-csharp[EnumExample](../../../samples/snippets/csharp/tour/enums/Program.cs#L3-L36)]

<span data-ttu-id="daa35-109">Každý `enum` typ má odpovídající integrální typ s názvem ***nadřízený typ*** z `enum` typu.</span><span class="sxs-lookup"><span data-stu-id="daa35-109">Each `enum` type has a corresponding integral type called the ***underlying type*** of the `enum` type.</span></span> <span data-ttu-id="daa35-110">`enum` Typ, který nedeklaruje explicitně nadřízený typ má základní typ `int`.</span><span class="sxs-lookup"><span data-stu-id="daa35-110">An `enum` type that does not explicitly declare an underlying type has an underlying type of `int`.</span></span> <span data-ttu-id="daa35-111">`enum` Úložném formátu a rozsah možných hodnot typu se určují podle jeho nadřízeného typu.</span><span class="sxs-lookup"><span data-stu-id="daa35-111">An `enum` type’s storage format and range of possible values are determined by its underlying type.</span></span> <span data-ttu-id="daa35-112">Sadu hodnot, které `enum` typu můžete provést na nebude omezen jeho `enum` členy.</span><span class="sxs-lookup"><span data-stu-id="daa35-112">The set of values that an `enum` type can take on is not limited by its `enum` members.</span></span> <span data-ttu-id="daa35-113">Konkrétně se libovolná hodnota základního typu `enum` lze převést na `enum` typ a je odlišné platnou hodnotou, která `enum` typu.</span><span class="sxs-lookup"><span data-stu-id="daa35-113">In particular, any value of the underlying type of an `enum` can be cast to the `enum` type and is a distinct valid value of that `enum` type.</span></span>

<span data-ttu-id="daa35-114">Následující příklad deklaruje `enum` typ s názvem `Alignment` pomocí základního typu `sbyte`.</span><span class="sxs-lookup"><span data-stu-id="daa35-114">The following example declares an `enum` type named `Alignment` with an underlying type of `sbyte`.</span></span>

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L38-L43)]

<span data-ttu-id="daa35-115">Jak je znázorněno v předchozím příkladu, `enum` deklarace člena. může obsahovat konstantní výraz, který určuje hodnotu člena.</span><span class="sxs-lookup"><span data-stu-id="daa35-115">As shown by the previous example, an `enum` member declaration can include a constant expression that specifies the value of the member.</span></span> <span data-ttu-id="daa35-116">Konstantní hodnota pro každé `enum` člen musí být v rozsahu od základního typu `enum`.</span><span class="sxs-lookup"><span data-stu-id="daa35-116">The constant value for each `enum` member must be in the range of the underlying type of the `enum`.</span></span> <span data-ttu-id="daa35-117">Při `enum` deklarace člena explicitně neurčí hodnotu, člen je zadána hodnota nula (Pokud je první člen v `enum` typ) nebo hodnotu textový předchozí `enum` člena plus jedna.</span><span class="sxs-lookup"><span data-stu-id="daa35-117">When an `enum` member declaration does not explicitly specify a value, the member is given the value zero (if it is the first member in the `enum` type) or the value of the textually preceding `enum` member plus one.</span></span>

<span data-ttu-id="daa35-118">`Enum` hodnoty mohou být převedeny na integrální hodnoty a naopak pomocí přetypování.</span><span class="sxs-lookup"><span data-stu-id="daa35-118">`Enum` values can be converted to integral values and vice versa using type casts.</span></span> <span data-ttu-id="daa35-119">Příklad:</span><span class="sxs-lookup"><span data-stu-id="daa35-119">For example:</span></span>

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L49-L50)]

<span data-ttu-id="daa35-120">Zadejte výchozí hodnotu kterékoli `enum` je celočíselná hodnota nula, převést na typ `enum` typu.</span><span class="sxs-lookup"><span data-stu-id="daa35-120">The default value of any `enum` type is the integral value zero converted to the `enum` type.</span></span> <span data-ttu-id="daa35-121">V případech, kdy proměnné jsou automaticky inicializovány na výchozí hodnotu, jedná se o hodnotu k proměnné `enum` typy.</span><span class="sxs-lookup"><span data-stu-id="daa35-121">In cases where variables are automatically initialized to a default value, this is the value given to variables of `enum` types.</span></span> <span data-ttu-id="daa35-122">Aby výchozí hodnota `enum` typ, který má být snadno k dispozici, literál `0` implicitně převede na jakýkoli `enum` typu.</span><span class="sxs-lookup"><span data-stu-id="daa35-122">In order for the default value of an `enum` type to be easily available, the literal `0` implicitly converts to any `enum` type.</span></span> <span data-ttu-id="daa35-123">Proto následující je povolený.</span><span class="sxs-lookup"><span data-stu-id="daa35-123">Thus, the following is permitted.</span></span>

[!code-csharp[EnumZero](../../../samples/snippets/csharp/tour/enums/Program.cs#L58-L58)]

> [!div class="step-by-step"]
> <span data-ttu-id="daa35-124">[Předchozí](interfaces.md)
> [další](delegates.md)</span><span class="sxs-lookup"><span data-stu-id="daa35-124">[Previous](interfaces.md)
[Next](delegates.md)</span></span>
