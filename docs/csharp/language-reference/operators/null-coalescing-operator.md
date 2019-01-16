---
title: ?? Operator - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ??_CSharpKeyword
helpviewer_keywords:
- coalesce operator [C#]
- ?? operator [C#]
- conditional-AND operator (&&) [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: b96fe4790aac7ff5ff5394cbaaeaddc1e334e96c
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333210"
---
# <a name="-operator-c-reference"></a>?? operator (Referenční dokumentace jazyka C#)

`??` Operátor se nazývá operátoru nulového sjednocení.  Vrátí levý operand, pokud hodnota operandu není null; v opačném případě vrátí pravý operand.

## <a name="remarks"></a>Poznámky

Typ povolené hodnoty null představuje hodnotu z domény typu, hodnotu lze také definovat (v takovém případě je hodnota null). Můžete použít `??` syntaktické expresivity obsluhy se vraťte na příslušnou hodnotu (pravý operand) Pokud levý operand má typ s možnou hodnotou Null, jehož hodnota je null. Pokud se pokusíte přiřadit typ s možnou hodnotou Null typu hodnotu Null bez použití `??` operátoru, vygeneruje chybu v době kompilace. Pokud použijete přetypování a typ s možnou hodnotou Null není aktuálně definován `InvalidOperationException` , bude vyvolána výjimka.

Další informace najdete v tématu [typy připouštějící hodnotu Null](../../programming-guide/nullable-types/index.md).

Výsledek?? operátor není považována za konstantu, i když jsou oba argumenty konstanty.

## <a name="example"></a>Příklad

[!code-csharp[csRefOperators#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#53)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [null operátor sloučení](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) v [ C# specifikace jazyka](../language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [C#operátory](index.md)
- [Typy s povolenou hodnotou Null](../../programming-guide/nullable-types/index.md)
- [Co přesně se pojem "zrušeno" znamenají?](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)