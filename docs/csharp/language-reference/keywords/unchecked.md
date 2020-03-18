---
title: nezaškrtnuté klíčové slovo – odkaz jazyka C#
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: 6dad0dfd508fb390dd0a52d1b48d70b4c5725513
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712998"
---
# <a name="unchecked-c-reference"></a>unchecked (Referenční dokumentace jazyka C#)

Klíčové `unchecked` slovo se používá k potlačení kontroly přetečení pro integrální typ aritmetické operace a převody.

V nekontrolovaném kontextu, pokud výraz vytvoří hodnotu, která je mimo rozsah cílového typu, přetečení není označeno příznakem. Například protože výpočet v následujícím příkladu `unchecked` se provádí v bloku nebo výrazu, skutečnost, že výsledek je `int1` příliš velký pro celé číslo je ignorována a je přiřazena hodnota -2,147,483,639.

[!code-csharp[csrefKeywordsChecked#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#5)]

Pokud `unchecked` je prostředí odebráno, dojde k chybě kompilace. Přetečení lze zjistit v době kompilace, protože všechny podmínky výrazu jsou konstanty.

Výrazy, které obsahují nekonstantní termíny, jsou ve výchozím nastavení nezaškrtnuté v době kompilace a běhu. Informace o povolení kontrolovaného prostředí naleznete [v tématu Zaškrtnuto](checked.md) je.

Vzhledem k tomu, že kontrola přetečení vyžaduje čas, použití nekontrolovaného kódu v situacích, kdy neexistuje žádné nebezpečí přetečení může zlepšit výkon. Pokud je však možné přetečení, je třeba použít kontrolované prostředí.

## <a name="example"></a>Příklad

Tato ukázka ukazuje, `unchecked` jak používat klíčové slovo.

[!code-csharp[csrefKeywordsChecked#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#2)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](index.md)
- [Checked a Unchecked](checked-and-unchecked.md)
- [Kontrolovány](checked.md)
