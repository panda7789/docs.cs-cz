---
title: += – operátor (Referenční dokumentace jazyka C#)
ms.date: 10/22/2018
f1_keywords:
- +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
- event subscription [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
ms.openlocfilehash: ee335e3e2e7d352d4e26b802bad2b08a05c666ab
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192028"
---
# <a name="-operator-c-reference"></a>+= – operátor (Referenční dokumentace jazyka C#)

Operátor přiřazení sčítání.

Pomocí výrazu `+=` operátorů, například  

```csharp
x += y
```  

je ekvivalentem  

```csharp
x = x + y
```  

s tím rozdílem, že `x` se jenom vyhodnotí jednou.
  
Pro číselné typy [operátor sčítání](addition-operator.md) `+` kód vypočítá součet operandů. Pokud je jeden nebo oba operandy typu [řetězec](../keywords/string.md), zřetězí řetězcové reprezentace jeho operandy. Pro typy delegátů `+` operátor vrátí novou instanci delegáta, který je kombinací operandů.

Pokud uživatelský typ [přetížení](../keywords/operator.md) [operátor sčítání](addition-operator.md) `+`, operátor přiřazení sčítání `+=` je implicitně přetížena.

Můžete také použít `+=` operátor zadat metodu obslužné rutiny události, když se přihlásíte k odběru [události](../keywords/event.md). Další informace najdete v tématu [postupy: přihlášení k odběru a zrušit její odběr události](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

Následující příklad ukazuje použití `+=` operátor:

[!code-csharp-interactive[+= examples](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddAndAssign)]
  
## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
- [Události](../../programming-guide/events/index.md)
- [Delegáti](../../programming-guide/delegates/index.md)
