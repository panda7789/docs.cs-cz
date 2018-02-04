---
title: "Short – datový typ (Visual Basic)"
ms.date: 01/31/2018
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
author: rpetrusha
ms.author: ronpet
f1_keywords:
- vb.Short
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- S literal type character [Visual Basic]
- Short data type
- literal type characters [Visual Basic], S
ms.assetid: 65fcbcf3-a841-400e-885e-301497729a8b
ms.openlocfilehash: 10c9869d4fb84cd013b22bc791bd31fad745f3d3
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2018
---
# <a name="short-data-type-visual-basic"></a>Short – datový typ (Visual Basic)
Blokování podepsané 16bitových celých čísel (2bajtová), které pohybovat v rozmezí-32 768 do 32 767.  
  
## <a name="remarks"></a>Poznámky  
 Použití `Short` datový typ tak, aby obsahovala celé číslo hodnoty, které nevyžadují šířku úplná data `Integer`. V některých případech může modul common language runtime pack vaší `Short` proměnné úzce spolupracují a uložte využití paměti.  
  
 Výchozí hodnota `Short` je 0.  
  
## <a name="literal-assignments"></a>Literál přiřazení

Můžete deklarace a inicializace `Short` proměnné jeho přiřazení decimal literál, hexadecimální literál, osmičková literál, nebo (počínaje 2017 Visual Basic) binární literál. Pokud literálu celé číslo je mimo rozsah `Short` (tj. Pokud je menší než <xref:System.Int16.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Int16.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace.

V následujícím příkladu, celá čísla rovno 1,034, která jsou reprezentovány jako decimal, šestnáctkové, a binární literály jsou implicitně převést z [celé číslo](integer-data-type.md) k `Short` hodnoty.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> Použijte předponu `&h` nebo `&H` k označení hexadecimální literál, předponu `&b` nebo `&B` k označení binární literál a předponu `&o` nebo `&O` k označení osmičková literál. Decimal literály mít žádná předpona.

Počínaje 2017 Visual Basic, můžete také použít znak podtržítka `_`, jako oddělovač číslice za účelem zlepšení čitelnosti jako následující příklad ukazuje.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

Od verze Visual Basic 15,5, můžete také použít znak podtržítka (`_`) jako oddělovač úvodní mezi předponu a hexadecimální, binary nebo osmičková číslice. Příklad:

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Číselné literály může také obsahovat `S` [znak typu](../../programming-guide\language-features\data-types/type-characters.md) k označení `Short` datového typu, jak ukazuje následující příklad.

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a>Tipy pro programování

-   **Rozšíření.** `Short` Datový typ rozšiřuje na `Integer`, `Long`, `Decimal`, `Single`, nebo `Double`. To znamená, že můžete převést `Short` na některý z těchto typů bez zjištění <xref:System.OverflowException?displayProperty=nameWithType> chyby.  
  
-   **Znaky typu.** Připojování znak typu literálu `S` k literál vynutí, aby `Short` datového typu. `Short`nemá žádné – znak typu identifikátoru.  
  
-   **Typ Framework.** Typ odpovídající v rozhraní .NET Framework je <xref:System.Int16?displayProperty=nameWithType> struktura.  
  
## <a name="see-also"></a>Viz také

 <xref:System.Int16?displayProperty=nameWithType>  
 [Datové typy](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Datový typ Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [Datový typ Long](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
