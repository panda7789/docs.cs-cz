---
title: '%= – operátor (Referenční dokumentace jazyka C#)'
ms.date: 09/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: ab3a6a8d5cbfeb4d527ca1f9c233ddfaba3d35ff
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188713"
---
# <a name="-operator-c-reference"></a>%= – operátor (Referenční dokumentace jazyka C#)

Operátor přiřazení zbytku.

Pomocí výrazu `%=` operátorů, například  

```csharp
x %= y
```  

je ekvivalentem  

```csharp
x = x % y
```  

s tím rozdílem, že `x` se jenom vyhodnotí jednou.
  
[Operátor zbytku](remainder-operator.md) `%` vypočítá zbytek po dělení operandů. Podporuje všechny číselné typy.

Pokud uživatelský typ [přetížení](../keywords/operator.md) [operátor zbytku](remainder-operator.md) `%`, operátor přiřazení zbytku `%=` je implicitně přetížena.
  
Následující příklad ukazuje použití `%=` operátor:

[!code-csharp-interactive[%= example](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#3)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
