---
description: '#undef – Referenční dokumentace jazyka C#'
title: '#undef – Referenční dokumentace jazyka C#'
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: 97f99ab4230585e61fed0e057552b78c7a4c2bb5
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137861"
---
# <a name="undef-c-reference"></a>#undef (referenční dokumentace jazyka C#)
`#undef` umožňuje zrušit definici symbolu, například pomocí symbolu jako výrazu v direktivě [#if](./preprocessor-if.md) . výraz se vyhodnotí jako `false` .  
  
 Symbol lze definovat buď pomocí direktivy [#define](./preprocessor-define.md) , nebo pomocí možnosti kompilátoru [-define](../compiler-options/define-compiler-option.md) . `#undef`Direktiva musí být uvedena v souboru předtím, než použijete příkazy, které nejsou zároveň direktivami.  
  
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

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [C# – direktivy preprocesoru](./index.md)
