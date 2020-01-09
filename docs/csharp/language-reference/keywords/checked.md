---
title: 'zaškrtnuté: C# odkaz na klíčové slovo'
ms.date: 07/20/2015
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
ms.openlocfilehash: 5963bb85ef4b61c1dc478667fb0e2e5438f3e4ad
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713706"
---
# <a name="checked-c-reference"></a>checked (Referenční dokumentace jazyka C#)

Klíčové slovo `checked` slouží k explicitnímu povolení kontroly přetečení pro aritmetické operace a převody integrálního typu.

Ve výchozím nastavení výraz, který obsahuje pouze konstantní hodnoty, způsobí chybu kompilátoru, pokud výraz vytvoří hodnotu, která je mimo rozsah cílového typu. Pokud výraz obsahuje jednu nebo více nekonstantních hodnot, kompilátor nerozpozná přetečení. Vyhodnocení výrazu přiřazeného k `i2` v následujícím příkladu nezpůsobí chybu kompilátoru.

[!code-csharp[csrefKeywordsChecked#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#3)]

Ve výchozím nastavení nejsou tyto nekonstantní výrazy kontrolovány pro přetečení v době běhu a nevyvolávají výjimky přetečení. Předchozí příklad zobrazí-2 147 483 639 jako součet dvou kladných celých čísel.

Kontrolu přetečení lze povolit pomocí možností kompilátoru, konfigurace prostředí nebo použití klíčového slova `checked`. Následující příklady ukazují, jak použít výraz `checked` nebo blok `checked` k detekci přetečení, které je vyrobeno předchozí součtem v době běhu. Oba příklady vyvolávají výjimku přetečení.

[!code-csharp[csrefKeywordsChecked#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#4)]

[Nezaškrtnuté](./unchecked.md) klíčové slovo lze použít k zabránění kontrole přetečení.

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak použít `checked` pro povolení kontroly přetečení v době běhu.

[!code-csharp[csrefKeywordsChecked#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#1)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](./index.md)
- [Zaškrtnuto a nezaškrtnuto](./checked-and-unchecked.md)
- [unchecked](./unchecked.md)
