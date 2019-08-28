---
title: Objektová proměnná nebo proměnná bloku With nebyla nastavena.
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: 07c215d373e4ac1cbadf82a48b8cb3d90efdbdb4
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040556"
---
# <a name="object-variable-or-with-block-variable-not-set"></a>Objektová proměnná nebo proměnná bloku With nebyla nastavena.
Je odkazováno na neplatnou proměnnou objektu.   K této chybě může dojít z několika důvodů:

- Proměnná byla deklarována bez určení typu. Je-li proměnná deklarována bez určení typu, je použita výchozí hodnota `Object`typu.

    `Dim x` Například Proměnná deklarovaná s by měla být typu `Object;` proměnná s `Dim x As String` deklarací by byla typu `String`.

    > [!TIP]
    > Příkaz nepovoluje implicitní zadání, které má `Object` za následek typ. `Option Strict` Pokud vynecháte typ, dojde k chybě při kompilaci. Viz [příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md).

- Pokoušíte se vytvořit odkaz na objekt, který byl nastaven na `Nothing`hodnotu.

- Pokoušíte se o přístup k prvku proměnné pole, která nebyla správně deklarována.

    Například pole deklarované jako `products() As String` aktivuje chybu, pokud se pokusíte odkazovat na prvek pole. `products(3) = "Widget"` Pole nemá žádné elementy a je považováno za objekt.

- Pokoušíte se o přístup k kódu v rámci `With...End With` bloku před inicializací bloku.   Blok musí být inicializován `With` spuštěním vstupního bodu příkazu. `With...End With`

> [!NOTE]
> V dřívějších verzích Visual Basic nebo v jazyce VBA se tato chyba aktivovala také přiřazením hodnoty proměnné bez použití `Set` klíčového slova (`x = "name"` místo `Set x = "name"`). `Set` Klíčové slovo již není platné v Visual Basic .NET.

## <a name="to-correct-this-error"></a>Oprava této chyby

1. Nastavte `Option Strict` na`On` začátek souboru přidáním následujícího kódu:

    ```vb
    Option Strict On
    ```

    Při spuštění projektu se zobrazí chyba kompilátoru v **Seznam chyb** pro jakoukoliv proměnnou, která byla zadána bez typu.

2. Pokud nechcete povolit `Option Strict`, vyhledejte v kódu proměnné, které byly zadány bez typu (`Dim x` namísto `Dim x As String`) a přidejte do deklarace zamýšlený typ.

3. Ujistěte se, že neodkazujete na proměnnou objektu, která je nastavená na `Nothing`.  Vyhledejte kód klíčového slova `Nothing`a upravte kód tak, aby objekt nebyl nastaven na `Nothing` hodnotu až po jeho odkazování.

4. Ujistěte se, že všechny proměnné pole jsou dimenze, než k nim přistupujete. Dimenzi můžete přiřadit buď při prvním vytvoření pole (`Dim x(5) As String` `Dim x() As String`místo `ReDim` ), nebo pomocí klíčového slova pro nastavení rozměrů pole před prvním přístupem.

5. Zajistěte `With` , aby byl váš blok inicializován `With` spuštěním vstupního bodu příkazu.

## <a name="see-also"></a>Viz také:

- [Deklarace objektové proměnné](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Příkaz ReDim](../../../visual-basic/language-reference/statements/redim-statement.md)
- [Příkaz With...End With](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
