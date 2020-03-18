---
title: operátor stackalloc - odkaz C#
ms.date: 09/20/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: 9c9767e0c9945a9589d049fa7abba192cb928ad5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846247"
---
# <a name="stackalloc-operator-c-reference"></a>operátor stackalloc (odkaz C#

Operátor `stackalloc` přiděluje blok paměti v zásobníku. Blok přidělené paměti zásobníku vytvořený během spuštění metody je automaticky zahozen, když se tato metoda vrátí. Nelze explicitně uvolnit paměť `stackalloc` přidělenou operátoru. Blok přidělené paměti zásobníku nepodléhá [uvolňování paměti](../../../standard/garbage-collection/index.md) a nemusí být připnut [ `fixed` příkazem](../keywords/fixed-statement.md).

Výsledek operátoru `stackalloc` můžete přiřadit proměnné jednoho z následujících typů:

- Počínaje C# <xref:System.Span%601?displayProperty=nameWithType> 7.2, <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>nebo , jak ukazuje následující příklad:

  [!code-csharp[stackalloc span](snippets/StackallocOperator.cs#AssignToSpan)]

  Není třeba používat [nebezpečný](../keywords/unsafe.md) kontext při přiřazení bloku přidělené paměti <xref:System.Span%601> zásobníku nebo <xref:System.ReadOnlySpan%601> proměnné.

  Při práci s těmito typy `stackalloc` můžete použít výraz ve [výrazech podmíněné](conditional-operator.md) nebo přiřazení, jak ukazuje následující příklad:

  [!code-csharp[stackalloc expression](snippets/StackallocOperator.cs#AsExpression)]

  Počínaje c# 8.0, můžete `stackalloc` použít výraz uvnitř jiných <xref:System.Span%601> <xref:System.ReadOnlySpan%601> výrazů vždy, když je povolena nebo proměnná, jak ukazuje následující příklad:

  [!code-csharp[stackalloc in nested expressions](snippets/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > Doporučujeme <xref:System.Span%601> používat <xref:System.ReadOnlySpan%601> nebo typy pro práci s přidělenou pamětí zásobníku, kdykoli je to možné.

- [Typ ukazatele](../../programming-guide/unsafe-code-pointers/pointer-types.md), jak ukazuje následující příklad:

  [!code-csharp[stackalloc pointer](snippets/StackallocOperator.cs#AssignToPointer)]

  Jak ukazuje předchozí příklad, musíte `unsafe` použít kontext při práci s typy ukazatelů.

  V případě typů ukazatelů můžete použít `stackalloc` výraz pouze v deklaraci místní proměnné k inicializaci proměnné.

Obsah nově přidělené paměti není definován. Počínaje C# 7.3, můžete použít syntaxi inicializátoru pole k definování obsahu nově přidělené paměti. Následující příklad ukazuje různé způsoby, jak to provést:

[!code-csharp[stackalloc initialization](snippets/StackallocOperator.cs#StackallocInit)]

Ve `stackalloc T[E]`výrazu musí `T` být [nespravovaný typ](../builtin-types/unmanaged-types.md) a `E` musí být výrazem typu [int](../builtin-types/integral-numeric-types.md).

## <a name="security"></a>Zabezpečení

Použití `stackalloc` automaticky umožňuje funkce detekce přetečení vyrovnávací paměti v clr (COMMON Language runtime). Pokud je zjištěno přetečení vyrovnávací paměti, proces je ukončen co nejrychleji minimalizovat pravděpodobnost spuštění škodlivého kódu.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [Přidělení zásobníku](~/_csharplang/spec/unsafe-code.md#stack-allocation) [specifikace jazyka C#](~/_csharplang/spec/introduction.md) a [povolit `stackalloc` v vnořených kontextech](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) poznámka k návrhu funkce.

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory jazyka C#](index.md)
- [Operátory související s ukazatelem](pointer-related-operators.md)
- [Typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Typy související s Memory a Span](../../../standard/memory-and-spans/index.md)
