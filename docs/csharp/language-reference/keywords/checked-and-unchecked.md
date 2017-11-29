---
title: "Zaškrtnuto a nezaškrtnuto (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4b7b18b39dbfa7ed0818d9ea6e9e62ef79a9f5b7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="02db2-102">Zaškrtnuto a nezaškrtnuto (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="02db2-102">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="02db2-103">Příkazy jazyka C# můžete spustit v kontextu zaškrtnuté nebo nezaškrtnuté.</span><span class="sxs-lookup"><span data-stu-id="02db2-103">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="02db2-104">V kontextu zaškrtnuté Přetečení aritmetické funkce vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="02db2-104">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="02db2-105">V kontextu nezaškrtnuté aritmetického přetečení je ignorován a výsledek je oříznuta.</span><span class="sxs-lookup"><span data-stu-id="02db2-105">In an unchecked context, arithmetic overflow is ignored and the result is truncated.</span></span>  
  
-   <span data-ttu-id="02db2-106">[zaškrtnutí](../../../csharp/language-reference/keywords/checked.md) zadejte zaškrtnutí kontextu.</span><span class="sxs-lookup"><span data-stu-id="02db2-106">[checked](../../../csharp/language-reference/keywords/checked.md) Specify checked context.</span></span>  
  
-   <span data-ttu-id="02db2-107">[nezaškrtnuté](../../../csharp/language-reference/keywords/unchecked.md) zadejte nezaškrtnuté kontextu.</span><span class="sxs-lookup"><span data-stu-id="02db2-107">[unchecked](../../../csharp/language-reference/keywords/unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="02db2-108">Pokud ani `checked` ani `unchecked` je zadána výchozí kontext závisí na externí faktorech, například – možnosti kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="02db2-108">If neither `checked` nor `unchecked` is specified, the default context depends on external factors such as compiler options.</span></span>  
  
 <span data-ttu-id="02db2-109">Kontrola přetečení se týká následující operace:</span><span class="sxs-lookup"><span data-stu-id="02db2-109">The following operations are affected by the overflow checking:</span></span>  
  
-   <span data-ttu-id="02db2-110">Pomocí následující předdefinované operátory na integrální typy výrazů:</span><span class="sxs-lookup"><span data-stu-id="02db2-110">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="02db2-111">`++``--` -(unární) `+`  -    `*``/`</span><span class="sxs-lookup"><span data-stu-id="02db2-111">`++` `--` - (unary)   `+` -   `*` `/`</span></span>  
  
-   <span data-ttu-id="02db2-112">Explicitní číselné převody mezi integrální typy.</span><span class="sxs-lookup"><span data-stu-id="02db2-112">Explicit numeric conversions between integral types.</span></span>  
  
 <span data-ttu-id="02db2-113">[/ Checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md) – možnost kompilátoru umožňuje určit zaškrtnuté nebo nezaškrtnuté kontext pro všechny příkazy aritmetické celé číslo, které nejsou výslovně v oboru `checked` nebo `unchecked` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="02db2-113">The [/checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md) compiler option lets you specify checked or unchecked context for all integer arithmetic statements that are not explicitly in the scope of a `checked` or `unchecked` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02db2-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="02db2-114">See Also</span></span>  
 [<span data-ttu-id="02db2-115">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="02db2-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="02db2-116">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="02db2-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="02db2-117">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="02db2-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="02db2-118">Klíčová slova příkazů</span><span class="sxs-lookup"><span data-stu-id="02db2-118">Statement Keywords</span></span>](../../../csharp/language-reference/keywords/statement-keywords.md)
