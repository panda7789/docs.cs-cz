---
title: Rozšíření a zúžení převodů
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
ms.openlocfilehash: 177ff6c6fe15c57563d2f62ed8927f9ee975be48
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392997"
---
# <a name="widening-and-narrowing-conversions-visual-basic"></a>Rozšíření a zúžení převodů (Visual Basic)
Důležitým aspektem převodu typu je, zda je výsledek převodu v rozsahu cílového datového typu.  
  
 *Rozšiřující převod* mění hodnotu na datový typ, který může umožňovat jakoukoli možnou hodnotu původních dat.  Rozšiřující převody zachovávají zdrojovou hodnotu, ale mohou změnit její reprezentace. K tomu dochází, pokud převedete z integrálního typu na `Decimal` nebo z `Char` na `String` .  
  
 *Zužující převod* mění hodnotu na datový typ, který nemusí být schopný uchovat některé z možných hodnot. Například desetinná hodnota je zaokrouhlena při převodu na celočíselný typ a číselný typ, na který je převeden na, `Boolean` je snížen na hodnotu `True` nebo `False` .  
  
## <a name="widening-conversions"></a>Rozšiřující převody  
 V následující tabulce jsou uvedeny standardní rozšiřující převody.  
  
|Datový typ|Rozšíří na datové typy <sup>1</sup> .|  
|---|---|  
|[SByte](../../../language-reference/data-types/sbyte-data-type.md)|`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[Bytové](../../../language-reference/data-types/byte-data-type.md)|`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Dostatečná](../../../language-reference/data-types/short-data-type.md)|`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[UShort](../../../language-reference/data-types/ushort-data-type.md)|`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Integer](../../../language-reference/data-types/integer-data-type.md)|`Integer`, `Long` , `Decimal` , `Single` , `Double` <sup>2</sup>|  
|[UInteger –](../../../language-reference/data-types/uinteger-data-type.md)|`UInteger`, `Long` , `ULong` , `Decimal` , `Single` , `Double` <sup>2</sup>|  
|[Dlouhou](../../../language-reference/data-types/long-data-type.md)|`Long`, `Decimal` , `Single` , `Double` <sup>2</sup>|  
|[ULong](../../../language-reference/data-types/ulong-data-type.md)|`ULong`, `Decimal` , `Single` , `Double` <sup>2</sup>|  
|[Notaci](../../../language-reference/data-types/decimal-data-type.md)|`Decimal`, `Single` , `Double` <sup>2</sup>|  
|[Single](../../../language-reference/data-types/single-data-type.md)|`Single`, `Double`|  
|[Klepat](../../../language-reference/data-types/double-data-type.md)|`Double`|  
|Libovolný Výčtový typ ([Enum](../../../language-reference/statements/enum-statement.md))|Svůj základní celočíselný typ a jakýkoliv typ, na který se rozšíří základní typ.|  
|[Char](../../../language-reference/data-types/char-data-type.md)|`Char`, `String`|  
|`Char`skupin|`Char`skupin`String`|  
|Libovolný typ|[Předmětů](../../../language-reference/data-types/object-data-type.md)|  
|Libovolný odvozený typ|Jakýkoli základní typ, ze kterého je odvozen <sup>3</sup>.|  
|Libovolný typ|Jakékoli rozhraní, které implementuje.|  
|[Nothing](../../../language-reference/nothing.md)|Libovolný datový typ nebo typ objektu.|  
  
 <sup>1</sup> podle definice se každý datový typ rozšiřuje na sebe sama.  
  
 <sup>2</sup> převody z `Integer` , `UInteger` , `Long` , `ULong` nebo `Decimal` na `Single` nebo `Double` by mohly vést ke ztrátám přesnosti, ale nikdy nemusejí mít za následek ztrátu velikosti. V tomto smyslu se neúčtují ztráty informací.  
  
 <sup>3</sup> může se zdát, že překvapivé převod z odvozeného typu na jeden z jeho základních typů rozšiřuje. Odůvodnění je, že odvozený typ obsahuje všechny členy základního typu, takže je jako instance základního typu. V opačném směru základní typ neobsahuje žádné nové členy definované odvozeným typem.  
  
 Rozšiřující převody jsou vždy úspěšné v době běhu a nikdy neúčtují ztrátu dat. Můžete je vždy provádět implicitně, bez ohledu na to, zda [příkaz Option Strict](../../../language-reference/statements/option-strict-statement.md) nastaví přepínač typu na `On` nebo na `Off` .  
  
