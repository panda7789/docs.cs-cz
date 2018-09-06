---
title: Uinteger – datový typ (Visual Basic)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: df89c099042de8acef687a5fd11fc0dbf7de86a7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43732998"
---
# <a name="uinteger-data-type"></a>UInteger – datový typ

Obsahuje 32bitová (4bajtová) celá čísla bez znaménka v rozmezí od 0 do 4 294 967 295.  
  
## <a name="remarks"></a>Poznámky

 `UInteger` Datový typ poskytuje největší hodnoty bez znaménka na nejúčinnější šířku data.  
  
 Výchozí hodnota `UInteger` je 0.  
  
## <a name="literal-assignments"></a>Literál přiřazení

Můžete deklarovat a inicializovat `UInteger` proměnnou ji přiřadíte desítkový literál, šestnáctkové literál, osmičkové literální, nebo (od verze 2017 jazyka Visual Basic) binární literál. Pokud celočíselný literál je mimo rozsah `UInteger` (tj. Pokud je menší než <xref:System.UInt32.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace.

V následujícím příkladu celých čísel je rovno 3,000,000,000, které jsou reprezentovány jako desítkové, hexadecimální, a binární literály jsou přiřazeny k `UInteger` hodnoty.
  
[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]  

> [!NOTE] 
> Použijte předponu `&h` nebo `&H` k označení šestnáctkové literálu předpona `&b` nebo `&B` k označení binárního typu literal a předponu `&o` nebo `&O` k označení osmičkové literální. Desítkové literály mají žádná předpona.

Počínaje rokem 2017 jazyka Visual Basic, můžete použít také znak podtržítka `_`, jako oddělovač číslice za účelem zlepšení čitelnosti jako následující příklad ukazuje.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]  

Od verze 15.5 jazyka Visual Basic, můžete také použít znak podtržítka (`_`) jako počáteční oddělovač mezi prefix a šestnáctkové, binární nebo osmičkové číslice. Příklad:

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Číselné literály může také zahrnovat `UI` nebo `ui` [znak](../../programming-guide\language-features\data-types/type-characters.md) k označení `UInteger` datového typu, jak ukazuje následující příklad.

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a>Tipy pro programování

 `UInteger` a `Integer` datových typů poskytuje optimální výkon na 32bitových procesorech, protože menší typy celých čísel (`UShort`, `Short`, `Byte`, a `SByte`), i když používají menší počet bitů, trvat déle načíst, uložit a načíst.  
  
-   **Záporná čísla.** Protože `UInteger` typ bez znaménka, je ho nemůže představovat záporné číslo. Pokud používáte Unární minus (`-`) operátor na výraz, který se vyhodnotí na typ `UInteger`, Visual Basic Převede výraz, který má `Long` první.  
  
-   **Dodržování specifikace CLS.** `UInteger` Datový typ není součástí [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), takže kód kompatibilní se Specifikací CLS nemůže využívat komponentu, která ji používá.
  
-   **Spolupráce aspekty.** Při vzájemném propojování součástí, které nejsou napsané pro rozhraní .NET Framework, například objekty automatizace nebo COM, mějte na paměti, že typy, jako `uint` může mít v jiných prostředích odlišnou datovou šířku (16 bitů). Pokud takové součásti předáváte 16bitový argument, deklarujte ho jako `UShort` místo `UInteger` v spravovaného kódu jazyka Visual Basic.  
  
-   **Rozšíření.** `UInteger` Datový typ rozšiřuje na `Long`, `ULong`, `Decimal`, `Single`, a `Double`. To znamená, že můžete převést `UInteger` ke kterékoli z těchto typů, aniž se objeví <xref:System.OverflowException?displayProperty=nameWithType> chyby.  
  
-   **Znaky typu.** Přidávání znaky literálového typu `UI` k literálu se z něj stane `UInteger` datového typu. `UInteger` nemá žádné – znak typu identifikátoru.  
  
-   **Typ architektury.** Odpovídajícím typem v rozhraní .NET Framework je <xref:System.UInt32?displayProperty=nameWithType> struktury.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.UInt32>  
 [Datové typy](../../../visual-basic/language-reference/data-types/index.md)  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
