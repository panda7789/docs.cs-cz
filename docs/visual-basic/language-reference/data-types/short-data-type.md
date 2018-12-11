---
title: Short – datový typ (Visual Basic)
ms.date: 01/31/2018
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
ms.openlocfilehash: dce345e049a1b89b85a340b8e9078f39882a45fb
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148501"
---
# <a name="short-data-type-visual-basic"></a>Short – datový typ (Visual Basic)
Blokování podepsané 16bitová celá čísla (2bajtových), které v rozsahu od-32 768 až 32 767.  
  
## <a name="remarks"></a>Poznámky  
 Použití `Short` datový typ tak, aby obsahovala celočíselných hodnot, které nevyžadují šířku úplná `Integer`. V některých případech můžete sbalit modul common language runtime vaše `Short` proměnné úzce spolupracují a uložit spotřebu paměti.  
  
 Výchozí hodnota `Short` je 0.  
  
## <a name="literal-assignments"></a>Literál přiřazení

Můžete deklarovat a inicializovat `Short` proměnnou ji přiřadíte desítkový literál, šestnáctkové literál, osmičkové literální, nebo (od verze 2017 jazyka Visual Basic) binární literál. Pokud celočíselný literál je mimo rozsah `Short` (tj. Pokud je menší než <xref:System.Int16.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Int16.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace.

V následujícím příkladu celých čísel je rovno 1,034, které jsou reprezentovány jako desítkové, hexadecimální, a binární literály jsou implicitně převeden z [celé číslo](integer-data-type.md) k `Short` hodnoty.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> Použijte předponu `&h` nebo `&H` k označení šestnáctkové literálu předpona `&b` nebo `&B` k označení binárního typu literal a předponu `&o` nebo `&O` k označení osmičkové literální. Desítkové literály mají žádná předpona.

Počínaje rokem 2017 jazyka Visual Basic, můžete použít také znak podtržítka `_`, jako oddělovač číslice za účelem zlepšení čitelnosti jako následující příklad ukazuje.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

Od verze 15.5 jazyka Visual Basic, můžete také použít znak podtržítka (`_`) jako počáteční oddělovač mezi prefix a šestnáctkové, binární nebo osmičkové číslice. Příklad:

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Číselné literály může také zahrnovat `S` [znak](../../programming-guide/language-features/data-types/type-characters.md) k označení `Short` datového typu, jak ukazuje následující příklad.

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a>Tipy pro programování

-   **Rozšíření.** `Short` Datový typ rozšiřuje na `Integer`, `Long`, `Decimal`, `Single`, nebo `Double`. To znamená, že můžete převést `Short` na některý z těchto typů, aniž se objeví <xref:System.OverflowException?displayProperty=nameWithType> chyby.  
  
-   **Znaky typu.** Přidávání znak typu literálu `S` k literálu se z něj stane `Short` datového typu. `Short` nemá žádné – znak typu identifikátoru.  
  
-   **Typ architektury.** Odpovídajícím typem v rozhraní .NET Framework je <xref:System.Int16?displayProperty=nameWithType> struktury.  
  
## <a name="see-also"></a>Viz také:

 <xref:System.Int16?displayProperty=nameWithType>  
 [Datové typy](../../../visual-basic/language-reference/data-types/index.md)  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Datový typ Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [Datový typ Long](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
