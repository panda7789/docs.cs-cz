---
title: "#<a name=\"if-c-reference\"></a>Pokud (referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#if'
helpviewer_keywords: '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e4e3b79f64f5190d48d7248726ecdf031ad685e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="if-c-reference"></a><span data-ttu-id="ae03b-102">#if (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ae03b-102">#if (C# Reference)</span></span>
<span data-ttu-id="ae03b-103">Když se zaznamená kompilátor jazyka C# `#if` – direktiva, a nakonec pomocí [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) direktivy, ji budou zkompilovat kód mezi direktivy pouze v případě, že je definován zadaný symbol.</span><span class="sxs-lookup"><span data-stu-id="ae03b-103">When the C# compiler encounters an `#if` directive, followed eventually by an [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) directive, it will compile the code between the directives only if the specified symbol is defined.</span></span>  <span data-ttu-id="ae03b-104">Na rozdíl od C a C++ nelze přiřadit číselnou hodnotu na symbol; příkaz #if v jazyce C# je logická hodnota a pouze testuje, zda je symbol byla definována nebo ne.</span><span class="sxs-lookup"><span data-stu-id="ae03b-104">Unlike C and C++, you cannot assign a numeric value to a symbol; the #if statement in C# is Boolean and only tests whether the symbol has been defined or not.</span></span> <span data-ttu-id="ae03b-105">Například</span><span class="sxs-lookup"><span data-stu-id="ae03b-105">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
 <span data-ttu-id="ae03b-106">Můžete použít operátory [ == ](../../../csharp/language-reference/operators/equality-comparison-operator.md) (rovnosti), [! =](../../../csharp/language-reference/operators/not-equal-operator.md) (nerovnost) pouze k testování pro [true](../../../csharp/language-reference/keywords/true.md) nebo [false](../../../csharp/language-reference/keywords/false.md) .</span><span class="sxs-lookup"><span data-stu-id="ae03b-106">You can use the operators [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) (equality), [!=](../../../csharp/language-reference/operators/not-equal-operator.md) (inequality) only to test for [true](../../../csharp/language-reference/keywords/true.md) or [false](../../../csharp/language-reference/keywords/false.md) .</span></span> <span data-ttu-id="ae03b-107">Hodnota TRUE znamená, že je definována symbolu.</span><span class="sxs-lookup"><span data-stu-id="ae03b-107">True means the symbol is defined.</span></span> <span data-ttu-id="ae03b-108">Příkaz `#if DEBUG` stejný význam jako `#if (DEBUG == true)`.</span><span class="sxs-lookup"><span data-stu-id="ae03b-108">The statement `#if DEBUG` has the same meaning as `#if (DEBUG == true)`.</span></span> <span data-ttu-id="ae03b-109">Můžete použít operátory [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) (a), [&#124; &#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) (nebo), a [!](../../../csharp/language-reference/operators/logical-negation-operator.md)</span><span class="sxs-lookup"><span data-stu-id="ae03b-109">You can use the operators [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) (and), [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) (or), and [!](../../../csharp/language-reference/operators/logical-negation-operator.md)</span></span> <span data-ttu-id="ae03b-110">(ne) k vyhodnocení, zda byly definovány více symbolů.</span><span class="sxs-lookup"><span data-stu-id="ae03b-110">(not) to evaluate whether multiple symbols have been defined.</span></span> <span data-ttu-id="ae03b-111">Symboly a operátory je také možné seskupovat pomocí závorek.</span><span class="sxs-lookup"><span data-stu-id="ae03b-111">You can also group symbols and operators with parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae03b-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ae03b-112">Remarks</span></span>  
 <span data-ttu-id="ae03b-113">`#if`, spolu s [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md), [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md), a [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) direktivy, vám umožní zahrnout nebo vyloučit kódu na základě existence jeden nebo více symbolů.</span><span class="sxs-lookup"><span data-stu-id="ae03b-113">`#if`, along with the [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md), [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md), and [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) directives, lets you include or exclude code based on the existence of one or more symbols.</span></span> <span data-ttu-id="ae03b-114">To může být užitečné při kompilaci kódu pro sestavení ladicí verze, nebo při kompilaci pro konkrétní konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="ae03b-114">This can be useful when compiling code for a debug build or when compiling for a specific configuration.</span></span>  
  
 <span data-ttu-id="ae03b-115">Podmíněné direktivy od verze `#if` – direktiva musí být explicitně ukončena s `#endif` – direktiva.</span><span class="sxs-lookup"><span data-stu-id="ae03b-115">A conditional directive beginning with a `#if` directive must explicitly be terminated with a `#endif` directive.</span></span>  
  
 <span data-ttu-id="ae03b-116">`#define`Umožňuje definovat symbol, tak, aby pomocí symbolu jako výraz předaný `#if` direktivy, výraz vyhodnotí jako `true`.</span><span class="sxs-lookup"><span data-stu-id="ae03b-116">`#define` lets you define a symbol, such that, by using the symbol as the expression passed to the `#if` directive, the expression will evaluate to `true`.</span></span>  
  
 <span data-ttu-id="ae03b-117">Můžete také definovat symbol s [/ define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="ae03b-117">You can also define a symbol with the [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="ae03b-118">Můžete nedefinované symbol s [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="ae03b-118">You can undefine a symbol with [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span></span>  
  
 <span data-ttu-id="ae03b-119">Symbol, který definujete s `/define` nebo s `#define` není v konfliktu s proměnné se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="ae03b-119">A symbol that you define with `/define` or with `#define` does not conflict with a variable of the same name.</span></span> <span data-ttu-id="ae03b-120">To znamená název proměnné nesmí být předaný direktivy preprocesoru a symbol lze vyhodnotit pouze direktivy preprocesoru.</span><span class="sxs-lookup"><span data-stu-id="ae03b-120">That is, a variable name should not be passed to a preprocessor directive and a symbol can only be evaluated by a preprocessor directive.</span></span>  
  
 <span data-ttu-id="ae03b-121">Rozsah symbol vytvořené pomocí `#define` je soubor, ve které byla definována.</span><span class="sxs-lookup"><span data-stu-id="ae03b-121">The scope of a symbol created with `#define` is the file in which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae03b-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="ae03b-122">Example</span></span>  
  
```csharp
// preprocessor_if.cs  
#define DEBUG
#define MYTEST  
using System;  
public class MyClass   
{  
    static void Main()   
    {  
#if (DEBUG && !MYTEST)  
        Console.WriteLine("DEBUG is defined");  
#elif (!DEBUG && MYTEST)  
        Console.WriteLine("MYTEST is defined");  
#elif (DEBUG && MYTEST)  
        Console.WriteLine("DEBUG and MYTEST are defined");  
#else  
        Console.WriteLine("DEBUG and MYTEST are not defined");  
#endif  
    }  
}  
```  
  
 <span data-ttu-id="ae03b-123">**Jsou definovány ladění a test**</span><span class="sxs-lookup"><span data-stu-id="ae03b-123">**DEBUG and MYTEST are defined**</span></span>  
## <a name="see-also"></a><span data-ttu-id="ae03b-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="ae03b-124">See Also</span></span>  
 [<span data-ttu-id="ae03b-125">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ae03b-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ae03b-126">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="ae03b-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ae03b-127">C# direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="ae03b-127">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
