---
title: '#undef - C# Odkaz'
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: 21923412aa178c3b86e94a54bd911130e48e4deb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712439"
---
# <a name="undef-c-reference"></a>#undef (referenční dokumentace jazyka C#)
`#undef`umožňuje zrušit definici symbolu, takže pomocí symbolu jako výrazu v direktivě [#if](./preprocessor-if.md) bude výraz vyhodnocen na `false`.  
  
 Symbol lze definovat buď pomocí [#define](./preprocessor-define.md) direktivy nebo [-define](../compiler-options/define-compiler-option.md) kompilátoru. Směrnice `#undef` musí být uvedeny v souboru před použitím všechny příkazy, které nejsou také direktivy.  
  
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

**LADĚNÍ není definováno.**

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [Direktivy preprocesoru jazyka C#](./index.md)
