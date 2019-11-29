---
title: '#If – direktiva preprocesoru C# – referenční informace'
ms.custom: seodec18
ms.date: 10/27/2019
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: e467a890e971e6c6f2c681ee503d7c7ead19a1e4
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552446"
---
# <a name="if-c-reference"></a>#if (referenční dokumentace jazyka C#)

Když C# kompilátor narazí na direktivu`#if`a následně na něj následuje direktiva [#endif](preprocessor-endif.md) , zkompiluje kód mezi direktivami pouze v případě, že je definován zadaný symbol. Na rozdíl od jazyka C++C a nemůžete přiřadit číselnou hodnotu k symbolu. Příkaz #if v C# je logický a pouze testuje, zda byl symbol definován nebo nikoli. Příklad:

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

Operátory [==](../operators/equality-operators.md#equality-operator-) (rovnost) a [! =](../operators/equality-operators.md#inequality-operator-) (nerovnost) lze použít pouze k testování hodnot [bool](../builtin-types/bool.md) `true` nebo `false`. Hodnota true znamená, že je symbol definován. Příkaz `#if DEBUG` má stejný význam jako `#if (DEBUG == true)`. Můžete použít operátory [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) (a), [ &#124; ](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) (nebo), a [!](../operators/boolean-logical-operators.md#logical-negation-operator-) (ne) k vyhodnocení, zda bylo definováno více symbolů. Symboly a operátory je také možné seskupovat pomocí závorek.

## <a name="remarks"></a>Poznámky

`#if`společně s direktivami [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md)a [#undef](preprocessor-undef.md) umožňuje zahrnout nebo vyloučit kód na základě existence jednoho nebo více symbolů. To může být užitečné při kompilování kódu pro sestavení pro ladění nebo při kompilování pro konkrétní konfiguraci.

Podmíněná direktiva začínající direktivou `#if` musí být explicitně ukončena direktivou `#endif`.

`#define` umožňuje definovat symbol. Když potom použijete symbol jako výraz předaný direktivě `#if`, výraz se vyhodnotí jako `true`.

Můžete také definovat symbol pomocí možnosti kompilátoru [-define](../compiler-options/define-compiler-option.md) . Symbol můžete zrušit definováním [#undef](preprocessor-undef.md).

Symbol definovaný pomocí `-define` nebo s `#define` není v konfliktu s proměnnou stejného názvu. To znamená, že název proměnné by neměl být předán direktivě preprocesoru a symbol může být vyhodnocen pouze direktivou preprocesoru.

Rozsah symbolu vytvořeného pomocí `#define` je soubor, ve kterém byl definován.

Systém sestavení také ví o předdefinovaných symbolech preprocesoru, které představují různá [cílová rozhraní](../../../standard/frameworks.md) v projektech ve stylu sady SDK. Jsou užitečné při vytváření aplikací, které mohou cílit na více než jednu implementaci nebo verzi rozhraní .NET.

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

> [!NOTE]
> Pro tradiční .NET Framework projekty je nutné ručně nakonfigurovat symboly podmíněné kompilace pro různé cílové architektury v aplikaci Visual Studio prostřednictvím stránek vlastností projektu.

Mezi další předdefinované symboly patří konstanty ladění a trasování. Můžete přepsat hodnoty nastavené pro projekt pomocí `#define`. Symbol ladění, například, je automaticky nastaven v závislosti na vlastnostech konfigurace sestavení ("ladění" nebo "Release" Mode).

## <a name="examples"></a>Příklady

Následující příklad ukazuje, jak definovat MYTEST symbol pro soubor a potom otestovat hodnoty symbolů MYTEST a ladění. Výstup tohoto příkladu závisí na tom, zda jste projekt sestavili v režimu konfigurace ladění nebo vydání.

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

Následující příklad ukazuje, jak otestovat pro různá cílová rozhraní, abyste mohli používat novější rozhraní API, pokud je to možné:

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

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [C# Direktivy preprocesoru](index.md)
- [Postupy: Podmíněná kompilace pomocí atributu Trace a Debug](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
