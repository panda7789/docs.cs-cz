---
title: Zaškrtnuto a nezaškrtnuto (Referenční dokumentace jazyka C#)
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: 04f603905690497bcd4249f73c7296be2c269a60
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43741929"
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="51678-102">Zaškrtnuto a nezaškrtnuto (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="51678-102">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="51678-103">Příkazy jazyka C# lze spustit v kontextu zaškrtnuté nebo nezaškrtnuté.</span><span class="sxs-lookup"><span data-stu-id="51678-103">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="51678-104">Aritmetické přetečení ve zkontrolovaném kontextu, vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="51678-104">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="51678-105">V nekontrolovaném kontextu je ignorován Přetečení aritmetické operace a výsledek je rozdělená do se zahodí všechny bity nejvyšším, které se nehodí do cílového typu.</span><span class="sxs-lookup"><span data-stu-id="51678-105">In an unchecked context, arithmetic overflow is ignored and the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>  
  
-   <span data-ttu-id="51678-106">[checked](checked.md) kontextu zadejte zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="51678-106">[checked](checked.md) Specify checked context.</span></span>  
  
-   <span data-ttu-id="51678-107">[unchecked](unchecked.md) zadejte nezkontrolovaném kontextu.</span><span class="sxs-lookup"><span data-stu-id="51678-107">[unchecked](unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="51678-108">Tyto operace jsou ovlivněny kontrola přetečení:</span><span class="sxs-lookup"><span data-stu-id="51678-108">The following operations are affected by the overflow checking:</span></span>  
  
-   <span data-ttu-id="51678-109">Pomocí následující předdefinované operátory na integrální typy výrazů:</span><span class="sxs-lookup"><span data-stu-id="51678-109">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="51678-110">`++`, `--`, unární `-`, `+`, `-`, `*`, `/`</span><span class="sxs-lookup"><span data-stu-id="51678-110">`++`, `--`, unary `-`, `+`, `-`, `*`, `/`</span></span>  
  
-   <span data-ttu-id="51678-111">Explicitní číselné převody mezi celočíselnými typy nebo z `float` nebo `double` na celočíselný typ.</span><span class="sxs-lookup"><span data-stu-id="51678-111">Explicit numeric conversions between integral types, or from `float` or `double` to an integral type.</span></span>  
  
 <span data-ttu-id="51678-112">Pokud ani `checked` ani `unchecked` není zadán, výchozí kontext pro výrazy nekonstantní (výrazy, které jsou vyhodnocovány v době běhu) je definován hodnotou [-checked](../compiler-options/checked-compiler-option.md) – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="51678-112">If neither `checked` nor `unchecked` is specified, the default context for non-constant expressions (expressions that are evaluated at run time) is defined by the value of the [-checked](../compiler-options/checked-compiler-option.md) compiler option.</span></span> <span data-ttu-id="51678-113">Ve výchozím nastavení má tato možnost hodnotu unset a aritmetické operace jsou provedeny v nekontrolovaném kontextu.</span><span class="sxs-lookup"><span data-stu-id="51678-113">By default the value of that option is unset and arithmetic operations are executed in an unchecked context.</span></span>
 
 <span data-ttu-id="51678-114">Pro konstantní výrazy (výrazy, které může být plně vyhodnocen v době kompilace) je vždy zaškrtnuto výchozí kontext.</span><span class="sxs-lookup"><span data-stu-id="51678-114">For constant expressions (expressions that can be fully evaluated at compile time), the default context is always checked.</span></span> <span data-ttu-id="51678-115">Pokud není konstantní výraz je explicitně umístěné v nekontrolovaném kontextu, přetečení, ke kterým dochází při vyhodnocení za kompilace výrazu způsobit chyby kompilace.</span><span class="sxs-lookup"><span data-stu-id="51678-115">Unless a constant expression is explicitly placed in an unchecked context, overflows that occur during the compile-time evaluation of the expression cause compile-time errors.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="51678-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="51678-116">See Also</span></span>  

- [<span data-ttu-id="51678-117">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="51678-117">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="51678-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="51678-118">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="51678-119">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="51678-119">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="51678-120">Klíčová slova příkazů</span><span class="sxs-lookup"><span data-stu-id="51678-120">Statement Keywords</span></span>](statement-keywords.md)
