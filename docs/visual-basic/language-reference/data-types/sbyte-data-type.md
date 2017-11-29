---
title: "SByte – datový typ (Visual Basic)"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.sbyte
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
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2bcd00665ec5b8651089811a61212bfa302fe95d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="sbyte-data-type-visual-basic"></a>SByte – datový typ (Visual Basic)

Blokování podepsaná celá čísla 8bitové (1bajtů), které pohybovat v rozmezí -128 do 127.  
  
## <a name="remarks"></a>Poznámky

Použití `SByte` datový typ tak, aby obsahovala celé číslo hodnoty, které nevyžadují šířku úplná data `Integer` nebo dokonce šířku poloviční data `Short`. V některých případech může být modul common language runtime moct pack vaší `SByte` proměnné úzce spolupracují a uložte využití paměti.

Výchozí hodnota `SByte` je 0.

## <a name="literal-assignments"></a>Literál přiřazení
  
Můžete deklarace a inicializace `SByte` proměnné jeho přiřazení decimal literál, hexadecimální literál, osmičková literál, nebo (počínaje 2017 Visual Basic) binární literál.

V následujícím příkladu, celá čísla rovno-102, která jsou reprezentovány jako decimal, šestnáctkové, a binární literály jsou přiřazeny k `SByte` hodnoty. Tento příklad vyžaduje, aby kompilujete s `/removeintchecks` přepínače kompilátoru.

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]  

> [!NOTE] 
> Použijte předponu `&h` nebo `&H` k označení hexadecimální literál, předponu `&b` nebo `&B` k označení binární literál a předponu `&o` nebo `&O` k označení osmičková literál. Decimal literály mít žádná předpona.

Počínaje 2017 Visual Basic, můžete také použít znak podtržítka `_`, jako oddělovač číslice za účelem zlepšení čitelnosti jako následující příklad ukazuje.

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]  

Pokud literálu celé číslo je mimo rozsah `SByte` (tj. Pokud je menší než <xref:System.SByte.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.SByte.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace. Když celé literál bez přípony, [celé číslo](integer-data-type.md) je odvodit. Pokud literálu celé číslo je mimo rozsah `Integer` typ, [dlouho](long-data-type.md) je odvodit. To znamená, že v předchozích příkladech číselné literály `0x9A` a `0b10011010` se interpretují jako 32bitová podepsaná celá čísla s hodnotou 156, který přesahuje <xref:System.SByte.MaxValue?displayProperty=nameWithType>. Úspěšně zkompilovat kód jako to, který přiřazuje celé číslo bez desetinných k `SByte`, můžete provést jeden z následujících akcí:

- Kompilování pomocí zakázat kontroly rozsah celých čísel `/removeintchecks` přepínače kompilátoru.

- Použití [znak typu](../../programming-guide\language-features\data-types/type-characters.md) explicitně definujte literálovou hodnotou, kterou chcete přiřadit `SByte`. Následující příklad přiřadí záporné literál `Short` hodnotu `SByte`. Všimněte si, že pro záporná čísla, musíte nastavit vysokou bitem aplikace word horní z číselný literál. V případě našem příkladu to je bit 15 literálové `Short` hodnotu.

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a>Tipy pro programování
  
-   **Souladu se specifikací CLS.** `SByte` Datový typ není součástí [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) CLS (), takže kompatibilní se specifikací CLS kódu nemůže využívat komponenty, která se používá.

-   **Rozšíření.** `SByte` Datový typ rozšiřuje na `Short`, `Integer`, `Long`, `Decimal`, `Single`, a `Double`. To znamená, že můžete převést `SByte` na některý z těchto typů bez zjištění <xref:System.OverflowException?displayProperty=nameWithType> chyby.
  
-   **Znaky typu.** `SByte`nemá žádnou – znak typu literálu nebo – znak typu identifikátoru.  
  
-   **Typ Framework.** Typ odpovídající v rozhraní .NET Framework je <xref:System.SByte?displayProperty=nameWithType> struktura.
  
## <a name="see-also"></a>Viz také

 <xref:System.SByte?displayProperty=nameWithType>  
 [Datové typy](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Souhrn konverze](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Short – datový typ](../../../visual-basic/language-reference/data-types/short-data-type.md)  
 [Integer – datový typ](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [Long – datový typ](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
