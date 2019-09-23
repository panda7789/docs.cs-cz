---
title: operátor stackalloc – C# odkaz
ms.custom: seodec18
ms.date: 09/20/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: 9ef5f98f2b4973c5873417ecc9a71c187e7299b9
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182415"
---
# <a name="stackalloc-operator-c-reference"></a>stackalloc – operátorC# (Referenční dokumentace)

`stackalloc` Operátor přiděluje blok paměti v zásobníku. Blok paměti přidělený zásobníkem, který byl vytvořen během provádění metody, je automaticky zahozen při návratu této metody. Nemůžete explicitně uvolnit paměť přidělenou `stackalloc` operátorem. Blok paměti přidělený zásobníku nepodléhá uvolňování [sběr odpadků](../../../standard/garbage-collection/index.md) paměti a nemusí být připnutý s [ `fixed` příkazem](../keywords/fixed-statement.md).

Ve výrazu `stackalloc T[E]` `int`  `E` musí být [nespravovaný typ](../builtin-types/unmanaged-types.md) a musí to být výraz typu. `T`

Výsledek `stackalloc` operátoru můžete přiřadit proměnné jednoho z následujících typů:

- Počínaje C# 7,2, <xref:System.Span%601?displayProperty=nameWithType> nebo <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, jak ukazuje následující příklad:

  [!code-csharp[stackalloc span](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToSpan)]

  Nemusíte používat [nezabezpečený](../keywords/unsafe.md) kontext, když přiřadíte blok paměti přidělené zásobníku <xref:System.Span%601> k <xref:System.ReadOnlySpan%601> proměnné nebo.

  Při práci s těmito typy můžete použít `stackalloc` výraz ve výrazech [podmíněného](conditional-operator.md) nebo přiřazení, jak ukazuje následující příklad:

  [!code-csharp[stackalloc expression](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AsExpression)]

  Počínaje C# 8,0 můžete použít `stackalloc` výraz uvnitř <xref:System.Span%601> jiných výrazů vždy, když je povolena proměnná nebo <xref:System.ReadOnlySpan%601> , jak je uvedeno v následujícím příkladu:

  [!code-csharp[stackalloc in nested expressions](~/samples/csharp/language-reference/operators/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > Pokud je to <xref:System.Span%601> možné <xref:System.ReadOnlySpan%601> , doporučujeme používat typy nebo pro práci s přidělenou pamětí zásobníku.

- [Typ ukazatele](../../programming-guide/unsafe-code-pointers/pointer-types.md), jak ukazuje následující příklad:

  [!code-csharp[stackalloc pointer](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToPointer)]

  Jak ukazuje předchozí příklad, je nutné použít `unsafe` kontext při práci s typy ukazatelů.

  V případě typů ukazatelů můžete použít `stackalloc` výraz pouze v deklaraci lokální proměnné pro inicializaci proměnné.

Obsah nově přidělené paměti není definován. Počínaje C# 7,3 můžete použít syntaxi inicializátoru pole k definování obsahu nově přidělené paměti. Následující příklad ukazuje různé způsoby, jak to provést:

[!code-csharp[stackalloc initialization](~/samples/csharp/language-reference/operators/StackallocOperator.cs#StackallocInit)]

## <a name="security"></a>Zabezpečení

V modulu CLR `stackalloc` (Common Language Runtime) se použití funkce automaticky zapne k detekci přetečení vyrovnávací paměti. Pokud se zjistí přetečení vyrovnávací paměti, proces se ukončí co nejrychleji, aby se minimalizovala pravděpodobnost spuštění škodlivého kódu.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [alokace zásobníku](~/_csharplang/spec/unsafe-code.md#stack-allocation) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- [Operátory související s ukazateli](pointer-related-operators.md)
- [Typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Typy související s Memory a Span](../../../standard/memory-and-spans/index.md)
