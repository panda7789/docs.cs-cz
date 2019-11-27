---
title: Znaky typu
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
ms.openlocfilehash: 628461c8136946dd902c0a52048eee7c516c52cd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352927"
---
# <a name="type-characters-visual-basic"></a>Znaky typu (Visual Basic)

Kromě určení datového typu v příkazu deklarace můžete vynutit datový typ některých programovacích prvků se *znakem typu*. Znak typu musí hned následovat za elementem bez jakýchkoli znaků.

Znak typu není součástí názvu elementu. Element definovaný s znakem typu může být odkazován bez znaku typu.

## <a name="identifier-type-characters"></a>Znaky typu identifikátoru

Visual Basic poskytuje sadu *znaků typu identifikátoru* , které lze použít v deklaraci k určení datového typu proměnné nebo konstanty. Následující tabulka uvádí dostupné znaky typu identifikátoru s příklady použití.
  
|Znak typu identifikátoru|Typ dat|Příklad|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 Neexistují žádné znaky typu identifikátoru pro `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`nebo `UShort` datových typů nebo pro všechny složené datové typy, jako jsou pole nebo struktury.

V některých případech můžete `$` znak připojit k funkci Visual Basic, například `Left$` místo `Left`, a získat tak vrácenou hodnotu typu `String`.

Ve všech případech znak typu identifikátoru musí hned následovat za názvem identifikátoru.

## <a name="literal-type-characters"></a>Literálové znaky typu

*Literál* je textová reprezentace konkrétní hodnoty datového typu.  

### <a name="default-literal-types"></a>Výchozí typy literálů

Tvar literálu, který se zobrazí ve vašem kódu, obvykle určuje jeho datový typ. Následující tabulka ukazuje tyto výchozí typy.  
  
|Textový tvar literálu|Výchozí datový typ|Příklad|  
|-----------------------------|-----------------------|-------------|  
|Číselná, bez zlomkové části|`Integer`|`2147483647`|  
|Číselná, bez zlomkové součásti, je pro `Integer` moc velká.|`Long`|`2147483648`|  
|Číselná, Zlomková část|`Double`|`1.2`|  
|Uzavřeno do dvojitých uvozovek|`String`|`"A"`|  
|Uzavřeno v symbolech čísla|`Date`|`#5/17/1993 9:32 AM#`|  

### <a name="forced-literal-types"></a>Typy vynucených literálů

Visual Basic poskytuje sadu *literálních znaků*, které lze použít k vynucení literálu, který předpokládá, že typ dat je jiný než ten, který formulář označuje. Provedete to tak, že na konec literálu připojíte znak. V následující tabulce jsou uvedeny dostupné znaky literálového typu s příklady použití.
  
|Literál – znak typu|Typ dat|Příklad|  
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

Pro `Boolean`, `Byte`, `Date`, `Object`, `SByte`nebo pro datové typy, jako jsou například pole nebo struktury, neexistuje žádný typ literálních znaků.`String`

Literály mohou také používat znaky typu identifikátoru (`%`, `&`, `@`, `!`, `#`, `$`), jako jsou proměnné, konstanty a výrazy. Literální znaky typu (`S`, `I`, `L`, `D`, `F`, `R`, `C`) však lze použít pouze s literály.

Ve všech případech znak literálního typu musí bezprostředně následovat po hodnotě literálu.

## <a name="hexadecimal-binary-and-octal-literals"></a>Šestnáctkové, binární a osmičkové literály

Kompilátor obvykle interpretuje celočíselný literál, který je v desítkovém systému desítkových čísel (desítkový 10). Můžete také definovat celočíselný literál jako hexadecimální (základní 16) číslo s předponou `&H` jako binární (základní 2) číslo s předponou `&B` a jako osmičkové (desítkové 8) číslo s předponou `&O`. Číslice, které následují předponu, musí být vhodné pro číselný systém. To je znázorněno v následující tabulce.  
  
|Základ čísla|směr|Platné číselné hodnoty|Příklad|
|-----------------|------------|------------------------|-------------|
|Šestnáctkový (základní 16)|`&H`|0-9 a a-F|`&HFFFF`|
|Binární (základní 2)|`&B`|0-1|`&B01111100`|
|Osmičková (základní 8)|`&O`|0-7|`&O77`|

Počínaje Visual Basic 2017 lze použít znak podtržítka (`_`) jako oddělovač skupin pro zlepšení čitelnosti integrálního literálu. V následujícím příkladu se používá znak `_` k seskupení binárního literálu do 8 bitových skupin:

```vb
Dim number As Integer = &B00100010_11000101_11001111_11001101
```

Můžete postupovat podle předem fixního literálu s literálovým znakem typu. Následující příklad ukazuje toto.

```vb
Dim counter As Short = &H8000S
Dim flags As UShort = &H8000US
```

V předchozím příkladu má `counter` desítkovou hodnotu-32768 a `flags` má desítkovou hodnotu + 32768.

Počínaje Visual Basic 15,5 můžete také použít znak podtržítka (`_`) jako úvodní oddělovač mezi předponou a šestnáctkovou, binární nebo osmičkovou číslicí. Příklad:

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../../includes/vb-separator-langversion.md)]

## <a name="see-also"></a>Viz také:

- [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Základní datové typy](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Převody typu v Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Datové typy](../../../../visual-basic/language-reference/data-types/index.md)
