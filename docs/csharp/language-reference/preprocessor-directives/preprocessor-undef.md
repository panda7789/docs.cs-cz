---
title: "#undef (referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e7a3c162c0ecb8bb39cc13a34dcd15fa3ce96ebb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="undef-c-reference"></a>#undef (referenční dokumentace jazyka C#)
`#undef`Umožňuje nedefinované symbol, tak, aby pomocí symbolu jako výraz ve [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) direktivy, výraz vyhodnotí jako `false`.  
  
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
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [C# direktivy preprocesoru](../../../csharp/language-reference/preprocessor-directives/index.md)
