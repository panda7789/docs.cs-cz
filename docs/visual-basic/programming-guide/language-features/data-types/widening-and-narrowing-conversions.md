---
title: "Rozšíření a zúžení převodů (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2cf1f8d956935a9a363211abf94b4f1c2f538074
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="widening-and-narrowing-conversions-visual-basic"></a>Rozšíření a zúžení převodů (Visual Basic)
Důležitý aspekt s převod typu je, zda výsledek převodu je v rozsahu cílového datového typu.  
  
 A *rozšiřující převod* změní hodnotu na datový typ, který můžete povolit pro všechny možné hodnotu původní data.  Rozšiřující převody zachovat zdrojové hodnoty, ale můžete změnit její reprezentace. K tomu dojde, pokud převedete z celočíselných typů na `Decimal`, nebo z `Char` k `String`.  
  
 A *zužující převod* změní hodnotu na datový typ, který nemusí obsahovat některé z možných hodnot. Například se zaokrouhlí desetinnou hodnotu, pokud je převést na typ integrální a číselného typu převáděn na `Boolean` zkrátila buď `True` nebo `False`.  
  
## <a name="widening-conversions"></a>Rozšiřující převody  
 V následující tabulce jsou standardní rozšiřující převody.  
  
|Datový typ|Rozšiřuje na datové typy <sup>1</sup>|  
|---|---|  
|[SByte –](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[Bajtů](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Krátký](../../../../visual-basic/language-reference/data-types/short-data-type.md)|`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[Ushort –](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Celé číslo](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Uinteger –](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Dlouhá](../../../../visual-basic/language-reference/data-types/long-data-type.md)|`Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Ulong –](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|`ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Decimal](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Jeden](../../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`, `Double`|  
|[Double](../../../../visual-basic/language-reference/data-types/double-data-type.md)|`Double`|  
|Žádné výčtového typu ([výčtu](../../../../visual-basic/language-reference/statements/enum-statement.md))|Jeho zdrojovým typem integrální a žádný typ, do které rozšiřuje základní typ.|  
|[Char –](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`Char`, `String`|  
|`Char`pole|`Char`pole,`String`|  
|Jakýkoli typ|[Objekt](../../../../visual-basic/language-reference/data-types/object-data-type.md)|  
|Všechny odvozený typ|Některé základní typ, ze kterého je odvozený <sup>3</sup>.|  
|Jakýkoli typ|Všechny rozhraní, které implementuje.|  
|[Nic](../../../../visual-basic/language-reference/nothing.md)|Datový typ nebo typ objektu.|  
  
 <sup>1</sup> podle definice, každý typ dat rozšiřuje na sebe sama.  
  
 <sup>2</sup> převody z `Integer`, `UInteger`, `Long`, `ULong`, nebo `Decimal` k `Single` nebo `Double` může způsobit ztrátu přesnosti, ale nikdy ztrátu rozsahem. V tomto smyslu jejich není dojít ke ztrátě informací.  
  
 <sup>3</sup> se může zdát, že se vám překvapivé, že je rozšiřující převod z odvozený typ na jednu z jeho základních typů. Odůvodnění je, že odvozený typ obsahuje všechny členy základní typ, takže se považují za instance základního typu. V opačném směru je základní typ neobsahuje žádné nové členy definované v odvozeném typu.  
  
 Rozšiřující převody proběhnout úspěšně v době běhu a nikdy dojít ke ztrátě dat. Je implicitně vždy provést, ať už [Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md) nastaví typ kontroly přepínač tak, aby `On` nebo `Off`.  
  
## <a name="narrowing-conversions"></a>Zužující převody  
 Standardní zužující převody zahrnují následující:  
  
-   Zpětné směrech rozšiřující převody v předchozím tabulky (kromě toho, že každý typ rozšiřuje na sebe sama)  
  
-   Převody v obou směrech mezi [Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) a všechny číselný typ.  
  
-   Převody z libovolného číselného typu žádnému výčtového typu (`Enum`)  
  
-   Převody v obou směrech mezi [řetězec](../../../../visual-basic/language-reference/data-types/string-data-type.md) a číselného typu, `Boolean`, nebo [datum](../../../../visual-basic/language-reference/data-types/date-data-type.md)  
  
-   Převody z datový typ nebo objekt typ typu odvozeného z něj  
  
 Zužující převody není vždy úspěch v době běhu a může selhat nebo dojít ke ztrátě dat. Pokud cílový datový typ nelze získat hodnotu převáděné dojde k chybě. Například můžete číselný převod způsobilo přetečení. Kompilátor neumožňuje provádět zužující převody implicitně, pokud [Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md) nastaví typ kontroly přepínač tak, aby `Off`.  
  
> [!NOTE]
>  Chyba zužující převod je potlačen pro převody z elementů v `For Each…Next` kolekce řídicí proměnná smyčky. Další informace a příklady naleznete v části "Zužující převody" v [For Each... Další příkaz](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
### <a name="when-to-use-narrowing-conversions"></a>Kdy použít zužující převody  
 Zužující převod používají, když víte, že zdrojové hodnoty lze převést na datový typ cílového bez ztráty chyby nebo data. Pokud máte například `String` , abyste věděli, obsahuje hodnotu "True" nebo "Nepravda", můžete použít `CBool` – klíčové slovo převést jej do `Boolean`.  
  
## <a name="exceptions-during-conversion"></a>Výjimky při převodu  
 Rozšiřující převody vždy úspěšné, a proto se nevyvolá výjimku výjimky. Zužující převody, pokud se nezdaří, nejčastěji throw následující výjimky:  
  
-   <xref:System.InvalidCastException>– Pokud je mezi těmito dvěma typy definovaný žádný převod  
  
-   <xref:System.OverflowException>– (jenom integrální typy) Pokud převedená hodnota je příliš velký pro cílový typ  
  
 Pokud definuje třídu nebo strukturu [CType – funkce](../../../../visual-basic/language-reference/functions/ctype-function.md) sloužit jako operátor převodu do nebo z třídy nebo struktura, která `CType` můžete vyvolat všechny výjimky považuje za vhodné. Kromě toho, který `CType` může volat [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] funkce nebo [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] metody, které pak může vyvolat různé výjimky.  
  
## <a name="changes-during-reference-type-conversions"></a>Změny během převody typu odkazu  
 Převod z *odkazují na typ* zkopíruje jenom ukazatel na hodnotu. Vlastní hodnota nebudou zkopírovány ani změnit žádným způsobem. Jediné, co můžete změnit je datový typ proměnné, která uchovává ukazatele. V následujícím příkladu je datový typ převést z odvozené třídy na její základní třída, ale objekt, který teď přejděte obě proměnné je beze změny.  
  
```  
' Assume class cSquare inherits from class cShape.  
Dim shape As cShape  
Dim square As cSquare = New cSquare  
' The following statement performs a widening  
' conversion from a derived class to its base class.  
shape = square  
```  
  
## <a name="see-also"></a>Viz také  
 [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Převody typů v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Implicitní a explicitní převody](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Převody mezi řetězci a ostatními typy](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [Postupy: převedení objektu na jiný typ v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [Převody pole](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [Datové typy](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funkce pro převod typů](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
