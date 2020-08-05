---
title: Výraz stackalloc – Referenční dokumentace jazyka C#
ms.date: 03/13/2020
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc expression [C#]
ms.openlocfilehash: 32ac85f678912cb7e5f506244265b1bf57d0b4aa
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555603"
---
# <a name="stackalloc-expression-c-reference"></a>stackalloc – výraz (Referenční dokumentace jazyka C#)

`stackalloc`Výraz přiděluje blok paměti v zásobníku. Blok paměti přidělený zásobníkem, který byl vytvořen během provádění metody, je automaticky zahozen při návratu této metody. Paměť přidělená pomocí nelze explicitně uvolnit `stackalloc` . Blok paměti přidělený zásobníku nepodléhá [uvolňování](../../../standard/garbage-collection/index.md) paměti a nemusí být připnutý s [ `fixed` příkazem](../keywords/fixed-statement.md).

Výsledek výrazu můžete přiřadit `stackalloc` proměnné jednoho z následujících typů:

- Počínaje jazykem C# 7,2 <xref:System.Span%601?displayProperty=nameWithType> nebo <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> , jak ukazuje následující příklad:

  [!code-csharp[stackalloc span](snippets/StackallocOperator.cs#AssignToSpan)]

  Nemusíte používat [nezabezpečený](../keywords/unsafe.md) kontext, když přiřadíte blok paměti přidělené zásobníku <xref:System.Span%601> k <xref:System.ReadOnlySpan%601> proměnné nebo.

  Při práci s těmito typy můžete použít `stackalloc` výraz ve výrazech [podmíněného](conditional-operator.md) nebo přiřazení, jak ukazuje následující příklad:

  [!code-csharp[stackalloc expression](snippets/StackallocOperator.cs#AsExpression)]

  Počínaje jazykem C# 8,0 můžete použít `stackalloc` výraz uvnitř jiných výrazů vždy <xref:System.Span%601> <xref:System.ReadOnlySpan%601> , když je povolena proměnná nebo, jak je uvedeno v následujícím příkladu:

  [!code-csharp[stackalloc in nested expressions](snippets/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > <xref:System.Span%601> <xref:System.ReadOnlySpan%601> Pokud je to možné, doporučujeme používat typy nebo pro práci s přidělenou pamětí zásobníku.

- [Typ ukazatele](../../programming-guide/unsafe-code-pointers/pointer-types.md), jak ukazuje následující příklad:

  [!code-csharp[stackalloc pointer](snippets/StackallocOperator.cs#AssignToPointer)]

  Jak ukazuje předchozí příklad, je nutné použít `unsafe` kontext při práci s typy ukazatelů.

  V případě typů ukazatelů můžete použít `stackalloc` výraz pouze v deklaraci lokální proměnné pro inicializaci proměnné.

Velikost paměti, která je k dispozici v zásobníku, je omezená. Pokud přidělíte příliš mnoho paměti v zásobníku, <xref:System.StackOverflowException> je vyvolána. Abyste tomu předešli, postupujte podle následujících pravidel:

- Omezte velikost paměti, kterou přidělíte `stackalloc` :

  [!code-csharp[limit stackalloc](snippets/StackallocOperator.cs#LimitStackalloc)]

  Vzhledem k tomu, že množství paměti dostupné v zásobníku závisí na prostředí, ve kterém je kód spuštěný, je při definování skutečné mezní hodnoty konzervativní.

- Nepoužívejte `stackalloc` uvnitř smyček smyčky. Přidělte blok paměti mimo smyčku a znovu ho použijte uvnitř smyčky.

Obsah nově přidělené paměti není definován. Měli byste ji inicializovat před použitím. Například můžete použít <xref:System.Span%601.Clear%2A?displayProperty=nameWithType> metodu, která nastaví všechny položky na výchozí hodnotu typu `T` .

Počínaje jazykem C# 7,3 můžete použít syntaxi inicializátoru pole k definování obsahu nově přidělené paměti. Následující příklad ukazuje různé způsoby, jak to provést:

[!code-csharp[stackalloc initialization](snippets/StackallocOperator.cs#StackallocInit)]

Ve výrazu `stackalloc T[E]` `T` musí být [nespravovaný typ](../builtin-types/unmanaged-types.md) a `E` musí se vyhodnotit jako nezáporná hodnota typu [int](../builtin-types/integral-numeric-types.md) .

## <a name="security"></a>Zabezpečení

`stackalloc`V modulu CLR (Common Language Runtime) se použití funkce automaticky zapne k detekci přetečení vyrovnávací paměti. Pokud se zjistí přetečení vyrovnávací paměti, proces se ukončí co nejrychleji, aby se minimalizovala pravděpodobnost spuštění škodlivého kódu.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [alokace zásobníku](~/_csharplang/spec/unsafe-code.md#stack-allocation) v tématu [specifikace jazyka C#](~/_csharplang/spec/introduction.md) a poznámky k návrhu [funkce `stackalloc` vnořené kontexty](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) .

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory a výrazy v C#](index.md)
- [Operátory související s ukazatelem](pointer-related-operators.md)
- [Typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Typy související s Memory a Span](../../../standard/memory-and-spans/index.md)
- [DOS a Don'ts z stackalloc](https://vcsjones.dev/2020/02/24/stackalloc/)
