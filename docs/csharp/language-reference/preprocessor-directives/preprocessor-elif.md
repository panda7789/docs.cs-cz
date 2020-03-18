---
title: '#elif - C# Reference'
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: c78818f40b76414d289af6c704ff019b63befe37
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712569"
---
# <a name="elif-c-reference"></a>#elif (referenční dokumentace jazyka C#)
Výraz `#elif` umožňuje vytvořit složenou podmíněnou direktivu. Výraz `#elif` bude vyhodnocen, pokud předchozí [#if](./preprocessor-if.md) ani žádné `#elif` předchozí, volitelné `true`výrazy direktivy vyhodnotí . Je-li výraz `#elif` vyhodnocen jako `true`, vyhodnotí kompilátor kód mezi výrazem `#elif` a další podmíněnou direktivou. Například:  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 K vyhodnocení více symbolů lze použít operátory `==` (rovnost), `!=` (nerovnost), `&&` (a) a `||` (nebo). Symboly a operátory je také možné seskupovat pomocí závorek.  
  
## <a name="remarks"></a>Poznámky  
 Výraz `#elif` je ekvivalentní tomuto:  
  
```csharp
#else  
#if  
```  
  
 Použití `#elif` je jednodušší, `#if` protože každý vyžaduje `#elif` [#endif](./preprocessor-endif.md), zatímco `#endif`lze použít bez odpovídající .  
  
 Příklad použití [viz #if](./preprocessor-if.md) `#elif`.  
  
## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [Direktivy preprocesoru jazyka C#](./index.md)
