---
title: '#pokud preprocesorová směrnice - C# Reference'
ms.date: 10/27/2019
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: d047b88f202341a795834809d0b601706c30fcb4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75899855"
---
# <a name="if-c-reference"></a><span data-ttu-id="7f034-102">#if (odkaz C#)</span><span class="sxs-lookup"><span data-stu-id="7f034-102">#if (C# reference)</span></span>

<span data-ttu-id="7f034-103">Když kompilátor Jazyka C# narazí na direktivu, `#if` následovanou nakonec direktivou [#endif,](preprocessor-endif.md) zkompiluje kód mezi direktivami pouze v případě, že je definován zadaný symbol.</span><span class="sxs-lookup"><span data-stu-id="7f034-103">When the C# compiler encounters an `#if` directive, followed eventually by an [#endif](preprocessor-endif.md) directive, it compiles the code between the directives only if the specified symbol is defined.</span></span> <span data-ttu-id="7f034-104">Na rozdíl od c a c++ nelze symbolu přiřadit číselnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7f034-104">Unlike C and C++, you cannot assign a numeric value to a symbol.</span></span> <span data-ttu-id="7f034-105">Příkaz `#if` v C# je logická a pouze testuje, zda byl symbol definován nebo ne.</span><span class="sxs-lookup"><span data-stu-id="7f034-105">The `#if` statement in C# is Boolean and only tests whether the symbol has been defined or not.</span></span> <span data-ttu-id="7f034-106">Například:</span><span class="sxs-lookup"><span data-stu-id="7f034-106">For example:</span></span>

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

