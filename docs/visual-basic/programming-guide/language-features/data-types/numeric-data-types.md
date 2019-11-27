---
title: Numerické datové typy
ms.date: 07/20/2015
helpviewer_keywords:
- integral types [Visual Basic], Visual Basic
- Short data type [Visual Basic], numeric data types
- Double data type [Visual Basic], numeric data types
- Long data type [Visual Basic], Visual Basic numeric data types
- numbers [Visual Basic], whole
- fractions
- numbers
- whole numbers
- integer numbers
- numbers [Visual Basic], integer
- fractional data types [Visual Basic]
- mantissas, of fractional numbers
- mantissas
- data types [Visual Basic], numeric
- Integer data type [Visual Basic], numeric data types
- exponent, of fractional numbers
- integers [Visual Basic]
- numeric data types [Visual Basic], Visual Basic
- Single data type [Visual Basic], numeric types
- Decimal data type [Visual Basic], numeric data types
ms.assetid: a27bd4d0-7e14-43eb-9cc4-b42eaab323c9
ms.openlocfilehash: dc8b630eebc48e5733344a00664b453360769c0b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346314"
---
# <a name="numeric-data-types-visual-basic"></a>Numerické datové typy (Visual Basic)
Visual Basic poskytuje několik *číselných datových typů* pro zpracování čísel v různých vyjádřeních reprezentace. *Integrální* typy reprezentují pouze celá čísla (kladné, záporné a nula) a *neintegrální* typy reprezentují čísla s celými čísly i zlomky částí.  
  
 Tabulka znázorňující souběžné porovnání Visual Basic datových typů najdete v tématu [datové typy](../../../../visual-basic/language-reference/data-types/index.md).  
  
## <a name="integral-numeric-types"></a>Celočíselné číselné typy  
 *Integrální datové typy* jsou ty, které představují pouze čísla bez zlomkových částí.  
  
 Počet *podepsaných* integrálních datových typů je [SByte datový typ](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md) (8bitové), [krátký datový typ](../../../../visual-basic/language-reference/data-types/short-data-type.md) (16bitový), [celočíselný datový typ](../../../../visual-basic/language-reference/data-types/integer-data-type.md) (32 bitů) a [dlouhý datový typ](../../../../visual-basic/language-reference/data-types/long-data-type.md) (64-bit). Pokud proměnná vždy ukládá celá čísla spíše než zlomková čísla, deklarujte ji jako jeden z těchto typů.  
  
 Celočíselné typy *bez znaménka* jsou [bajtový datový typ](../../../../visual-basic/language-reference/data-types/byte-data-type.md) (8bitové), [UShort datový typ](../../../../visual-basic/language-reference/data-types/ushort-data-type.md) (16bitový), [UInteger – datový typ](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md) (32-bit) a [ulong datový typ](../../../../visual-basic/language-reference/data-types/ulong-data-type.md) (64-bit). Pokud proměnná obsahuje binární data nebo data neznámé povahy, deklarujete je jako jeden z těchto typů.  
  
### <a name="performance"></a>Výkon  
 Aritmetické operace jsou rychlejší s integrálními typy než s jinými datovými typy. Jsou nejrychlejší díky `Integer` a `UInteger` typy v Visual Basic.  
  
### <a name="large-integers"></a>Velká celá čísla  
 Pokud potřebujete držet celé číslo větší, než `Integer` datový typ, můžete místo toho použít datový typ `Long`. proměnné `Long` můžou uchovávat čísla od-9223372036854775808 do 9 223 372 036 854 775 807. Operace s `Long` jsou mírně pomalejší než u `Integer`.  
  
 Pokud potřebujete ještě větší hodnoty, můžete použít [datový typ Decimal](../../../../visual-basic/language-reference/data-types/decimal-data-type.md). Pokud nepoužíváte žádná desetinná místa, můžete čísla z-79,228,162,514,264,337,593,543,950,335 až 79,228,162,514,264,337,593,543,950,335 ve `Decimal` proměnné uchovávat. Operace s `Decimal`mi čísly jsou ale výrazně pomalejší než u jakéhokoli jiného číselného datového typu.  
  
### <a name="small-integers"></a>Malá celá čísla  
 Pokud nepotřebujete plný rozsah datového typu `Integer`, můžete použít datový typ `Short`, který může obsahovat celá čísla od-32 768 do 32 767. Pro nejmenší rozsah celého čísla datový typ `SByte` obsahuje celá čísla od-128 do 127. Pokud máte velmi velký počet proměnných, které obsahují malá celá čísla, může modul CLR (Common Language Runtime) někdy ukládat `Short` a `SByte` proměnné efektivněji a ušetřit spotřebu paměti. Operace s `Short` a `SByte` ale jsou trochu pomalejší než u `Integer`.  
  