## <a name="narrowing-conversions"></a>Zužující převody  
 Standardní zužující převody zahrnují následující:  
  
- Zpětné směry rozšiřujících převodů v předchozí tabulce (s výjimkou toho, že každý typ se rozšiřuje sám na sebe)  
  
- Převody v obou směrech mezi [logickou](../../../language-reference/data-types/boolean-data-type.md) a jakýmkoli číselným typem  
  
- Převody z libovolného číselného typu na libovolný Výčtový typ ( `Enum` )  
  
- Převody v obou směrech mezi [řetězcem](../../../language-reference/data-types/string-data-type.md) a jakýmkoli číselným typem, `Boolean` nebo [Datum](../../../language-reference/data-types/date-data-type.md)  
  
- Převody z datového typu nebo typu objektu na typ odvozený od něj  
  
 Zužující převody nejsou vždycky úspěšné v době běhu a můžou selhat nebo může dojít ke ztrátě dat. Pokud cílový datový typ nemůže přijmout převáděnou hodnotu, dojde k chybě. Například číselný převod může mít za následek přetečení. Kompilátor neumožňuje provádět zužující převody implicitně, pokud [příkaz Option Strict](../../../language-reference/statements/option-strict-statement.md) nenastaví přepínač typu na `Off` .  
  
> [!NOTE]
> Chyba zužujícího převodu je potlačena pro převody z prvků v `For Each…Next` kolekci na řídicí proměnnou smyčky. Další informace a příklady najdete v části "zužující převody" v tématu.. [. Další příkaz](../../../language-reference/statements/for-each-next-statement.md).  
  
### <a name="when-to-use-narrowing-conversions"></a>Kdy použít zužující převody  
 Zužující převod se používá, pokud víte, že zdrojová hodnota může být převedena na cílový datový typ bez chyby nebo ztráty dat. Pokud máte například `String` , že víte, že obsahuje hodnotu "true" nebo "false", můžete použít `CBool` klíčové slovo k převedení na `Boolean` .  
  
## <a name="exceptions-during-conversion"></a>Výjimky při převodu  
 Vzhledem k tomu, že rozšiřující převody jsou vždy úspěšné, nevyvolají výjimky. Zužující převody, pokud selžou, nejčastěji vyvolávají následující výjimky:  
  
- <xref:System.InvalidCastException>– Pokud mezi těmito dvěma typy není definovaný žádný převod  
  
- <xref:System.OverflowException>– (jenom celočíselné typy), pokud je převedená hodnota pro cílový typ moc velká.  
  
 Pokud třída nebo struktura definuje [funkci CType](../../../language-reference/functions/ctype-function.md) , která bude sloužit jako operátor převodu na nebo z dané třídy nebo struktury, která `CType` může vyvolat jakoukoli výjimku, kterou považuje za vhodnou. Kromě toho `CType` může volat funkce Visual Basic nebo .NET Framework metody, které zase mohou vyvolat různé výjimky.  
  
## <a name="changes-during-reference-type-conversions"></a>Změny během převodů typu reference  
 Převod z *typu odkazu* kopíruje pouze ukazatel na hodnotu. Samotná hodnota není ani zkopírována ani měněna žádným způsobem. Jediná věc, kterou lze změnit, je datový typ proměnné obsahující ukazatel. V následujícím příkladu je datový typ převeden z odvozené třídy na svou základní třídu, ale objekt, na který obě proměnné nyní odkazuje, zůstane beze změny.  
  
```vb  
' Assume class cSquare inherits from class cShape.  
Dim shape As cShape  
Dim square As cSquare = New cSquare  
' The following statement performs a widening  
' conversion from a derived class to its base class.  
shape = square  
```  
  
## <a name="see-also"></a>Viz také

- [Datové typy](index.md)
- [Převody typů v jazyce Visual Basic](type-conversions.md)
- [Implicitní a explicitní převody](implicit-and-explicit-conversions.md)
- [Převody mezi řetězci a ostatními typy](conversions-between-strings-and-other-types.md)
- [Postupy: Převedení objektu na jiný typ v jazyce Visual Basic](how-to-convert-an-object-to-another-type.md)
- [Převody polí](array-conversions.md)
- [Datové typy](../../../language-reference/data-types/index.md)
- [Funkce pro převod typů](../../../language-reference/functions/type-conversion-functions.md)
