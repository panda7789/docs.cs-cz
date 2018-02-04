---
title: "Byte – datový typ (Visual Basic)"
ms.date: 01/31/2018
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 02234afc0dc51a2c1338cdd16d1f97765f64b45e
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2018
---
# <a name="byte-data-type-visual-basic"></a>Byte – datový typ (Visual Basic)
Ukládání nepodepsané celých čísel 8bitové (1bajtů), které rozsah v hodnotě od 0 do 255.

## <a name="remarks"></a>Poznámky

Použití `Byte` datový typ tak, aby obsahovala binární data.  
  
Výchozí hodnota `Byte` je 0.

## <a name="literal-assignments"></a>Literál přiřazení

Můžete deklarace a inicializace `Byte` proměnné jeho přiřazení decimal literál, hexadecimální literál, osmičková literál, nebo (počínaje 2017 Visual Basic) binární literál. Pokud celočíselný literál je mimo rozsah `Byte` (tj. Pokud je menší než <xref:System.Byte.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Byte.MaxValue?displayProperty=nameWithType>), dojde k chybě kompilace.

V následujícím příkladu, celá čísla rovno 201, která jsou reprezentovány jako decimal, šestnáctkové, a binární literály jsou implicitně převést z [celé číslo](integer-data-type.md) k `byte` hodnoty.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> Použijte předponu `&h` nebo `&H` k označení hexadecimální literál, předponu `&b` nebo `&B` k označení binární literál a předponu `&o` nebo `&O` k označení osmičková literál. Decimal literály mít žádná předpona.

Počínaje 2017 Visual Basic, můžete také použít znak podtržítka `_`, jako oddělovač číslice za účelem zlepšení čitelnosti jako následující příklad ukazuje.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

Od verze Visual Basic 15,5, můžete také použít znak podtržítka (`_`) jako oddělovač úvodní mezi předponu a hexadecimální, binary nebo osmičková číslice. Příklad:

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a>Tipy pro programování

-   **Záporná čísla.** Protože `Byte` je typ bez znaménka, nelze ho představují záporné číslo. Pokud používáte Unární minus (`-`) operátor na výraz, který se vyhodnotí na typ `Byte`, Visual Basic Převede výraz, který se `Short` první.
  
-   **Převody formátu.** Když Visual Basic čte a zapisuje soubory nebo při volání knihovny DLL, metod a vlastností, může automaticky převádět mezi formáty dat. Binární data uložená v `Byte` proměnných a polí je během takový formát převody zachována. Neměli byste používat `String` proměnná pro binární data, protože její obsah může dojít k porušení během převodu mezi formáty ANSI a Unicode.

-   **Rozšíření.** `Byte` Datový typ rozšiřuje na `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, nebo `Double`. To znamená, že můžete převést `Byte` na některý z těchto typů bez zjištění <xref:System.OverflowException?displayProperty=nameWithType> chyby.
  
-   **Znaky typu.** `Byte`nemá žádnou – znak typu literálu nebo – znak typu identifikátoru.

-   **Typ Framework.** Typ odpovídající v rozhraní .NET Framework je <xref:System.Byte?displayProperty=nameWithType> struktura.

## <a name="example"></a>Příklad

 V následujícím příkladu `b` je `Byte` proměnné. Příkazy ukazují rozsahu proměnné a do něj aplikaci bitové posunutí – operátory.

[!code-vb[VbVbalrDataTypes#16](../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/byte-data-type_1.vb)]  

## <a name="see-also"></a>Viz také

 <xref:System.Byte?displayProperty=nameWithType>  
 [Datové typy](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
