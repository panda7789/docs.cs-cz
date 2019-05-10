---
title: Objektová proměnná nebo proměnná bloku With nebyla nastavena.
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: 766b95163f164ec76135b964115069b6855ceebf
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64750674"
---
# <a name="object-variable-or-with-block-variable-not-set"></a>Objektová proměnná nebo proměnná bloku With nebyla nastavena.
Odkazují na neplatný objekt proměnnou.   Této chybě může dojít z několika důvodů:

- Proměnná byla deklarovaná bez zadaného typu. Pokud je proměnná deklarována bez určení typu, použije se výchozí typ `Object`.

    Například proměnná deklarovaná pomocí `Dim x` budou mít typ `Object;` proměnná deklarovaná pomocí `Dim x As String` budou mít typ `String`.

    > [!TIP]
    >  `Option Strict` Příkaz zakáže implicitního zápisu, která vede `Object` typu. Vynecháte-li typ, dojde k chybě kompilace. Zobrazit [Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md).

- Pokoušíte se odkazovat na objekt, který je nastavená na `Nothing`.

- Pokoušíte se o přístup k prvku, který nebyl správně deklarované proměnné pole.

    Například pole deklarované jako `products() As String` chyba se aktivuje, pokud se pokusíte odkazovat na prvek pole `products(3) = "Widget"`. Pole neobsahuje žádné prvky a je považován za objekt.

- Pokoušíte se přístupový kód v rámci `With...End With` blokovat před inicializací bloku.   A `With...End With` bloku se musí inicializovat pomocí provádí `With` příkaz vstupní bod.

> [!NOTE]
> V dřívějších verzích jazyka Visual Basic nebo VBA k této chybě také aktivovaly přiřazení hodnoty proměnné bez použití `Set` – klíčové slovo (`x = "name"` místo `Set x = "name"`). `Set` – Klíčové slovo již není platný v jazyce Visual Basic .net.

## <a name="to-correct-this-error"></a>Oprava této chyby

1. Nastavte `Option Strict` k `On` na začátek souboru přidejte následující kód:

    ```vb
    Option Strict On
    ```

    Při spuštění projektu se objevit Chyba kompilátoru **seznam chyb** jakékoli proměnné, který byl zadán bez typu.

2. Pokud nechcete povolit `Option Strict`, vyhledávání v kódu pro všechny proměnné, které byly zadány bez typu (`Dim x` místo `Dim x As String`) a přidejte odpovídající typu k deklaraci.

3. Ujistěte se, že nejsou odkazující na proměnné objektu, která byla nastavena na `Nothing`.  Vyhledávání v kódu pro klíčové slovo `Nothing`a upravte kód tak, aby objekt není nastaven na `Nothing` až poté, co mají odkazovat.

4. Ujistěte se, že jsou všechny proměnné pole dimenzovanými předtím, než k nim přístup. Dimenze můžete přiřadit při prvním vytvoření pole (`Dim x(5) As String` místo `Dim x() As String`), nebo použijte `ReDim` – klíčové slovo k nastavení rozměrů pole před první přístup.

5. Ujistěte se, že vaše `With` bloku je inicializován pomocí provádí `With` příkaz vstupní bod.

## <a name="see-also"></a>Viz také:

- [Deklarace objektové proměnné](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Příkaz ReDim](../../../visual-basic/language-reference/statements/redim-statement.md)
- [Příkaz With...End With](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
