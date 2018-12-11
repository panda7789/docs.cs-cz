---
title: '% = – Operátor - C# odkaz'
ms.custom: seodec18
ms.date: 09/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: d0732f9578b64c894ecc1d3bb15cee11a8d5b6a3
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245558"
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
