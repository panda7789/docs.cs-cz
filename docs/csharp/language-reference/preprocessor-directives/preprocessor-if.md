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
# <a name="if-c-reference"></a>#if (referenční dokumentace jazyka C#)
Když se zaznamená kompilátor jazyka C# `#if` – direktiva, a nakonec pomocí [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) direktivy, ji budou zkompilovat kód mezi direktivy pouze v případě, že je definován zadaný symbol.  Na rozdíl od C a C++ nelze přiřadit číselnou hodnotu na symbol; příkaz #if v jazyce C# je logická hodnota a pouze testuje, zda je symbol byla definována nebo ne. Například  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
 Můžete použít operátory [ == ](../../../csharp/language-reference/operators/equality-comparison-operator.md) (rovnosti), [! =](../../../csharp/language-reference/operators/not-equal-operator.md) (nerovnost) pouze k testování pro [true](../../../csharp/language-reference/keywords/true.md) nebo [false](../../../csharp/language-reference/keywords/false.md) . Hodnota TRUE znamená, že je definována symbolu. Příkaz `#if DEBUG` stejný význam jako `#if (DEBUG == true)`. Můžete použít operátory [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) (a), [&#124; &#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) (nebo), a [!](../../../csharp/language-reference/operators/logical-negation-operator.md) (ne) k vyhodnocení, zda byly definovány více symbolů. Symboly a operátory je také možné seskupovat pomocí závorek.  
  
## <a name="remarks"></a>Poznámky  
 `#if`, spolu s [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md), [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md), a [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) direktivy, vám umožní zahrnout nebo vyloučit kódu na základě existence jeden nebo více symbolů. To může být užitečné při kompilaci kódu pro sestavení ladicí verze, nebo při kompilaci pro konkrétní konfiguraci.  
  
 Podmíněné direktivy od verze `#if` – direktiva musí být explicitně ukončena s `#endif` – direktiva.  
  
 `#define`Umožňuje definovat symbol, tak, aby pomocí symbolu jako výraz předaný `#if` direktivy, výraz vyhodnotí jako `true`.  
  
 Můžete také definovat symbol s [/ define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) – možnost kompilátoru. Můžete nedefinované symbol s [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).  
  
 Symbol, který definujete s `/define` nebo s `#define` není v konfliktu s proměnné se stejným názvem. To znamená název proměnné nesmí být předaný direktivy preprocesoru a symbol lze vyhodnotit pouze direktivy preprocesoru.  
  
 Rozsah symbol vytvořené pomocí `#define` je soubor, ve které byla definována.  
  
## <a name="example"></a>Příklad  
  
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
  
 **Jsou definovány ladění a test**  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [C# direktivy preprocesoru](../../../csharp/language-reference/preprocessor-directives/index.md)
