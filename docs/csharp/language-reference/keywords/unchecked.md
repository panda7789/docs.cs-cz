---
description: nezaškrtnuté klíčové slovo – Reference jazyka C#
title: nezaškrtnuté klíčové slovo – Reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: bb66639e3657b247b9ebcad1594daf1f57a5c76b
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141982"
---
# <a name="unchecked-c-reference"></a>unchecked (Referenční dokumentace jazyka C#)

`unchecked`Klíčové slovo slouží k potlačení kontroly přetečení pro aritmetické operace a převody integrálního typu.

V nekontrolovaném kontextu, pokud výraz vytvoří hodnotu, která je mimo rozsah cílového typu, přetečení není označeno příznakem. Například vzhledem k tomu, že výpočet v následujícím příkladu je proveden v `unchecked` bloku nebo výrazu, je fakt, že výsledek je příliš velký pro celé číslo, ignorován a `int1` je přiřazena hodnota-2 147 483 639.

[!code-csharp[csrefKeywordsChecked#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#5)]

Pokud `unchecked` je prostředí odebráno, dojde k chybě kompilace. Přetečení lze zjistit v době kompilace, protože všechny výrazy výrazu jsou konstanty.

Výrazy, které obsahují nekonstantní podmínky, jsou ve výchozím nastavení v době kompilace a v době spuštění nezaškrtnuté. Další informace o povolení kontrolovaného prostředí naleznete v tématu [checked](checked.md) .

Vzhledem k tomu, že kontrola přetečení trvá, použití nekontrolovaného kódu v situacích, kdy nehrozí nebezpečí přetečení, může zvýšit výkon. Pokud je ale možnost přetečení, měla by se použít kontrolované prostředí.

## <a name="example"></a>Příklad

Tato ukázka ukazuje, jak použít `unchecked` klíčové slovo.

[!code-csharp[csrefKeywordsChecked#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#2)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Checked a Unchecked](checked-and-unchecked.md)
- [kontrolovaný](checked.md)
