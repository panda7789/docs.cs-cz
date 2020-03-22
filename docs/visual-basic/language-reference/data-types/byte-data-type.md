---
title: Byte – datový typ
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: 347d7e7d0f09e089886bc81bd0be659deaca9b46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400741"
---
# <a name="byte-data-type-visual-basic"></a>Datový typ bajtů (Visual Basic)

Obsahuje nepodepsaná 8bitová (1bajtová) celá čísla, která se pohybují v hodnotě od 0 do 255.

## <a name="remarks"></a>Poznámky

Pomocí `Byte` datového typu můžete obsahovat binární data.  
  
Výchozí hodnota `Byte` je 0.

## <a name="literal-assignments"></a>Doslovná přiřazení

Proměnnou `Byte` můžete deklarovat a inicializovat přiřazením desetinného literálu, šestnáctkového literálu, osmičkového literálu nebo (počínaje jazykem Visual Basic 2017) binárníliterál. Pokud integrální literál `Byte` je mimo rozsah (to <xref:System.Byte.MinValue?displayProperty=nameWithType> znamená, <xref:System.Byte.MaxValue?displayProperty=nameWithType>pokud je menší nebo větší než ) dojde k chybě kompilace.

V následujícím příkladu jsou celá čísla rovna 201, která jsou reprezentována jako desetinné, šestnáctkové a binární literály, implicitně převedeny z [Integer](integer-data-type.md) na `byte` hodnoty.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> Předponu nebo `&h` `&H` k označení šestnáctkového `&b` literálu, předpony nebo `&B` k označení binárního literálu `&o` a `&O` předpony nebo k označení osmičkového literálu. Desetinné literály nemají předponu.

Počínaje visual basicem 2017, můžete také `_`použít znak podtržítko , jako oddělovač číslic pro zvýšení čitelnosti, jak ukazuje následující příklad.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

Počínaje jazykem Visual Basic 15.5 můžete také`_`použít znak podtržítka ( ) jako úvodní oddělovač mezi předponou a šestnáctkovými, binárními nebo osmičkovými číslicemi. Například:

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a>Tipy k programování

- **Záporná čísla.** Protože `Byte` je nepodepsaný typ, nemůže představovat záporné číslo. Pokud použijete unární`-`minus ( ) operátor pro `Byte`výraz, který je vyhodnocen na typ , Visual Basic převede výraz na `Short` první.
  
- **Převody formátu.** Při čtení nebo zápisu souborů v jazyce Visual Basic nebo při volání knihoven DLL, metod a vlastností může automaticky převést mezi formáty dat. Binární data `Byte` uložená v proměnných a polích jsou zachována během těchto převodů formátu. Pro binární data `String` byste neměli používat proměnnou, protože její obsah může být poškozen během převodu mezi formáty ANSI a Unicode.

- **Rozšíření.** Datový `Byte` typ se `Short`rozšiřuje `UShort` `Integer`na `UInteger` `Long`, `ULong` `Decimal`, `Single`, `Double`, , , , , , nebo . To znamená, `Byte` že můžete převést na <xref:System.OverflowException?displayProperty=nameWithType> některý z těchto typů bez výskytu chyby.
  
- **Zadejte znaky.** `Byte`nemá žádný znak literálu typu nebo znak typu identifikátoru.

- **Typ rámce.** Odpovídající typ v rozhraní .NET <xref:System.Byte?displayProperty=nameWithType> Framework je struktura.

## <a name="example"></a>Příklad

 V následujícím příkladu `b` `Byte` je proměnná. Příkazy ukazují rozsah proměnné a použití operátorů bitového posunu na něj.

 [!code-vb[VbVbalrDataTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#16)]  

## <a name="see-also"></a>Viz také

- <xref:System.Byte?displayProperty=nameWithType>
- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
