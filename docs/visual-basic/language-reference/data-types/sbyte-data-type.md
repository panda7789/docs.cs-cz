---
title: SByte – datový typ (Visual Basic)
ms.date: 04/20/2017
f1_keywords:
- vb.sbyte
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- SByte data type
ms.assetid: 5c38374a-18a1-4cc2-b493-299e3dcaa60f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 94ab72b2ac2678640697e3cfab426e5a7d6d889a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518582"
---
# <a name="sbyte-data-type-visual-basic"></a>SByte – datový typ (Visual Basic)

Blokování podepsané 8bitová celá čísla (1bajtový), které v rozsahu od -128 až 127.  
  
## <a name="remarks"></a>Poznámky

Použití `SByte` datový typ tak, aby obsahovala celočíselných hodnot, které nevyžadují šířku úplná `Integer` nebo dokonce data poloviční šířku `Short`. V některých případech může být modul common language runtime moct pack vaše `SByte` proměnné úzce spolupracují a uložit spotřebu paměti.

Výchozí hodnota `SByte` je 0.

## <a name="literal-assignments"></a>Literál přiřazení
  
Můžete deklarovat a inicializovat `SByte` proměnnou ji přiřadíte desítkový literál, šestnáctkové literál, osmičkové literální, nebo (od verze 2017 jazyka Visual Basic) binární literál.

V následujícím příkladu celých čísel je rovno-102, které jsou reprezentovány jako desítkové, hexadecimální, a binární literály jsou přiřazeny k `SByte` hodnoty. Tento příklad vyžaduje kompilaci s parametrem `/removeintchecks` přepínač kompilátoru.

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]  

> [!NOTE] 
> Použijte předponu `&h` nebo `&H` k označení šestnáctkové literálu předpona `&b` nebo `&B` k označení binárního typu literal a předponu `&o` nebo `&O` k označení osmičkové literální. Desítkové literály mají žádná předpona.

Počínaje rokem 2017 jazyka Visual Basic, můžete použít také znak podtržítka `_`, jako oddělovač číslice za účelem zlepšení čitelnosti jako následující příklad ukazuje.

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]  

Od verze 15.5 jazyka Visual Basic, můžete také použít znak podtržítka (`_`) jako počáteční oddělovač mezi prefix a šestnáctkové, binární nebo osmičkové číslice. Příklad:

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Pokud celočíselný literál je mimo rozsah `SByte` (tj. Pokud je menší než <xref:System.SByte.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.SByte.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace. Pokud má celočíselného literálu bez přípony [celé číslo](integer-data-type.md) je odvozen. Pokud celočíselný literál je mimo rozsah `Integer` typ, [dlouhé](long-data-type.md) je odvozen. To znamená, že v předchozích příkladech číselné literály `0x9A` a `0b10011010` jsou interpretovány jako 32bitová celá čísla se znaménkem s hodnotou 156, což překračuje <xref:System.SByte.MaxValue?displayProperty=nameWithType>. Aby mohl úspěšně kompilovat kód následujícím způsobem, který přiřazuje nedesetinné číslo do `SByte`, můžete provést jeden z následujících akcí:

- Zakázat kontroly rozsah celých čísel s kompilací `/removeintchecks` přepínač kompilátoru.

- Použití [znak](../../programming-guide\language-features\data-types/type-characters.md) explicitně definovat, kterou chcete přiřadit k hodnotě literálu `SByte`. Následující příklad přiřadí negativní literál `Short` hodnota, která se `SByte`. Všimněte si, že pro záporná čísla, musí být nastaven bit nejvyšším vyšší řád slova číselný literál. V případě v našem příkladu to je bit 15 literálu `Short` hodnotu.

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a>Tipy pro programování
  
-   **Dodržování specifikace CLS.** `SByte` Datový typ není součástí [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), takže kód kompatibilní se Specifikací CLS nemůže využívat komponentu, která ji používá.

-   **Rozšíření.** `SByte` Datový typ rozšiřuje na `Short`, `Integer`, `Long`, `Decimal`, `Single`, a `Double`. To znamená, že můžete převést `SByte` ke kterékoli z těchto typů, aniž se objeví <xref:System.OverflowException?displayProperty=nameWithType> chyby.
  
-   **Znaky typu.** `SByte` nemá žádný – znak typu literálu nebo – znak typu identifikátoru.  
  
-   **Typ architektury.** Odpovídajícím typem v rozhraní .NET Framework je <xref:System.SByte?displayProperty=nameWithType> struktury.
  
## <a name="see-also"></a>Viz také:

 <xref:System.SByte?displayProperty=nameWithType>  
 [Datové typy](../../../visual-basic/language-reference/data-types/index.md)  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Datový typ Short](../../../visual-basic/language-reference/data-types/short-data-type.md)  
 [Datový typ Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [Datový typ Long](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
