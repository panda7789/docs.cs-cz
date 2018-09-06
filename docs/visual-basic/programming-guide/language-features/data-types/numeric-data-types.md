---
title: Numerické datové typy (Visual Basic)
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
ms.openlocfilehash: 6578a410e389a313b0bad70f043691240e288887
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865755"
---
# <a name="numeric-data-types-visual-basic"></a>Numerické datové typy (Visual Basic)
Visual Basic poskytuje několik *číselných datových typů* pro zpracování čísel v různé reprezentace. *Integrální* typy představují pouze celá čísla (kladná, záporná a nula), a *nonintegral* typy představují celé číslo a zlomkové části čísla.  
  
 Tabulka zobrazující vedle sebe porovnání datových typů jazyka Visual Basic, naleznete v tématu [datové typy](../../../../visual-basic/language-reference/data-types/index.md).  
  
## <a name="integral-numeric-types"></a>Integrální číselné typy  
 *Integrální datové typy* jsou ty, které představují pouze čísel bez zlomkové části.  
  
 *Podepsané* integrální datové typy jsou [SByte – datový typ](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md) (8 bitů), [krátký datový typ](../../../../visual-basic/language-reference/data-types/short-data-type.md) (16-bit), [Integer – datový typ](../../../../visual-basic/language-reference/data-types/integer-data-type.md) (32bitová verze) a [ Long – datový typ](../../../../visual-basic/language-reference/data-types/long-data-type.md) (64 bitů). Pokud proměnnou vždy uloží, celá čísla, spíše než desetinná čísla, deklarujte ho jako jeden z těchto typů.  
  
 *Bez znaménka* integrální typy jsou [Byte – datový typ](../../../../visual-basic/language-reference/data-types/byte-data-type.md) (8 bitů), [ushort – datový typ](../../../../visual-basic/language-reference/data-types/ushort-data-type.md) (16-bit), [uinteger – datový typ](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md) (32bitová verze) a [ Ulong – datový typ](../../../../visual-basic/language-reference/data-types/ulong-data-type.md) (64 bitů). Pokud proměnná obsahuje binární data nebo data neznámé fázi, deklarujte ho jako jeden z těchto typů.  
  
### <a name="performance"></a>Výkon  
 Aritmetické operace jsou rychleji s využitím celočíselných typů než s jinými datovými typy. Jsou nejrychlejší `Integer` a `UInteger` typy v jazyce Visual Basic.  
  
### <a name="large-integers"></a>Velkých celých čísel  
 Pokud potřebujete k uložení celé číslo větší než `Integer` může obsahovat datový typ, můžete použít `Long` datový typ místo. `Long` proměnné můžou obsahovat čísla z-9,223,372,036,854,775,808 prostřednictvím 9,223,372,036,854,775,807. Operace s `Long` se nepatrně pomalejší v porovnání s `Integer`.  
  
 Pokud ještě větší hodnoty budete potřebovat, můžete použít [datový typ Decimal](../../../../visual-basic/language-reference/data-types/decimal-data-type.md). Může obsahovat čísla z-79,228,162,514,264,337,593,543,950,335 prostřednictvím 79,228,162,514,264,337,593,543,950,335 v `Decimal` proměnnou, pokud nepoužijete desetinná místa. Nicméně operace s `Decimal` čísla jsou mnohem pomalejší než s žádným jiným typem číselná data.  
  
### <a name="small-integers"></a>Malé celých čísel  
 Pokud nepotřebujete celou škálu `Integer` datový typ, můžete použít `Short` datového typu, který může obsahovat celá čísla od-32 768 až 32 767. Pro nejmenší rozsah celých čísel `SByte` datového typu obsahuje celá čísla od -128 až 127. Pokud máte velký počet proměnné, které obsahují malé celých čísel, modul common language runtime může někdy ukládat vaše `Short` a `SByte` proměnné efektivněji a uložte si využití paměti. Nicméně operace s `Short` a `SByte` jsou o něco pomalejší než s `Integer`.  
  
