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
ms.openlocfilehash: 29e5cbe09026dd52811c6c5fb88e940b45b7c0bb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821969"
---
# <a name="data-type-summary-visual-basic"></a>Souhrn datových typů (Visual Basic)
Následující tabulka uvádí datové typy jazyka Visual Basic, jejich podpůrné běžných typů modulu runtime jazyka, jejich přidělení nominální úložiště a jejich rozsahy hodnot.  
  
|Typ jazyka Visual Basic|Obvyklá struktura typu modulu runtime jazyka|Přidělení úložiště nominální|Rozsah hodnot|  
|-----------------------|--------------------------------------------|--------------------------------|-----------------|  
|[Datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<xref:System.Boolean>|Závisí na implementaci platformy|`True` Nebo `False`|  
|[Bajtů](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<xref:System.Byte>|1 bajt|0 až 255 (unsigned)|  
|[Char –](../../../visual-basic/language-reference/data-types/char-data-type.md) (jeden znak)|<xref:System.Char>|2 bajty|0 až 65535 (unsigned)|  
|[Datum](../../../visual-basic/language-reference/data-types/date-data-type.md)|<xref:System.DateTime>|8 bajtů|0:00:00 (půlnoc) na 1. ledna 0001 až 11:59:59 odp v 31. prosince 9999|  
|[Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<xref:System.Decimal>|16 bajtů|0 až +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9... E + 28) <sup>†</sup> s žádné desetinné čárky, 0 až +/-7,9228162514264337593543950335 28 míst napravo od desetinné čárky;<br /><br /> nejmenší nenulové číslo je +/-0,0000000000000000000000000001 (+/-1E-28) <sup>†</sup>|  
|[Dvojité](../../../visual-basic/language-reference/data-types/double-data-type.md) (dvojité přesnosti s plovoucí desetinnou čárkou)|<xref:System.Double>|8 bajtů|-1.79769313486231570E + 308 do - 4.94065645841246544E-324 <sup>†</sup> pro záporné hodnoty;<br /><br /> 4.94065645841246544E-324 prostřednictvím 1.79769313486231570E + 308 <sup>†</sup> pro kladné hodnoty|  
|[Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<xref:System.Int32>|4 bajty|-2,147,483,648 prostřednictvím 2 147 483 647 (se znaménkem)|  
|[Dlouhé](../../../visual-basic/language-reference/data-types/long-data-type.md) (long integer)|<xref:System.Int64>|8 bajtů|-9,223,372,036,854,775,808 prostřednictvím 9,223,372,036,854,775,807 (9.2... E + 18 <sup>†</sup>) (se znaménkem)|  
|[objekt](../../../visual-basic/language-reference/data-types/object-data-type.md)|<xref:System.Object> (třídy)|4 bajtů na 32bitové platformě<br /><br /> 8 bajtů na 64bitové platformě|Libovolný typ může být uložen v proměnné typu `Object`|  
|[SByte –](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<xref:System.SByte>|1 bajt|-128 až 127 (se znaménkem)|  
|[Krátký](../../../visual-basic/language-reference/data-types/short-data-type.md) (krátké celé číslo)|<xref:System.Int16>|2 bajty|-32 768 až 32 767 (se znaménkem)|  
|[Jeden](../../../visual-basic/language-reference/data-types/single-data-type.md) (jednoduchou přesnost s plovoucí desetinnou čárkou)|<xref:System.Single>|4 bajty|-3.4028235E + 38-1, 401298E-45 <sup>†</sup> pro záporné hodnoty;<br /><br /> 1, 401298E-45 prostřednictvím 3.4028235E + 38 <sup>†</sup> pro kladné hodnoty|  
|[Řetězec](../../../visual-basic/language-reference/data-types/string-data-type.md) (proměnné délky)|<xref:System.String> (třídy)|Závisí na implementaci platformy|0 na přibližně 2 miliardy znaků Unicode|  
|[UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<xref:System.UInt32>|4 bajty|0 až 4 294 967 295 (unsigned)|  
|[ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<xref:System.UInt64>|8 bajtů|0 až 18,446,744,073,709,551,615 (1.8... E + 19 <sup>†</sup>) (unsigned)|  
|[Uživatelem definované](../../../visual-basic/language-reference/data-types/user-defined-data-type.md) (struktura)|(dědí z <xref:System.ValueType>)|Závisí na implementaci platformy|Každý člen struktury má rozsah určují jeho datový typ a nezávislé z rozsahů jiných členů|  
|[UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<xref:System.UInt16>|2 bajty|0 až 65535 (unsigned)|  
  
 <sup>†</sup> v *vědecký zápis*, "E" odkazuje na násobky 10. Takže 3.56E + 2 označuje 3.56 x 10<sup>2</sup> nebo 356 a 3.56E-2 označuje 3.56 / 10<sup>2</sup> nebo 0.0356.  
  
> [!NOTE]
>  U řetězců obsahující text, použijte <xref:Microsoft.VisualBasic.Strings.StrConv%2A> funkce pro převod z jednoho formátu do jiného.  
  
 Kromě zadání datový typ v příkazu deklarace, můžete vynutit datový typ některé programovací prvky pomocí znak typu. Zobrazit [znaky](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).  
  
## <a name="memory-consumption"></a>Využití paměti  
 Při deklaraci základní datový typ není bezpečné předpokládá, že jeho využití paměti je stejné jako jeho přidělení nominální úložiště. Je to z důvodu následující aspekty:  
  
-   **Přiřazení úložiště.** Modul common language runtime můžete přiřadit úložiště založené na aktuální vlastnosti platformy, na kterém vaše aplikace provádí. Pokud paměti je téměř plná, může ji co nejblíže k sobě pack vaše deklarované elementy co nejvíce. V ostatních případech to může být zarovnat jejich adresy paměti na hranice fyzických hardwarových vazeb pro optimalizaci výkonu.  
  
-   **Šířka platformy.** Přiřazení úložiště na 64bitové platformě se liší od přiřazení na 32bitové platformě.  
  
### <a name="composite-data-types"></a>Složené datové typy  
 Jaké jsou požadavky stejné platí pro každý člen složené datového typu, jako je například struktura nebo pole. Nelze spoléhat na jednoduše sečtením nominálních přidělení úložiště členů typu. Kromě toho existují další důležité informace, jako je následující:  
  
-   **Režie.** Některé složené typy mají požadavky na paměť navíc. Například pole používá extra paměť pro pole samotného a také pro jednotlivé rozměry. Na 32bitové platformě právě tato dodatečná režie 12 bajtů plus 8 bajtů pro jednotlivé rozměry. Na 64bitové platformě je dvojitá tento požadavek.  
  
-   **Rozložení úložiště.** Nelze bezpečně předpokládat, že pořadí úložiště v paměti je stejné jako vaše pořadí prohlášení. I nelze vytvořit předpoklady o zarovnání bajt, jako jsou hranice bajtu 2 nebo 4 bajty. Pokud definujete třídu nebo strukturu a je nutné řídit rozložení úložiště z jejích členů, můžete použít <xref:System.Runtime.InteropServices.StructLayoutAttribute> atribut třídy nebo struktury.  
  
### <a name="object-overhead"></a>Režijní náklady na objekt  
 `Object` Vztahující se k libovolným datům základní nebo složený typ používá 4 bajty kromě data obsažená v datovém typu.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Strings.StrConv%2A>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Znaky typu](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
