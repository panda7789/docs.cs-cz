---
title: Zkontrolováno a nezkontrolováno - C# odkaz
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: a3b1ef8e6d8e496eda74ab25b3fe17f8174bac11
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713721"
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="dc997-102">Zaškrtnuto a nezaškrtnuto (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="dc997-102">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="dc997-103">C#příkazy mohou být provedeny v kontrolovaném nebo nezaškrtnutém kontextu.</span><span class="sxs-lookup"><span data-stu-id="dc997-103">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="dc997-104">V kontrolovaném kontextu přetečení aritmetického přetečení vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="dc997-104">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="dc997-105">V nekontrolovaném kontextu se aritmetické přetečení ignoruje a výsledek se zkrátí tak, že zahodí jakékoli bity s vysokým pořadím, které se nevejdou do cílového typu.</span><span class="sxs-lookup"><span data-stu-id="dc997-105">In an unchecked context, arithmetic overflow is ignored and the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>  
  
- <span data-ttu-id="dc997-106">[zaškrtnuté políčko](checked.md) Zadejte kontrolovaný kontext.</span><span class="sxs-lookup"><span data-stu-id="dc997-106">[checked](checked.md) Specify checked context.</span></span>  
  
- <span data-ttu-id="dc997-107">[nezaškrtnuto](unchecked.md) Zadejte nezaškrtnutý kontext.</span><span class="sxs-lookup"><span data-stu-id="dc997-107">[unchecked](unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="dc997-108">Kontrola přetečení má vliv na následující operace:</span><span class="sxs-lookup"><span data-stu-id="dc997-108">The following operations are affected by the overflow checking:</span></span>  
  
- <span data-ttu-id="dc997-109">Výrazy s použitím následujících předdefinovaných operátorů pro celočíselné typy:</span><span class="sxs-lookup"><span data-stu-id="dc997-109">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="dc997-110">`++`, `--`, unární `-`, `+`, `-`, `*`, `/`</span><span class="sxs-lookup"><span data-stu-id="dc997-110">`++`, `--`, unary `-`, `+`, `-`, `*`, `/`</span></span>  
  
- <span data-ttu-id="dc997-111">Explicitní číselné převody mezi celočíselnými typy nebo z `float` nebo `double` na celočíselný typ.</span><span class="sxs-lookup"><span data-stu-id="dc997-111">Explicit numeric conversions between integral types, or from `float` or `double` to an integral type.</span></span>  
  
 <span data-ttu-id="dc997-112">Pokud není zadána žádná `checked` ani `unchecked`, výchozí kontext pro nekonstantní výrazy (výrazy, které jsou vyhodnocovány za běhu) je definován hodnotou možnosti kompilátoru [zaškrtnuto](../compiler-options/checked-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="dc997-112">If neither `checked` nor `unchecked` is specified, the default context for non-constant expressions (expressions that are evaluated at run time) is defined by the value of the [-checked](../compiler-options/checked-compiler-option.md) compiler option.</span></span> <span data-ttu-id="dc997-113">Ve výchozím nastavení je hodnota této možnosti nastavená na hodnotu zrušit a aritmetické operace jsou spouštěny v nekontrolovaném kontextu.</span><span class="sxs-lookup"><span data-stu-id="dc997-113">By default the value of that option is unset and arithmetic operations are executed in an unchecked context.</span></span>
 
 <span data-ttu-id="dc997-114">V případě konstantních výrazů (výrazy, které mohou být plně vyhodnocovány v době kompilace) je výchozí kontext vždy zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="dc997-114">For constant expressions (expressions that can be fully evaluated at compile time), the default context is always checked.</span></span> <span data-ttu-id="dc997-115">Pokud není konstantní výraz explicitně umístěn v nekontrolovaném kontextu, přetečení, ke kterým dojde během kompilace výrazu, způsobují chyby při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="dc997-115">Unless a constant expression is explicitly placed in an unchecked context, overflows that occur during the compile-time evaluation of the expression cause compile-time errors.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="dc997-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dc997-116">See also</span></span>

- [<span data-ttu-id="dc997-117">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="dc997-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="dc997-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="dc997-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="dc997-119">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="dc997-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="dc997-120">Klíčová slova příkazů</span><span class="sxs-lookup"><span data-stu-id="dc997-120">Statement Keywords</span></span>](statement-keywords.md)
