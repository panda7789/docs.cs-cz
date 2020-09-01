---
description: '#If – direktiva preprocesoru – reference jazyka C#'
title: '#If – direktiva preprocesoru – reference jazyka C#'
ms.date: 10/27/2019
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: f01db9d7801d4b6f4c273a9cf82806acbb4828bb
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138134"
---
# <a name="if-c-reference"></a><span data-ttu-id="408e7-103">#if (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="408e7-103">#if (C# reference)</span></span>

<span data-ttu-id="408e7-104">Když kompilátor jazyka C# nalezne `#if` direktivu, za kterou následuje směrnice [#endif](preprocessor-endif.md) , zkompiluje kód mezi direktivami pouze v případě, že je definován zadaný symbol.</span><span class="sxs-lookup"><span data-stu-id="408e7-104">When the C# compiler encounters an `#if` directive, followed eventually by an [#endif](preprocessor-endif.md) directive, it compiles the code between the directives only if the specified symbol is defined.</span></span> <span data-ttu-id="408e7-105">Na rozdíl od jazyka C a C++ nemůžete přiřadit číselnou hodnotu k symbolu.</span><span class="sxs-lookup"><span data-stu-id="408e7-105">Unlike C and C++, you cannot assign a numeric value to a symbol.</span></span> <span data-ttu-id="408e7-106">`#if`Příkaz v jazyce C# je logický a testuje pouze, zda byl symbol definován nebo nikoli.</span><span class="sxs-lookup"><span data-stu-id="408e7-106">The `#if` statement in C# is Boolean and only tests whether the symbol has been defined or not.</span></span> <span data-ttu-id="408e7-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="408e7-107">For example:</span></span>

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

