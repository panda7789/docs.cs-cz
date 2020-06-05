---
title: 'Postupy: Vytvoření nové proměnné'
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: 501c8f3aff4c5b204d231bdc26213e13d125a7cf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410526"
---
# <a name="how-to-create-a-new-variable-visual-basic"></a>Postupy: Vytvoření nové proměnné (Visual Basic)

Vytvoříte proměnnou pomocí [příkazu Dim](../../../language-reference/statements/dim-statement.md).

### <a name="to-create-a-new-variable"></a>Vytvoření nové proměnné

1. Deklarujte proměnnou v `Dim` příkazu.

    ```vb
    Dim newCustomer
    ```

2. Zahrňte specifikace charakteristik proměnných, jako jsou [Private](../../../language-reference/modifiers/private.md), [static](../../../language-reference/modifiers/static.md), [Shadows](../../../language-reference/modifiers/shadows.md)nebo [WithEvents](../../../language-reference/modifiers/withevents.md). Další informace naleznete v tématu [deklarované charakteristiky elementu](../declared-elements/declared-element-characteristics.md).

    ```vb
    Public Static newCustomer
    ```

    Klíčové slovo nemusíte potřebovat, `Dim` Pokud v deklaraci použijete jiná klíčová slova.

3. Postupujte podle specifikace s názvem proměnné, který musí dodržovat pravidla Visual Basic a konvence. Další informace naleznete v tématu [deklarované názvy elementů](../declared-elements/declared-element-names.md).

    ```vb
    Public Static newCustomer
    ```

4. Podle názvu s klauzulí [as](../../../language-reference/statements/as-clause.md) určete datový typ proměnné.

    ```vb
    Public Static newCustomer As Customer
    ```

    Pokud datový typ nezadáte, použije se výchozí hodnota: `Object` .

5. Použijte klauzuli symbolem `As` rovná se ( `=` ) a použijte symbol rovná se s počáteční hodnotou proměnné.

    Visual Basic přiřazuje zadanou hodnotu proměnné při každém spuštění `Dim` příkazu. Pokud nezadáte počáteční hodnotu, Visual Basic přiřadí výchozí počáteční hodnotu pro datový typ proměnné při prvním zadání kódu, který obsahuje `Dim` příkaz.

    Pokud je proměnná typem odkazu, můžete vytvořit instanci své třídy zahrnutím klíčového slova [New operátor](../../../language-reference/operators/new-operator.md) do `As` klauzule. Pokud nepoužijete `New` , počáteční hodnota proměnné není [Nothing](../../../language-reference/nothing.md).

    ```vb
    Public Static newCustomer As New Customer
    ```

## <a name="see-also"></a>Viz také

- [Proměnné](index.md)
- [Deklarace proměnné](variable-declaration.md)
- [Deklarované názvy elementů](../declared-elements/declared-element-names.md)
- [Deklarované charakteristiky elementů](../declared-elements/declared-element-characteristics.md)
- [Typy hodnot a typy odkazu](../data-types/value-types-and-reference-types.md)
- [Příkazy](../../../language-reference/statements/index.md)
- [Odvození místního typu](local-type-inference.md)
- [Option Infer – příkaz](../../../language-reference/statements/option-infer-statement.md)
