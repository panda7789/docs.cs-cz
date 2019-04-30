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
ms.openlocfilehash: ca0f95342783d22559761294ccea6056cd3e4fa7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61918447"
---
# <a name="long-data-type-visual-basic"></a>Long – datový typ (Visual Basic)

Blokování podepsané 64bitová celá čísla (8 bajtů) v rozmezí od-9,223,372,036,854,775,808 prostřednictvím 9,223,372,036,854,775,807 (9.2... E + 18).  
  
## <a name="remarks"></a>Poznámky

 Použití `Long` datový typ tak, aby obsahovala celých čísel, které jsou příliš velká `Integer` datového typu.  
  
 Výchozí hodnota `Long` je 0.

## <a name="literal-assignments"></a>Literál přiřazení 

Můžete deklarovat a inicializovat `Long` proměnnou ji přiřadíte desítkový literál, šestnáctkové literál, osmičkové literální, nebo (od verze 2017 jazyka Visual Basic) binární literál. Pokud celočíselný literál je mimo rozsah `Long` (tj. Pokud je menší než <xref:System.Int64.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Int64.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace.

V následujícím příkladu celých čísel rovnat do 4 294 967 296 jsou reprezentovány jako desítkové, hexadecimální, a binární literály jsou přiřazeny k `Long` hodnoty.
  
[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]  

> [!NOTE]
> Použijte předponu `&h` nebo `&H` k označení šestnáctkové literálu předpona `&b` nebo `&B` k označení binárního typu literal a předponu `&o` nebo `&O` k označení osmičkové literální. Desítkové literály mají žádná předpona.

Počínaje rokem 2017 jazyka Visual Basic, můžete použít také znak podtržítka `_`, jako oddělovač číslice za účelem zlepšení čitelnosti jako následující příklad ukazuje.

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Od verze 15.5 jazyka Visual Basic, můžete také použít znak podtržítka (`_`) jako počáteční oddělovač mezi prefix a šestnáctkové, binární nebo osmičkové číslice. Příklad:

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Číselné literály může také zahrnovat `L` [znak](../../programming-guide/language-features/data-types/type-characters.md) k označení `Long` datového typu, jak ukazuje následující příklad.

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a>Tipy pro programování

- **Spolupráce aspekty.** Při vzájemném propojování součástí, které nejsou napsané pro rozhraní .NET Framework, například objekty automatizace nebo COM, nezapomeňte, že `Long` má v jiných prostředích odlišnou datovou šířku (32bitová verze). Pokud takové součásti předáváte 32-bit argument, deklarujte ho jako `Integer` místo `Long` v váš nový kód jazyka Visual Basic.  
  
- **Rozšíření.** `Long` Datový typ rozšiřuje na `Decimal`, `Single`, nebo `Double`. To znamená, že můžete převést `Long` na některý z těchto typů, aniž se objeví <xref:System.OverflowException?displayProperty=nameWithType> chyby.  
  
- **Znaky typu.** Přidávání znak typu literálu `L` k literálu se z něj stane `Long` datového typu. Přidávání znak typu identifikátoru `&` k libovolnému identifikátoru se z něj stane `Long`.  
  
- **Typ architektury.** Odpovídajícím typem v rozhraní .NET Framework je <xref:System.Int64?displayProperty=nameWithType> struktury.  

## <a name="see-also"></a>Viz také:

- <xref:System.Int64>
- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Datový typ Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Datový typ Short](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
