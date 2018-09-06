---
title: '#undef (referenční dokumentace jazyka C#)'
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: 3957d58f61e51fab01618f5e1146be9cd0da58fd
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43881142"
---
# <a name="undef-c-reference"></a>#undef (referenční dokumentace jazyka C#)
`#undef` můžete nedefinovat symbol, tak, že při použití symbolu jako výraz v [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) direktiv, bude výraz vyhodnocen na `false`.  
  
 Symbol může být definována buď [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) – direktiva nebo [-definovat](../../../csharp/language-reference/compiler-options/define-compiler-option.md) – možnost kompilátoru. `#undef` Direktiva musí být uvedená v souboru, než použijete všechny příkazy, které nejsou také direktivy.  
  
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

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [C# Direktivy preprocesoru](../../../csharp/language-reference/preprocessor-directives/index.md)
