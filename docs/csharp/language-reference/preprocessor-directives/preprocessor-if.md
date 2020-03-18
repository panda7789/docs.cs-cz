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
# <a name="if-c-reference"></a>#if (odkaz C#)

Když kompilátor Jazyka C# narazí na direktivu, `#if` následovanou nakonec direktivou [#endif,](preprocessor-endif.md) zkompiluje kód mezi direktivami pouze v případě, že je definován zadaný symbol. Na rozdíl od c a c++ nelze symbolu přiřadit číselnou hodnotu. Příkaz `#if` v C# je logická a pouze testuje, zda byl symbol definován nebo ne. Například:

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

Operátory [==](../operators/equality-operators.md#equality-operator-) (rovnost) a [!=](../operators/equality-operators.md#inequality-operator-) (nerovnost) můžete použít pouze k `true` testování `false` [bool](../builtin-types/bool.md) hodnot nebo . `true`znamená, že symbol je definován. Příkaz `#if DEBUG` má stejný význam `#if (DEBUG == true)`jako . Můžete použít [&& (a)](../operators/boolean-logical-operators.md#conditional-logical-and-operator-), [&#124;&#124; (nebo)](../operators/boolean-logical-operators.md#conditional-logical-or-operator-)a [! (ne)](../operators/boolean-logical-operators.md#logical-negation-operator-) vyhodnocovat, zda bylo definováno více symbolů. Symboly a operátory je také možné seskupovat pomocí závorek.

## <a name="remarks"></a>Poznámky

`#if`Spolu se direktivami [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md)a [#undef](preprocessor-undef.md) umožňuje zahrnout nebo vyloučit kód založený na existenci jednoho nebo více symbolů. To může být užitečné při kompilaci kódu pro sestavení ladění nebo při kompilaci pro konkrétní konfiguraci.

Podmíněná směrnice začínající `#if` direktivou musí `#endif` být explicitně ukončena direktivou.

`#define`umožňuje definovat symbol. Tím, že pomocí symbolu jako `#if` výraz předán direktivy, výraz vyhodnotí `true`.

Můžete také definovat symbol s volbou [-define](../compiler-options/define-compiler-option.md) kompilátoru. Symbol můžete zrušit pomocí [#undef](preprocessor-undef.md).

Symbol, který definujete `-define` `#define` s nebo s není v konfliktu s proměnnou se stejným názvem. To znamená, že název proměnné by neměl být předán direktivě preprocesoru a symbol může být vyhodnocen pouze direktivou preprocesoru.

Rozsah symbolu vytvořeného `#define` pomocí je soubor, ve kterém byl definován.

Systém sestavení si je také vědom předdefinovaných předprocesorových symbolů [představujících](../../../standard/frameworks.md) různé cílové architektury v projektech ve stylu sady SDK. Jsou užitečné při vytváření aplikací, které mohou cílit na více než jednu implementaci nebo verzi rozhraní .NET.

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

> [!NOTE]
> U tradičních projektů rozhraní .NET Framework je nutné ručně nakonfigurovat symboly podmíněné kompilace pro různé cílové architektury v sadě Visual Studio prostřednictvím stránek vlastností projektu.

Mezi další předdefinované symboly patří konstanty DEBUG a TRACE. Hodnoty nastavené pro projekt můžete `#define`přepsat pomocí aplikace . Symbol ladění je například automaticky nastaven v závislosti na vlastnostech konfigurace sestavení ("Ladění" nebo "Uvolnění" režimu).

## <a name="examples"></a>Příklady

Následující příklad ukazuje, jak definovat symbol MYTEST v souboru a potom otestovat hodnoty symbolů MYTEST a DEBUG. Výstup tohoto příkladu závisí na tom, zda jste vytvořili projekt v režimu konfigurace ladění nebo vydání.

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

Následující příklad ukazuje, jak testovat různé cílové architektury, takže můžete použít novější rozhraní API, pokud je to možné:

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

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [Direktivy preprocesoru jazyka C#](index.md)
- [Postupy: Podmíněná kompilace pomocí atributu Trace a Debug](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
