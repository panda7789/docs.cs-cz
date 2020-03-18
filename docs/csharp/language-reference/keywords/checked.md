---
title: zaškrtnuté klíčové slovo – odkaz jazyka C#
ms.date: 07/20/2015
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
ms.openlocfilehash: 5963bb85ef4b61c1dc478667fb0e2e5438f3e4ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713706"
---
# <a name="checked-c-reference"></a>checked (Referenční dokumentace jazyka C#)

Klíčové `checked` slovo se používá k explicitnímu povolení kontroly přetečení pro aritmetické operace a převody integrálního typu.

Ve výchozím nastavení výraz, který obsahuje pouze konstantní hodnoty způsobí chybu kompilátoru, pokud výraz vytváří hodnotu, která je mimo rozsah cílového typu. Pokud výraz obsahuje jednu nebo více nekonstantních hodnot, kompilátor nezjistí přetečení. Vyhodnocení výrazu přiřazeného v `i2` následujícím příkladu nezpůsobí chybu kompilátoru.

[!code-csharp[csrefKeywordsChecked#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#3)]

Ve výchozím nastavení tyto nekonstantní výrazy nejsou kontrolovány pro přetečení v době běhu buď a nevyvolávají výjimky přetečení. Předchozí příklad zobrazí -2,147,483,639 jako součet dvou kladných celá čísla.

Kontrola přetečení může být povolena možnostmi kompilátoru, konfigurací prostředí nebo použitím klíčového `checked` slova. Následující příklady ukazují, jak `checked` použít `checked` výraz nebo blok ke zjištění přetečení, které je produkováno předchozím součtem za běhu. Oba příklady vyvolávají výjimku přetečení.

[!code-csharp[csrefKeywordsChecked#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#4)]

[Nezaškrtnuté](./unchecked.md) klíčové slovo lze použít k zabránění přetečení kontroly.

## <a name="example"></a>Příklad

Tato ukázka ukazuje, jak použít `checked` k povolení kontroly přetečení za běhu.

[!code-csharp[csrefKeywordsChecked#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#1)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](./index.md)
- [Checked a Unchecked](./checked-and-unchecked.md)
- [unchecked](./unchecked.md)
