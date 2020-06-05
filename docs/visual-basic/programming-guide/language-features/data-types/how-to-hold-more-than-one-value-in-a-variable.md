---
title: 'Postupy: Uchování více než jedné hodnoty v proměnné'
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
ms.openlocfilehash: 399c5909ee6988f96bcc85260b0401f3bd18a0f2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393893"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a>Postupy: Do proměnné umístit více než jednu hodnotu (Visual Basic)

Proměnná obsahuje více než jednu hodnotu, pokud deklarujete jako *složený datový typ*.

[Složené datové typy](composite-data-types.md) zahrnují struktury, pole a třídy. Proměnná složeného datového typu může obsahovat kombinaci základních datových typů a dalších složených typů. Struktury a třídy mohou uchovávat kód i data.

## <a name="to-hold-more-than-one-value-in-a-variable"></a>Uložení více než jedné hodnoty v proměnné

1. Určete, jaký typ složeného dat chcete pro proměnnou použít.

2. Pokud se složený datový typ ještě nedefinuje, definujte ho, aby ho vaše proměnná mohla použít.

    - Definujte strukturu pomocí [příkazu struktury](../../../language-reference/statements/structure-statement.md).

    - Definujte pole pomocí [příkazu Dim](../../../language-reference/statements/dim-statement.md).

    - Definujte třídu pomocí [příkazu třídy](../../../language-reference/statements/class-statement.md).

3. Deklarujte proměnnou pomocí `Dim` příkazu.

4. Použijte název proměnné s `As` klauzulí.

5. Použijte `As` klíčové slovo s názvem vhodného složeného datového typu.

## <a name="see-also"></a>Viz také

- [Datové typy](../../../language-reference/data-types/index.md)
- [Znaky typu](type-characters.md)
- [Složené datové typy](composite-data-types.md)
- [Struktury](structures.md)
- [Pole](../arrays/index.md)
- [Objekty a třídy](../objects-and-classes/index.md)
- [Typy hodnot a typy odkazu](value-types-and-reference-types.md)
