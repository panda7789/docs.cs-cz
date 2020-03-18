---
title: Názvy identifikátorů
description: Naučte se pravidla pro platné názvy identifikátorů v programovacím jazyce C#.
ms.date: 08/21/2018
ms.openlocfilehash: bef6e2ea285b5391af3350ae42a4105d140c6d1b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77673365"
---
# <a name="identifier-names"></a><span data-ttu-id="9f7fc-103">Názvy identifikátorů</span><span class="sxs-lookup"><span data-stu-id="9f7fc-103">Identifier names</span></span>

<span data-ttu-id="9f7fc-104">**Identifikátor** je název, který přiřadíte typu (třída, rozhraní, struktura, delegát nebo výčt), člen, proměnná nebo obor názvů.</span><span class="sxs-lookup"><span data-stu-id="9f7fc-104">An **identifier** is the name you assign to a type (class, interface, struct, delegate, or enum), member, variable, or namespace.</span></span> <span data-ttu-id="9f7fc-105">Platné identifikátory se musí řídit těmito pravidly:</span><span class="sxs-lookup"><span data-stu-id="9f7fc-105">Valid identifiers must follow these rules:</span></span>

- <span data-ttu-id="9f7fc-106">Identifikátory musí začínat `_`písmenem nebo .</span><span class="sxs-lookup"><span data-stu-id="9f7fc-106">Identifiers must start with a letter, or `_`.</span></span>
- <span data-ttu-id="9f7fc-107">Identifikátory mohou obsahovat znaky písmen Unicode, desetinné číslice, spojovací znaky Unicode, znaky kombinující znaky Unicode nebo formátovací znaky Unicode.</span><span class="sxs-lookup"><span data-stu-id="9f7fc-107">Identifiers may contain Unicode letter characters, decimal digit characters, Unicode connecting characters, Unicode combining characters, or Unicode formatting characters.</span></span> <span data-ttu-id="9f7fc-108">Další informace o kategoriích Unicode naleznete v [databázi kategorií Unicode](https://www.unicode.org/reports/tr44/).</span><span class="sxs-lookup"><span data-stu-id="9f7fc-108">For more information on Unicode categories, see the [Unicode Category Database](https://www.unicode.org/reports/tr44/).</span></span>
<span data-ttu-id="9f7fc-109">Můžete deklarovat identifikátory, které odpovídají `@` c# klíčová slova pomocí předpony na identifikátor.</span><span class="sxs-lookup"><span data-stu-id="9f7fc-109">You can declare identifiers that match C# keywords by using the `@` prefix on the identifier.</span></span> <span data-ttu-id="9f7fc-110">Není `@` součástí názvu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="9f7fc-110">The `@` is not part of the identifier name.</span></span> <span data-ttu-id="9f7fc-111">Například `@if` deklaruje `if`identifikátor s názvem .</span><span class="sxs-lookup"><span data-stu-id="9f7fc-111">For example, `@if` declares an identifier named `if`.</span></span> <span data-ttu-id="9f7fc-112">Tyto [doslovné identifikátory](../../language-reference/tokens/verbatim.md) jsou primárně pro interoperabilitu s identifikátory deklarovanými v jiných jazycích.</span><span class="sxs-lookup"><span data-stu-id="9f7fc-112">These [verbatim identifiers](../../language-reference/tokens/verbatim.md) are primarily for interoperability with identifiers declared in other languages.</span></span>

<span data-ttu-id="9f7fc-113">For a complete definition of valid identifiers, see the [Identifiers topic in the C# Language Specification](../../../../_csharplang/spec/lexical-structure.md#identifiers).</span><span class="sxs-lookup"><span data-stu-id="9f7fc-113">For a complete definition of valid identifiers, see the [Identifiers topic in the C# Language Specification](../../../../_csharplang/spec/lexical-structure.md#identifiers).</span></span>

## <a name="naming-conventions"></a><span data-ttu-id="9f7fc-114">Zásady vytváření názvů</span><span class="sxs-lookup"><span data-stu-id="9f7fc-114">Naming conventions</span></span>

<span data-ttu-id="9f7fc-115">Kromě pravidel existuje řada [konvencí pojmenování identifikátorů používaných](../../../standard/design-guidelines/naming-guidelines.md) v rámci rozhraní API .NET.</span><span class="sxs-lookup"><span data-stu-id="9f7fc-115">In addition to the rules, there are a number of identifier [naming conventions](../../../standard/design-guidelines/naming-guidelines.md) used throughout the .NET APIs.</span></span> <span data-ttu-id="9f7fc-116">Podle konvence c# `PascalCase` programy používají pro názvy typů, obory názvů a všechny veřejné členy.</span><span class="sxs-lookup"><span data-stu-id="9f7fc-116">By convention, C# programs use `PascalCase` for type names, namespaces, and all public members.</span></span> <span data-ttu-id="9f7fc-117">Kromě toho jsou společné následující konvence:</span><span class="sxs-lookup"><span data-stu-id="9f7fc-117">In addition, the following conventions are common:</span></span>

- <span data-ttu-id="9f7fc-118">Názvy rozhraní začínají `I`velkým písmenem .</span><span class="sxs-lookup"><span data-stu-id="9f7fc-118">Interface names start with a capital `I`.</span></span>
- <span data-ttu-id="9f7fc-119">Typy atributů končí `Attribute`slovem .</span><span class="sxs-lookup"><span data-stu-id="9f7fc-119">Attribute types end with the word `Attribute`.</span></span>
- <span data-ttu-id="9f7fc-120">Typy výčtu používají jednotné ho nitkového označení pro nepříznaky a množné číslo pro příznaky.</span><span class="sxs-lookup"><span data-stu-id="9f7fc-120">Enum types use a singular noun for non-flags, and a plural noun for flags.</span></span>
- <span data-ttu-id="9f7fc-121">Identifikátory by neměly `_` obsahovat dva po sobě jdoucí znaky.</span><span class="sxs-lookup"><span data-stu-id="9f7fc-121">Identifiers should not contain two consecutive `_` characters.</span></span> <span data-ttu-id="9f7fc-122">Tyto názvy jsou vyhrazeny pro identifikátory generované kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="9f7fc-122">Those names are reserved for compiler generated identifiers.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9f7fc-123">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9f7fc-123">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9f7fc-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="9f7fc-124">See also</span></span>

- [<span data-ttu-id="9f7fc-125">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9f7fc-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9f7fc-126">V programu v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="9f7fc-126">Inside a C# Program</span></span>](./index.md)
- [<span data-ttu-id="9f7fc-127">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9f7fc-127">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="9f7fc-128">Třídy</span><span class="sxs-lookup"><span data-stu-id="9f7fc-128">Classes</span></span>](../classes-and-structs/classes.md)
- [<span data-ttu-id="9f7fc-129">Typy struktur</span><span class="sxs-lookup"><span data-stu-id="9f7fc-129">Structure types</span></span>](../../language-reference/builtin-types/struct.md)
- [<span data-ttu-id="9f7fc-130">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="9f7fc-130">Namespaces</span></span>](../namespaces/index.md)
- [<span data-ttu-id="9f7fc-131">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="9f7fc-131">Interfaces</span></span>](../interfaces/index.md)
- [<span data-ttu-id="9f7fc-132">Delegáty</span><span class="sxs-lookup"><span data-stu-id="9f7fc-132">Delegates</span></span>](../delegates/index.md)
