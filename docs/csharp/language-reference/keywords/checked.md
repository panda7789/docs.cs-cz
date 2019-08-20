---
title: 'zaškrtnuté: C# odkaz na klíčové slovo'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
ms.openlocfilehash: 69bd8cc95012533a6be279b04dc883a56f6f78ea
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605909"
---
# <a name="checked-c-reference"></a>checked (Referenční dokumentace jazyka C#)

`checked` Klíčové slovo slouží k explicitnímu povolení kontroly přetečení pro aritmetické operace a převody integrálního typu.

Ve výchozím nastavení výraz, který obsahuje pouze konstantní hodnoty, způsobí chybu kompilátoru, pokud výraz vytvoří hodnotu, která je mimo rozsah cílového typu. Pokud výraz obsahuje jednu nebo více nekonstantních hodnot, kompilátor nerozpozná přetečení. Vyhodnocení výrazu přiřazeného `i2` v následujícím příkladu nezpůsobí chybu kompilátoru.

[!code-csharp[csrefKeywordsChecked#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#3)]

Ve výchozím nastavení nejsou tyto nekonstantní výrazy kontrolovány pro přetečení v době běhu a nevyvolávají výjimky přetečení. Předchozí příklad zobrazí-2 147 483 639 jako součet dvou kladných celých čísel.

Kontrolu přetečení lze povolit pomocí možností kompilátoru, konfigurace prostředí nebo použití `checked` klíčového slova. Následující příklady ukazují, jak použít `checked` výraz `checked` nebo blok k detekci přetečení, které je vyrobeno předchozí součtem v době běhu. Oba příklady vyvolávají výjimku přetečení.

[!code-csharp[csrefKeywordsChecked#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#4)]

Nezaškrtnuté klíčové slovo lze použít k zabránění kontrole přetečení. [](./unchecked.md)

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak použít `checked` k povolení kontroly přetečení v době běhu.

[!code-csharp[csrefKeywordsChecked#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#1)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](./index.md)
- [Zaškrtnuto a nezaškrtnuto](./checked-and-unchecked.md)
- [unchecked](./unchecked.md)