<span data-ttu-id="7f034-107">Operátory [==](../operators/equality-operators.md#equality-operator-) (rovnost) a [!=](../operators/equality-operators.md#inequality-operator-) (nerovnost) můžete použít pouze k `true` testování `false` [bool](../builtin-types/bool.md) hodnot nebo .</span><span class="sxs-lookup"><span data-stu-id="7f034-107">You can use the operators [==](../operators/equality-operators.md#equality-operator-) (equality) and [!=](../operators/equality-operators.md#inequality-operator-) (inequality) only to test for the [bool](../builtin-types/bool.md) values `true` or `false`.</span></span> <span data-ttu-id="7f034-108">`true`znamená, že symbol je definován.</span><span class="sxs-lookup"><span data-stu-id="7f034-108">`true` means the symbol is defined.</span></span> <span data-ttu-id="7f034-109">Příkaz `#if DEBUG` má stejný význam `#if (DEBUG == true)`jako .</span><span class="sxs-lookup"><span data-stu-id="7f034-109">The statement `#if DEBUG` has the same meaning as `#if (DEBUG == true)`.</span></span> <span data-ttu-id="7f034-110">Můžete použít [&& (a)](../operators/boolean-logical-operators.md#conditional-logical-and-operator-), [&#124;&#124; (nebo)](../operators/boolean-logical-operators.md#conditional-logical-or-operator-)a [! (ne)](../operators/boolean-logical-operators.md#logical-negation-operator-) vyhodnocovat, zda bylo definováno více symbolů.</span><span class="sxs-lookup"><span data-stu-id="7f034-110">You can use the [&& (and)](../operators/boolean-logical-operators.md#conditional-logical-and-operator-), [&#124;&#124; (or)](../operators/boolean-logical-operators.md#conditional-logical-or-operator-), and [! (not)](../operators/boolean-logical-operators.md#logical-negation-operator-) operators to evaluate whether multiple symbols have been defined.</span></span> <span data-ttu-id="7f034-111">Symboly a operátory je také možné seskupovat pomocí závorek.</span><span class="sxs-lookup"><span data-stu-id="7f034-111">You can also group symbols and operators with parentheses.</span></span>

## <a name="remarks"></a><span data-ttu-id="7f034-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7f034-112">Remarks</span></span>

<span data-ttu-id="7f034-113">`#if`Spolu se direktivami [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md)a [#undef](preprocessor-undef.md) umožňuje zahrnout nebo vyloučit kód založený na existenci jednoho nebo více symbolů.</span><span class="sxs-lookup"><span data-stu-id="7f034-113">`#if`, along with the [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md), and [#undef](preprocessor-undef.md) directives, lets you include or exclude code based on the existence of one or more symbols.</span></span> <span data-ttu-id="7f034-114">To může být užitečné při kompilaci kódu pro sestavení ladění nebo při kompilaci pro konkrétní konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="7f034-114">This can be useful when compiling code for a debug build or when compiling for a specific configuration.</span></span>

<span data-ttu-id="7f034-115">Podmíněná směrnice začínající `#if` direktivou musí `#endif` být explicitně ukončena direktivou.</span><span class="sxs-lookup"><span data-stu-id="7f034-115">A conditional directive beginning with a `#if` directive must explicitly be terminated with a `#endif` directive.</span></span>

<span data-ttu-id="7f034-116">`#define`umožňuje definovat symbol.</span><span class="sxs-lookup"><span data-stu-id="7f034-116">`#define` lets you define a symbol.</span></span> <span data-ttu-id="7f034-117">Tím, že pomocí symbolu jako `#if` výraz předán direktivy, výraz vyhodnotí `true`.</span><span class="sxs-lookup"><span data-stu-id="7f034-117">By then using the symbol as the expression passed to the `#if` directive, the expression evaluates to `true`.</span></span>

<span data-ttu-id="7f034-118">Můžete také definovat symbol s volbou [-define](../compiler-options/define-compiler-option.md) kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="7f034-118">You can also define a symbol with the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="7f034-119">Symbol můžete zrušit pomocí [#undef](preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="7f034-119">You can undefine a symbol with [#undef](preprocessor-undef.md).</span></span>

<span data-ttu-id="7f034-120">Symbol, který definujete `-define` `#define` s nebo s není v konfliktu s proměnnou se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="7f034-120">A symbol that you define with `-define` or with `#define` doesn't conflict with a variable of the same name.</span></span> <span data-ttu-id="7f034-121">To znamená, že název proměnné by neměl být předán direktivě preprocesoru a symbol může být vyhodnocen pouze direktivou preprocesoru.</span><span class="sxs-lookup"><span data-stu-id="7f034-121">That is, a variable name should not be passed to a preprocessor directive, and a symbol can only be evaluated by a preprocessor directive.</span></span>

<span data-ttu-id="7f034-122">Rozsah symbolu vytvořeného `#define` pomocí je soubor, ve kterém byl definován.</span><span class="sxs-lookup"><span data-stu-id="7f034-122">The scope of a symbol created with `#define` is the file in which it was defined.</span></span>

<span data-ttu-id="7f034-123">Systém sestavení si je také vědom předdefinovaných předprocesorových symbolů [představujících](../../../standard/frameworks.md) různé cílové architektury v projektech ve stylu sady SDK.</span><span class="sxs-lookup"><span data-stu-id="7f034-123">The build system is also aware of predefined preprocessor symbols representing different [target frameworks](../../../standard/frameworks.md) in SDK-style projects.</span></span> <span data-ttu-id="7f034-124">Jsou užitečné při vytváření aplikací, které mohou cílit na více než jednu implementaci nebo verzi rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="7f034-124">They're useful when creating applications that can target more than one .NET implementation or version.</span></span>

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

> [!NOTE]
> <span data-ttu-id="7f034-125">U tradičních projektů rozhraní .NET Framework je nutné ručně nakonfigurovat symboly podmíněné kompilace pro různé cílové architektury v sadě Visual Studio prostřednictvím stránek vlastností projektu.</span><span class="sxs-lookup"><span data-stu-id="7f034-125">For traditional .NET Framework projects, you have to manually configure the conditional compilation symbols for the different target frameworks in Visual Studio via the project's properties pages.</span></span>

<span data-ttu-id="7f034-126">Mezi další předdefinované symboly patří konstanty DEBUG a TRACE.</span><span class="sxs-lookup"><span data-stu-id="7f034-126">Other predefined symbols include the DEBUG and TRACE constants.</span></span> <span data-ttu-id="7f034-127">Hodnoty nastavené pro projekt můžete `#define`přepsat pomocí aplikace .</span><span class="sxs-lookup"><span data-stu-id="7f034-127">You can override the values set for the project using `#define`.</span></span> <span data-ttu-id="7f034-128">Symbol ladění je například automaticky nastaven v závislosti na vlastnostech konfigurace sestavení ("Ladění" nebo "Uvolnění" režimu).</span><span class="sxs-lookup"><span data-stu-id="7f034-128">The DEBUG symbol, for example, is automatically set depending on your build configuration properties ("Debug" or "Release" mode).</span></span>

## <a name="examples"></a><span data-ttu-id="7f034-129">Příklady</span><span class="sxs-lookup"><span data-stu-id="7f034-129">Examples</span></span>

<span data-ttu-id="7f034-130">Následující příklad ukazuje, jak definovat symbol MYTEST v souboru a potom otestovat hodnoty symbolů MYTEST a DEBUG.</span><span class="sxs-lookup"><span data-stu-id="7f034-130">The following example shows you how to define a MYTEST symbol on a file and then test the values of the MYTEST and DEBUG symbols.</span></span> <span data-ttu-id="7f034-131">Výstup tohoto příkladu závisí na tom, zda jste vytvořili projekt v režimu konfigurace ladění nebo vydání.</span><span class="sxs-lookup"><span data-stu-id="7f034-131">The output of this example depends on whether you built the project on Debug or Release configuration mode.</span></span>

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

<span data-ttu-id="7f034-132">Následující příklad ukazuje, jak testovat různé cílové architektury, takže můžete použít novější rozhraní API, pokud je to možné:</span><span class="sxs-lookup"><span data-stu-id="7f034-132">The following example shows you how to test for different target frameworks so you can use newer APIs when possible:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7f034-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="7f034-133">See also</span></span>

- [<span data-ttu-id="7f034-134">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7f034-134">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7f034-135">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7f034-135">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7f034-136">Direktivy preprocesoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7f034-136">C# Preprocessor Directives</span></span>](index.md)
- [<span data-ttu-id="7f034-137">Postupy: Podmíněná kompilace pomocí atributu Trace a Debug</span><span class="sxs-lookup"><span data-stu-id="7f034-137">How to: Compile Conditionally with Trace and Debug</span></span>](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
