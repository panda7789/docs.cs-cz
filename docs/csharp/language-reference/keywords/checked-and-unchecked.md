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
ms.openlocfilehash: 3378cffc1dcee7bb12705704e66b7fdd287105fb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592995"
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="e0637-102">Zaškrtnuto a nezaškrtnuto (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e0637-102">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="e0637-103">Příkazy jazyka C# lze spustit v kontextu zaškrtnuté nebo nezaškrtnuté.</span><span class="sxs-lookup"><span data-stu-id="e0637-103">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="e0637-104">Aritmetické přetečení ve zkontrolovaném kontextu, vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="e0637-104">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="e0637-105">V nekontrolovaném kontextu je ignorován Přetečení aritmetické operace a výsledek je rozdělená do se zahodí všechny bity nejvyšším, které se nehodí do cílového typu.</span><span class="sxs-lookup"><span data-stu-id="e0637-105">In an unchecked context, arithmetic overflow is ignored and the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>  
  
- <span data-ttu-id="e0637-106">[checked](checked.md) kontextu zadejte zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="e0637-106">[checked](checked.md) Specify checked context.</span></span>  
  
- <span data-ttu-id="e0637-107">[unchecked](unchecked.md) zadejte nezkontrolovaném kontextu.</span><span class="sxs-lookup"><span data-stu-id="e0637-107">[unchecked](unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="e0637-108">Tyto operace jsou ovlivněny kontrola přetečení:</span><span class="sxs-lookup"><span data-stu-id="e0637-108">The following operations are affected by the overflow checking:</span></span>  
  
- <span data-ttu-id="e0637-109">Pomocí následující předdefinované operátory na integrální typy výrazů:</span><span class="sxs-lookup"><span data-stu-id="e0637-109">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="e0637-110">`++`, `--`, unární `-`, `+`, `-`, `*`, `/`</span><span class="sxs-lookup"><span data-stu-id="e0637-110">`++`, `--`, unary `-`, `+`, `-`, `*`, `/`</span></span>  
  
- <span data-ttu-id="e0637-111">Explicitní číselné převody mezi celočíselnými typy nebo z `float` nebo `double` na celočíselný typ.</span><span class="sxs-lookup"><span data-stu-id="e0637-111">Explicit numeric conversions between integral types, or from `float` or `double` to an integral type.</span></span>  
  
 <span data-ttu-id="e0637-112">Pokud ani `checked` ani `unchecked` není zadán, výchozí kontext pro výrazy nekonstantní (výrazy, které jsou vyhodnocovány v době běhu) je definován hodnotou [-checked](../compiler-options/checked-compiler-option.md) – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="e0637-112">If neither `checked` nor `unchecked` is specified, the default context for non-constant expressions (expressions that are evaluated at run time) is defined by the value of the [-checked](../compiler-options/checked-compiler-option.md) compiler option.</span></span> <span data-ttu-id="e0637-113">Ve výchozím nastavení má tato možnost hodnotu unset a aritmetické operace jsou provedeny v nekontrolovaném kontextu.</span><span class="sxs-lookup"><span data-stu-id="e0637-113">By default the value of that option is unset and arithmetic operations are executed in an unchecked context.</span></span>
 
 <span data-ttu-id="e0637-114">Pro konstantní výrazy (výrazy, které může být plně vyhodnocen v době kompilace) je vždy zaškrtnuto výchozí kontext.</span><span class="sxs-lookup"><span data-stu-id="e0637-114">For constant expressions (expressions that can be fully evaluated at compile time), the default context is always checked.</span></span> <span data-ttu-id="e0637-115">Pokud není konstantní výraz je explicitně umístěné v nekontrolovaném kontextu, přetečení, ke kterým dochází při vyhodnocení za kompilace výrazu způsobit chyby kompilace.</span><span class="sxs-lookup"><span data-stu-id="e0637-115">Unless a constant expression is explicitly placed in an unchecked context, overflows that occur during the compile-time evaluation of the expression cause compile-time errors.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e0637-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e0637-116">See also</span></span>

- [<span data-ttu-id="e0637-117">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e0637-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e0637-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e0637-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e0637-119">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e0637-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="e0637-120">Klíčová slova příkazů</span><span class="sxs-lookup"><span data-stu-id="e0637-120">Statement Keywords</span></span>](statement-keywords.md)
