---
title: Číselné datové typy
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
ms.openlocfilehash: 72cdca295e209935687f67ad290e816775d9fe13
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393673"
---
# <a name="numeric-data-types-visual-basic"></a>Numerické datové typy (Visual Basic)
Visual Basic poskytuje několik *číselných datových typů* pro zpracování čísel v různých vyjádřeních reprezentace. *Integrální* typy reprezentují pouze celá čísla (kladné, záporné a nula) a *neintegrální* typy reprezentují čísla s celými čísly i zlomky částí.  
  
 Tabulka znázorňující souběžné porovnání Visual Basic datových typů najdete v tématu [datové typy](../../../language-reference/data-types/index.md).  
  
## <a name="integral-numeric-types"></a>Celočíselné číselné typy  
 *Integrální datové typy* jsou ty, které představují pouze čísla bez zlomkových částí.  
  
 Počet *podepsaných* integrálních datových typů je [SByte datový typ](../../../language-reference/data-types/sbyte-data-type.md) (8bitové), [krátký datový typ](../../../language-reference/data-types/short-data-type.md) (16bitový), [celočíselný datový typ](../../../language-reference/data-types/integer-data-type.md) (32 bitů) a [dlouhý datový typ](../../../language-reference/data-types/long-data-type.md) (64-bit). Pokud proměnná vždy ukládá celá čísla spíše než zlomková čísla, deklarujte ji jako jeden z těchto typů.  
  
 Celočíselné typy *bez znaménka* jsou [bajtový datový typ](../../../language-reference/data-types/byte-data-type.md) (8bitové), [UShort datový typ](../../../language-reference/data-types/ushort-data-type.md) (16bitový), [UInteger – datový typ](../../../language-reference/data-types/uinteger-data-type.md) (32-bit) a [ulong datový typ](../../../language-reference/data-types/ulong-data-type.md) (64-bit). Pokud proměnná obsahuje binární data nebo data neznámé povahy, deklarujete je jako jeden z těchto typů.  
  
### <a name="performance"></a>Výkon  
 Aritmetické operace jsou rychlejší s integrálními typy než s jinými datovými typy. Jsou nejrychlejší s `Integer` `UInteger` typy a v Visual Basic.  
  
### <a name="large-integers"></a>Velká celá čísla  
 Pokud potřebujete uchovat celé číslo větší než `Integer` datový typ, můžete `Long` místo toho použít datový typ. `Long`proměnné můžou obsahovat čísla od-9223372036854775808 do 9 223 372 036 854 775 807. Operace s `Long` jsou trochu pomalejší než s `Integer` .  
  
 Pokud potřebujete ještě větší hodnoty, můžete použít [datový typ Decimal](../../../language-reference/data-types/decimal-data-type.md). `Decimal`Pokud nepoužijete žádné desetinné místo, můžete čísla z-79,228,162,514,264,337,593,543,950,335 až 79,228,162,514,264,337,593,543,950,335 v proměnné uchovávat. Operace s `Decimal` čísly však jsou mnohem pomalejší než u jakéhokoli jiného číselného datového typu.  
  
### <a name="small-integers"></a>Malá celá čísla  
 Pokud nepotřebujete plný rozsah `Integer` datového typu, můžete použít `Short` datový typ, který může uchovávat celá čísla od-32 768 do 32 767. Pro nejmenší rozsah celého čísla `SByte` datový typ obsahuje celá čísla od-128 do 127. Pokud máte velmi velký počet proměnných, které obsahují malá celá čísla, může modul CLR (Common Language Runtime) někdy úložiště `Short` a `SByte` proměnné ukládat efektivněji a ušetřit spotřebu paměti. Nicméně operace s `Short` a `SByte` jsou trochu pomalejší než s `Integer` .  
  
### <a name="unsigned-integers"></a>Celá čísla bez znaménka  
 Pokud víte, že proměnná nikdy nepotřebuje držet záporné číslo, můžete použít *typy bez znaménka* `Byte` , `UShort` , `UInteger` a `ULong` . Každý z těchto datových typů může uchovávat kladné celé číslo dvakrát tak velké jako odpovídající typ se znaménkem ( `SByte` , `Short` , `Integer` a `Long` ). V souvislosti s výkonem je každý typ bez znaménka přesně stejně účinný jako odpovídající typ se znaménkem. Zejména `UInteger` sdílené složky s rozlišením, které jsou nejúčinnější `Integer` ze všech základních číselných datových typů.  
  
