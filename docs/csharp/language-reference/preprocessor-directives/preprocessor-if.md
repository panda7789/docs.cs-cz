---
title: "#Pokud preprocesoru – direktiva (referenční dokumentace jazyka C#)"
ms.date: 02/13/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 710452d6fddea239cb2e65901fd5ce56d6be699f
ms.sourcegitcommit: 08684dd61444c2f072b89b926370f750e456fca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="if-c-reference"></a><span data-ttu-id="48bb1-102">#if (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="48bb1-102">#if (C# Reference)</span></span>

<span data-ttu-id="48bb1-103">Když se zaznamená kompilátor jazyka C# `#if` – direktiva, a nakonec pomocí [#endif](preprocessor-endif.md) direktivy, se zkompiluje kód mezi direktivy pouze v případě, že je definován zadaný symbol.</span><span class="sxs-lookup"><span data-stu-id="48bb1-103">When the C# compiler encounters an `#if` directive, followed eventually by an [#endif](preprocessor-endif.md) directive, it compiles the code between the directives only if the specified symbol is defined.</span></span> <span data-ttu-id="48bb1-104">Na rozdíl od C a C++ nelze přiřadit číselnou hodnotu symbol.</span><span class="sxs-lookup"><span data-stu-id="48bb1-104">Unlike C and C++, you cannot assign a numeric value to a symbol.</span></span> <span data-ttu-id="48bb1-105">Příkaz #if v jazyce C# je logická hodnota a pouze testuje, zda je symbol byla definována nebo ne.</span><span class="sxs-lookup"><span data-stu-id="48bb1-105">The #if statement in C# is Boolean and only tests whether the symbol has been defined or not.</span></span> <span data-ttu-id="48bb1-106">Příklad:</span><span class="sxs-lookup"><span data-stu-id="48bb1-106">For example:</span></span>

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

