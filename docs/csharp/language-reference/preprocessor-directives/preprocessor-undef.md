---
title: '#undef – C# odkaz'
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: 21923412aa178c3b86e94a54bd911130e48e4deb
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712439"
---
# <a name="undef-c-reference"></a>#undef (referenční dokumentace jazyka C#)
`#undef` umožňuje zrušit definici symbolu, například pomocí symbolu jako výrazu v direktivě [#if](./preprocessor-if.md) , výraz se vyhodnotí jako `false`.  
  
 Symbol lze definovat buď pomocí direktivy [#define](./preprocessor-define.md) , nebo pomocí možnosti kompilátoru [-define](../compiler-options/define-compiler-option.md) . Aby bylo možné použít jakékoli příkazy, které nejsou zároveň direktivami, je nutné, aby se v souboru objevila direktiva `#undef`.  
  
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

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [C# Direktivy preprocesoru](./index.md)
