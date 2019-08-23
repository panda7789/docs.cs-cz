---
title: + – Operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.+
helpviewer_keywords:
- arithmetic operators [Visual Basic], addition
- + operator
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
- sum operator [Visual Basic]
ms.assetid: 5694778f-0a2c-4539-8009-f66f318fb46d
ms.openlocfilehash: ab18a7137a31ed8e616f465e7d617305c96d7b10
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943027"
---
# <a name="-operator-visual-basic"></a>+ – operátor (Visual Basic)
Přidá dvě čísla nebo vrátí kladnou hodnotu číselného výrazu. Lze také použít ke zřetězení dvou řetězcových výrazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb
expression1 + expression2  
- or -  
+ expression1  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`expression1`|Povinný parametr. Libovolný numerický nebo řetězcový výraz.|  
|`expression2`|Povinné, pokud `+` operátor nevypočítá zápornou hodnotu. Libovolný numerický nebo řetězcový výraz.|  
  
## <a name="result"></a>Výsledek  
 Pokud `expression1` a`expression2` jsou oba číselné, výsledek je aritmetický součet.  
  
 Pokud `expression2` chybí`+` , operátor je *unární* operátor identity pro nezměněnou hodnotu výrazu. V tomto smyslu se operace skládá z zachování znaménka `expression1`, takže výsledek je záporný, pokud `expression1` je záporná.  
  
 Pokud `expression1` a`expression2` jsou oba řetězce, je výsledkem zřetězení jejich hodnot.  
  
 V případě `expression1` smíšených typů závisí akce prováděná na jejich typech, jejich obsahu a nastavení [příkazu Option Strict.](../../../visual-basic/language-reference/statements/option-strict-statement.md) `expression2` Další informace najdete v tabulkách v části "poznámky".  
  
## <a name="supported-types"></a>Podporované typy  
 Všechny číselné typy, včetně typů unsigned a float-Point a `Decimal`a. `String`  
  
## <a name="remarks"></a>Poznámky  
 Obecně `+` provádí aritmetické sčítání, pokud je to možné, a zřetězení pouze v případě, že oba výrazy jsou řetězce.  
  
 Pokud žádný výraz není `Object`, Visual Basic provede následující akce.  
  
|Datové typy výrazů|Akce podle kompilátoru|  
|---|---|  
|Oba výrazy jsou číselné datové typy (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, ,`Decimal` ,nebo`Double`). `Single`|Přidávání. Výsledný datový typ je číselný typ odpovídající datovým typům `expression1` a. `expression2` Podívejte se na tabulky "celočíselné aritmetické" v [datových typech výsledků operátoru](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).|  
|Oba výrazy jsou typu`String`|Zřetězit.|  
|Jeden výraz je číselný datový typ a druhý je řetězec.|Pokud `Option Strict` je`On`, vygenerujte chybu kompilátoru.<br /><br /> Pokud `Option Strict` je `Off`, `Double`pakimplicitně převeďte naapřidat.`String`<br /><br /> Pokud nelze převést na, vyvolejte <xref:System.InvalidCastException>výjimku. `Double` `String`|  
|Jeden výraz je numerický datový typ a druhý není [nic](../../../visual-basic/language-reference/nothing.md)|Přidejte s `Nothing` hodnotou nula.|  
|Jeden výraz je řetězec a druhý je`Nothing`|CONCATENATE s `Nothing` hodnotou "".|  
  
 Pokud je `Object` jedním výrazem výraz, Visual Basic provede následující akce.  
  
|Datové typy výrazů|Akce podle kompilátoru|  
|---|---|  
|`Object`výraz obsahuje číselnou hodnotu a druhý je číselný datový typ.|Pokud `Option Strict` je`On`, vygenerujte chybu kompilátoru.<br /><br /> Pokud `Option Strict` je`Off`, přidejte.|  
|`Object`výraz obsahuje číselnou hodnotu a druhý je typu.`String`|Pokud `Option Strict` je`On`, vygenerujte chybu kompilátoru.<br /><br /> Pokud `Option Strict` je `Off`, `Double`pakimplicitně převeďte naapřidat.`String`<br /><br /> Pokud nelze převést na, vyvolejte <xref:System.InvalidCastException>výjimku. `Double` `String`|  
|`Object`výraz obsahuje řetězec a druhý je číselný datový typ.|Pokud `Option Strict` je`On`, vygenerujte chybu kompilátoru.<br /><br /> Pokud `Option Strict` `Object` `Double` je `Off`, pak implicitně převeďte řetězec na a přidat.<br /><br /> Pokud řetězec `Object` nelze převést na `Double`, vyvolejte <xref:System.InvalidCastException> výjimku.|  
|`Object`výraz obsahuje řetězec a druhý je typu`String`|Pokud `Option Strict` je`On`, vygenerujte chybu kompilátoru.<br /><br /> Pokud `Option Strict` `Object` `String` je `Off`, pak implicitní převod na a zřetězení.|  
  
 Pokud jsou `Object` oba výrazy výrazy, Visual Basic provádí následující akce (`Option Strict Off` pouze).  
  
|Datové typy výrazů|Akce podle kompilátoru|  
|---|---|  
|Oba `Object` výrazy uchovávají číselné hodnoty|Přidávání.|  
|Oba `Object` výrazy jsou typu`String`|Zřetězit.|  
|Jeden `Object` výraz obsahuje číselnou hodnotu a druhý obsahuje řetězec.|Implicitně převeďte řetězec `Object` na `Double` a přidat.<br /><br /> Pokud řetězec `Object` nelze převést na číselnou hodnotu, <xref:System.InvalidCastException> vyvolejte výjimku.|  
  
 Pokud se `Object` některý výraz vyhodnotí jako <xref:System.DBNull> [Nothing](../../../visual-basic/language-reference/nothing.md) nebo `+` , operátor ho považuje za `String` s hodnotou "".  
  
> [!NOTE]
> Při použití `+` operátoru nemusí být možné určit, zda dojde k přidání nebo zřetězení řetězců. `&` Použijte operátor pro zřetězení k eliminaci nejednoznačnosti a k poskytnutí kódu pro samoobslužné dokumenty.  
  
## <a name="overloading"></a>Přetížení  
 Operátor může být přetížen, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury. `+` Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `+` operátor pro přidání čísel. Pokud jsou operandy číselné, Visual Basic vypočítá aritmetický výsledek. Aritmetický výsledek představuje součet dvou operandů.  
  
 [!code-vb[VbVbalrOperators#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#6)]  
  
 `+` Operátor můžete také použít k zřetězení řetězců. Pokud jsou operandy řetězcem, Visual Basic je zřetězí. Výsledek zřetězení představuje jeden řetězec skládající se z obsahu dvou operandů jednoho po druhém.  
  
 Pokud jsou operandy smíšeného typu, výsledek závisí na nastavení [příkazu Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md). Následující příklad ilustruje výsledek, pokud `Option Strict` je `On`.  
  
 [!code-vb[VbVbalrOperators#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class3.vb#53)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#51)]  
  
 Následující příklad ilustruje výsledek, pokud `Option Strict` je `Off`.  
  
 [!code-vb[VbVbalrOperators#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#54)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#52)]  
  
 Chcete-li eliminovat nejednoznačnost, `&` použijte `+` místo pro zřetězení operátor.  
  
## <a name="see-also"></a>Viz také:

- [& – operátor](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [Operátory zřetězení](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Aritmetické operátory v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
