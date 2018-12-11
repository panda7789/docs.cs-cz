---
title: '#elif – C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: d7ca980146369174a202c8096cdba154712a438e
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239387"
---
# <a name="elif-c-reference"></a>#elif (referenční dokumentace jazyka C#)
Výraz `#elif` umožňuje vytvořit složenou podmíněnou direktivu. `#elif` Výraz bude vyhodnocen, pokud ani předchozí [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) ani žádné předchozí volitelné `#elif` vyhodnotit výrazy direktivy `true`. Je-li výraz `#elif` vyhodnocen jako `true`, vyhodnotí kompilátor kód mezi výrazem `#elif` a další podmíněnou direktivou. Příklad:  
  
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
  
 Pomocí `#elif` je jednodušší, protože každý `#if` vyžaduje [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), že `#elif` lze použít bez odpovídajícího `#endif`.  
  
 Zobrazit [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) příklad, jak používat `#elif`.  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [C# Direktivy preprocesoru](../../../csharp/language-reference/preprocessor-directives/index.md)
