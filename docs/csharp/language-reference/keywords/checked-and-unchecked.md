---
description: Zaškrtnuté a nezaškrtnuté – referenční informace jazyka C#
title: Zaškrtnuté a nezaškrtnuté – referenční informace jazyka C#
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: a8d6a26e28062da682689bf64a9e38ea5fd158b2
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138264"
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="4e51b-103">Zaškrtnuto a nezaškrtnuto (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="4e51b-103">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="4e51b-104">Příkazy jazyka C# mohou být provedeny buď v kontrolovaném, nebo nezaškrtnutém kontextu.</span><span class="sxs-lookup"><span data-stu-id="4e51b-104">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="4e51b-105">V kontrolovaném kontextu přetečení aritmetického přetečení vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="4e51b-105">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="4e51b-106">V nekontrolovaném kontextu se aritmetické přetečení ignoruje a výsledek se zkrátí tak, že zahodí jakékoli bity s vysokým pořadím, které se nevejdou do cílového typu.</span><span class="sxs-lookup"><span data-stu-id="4e51b-106">In an unchecked context, arithmetic overflow is ignored and the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>  
  
- <span data-ttu-id="4e51b-107">[zaškrtnuté políčko](checked.md) Zadejte kontrolovaný kontext.</span><span class="sxs-lookup"><span data-stu-id="4e51b-107">[checked](checked.md) Specify checked context.</span></span>  
  
- <span data-ttu-id="4e51b-108">[nezaškrtnuto](unchecked.md) Zadejte nezaškrtnutý kontext.</span><span class="sxs-lookup"><span data-stu-id="4e51b-108">[unchecked](unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="4e51b-109">Kontrola přetečení má vliv na následující operace:</span><span class="sxs-lookup"><span data-stu-id="4e51b-109">The following operations are affected by the overflow checking:</span></span>  
  
- <span data-ttu-id="4e51b-110">Výrazy s použitím následujících předdefinovaných operátorů pro celočíselné typy:</span><span class="sxs-lookup"><span data-stu-id="4e51b-110">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="4e51b-111">`++`, `--` , unární `-` , `+` , `-` , `*` , `/`</span><span class="sxs-lookup"><span data-stu-id="4e51b-111">`++`, `--`, unary `-`, `+`, `-`, `*`, `/`</span></span>  
  
- <span data-ttu-id="4e51b-112">Explicitní číselné převody mezi celočíselnými typy nebo z `float` nebo `double` na celočíselný typ.</span><span class="sxs-lookup"><span data-stu-id="4e51b-112">Explicit numeric conversions between integral types, or from `float` or `double` to an integral type.</span></span>  
  
 <span data-ttu-id="4e51b-113">Pokud ani `checked` `unchecked` není zadán, výchozí kontext pro nekonstantní výrazy (výrazy, které jsou vyhodnocovány za běhu), je definována hodnotou možnosti kompilátoru [-checked](../compiler-options/checked-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="4e51b-113">If neither `checked` nor `unchecked` is specified, the default context for non-constant expressions (expressions that are evaluated at run time) is defined by the value of the [-checked](../compiler-options/checked-compiler-option.md) compiler option.</span></span> <span data-ttu-id="4e51b-114">Ve výchozím nastavení je hodnota této možnosti nastavená na hodnotu zrušit a aritmetické operace jsou spouštěny v nekontrolovaném kontextu.</span><span class="sxs-lookup"><span data-stu-id="4e51b-114">By default the value of that option is unset and arithmetic operations are executed in an unchecked context.</span></span>

 <span data-ttu-id="4e51b-115">V případě konstantních výrazů (výrazy, které mohou být plně vyhodnocovány v době kompilace) je výchozí kontext vždy zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="4e51b-115">For constant expressions (expressions that can be fully evaluated at compile time), the default context is always checked.</span></span> <span data-ttu-id="4e51b-116">Pokud není konstantní výraz explicitně umístěn v nekontrolovaném kontextu, přetečení, ke kterým dojde během kompilace výrazu, způsobují chyby při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="4e51b-116">Unless a constant expression is explicitly placed in an unchecked context, overflows that occur during the compile-time evaluation of the expression cause compile-time errors.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4e51b-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="4e51b-117">See also</span></span>

- [<span data-ttu-id="4e51b-118">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4e51b-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4e51b-119">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="4e51b-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4e51b-120">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4e51b-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="4e51b-121">Klíčová slova příkazů</span><span class="sxs-lookup"><span data-stu-id="4e51b-121">Statement Keywords</span></span>](statement-keywords.md)
