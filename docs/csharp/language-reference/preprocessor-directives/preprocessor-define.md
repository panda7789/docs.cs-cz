---
title: '#definovat – C# referenční informace'
ms.date: 06/30/2018
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: 7457b05ae827675969398792bcb02f025f3028fb
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712582"
---
# <a name="define-c-reference"></a>#define (referenční dokumentace jazyka C#)
Použijete `#define` k definování symbolu. Použijete-li symbol jako výraz, který je předán direktivě [#if](./preprocessor-if.md) , bude výraz vyhodnocen jako `true`, jak ukazuje následující příklad:  
 
 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Direktiva `#define` nemůže být použita k deklaraci konstantních hodnot, jak je obvykle prováděna v jazyce C a C++. Konstanty C# v jsou nejlépe definovány jako statické členy třídy nebo struktury. Pokud máte několik takových konstant, zvažte vytvoření samostatné třídy "konstanty" pro jejich uložení.  
  
 Symboly lze použít k zadání podmínek pro kompilaci. Symbol můžete testovat buď pomocí [#if](./preprocessor-if.md) nebo [#elif](./preprocessor-elif.md). Můžete také použít <xref:System.Diagnostics.ConditionalAttribute> k provedení podmíněné kompilace.  
  
 Můžete definovat symbol, ale nelze přiřadit hodnotu k symbolu. Direktiva `#define` musí být uvedená v souboru předtím, než použijete pokyny, které nejsou také direktivami preprocesoru.  
  
 Můžete také definovat symbol pomocí možnosti kompilátoru [-define](../compiler-options/define-compiler-option.md) . Symbol můžete zrušit definováním [#undef](./preprocessor-undef.md).  
  
 Symbol definovaný pomocí `-define` nebo with `#define` není v konfliktu s proměnnou stejného názvu. To znamená, že název proměnné by neměl být předán direktivě preprocesoru a symbol lze vyhodnotit pouze pomocí direktivy preprocesoru.  
  
 Rozsah symbolu, který byl vytvořen pomocí `#define` je soubor, ve kterém byl symbol definován.  
  
 Jak ukazuje následující příklad, je nutné umístit direktivy `#define` v horní části souboru.  
  
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
- [Postupy: Podmíněná kompilace pomocí atributu Trace a Debug](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
- [#undef](./preprocessor-undef.md)
- [#if](./preprocessor-if.md)
