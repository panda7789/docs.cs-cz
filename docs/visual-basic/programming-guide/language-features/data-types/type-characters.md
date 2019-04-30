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
ms.openlocfilehash: a469a08ebadd77d5abbfa95b270784c9ef534691
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61906747"
---
# <a name="type-characters-visual-basic"></a>Zadejte znaky (Visual Basic)

Kromě zadání datový typ v příkazu deklarace, můžete vynutit datový typ některé programovací prvky s *znak*. Znak typu musí následovat bezprostředně za elementem žádné znaky použité jakéhokoli druhu.

Znak typu není součástí názvu elementu. Element definice se znakem typu může být odkazováno bez znak typu.

## <a name="identifier-type-characters"></a>Identifikátor – znaky typu

Visual Basic poskytuje sadu *identifikátor – znaky typu* , můžete použít v deklaraci zadat datový typ proměnné nebo konstanta. V následující tabulce jsou uvedeny k dispozici identifikátor – znaky typu s příklady využití.
  
|Znak typu identifikátoru|Datový typ|Příklad|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 Neexistuje žádný identifikátor – znaky typu pro `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, nebo `UShort` datové typy, nebo pro všechny složené datové typy, například pole nebo struktury.

V některých případech se můžete připojit `$` znak pro funkci jazyka Visual Basic, například `Left$` místo `Left`, k získání vrácené hodnoty typu `String`.

Ve všech případech se znak typu identifikátoru musí následovat bezprostředně za název identifikátoru.

## <a name="literal-type-characters"></a>Literálové znaky typu

A *literálu* je textovou reprezentaci určité hodnoty datového typu.  

### <a name="default-literal-types"></a>Výchozí typy literálu

Formulář literál jak se zobrazí v kódu obvykle určuje jeho datového typu. V následující tabulce jsou uvedeny tyto výchozí typy.  
  
|Textové formě literál|Výchozí typ.|Příklad|  
|-----------------------------|-----------------------|-------------|  
|Číselné, ne desetinné části|`Integer`|`2147483647`|  
|Číselné, ne zlomkové části, příliš velký pro `Integer`|`Long`|`2147483648`|  
|Číselné, desetinné části|`Double`|`1.2`|  
|Uzavřený do dvojitých uvozovek|`String`|`"A"`|  
|Uzavřený do znaky složených závorek|`Date`|`#5/17/1993 9:32 AM#`|  

### <a name="forced-literal-types"></a>Vynucené typy literálu

Visual Basic poskytuje sadu *– literálové znaky typu*, označuje, který můžete použít k vynucení literál předpokládat, že datový typ jiný než ten její formulář. To provedete přidáním znak na konci literál. V následující tabulce jsou uvedeny k dispozici – literálové znaky typu s příklady využití.
  
|Znak typu literálu|Datový typ|Příklad|  
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

Pro neexistují žádné znaky typu literálu `Boolean`, `Byte`, `Date`, `Object`, `SByte`, nebo `String` datové typy, nebo pro všechny složené datové typy, jako je například pole nebo struktury.

Literály můžou používat také identifikátor – znaky typu (`%`, `&`, `@`, `!`, `#`, `$`), jak můžete proměnné, konstanty a výrazy. Ale literál znaky (`S`, `I`, `L`, `D`, `F`, `R`, `C`) lze použít pouze s literály.

Ve všech případech se znak typu literálu musí bezprostředně následuje po hodnotě literálu.

## <a name="hexadecimal-binary-and-octal-literals"></a>Šestnáctkové binární a osmičkové literály

Kompilátor interpretuje obvykle celočíselného literálu v systému desetinné číslo (se základem 10) čísla. Můžete také definovat celočíselného literálu jako šestnáctkové číslo (základní 16) číslo s `&H` předpony jako binární soubor (základní 2) číslo s `&B` předponu a jako osmičkové (základní 8) čísla s `&O` předponu. Číslic, které následují předpona, která musí odpovídat číslo systému. Následující tabulka ukazuje to.  
  
|Základna čísla|Předpona|Hodnoty platné číslice|Příklad|
|-----------------|------------|------------------------|-------------|
|Šestnáctková (základní 16)|`&H`|0 – 9 a A-F|`&HFFFF`|
|Binární soubor (základní 2)|`&B`|0-1|`&B01111100`|
|Octal (základní 8)|`&O`|0-7|`&O77`|

Spuštění v jazyce Visual Basic 2017, můžete použít znak podtržítka (`_`) jako oddělovač skupin za účelem zlepšení čitelnosti celočíselný literál. V následujícím příkladu `_` znak pro literál binární soubor pro seskupení 8bitové skupiny:

```vb
Dim number As Integer = &B00100010_11000101_11001111_11001101
```

Můžete postupovat podle předponou literální znak typu literálu. Následující příklad ukazuje to.

```vb
Dim counter As Short = &H8000S
Dim flags As UShort = &H8000US
```

V předchozím příkladu `counter` má desetinnou hodnotou-32 768, a `flags` má desetinnou hodnotou +32768.

Od verze 15.5 jazyka Visual Basic, můžete také použít znak podtržítka (`_`) jako počáteční oddělovač mezi prefix a šestnáctkové, binární nebo osmičkové číslice. Příklad:

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../../includes/vb-separator-langversion.md)]

## <a name="see-also"></a>Viz také:

- [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Základní datové typy](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Převody typů v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Datové typy](../../../../visual-basic/language-reference/data-types/index.md)
