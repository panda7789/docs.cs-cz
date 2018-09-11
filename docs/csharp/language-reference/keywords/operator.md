---
title: klíčové slovo pro operátor (referenční dokumentace jazyka C#)
description: Zjistěte, jak přetížení předdefinovaný operátor C#
ms.date: 08/27/2018
f1_keywords:
- operator_CSharpKeyword
- operator
helpviewer_keywords:
- operator keyword [C#]
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
ms.openlocfilehash: 1e11d7767b61becc39b1158fae9cb2abe997e4bd
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44342378"
---
# <a name="operator-c-reference"></a>operator (Referenční dokumentace jazyka C#)

Použití `operator` – klíčové slovo přetížení předdefinovaný operátor nebo k poskytování uživatelsky definovaný převod v deklaraci třídy nebo struktury.

Přetížení operátoru na vlastní třídy nebo struktury, vytvoříte v odpovídající typ deklarace operátoru. Deklarace operátor, který přetěžuje předdefinovaný operátor C# musí splňovat následující pravidla:

- To zahrnuje i `public` a `static` modifikátor.
- Zahrnuje `operator X` kde `X` je název nebo symbol přetížení operátoru.
- Unární operátory mít jeden parametr a binární operátory mají dva parametry. V každém případě alespoň jeden parametr musí být stejného typu jako třída nebo struktura, která deklaruje operátor.

Informace o tom, jak definovat operátory převodu, najdete v článku [explicitní](explicit.md) a [implicitní](implicit.md) články – klíčové slovo.

Přehled, které mohou být přetíženy operátory jazyka C# najdete v tématu [přetížitelné operátory](../../programming-guide/statements-expressions-operators/overloadable-operators.md) článku.

## <a name="example"></a>Příklad

Následující příklad definuje `Fraction` typ, který představuje desetinná čísla. Přetěžuje `+` a `*` operátory provádět desetinné sčítání a násobení a také poskytuje operátor převodu které převádí `Fraction` typ, který `double` typu.

[!code-csharp[csrefKeywordsConversion#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#6)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [implicit](implicit.md)
- [explicit](explicit.md)
- [Přetížitelné operátory](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
- [Postupy: Implementace uživatelem definovaných převodů mezi strukturami](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
