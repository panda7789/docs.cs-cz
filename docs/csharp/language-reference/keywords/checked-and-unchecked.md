---
title: Zaškrtnuto a nezaškrtnuto - odkaz jazyka C#
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: 8ee4c481a30dce30029fbe8cc26f4798b523a7ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173637"
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="03173-102">Zaškrtnuto a nezaškrtnuto (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="03173-102">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="03173-103">Příkazy jazyka C# lze spustit v zadávaného nebo nekontrolovaném kontextu.</span><span class="sxs-lookup"><span data-stu-id="03173-103">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="03173-104">V kontrolovaném kontextu aritmetické přetečení vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="03173-104">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="03173-105">V nekontrolovaném kontextu je aritmetické přetečení ignorováno a výsledek je zkrácen zahozením všech bitů vyššího řádu, které se nevejdou do cílového typu.</span><span class="sxs-lookup"><span data-stu-id="03173-105">In an unchecked context, arithmetic overflow is ignored and the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>  
  
- <span data-ttu-id="03173-106">[zaškrtnuto](checked.md) Zadejte kontrolovaný kontext.</span><span class="sxs-lookup"><span data-stu-id="03173-106">[checked](checked.md) Specify checked context.</span></span>  
  
- <span data-ttu-id="03173-107">[nezaškrtnuté políčko](unchecked.md) Zadejte nezaškrtnutý kontext.</span><span class="sxs-lookup"><span data-stu-id="03173-107">[unchecked](unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="03173-108">Kontrola přetečení ovlivňuje následující operace:</span><span class="sxs-lookup"><span data-stu-id="03173-108">The following operations are affected by the overflow checking:</span></span>  
  
- <span data-ttu-id="03173-109">Výrazy používající následující předdefinované operátory na integrálních typech:</span><span class="sxs-lookup"><span data-stu-id="03173-109">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="03173-110">`++`, `--`, `-`unární `-` `*`, `+`, ,`/`</span><span class="sxs-lookup"><span data-stu-id="03173-110">`++`, `--`, unary `-`, `+`, `-`, `*`, `/`</span></span>  
  
- <span data-ttu-id="03173-111">Explicitní číselné převody mezi `float` integrální typy nebo z nebo `double` integrální typu.</span><span class="sxs-lookup"><span data-stu-id="03173-111">Explicit numeric conversions between integral types, or from `float` or `double` to an integral type.</span></span>  
  
 <span data-ttu-id="03173-112">Pokud ani `checked` `unchecked` není zadán, výchozí kontext pro nekonstantní výrazy (výrazy, které jsou vyhodnocovány za běhu) je definován hodnotou [-checked](../compiler-options/checked-compiler-option.md) kompilátoru možnost.</span><span class="sxs-lookup"><span data-stu-id="03173-112">If neither `checked` nor `unchecked` is specified, the default context for non-constant expressions (expressions that are evaluated at run time) is defined by the value of the [-checked](../compiler-options/checked-compiler-option.md) compiler option.</span></span> <span data-ttu-id="03173-113">Ve výchozím nastavení je hodnota této možnosti unset a aritmetické operace jsou prováděny v nekontrolovaném kontextu.</span><span class="sxs-lookup"><span data-stu-id="03173-113">By default the value of that option is unset and arithmetic operations are executed in an unchecked context.</span></span>

 <span data-ttu-id="03173-114">Pro konstantní výrazy (výrazy, které lze plně vyhodnotit v době kompilace), výchozí kontext je vždy kontrolována.</span><span class="sxs-lookup"><span data-stu-id="03173-114">For constant expressions (expressions that can be fully evaluated at compile time), the default context is always checked.</span></span> <span data-ttu-id="03173-115">Pokud konstantní výraz je explicitně umístěn v nekontrolovaném kontextu, přetečení, ke kterým dochází během vyhodnocení výrazu v době kompilace způsobit chyby kompilace.</span><span class="sxs-lookup"><span data-stu-id="03173-115">Unless a constant expression is explicitly placed in an unchecked context, overflows that occur during the compile-time evaluation of the expression cause compile-time errors.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="03173-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="03173-116">See also</span></span>

- [<span data-ttu-id="03173-117">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="03173-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="03173-118">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="03173-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="03173-119">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="03173-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="03173-120">Klíčová slova příkazů</span><span class="sxs-lookup"><span data-stu-id="03173-120">Statement Keywords</span></span>](statement-keywords.md)
