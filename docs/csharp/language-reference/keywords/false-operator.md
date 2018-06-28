---
title: false – – operátor (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- false operator keyword [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: e1c6da604f35031dd9d712125356243e1735f452
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027834"
---
# <a name="false-operator-c-reference"></a>false – – operátor (referenční dokumentace jazyka C#)

Vrátí [bool](bool.md) hodnotu `true` označuje, že operand `false` a vrátí `false` jinak.

Před C# 2.0 `true` a `false` operátory jste použili k vytvoření typů s povolenou hodnotou Null hodnotu definovanou uživatelem, které byly kompatibilní s typy, jako `SqlBool`. Ale jazyk teď poskytuje integrovanou podporu pro typy hodnot s povolenou hodnotou Null, a kdykoli je to možné postupujte podle těchto místo přetížení `true` a `false` operátory. Další informace najdete v tématu [typy s možnou hodnotou Null](../../programming-guide/nullable-types/index.md).

S s možnou hodnotou Null logické hodnoty, výraz `a != b` není nutně roven `!(a == b)` vzhledem k tomu, že jedna nebo obě hodnoty může mít hodnotu null. Budete muset přetížení i `true` a `false` operátorům samostatně správně zpracování hodnot null ve výrazu. Následující příklad ukazuje, jak přetížení a používat `true` a `false` operátory.

[!code-csharp[csrefKeywordsOperator#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#16)]

Typ, který přetížení `true` a `false` operátory lze použít pro řízení výrazu v [Pokud](if-else.md), [provést](do.md), [při](while.md), a [ pro](for.md) příkazy a v [podmíněné výrazy](../operators/conditional-operator.md).

Pokud typ definuje operátor `false`, musí definovat také operátor [true](true.md).

Typ nelze přímo přetížení podmíněného logické operátory [ && ](../operators/conditional-and-operator.md) a [ &#124; &#124; ](../operators/conditional-or-operator.md), ale lze dosáhnout ekvivalentní vliv přetížení regulární logické operátory operátory a `true` a `false`.

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C#](../index.md)  
[Průvodce programováním v jazyce C#](../../programming-guide/index.md)  
[Klíčová slova jazyka C#](index.md)  
[Operátory jazyka C#](../operators/index.md)  
[true](true.md)  