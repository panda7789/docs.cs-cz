---
title: false – – operátor (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- false operator keyword [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: e73113bd37dbb68590267141ad037f78919520bc
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44272134"
---
# <a name="false-operator-c-reference"></a>false – – operátor (referenční dokumentace jazyka C#)

Vrátí [bool](bool.md) hodnotu `true` označuje, že operand `false` a vrátí `false` jinak.

Před C# 2.0 `true` a `false` operátory byly použity k vytvoření typy s možnou hodnotou Null hodnotu definovanou uživatelem, které byly kompatibilní s typy, jako `SqlBool`. Však jazyk teď poskytuje integrovanou podporu pro typy s možnou hodnotou Null, a kdykoli je to možné, abyste používali tyto místo přetížení `true` a `false` operátory. Další informace najdete v tématu [typy připouštějící hodnotu Null](../../programming-guide/nullable-types/index.md).

S s povolenou hodnotou Null, logické hodnoty výrazu `a != b` , nemusí být nutně roven `!(a == b)` protože jedna nebo obě hodnoty může mít hodnotu null. Budete muset obě přetížení `true` a `false` operátorům samostatně správně zpracování hodnot null ve výrazu. Následující příklad ukazuje, jak přetížení a použít `true` a `false` operátory.

[!code-csharp[csrefKeywordsOperator#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#16)]

Typ, který přetížení `true` a `false` operátory lze používat pro řídicí výraz v [Pokud](if-else.md), [proveďte](do.md), [při](while.md), a [ pro](for.md) příkazy a [podmíněné výrazy](../operators/conditional-operator.md).

Pokud typ definuje operátor `false`, musíte také definovat operátor [true](true.md).

Typ nejde přetížit přímo podmíněné logické operátory [ && ](../operators/conditional-and-operator.md) a [ &#124; &#124; ](../operators/conditional-or-operator.md), ale stejného účinku lze dosáhnout přetížení regulární logické operátory operátory a operátory `true` a `false`.

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)  
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)  
- [Klíčová slova jazyka C#](index.md)  
- [Operátory jazyka C#](../operators/index.md)  
- [true](true.md)  