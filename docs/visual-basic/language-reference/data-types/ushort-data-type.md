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
ms.openlocfilehash: 7cdbd5fb192fd5cc1be6260dcdcdb1f30cf3f865
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400692"
---
# <a name="ushort-data-type-visual-basic"></a>UKrátký datový typ (Visual Basic)

Obsahuje nepodepsaná 16bitová (2bajtová) celá čísla v hodnotě od 0 do 65 535.  
  
## <a name="remarks"></a>Poznámky

 `UShort` Datový typ slouží k tomu, `Byte`aby obsahoval binární data příliš velká pro .  
  
 Výchozí hodnota `UShort` je 0.  

## <a name="literal-assignments"></a>Doslovná přiřazení

Proměnnou `UShort` můžete deklarovat a inicializovat přiřazením desetinného literálu, šestnáctkového literálu, osmičkového literálu nebo (počínaje jazykem Visual Basic 2017) binárníliterál. Pokud celé číslo literál je `UShort` mimo rozsah (to znamená, <xref:System.UInt16.MinValue?displayProperty=nameWithType> pokud <xref:System.UInt16.MaxValue?displayProperty=nameWithType>je menší než nebo větší než , dojde k chybě kompilace.

V následujícím příkladu jsou `UShort` hodnoty přiřazeny celá čísla rovnající se 65 034, která jsou reprezentována jako desetinné, šestnáctkové a binární literály.
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> Předponu nebo `&h` `&H` k označení šestnáctkového `&b` literálu, předpony nebo `&B` k označení binárního literálu `&o` a `&O` předpony nebo k označení osmičkového literálu. Desetinné literály nemají předponu.

Počínaje visual basicem 2017, můžete také `_`použít znak podtržítko , jako oddělovač číslic pro zvýšení čitelnosti, jak ukazuje následující příklad.

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

Počínaje jazykem Visual Basic 15.5 můžete také`_`použít znak podtržítka ( ) jako úvodní oddělovač mezi předponou a šestnáctkovými, binárními nebo osmičkovými číslicemi. Například:

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Číselné literály mohou `US` `us` také obsahovat znak `UShort` nebo [typ](../../programming-guide/language-features/data-types/type-characters.md) označující datový typ, jak ukazuje následující příklad.

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a>Tipy k programování
  
- **Záporná čísla.** Protože `UShort` je nepodepsaný typ, nemůže představovat záporné číslo. Pokud použijete unární`-`minus ( ) operátor pro `UShort`výraz, který je vyhodnocen na typ , Visual Basic převede výraz na `Integer` první.  
  
- **Dodržování předpisů CLS.** Datový `UShort` typ není součástí [specifikace common language](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), takže kód kompatibilní se specifikací CLS nemůže spotřebovat komponentu, která jej používá.
  
- **Rozšíření.** Datový `UShort` typ se `Integer`rozšiřuje `UInteger` `Long`na `ULong` `Decimal`, `Single`, `Double`, , a . To znamená, `UShort` že můžete převést na <xref:System.OverflowException?displayProperty=nameWithType> některý z těchto typů bez výskytu chyby.  
  
- **Zadejte znaky.** Připojení znaků `US` literálu typu k literálu `UShort` vynutí na datový typ. `UShort`nemá žádný znak typu identifikátoru.  
  
- **Typ rámce.** Odpovídající typ v rozhraní .NET <xref:System.UInt16?displayProperty=nameWithType> Framework je struktura.  
  
## <a name="see-also"></a>Viz také

- <xref:System.UInt16>
- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
