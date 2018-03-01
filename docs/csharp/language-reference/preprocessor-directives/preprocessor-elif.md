---
title: "#elif (referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1512bbbc46ce15570507c8b51540eef607d55dc8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="elif-c-reference"></a>#elif (referenční dokumentace jazyka C#)
Výraz `#elif` umožňuje vytvořit složenou podmíněnou direktivu. `#elif` Výraz vyhodnotí, pokud předchozím [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) ani žádný předcházející, volitelné, `#elif` direktivy výrazy vyhodnocení `true`. Je-li výraz `#elif` vyhodnocen jako `true`, vyhodnotí kompilátor kód mezi výrazem `#elif` a další podmíněnou direktivou. Příklad:  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.Writeline("Debug build");  
#elif VC7  
    Console.Writeline("Visual Studio 7");  
#endif  
```  
  
 K vyhodnocení více symbolů lze použít operátory `==` (rovnost), `!=` (nerovnost), `&&` (a) a `||` (nebo). Symboly a operátory je také možné seskupovat pomocí závorek.  
  
## <a name="remarks"></a>Poznámky  
 Výraz `#elif` je ekvivalentní tomuto:  
  
```csharp
#else  
#if  
```  
  
 Pomocí `#elif` je jednodušší, protože každý `#if` vyžaduje [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), zatímco `#elif` lze použít bez odpovídající `#endif`.  
  
 V tématu [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) příklad použití `#elif`.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [C# direktivy preprocesoru](../../../csharp/language-reference/preprocessor-directives/index.md)
