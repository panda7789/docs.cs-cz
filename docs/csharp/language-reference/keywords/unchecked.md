---
title: nezaškrtnuté klíčové slovo C# – odkaz
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: 6dad0dfd508fb390dd0a52d1b48d70b4c5725513
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712998"
---
# <a name="unchecked-c-reference"></a>unchecked (Referenční dokumentace jazyka C#)

Klíčové slovo `unchecked` slouží k potlačení kontroly přetečení pro aritmetické operace a převody integrálního typu.

V nekontrolovaném kontextu, pokud výraz vytvoří hodnotu, která je mimo rozsah cílového typu, přetečení není označeno příznakem. Například vzhledem k tomu, že výpočet v následujícím příkladu je proveden v `unchecked` bloku nebo výrazu, je fakt, že výsledek je příliš velký pro celé číslo, ignorován a `int1` je přiřazena hodnota-2 147 483 639.

[!code-csharp[csrefKeywordsChecked#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#5)]

Pokud je prostředí `unchecked` odebrané, dojde k chybě kompilace. Přetečení lze zjistit v době kompilace, protože všechny výrazy výrazu jsou konstanty.

Výrazy, které obsahují nekonstantní podmínky, jsou ve výchozím nastavení v době kompilace a v době spuštění nezaškrtnuté. Další informace o povolení kontrolovaného prostředí naleznete v tématu [checked](checked.md) .

Vzhledem k tomu, že kontrola přetečení trvá, použití nekontrolovaného kódu v situacích, kdy nehrozí nebezpečí přetečení, může zvýšit výkon. Pokud je ale možnost přetečení, měla by se použít kontrolované prostředí.

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak použít klíčové slovo `unchecked`.

[!code-csharp[csrefKeywordsChecked#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#2)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Zaškrtnuto a nezaškrtnuto](checked-and-unchecked.md)
- [checked](checked.md)
