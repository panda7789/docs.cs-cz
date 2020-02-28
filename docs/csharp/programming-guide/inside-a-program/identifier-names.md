---
title: Názvy identifikátorů
description: Přečtěte si pravidla platných názvů identifikátorů v C# programovacím jazyce.
ms.date: 08/21/2018
ms.openlocfilehash: bef6e2ea285b5391af3350ae42a4105d140c6d1b
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "77673365"
---
# <a name="identifier-names"></a><span data-ttu-id="c40cf-103">Názvy identifikátorů</span><span class="sxs-lookup"><span data-stu-id="c40cf-103">Identifier names</span></span>

<span data-ttu-id="c40cf-104">**Identifikátor** je název, který přiřadíte typu (třída, rozhraní, struktura, delegát nebo výčet), člen, proměnná nebo obor názvů.</span><span class="sxs-lookup"><span data-stu-id="c40cf-104">An **identifier** is the name you assign to a type (class, interface, struct, delegate, or enum), member, variable, or namespace.</span></span> <span data-ttu-id="c40cf-105">Platné identifikátory musí dodržovat tato pravidla:</span><span class="sxs-lookup"><span data-stu-id="c40cf-105">Valid identifiers must follow these rules:</span></span>

- <span data-ttu-id="c40cf-106">Identifikátory musí začínat písmenem nebo `_`.</span><span class="sxs-lookup"><span data-stu-id="c40cf-106">Identifiers must start with a letter, or `_`.</span></span>
- <span data-ttu-id="c40cf-107">Identifikátory můžou obsahovat znaky písmen Unicode, desítkové číslice, připojovací znaky Unicode, kombinaci znaků Unicode nebo formátovacích znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="c40cf-107">Identifiers may contain Unicode letter characters, decimal digit characters, Unicode connecting characters, Unicode combining characters, or Unicode formatting characters.</span></span> <span data-ttu-id="c40cf-108">Další informace o kategoriích sady Unicode najdete v tématu [databáze kategorií Unicode](https://www.unicode.org/reports/tr44/).</span><span class="sxs-lookup"><span data-stu-id="c40cf-108">For more information on Unicode categories, see the [Unicode Category Database](https://www.unicode.org/reports/tr44/).</span></span>
<span data-ttu-id="c40cf-109">Identifikátory, které odpovídají C# klíčovým slovům, můžete deklarovat pomocí předpony `@` v identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="c40cf-109">You can declare identifiers that match C# keywords by using the `@` prefix on the identifier.</span></span> <span data-ttu-id="c40cf-110">`@` není součástí názvu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="c40cf-110">The `@` is not part of the identifier name.</span></span> <span data-ttu-id="c40cf-111">Například `@if` deklaruje identifikátor s názvem `if`.</span><span class="sxs-lookup"><span data-stu-id="c40cf-111">For example, `@if` declares an identifier named `if`.</span></span> <span data-ttu-id="c40cf-112">Tyto [doslovné identifikátory](../../language-reference/tokens/verbatim.md) jsou primárně určeny pro interoperabilitu s identifikátory deklarovanými v jiných jazycích.</span><span class="sxs-lookup"><span data-stu-id="c40cf-112">These [verbatim identifiers](../../language-reference/tokens/verbatim.md) are primarily for interoperability with identifiers declared in other languages.</span></span>

<span data-ttu-id="c40cf-113">Úplnou definici platných identifikátorů najdete v [tématu identifikátory v tématu C# specifikace jazyka](../../../../_csharplang/spec/lexical-structure.md#identifiers).</span><span class="sxs-lookup"><span data-stu-id="c40cf-113">For a complete definition of valid identifiers, see the [Identifiers topic in the C# Language Specification](../../../../_csharplang/spec/lexical-structure.md#identifiers).</span></span>

## <a name="naming-conventions"></a><span data-ttu-id="c40cf-114">Zásady vytváření názvů</span><span class="sxs-lookup"><span data-stu-id="c40cf-114">Naming conventions</span></span>

<span data-ttu-id="c40cf-115">Kromě pravidel existuje několik [konvencí pojmenování](../../../standard/design-guidelines/naming-guidelines.md) identifikátorů používaných v rámci rozhraní API .NET.</span><span class="sxs-lookup"><span data-stu-id="c40cf-115">In addition to the rules, there are a number of identifier [naming conventions](../../../standard/design-guidelines/naming-guidelines.md) used throughout the .NET APIs.</span></span> <span data-ttu-id="c40cf-116">Podle konvence C# používají programy `PascalCase` pro názvy typů, obory názvů a všechny veřejné členy.</span><span class="sxs-lookup"><span data-stu-id="c40cf-116">By convention, C# programs use `PascalCase` for type names, namespaces, and all public members.</span></span> <span data-ttu-id="c40cf-117">Kromě toho jsou běžné následující konvence:</span><span class="sxs-lookup"><span data-stu-id="c40cf-117">In addition, the following conventions are common:</span></span>

- <span data-ttu-id="c40cf-118">Názvy rozhraní začínají velkým `I`m.</span><span class="sxs-lookup"><span data-stu-id="c40cf-118">Interface names start with a capital `I`.</span></span>
- <span data-ttu-id="c40cf-119">Typy atributů končí slovem `Attribute`.</span><span class="sxs-lookup"><span data-stu-id="c40cf-119">Attribute types end with the word `Attribute`.</span></span>
- <span data-ttu-id="c40cf-120">Výčtové typy používají podstatná jména pro nepříznaky a v množném čísle pro příznaky.</span><span class="sxs-lookup"><span data-stu-id="c40cf-120">Enum types use a singular noun for non-flags, and a plural noun for flags.</span></span>
- <span data-ttu-id="c40cf-121">Identifikátory by neměly obsahovat dva po sobě jdoucí `_` znaky.</span><span class="sxs-lookup"><span data-stu-id="c40cf-121">Identifiers should not contain two consecutive `_` characters.</span></span> <span data-ttu-id="c40cf-122">Tyto názvy jsou vyhrazeny pro identifikátory generované kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="c40cf-122">Those names are reserved for compiler generated identifiers.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c40cf-123">C# – jazyková specifikace</span><span class="sxs-lookup"><span data-stu-id="c40cf-123">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c40cf-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="c40cf-124">See also</span></span>

- [<span data-ttu-id="c40cf-125">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="c40cf-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c40cf-126">V programu v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="c40cf-126">Inside a C# Program</span></span>](./index.md)
- [<span data-ttu-id="c40cf-127">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="c40cf-127">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="c40cf-128">Třídy</span><span class="sxs-lookup"><span data-stu-id="c40cf-128">Classes</span></span>](../classes-and-structs/classes.md)
- [<span data-ttu-id="c40cf-129">Typy struktury</span><span class="sxs-lookup"><span data-stu-id="c40cf-129">Structure types</span></span>](../../language-reference/builtin-types/struct.md)
- [<span data-ttu-id="c40cf-130">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="c40cf-130">Namespaces</span></span>](../namespaces/index.md)
- [<span data-ttu-id="c40cf-131">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="c40cf-131">Interfaces</span></span>](../interfaces/index.md)
- [<span data-ttu-id="c40cf-132">Delegáty</span><span class="sxs-lookup"><span data-stu-id="c40cf-132">Delegates</span></span>](../delegates/index.md)
