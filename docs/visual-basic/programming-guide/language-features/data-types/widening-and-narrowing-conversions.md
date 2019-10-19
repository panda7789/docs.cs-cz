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
ms.openlocfilehash: d1822afc4b10a725e13c1469a068c30813d3a2d3
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582739"
---
# <a name="widening-and-narrowing-conversions-visual-basic"></a>Rozšíření a zúžení převodů (Visual Basic)
Důležitým aspektem převodu typu je, zda je výsledek převodu v rozsahu cílového datového typu.  
  
 *Rozšiřující převod* mění hodnotu na datový typ, který může umožňovat jakoukoli možnou hodnotu původních dat.  Rozšiřující převody zachovávají zdrojovou hodnotu, ale mohou změnit její reprezentace. K tomu dochází, pokud převedete z integrálního typu na `Decimal` nebo z `Char` na `String`.  
  
 *Zužující převod* mění hodnotu na datový typ, který nemusí být schopný uchovat některé z možných hodnot. Například desetinná hodnota je zaokrouhlena při převodu na celočíselný typ a číselný typ převedený na `Boolean` je snížen buď na `True` nebo `False`.  
  
## <a name="widening-conversions"></a>Rozšiřující převody  
 V následující tabulce jsou uvedeny standardní rozšiřující převody.  
  
|Datový typ|Rozšíří na datové typy <sup>1</sup> .|  
|---|---|  
|[SByte](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[Bytové](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Dostatečná](../../../../visual-basic/language-reference/data-types/short-data-type.md)|`Short`, `Integer`, `Long`, `Decimal`, `Single` `Double`|  
|[UShort](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Čísla](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[UInteger –](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Dlouhou](../../../../visual-basic/language-reference/data-types/long-data-type.md)|`Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[ULong](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|`ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Notaci](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Konkrétní](../../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single` `Double`|  
|[Klepat](../../../../visual-basic/language-reference/data-types/double-data-type.md)|`Double`|  
|Libovolný Výčtový typ ([Enum](../../../../visual-basic/language-reference/statements/enum-statement.md))|Svůj základní celočíselný typ a jakýkoliv typ, na který se rozšíří základní typ.|  
|[Char](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`Char` `String`|  
|`Char` pole|pole `Char`, `String`|  
|Libovolný typ|[Předmětů](../../../../visual-basic/language-reference/data-types/object-data-type.md)|  
|Libovolný odvozený typ|Jakýkoli základní typ, ze kterého je odvozen <sup>3</sup>.|  
|Libovolný typ|Jakékoli rozhraní, které implementuje.|  
|[Nothing](../../../../visual-basic/language-reference/nothing.md)|Libovolný datový typ nebo typ objektu.|  
  
 <sup>1</sup> podle definice se každý datový typ rozšiřuje na sebe sama.  
  
 <sup>2</sup> převody z `Integer`, `UInteger`, `Long`, `ULong` nebo `Decimal` na `Single` nebo `Double` mohou způsobit ztrátu přesnosti, ale nikdy nemusejí mít za následek ztrátu velikosti. V tomto smyslu se neúčtují ztráty informací.  
  
 <sup>3</sup> může se zdát, že překvapivé převod z odvozeného typu na jeden z jeho základních typů rozšiřuje. Odůvodnění je, že odvozený typ obsahuje všechny členy základního typu, takže je jako instance základního typu. V opačném směru základní typ neobsahuje žádné nové členy definované odvozeným typem.  
  
 Rozšiřující převody jsou vždy úspěšné v době běhu a nikdy neúčtují ztrátu dat. Můžete je vždy provést implicitně, bez ohledu na to, zda [příkaz Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) nastaví přepínač typu na `On` nebo na `Off`.  
  
## <a name="narrowing-conversions"></a>Zužující převody  
 Standardní zužující převody zahrnují následující:  
  
- Zpětné směry rozšiřujících převodů v předchozí tabulce (s výjimkou toho, že každý typ se rozšiřuje sám na sebe)  
  
- Převody v obou směrech mezi [logickou](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) a jakýmkoli číselným typem  
  
- Převody z libovolného číselného typu na libovolný Výčtový typ (`Enum`)  
  
- Převody v obou směrech mezi [řetězcem](../../../../visual-basic/language-reference/data-types/string-data-type.md) a jakýmkoli číselným typem, `Boolean` nebo [Date](../../../../visual-basic/language-reference/data-types/date-data-type.md)  
  
- Převody z datového typu nebo typu objektu na typ odvozený od něj  
  
 Zužující převody nejsou vždycky úspěšné v době běhu a můžou selhat nebo může dojít ke ztrátě dat. Pokud cílový datový typ nemůže přijmout převáděnou hodnotu, dojde k chybě. Například číselný převod může mít za následek přetečení. Kompilátor neumožňuje provádět zužující převody implicitně, pokud [příkaz Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) nenastaví přepínač typu na `Off`.  
  
> [!NOTE]
> Chyba zužujícího převodu je potlačena pro převody z prvků v kolekci `For Each…Next` na proměnnou ovládacího prvku smyčky. Další informace a příklady najdete v části "zužující převody" v tématu.. [. Další příkaz](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
### <a name="when-to-use-narrowing-conversions"></a>Kdy použít zužující převody  
 Zužující převod se používá, pokud víte, že zdrojová hodnota může být převedena na cílový datový typ bez chyby nebo ztráty dat. Pokud máte například `String`, že víte, že je "true" nebo "false", můžete použít klíčové slovo `CBool` k jeho převedení na `Boolean`.  
  
## <a name="exceptions-during-conversion"></a>Výjimky při převodu  
 Vzhledem k tomu, že rozšiřující převody jsou vždy úspěšné, nevyvolají výjimky. Zužující převody, pokud selžou, nejčastěji vyvolávají následující výjimky:  
  
- <xref:System.InvalidCastException> – Pokud mezi těmito dvěma typy není definovaný žádný převod  
  
- <xref:System.OverflowException> – (pouze integrální typy), pokud je převedená hodnota pro cílový typ příliš velká  
  
 Definuje-li třída nebo struktura [funkci CType](../../../../visual-basic/language-reference/functions/ctype-function.md) , která bude sloužit jako operátor převodu na nebo z dané třídy nebo struktury, může `CType` vyvolat jakoukoli výjimku, kterou považuje za vhodné. Kromě toho může `CType` volat funkce Visual Basic nebo .NET Framework metody, které zase mohou vyvolat různé výjimky.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Převody typu v Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Implicitní a explicitní převody](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Převody mezi řetězci a ostatními typy](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [Postupy: převod objektu na jiný typ v Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [Převody polí](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [Datové typy](../../../../visual-basic/language-reference/data-types/index.md)
- [Funkce pro převod typů](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
