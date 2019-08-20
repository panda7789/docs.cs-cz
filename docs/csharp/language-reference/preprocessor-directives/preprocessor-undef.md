---
title: '#undef – C# odkaz'
ms.custom: seodec18
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: fdf22e90be766e87e823a7f8cc27ea00c17d2bb5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605586"
---
# <a name="undef-c-reference"></a>#undef (referenční dokumentace jazyka C#)
`#undef`umožňuje zrušit definici symbolu, například pomocí symbolu jako výrazu v direktivě [#if](./preprocessor-if.md) `false`. výraz se vyhodnotí jako.  
  
 Symbol lze definovat buď pomocí direktivy [#define](./preprocessor-define.md) , nebo pomocí možnosti kompilátoru [-define](../compiler-options/define-compiler-option.md) . `#undef` Direktiva musí být uvedena v souboru předtím, než použijete příkazy, které nejsou zároveň direktivami.  
  
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
