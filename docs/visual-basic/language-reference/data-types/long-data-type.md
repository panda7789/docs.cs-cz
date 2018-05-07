---
title: Long – datový typ (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.Long
helpviewer_keywords:
- identifier type characters [Visual Basic], &
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- '& identifier type character'
- integer numbers
- literal type characters [Visual Basic], L
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- L literal type character [Visual Basic]
- integers [Visual Basic], types
- Long keyword [Visual Basic]
- data types [Visual Basic], integral
- data types [Visual Basic], assigning
- Long data type
ms.assetid: b4770c34-1804-4f8c-b512-c10b0893e516
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 687c235be76ef522758658fd1c5fe0cb1dbeb414
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="long-data-type-visual-basic"></a>Long – datový typ (Visual Basic)

Blokování podepsaná celá čísla 64-bit (8 bajtů) v rozmezí od-9,223,372,036,854,775,808 prostřednictvím 9,223,372,036,854,775,807 (9.2 … E + 18).  
  
## <a name="remarks"></a>Poznámky

 Použití `Long` datový typ tak, aby obsahovala celá čísla, která je příliš velký, aby se vešla do `Integer` datového typu.  
  
 Výchozí hodnota `Long` je 0.

## <a name="literal-assignments"></a>Literál přiřazení 

Můžete deklarace a inicializace `Long` proměnné jeho přiřazení decimal literál, hexadecimální literál, osmičková literál, nebo (počínaje 2017 Visual Basic) binární literál. Pokud literálu celé číslo je mimo rozsah `Long` (tj. Pokud je menší než <xref:System.Int64.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Int64.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace.

V následujícím příkladu, celá čísla rovno 4 294 967 296 jsou reprezentovány jako decimal, šestnáctkové, a binární literály jsou přiřazeny k `Long` hodnoty.
  
[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]  

> [!NOTE]
> Použijte předponu `&h` nebo `&H` k označení hexadecimální literál, předponu `&b` nebo `&B` k označení binární literál a předponu `&o` nebo `&O` k označení osmičková literál. Decimal literály mít žádná předpona.

Počínaje 2017 Visual Basic, můžete také použít znak podtržítka `_`, jako oddělovač číslice za účelem zlepšení čitelnosti jako následující příklad ukazuje.

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Od verze Visual Basic 15,5, můžete také použít znak podtržítka (`_`) jako oddělovač úvodní mezi předponu a hexadecimální, binary nebo osmičková číslice. Příklad:

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Číselné literály může také obsahovat `L` [znak typu](../../programming-guide\language-features\data-types/type-characters.md) k označení `Long` datového typu, jak ukazuje následující příklad.

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a>Tipy pro programování

-   **Spolupráce aspekty.** Pokud jsou během propojení s součásti, které nejsou určeny pro rozhraní .NET Framework pro příklad objekty automatizace nebo COM, nezapomeňte, že `Long` má odlišné datové šířku (32bitová verze) v jiných prostředích. 32-bit argument předáte pro tyto součásti, deklarujte ji jako `Integer` místo `Long` v váš nový kód jazyka Visual Basic.  
  
-   **Rozšíření.** `Long` Datový typ rozšiřuje na `Decimal`, `Single`, nebo `Double`. To znamená, že můžete převést `Long` na některý z těchto typů bez zjištění <xref:System.OverflowException?displayProperty=nameWithType> chyby.  
  
-   **Znaky typu.** Připojování znak typu literálu `L` k literál vynutí, aby `Long` datového typu. Připojování znak typu identifikátoru `&` na všechny identifikátor vynutí jeho `Long`.  
  
-   **Typ Framework.** Typ odpovídající v rozhraní .NET Framework je <xref:System.Int64?displayProperty=nameWithType> struktura.  

## <a name="see-also"></a>Viz také

<xref:System.Int64>
[Datové typy](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
[Integer – datový typ](../../../visual-basic/language-reference/data-types/integer-data-type.md)   
[Short – datový typ](../../../visual-basic/language-reference/data-types/short-data-type.md)   
[Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
[Souhrn konverze](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
[Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
