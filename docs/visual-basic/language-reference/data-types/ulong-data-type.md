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
ms.openlocfilehash: 13dec9f298655a4bfe6672e2dbba7c7262379cc4
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50202878"
---
# <a name="ulong-data-type-visual-basic"></a>Ulong – datový typ (Visual Basic)

Obsahuje bez znaménka 64bitová (8 bajtů) celá čísla v rozmezí od 0 do 18,446,744,073,709,551,615 (více než 1.84 časy 10 ^ 19).  
  
## <a name="remarks"></a>Poznámky

Použití `ULong` datový typ obsahující binární data jsou příliš velká pro `UInteger`, nebo unsigned nejvyšší možné celočíselné hodnoty.  
  
Výchozí hodnota `ULong` je 0.

## <a name="literal-assignments"></a>Literál přiřazení

Můžete deklarovat a inicializovat `ULong` proměnnou ji přiřadíte desítkový literál, šestnáctkové literál, osmičkové literální, nebo (od verze 2017 jazyka Visual Basic) binární literál. Pokud celočíselný literál je mimo rozsah `ULong` (tj. Pokud je menší než <xref:System.UInt64.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace.

V následujícím příkladu celých čísel je rovno 7,934,076,125, které jsou reprezentovány jako desítkové, hexadecimální, a binární literály jsou přiřazeny k `ULong` hodnoty.
  
[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE] 
> Použijte předponu `&h` nebo `&H` k označení šestnáctkové literálu předpona `&b` nebo `&B` k označení binárního typu literal a předponu `&o` nebo `&O` k označení osmičkové literální. Desítkové literály mají žádná předpona.

Počínaje rokem 2017 jazyka Visual Basic, můžete použít také znak podtržítka `_`, jako oddělovač číslice za účelem zlepšení čitelnosti jako následující příklad ukazuje.

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Od verze 15.5 jazyka Visual Basic, můžete také použít znak podtržítka (`_`) jako počáteční oddělovač mezi prefix a šestnáctkové, binární nebo osmičkové číslice. Příklad:

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Číselné literály může také zahrnovat `UL` nebo `ul` [znak](../../programming-guide\language-features\data-types/type-characters.md) k označení `ULong` datového typu, jak ukazuje následující příklad.

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a>Tipy pro programování
  
-   **Záporná čísla.** Protože `ULong` typ bez znaménka, je ho nemůže představovat záporné číslo. Pokud používáte Unární minus (`-`) operátor na výraz, který se vyhodnotí na typ `ULong`, Visual Basic Převede výraz, který má `Decimal` první.  
  
-   **Dodržování specifikace CLS.** `ULong` Datový typ není součástí [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), takže kód kompatibilní se Specifikací CLS nemůže využívat komponentu, která ji používá.  
  
-   **Spolupráce aspekty.** Při vzájemném propojování součástí, které nejsou napsané pro rozhraní .NET Framework, například objekty automatizace nebo COM, mějte na paměti, že typy, jako `ulong` může mít v jiných prostředích odlišnou datovou šířku (32bitová verze). Pokud takové součásti předáváte 32-bit argument, deklarujte ho jako `UInteger` místo `ULong` v spravovaného kódu jazyka Visual Basic.  
  
     Kromě toho automatizace nepodporuje 64bitová celá čísla na Windows 95, Windows 98, Windows ME nebo Windows 2000. V jazyce Visual Basic nelze předat `ULong` argument pro komponentu služby Automation na těchto platformách.  
  
-   **Rozšíření.** `ULong` Datový typ rozšiřuje na `Decimal`, `Single`, a `Double`. To znamená, že můžete převést `ULong` ke kterékoli z těchto typů, aniž se objeví <xref:System.OverflowException?displayProperty=nameWithType> chyby.  
  
-   **Znaky typu.** Přidávání znaky literálového typu `UL` k literálu se z něj stane `ULong` datového typu. `ULong` nemá žádné – znak typu identifikátoru.
  
-   **Typ architektury.** Odpovídajícím typem v rozhraní .NET Framework je <xref:System.UInt64?displayProperty=nameWithType> struktury.  
  
## <a name="see-also"></a>Viz také:

 <xref:System.UInt64>  
 [Datové typy](../../../visual-basic/language-reference/data-types/index.md)  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
