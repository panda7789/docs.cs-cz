---
title: '#elif – C# reference'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: b04db4bd23a459043efec59b8ebf9d322defbcf7
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608581"
---
# <a name="elif-c-reference"></a>#elif (referenční dokumentace jazyka C#)
Výraz `#elif` umožňuje vytvořit složenou podmíněnou direktivu. Výraz bude vyhodnocen, pokud ani předchozí [#if](./preprocessor-if.md) ani žádné `#elif` předchozí, nepovinné výrazy direktivy vyhodnoceny na. `true` `#elif` Je-li výraz `#elif` vyhodnocen jako `true`, vyhodnotí kompilátor kód mezi výrazem `#elif` a další podmíněnou direktivou. Příklad:  
  
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
  
 Použití `#elif` je jednodušší, protože každý `#if` vyžaduje [#endif](./preprocessor-endif.md), zatímco `#elif` lze použít bez odpovídajícího. `#endif`  
  
 Příklad [](./preprocessor-if.md) použití `#elif`naleznete v tématu #if.  
  
## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [C# Direktivy preprocesoru](./index.md)
