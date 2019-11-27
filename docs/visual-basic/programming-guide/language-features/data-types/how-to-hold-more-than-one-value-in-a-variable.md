---
title: 'Postupy: Do proměnné umístit více než jednu hodnotu'
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- arrays [Visual Basic], compilation errors
- types [Visual Basic], composite
ms.assetid: 5fe0e558-aac2-4a40-b7f2-7cfea7336917
ms.openlocfilehash: d452fbf35f9d200348234b38c40f8636f0ec4b4e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350019"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a>Postupy: Do proměnné umístit více než jednu hodnotu (Visual Basic)

Proměnná obsahuje více než jednu hodnotu, pokud deklarujete jako *složený datový typ*.

[Složené datové typy](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) zahrnují struktury, pole a třídy. Proměnná složeného datového typu může obsahovat kombinaci základních datových typů a dalších složených typů. Struktury a třídy mohou uchovávat kód i data.

## <a name="to-hold-more-than-one-value-in-a-variable"></a>Uložení více než jedné hodnoty v proměnné

1. Určete, jaký typ složeného dat chcete pro proměnnou použít.

2. Pokud se složený datový typ ještě nedefinuje, definujte ho, aby ho vaše proměnná mohla použít.

    - Definujte strukturu pomocí [příkazu struktury](../../../../visual-basic/language-reference/statements/structure-statement.md).

    - Definujte pole pomocí [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).

    - Definujte třídu pomocí [příkazu třídy](../../../../visual-basic/language-reference/statements/class-statement.md).

3. Deklarujte proměnnou pomocí příkazu `Dim`.

4. Použijte název proměnné s klauzulí `As`.

5. Použijte klíčové slovo `As` s názvem vhodného složeného datového typu.

## <a name="see-also"></a>Viz také:

- [Datové typy](../../../../visual-basic/language-reference/data-types/index.md)
- [Znaky typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [Složené datové typy](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Objekty a třídy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
