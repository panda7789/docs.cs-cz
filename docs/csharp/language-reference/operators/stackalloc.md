---
title: operátor stackalloc – C# odkaz
ms.custom: seodec18
ms.date: 06/10/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: eeacd7628a11c87c8d21c7b18687892105374587
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2019
ms.locfileid: "66834100"
---
# <a name="stackalloc-operator-c-reference"></a>operátor stackalloc (C# odkaz)

`stackalloc` Operátor přiděluje blok paměti v zásobníku. Zásobníku přidělený blok paměti, vytvořené během provádění metody se automaticky zruší po návratu tato metoda. Nelze explicitně uvolnit paměť alokována `stackalloc` operátor. Blok paměti přidělené zásobník není podléhají [uvolňování](../../../standard/garbage-collection/index.md) a nemusí být připojená s [ `fixed` příkaz](../keywords/fixed-statement.md).

Můžete přiřadit výsledek `stackalloc` operátor proměnné jednu z následujících typů:

- Počínaje C# 7.2, <xref:System.Span%601?displayName=nameWithType> nebo <xref:System.ReadOnlySpan%601?displayName=nameWithType>, jak je vidět v následujícím příkladu:

  [!code-csharp[stackalloc span](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToSpan)]

  Není nutné používat `unsafe` kontextu při přiřazování zásobníku přidělený blok paměti k <xref:System.Span%601> nebo <xref:System.ReadOnlySpan%601> proměnné.

  Při práci s těmito typy, můžete použít `stackalloc` výrazu v [podmíněného](conditional-operator.md) nebo výrazy přiřazení, jak ukazuje následující příklad:

  [!code-csharp[stackalloc expression](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AsExpression)]

  > [!NOTE]
  > Doporučujeme používat <xref:System.Span%601> nebo <xref:System.ReadOnlySpan%601> typy pro práci s zásobníku přidělenou paměť, kdykoli je to možné.

- A [typ ukazatele](../../programming-guide/unsafe-code-pointers/pointer-types.md), jak je vidět v následujícím příkladu:

  [!code-csharp[stackalloc pointer](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToPointer)]

  Jak ukazuje předchozí příklad, musíte použít [nebezpečné](../keywords/unsafe.md) kontextu při práci s typy ukazatelů.

Obsah nově přidělenou paměť není definován. Počínaje C# 7.3, můžete použít syntaxi inicializátoru pole definovat obsah nově přidělenou paměť. Následující příklad ukazuje různé způsoby, jak to udělat:

[!code-csharp[stackalloc initialization](~/samples/csharp/language-reference/operators/StackallocOperator.cs#StackallocInit)]

## <a name="security"></a>Zabezpečení

Použití `stackalloc` automaticky povoluje funkce detekce přetečení vyrovnávací paměti v modulu common language runtime (CLR). Pokud se zjistí přetečení vyrovnávací paměti, co nejrychleji, chcete-li minimalizovat pravděpodobnost, že je proveden škodlivý kód ukončení procesu.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [zásobníku přidělení](~/_csharplang/spec/unsafe-code.md#stack-allocation) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#referenční dokumentace](../index.md)
- [Operátory jazyka C#](index.md)
- [Ukazatel související s operátory](pointer-related-operators.md)
- [Typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Typy související s Memory a Span](../../../standard/memory-and-spans/index.md)
