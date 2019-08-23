---
title: Souhrn datových typů (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Boolean data type [Visual Basic], supported types in Visual Basic
- storage [Visual Basic], order of storage
- data types [Visual Basic], Visual Basic
- Single data type [Visual Basic], supported types in Visual Basic
- notation [Visual Basic], scientific
- memory requirements, data types
- user-defined data types [Visual Basic], Visual Basic
- Date data type [Visual Basic], Visual Basic
- Visual Basic, data types
- storage [Visual Basic], allocation
- Integer data type [Visual Basic], Visual Basic data types
- storage [Visual Basic], space
- Variant data types [Visual Basic], supported types in Visual Basic
- Char data type [Visual Basic], Visual Basic data types
- intrinsic data types [Visual Basic]
- memory consumption [Visual Basic], data types
- single-precision numbers
- data types [Visual Basic], order of storage
- Long data type [Visual Basic], supported types in Visual Basic
- String data type [Visual Basic], Visual Basic data types
- storage order, data types
- StructLayoutAttribute class, Visual Basic data type storage
- scientific notation
- Double data type [Visual Basic], Visual Basic data types
- Byte data type [Visual Basic], Visual Basic data types
- Object data type [Visual Basic], supported types in Visual Basic
- data types [Visual Basic], storage allocation
- double-precision numbers
- data types [Visual Basic], summary
- dates [Visual Basic], data types
- strings [Visual Basic], data types
- memory consumption
- storage order, controlling in Visual Basic
- data types [Visual Basic], memory requirements
ms.assetid: e975cdb6-64d8-4a4a-ae27-f3b3ed198ae0
ms.openlocfilehash: 57f6caa00806f4874cb8070805e8b6784ec82e40
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956806"
---
# <a name="data-type-summary-visual-basic"></a>Souhrn datových typů (Visual Basic)
V následující tabulce jsou uvedeny Visual Basic datových typů, jejich podporují typy společného jazykového modulu runtime, jejich jmenovité přidělení úložiště a jejich rozsahy hodnot.  
  
|Typ Visual Basic|Struktura typů společného jazykového modulu runtime|Přidělení nominálního úložiště|Rozsah hodnot|  
|-----------------------|--------------------------------------------|--------------------------------|-----------------|  
|[Datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<xref:System.Boolean>|Závisí na implementaci platformy|`True` Nebo `False`|  
|[Bytové](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<xref:System.Byte>|1 bajt|0 až 255 (bez znaménka)|  
|[Znak](../../../visual-basic/language-reference/data-types/char-data-type.md) (jeden znak)|<xref:System.Char>|2 bajty|0 až 65535 (bez znaménka)|  
|[Datum](../../../visual-basic/language-reference/data-types/date-data-type.md)|<xref:System.DateTime>|8 bajtů|0:00:00 (půlnoc) 1. ledna 0001 až 11:59:59 odp. prosince 9999|  
|[Notaci](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<xref:System.Decimal>|16 bajtů|od 0 do +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9...E + 28) <sup>†</sup> bez desetinné čárky; 0 až +/-7.9228162514264337593543950335 s 28 místy napravo od desetinné čárky;<br /><br /> nejmenší nenulové číslo je +/-0,0000000000000000000000000001 (+/-1E-28) <sup>†</sup> .|  
|[Typ Double](../../../visual-basic/language-reference/data-types/double-data-type.md) (plovoucí desetinná čárka s dvojitou přesností)|<xref:System.Double>|8 bajtů|-1.79769313486231570 e + 308 do-4.94065645841246544 E-324 <sup>†</sup> pro záporné hodnoty;<br /><br /> 4.94065645841246544 e-324 až 1.79769313486231570 E + 308 <sup>†</sup> pro kladné hodnoty|  
|[Čísla](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<xref:System.Int32>|4 bajty|-2 147 483 648 až 2 147 483 647 (podepsáno)|  
|[Long](../../../visual-basic/language-reference/data-types/long-data-type.md) (dlouhé celé číslo)|<xref:System.Int64>|8 bajtů|-9223372036854775808 až 9 223 372 036 854 775 807 (9.2... E + 18 <sup>†</sup>) (podepsáno)|  
|[objekt](../../../visual-basic/language-reference/data-types/object-data-type.md)|<xref:System.Object>Deník|4 bajty na 32 bitové platformě<br /><br /> 8 bajtů na 64. bitová platforma|Libovolný typ může být uložený v proměnné typu.`Object`|  
|[SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<xref:System.SByte>|1 bajt|-128 až 127 (podepsáno)|  
|[Krátká](../../../visual-basic/language-reference/data-types/short-data-type.md) (krátké celé číslo)|<xref:System.Int16>|2 bajty|-32 768 až 32 767 (podepsáno)|  
|[Jeden](../../../visual-basic/language-reference/data-types/single-data-type.md) (plovoucí desetinná čárka s jednoduchou přesností)|<xref:System.Single>|4 bajty|-3.4028235 e + + 38 do-1.401298 E-45 <sup>†</sup> pro záporné hodnoty;<br /><br /> 1.401298 e-45 až 3.4028235 E + 38 <sup>†</sup> pro kladné hodnoty|  
|[Řetězec](../../../visual-basic/language-reference/data-types/string-data-type.md) (proměnlivá délka)|<xref:System.String>Deník|Závisí na implementaci platformy|0 až přibližně 2 000 000 000 znaků Unicode|  
|[UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<xref:System.UInt32>|4 bajty|0 až 4 294 967 295 (bez znaménka)|  
|[ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<xref:System.UInt64>|8 bajtů|0 až 18446744073709551615 (1.8... E + 19 <sup>†</sup>) (bez znaménka)|  
|[Uživatelsky definované](../../../visual-basic/language-reference/data-types/user-defined-data-type.md) strukturované|(dědí z <xref:System.ValueType>)|Závisí na implementaci platformy|Každý člen struktury má rozsah určený jeho datovým typem a nezávisle na rozsahu ostatních členů.|  
|[UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<xref:System.UInt16>|2 bajty|0 až 65 535 (bez znaménka)|  
  
 <sup>†</sup> V *matematickém zápisu*"E" odkazuje na sílu 10. Takže 3.56 E + 2 znamená 3,56 x 10<sup>2</sup> nebo 356 a 3.56 e-2 znamená 3,56/10<sup>2</sup> nebo 0,0356.  
  
> [!NOTE]
> Pro řetězce obsahující text použijte <xref:Microsoft.VisualBasic.Strings.StrConv%2A> funkci pro převod z jednoho textového formátu do jiného.  
  
 Kromě určení datového typu v příkazu deklarace můžete vynutit datový typ některých programovacích prvků pomocí znaku typu. Viz [znaky typu](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).  
  
## <a name="memory-consumption"></a>Spotřeba paměti  
 Pokud deklarujete základní datový typ, není bezpečné předpokládat, že jeho využití paměti je stejné jako jeho jmenovité přidělení úložiště. To je způsobeno následujícími požadavky:  
  
- **Přiřazení úložiště** Modul CLR (Common Language Runtime) může přiřazovat úložiště na základě aktuálních vlastností platformy, na které je aplikace spuštěná. Pokud je paměť skoro plná, může vaše deklarované prvky nabalit co nejpřesněji. V ostatních případech může zarovnávat jejich paměťové adresy s přirozenými hranicemi hardwaru za účelem optimalizace výkonu.  
  
- **Šířka platformy.** Přiřazení úložiště na 64 platformě se liší od přiřazení na 32 platformě.  
  
### <a name="composite-data-types"></a>Složené datové typy  
 Stejné požadavky platí pro každého člena složeného datového typu, jako je například struktura nebo pole. Nemůžete spoléhat na pouhé přidání nominálního přidělení úložiště členů typu. Kromě toho existují i další okolnosti, například následující:  
  
- **Zvyšoval.** Některé složené typy mají další požadavky na paměť. Například pole používá dodatečnou paměť pro samotné pole a také pro každou dimenzi. Na 32 platformě je tato režie aktuálně 12 bajtů plus 8 bajtů pro každou dimenzi. Na 64 platformě se tento požadavek zdvojnásobuje.  
  
- **Rozložení úložiště** Nemůžete bezpečně předpokládat, že pořadí úložiště v paměti je stejné jako vaše pořadí deklarace. Nemůžete ani dělat předpoklady o zarovnání bajtů, jako je například hranice 2 nebo 4 bajty. Pokud definujete třídu nebo strukturu a potřebujete řídit rozložení úložiště členů, můžete použít <xref:System.Runtime.InteropServices.StructLayoutAttribute> atribut pro třídu nebo strukturu.  
  
### <a name="object-overhead"></a>Režie objektu  
 `Object` Odkaz na jakýkoli základní nebo složený datový typ používá kromě dat obsažených v datovém typu 4 bajty.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Strings.StrConv%2A>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Znaky typu](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
