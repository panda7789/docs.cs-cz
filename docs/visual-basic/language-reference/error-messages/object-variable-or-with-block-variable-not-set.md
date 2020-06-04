---
title: Objektová proměnná nebo proměnná bloku With nebyla nastavena.
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: d1778e2bb58d32e976f10b3fba1637918278d36e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409280"
---
# <a name="object-variable-or-with-block-variable-not-set"></a>Objektová proměnná nebo proměnná bloku With nebyla nastavena.
Je odkazováno na neplatnou proměnnou objektu.   K této chybě může dojít z několika důvodů:

- Proměnná byla deklarována bez určení typu. Je-li proměnná deklarována bez určení typu, je použita výchozí hodnota typu `Object` .

    Například Proměnná deklarovaná s by měla `Dim x` být typu `Object;` Proměnná s deklarací `Dim x As String` by byla typu `String` .

    > [!TIP]
    > `Option Strict`Příkaz nepovoluje implicitní zadání, které má za následek `Object` typ. Pokud vynecháte typ, dojde k chybě při kompilaci. Viz [příkaz Option Strict](../statements/option-strict-statement.md).

- Pokoušíte se vytvořit odkaz na objekt, který byl nastaven na hodnotu `Nothing` .

- Pokoušíte se o přístup k prvku proměnné pole, která nebyla správně deklarována.

    Například pole deklarované jako `products() As String` aktivuje chybu, pokud se pokusíte odkazovat na prvek pole `products(3) = "Widget"` . Pole nemá žádné elementy a je považováno za objekt.

- Pokoušíte se o přístup k kódu v rámci `With...End With` bloku před inicializací bloku.   `With...End With`Blok musí být inicializován spuštěním `With` vstupního bodu příkazu.

> [!NOTE]
> V dřívějších verzích Visual Basic nebo v jazyce VBA se tato chyba aktivovala také přiřazením hodnoty proměnné bez použití `Set` klíčového slova ( `x = "name"` místo `Set x = "name"` ). `Set`Klíčové slovo již není platné v Visual Basic .NET.

## <a name="to-correct-this-error"></a>Oprava této chyby

1. Nastavte `Option Strict` na `On` začátek souboru přidáním následujícího kódu:

    ```vb
    Option Strict On
    ```

    Při spuštění projektu se zobrazí chyba kompilátoru v **Seznam chyb** pro jakoukoliv proměnnou, která byla zadána bez typu.

2. Pokud nechcete povolit `Option Strict` , vyhledejte v kódu proměnné, které byly zadány bez typu ( `Dim x` namísto `Dim x As String` ) a přidejte do deklarace zamýšlený typ.

3. Ujistěte se, že neodkazujete na proměnnou objektu, která je nastavená na `Nothing` .  Vyhledejte kód klíčového slova `Nothing` a upravte kód tak, aby objekt nebyl nastaven na hodnotu `Nothing` až po jeho odkazování.

4. Ujistěte se, že všechny proměnné pole jsou dimenze, než k nim přistupujete. Dimenzi můžete přiřadit buď při prvním vytvoření pole ( `Dim x(5) As String` místo `Dim x() As String` ), nebo pomocí `ReDim` klíčového slova pro nastavení rozměrů pole před prvním přístupem.

5. Zajistěte, aby `With` byl váš blok inicializován spuštěním `With` vstupního bodu příkazu.

## <a name="see-also"></a>Viz také

- [Deklarace proměnné objektu](../../programming-guide/language-features/variables/object-variable-declaration.md)
- [ReDim – příkaz](../statements/redim-statement.md)
- [With...End With – příkaz](../statements/with-end-with-statement.md)
