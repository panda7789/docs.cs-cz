---
title: Zaškrtnuto a nezaškrtnuto - C# odkaz
ms.custom: seodec18
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: ba4ddd7fa87eb200de0de3aea6f0bc056a40f0e5
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235800"
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="a3584-102">Zaškrtnuto a nezaškrtnuto (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="a3584-102">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="a3584-103">Příkazy jazyka C# lze spustit v kontextu zaškrtnuté nebo nezaškrtnuté.</span><span class="sxs-lookup"><span data-stu-id="a3584-103">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="a3584-104">Aritmetické přetečení ve zkontrolovaném kontextu, vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="a3584-104">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="a3584-105">V nekontrolovaném kontextu je ignorován Přetečení aritmetické operace a výsledek je rozdělená do se zahodí všechny bity nejvyšším, které se nehodí do cílového typu.</span><span class="sxs-lookup"><span data-stu-id="a3584-105">In an unchecked context, arithmetic overflow is ignored and the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>  
  
-   <span data-ttu-id="a3584-106">[checked](checked.md) kontextu zadejte zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="a3584-106">[checked](checked.md) Specify checked context.</span></span>  
  
-   <span data-ttu-id="a3584-107">[unchecked](unchecked.md) zadejte nezkontrolovaném kontextu.</span><span class="sxs-lookup"><span data-stu-id="a3584-107">[unchecked](unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="a3584-108">Tyto operace jsou ovlivněny kontrola přetečení:</span><span class="sxs-lookup"><span data-stu-id="a3584-108">The following operations are affected by the overflow checking:</span></span>  
  
-   <span data-ttu-id="a3584-109">Pomocí následující předdefinované operátory na integrální typy výrazů:</span><span class="sxs-lookup"><span data-stu-id="a3584-109">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="a3584-110">`++`, `--`, unární `-`, `+`, `-`, `*`, `/`</span><span class="sxs-lookup"><span data-stu-id="a3584-110">`++`, `--`, unary `-`, `+`, `-`, `*`, `/`</span></span>  
  
-   <span data-ttu-id="a3584-111">Explicitní číselné převody mezi celočíselnými typy nebo z `float` nebo `double` na celočíselný typ.</span><span class="sxs-lookup"><span data-stu-id="a3584-111">Explicit numeric conversions between integral types, or from `float` or `double` to an integral type.</span></span>  
  
 <span data-ttu-id="a3584-112">Pokud ani `checked` ani `unchecked` není zadán, výchozí kontext pro výrazy nekonstantní (výrazy, které jsou vyhodnocovány v době běhu) je definován hodnotou [-checked](../compiler-options/checked-compiler-option.md) – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="a3584-112">If neither `checked` nor `unchecked` is specified, the default context for non-constant expressions (expressions that are evaluated at run time) is defined by the value of the [-checked](../compiler-options/checked-compiler-option.md) compiler option.</span></span> <span data-ttu-id="a3584-113">Ve výchozím nastavení má tato možnost hodnotu unset a aritmetické operace jsou provedeny v nekontrolovaném kontextu.</span><span class="sxs-lookup"><span data-stu-id="a3584-113">By default the value of that option is unset and arithmetic operations are executed in an unchecked context.</span></span>
 
 <span data-ttu-id="a3584-114">Pro konstantní výrazy (výrazy, které může být plně vyhodnocen v době kompilace) je vždy zaškrtnuto výchozí kontext.</span><span class="sxs-lookup"><span data-stu-id="a3584-114">For constant expressions (expressions that can be fully evaluated at compile time), the default context is always checked.</span></span> <span data-ttu-id="a3584-115">Pokud není konstantní výraz je explicitně umístěné v nekontrolovaném kontextu, přetečení, ke kterým dochází při vyhodnocení za kompilace výrazu způsobit chyby kompilace.</span><span class="sxs-lookup"><span data-stu-id="a3584-115">Unless a constant expression is explicitly placed in an unchecked context, overflows that occur during the compile-time evaluation of the expression cause compile-time errors.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a3584-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="a3584-116">See Also</span></span>  

- [<span data-ttu-id="a3584-117">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a3584-117">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="a3584-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="a3584-118">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="a3584-119">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a3584-119">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="a3584-120">Klíčová slova příkazů</span><span class="sxs-lookup"><span data-stu-id="a3584-120">Statement Keywords</span></span>](statement-keywords.md)
