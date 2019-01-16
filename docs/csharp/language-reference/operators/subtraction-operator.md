---
title: '- Operator - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- -_CSharpKeyword
helpviewer_keywords:
- '- operator [C#]'
- subtraction operator (-) [C#]
ms.assetid: 4de7a4fa-c69d-48e6-aff1-3130af970b2d
ms.openlocfilehash: 8cf6e8871a88e2b37b9531ecbd616289523473c7
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333756"
---
# <a name="--operator-c-reference"></a>-– operátor (C# odkaz)

`-` Operátor může fungovat jako unární nebo binární operátor.

## <a name="remarks"></a>Poznámky

Unární `-` operátory jsou předdefinované pro všechny číselné typy. Výsledek unární `-` operace na číselný typ je negaci číselného operandu.

Binární `-` operátory jsou předdefinované pro všechny typy číselné a výčet odečte druhý operand od prvního.

Typy delegátů také poskytují binární soubor `-` operátor, který provádí odebrání delegátů.

Uživatelem definované typy mohou přetížit unární `-` a binární `-` operátory. Další informace najdete v tématu [– klíčové slovo operátoru](../keywords/operator.md).

## <a name="example"></a>Příklad

[!code-csharp[csRefOperators#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#40)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [C#operátory](index.md)