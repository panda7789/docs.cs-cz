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
ms.openlocfilehash: 8afeba3f88c4bfe6e1c9777f950c3b458665e340
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591791"
---
# <a name="data-type-summary-visual-basic"></a>Souhrn datových typů (Visual Basic)
V následující tabulce jsou uvedeny Visual Basic – datové typy a jejich podpůrné běžné typy runtime jazyka, jejich přidělení nominální úložiště a jejich rozsahy hodnotu.  
  
|Typ jazyka Visual Basic|Běžné struktura typu modulu runtime jazyka|Přidělení nominální úložiště|Rozsah hodnot|  
|-----------------------|--------------------------------------------|--------------------------------|-----------------|  
|[Logická hodnota](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<xref:System.Boolean>|Závisí na implementaci platformy|`True` Nebo `False`|  
|[Bajtů](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<xref:System.Byte>|1 bajt|0 do 255 (bez znaménka)|  
|[Char –](../../../visual-basic/language-reference/data-types/char-data-type.md) (jeden znak)|<xref:System.Char>|2 bajtů|0 až 65535 (bez znaménka)|  
|[Datum](../../../visual-basic/language-reference/data-types/date-data-type.md)|<xref:System.DateTime>|8 bajtů|0:00:00 (půlnoc) na 1. ledna 0001 prostřednictvím 23:59:59: 00 na 31. prosince 9999|  
|[Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<xref:System.Decimal>|16 bajtů|0 až +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9 … E + 28) <sup>†</sup> bez desetinné čárky; 0 až +/-7,9228162514264337593543950335 s 28 místy vpravo od desetinné čárky;<br /><br /> nejmenší nenulové číslo je +/-0,0000000000000000000000000001 (+/-1E-28) <sup>†</sup>|  
|[Dvojité](../../../visual-basic/language-reference/data-types/double-data-type.md) (Dvojitá přesnost s plovoucí desetinnou čárkou)|<xref:System.Double>|8 bajtů|-1.79769313486231570E + 308 prostřednictvím - 4.94065645841246544E-324 <sup>†</sup> pro záporné hodnoty;<br /><br /> 4.94065645841246544E-324 prostřednictvím 1.79769313486231570E + 308 <sup>†</sup> pro kladné hodnoty.|  
|[celé číslo](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<xref:System.Int32>|4 bajty|-2,147,483,648 prostřednictvím 2 147 483 647 (se znaménkem)|  
|[Dlouhé](../../../visual-basic/language-reference/data-types/long-data-type.md) (dlouhých celých čísel)|<xref:System.Int64>|8 bajtů|-9,223,372,036,854,775,808 prostřednictvím 9,223,372,036,854,775,807 (9.2 … E + 18 <sup>†</sup>) (se znaménkem)|  
|[Objekt](../../../visual-basic/language-reference/data-types/object-data-type.md)|<xref:System.Object> (třída)|4 bajtů na 32bitové platformě<br /><br /> 8 bajtů na 64bitové platformě|Žádný typ, může být uložené v proměnné typu `Object`|  
|[SByte –](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<xref:System.SByte>|1 bajt|-128 až 127 (se znaménkem)|  
|[Krátký](../../../visual-basic/language-reference/data-types/short-data-type.md) (krátký celé číslo)|<xref:System.Int16>|2 bajtů|-32 768 do 32 767 (se znaménkem)|  
|[Jeden](../../../visual-basic/language-reference/data-types/single-data-type.md) (jednoduchou přesností s plovoucí desetinnou čárkou)|<xref:System.Single>|4 bajty|-3.4028235E + 38 prostřednictvím - 1, 401298E-45 <sup>†</sup> pro záporné hodnoty;<br /><br /> 1, 401298E-45 prostřednictvím 3.4028235E + 38 <sup>†</sup> pro kladné hodnoty.|  
|[Řetězec](../../../visual-basic/language-reference/data-types/string-data-type.md) (proměnlivou délkou)|<xref:System.String> (třída)|Závisí na implementaci platformy|0 přibližně 2 miliardy znaků Unicode|  
|[Uinteger –](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<xref:System.UInt32>|4 bajty|0 až 4 294 967 295 (bez znaménka)|  
|[Ulong –](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<xref:System.UInt64>|8 bajtů|0 až 18,446,744,073,709,551,615 (1.8 … E + 19 <sup>†</sup>) (bez znaménka)|  
|[Uživatelem definované](../../../visual-basic/language-reference/data-types/user-defined-data-type.md) (struktura)|(dědí z <xref:System.ValueType>)|Závisí na implementaci platformy|Každý člen struktury má rozsah zjistit podle jeho datového typu a nezávislé na rozsahy ostatních členů|  
|[Ushort –](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<xref:System.UInt16>|2 bajtů|0 až 65 535 (bez znaménka)|  
  
 <sup>†</sup> v *vědecká notace*, "E" odkazuje na zadanou mocninu. 10. Takže 3.56E + 2 označuje 3.56 × 10<sup>2</sup> nebo 356 a 3.56E-2 označuje 3.56 / 10<sup>2</sup> nebo 0.0356.  
  
> [!NOTE]
>  Řetězce obsahující text, použijte <xref:Microsoft.VisualBasic.Strings.StrConv%2A> funkce pro převod z jednoho textového formátu do druhého.  
  
 Kromě určení datový typ v příkazu deklaraci, můžete vynutit datový typ některé elementům programování s použitím – znak typu. V tématu [zadejte znaky](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).  
  
## <a name="memory-consumption"></a>Paměťové nároky  
 Po deklarování základní datový typ není bezpečné předpokládat, že jeho využití paměti je stejný jako jeho přidělení nominální úložiště. Je to z důvodu následující aspekty:  
  
-   **Přiřazení úložiště.** Modul common language runtime můžete přiřadit úložiště založené na aktuální charakteristiky platformy, na kterém je prováděna vaší aplikace. Pokud paměti je téměř plná, může ho vaše deklarované elementy jako úzce pack společně, nejdříve. V ostatních případech se může zarovnat jejich adresy paměti na hranice přirozené hardwaru za účelem optimalizace výkonu.  
  
-   **Šířka platformy.** Přiřazení úložiště na 64bitové platformě se liší od přiřazení na 32bitové platformě.  
  
### <a name="composite-data-types"></a>Složené datové typy  
 Stejné aspekty platí pro každého člena složený datový typ, třeba do struktury nebo pole. Nelze spoléhat na jednoduše přidáním společně přidělení nominální úložiště typ členů. Kromě toho existují další důležité informace, například následující:  
  
-   **Režijní náklady.** Některé složené typy mít požadavky na další paměť. Například pole používá paměť navíc pro samotné pole a také pro každou dimenzi. Na 32bitové platformě právě tato dodatečná režie 12 bajtů plus 8 bajtů pro každý dimenzi. Na 64bitové platformě je dvojnásobný tento požadavek.  
  
-   **Rozložení úložiště.** Nelze předpokládat bezpečně pořadí úložiště v paměti je stejný jako vaši objednávku deklarace. Nemůžete i předpoklady o zarovnání bajtů, jako je například 2bajtová nebo 4bajtový hranic. Pokud definujete třídu nebo strukturu a potřebujete řídit rozložení úložiště svých členů, můžete použít <xref:System.Runtime.InteropServices.StructLayoutAttribute> atribut třídu nebo strukturu.  
  
### <a name="object-overhead"></a>Režijní náklady na objekt  
 `Object` Odkazující na všechna data základní nebo složený typ používá 4 bajtů navíc data obsažená v datovém typu.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Strings.StrConv%2A>  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Znaky typu](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
