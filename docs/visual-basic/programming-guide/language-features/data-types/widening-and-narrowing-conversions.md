---
title: Rozšíření a zúžení převodů (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- widening conversions [Visual Basic]
- narrowing conversions [Visual Basic]
- conversions [Visual Basic], type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- conversions [Visual Basic], exceptions during conversion
- type conversion [Visual Basic], exceptions during conversion
- conversions [Visual Basic], data type
- conversions [Visual Basic], narrowing
- type conversion [Visual Basic], narrowing
- data type conversion [Visual Basic], widening
- data type conversion [Visual Basic], narrowing
- changing data types [Visual Basic]
- type conversion [Visual Basic], widening
- data type conversion [Visual Basic], exceptions during conversion
- conversions [Visual Basic], widening
ms.assetid: 058c3152-6c28-4268-af44-2209e774f0bd
ms.openlocfilehash: e2dbbd63be07a19c6e05c7ec8f94bdcd8f50c902
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586313"
---
# <a name="widening-and-narrowing-conversions-visual-basic"></a>Rozšíření a zúžení převodů (Visual Basic)
Což je důležité při převodu typu je, zda výsledkem převodu je v rozsahu cílového datového typu.  
  
 A *rozšiřující převod* změní hodnotu na datový typ, který můžete povolit pro všechny možné hodnoty původní data.  Rozšiřující převody zachovat zdrojovou hodnotu, ale můžete změnit její reprezentace. K tomu dojde, pokud převod z celočíselného typu na `Decimal`, nebo z `Char` k `String`.  
  
 A *zužující převod* změní hodnotu na datový typ, který nemusí být schopný uchovat některou z možných hodnot. Například je desetinná hodnota zaokrouhlena při převodu integrálního typu a číselného typu, který je převáděn na `Boolean` je omezená na jednu `True` nebo `False`.  
  
## <a name="widening-conversions"></a>Rozšiřující převody  
 V následující tabulce jsou uvedeny standard rozšiřující převody.  
  
|Datový typ|Rozšiřuje na datové typy <sup>1</sup>|  
|---|---|  
|[SByte –](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[Bajtů](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[krátké](../../../../visual-basic/language-reference/data-types/short-data-type.md)|`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[UShort](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Integer](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[UInteger](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Long](../../../../visual-basic/language-reference/data-types/long-data-type.md)|`Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[ULong](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|`ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Decimal](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Jeden](../../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`, `Double`|  
|[Double](../../../../visual-basic/language-reference/data-types/double-data-type.md)|`Double`|  
|Některé Výčtový typ ([výčtu](../../../../visual-basic/language-reference/statements/enum-statement.md))|Jeho základní integrálního typu a libovolný typ, ke kterému základní typ rozšiřuje.|  
|[Char](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`Char`, `String`|  
|`Char` Pole|`Char` pole, `String`|  
|Jakýkoli typ|[objekt](../../../../visual-basic/language-reference/data-types/object-data-type.md)|  
|Žádné odvozený typ|Některé základní typ, ze kterého je odvozen <sup>3</sup>.|  
|Jakýkoli typ|Každé rozhraní, který jej implementuje.|  
|[Nothing](../../../../visual-basic/language-reference/nothing.md)|Datový typ nebo typ objektu.|  
  
 <sup>1</sup> podle definice každý datový typ rozšiřuje na sebe sama.  
  
 <sup>2</sup> převody z `Integer`, `UInteger`, `Long`, `ULong`, nebo `Decimal` k `Single` nebo `Double` může způsobit ztrátu přesnosti, ale nikdy ztrátu velikost. V tomto smyslu jejich nejsou spojené ztráty informací.  
  
 <sup>3</sup> může zdát překvapivé, že je rozšiřující převod z odvozeného typu na některém z jeho základních typů. Odůvodnění je, že odvozený typ obsahuje všechny členy základního typu, takže se považují za instanci základního typu. V opačném směru základní typ neobsahuje žádné nové členy definované odvozeného typu.  
  
 Rozšiřující převody proběhnout úspěšně, v době spuštění a nikdy ztrátě dat se vám účtovat. Je implicitně vždy provést, ať už [Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md) nastaví typ kontroly přepínač tak, aby `On` nebo `Off`.  
  
## <a name="narrowing-conversions"></a>Zužující převody  
 Standardní zužující převody zahrnují následující:  
  
- Reverzní pokynů rozšiřující převody v předchozí tabulky (s tím rozdílem, že každý typ rozšiřuje na sebe sama)  
  
- Převody v obou směrech mezi [logická](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) a jakýkoli číselný typ  
  
- Převody z libovolného číselného typu k libovolnému Výčtový typ (`Enum`)  
  
- Převody v obou směrech mezi [řetězec](../../../../visual-basic/language-reference/data-types/string-data-type.md) a libovolného číselného typu `Boolean`, nebo [datum](../../../../visual-basic/language-reference/data-types/date-data-type.md)  
  
- Převody z datového typu nebo objekt typu na typ odvozený z ní  
  
 Zužující převody nejsou vždy v době spuštění úspěšné a může selhat nebo ztrátě dat se vám účtovat. Pokud cílový datový typ nemůže přijímat převáděná hodnota dojde k chybě. Například převod čísla může způsobit přetečení. Kompilátor neumožňuje provést zužující převody implicitně, není-li [Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md) nastaví typ kontroly přepínač tak, aby `Off`.  
  
> [!NOTE]
>  Chyba zúžit převodu je potlačeno pro převod z prvků v `For Each…Next` kolekce řídicí proměnná smyčky for. Další informace a příklady najdete v tématu v části "Zužující převody" [For Each... Další příkaz](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
### <a name="when-to-use-narrowing-conversions"></a>Kdy použít Zužujících převodů  
 Zužující převod používají, když víte, že zdrojové hodnoty lze převést na cílový datový typ bez chyb nebo ztrátu. Pokud máte například `String` znát obsahuje "True" nebo "False", můžete použít `CBool` – klíčové slovo lze převést na `Boolean`.  
  
## <a name="exceptions-during-conversion"></a>Výjimky při převodu  
 Protože rozšiřující převody vždy úspěšné, nevyvolají výjimky. Zužující převody, když selžou, nejčastěji vyvolání následující výjimky:  
  
- <xref:System.InvalidCastException> – Pokud není definován žádný převod mezi těmito dvěma typy  
  
- <xref:System.OverflowException> – (pouze integrálovými typy) Pokud převedená hodnota je příliš velký pro cílový typ  
  
 Pokud třída nebo struktura, definuje [CType – funkce](../../../../visual-basic/language-reference/functions/ctype-function.md) sloužit jako operátor převodu na nebo z této třídě nebo struktuře, který `CType` lze vyvolat jakoukoli výjimku považuje za vhodné. Kromě toho, který `CType` může volat funkce jazyka Visual Basic nebo metody rozhraní .NET Framework, které pak může vyvolat různé výjimky.  
  
## <a name="changes-during-reference-type-conversions"></a>Změny během převody typů odkazů  
 Převod z *odkazovat na typ* zkopíruje pouze ukazatel na hodnotu. Samotná hodnota není zkopírován ani změnit žádným způsobem. Jediné, co, která může měnit je datový typ proměnné, která uchovává ukazatel. V následujícím příkladu je datový typ převést z odvozené třídy se svou základní třídou, ale objekt, který je nyní přejděte obě proměnné se nezmění.  
  
```  
' Assume class cSquare inherits from class cShape.  
Dim shape As cShape  
Dim square As cSquare = New cSquare  
' The following statement performs a widening  
' conversion from a derived class to its base class.  
shape = square  
```  
  
## <a name="see-also"></a>Viz také:

- [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Převody typů v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Implicitní a explicitní převody](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Převody mezi řetězci a ostatními typy](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [Postupy: Převést objekt na jiný typ v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [Převody polí](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [Datové typy](../../../../visual-basic/language-reference/data-types/index.md)
- [Funkce pro převod typů](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
