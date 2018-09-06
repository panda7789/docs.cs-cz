---
title: '%= – operátor (Referenční dokumentace jazyka C#)'
ms.date: 09/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: c475517666bdadaa457dbb4188808b3a96fcdf0e
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43738285"
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
  
[Operátor zbytku](remainder-operator.md) `%` podporuje všechny číselné typy a vypočítá zbytek po dělení operandů.

Pokud uživatelský typ [přetížení](../keywords/operator.md) [operátor zbytku](remainder-operator.md) `%`, operátor přiřazení zbytku `%=` je implicitně přetížena.
  
Následující příklad ukazuje použití `%=` operátor:

[!code-csharp-interactive[%= example](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#3)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