## <a name="nonintegral-numeric-types"></a>Neceločíselné číselné typy  
 *Neintegrální datové typy* jsou ty, které představují čísla s celočíselnou i zlomkovou částí.  
  
 Neintegrální číselné datové typy jsou `Decimal` (128 – pevný pevný bod), [jeden datový typ](../../../language-reference/data-types/single-data-type.md) (32-bit s plovoucí desetinnou čárkou) a [datový typ Double](../../../language-reference/data-types/double-data-type.md) (64-bit floated Point). Jsou to všechny typy se znaménkem. Pokud proměnná může obsahovat zlomek, deklarujte ji jako jeden z těchto typů.  
  
 `Decimal`není datový typ s plovoucí desetinnou čárkou. `Decimal`čísla mají binární celočíselnou hodnotu a faktor měřítka celého čísla, který určuje, jaká část hodnoty je desítkový zlomek.  
  
 `Decimal`Pro peněžní hodnoty můžete použít proměnné. Výhodou je přesnost hodnot. `Double`Datový typ je rychlejší a vyžaduje méně paměti, ale může se jednat o chyby při zaokrouhlování. `Decimal`Datový typ zachovává úplnou přesnost na 28 desetinných míst.  
  
 Čísla s plovoucí desetinnou čárkou ( `Single` a `Double` ) mají větší rozsahy než `Decimal` čísla, ale můžou být v souladu s chybami při zaokrouhlování. Typy s plovoucí desetinnou čárkou podporují méně platných číslic `Decimal` , než mohou představovat hodnoty většího rozsahu.  
  
 Hodnoty neintegrálního čísla mohou být vyjádřeny jako mmmEeee, ve kterém je mmm, kde je hodnota *mantisy* (nejvýznamnější číslice) a Eee je *exponent* (mocnina 10). Nejvyšší kladné hodnoty neintegrálních typů jsou 7.9228162514264337593543950335 E + 28 pro `Decimal` , 3.4028235 e + 38 pro a `Single` 1.79769313486231570 e + 308 pro `Double` .  
  
### <a name="performance"></a>Výkon  
 `Double`je nejúčinnější pro zlomky datových typů, protože procesory na současných platformách provádějí operace s plovoucí desetinnou čárkou s dvojitou přesností. Operace s ale nejsou `Double` stejně rychlé jako u integrálních typů, jako je `Integer` .  
  
### <a name="small-magnitudes"></a>Malá velikost  
 Pro čísla s nejmenším možným rozsahem (nejbližší 0) `Double` mohou proměnné uchovávat čísla jako malá, 4.94065645841246544 e-324 pro záporné hodnoty a 4.94065645841246544 e-324 pro kladné hodnoty.  
  
### <a name="small-fractional-numbers"></a>Malá zlomková čísla  
 Pokud nepotřebujete plný rozsah `Double` datového typu, můžete použít `Single` datový typ, který může uchovávat čísla s plovoucí desetinnou čárkou z-3.4028235 e + 38 do 3.4028235 e + 38. Nejmenší velikost pro `Single` proměnné jsou-1.401298 e-45 pro záporné hodnoty a 1.401298 e-45 pro kladné hodnoty. Pokud máte velmi velký počet proměnných, které obsahují malá čísla s plovoucí desetinnou čárkou, může modul CLR (Common Language Runtime) někdy ukládat `Single` proměnné efektivněji a ušetřit spotřebu paměti.  
  
## <a name="see-also"></a>Viz také

- [Základní datové typy](elementary-data-types.md)
- [Znakové datové typy](character-data-types.md)
- [Různé datové typy](miscellaneous-data-types.md)
- [Řešení potíží s datovými typy](troubleshooting-data-types.md)
- [Postupy: Volání funkce Windows, která přebírá typy bez znaménka](../../com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
