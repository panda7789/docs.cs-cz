---
title: UInteger – datový typ
ms.date: 01/31/2018
f1_keywords:
- vb.uinteger
helpviewer_keywords:
- numbers [Visual Basic], whole
- UInteger data type
- literal type characters [Visual Basic], UI
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- UI literal type characters [Visual Basic]
- data types [Visual Basic], integral
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
ms.openlocfilehash: 11070f6c7f3259b8c34528eb54d99b031b68f9f9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415541"
---
# <a name="uinteger-data-type"></a>UInteger – datový typ

Obsahuje nepodepsaná 32 (4 bajt) celá čísla v rozsahu od 0 do 4 294 967 295.

## <a name="remarks"></a>Poznámky

`UInteger`Datový typ poskytuje největší hodnotu bez znaménka v nejúčinnější šířce dat.

Výchozí hodnota `UInteger` je 0.

## <a name="literal-assignments"></a>Přiřazení literálů

Můžete deklarovat a inicializovat `UInteger` proměnnou přiřazením desítkového literálu, šestnáctkového literálu, osmičkového literálu nebo (začínajícího Visual Basic 2017) binárního literálu. Pokud je celočíselný literál mimo rozsah `UInteger` (tj. Pokud je menší <xref:System.UInt32.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.UInt32.MaxValue?displayProperty=nameWithType> , dojde k chybě kompilace.

V následujícím příkladu jsou celá čísla rovna 3 000 000 000, která jsou reprezentována jako Desítková, šestnáctková a binární literála přiřazena `UInteger` hodnotám.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> Použijte předponu `&h` nebo `&H` k označení šestnáctkového literálu, předpony `&b` nebo `&B` označení binárního literálu a předpony `&o` nebo `&O` k označení osmičkového literálu. Desítkové literály nemají žádnou předponu.

Počínaje Visual Basic 2017 můžete také použít znak podtržítka, `_` jako oddělovač číslic pro zlepšení čitelnosti, jak ukazuje následující příklad.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

Počínaje Visual Basic 15,5 můžete také použít znak podtržítka ( `_` ) jako úvodní oddělovač mezi předponou a šestnáctkovou, binární nebo osmičkovou číslicí. Příklad:

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Číselné literály mohou také zahrnovat `UI` `ui` [znak typu](../../programming-guide/language-features/data-types/type-characters.md) nebo, který označuje `UInteger` datový typ, jak ukazuje následující příklad.

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a>Tipy k programování

`UInteger` `Integer` Datové typy a poskytují optimální výkon na 32 procesor, protože menší celočíselné typy ( `UShort` , `Short` , `Byte` a `SByte` ), i když používají méně bitů, si můžete vyčítat, ukládat a načítat.

- **Záporná čísla.** Protože `UInteger` je typ bez znaménka, nemůže představovat záporné číslo. Použijete-li unární operátor mínus ( `-` ) u výrazu, který je vyhodnocen jako typ `UInteger` , Visual Basic výraz převede na `Long` první.

- **Kompatibilita se specifikací CLS.** `UInteger`Datový typ není součástí specifikace CLS ( [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) ), takže kód odpovídající specifikaci CLS nemůže spotřebovat komponentu, která ji používá.

- **Problematika spolupráce.** Pokud procházejíte s komponentami, které nejsou napsané pro .NET Framework, například automatizace nebo objekty COM, pamatujte, že typy, jako například, `uint` mohou mít v jiných prostředích různou šířku dat (16 bitů). Pokud předáváte pro takovou součást 16bitový argument, deklarujte ji jako `UShort` místo `UInteger` ve spravovaném kódu Visual Basic.

- **Rozšiřující.** `UInteger`Datový typ se rozšíří na `Long` ,, `ULong` , `Decimal` `Single` a `Double` . To znamená, že můžete převést `UInteger` na některý z těchto typů bez výskytu <xref:System.OverflowException?displayProperty=nameWithType> chyby.

- **Znaky typu.** Připojení znaků literálového typu `UI` k literálu vynutí tento `UInteger` datový typ. `UInteger`nemá žádný znak typu identifikátoru.

- **Typ rozhraní.** Odpovídající typ v .NET Framework je <xref:System.UInt32?displayProperty=nameWithType> Struktura.

## <a name="see-also"></a>Viz také

- <xref:System.UInt32>
- [Datové typy](index.md)
- [Funkce pro převod typů](../functions/type-conversion-functions.md)
- [Souhrn převodu](../keywords/conversion-summary.md)
- [Postupy: Volání funkce Windows, která přebírá typy bez znaménka](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Účinné používání datových typů](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
