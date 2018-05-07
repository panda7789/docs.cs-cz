---
title: ULong – datový typ (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.ulong
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- literal type characters [Visual Basic], UL
- ULong data type
- UL literal type characters [Visual Basic]
ms.assetid: 017e0702-774e-44ae-bedc-786b424ca84e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b0137f0f33abfdb3f03758323edeaa63ac60117
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ulong-data-type-visual-basic"></a>Ulong – datový typ (Visual Basic)

Ukládání nepodepsané celých čísel 64-bit (8 bajtů), v rozmezí od 0 prostřednictvím 18,446,744,073,709,551,615 (více než 1.84 výskyty 10 ^ 19).  
  
## <a name="remarks"></a>Poznámky

Použití `ULong` datový typ tak, aby obsahovala binární data příliš velké vzhledem k `UInteger`, nebo největší možné nepodepsané celočíselné hodnoty.  
  
Výchozí hodnota `ULong` je 0.

## <a name="literal-assignments"></a>Literál přiřazení

Můžete deklarace a inicializace `ULong` proměnné jeho přiřazení decimal literál, hexadecimální literál, osmičková literál, nebo (počínaje 2017 Visual Basic) binární literál. Pokud literálu celé číslo je mimo rozsah `ULong` (tj. Pokud je menší než <xref:System.UInt64.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace.

V následujícím příkladu, celá čísla rovno 7,934,076,125, která jsou reprezentovány jako decimal, šestnáctkové, a binární literály jsou přiřazeny k `ULong` hodnoty.
  
[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE] 
> Použijte předponu `&h` nebo `&H` k označení hexadecimální literál, předponu `&b` nebo `&B` k označení binární literál a předponu `&o` nebo `&O` k označení osmičková literál. Decimal literály mít žádná předpona.

Počínaje 2017 Visual Basic, můžete také použít znak podtržítka `_`, jako oddělovač číslice za účelem zlepšení čitelnosti jako následující příklad ukazuje.

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Od verze Visual Basic 15,5, můžete také použít znak podtržítka (`_`) jako oddělovač úvodní mezi předponu a hexadecimální, binary nebo osmičková číslice. Příklad:

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Číselné literály může také obsahovat `UL` nebo `ul` [znak typu](../../programming-guide\language-features\data-types/type-characters.md) k označení `ULong` datového typu, jak ukazuje následující příklad.

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a>Tipy pro programování
  
-   **Záporná čísla.** Protože `ULong` je typ bez znaménka, nelze ho představují záporné číslo. Pokud používáte Unární minus (`-`) operátor na výraz, který se vyhodnotí na typ `ULong`, Visual Basic Převede výraz, který se `Decimal` první.  
  
-   **Souladu se specifikací CLS.** `ULong` Datový typ není součástí [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) CLS (), takže kompatibilní se specifikací CLS kódu nemůže využívat komponenty, která se používá.  
  
-   **Spolupráce aspekty.** Pokud jsou během propojení s součásti, které nejsou určeny pro rozhraní .NET Framework pro příklad objekty automatizace nebo COM, mějte na paměti, které typy, jako `ulong` může mít různé datové šířka (32bitová verze) v jiných prostředích. 32-bit argument předáte pro tyto součásti, deklarujte ji jako `UInteger` místo `ULong` v spravovaného kódu jazyka Visual Basic.  
  
     Kromě toho automatizace nepodporuje 64bitových celých čísel na systém Windows 95, Windows 98, Windows ME nebo Windows 2000. Nelze předat jazyka Visual Basic `ULong` argument pro komponentu automatizace na těchto platformách.  
  
-   **Rozšíření.** `ULong` Datový typ rozšiřuje na `Decimal`, `Single`, a `Double`. To znamená, že můžete převést `ULong` na některý z těchto typů bez zjištění <xref:System.OverflowException?displayProperty=nameWithType> chyby.  
  
-   **Znaky typu.** Připojování znaky typu literálu `UL` k literál vynutí, aby `ULong` datového typu. `ULong` nemá žádné – znak typu identifikátoru.
  
-   **Typ Framework.** Typ odpovídající v rozhraní .NET Framework je <xref:System.UInt64?displayProperty=nameWithType> struktura.  
  
## <a name="see-also"></a>Viz také

 <xref:System.UInt64>  
 [Datové typy](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