<span data-ttu-id="408e7-108">Operátory [==](../operators/equality-operators.md#equality-operator-) (rovnost) a [! =](../operators/equality-operators.md#inequality-operator-) (nerovnost) lze použít pouze k testování hodnot [bool](../builtin-types/bool.md) `true` nebo `false` .</span><span class="sxs-lookup"><span data-stu-id="408e7-108">You can use the operators [==](../operators/equality-operators.md#equality-operator-) (equality) and [!=](../operators/equality-operators.md#inequality-operator-) (inequality) only to test for the [bool](../builtin-types/bool.md) values `true` or `false`.</span></span> <span data-ttu-id="408e7-109">`true` znamená, že symbol je definován.</span><span class="sxs-lookup"><span data-stu-id="408e7-109">`true` means the symbol is defined.</span></span> <span data-ttu-id="408e7-110">Příkaz `#if DEBUG` má stejný význam jako `#if (DEBUG == true)` .</span><span class="sxs-lookup"><span data-stu-id="408e7-110">The statement `#if DEBUG` has the same meaning as `#if (DEBUG == true)`.</span></span> <span data-ttu-id="408e7-111">Můžete použít [&&  (a)](../operators/boolean-logical-operators.md#conditional-logical-and-operator-), [&#124;&#124;  (nebo)](../operators/boolean-logical-operators.md#conditional-logical-or-operator-), a [! (ne)](../operators/boolean-logical-operators.md#logical-negation-operator-) operátory k vyhodnocení, zda bylo definováno více symbolů.</span><span class="sxs-lookup"><span data-stu-id="408e7-111">You can use the [&& (and)](../operators/boolean-logical-operators.md#conditional-logical-and-operator-), [&#124;&#124; (or)](../operators/boolean-logical-operators.md#conditional-logical-or-operator-), and [! (not)](../operators/boolean-logical-operators.md#logical-negation-operator-) operators to evaluate whether multiple symbols have been defined.</span></span> <span data-ttu-id="408e7-112">Symboly a operátory je také možné seskupovat pomocí závorek.</span><span class="sxs-lookup"><span data-stu-id="408e7-112">You can also group symbols and operators with parentheses.</span></span>

## <a name="remarks"></a><span data-ttu-id="408e7-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="408e7-113">Remarks</span></span>

<span data-ttu-id="408e7-114">`#if`spolu s direktivami [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md)a [#undef](preprocessor-undef.md) umožňuje zahrnout nebo vyloučit kód na základě existence jednoho nebo více symbolů.</span><span class="sxs-lookup"><span data-stu-id="408e7-114">`#if`, along with the [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md), and [#undef](preprocessor-undef.md) directives, lets you include or exclude code based on the existence of one or more symbols.</span></span> <span data-ttu-id="408e7-115">To může být užitečné při kompilování kódu pro sestavení pro ladění nebo při kompilování pro konkrétní konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="408e7-115">This can be useful when compiling code for a debug build or when compiling for a specific configuration.</span></span>

<span data-ttu-id="408e7-116">Podmíněná direktiva začínající `#if` direktivou musí být explicitně ukončena `#endif` direktivou.</span><span class="sxs-lookup"><span data-stu-id="408e7-116">A conditional directive beginning with a `#if` directive must explicitly be terminated with a `#endif` directive.</span></span>

<span data-ttu-id="408e7-117">`#define` umožňuje definovat symbol.</span><span class="sxs-lookup"><span data-stu-id="408e7-117">`#define` lets you define a symbol.</span></span> <span data-ttu-id="408e7-118">Když potom použijete symbol jako výraz předaný `#if` direktivě, výraz se vyhodnotí jako `true` .</span><span class="sxs-lookup"><span data-stu-id="408e7-118">By then using the symbol as the expression passed to the `#if` directive, the expression evaluates to `true`.</span></span>

<span data-ttu-id="408e7-119">Můžete také definovat symbol pomocí možnosti kompilátoru [-define](../compiler-options/define-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="408e7-119">You can also define a symbol with the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="408e7-120">Symbol můžete zrušit definováním [#undef](preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="408e7-120">You can undefine a symbol with [#undef](preprocessor-undef.md).</span></span>

<span data-ttu-id="408e7-121">Symbol, který definujete s `-define` nebo s, `#define` není v konfliktu s proměnnou stejného názvu.</span><span class="sxs-lookup"><span data-stu-id="408e7-121">A symbol that you define with `-define` or with `#define` doesn't conflict with a variable of the same name.</span></span> <span data-ttu-id="408e7-122">To znamená, že název proměnné by neměl být předán direktivě preprocesoru a symbol může být vyhodnocen pouze direktivou preprocesoru.</span><span class="sxs-lookup"><span data-stu-id="408e7-122">That is, a variable name should not be passed to a preprocessor directive, and a symbol can only be evaluated by a preprocessor directive.</span></span>

<span data-ttu-id="408e7-123">Rozsah symbolu vytvořeného pomocí `#define` je soubor, ve kterém byl definován.</span><span class="sxs-lookup"><span data-stu-id="408e7-123">The scope of a symbol created with `#define` is the file in which it was defined.</span></span>

<span data-ttu-id="408e7-124">Systém sestavení také ví o předdefinovaných symbolech preprocesoru, které představují různá [cílová rozhraní](../../../standard/frameworks.md) v projektech ve stylu sady SDK.</span><span class="sxs-lookup"><span data-stu-id="408e7-124">The build system is also aware of predefined preprocessor symbols representing different [target frameworks](../../../standard/frameworks.md) in SDK-style projects.</span></span> <span data-ttu-id="408e7-125">Jsou užitečné při vytváření aplikací, které mohou cílit na více než jednu implementaci nebo verzi rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="408e7-125">They're useful when creating applications that can target more than one .NET implementation or version.</span></span>

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

> [!NOTE]
> <span data-ttu-id="408e7-126">Pro tradiční .NET Framework projekty je nutné ručně nakonfigurovat symboly podmíněné kompilace pro různé cílové architektury v aplikaci Visual Studio prostřednictvím stránek vlastností projektu.</span><span class="sxs-lookup"><span data-stu-id="408e7-126">For traditional .NET Framework projects, you have to manually configure the conditional compilation symbols for the different target frameworks in Visual Studio via the project's properties pages.</span></span>

<span data-ttu-id="408e7-127">Mezi další předdefinované symboly patří konstanty ladění a trasování.</span><span class="sxs-lookup"><span data-stu-id="408e7-127">Other predefined symbols include the DEBUG and TRACE constants.</span></span> <span data-ttu-id="408e7-128">Můžete přepsat hodnoty nastavené pro projekt pomocí `#define` .</span><span class="sxs-lookup"><span data-stu-id="408e7-128">You can override the values set for the project using `#define`.</span></span> <span data-ttu-id="408e7-129">Symbol ladění, například, je automaticky nastaven v závislosti na vlastnostech konfigurace sestavení ("ladění" nebo "Release" Mode).</span><span class="sxs-lookup"><span data-stu-id="408e7-129">The DEBUG symbol, for example, is automatically set depending on your build configuration properties ("Debug" or "Release" mode).</span></span>

## <a name="examples"></a><span data-ttu-id="408e7-130">Příklady</span><span class="sxs-lookup"><span data-stu-id="408e7-130">Examples</span></span>

<span data-ttu-id="408e7-131">Následující příklad ukazuje, jak definovat MYTEST symbol pro soubor a potom otestovat hodnoty symbolů MYTEST a ladění.</span><span class="sxs-lookup"><span data-stu-id="408e7-131">The following example shows you how to define a MYTEST symbol on a file and then test the values of the MYTEST and DEBUG symbols.</span></span> <span data-ttu-id="408e7-132">Výstup tohoto příkladu závisí na tom, zda jste projekt sestavili v režimu konfigurace ladění nebo vydání.</span><span class="sxs-lookup"><span data-stu-id="408e7-132">The output of this example depends on whether you built the project on Debug or Release configuration mode.</span></span>

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

<span data-ttu-id="408e7-133">Následující příklad ukazuje, jak otestovat pro různá cílová rozhraní, abyste mohli používat novější rozhraní API, pokud je to možné:</span><span class="sxs-lookup"><span data-stu-id="408e7-133">The following example shows you how to test for different target frameworks so you can use newer APIs when possible:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="408e7-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="408e7-134">See also</span></span>

- [<span data-ttu-id="408e7-135">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="408e7-135">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="408e7-136">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="408e7-136">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="408e7-137">C# – direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="408e7-137">C# Preprocessor Directives</span></span>](index.md)
- [<span data-ttu-id="408e7-138">Postupy: Podmíněná kompilace pomocí atributu Trace a Debug</span><span class="sxs-lookup"><span data-stu-id="408e7-138">How to: Compile Conditionally with Trace and Debug</span></span>](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
