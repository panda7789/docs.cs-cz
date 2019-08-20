---
title: Názvy identifikátorů
description: Přečtěte si pravidla platných názvů identifikátorů v C# programovacím jazyce.
ms.date: 08/21/2018
ms.openlocfilehash: f8a27ddae0437ed037b59f76d60dc7e420ddc2eb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589351"
---
# <a name="identifier-names"></a><span data-ttu-id="e738b-103">Názvy identifikátorů</span><span class="sxs-lookup"><span data-stu-id="e738b-103">Identifier names</span></span>

<span data-ttu-id="e738b-104">**Identifikátor** je název, který přiřadíte typu (třída, rozhraní, struktura, delegát nebo výčet), člen, proměnná nebo obor názvů.</span><span class="sxs-lookup"><span data-stu-id="e738b-104">An **identifier** is the name you assign to a type (class, interface, struct, delegate, or enum), member, variable, or namespace.</span></span> <span data-ttu-id="e738b-105">Platné identifikátory musí dodržovat tato pravidla:</span><span class="sxs-lookup"><span data-stu-id="e738b-105">Valid identifiers must follow these rules:</span></span>

- <span data-ttu-id="e738b-106">Identifikátory musí začínat písmenem nebo `_`.</span><span class="sxs-lookup"><span data-stu-id="e738b-106">Identifiers must start with a letter, or `_`.</span></span>
- <span data-ttu-id="e738b-107">Identifikátory můžou obsahovat znaky písmen Unicode, desítkové číslice, připojovací znaky Unicode, kombinaci znaků Unicode nebo formátovacích znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="e738b-107">Identifiers may contain Unicode letter characters, decimal digit characters, Unicode connecting characters, Unicode combining characters, or Unicode formatting characters.</span></span> <span data-ttu-id="e738b-108">Další informace o kategoriích sady Unicode najdete v tématu [databáze kategorií Unicode](https://www.unicode.org/reports/tr44/).</span><span class="sxs-lookup"><span data-stu-id="e738b-108">For more information on Unicode categories, see the [Unicode Category Database](https://www.unicode.org/reports/tr44/).</span></span>
<span data-ttu-id="e738b-109">Můžete deklarovat identifikátory, které odpovídají C# klíčovým slovům `@` pomocí předpony na identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="e738b-109">You can declare identifiers that match C# keywords by using the `@` prefix on the identifier.</span></span> <span data-ttu-id="e738b-110">`@` Není součástí názvu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="e738b-110">The `@` is not part of the identifier name.</span></span> <span data-ttu-id="e738b-111">Například `@if` deklaruje identifikátor s názvem `if`.</span><span class="sxs-lookup"><span data-stu-id="e738b-111">For example, `@if` declares an identifier named `if`.</span></span> <span data-ttu-id="e738b-112">Tyto [doslovné identifikátory](../../language-reference/tokens/verbatim.md) jsou primárně určeny pro interoperabilitu s identifikátory deklarovanými v jiných jazycích.</span><span class="sxs-lookup"><span data-stu-id="e738b-112">These [verbatim identifiers](../../language-reference/tokens/verbatim.md) are primarily for interoperability with identifiers declared in other languages.</span></span>

<span data-ttu-id="e738b-113">Úplnou definici platných identifikátorů najdete v [tématu identifikátory v tématu C# specifikace jazyka](../../../../_csharplang/spec/lexical-structure.md#identifiers).</span><span class="sxs-lookup"><span data-stu-id="e738b-113">For a complete definition of valid identifiers, see the [Identifiers topic in the C# Language Specification](../../../../_csharplang/spec/lexical-structure.md#identifiers).</span></span>

## <a name="naming-conventions"></a><span data-ttu-id="e738b-114">Zásady vytváření názvů</span><span class="sxs-lookup"><span data-stu-id="e738b-114">Naming conventions</span></span>

<span data-ttu-id="e738b-115">Kromě pravidel existuje několik konvencí pojmenování identifikátorů používaných [](../../../standard/design-guidelines/naming-guidelines.md) v rámci rozhraní API .NET.</span><span class="sxs-lookup"><span data-stu-id="e738b-115">In addition to the rules, there are a number of identifier [naming conventions](../../../standard/design-guidelines/naming-guidelines.md) used throughout the .NET APIs.</span></span> <span data-ttu-id="e738b-116">Podle konvence C# používají `PascalCase` programy pro názvy typů, obory názvů a všechny veřejné členy.</span><span class="sxs-lookup"><span data-stu-id="e738b-116">By convention, C# programs use `PascalCase` for type names, namespaces, and all public members.</span></span> <span data-ttu-id="e738b-117">Kromě toho jsou běžné následující konvence:</span><span class="sxs-lookup"><span data-stu-id="e738b-117">In addition, the following conventions are common:</span></span>

- <span data-ttu-id="e738b-118">Názvy rozhraní začínají velkým písmenem `I`.</span><span class="sxs-lookup"><span data-stu-id="e738b-118">Interface names start with a capital `I`.</span></span>
- <span data-ttu-id="e738b-119">Typy atributů končí slovem `Attribute`.</span><span class="sxs-lookup"><span data-stu-id="e738b-119">Attribute types end with the word `Attribute`.</span></span>
- <span data-ttu-id="e738b-120">Výčtové typy používají podstatná jména pro nepříznaky a v množném čísle pro příznaky.</span><span class="sxs-lookup"><span data-stu-id="e738b-120">Enum types use a singular noun for non-flags, and a plural noun for flags.</span></span>
- <span data-ttu-id="e738b-121">Identifikátory by neměly obsahovat dva po `_` sobě jdoucí znaky.</span><span class="sxs-lookup"><span data-stu-id="e738b-121">Identifiers should not contain two consecutive `_` characters.</span></span> <span data-ttu-id="e738b-122">Tyto názvy jsou vyhrazeny pro identifikátory generované kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="e738b-122">Those names are reserved for compiler generated identifiers.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e738b-123">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e738b-123">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e738b-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e738b-124">See also</span></span>

- [<span data-ttu-id="e738b-125">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e738b-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e738b-126">V programu v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e738b-126">Inside a C# Program</span></span>](./index.md)
- [<span data-ttu-id="e738b-127">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="e738b-127">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="e738b-128">Třídy</span><span class="sxs-lookup"><span data-stu-id="e738b-128">Classes</span></span>](../classes-and-structs/classes.md)
- [<span data-ttu-id="e738b-129">Struktury</span><span class="sxs-lookup"><span data-stu-id="e738b-129">Structs</span></span>](../classes-and-structs/structs.md)
- [<span data-ttu-id="e738b-130">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="e738b-130">Namespaces</span></span>](../namespaces/index.md)
- [<span data-ttu-id="e738b-131">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="e738b-131">Interfaces</span></span>](../interfaces/index.md)
- [<span data-ttu-id="e738b-132">Delegáti</span><span class="sxs-lookup"><span data-stu-id="e738b-132">Delegates</span></span>](../delegates/index.md)
