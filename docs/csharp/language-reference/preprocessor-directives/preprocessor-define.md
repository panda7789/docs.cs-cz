---
title: '#definování - C# odkaz'
ms.custom: seodec18
ms.date: 06/30/2018
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: 7be2a2d00e96b4b734e1a68f6dc63180bcbe5e82
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244964"
---
# <a name="define-c-reference"></a>#define (referenční dokumentace jazyka C#)
Použijete `#define` k definici symbolu. Při použití symbolu jako výraz, který je předán [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) direktiv, bude výraz vyhodnocen na `true`, jak je vidět v následujícím příkladu:  
 
 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  `#define` – Direktiva nelze použít k deklarování konstantních hodnot, což se většinou děje v jazyce C a C++. Konstanty v jazyce C# jsou nejlépe definovány jako statické členy třídy nebo struktury. Pokud máte několik takových konstant, zvažte vytvoření samostatné třídy "Konstanty" pro jejich uložení.  
  
 Symboly lze použít k určení podmínek kompilace. Můžete vyzkoušet symbol s [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) nebo [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md). Můžete také použít <xref:System.Diagnostics.ConditionalAttribute> k provedení podmíněné kompilace.  
  
 Můžete definovat symbol, ale nelze přiřadit hodnotu symbolu. `#define` Direktiva musí být uvedená v souboru, než použijete pokyny, které nejsou zároveň i direktivy preprocesoru.  
  
 Můžete také definovat symbol s [-definovat](../../../csharp/language-reference/compiler-options/define-compiler-option.md) – možnost kompilátoru. Můžete nedefinovat symbol s [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).  
  
 Symbol, který definujete pomocí `-define` nebo s `#define` není v rozporu s proměnnou se stejným názvem. To znamená že název proměnné by neměl být předán direktivě preprocesoru a symbol lze vyhodnotit pouze pomocí direktivy preprocesoru.  
  
 Rozsah symbolu, který byl vytvořen pomocí `#define` je soubor, ve kterém byl definován symbol.  
  
 Jak ukazuje následující příklad, je nutné umístit `#define` direktivy v horní části souboru.  
  
```csharp  
#define DEBUG  
//#define TRACE  
#undef TRACE  
  
using System;  
  
public class TestDefine  
{  
    static void Main()  
    {  
#if (DEBUG)  
        Console.WriteLine("Debugging is enabled.");  
#endif  
  
#if (TRACE)  
     Console.WriteLine("Tracing is enabled.");  
#endif  
    }  
}  
// Output:  
// Debugging is enabled.  
```  
  
 Příklad zrušení definice symbolu naleznete v tématu [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [C# Direktivy preprocesoru](../../../csharp/language-reference/preprocessor-directives/index.md)  
- [const](../../../csharp/language-reference/keywords/const.md)  
- [Postupy: Podmíněná kompilace pomocí trasování a ladění](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)  
- [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)  
- [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)