<span data-ttu-id="48bb1-107">Můžete použít operátory [ == ](../operators/equality-comparison-operator.md) (rovnosti) a [! =](../operators/not-equal-operator.md) (nerovnost) pouze k testování pro [true](../keywords/true.md) nebo [false](../keywords/false.md).</span><span class="sxs-lookup"><span data-stu-id="48bb1-107">You can use the operators [==](../operators/equality-comparison-operator.md) (equality) and [!=](../operators/not-equal-operator.md) (inequality) only to test for [true](../keywords/true.md) or [false](../keywords/false.md).</span></span> <span data-ttu-id="48bb1-108">Hodnota TRUE znamená, že je definována symbolu.</span><span class="sxs-lookup"><span data-stu-id="48bb1-108">True means the symbol is defined.</span></span> <span data-ttu-id="48bb1-109">Příkaz `#if DEBUG` stejný význam jako `#if (DEBUG == true)`.</span><span class="sxs-lookup"><span data-stu-id="48bb1-109">The statement `#if DEBUG` has the same meaning as `#if (DEBUG == true)`.</span></span> <span data-ttu-id="48bb1-110">Můžete použít operátory [ && ](../operators/conditional-and-operator.md) (a), [&#124; &#124;](../operators/conditional-or-operator.md) (nebo), a [!](../operators/logical-negation-operator.md)</span><span class="sxs-lookup"><span data-stu-id="48bb1-110">You can use the operators [&&](../operators/conditional-and-operator.md) (and), [&#124;&#124;](../operators/conditional-or-operator.md) (or), and [!](../operators/logical-negation-operator.md)</span></span> <span data-ttu-id="48bb1-111">(ne) k vyhodnocení, zda byly definovány více symbolů.</span><span class="sxs-lookup"><span data-stu-id="48bb1-111">(not) to evaluate whether multiple symbols have been defined.</span></span> <span data-ttu-id="48bb1-112">Symboly a operátory je také možné seskupovat pomocí závorek.</span><span class="sxs-lookup"><span data-stu-id="48bb1-112">You can also group symbols and operators with parentheses.</span></span>

## <a name="remarks"></a><span data-ttu-id="48bb1-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="48bb1-113">Remarks</span></span>

<span data-ttu-id="48bb1-114">`#if`, spolu s [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md), a [#undef](preprocessor-undef.md) direktivy, vám umožní zahrnout nebo vyloučit kódu na základě existence jeden nebo více symbolů.</span><span class="sxs-lookup"><span data-stu-id="48bb1-114">`#if`, along with the [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md), and [#undef](preprocessor-undef.md) directives, lets you include or exclude code based on the existence of one or more symbols.</span></span> <span data-ttu-id="48bb1-115">To může být užitečné při kompilaci kódu pro sestavení ladicí verze, nebo při kompilaci pro konkrétní konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="48bb1-115">This can be useful when compiling code for a debug build or when compiling for a specific configuration.</span></span>

<span data-ttu-id="48bb1-116">Podmíněné direktivy od verze `#if` – direktiva musí být explicitně ukončena s `#endif` – direktiva.</span><span class="sxs-lookup"><span data-stu-id="48bb1-116">A conditional directive beginning with a `#if` directive must explicitly be terminated with a `#endif` directive.</span></span>

<span data-ttu-id="48bb1-117">`#define` Umožňuje definovat symbol.</span><span class="sxs-lookup"><span data-stu-id="48bb1-117">`#define` lets you define a symbol.</span></span> <span data-ttu-id="48bb1-118">Potom pomocí symbolu jako výraz předaný `#if` direktivy, vyhodnocen jako `true`.</span><span class="sxs-lookup"><span data-stu-id="48bb1-118">By then using the symbol as the expression passed to the `#if` directive, the expression evaluates to `true`.</span></span>

<span data-ttu-id="48bb1-119">Můžete také definovat symbol s [/ define](../compiler-options/define-compiler-option.md) – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="48bb1-119">You can also define a symbol with the [/define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="48bb1-120">Můžete nedefinované symbol s [#undef](preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="48bb1-120">You can undefine a symbol with [#undef](preprocessor-undef.md).</span></span>

<span data-ttu-id="48bb1-121">Symbol, který definujete s `/define` nebo s `#define` není v konfliktu s proměnné se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="48bb1-121">A symbol that you define with `/define` or with `#define` doesn't conflict with a variable of the same name.</span></span> <span data-ttu-id="48bb1-122">To znamená název proměnné nesmí být předaný direktivy preprocesoru a symbol lze vyhodnotit pouze direktivy preprocesoru.</span><span class="sxs-lookup"><span data-stu-id="48bb1-122">That is, a variable name should not be passed to a preprocessor directive, and a symbol can only be evaluated by a preprocessor directive.</span></span>

<span data-ttu-id="48bb1-123">Rozsah symbol vytvořené pomocí `#define` je soubor, ve které byla definována.</span><span class="sxs-lookup"><span data-stu-id="48bb1-123">The scope of a symbol created with `#define` is the file in which it was defined.</span></span>

<span data-ttu-id="48bb1-124">Systém sestavení má také informace o předdefinovaných symbolů preprocesoru představující různé [cílové rozhraní](../../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="48bb1-124">The build system is also aware of predefined preprocessor symbols representing different [target frameworks](../../../standard/frameworks.md).</span></span> <span data-ttu-id="48bb1-125">Jsou užitečná při vytváření aplikace, které můžete vybrat víc než jeden implementace rozhraní .NET nebo verzi.</span><span class="sxs-lookup"><span data-stu-id="48bb1-125">They're useful when creating applications that can target more than one .NET implementation or version.</span></span>

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

<span data-ttu-id="48bb1-126">Jiné předdefinované symboly obsahovat konstanty pro ladění a trasování.</span><span class="sxs-lookup"><span data-stu-id="48bb1-126">Other predefined symbols include the DEBUG and TRACE constants.</span></span> <span data-ttu-id="48bb1-127">Můžete přepsat hodnoty nastavené pro projekt pomocí `#define`.</span><span class="sxs-lookup"><span data-stu-id="48bb1-127">You can override the values set for the project using `#define`.</span></span> <span data-ttu-id="48bb1-128">Symbol ladění, například bude automaticky nastavena v závislosti na vaší vlastnosti konfigurace sestavení (režim "Ladění" nebo "Verze").</span><span class="sxs-lookup"><span data-stu-id="48bb1-128">The DEBUG symbol, for example, is automatically set depending on your build configuration properties ("Debug" or "Release" mode).</span></span>

## <a name="examples"></a><span data-ttu-id="48bb1-129">Příklady</span><span class="sxs-lookup"><span data-stu-id="48bb1-129">Examples</span></span>

<span data-ttu-id="48bb1-130">Následující příklad ukazuje, jak definovat symbol test v souboru a poté otestujte hodnoty symbolů test a ladění.</span><span class="sxs-lookup"><span data-stu-id="48bb1-130">The following example shows you how to define a MYTEST symbol on a file and then test the values of the MYTEST and DEBUG symbols.</span></span> <span data-ttu-id="48bb1-131">Výstup tohoto příkladu závisí na tom, jestli jste vytvořili projekt na režim ladění nebo verze konfigurace.</span><span class="sxs-lookup"><span data-stu-id="48bb1-131">The output of this example depends on whether you built the project on Debug or Release configuration mode.</span></span>

```csharp
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

<span data-ttu-id="48bb1-132">Následující příklad ukazuje, jak k testování pro různé cílové rozhraní, abyste mohli používat novější rozhraní API, pokud je to možné:</span><span class="sxs-lookup"><span data-stu-id="48bb1-132">The following example shows you how to test for different target frameworks so you can use newer APIs when possible:</span></span>

```csharp
public class MyClass
{
    static void Main()
    {
#if NET40
        WebClient _client = new WebClient();
#else
        HttpClient _client = new HttpClient();
#endif
    }
    //...
}
```

## <a name="see-also"></a><span data-ttu-id="48bb1-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="48bb1-133">See also</span></span>

[<span data-ttu-id="48bb1-134">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="48bb1-134">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
[<span data-ttu-id="48bb1-135">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="48bb1-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
[<span data-ttu-id="48bb1-136">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="48bb1-136">C# Preprocessor Directives</span></span>](index.md)  
<span data-ttu-id="48bb1-137">[Postupy: Podmíněná kompilace pomocí trasování a ladění](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md).</span><span class="sxs-lookup"><span data-stu-id="48bb1-137">[How to: Compile Conditionally with Trace and Debug](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md).</span></span>
