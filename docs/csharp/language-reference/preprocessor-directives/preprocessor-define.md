---
title: '#definovat – C# referenční informace'
ms.custom: seodec18
ms.date: 06/30/2018
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: d207c96621564acd8070c9d5f618f43a6d8f15a4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924604"
---
# <a name="define-c-reference"></a>#define (referenční dokumentace jazyka C#)
Použijte `#define` k definování symbolu. Použijete-li symbol jako výraz, který je předán direktivě [#if](./preprocessor-if.md) , výraz se vyhodnotí na `true`, jak ukazuje následující příklad:  
 
 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Direktiva se nedá použít k deklaraci konstantních hodnot, jak se obvykle provádí v C a C++ `#define` Konstanty C# v jsou nejlépe definovány jako statické členy třídy nebo struktury. Pokud máte několik takových konstant, zvažte vytvoření samostatné třídy "konstanty" pro jejich uložení.  
  
 Symboly lze použít k zadání podmínek pro kompilaci. Symbol můžete testovat buď pomocí [#if](./preprocessor-if.md) nebo [#elif](./preprocessor-elif.md). Můžete také použít <xref:System.Diagnostics.ConditionalAttribute> k provedení podmíněné kompilace.  
  
 Můžete definovat symbol, ale nelze přiřadit hodnotu k symbolu. `#define` Direktiva musí být uvedena v souboru předtím, než použijete pokyny, které nejsou také direktivami preprocesoru.  
  
 Můžete také definovat symbol pomocí možnosti kompilátoru [-define](../compiler-options/define-compiler-option.md) . Symbol můžete zrušit definováním [#undef](./preprocessor-undef.md).  
  
 Symbol, který definujete pomocí `-define` nebo s `#define` , není v konfliktu s proměnnou stejného názvu. To znamená, že název proměnné by neměl být předán direktivě preprocesoru a symbol lze vyhodnotit pouze pomocí direktivy preprocesoru.  
  
 Rozsah symbolu, který byl vytvořen pomocí `#define` , je soubor, ve kterém byl symbol definován.  
  
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
  
 Příklad, jak zrušit definování symbolu, naleznete v tématu [#undef](./preprocessor-undef.md).  
  
## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [C# Direktivy preprocesoru](./index.md)
- [const](../keywords/const.md)
- [Postupy: Podmíněně kompilovat pomocí trasování a ladění](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
- [#undef](./preprocessor-undef.md)
- [#if](./preprocessor-if.md)
