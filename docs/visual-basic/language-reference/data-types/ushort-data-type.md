---
title: "UShort – datový typ (Visual Basic)"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.ushort
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
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 513e8ce4694788d33c5aa14e34b95e88b6d37ff1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ushort-data-type-visual-basic"></a>Ushort – datový typ (Visual Basic)

(Blokování nepodepsaných 16bitové 2bajtový) typ Integer v rozmezí od 0 do 65 535.  
  
## <a name="remarks"></a>Poznámky

 Použití `UShort` datový typ tak, aby obsahovala binární data příliš velké vzhledem k `Byte`.  
  
 Výchozí hodnota `UShort` je 0.  

# <a name="literal-assignments"></a>Literál přiřazení

Můžete deklarace a inicializace `UShort` proměnné jeho přiřazení decimal literál, hexadecimální literál, osmičková literál, nebo (počínaje 2017 Visual Basic) binární literál. Pokud literálu celé číslo je mimo rozsah `UShort` (tj. Pokud je menší než <xref:System.UInt16.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace.

V následujícím příkladu, celá čísla rovno 65,034, která jsou reprezentovány jako decimal, šestnáctkové, a binární literály jsou přiřazeny k `UShort` hodnoty.
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> Použijte předponu `&h` nebo `&H` k označení hexadecimální literál, předponu `&b` nebo `&B` k označení binární literál a předponu `&o` nebo `&O` k označení osmičková literál. Decimal literály mít žádná předpona.

Počínaje 2017 Visual Basic, můžete také použít znak podtržítka `_`, jako oddělovač číslice za účelem zlepšení čitelnosti jako následující příklad ukazuje.

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

Číselné literály může také obsahovat `US` nebo `us` [znak typu](../../programming-guide\language-features\data-types/type-characters.md) k označení `UShort` datového typu, jak ukazuje následující příklad.

```vb
Dim number = &H035826us
```

## <a name="programming-tips"></a>Tipy pro programování
  
-   **Záporná čísla.** Protože `UShort` je typ bez znaménka, nelze ho představují záporné číslo. Pokud používáte Unární minus (`-`) operátor na výraz, který se vyhodnotí na typ `UShort`, Visual Basic Převede výraz, který se `Integer` první.  
  
-   **Souladu se specifikací CLS.** `UShort` Datový typ není součástí [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) CLS (), takže kompatibilní se specifikací CLS kódu nemůže využívat komponenty, která se používá.
  
-   **Rozšíření.** `UShort` Datový typ rozšiřuje na `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, a `Double`. To znamená, že můžete převést `UShort` na některý z těchto typů bez zjištění <xref:System.OverflowException?displayProperty=nameWithType> chyby.  
  
-   **Znaky typu.** Připojování znaky typu literálu `US` k literál vynutí, aby `UShort` datového typu. `UShort`nemá žádné – znak typu identifikátoru.  
  
-   **Typ Framework.** Typ odpovídající v rozhraní .NET Framework je <xref:System.UInt16?displayProperty=nameWithType> struktura.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.UInt16>  
 [Datové typy](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Souhrn konverze](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Postupy: volání funkce systému Windows, která přebírá nepřiřazené typy](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
