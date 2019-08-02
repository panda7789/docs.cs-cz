---
title: 'Postupy: Vytvořit novou proměnnou (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: a6cb7225ea203f0b38b731795684bfb0cfdfd2d1
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630896"
---
# <a name="how-to-create-a-new-variable-visual-basic"></a>Postupy: Vytvořit novou proměnnou (Visual Basic)

Vytvoříte proměnnou pomocí [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).

### <a name="to-create-a-new-variable"></a>Vytvoření nové proměnné

1. Deklarujte proměnnou v `Dim` příkazu.

    ```vb
    Dim newCustomer
    ```

2. Zahrňte specifikace charakteristik proměnných, jako jsou [Private](../../../../visual-basic/language-reference/modifiers/private.md), [static](../../../../visual-basic/language-reference/modifiers/static.md), Shadows [](../../../../visual-basic/language-reference/modifiers/shadows.md)nebo [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md). Další informace naleznete v tématu [deklarované charakteristiky elementu](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).

    ```vb
    Public Static newCustomer
    ```

    Klíčové slovo nemusíte `Dim` potřebovat, pokud v deklaraci použijete jiná klíčová slova.

3. Postupujte podle specifikace s názvem proměnné, který musí dodržovat pravidla Visual Basic a konvence. Další informace naleznete v tématu [deklarované názvy elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).

    ```vb
    Public Static newCustomer
    ```

4. Podle názvu s klauzulí [as](../../../../visual-basic/language-reference/statements/as-clause.md) určete datový typ proměnné.

    ```vb
    Public Static newCustomer As Customer
    ```

    Pokud datový typ nezadáte, použije se výchozí hodnota: `Object`.

5. Použijte klauzuli symbolem rovná se (`=`) a použijte symbol rovná se s počáteční hodnotou proměnné. `As`

    Visual Basic přiřazuje zadanou hodnotu proměnné při každém spuštění `Dim` příkazu. Pokud nezadáte počáteční hodnotu, Visual Basic přiřadí výchozí počáteční hodnotu pro datový typ proměnné při prvním zadání kódu, který obsahuje `Dim` příkaz.

    Pokud je proměnná typem odkazu, můžete vytvořit instanci své třídy zahrnutím klíčového slova [New operátor](../../../../visual-basic/language-reference/operators/new-operator.md) do `As` klauzule. Pokud nepoužijete `New`, počáteční hodnota proměnné není [Nothing](../../../../visual-basic/language-reference/nothing.md).

    ```vb
    Public Static newCustomer As New Customer
    ```

## <a name="see-also"></a>Viz také:

- [Proměnné](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Deklarované názvy elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Deklarované charakteristiky elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Příkazy](../../../../visual-basic/language-reference/statements/index.md)
- [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Příkaz Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
