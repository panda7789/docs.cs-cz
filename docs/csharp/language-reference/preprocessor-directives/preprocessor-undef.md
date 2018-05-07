---
title: '#undef (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: 870b78580e5350f06fae33f2ac107dc3968b2c6e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="undef-c-reference"></a>#undef (referenční dokumentace jazyka C#)
`#undef` Umožňuje nedefinované symbol, tak, aby pomocí symbolu jako výraz ve [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) direktivy, výraz vyhodnotí jako `false`.  
  
 Symbol může být definována buď pomocí [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) – direktiva nebo [/ define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) – možnost kompilátoru. `#undef` – Direktiva musí být v souboru před používat všechny příkazy, které nejsou také direktivy.  
  
## <a name="example"></a>Příklad  
  
```csharp
// preprocessor_undef.cs  
// compile with: /d:DEBUG  
#undef DEBUG  
using System;  
class MyClass   
{  
    static void Main()   
    {  
#if DEBUG  
        Console.WriteLine("DEBUG is defined");  
#else  
        Console.WriteLine("DEBUG is not defined");  
#endif  
    }  
}  
```  
  
 **LADĚNÍ není definován.**  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [C# Direktivy preprocesoru](../../../csharp/language-reference/preprocessor-directives/index.md)
