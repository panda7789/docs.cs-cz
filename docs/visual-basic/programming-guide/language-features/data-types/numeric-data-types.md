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
ms.openlocfilehash: 8fa88172c9914a071e1b24e959c9030e6d219a30
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="numeric-data-types-visual-basic"></a>Numerické datové typy (Visual Basic)
Visual Basic poskytuje několik *číselné datové typy* pro zpracování čísla v různých reprezentace. *Integrální* typy představují jenom celá čísla (kladnou, zápornou a nula), a *nonintegral* typy představují čísla s celým číslem a zlomkové části.  
  
 Tabulka zobrazující porovnání vedle sebe Visual Basic – datové typy, najdete v části [datové typy](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
## <a name="integral-numeric-types"></a>Integrální číselné typy  
 *Integrální datové typy* jsou ty, které představují pouze čísel bez zlomkové části.  
  
 *Podepsané* integrální datové typy jsou [SByte – datový typ](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md) (8 bitů), [krátké datový typ](../../../../visual-basic/language-reference/data-types/short-data-type.md) (16 bitů), [Integer – datový typ](../../../../visual-basic/language-reference/data-types/integer-data-type.md) (32bitová verze) a [ Long – datový typ](../../../../visual-basic/language-reference/data-types/long-data-type.md) (64 bitů). Pokud proměnná obsahuje vždy celá čísla, nikoli desetinná čísla, deklarujte ji jako jeden z těchto typů.  
  
 *Nepodepsané* integrální typy jsou [Byte – datový typ](../../../../visual-basic/language-reference/data-types/byte-data-type.md) (8 bitů), [ushort – datový typ](../../../../visual-basic/language-reference/data-types/ushort-data-type.md) (16 bitů), [uinteger – datový typ](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md) (32bitová verze) a [ Ulong – datový typ](../../../../visual-basic/language-reference/data-types/ulong-data-type.md) (64 bitů). Pokud proměnná obsahuje binární data nebo data neznámé povahy, deklarujte ji jako jeden z těchto typů.  
  
### <a name="performance"></a>Výkon  
 Aritmetické operace je rychlejší s integrální typy než jiných typů. Jsou nejrychlejší s `Integer` a `UInteger` typy v jazyce Visual Basic.  
  
### <a name="large-integers"></a>Dlouhých celých čísel  
 Pokud potřebujete pro uložení celé číslo větší než `Integer` mohou být uloženy datový typ, můžete použít `Long` datový typ místo. `Long` proměnné mohou být uloženy čísla z-9,223,372,036,854,775,808 prostřednictvím 9,223,372,036,854,775,807. Operace s `Long` se nepatrně pomalejší v porovnání s `Integer`.  
  
 Pokud potřebujete i vyšší hodnoty, můžete použít [Decimal – datový typ](../../../../visual-basic/language-reference/data-types/decimal-data-type.md). Může obsahovat čísla z-79,228,162,514,264,337,593,543,950,335 prostřednictvím 79,228,162,514,264,337,593,543,950,335 v `Decimal` proměnnou, pokud se nepoužívá žádné desetinných míst. Ale operací s `Decimal` čísla je podstatně pomalejší než s žádným jiným typem číselná data.  
  
### <a name="small-integers"></a>Malá celá čísla  
 Pokud nepotřebujete plný rozsah `Integer` datového typu, můžete použít `Short` datového typu, která může pojmout celá čísla od-32 768 do 32 767. Pro nejmenší rozsah celých čísel `SByte` datový typ obsahuje celá čísla od -128 až 127. Pokud máte velký počet proměnných, které mají malý celá čísla, můžete modul common language runtime někdy uložit vaše `Short` a `SByte` proměnné efektivněji a uložte využití paměti. Ale operací s `Short` a `SByte` poněkud pomalejší, než se `Integer`.  
  
### <a name="unsigned-integers"></a>Celá čísla bez znaménka  
 Pokud víte, že vaše proměnná nikdy musí obsahovat záporné číslo, můžete použít *typy bez znaménka*`Byte`, `UShort`, `UInteger`, a `ULong`. Každý z těchto typů dat mohou být uloženy kladné celé číslo dvakrát tak velké, jeho odpovídající podepsané typu (`SByte`, `Short`, `Integer`, a `Long`). Z hlediska výkonu je právě efektivní jako jeho odpovídající typ se znaménkem každého typu bez znaménka. Konkrétně `UInteger` sdílí s `Integer` rozdíl způsobená maximální efektivitou všechny základní číselné datové typy.  
  
## <a name="nonintegral-numeric-types"></a>Nonintegral číselnými typy  
 *Nonintegral datové typy* jsou ty, které představují čísla s celým číslem a zlomkové části.  
  
 Nonintegral číselné datové typy jsou `Decimal` (dlouhodobý bod 128-bit), [jeden datový typ](../../../../visual-basic/language-reference/data-types/single-data-type.md) (32bitová verze plovoucí desetinné čárky), a [dvojitý datový typ](../../../../visual-basic/language-reference/data-types/double-data-type.md) (64 bitů plovoucí desetinné čárky). Jsou všechny podepsané typy. Pokud proměnná může obsahovat zlomek, deklarujte ji jako jeden z těchto typů.  
  
 `Decimal` není typu data s plovoucí desetinnou čárkou. `Decimal` čísla mají binární celočíselná hodnota a škálování faktor celé číslo, která určuje, jaká část hodnoty je zlomek decimal.  
  
 Můžete použít `Decimal` proměnných pro hodnoty peníze. Výhoda spočívá v tom přesnost hodnoty. `Double` Datový typ je rychlejší a vyžaduje méně paměti, ale je předmětem zaokrouhlení chyby. `Decimal` Datový typ uchovává dokončení přesnost na 28 desetinná místa.  
  
 S plovoucí desetinnou čárkou (`Single` a `Double`) čísla mít větší rozsah než `Decimal` čísla, ale mohou být předmětem zaokrouhlení chyby. Typy s plovoucí desetinnou čárkou podporují menší počet platných číslic než `Decimal` , ale může představovat hodnoty větší rozsahem.  
  
 Nonintegral číselné hodnoty může být vyjádřený jako mmmEeee, ve kterých je mmm *mantisa* (platných číslic) a je EEZ *exponent* (power 10). Nejvyšší kladné hodnoty nonintegral typy jsou 7.9228162514264337593543950335E + 28 pro `Decimal`, 3.4028235E + 38 pro `Single`a 1.79769313486231570E + 308 pro `Double`.  
  
### <a name="performance"></a>Výkon  
 `Double` je nejúčinnější desetinné datové typy, protože procesory na aktuální platformy provádět operace s plovoucí desetinnou čárkou v dvojitou přesností. Ale operací s `Double` nejsou tak rychlý jako u celočíselných typů jako `Integer`.  
  
### <a name="small-magnitudes"></a>Malé veličin  
 Pro čísla s nejnižší možné hodnotou (nejblíže k 0) `Double` proměnné mohou být uloženy čísla co - 4.94065645841246544E-324 pro záporné hodnoty a 4.94065645841246544E-324 pro kladné hodnoty.  
  
### <a name="small-fractional-numbers"></a>Malé desetinná čísla  
 Pokud nepotřebujete plný rozsah `Double` datového typu, můžete použít `Single` datového typu, která může pojmout čísla s plovoucí desetinnou čárkou od - 3.4028235E + 38 prostřednictvím 3.4028235E + 38. Nejmenší uskutečněných pro `Single` proměnné jsou – 1, 401298E-45 pro záporné hodnoty a 1, 401298E-45 pro kladné hodnoty. Pokud máte velký počet proměnných, které mají malý čísla s plovoucí desetinnou čárkou, modul CLR může někdy ukládat vaše `Single` proměnné efektivněji a uložte využití paměti.  
  
## <a name="see-also"></a>Viz také  
 [Základní datové typy](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Znakové datové typy](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)  
 [Různé datové typy](../../../../visual-basic/programming-guide/language-features/data-types/miscellaneous-data-types.md)  
 [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy](../../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
