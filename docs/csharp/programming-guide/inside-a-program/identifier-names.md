---
title: Názvy identifikátorů
description: Další pravidla pro názvy platný identifikátor v programovacím jazyce C#.
ms.date: 08/21/2018
ms.openlocfilehash: 2147b3846d4ba6d5471b81448489c6d716e3cd61
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61680490"
---
# <a name="identifier-names"></a><span data-ttu-id="44cf5-103">Názvy identifikátorů</span><span class="sxs-lookup"><span data-stu-id="44cf5-103">Identifier names</span></span>

<span data-ttu-id="44cf5-104">**Identifikátor** je název přiřadit k typu (třída, rozhraní, struktury, delegáta nebo výčtu), člen, proměnná nebo oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="44cf5-104">An **identifier** is the name you assign to a type (class, interface, struct, delegate, or enum), member, variable, or namespace.</span></span> <span data-ttu-id="44cf5-105">Platné identifikátory musí dodržovat tato pravidla:</span><span class="sxs-lookup"><span data-stu-id="44cf5-105">Valid identifiers must follow these rules:</span></span>

- <span data-ttu-id="44cf5-106">Identifikátory musí začínat písmenem, nebo `_`.</span><span class="sxs-lookup"><span data-stu-id="44cf5-106">Identifiers must start with a letter, or `_`.</span></span>
- <span data-ttu-id="44cf5-107">Identifikátory mohou obsahovat písmena, znaky desítkových číslic, připojení znaků Unicode, kombinace znaků Unicode nebo formátování znaků Unicode kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="44cf5-107">Identifiers may contain Unicode letter characters, decimal digit characters, Unicode connecting characters, Unicode combining characters, or Unicode formatting characters.</span></span> <span data-ttu-id="44cf5-108">Další informace o kódování Unicode kategorií, najdete v článku [databáze kategorie sady Unicode](https://www.unicode.org/reports/tr44/).</span><span class="sxs-lookup"><span data-stu-id="44cf5-108">For more information on Unicode categories, see the [Unicode Category Database](https://www.unicode.org/reports/tr44/).</span></span>
<span data-ttu-id="44cf5-109">Je možné deklarovat identifikátory, které odpovídají klíčová slova jazyka C# s použitím `@` předpony u identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="44cf5-109">You can declare identifiers that match C# keywords by using the `@` prefix on the identifier.</span></span> <span data-ttu-id="44cf5-110">`@` Není součástí název identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="44cf5-110">The `@` is not part of the identifier name.</span></span> <span data-ttu-id="44cf5-111">Například `@if` deklaruje identifikátor s názvem `if`.</span><span class="sxs-lookup"><span data-stu-id="44cf5-111">For example, `@if` declares an identifier named `if`.</span></span> <span data-ttu-id="44cf5-112">Tyto [verbatim identifikátory](../../language-reference/tokens/verbatim.md) jsou primárně určeny pro interoperabilitu s identifikátory deklarované v jiných jazycích.</span><span class="sxs-lookup"><span data-stu-id="44cf5-112">These [verbatim identifiers](../../language-reference/tokens/verbatim.md) are primarily for interoperability with identifiers declared in other languages.</span></span>

<span data-ttu-id="44cf5-113">Kompletní definici platné identifikátory, najdete v článku [identifikátory tématu ve specifikaci jazyka C#](../../../../_csharplang/spec/lexical-structure.md#identifiers).</span><span class="sxs-lookup"><span data-stu-id="44cf5-113">For a complete definition of valid identifiers, see the [Identifiers topic in the C# Language Specification](../../../../_csharplang/spec/lexical-structure.md#identifiers).</span></span>

## <a name="naming-conventions"></a><span data-ttu-id="44cf5-114">Zásady vytváření názvů</span><span class="sxs-lookup"><span data-stu-id="44cf5-114">Naming conventions</span></span>

<span data-ttu-id="44cf5-115">Kromě pravidel, existuje mnoho identifikátoru [zásady vytváření názvů](../../../standard/design-guidelines/naming-guidelines.md) používaný v celém rozhraní .NET API.</span><span class="sxs-lookup"><span data-stu-id="44cf5-115">In addition to the rules, there are a number of identifier [naming conventions](../../../standard/design-guidelines/naming-guidelines.md) used throughout the .NET APIs.</span></span> <span data-ttu-id="44cf5-116">Podle konvence, C# programy používají `PascalCase` pro názvy typů, obory názvů a všechny veřejné členy.</span><span class="sxs-lookup"><span data-stu-id="44cf5-116">By convention, C# programs use `PascalCase` for type names, namespaces, and all public members.</span></span> <span data-ttu-id="44cf5-117">Kromě toho jsou společné následující konvence:</span><span class="sxs-lookup"><span data-stu-id="44cf5-117">In addition, the following conventions are common:</span></span>

- <span data-ttu-id="44cf5-118">Rozhraní názvy začíná na velké `I`.</span><span class="sxs-lookup"><span data-stu-id="44cf5-118">Interface names start with a capital `I`.</span></span>
- <span data-ttu-id="44cf5-119">Atribut typy končí slovem `Attribute`.</span><span class="sxs-lookup"><span data-stu-id="44cf5-119">Attribute types end with the word `Attribute`.</span></span>
- <span data-ttu-id="44cf5-120">Typy výčtu pomocí příznaků singulární podstatné jméno pro jiné příznaky a množném čísle podstatné jméno.</span><span class="sxs-lookup"><span data-stu-id="44cf5-120">Enum types use a singular noun for non-flags, and a plural noun for flags.</span></span>
- <span data-ttu-id="44cf5-121">Identifikátory by neměly obsahovat dva po sobě jdoucích `_` znaků.</span><span class="sxs-lookup"><span data-stu-id="44cf5-121">Identifiers should not contain two consecutive `_` characters.</span></span> <span data-ttu-id="44cf5-122">Tyto názvy jsou vyhrazené pro identifikátory generovaný kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="44cf5-122">Those names are reserved for compiler generated identifiers.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="44cf5-123">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="44cf5-123">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="44cf5-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="44cf5-124">See also</span></span>

- [<span data-ttu-id="44cf5-125">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="44cf5-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="44cf5-126">V programu v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="44cf5-126">Inside a C# Program</span></span>](../inside-a-program/index.md)
- [<span data-ttu-id="44cf5-127">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="44cf5-127">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="44cf5-128">Třídy</span><span class="sxs-lookup"><span data-stu-id="44cf5-128">Classes</span></span>](../classes-and-structs/classes.md)
- [<span data-ttu-id="44cf5-129">Struktury</span><span class="sxs-lookup"><span data-stu-id="44cf5-129">Structs</span></span>](../classes-and-structs/structs.md)
- [<span data-ttu-id="44cf5-130">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="44cf5-130">Namespaces</span></span>](../namespaces/index.md)
- [<span data-ttu-id="44cf5-131">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="44cf5-131">Interfaces</span></span>](../interfaces/index.md)
- [<span data-ttu-id="44cf5-132">Delegáti</span><span class="sxs-lookup"><span data-stu-id="44cf5-132">Delegates</span></span>](../delegates/index.md)
