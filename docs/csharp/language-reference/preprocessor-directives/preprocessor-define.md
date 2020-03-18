---
title: '#definovat - C# Reference'
ms.date: 06/30/2018
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: c08d6f42c11184a4d14aa6712f9f0f8706a72cab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173429"
---
# <a name="define-c-reference"></a>#define (referenční dokumentace jazyka C#)
Slouží `#define` k definování symbolu. Použijete-li symbol jako výraz, který je předán direktivě [#if,](./preprocessor-if.md) výraz se vyhodnotí na `true`, jak ukazuje následující příklad:  

 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Direktivu `#define` nelze použít k deklarování konstantních hodnot, jak se obvykle provádí v jazycích C a C++. Konstanty v C# jsou nejlépe definovány jako statické členy třídy nebo struktury. Pokud máte několik takových konstant, zvažte vytvoření samostatné třídy "Konstanty", která je bude držet.  
  
 Symboly lze použít k určení podmínek pro kompilaci. Symbol můžete testovat buď [#if,](./preprocessor-if.md) nebo [#elif](./preprocessor-elif.md). Můžete také použít <xref:System.Diagnostics.ConditionalAttribute> k provedení podmíněné kompilace.  
  
 Symbol můžete definovat, ale nelze mu přiřadit hodnotu. Směrnice `#define` se musí objevit v souboru před použitím pokynů, které nejsou také direktivy preprocesoru.  
  
 Můžete také definovat symbol s volbou [-define](../compiler-options/define-compiler-option.md) kompilátoru. Symbol můžete zrušit pomocí [#undef](./preprocessor-undef.md).  
  
 Symbol, který definujete `-define` `#define` s nebo s není v konfliktu s proměnnou se stejným názvem. To znamená, že název proměnné by neměl být předán direktivě preprocesoru a symbol může být vyhodnocen pouze direktivou preprocesoru.  
  
 Rozsah symbolu, který byl `#define` vytvořen pomocí, je soubor, ve kterém byl definován symbol.  
  
 Jak ukazuje následující příklad, `#define` je nutné umístit direktivy v horní části souboru.  
  
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
  
 Příklad zrušení definice symbolu naleznete v [tématu #undef](./preprocessor-undef.md).  
  
## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [Direktivy preprocesoru jazyka C#](./index.md)
- [const](../keywords/const.md)
- [Postupy: Podmíněná kompilace pomocí atributu Trace a Debug](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
- [#undef](./preprocessor-undef.md)
- [#if](./preprocessor-if.md)
