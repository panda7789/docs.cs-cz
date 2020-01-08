---
title: operátor stackalloc – C# odkaz
ms.custom: seodec18
ms.date: 09/20/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: 4f3ba6594eb16cf16db6a1de78fe05509c5f4d7d
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345274"
---
# <a name="stackalloc-operator-c-reference"></a>stackalloc – operátorC# (Referenční dokumentace)

Operátor `stackalloc` přiděluje blok paměti v zásobníku. Blok paměti přidělený zásobníkem, který byl vytvořen během provádění metody, je automaticky zahozen při návratu této metody. Nelze explicitně uvolnit paměť přidělenou operátorem `stackalloc`. Blok paměti přidělený zásobníku nepodléhá [uvolňování](../../../standard/garbage-collection/index.md) paměti a nemusí být připnutý s [příkazem`fixed`](../keywords/fixed-statement.md).

Výsledek operátoru `stackalloc` můžete přiřadit proměnné jednoho z následujících typů:

- Počínaje C# 7,2 <xref:System.Span%601?displayProperty=nameWithType> nebo <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, jak ukazuje následující příklad:

  [!code-csharp[stackalloc span](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToSpan)]

  Nemusíte používat [nezabezpečený](../keywords/unsafe.md) kontext, když přiřadíte blok paměti přidělené zásobníku k proměnné <xref:System.Span%601> nebo <xref:System.ReadOnlySpan%601>.

  Při práci s těmito typy můžete použít výraz `stackalloc` ve výrazech [podmíněného](conditional-operator.md) nebo přiřazení, jak ukazuje následující příklad:

  [!code-csharp[stackalloc expression](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AsExpression)]

  Počínaje C# 8,0 můžete použít výraz `stackalloc` v jiných výrazech vždy, když je povolena proměnná <xref:System.Span%601> nebo <xref:System.ReadOnlySpan%601>, jak ukazuje následující příklad:

  [!code-csharp[stackalloc in nested expressions](~/samples/csharp/language-reference/operators/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > Pokud je to možné, doporučujeme používat <xref:System.Span%601> nebo <xref:System.ReadOnlySpan%601> typy pro práci s přidělenou pamětí stacku.

- [Typ ukazatele](../../programming-guide/unsafe-code-pointers/pointer-types.md), jak ukazuje následující příklad:

  [!code-csharp[stackalloc pointer](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToPointer)]

  Jak ukazuje předchozí příklad, je nutné při práci s typy ukazatelů použít kontext `unsafe`.

  V případě typů ukazatelů můžete použít výraz `stackalloc` pouze v deklaraci lokální proměnné pro inicializaci proměnné.

Obsah nově přidělené paměti není definován. Počínaje C# 7,3 můžete použít syntaxi inicializátoru pole k definování obsahu nově přidělené paměti. Následující příklad ukazuje různé způsoby, jak to provést:

[!code-csharp[stackalloc initialization](~/samples/csharp/language-reference/operators/StackallocOperator.cs#StackallocInit)]

Ve výrazu `stackalloc T[E]`musí být `T` [nespravovaného typu](../builtin-types/unmanaged-types.md) a `E` musí být výraz typu [int](../builtin-types/integral-numeric-types.md).

## <a name="security"></a>Zabezpečení –

Použití `stackalloc` v modulu CLR (Common Language Runtime) automaticky povoluje funkce pro detekci přetečení vyrovnávací paměti. Pokud se zjistí přetečení vyrovnávací paměti, proces se ukončí co nejrychleji, aby se minimalizovala pravděpodobnost spuštění škodlivého kódu.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [alokace zásobníku](~/_csharplang/spec/unsafe-code.md#stack-allocation) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md) a v poznámce k návrhu funkce pro [Povolení `stackalloc` ve vnořených kontextech](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) .

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- [Operátory související s ukazateli](pointer-related-operators.md)
- [Typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Typy související s Memory a Span](../../../standard/memory-and-spans/index.md)