### <a name="unsigned-integers"></a>Celá čísla bez znaménka  
 Pokud víte, že vaše proměnná nikdy nemusí obsahovat záporné číslo, můžete použít *typy bez znaménka*`Byte`, `UShort`, `UInteger`, a `ULong`. Každý z těchto typů dat může obsahovat kladné celé číslo dvakrát zvětšit jak odpovídající typ se znaménkem (`SByte`, `Short`, `Integer`, a `Long`). Každý typ bez znaménka se z hlediska výkonu, přesně tak efektivní jako jeho odpovídající typ se znaménkem. Zejména `UInteger` sdílí s `Integer` rozlišení je nejúčinnější základní číselných datových typů.  
  
## <a name="nonintegral-numeric-types"></a>Nonintegral číselné typy  
 *Nonintegral datové typy* jsou ty, které představují číslice se celé číslo a zlomkové části.  
  
 Nonintegral číselné datové typy jsou `Decimal` (128bitové pevnému bodu) [jeden datový typ](../../../../visual-basic/language-reference/data-types/single-data-type.md) (32 bitů s plovoucí desetinnou čárkou bodu), a [datový typ Double](../../../../visual-basic/language-reference/data-types/double-data-type.md) (64 bitů s plovoucí desetinnou čárkou). Jsou všechny podepsané typy. Pokud proměnná může obsahovat zlomek, deklarujte ho jako jeden z těchto typů.  
  
 `Decimal` není typ s plovoucí desetinnou čárkou data. `Decimal` čísla mají binární celočíselnou hodnotou a škálovací faktor celého čísla, která určuje, jaká část hodnoty je desetinný zlomek.  
  
 Můžete použít `Decimal` proměnné pro peněžní hodnoty. Výhodou je přesnosti hodnoty. `Double` Datový typ je rychlejší a vyžaduje méně paměti, ale je v souladu s předešlo chybám při zaokrouhlování. `Decimal` Datový typ zachová úplný přesnost na 28 desetinná místa.  
  
 S plovoucí desetinnou čárkou (`Single` a `Double`) čísla mají větší rozsah než `Decimal` čísla, ale může být v souladu s předešlo chybám při zaokrouhlování. Typy s plovoucí desetinnou čárkou podporují méně významných číslic než `Decimal` ale může představovat hodnoty větší velikosti.  
  
 Nonintegral číselných hodnot může být vyjádřený jako mmmEeee, ve kterých je mmm *mantisa* (významných číslic) a je EEZ *exponent* (násobky 10). Nejvyšší kladné hodnoty nonintegral typy jsou 7.9228162514264337593543950335E + 28 pro `Decimal`, 3.4028235E + 38 pro `Single`a 1.79769313486231570E + 308 pro `Double`.  
  
### <a name="performance"></a>Výkon  
 `Double` je nejefektivnější desetinné části datových typů, protože procesory na aktuální platformy provádět operace s plovoucí desetinnou čárkou v dvojité přesnosti. Nicméně operace s `Double` nejsou tak rychle, stejně jako u celočíselných typů, jako `Integer`.  
  
### <a name="small-magnitudes"></a>Malé veličin  
 Pro čísla s nejmenší možné velikost (nejbližší 0) `Double` proměnné můžou obsahovat čísla malá jako - 4.94065645841246544E-324 pro záporné hodnoty a 4.94065645841246544E-324 pro kladné hodnoty.  
  
### <a name="small-fractional-numbers"></a>Malé zlomkové číslice  
 Pokud nepotřebujete celou škálu `Double` datový typ, můžete použít `Single` datového typu, který může obsahovat čísla s plovoucí desetinnou čárkou z - 3.4028235E + 38 prostřednictvím 3.4028235E + 38. Nejmenší řádově pro `Single` proměnné jsou – 1, 401298E-45 pro záporné hodnoty a 1, 401298E-45 pro kladné hodnoty. Pokud máte velký počet proměnné, které obsahují malé čísla s plovoucí desetinnou čárkou, modul common language runtime může někdy ukládat vaše `Single` proměnné efektivněji a uložte si využití paměti.  
  
## <a name="see-also"></a>Viz také  
 [Základní datové typy](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Znakové datové typy](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)  
 [Různé datové typy](../../../../visual-basic/programming-guide/language-features/data-types/miscellaneous-data-types.md)  
 [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy](../../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
