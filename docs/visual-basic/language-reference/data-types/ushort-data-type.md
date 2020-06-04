---
title: UShort – datový typ
ms.date: 01/31/2018
f1_keywords:
- vb.ushort
helpviewer_keywords:
- numbers [Visual Basic], whole
- literal type characters [Visual Basic], US
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- UShort data type
- US literal type characters [Visual Basic]
ms.assetid: 138db892-665d-4ba8-9cae-d8d91c4a8f39
ms.openlocfilehash: ee31156e00059699125fd72a7f091afbb21beab0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415476"
---
# <a name="ushort-data-type-visual-basic"></a>UShort – datový typ (Visual Basic)

Obsahuje nepodepsaná 16bitová (2-bajt) celá čísla v rozsahu od 0 do 65 535.  
  
## <a name="remarks"></a>Poznámky

 `UShort`Datový typ použijte k zahrnutí binárních dat, která jsou příliš velká pro `Byte` .  
  
 Výchozí hodnota `UShort` je 0.  

## <a name="literal-assignments"></a>Přiřazení literálů

Můžete deklarovat a inicializovat `UShort` proměnnou přiřazením desítkového literálu, šestnáctkového literálu, osmičkového literálu nebo (začínajícího Visual Basic 2017) binárního literálu. Pokud je celočíselný literál mimo rozsah `UShort` (tj. Pokud je menší <xref:System.UInt16.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.UInt16.MaxValue?displayProperty=nameWithType> , dojde k chybě kompilace.

V následujícím příkladu jsou celá čísla rovna 65 034, která jsou reprezentována jako Desítková, šestnáctková a binární literála přiřazena `UShort` hodnotám.
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> Použijte předponu `&h` nebo `&H` k označení šestnáctkového literálu, předpony `&b` nebo `&B` označení binárního literálu a předpony `&o` nebo `&O` k označení osmičkového literálu. Desítkové literály nemají žádnou předponu.

Počínaje Visual Basic 2017 můžete také použít znak podtržítka, `_` jako oddělovač číslic pro zlepšení čitelnosti, jak ukazuje následující příklad.

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

Počínaje Visual Basic 15,5 můžete také použít znak podtržítka ( `_` ) jako úvodní oddělovač mezi předponou a šestnáctkovou, binární nebo osmičkovou číslicí. Příklad:

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Číselné literály mohou také zahrnovat `US` `us` [znak typu](../../programming-guide/language-features/data-types/type-characters.md) nebo, který označuje `UShort` datový typ, jak ukazuje následující příklad.

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a>Tipy k programování
  
- **Záporná čísla.** Protože `UShort` je typ bez znaménka, nemůže představovat záporné číslo. Použijete-li unární operátor mínus ( `-` ) u výrazu, který je vyhodnocen jako typ `UShort` , Visual Basic výraz převede na `Integer` první.  
  
- **Kompatibilita se specifikací CLS.** `UShort`Datový typ není součástí specifikace CLS ( [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) ), takže kód odpovídající specifikaci CLS nemůže spotřebovat komponentu, která ji používá.
  
- **Rozšiřující.** `UShort`Datový typ se rozšíří na `Integer` ,,,, `UInteger` `Long` `ULong` `Decimal` , `Single` a `Double` . To znamená, že můžete převést `UShort` na některý z těchto typů bez výskytu <xref:System.OverflowException?displayProperty=nameWithType> chyby.  
  
- **Znaky typu.** Připojení znaků literálového typu `US` k literálu vynutí tento `UShort` datový typ. `UShort`nemá žádný znak typu identifikátoru.  
  
- **Typ rozhraní.** Odpovídající typ v .NET Framework je <xref:System.UInt16?displayProperty=nameWithType> Struktura.  
  
## <a name="see-also"></a>Viz také

- <xref:System.UInt16>
- [Datové typy](index.md)
- [Funkce pro převod typů](../functions/type-conversion-functions.md)
- [Souhrn převodu](../keywords/conversion-summary.md)
- [Postupy: Volání funkce Windows, která přebírá typy bez znaménka](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Účinné používání datových typů](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
