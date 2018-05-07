---
title: Znaky typu (Visual Basic)
ms.date: 01/31/2018
helpviewer_keywords:
- '&H prefix for hexadecimal values'
- hexadecimal literals [Visual Basic]
- F literal type character [Visual Basic]
- '& identifier type character'
- type characters [Visual Basic]
- octal literals [Visual Basic]
- literals [Visual Basic], hexadecimal
- '&O prefix for octal values'
- literals [Visual Basic], default types
- defaults, literal types
- C literal type character [Visual Basic]
- type characters [Visual Basic], literal
- $ identifier type character
- L literal type character [Visual Basic]
- UI literal type characters [Visual Basic]
- default literal types [Visual Basic]
- D literal type character [Visual Basic]
- literals [Visual Basic], octal
- S literal type character [Visual Basic]
- '! identifier type character'
- US literal type characters [Visual Basic]
- '% identifier type character'
- data types [Visual Basic], type characters
- characters [Visual Basic], identifier type
- type characters [Visual Basic], identifier
- '# identifier type character'
- identifier type characters [Visual Basic]
- literal type characters [Visual Basic]
- I literal type character [Visual Basic]
- R literal type character [Visual Basic]
- '@ identifier type character'
- UL literal type characters [Visual Basic]
- literal types [Visual Basic], default
ms.assetid: 6353cb9b-6ee4-4af6-a5a8-88ce39f90cc5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9262c57c5773b947f18fd9e8cf9087bb8e02de7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="type-characters-visual-basic"></a>Zadejte znaky (Visual Basic)

Kromě určení datový typ v příkazu deklaraci, můžete vynutit datový typ některé elementům programování s *znak typu*. Znak, který typ musí následovat okamžitě element s žádné použité znaky jakéhokoli druhu.

Typ znak, který není součástí názvu elementu. Element definovaný s – znak typu může být odkaz bez typu znaků.

## <a name="identifier-type-characters"></a>Identifikátor – znaky typu

Visual Basic poskytuje sadu *identifikátor – znaky typu* používané v deklaraci zadat datový typ proměnné nebo konstanta. V následující tabulce jsou uvedeny k dispozici identifikátor – znaky typu s příklady využití.
  
|– Znak typu identifikátoru|Datový typ|Příklad|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 Pro neexistují žádné identifikátor – znaky typu `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, nebo `UShort` datové typy, nebo pro všechny složené datové typy, jako je například pole nebo struktury.

V některých případech se můžete připojit `$` znak pro funkci jazyka Visual Basic, například `Left$` místo `Left`, získat vrácená hodnota typu `String`.

Ve všech případech musí následovat znak typu identifikátoru okamžitě název identifikátoru.

## <a name="literal-type-characters"></a>Literálové znaky typu

A *literálu* je textovou reprezentaci konkrétní hodnotu datového typu.  

### <a name="default-literal-types"></a>Výchozí typy literálu

Formu literál, jak se objevuje v kódu normálně určuje jeho datového typu. V následující tabulce jsou tyto typy výchozí.  
  
|Textové formě literál|Výchozí datový typ|Příklad|  
|-----------------------------|-----------------------|-------------|  
|Číselné, ne zlomkové části|`Integer`|`2147483647`|  
|Číselné, ne zlomkové části, příliš velký pro `Integer`|`Long`|`2147483648`|  
|Číselné, zlomkové části|`Double`|`1.2`|  
|Uzavřena v uvozovkách|`String`|`"A"`|  
|Uzavřené v rámci znaky|`Date`|`#5/17/1993 9:32 AM#`|  

### <a name="forced-literal-types"></a>Typy vynucené literálu

Visual Basic poskytuje sadu *literálové znaky typu*, určuje, který můžete použít k vynucení literál předpokládat, že datový typ jiný než ten jeho formuláře. Provedete to přidáním znak na konec literál. V následující tabulce jsou uvedeny k dispozici literálové znaky typu s příklady využití.
  
|– Znak typu literálu|Datový typ|Příklad|  
|----------------------------|---------------|-------------|  
|`S`|`Short`|`I = 347S`|
|`I`|`Integer`|`J = 347I`|
|`L`|`Long`|`K = 347L`|
|`D`|`Decimal`|`X = 347D`|
|`F`|`Single`|`Y = 347F`|
|`R`|`Double`|`Z = 347R`|
|`US`|`UShort`|`L = 347US`|
|`UI`|`UInteger`|`M = 347UI`|
|`UL`|`ULong`|`N = 347UL`|
|`C`|`Char`|`Q = "."C`|

Pro neexistují žádné znaky typu literálu `Boolean`, `Byte`, `Date`, `Object`, `SByte`, nebo `String` datové typy, nebo pro jakékoli složené datové typy, jako je například pole nebo struktury.

Literály můžete také použít identifikátor – znaky typu (`%`, `&`, `@`, `!`, `#`, `$`), jak můžete proměnné, konstanty a výrazy. Nicméně skutečné zadejte znaky (`S`, `I`, `L`, `D`, `F`, `R`, `C`) lze použít pouze s literály.

Ve všech případech musí následovat znak typu literálu okamžitě literálovou hodnotou.

## <a name="hexadecimal-binary-and-octal-literals"></a>Hexadecimální, binární a osmičkové literály

Kompilátor normálně interpretuje celé literálu jako v systému desetinné číslo (se základem 10) čísla. Můžete také definovat celé literálu jako číslo šestnáctkové (základ 16) s `&H` předponou, jako číslo binárního souboru (se základem 2) s `&B` Předpona a jako osmičkové (základ 8) číslo s `&O` předponu. Musí být vhodný pro systém, počet číslic, které následují předponu. Následující tabulka znázorňuje to.  
  
|Číslo základní|Předpona|Platný dvouciferné hodnoty|Příklad|
|-----------------|------------|------------------------|-------------|
|Šestnáctkové (základ 16)|`&H`|0 – 9 a A-F|`&HFFFF`|
|Binární (se základem 2)|`&B`|0-1|`&B01111100`|
|Octal (základní 8)|`&O`|0-7|`&O77`|

Počínaje 2017 Visual Basic, můžete použít znak podtržítka (`_`) jako oddělovač skupin pro zlepšení čitelnosti celočíselný literál. Následující příklad používá `_` znak, který má skupinu binární literálu do skupin 8bitové:

```vb
Dim number As Integer = &B00100010_11000101_11001111_11001101
```

Můžete postupovat podle předponou literál s – znak typu literálu. Následující příklad ukazuje to.

```vb
Dim counter As Short = &H8000S
Dim flags As UShort = &H8000US
```

V předchozím příkladu `counter` má hodnotu decimal-32 768, a `flags` desetinnou hodnotu +32768.

Od verze Visual Basic 15,5, můžete také použít znak podtržítka (`_`) jako oddělovač úvodní mezi předponu a hexadecimální, binary nebo osmičková číslice. Příklad:

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../../includes/vb-separator-langversion.md)]

## <a name="see-also"></a>Viz také

 [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Základní datové typy](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Převody typů v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Datové typy](../../../../visual-basic/language-reference/data-types/data-type-summary.md)
