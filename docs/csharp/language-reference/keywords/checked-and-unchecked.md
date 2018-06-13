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
ms.openlocfilehash: f8e292a67fab49b5fc3616e438d063eca2617274
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34234370"
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="8364a-102">Zaškrtnuto a nezaškrtnuto (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="8364a-102">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="8364a-103">Příkazy jazyka C# můžete spustit v kontextu zaškrtnuté nebo nezaškrtnuté.</span><span class="sxs-lookup"><span data-stu-id="8364a-103">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="8364a-104">V kontextu zaškrtnuté Přetečení aritmetické funkce vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="8364a-104">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="8364a-105">V kontextu nezaškrtnuté aritmetického přetečení je ignorován a výsledek je rozdělená do zahození žádné nejvyšších bitů, které se nehodí typu cílového.</span><span class="sxs-lookup"><span data-stu-id="8364a-105">In an unchecked context, arithmetic overflow is ignored and the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>  
  
-   <span data-ttu-id="8364a-106">[zaškrtnutí](checked.md) zadejte zaškrtnutí kontextu.</span><span class="sxs-lookup"><span data-stu-id="8364a-106">[checked](checked.md) Specify checked context.</span></span>  
  
-   <span data-ttu-id="8364a-107">[nezaškrtnuté](unchecked.md) zadejte nezaškrtnuté kontextu.</span><span class="sxs-lookup"><span data-stu-id="8364a-107">[unchecked](unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="8364a-108">Kontrola přetečení se týká následující operace:</span><span class="sxs-lookup"><span data-stu-id="8364a-108">The following operations are affected by the overflow checking:</span></span>  
  
-   <span data-ttu-id="8364a-109">Pomocí následující předdefinované operátory na integrální typy výrazů:</span><span class="sxs-lookup"><span data-stu-id="8364a-109">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="8364a-110">`++`, `--`, unární `-`, `+`, `-`, `*`, `/`</span><span class="sxs-lookup"><span data-stu-id="8364a-110">`++`, `--`, unary `-`, `+`, `-`, `*`, `/`</span></span>  
  
-   <span data-ttu-id="8364a-111">Explicitní číselné převody mezi celočíselných typů, nebo z `float` nebo `double` integrální typu.</span><span class="sxs-lookup"><span data-stu-id="8364a-111">Explicit numeric conversions between integral types, or from `float` or `double` to an integral type.</span></span>  
  
 <span data-ttu-id="8364a-112">Pokud ani `checked` ani `unchecked` je zadána výchozí kontext není konstantní výrazy (výrazy, které jsou vyhodnocovány v době běhu) je definován hodnotou [-zaškrtnutí](../compiler-options/checked-compiler-option.md) – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="8364a-112">If neither `checked` nor `unchecked` is specified, the default context for non-constant expressions (expressions that are evaluated at run time) is defined by the value of the [-checked](../compiler-options/checked-compiler-option.md) compiler option.</span></span> <span data-ttu-id="8364a-113">Ve výchozím nastavení je hodnota tuto možnost nastavení a aritmetické operace jsou spouštěny v kontextu není zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="8364a-113">By default the value of that option is unset and arithmetic operations are executed in an unchecked context.</span></span>
 
 <span data-ttu-id="8364a-114">Pro konstantní výrazy (výrazy, které se dají posoudit plně v době kompilace) je vždy zaškrtnuto výchozí kontext.</span><span class="sxs-lookup"><span data-stu-id="8364a-114">For constant expressions (expressions that can be fully evaluated at compile time), the default context is always checked.</span></span> <span data-ttu-id="8364a-115">Pokud konstantní výraz je explicitně umístěn v kontextu není zaškrtnuto, některé, ke kterým došlo během kompilace vyhodnocování výrazu způsobit chyby při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="8364a-115">Unless a constant expression is explicitly placed in an unchecked context, overflows that occur during the compile-time evaluation of the expression cause compile-time errors.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8364a-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="8364a-116">See Also</span></span>  
 [<span data-ttu-id="8364a-117">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8364a-117">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="8364a-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8364a-118">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="8364a-119">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8364a-119">C# Keywords</span></span>](index.md)  
 [<span data-ttu-id="8364a-120">Klíčová slova příkazů</span><span class="sxs-lookup"><span data-stu-id="8364a-120">Statement Keywords</span></span>](statement-keywords.md)