### <a name="unsigned-integers"></a>Celá čísla bez znaménka  
 Pokud víte, že proměnná nikdy nepotřebuje držet záporné číslo, můžete použít *typy bez znaménka*`Byte`, `UShort`, `UInteger`a `ULong`. Každý z těchto datových typů může uchovávat kladné celé číslo dvakrát tak velké jako odpovídající typ se znaménkem (`SByte`, `Short`, `Integer`a `Long`). V souvislosti s výkonem je každý typ bez znaménka přesně stejně účinný jako odpovídající typ se znaménkem. Konkrétně `UInteger` sdílené složky s `Integer` rozlišením nejúčinnějších ze všech základních datových typů.  
  
## <a name="nonintegral-numeric-types"></a>Neceločíselné číselné typy  
 *Neintegrální datové typy* jsou ty, které představují čísla s celočíselnou i zlomkovou částí.  
  
 Neceločíselné číselné datové typy jsou `Decimal` (128-bit pevná bod), [jeden datový typ](../../../../visual-basic/language-reference/data-types/single-data-type.md) (32-bit floated Point) a [Double data Type](../../../../visual-basic/language-reference/data-types/double-data-type.md) (64-bit floated Point). Jsou to všechny typy se znaménkem. Pokud proměnná může obsahovat zlomek, deklarujte ji jako jeden z těchto typů.  
  
 `Decimal` není datový typ s plovoucí desetinnou čárkou. čísla `Decimal` mají binární celočíselnou hodnotu a faktor horizontálního měřítka, který určuje, jaká část hodnoty je desítkový zlomek.  
  
 Pro peněžní hodnoty můžete použít proměnné `Decimal`. Výhodou je přesnost hodnot. `Double` datový typ je rychlejší a vyžaduje méně paměti, ale může se vymezit chybami při zaokrouhlování. Datový typ `Decimal` zachovává úplnou přesnost na 28 desetinných míst.  
  
 Čísla s plovoucí desetinnou čárkou (`Single` a `Double`) mají větší rozsahy než čísla `Decimal`, ale mohou se vztahovat k chybám při zaokrouhlování. Typy s plovoucí desetinnou čárkou podporují méně platných číslic než `Decimal`, ale mohou představovat hodnoty většího rozsahu.  
  
 Hodnoty neintegrálního čísla mohou být vyjádřeny jako mmmEeee, ve kterém je mmm, kde je hodnota *mantisy* (nejvýznamnější číslice) a Eee je *exponent* (mocnina 10). Nejvyšší kladné hodnoty neintegrálních typů jsou 7.9228162514264337593543950335 E + 28 pro `Decimal`, 3.4028235 E + 38 pro `Single`a 1.79769313486231570 E + 308 pro `Double`.  
  
### <a name="performance"></a>Výkon  
 `Double` je nejúčinnější pro zlomky datových typů, protože procesory na současných platformách provádějí operace s plovoucí desetinnou čárkou s dvojitou přesností. Operace s `Double` ale nejsou stejně rychlé jako u integrálních typů, jako je `Integer`.  
  
### <a name="small-magnitudes"></a>Malá velikost  
 U čísel s nejmenším možným množstvím (nejbližším 0) mohou `Double` proměnné uchovávat čísla jako malá, 4.94065645841246544 E-324 pro záporné hodnoty a 4.94065645841246544 E-324 pro kladné hodnoty.  
  
### <a name="small-fractional-numbers"></a>Malá zlomková čísla  
 Pokud nepotřebujete plný rozsah datového typu `Double`, můžete použít datový typ `Single`, který může uchovávat čísla s plovoucí desetinnou čárkou z-3.4028235 E + 38 do 3.4028235 E + 38. Nejmenší velikost `Single` proměnných jsou-1.401298 E-45 pro záporné hodnoty a 1.401298 E-45 pro kladné hodnoty. Pokud máte velmi velký počet proměnných, které obsahují malá čísla s plovoucí desetinnou čárkou, může modul CLR (Common Language Runtime) někdy ukládat proměnné `Single` efektivněji a ušetřit spotřebu paměti.  
  
## <a name="see-also"></a>Viz také:

- [Základní datové typy](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Znakové datové typy](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)
- [Různé datové typy](../../../../visual-basic/programming-guide/language-features/data-types/miscellaneous-data-types.md)
- [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy](../../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
