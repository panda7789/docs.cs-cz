---
title: Byte – datový typ
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: 97acd1bc2ff29bac6588216b9ee4a4f187078815
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374314"
---
# <a name="byte-data-type-visual-basic"></a>Byte – datový typ (Visual Basic)

Obsahuje nepodepsaná 8bitové (1 bajt) celá čísla, která mají rozsah hodnot od 0 do 255.

## <a name="remarks"></a>Poznámky

`Byte`Datový typ použijte k zahrnutí binárních dat.  
  
Výchozí hodnota `Byte` je 0.

## <a name="literal-assignments"></a>Přiřazení literálů

Můžete deklarovat a inicializovat `Byte` proměnnou přiřazením desítkového literálu, šestnáctkového literálu, osmičkového literálu nebo (začínajícího Visual Basic 2017) binárního literálu. Pokud je celočíselný literál mimo rozsah a `Byte` (tj. Pokud je menší <xref:System.Byte.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Byte.MaxValue?displayProperty=nameWithType> ), dojde k chybě kompilace.

V následujícím příkladu jsou celá čísla rovnající se 201, která jsou reprezentována jako Desítková, šestnáctková a binární literála, implicitně převedena z [celého čísla](integer-data-type.md) na `byte` hodnoty.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> Použijte předponu `&h` nebo `&H` k označení šestnáctkového literálu, předpony `&b` nebo `&B` označení binárního literálu a předpony `&o` nebo `&O` k označení osmičkového literálu. Desítkové literály nemají žádnou předponu.

Počínaje Visual Basic 2017 můžete také použít znak podtržítka, `_` jako oddělovač číslic pro zlepšení čitelnosti, jak ukazuje následující příklad.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

Počínaje Visual Basic 15,5 můžete také použít znak podtržítka ( `_` ) jako úvodní oddělovač mezi předponou a šestnáctkovou, binární nebo osmičkovou číslicí. Příklad:

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a>Tipy k programování

- **Záporná čísla.** Protože `Byte` je typ bez znaménka, nemůže představovat záporné číslo. Použijete-li unární operátor mínus ( `-` ) u výrazu, který je vyhodnocen jako typ `Byte` , Visual Basic výraz převede na `Short` první.
  
- **Převody formátu.** Když Visual Basic čte nebo zapisuje soubory nebo když volá knihovny DLL, metody a vlastnosti, může automaticky převádět mezi formáty dat. Binární data uložená v `Byte` proměnných a polích jsou během těchto převodů formátu zachovaná. `String`Pro binární data byste neměli používat proměnnou, protože její obsah může být během konverze mezi formáty ANSI a Unicode poškozen.

- **Rozšiřující.** `Byte`Datový typ se rozšíří na `Short` ,, `UShort` , `Integer` `UInteger` , `Long` , `ULong` , `Decimal` , `Single` nebo `Double` . To znamená, že můžete převést `Byte` na některý z těchto typů bez výskytu <xref:System.OverflowException?displayProperty=nameWithType> chyby.
  
- **Znaky typu.** `Byte`nemá žádný znak typu literálu nebo znak typu identifikátoru.

- **Typ rozhraní.** Odpovídající typ v .NET Framework je <xref:System.Byte?displayProperty=nameWithType> Struktura.

## <a name="example"></a>Příklad

 V následujícím příkladu `b` je `Byte` Proměnná. Příkazy ukazují rozsah proměnné a aplikaci operátorů bitových posunutí na ni.

 [!code-vb[VbVbalrDataTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#16)]  

## <a name="see-also"></a>Viz také

- <xref:System.Byte?displayProperty=nameWithType>
- [Datové typy](index.md)
- [Funkce pro převod typů](../functions/type-conversion-functions.md)
- [Souhrn převodu](../keywords/conversion-summary.md)
- [Účinné používání datových typů](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
