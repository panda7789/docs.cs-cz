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
# <a name="if-c-reference"></a>#if (referenční dokumentace jazyka C#)

Když se zaznamená kompilátor jazyka C# `#if` – direktiva, a nakonec pomocí [#endif](preprocessor-endif.md) direktivy, se zkompiluje kód mezi direktivy pouze v případě, že je definován zadaný symbol. Na rozdíl od C a C++ nelze přiřadit číselnou hodnotu symbol. Příkaz #if v jazyce C# je logická hodnota a pouze testuje, zda je symbol byla definována nebo ne. Příklad:

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

Můžete použít operátory [ == ](../operators/equality-comparison-operator.md) (rovnosti) a [! =](../operators/not-equal-operator.md) (nerovnost) pouze k testování pro [true](../keywords/true.md) nebo [false](../keywords/false.md). Hodnota TRUE znamená, že je definována symbolu. Příkaz `#if DEBUG` stejný význam jako `#if (DEBUG == true)`. Můžete použít operátory [ && ](../operators/conditional-and-operator.md) (a), [&#124; &#124;](../operators/conditional-or-operator.md) (nebo), a [!](../operators/logical-negation-operator.md) (ne) k vyhodnocení, zda byly definovány více symbolů. Symboly a operátory je také možné seskupovat pomocí závorek.

## <a name="remarks"></a>Poznámky

`#if`, spolu s [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md), a [#undef](preprocessor-undef.md) direktivy, vám umožní zahrnout nebo vyloučit kódu na základě existence jeden nebo více symbolů. To může být užitečné při kompilaci kódu pro sestavení ladicí verze, nebo při kompilaci pro konkrétní konfiguraci.

Podmíněné direktivy od verze `#if` – direktiva musí být explicitně ukončena s `#endif` – direktiva.

`#define` Umožňuje definovat symbol. Potom pomocí symbolu jako výraz předaný `#if` direktivy, vyhodnocen jako `true`.

Můžete také definovat symbol s [/ define](../compiler-options/define-compiler-option.md) – možnost kompilátoru. Můžete nedefinované symbol s [#undef](preprocessor-undef.md).

Symbol, který definujete s `/define` nebo s `#define` není v konfliktu s proměnné se stejným názvem. To znamená název proměnné nesmí být předaný direktivy preprocesoru a symbol lze vyhodnotit pouze direktivy preprocesoru.

Rozsah symbol vytvořené pomocí `#define` je soubor, ve které byla definována.

Systém sestavení má také informace o předdefinovaných symbolů preprocesoru představující různé [cílové rozhraní](../../../standard/frameworks.md). Jsou užitečná při vytváření aplikace, které můžete vybrat víc než jeden implementace rozhraní .NET nebo verzi.

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

Jiné předdefinované symboly obsahovat konstanty pro ladění a trasování. Můžete přepsat hodnoty nastavené pro projekt pomocí `#define`. Symbol ladění, například bude automaticky nastavena v závislosti na vaší vlastnosti konfigurace sestavení (režim "Ladění" nebo "Verze").

## <a name="examples"></a>Příklady

Následující příklad ukazuje, jak definovat symbol test v souboru a poté otestujte hodnoty symbolů test a ladění. Výstup tohoto příkladu závisí na tom, jestli jste vytvořili projekt na režim ladění nebo verze konfigurace.

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

Následující příklad ukazuje, jak k testování pro různé cílové rozhraní, abyste mohli používat novější rozhraní API, pokud je to možné:

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

## <a name="see-also"></a>Viz také

[Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
[Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
[C# Direktivy preprocesoru](index.md)  
[Postupy: Podmíněná kompilace pomocí trasování a ladění](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md).
