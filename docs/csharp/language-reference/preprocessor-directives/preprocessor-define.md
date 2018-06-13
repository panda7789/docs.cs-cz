---
title: '#definování (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: 1903b96de5f9dfa4efc252897a4a4bd18ed64924
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33286731"
---
# <a name="define-c-reference"></a>#define (referenční dokumentace jazyka C#)
Používáte `#define` k definování symbol. Při použití symbol jako výraz, který je předán [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) direktivy, výraz vyhodnotí jako `true`, jak ukazuje následující příklad:  
 
 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  `#define` – Direktiva nelze použít k deklarace konstantní hodnoty, což se většinou děje jazyka C a C++. Konstanty v jazyku C# jsou nejlépe definované jako statické členy třídě nebo struktuře. Pokud máte několik takové konstanty, zvažte vytvoření samostatné třídy "Konstanty" k jejich umístění.  
  
 Symboly můžete použít k určení podmínek pro kompilaci. Můžete otestovat pro symbol s buď [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) nebo [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md). Můžete také `conditional` atribut provést Podmíněná kompilace.  
  
 Můžete definovat symbol, ale nelze přiřadit hodnotu symbol. `#define` – Direktiva musí být v souboru dříve, než použijete žádné pokyny, které nejsou také preprocesor – direktivy.  
  
 Můžete také definovat symbol s [/ define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) – možnost kompilátoru. Můžete nedefinované symbol s [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).  
  
 Symbol, který definujete s `/define` nebo s `#define` není v konfliktu s proměnné se stejným názvem. To znamená název proměnné nesmí být předaný direktivy preprocesoru a symbol lze vyhodnotit pouze direktivy preprocesoru.  
  
 Rozsah symbol, který byl vytvořen pomocí `#define` je soubor, ve které byla definována symbolu.  
  
 Jak ukazuje následující příklad, musíte umístit `#define` direktivy v horní části souboru.  
  
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
  
 Příklad toho, jak nedefinované symbol, naleznete v části [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [C# Direktivy preprocesoru](../../../csharp/language-reference/preprocessor-directives/index.md)  
 [const](../../../csharp/language-reference/keywords/const.md)  
 [Postupy: Podmíněná kompilace pomocí atributu Trace a Debug](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)  
 [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)  
 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)
