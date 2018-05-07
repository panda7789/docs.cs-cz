---
title: + Operátor (Visual Basic)
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
ms.openlocfilehash: ccf79c700cf852c0febb9c3f3464cbacdd39296e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-visual-basic"></a>+ – operátor (Visual Basic)
Sečte dvě čísla nebo vrátí kladnou hodnotu číselného výrazu. Můžete také použít ke zřetězení dvou výrazů řetězec.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
      expression1 + expression2  
- or -  
+ expression1  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`expression1`|Požadováno. Číselný nebo řetězec výraz.|  
|`expression2`|Vyžaduje, pokud `+` operátor je výpočet zápornou hodnotu. Číselný nebo řetězec výraz.|  
  
## <a name="result"></a>Výsledek  
 Pokud `expression1` a `expression2` jsou obě číselné, výsledkem je jejich aritmetické součet.  
  
 Pokud `expression2` chybí, `+` operátor je *unární* operátor identity pro beze změny hodnotu výrazu. V tomto smyslu operaci se skládá z ponechá znaménko `expression1`, takže výsledek je záporný, pokud `expression1` záporné.  
  
 Pokud `expression1` a `expression2` jsou oba řetězce, výsledkem je zřetězení jejich hodnot.  
  
 Pokud `expression1` a `expression2` jsou smíšené typů akci prováděnou závisí na jejich typy, jejich obsah a nastavení [Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md). Další informace najdete v tématu tabulky v "Poznámky."  
  
## <a name="supported-types"></a>Podporované typy  
 Všechny číselné typy, včetně typy bez znaménka a s plovoucí desetinnou čárkou a `Decimal`, a `String`.  
  
## <a name="remarks"></a>Poznámky  
 Obecně platí `+` provede aritmetické přidání, pokud je to možné a zřetězí, pouze pokud jsou oba výrazy řetězce.  
  
 Pokud ani výraz `Object`, Visual Basic provede následující akce.  
  
|Datové typy výrazů|Akce kompilátorem|  
|---|---|  
|Číselné datové typy jsou oba výrazy (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, nebo `Double`)|Přidáte. Datový typ výsledků je vhodné pro datové typy číselného typu `expression1` a `expression2`. Podívejte se na tabulky "Celočíselné aritmetiky" v [typy výsledků operátoru Data](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).|  
|Jsou oba výrazy typu `String`|Zřetězení.|  
|Jeden výraz je číselný datový typ a druhá je řetězec|Pokud `Option Strict` je `On`, pak vygenerována chyba kompilátoru.<br /><br /> Pokud `Option Strict` je `Off`, pak implicitně převést `String` k `Double` a přidejte.<br /><br /> Pokud `String` nelze převést na `Double`, pak throw <xref:System.InvalidCastException> výjimka.|  
|Jeden výraz je číselný datový typ, a druhá je [nic](../../../visual-basic/language-reference/nothing.md)|Přidat, s `Nothing` s hodnotou nula.|  
|Jeden výraz je řetězec, a druhá je `Nothing`|Zřetězení s `Nothing` cenná jako "".|  
  
 Pokud je jeden výraz `Object` výrazu jazyka Visual Basic provede následující akce.  
  
|Datové typy výrazů|Akce kompilátorem|  
|---|---|  
|`Object` výraz obsahuje číselnou hodnotu a druhá je číselný datový typ.|Pokud `Option Strict` je `On`, pak vygenerována chyba kompilátoru.<br /><br /> Pokud `Option Strict` je `Off`, pak přidat.|  
|`Object` výraz obsahuje číselnou hodnotu a druhá je typu `String`|Pokud `Option Strict` je `On`, pak vygenerována chyba kompilátoru.<br /><br /> Pokud `Option Strict` je `Off`, pak implicitně převést `String` k `Double` a přidejte.<br /><br /> Pokud `String` nelze převést na `Double`, pak throw <xref:System.InvalidCastException> výjimka.|  
|`Object` výraz obsahuje řetězec a druhá je číselný datový typ.|Pokud `Option Strict` je `On`, pak vygenerována chyba kompilátoru.<br /><br /> Pokud `Option Strict` je `Off`, implicitně převést řetězec `Object` k `Double` a přidejte.<br /><br /> Pokud řetězec `Object` nelze převést na `Double`, pak throw <xref:System.InvalidCastException> výjimka.|  
|`Object` výraz obsahuje řetězec a druhá je typu `String`|Pokud `Option Strict` je `On`, pak vygenerována chyba kompilátoru.<br /><br /> Pokud `Option Strict` je `Off`, pak implicitně převést `Object` k `String` a zřetězení.|  
  
 Pokud jsou oba výrazy `Object` výrazy jazyka Visual Basic provede následující akce (`Option Strict Off` pouze).  
  
|Datové typy výrazů|Akce kompilátorem|  
|---|---|  
|Obě `Object` výrazy uložení číselné hodnoty.|Přidáte.|  
|Obě `Object` výrazy jsou typu `String`|Zřetězení.|  
|Jeden `Object` výraz obsahuje číselnou hodnotu a dalších obsahuje řetězec|Implicitně převést řetězec `Object` k `Double` a přidejte.<br /><br /> Pokud řetězec `Object` nelze převést na číselnou hodnotu, pak throw <xref:System.InvalidCastException> výjimka.|  
  
 Pokud má jedna `Object` výraz vyhodnocen jako [nic](../../../visual-basic/language-reference/nothing.md) nebo <xref:System.DBNull>, `+` operátor považuje za `String` s hodnotou "".  
  
> [!NOTE]
>  Při použití `+` operátor, nemusí být schopní určit, zda dojde k přidání nebo řetězec zřetězení. Použití `&` operátor řetězení odstranit nejednoznačnost a k poskytování samoobslužných dokumentů kódu.  
  
## <a name="overloading"></a>Přetížení  
 `+` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura. Pokud váš kód používá tento operátor na takové třídu nebo strukturu, ujistěte se, že rozumíte své Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `+` operátor přidat čísla. Pokud operandy číselné, Visual Basic vypočte aritmetický výsledek. Aritmetické výsledek představuje součet hodnot dva operandy.  
  
 [!code-vb[VbVbalrOperators#6](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_1.vb)]  
  
 Můžete také `+` operátor ke zřetězení řetězců. Pokud operandy oba řetězce, Visual Basic je zřetězí. Výsledek zřetězení představuje jeden řetězec sestávající z obsah dva operandy jedna po druhé.  
  
 Pokud operandy smíšený typů, výsledek bude záviset na nastavení jazyka [Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md). Následující příklad ilustruje výsledek při `Option Strict` je `On`.  
  
 [!code-vb[VbVbalrOperators#53](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_2.vb)]  
  
 [!code-vb[VbVbalrOperators#50](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_3.vb)]  
[!code-vb[VbVbalrOperators#51](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_4.vb)]  
  
 Následující příklad ilustruje výsledek při `Option Strict` je `Off`.  
  
 [!code-vb[VbVbalrOperators#54](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_5.vb)]  
  
 [!code-vb[VbVbalrOperators#50](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_3.vb)]  
[!code-vb[VbVbalrOperators#52](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_6.vb)]  
  
 Chcete-li odstranit nejednoznačnost, použijte `&` operátor místo `+` pro zřetězení.  
  
## <a name="see-also"></a>Viz také  
 [& – operátor](../../../visual-basic/language-reference/operators/concatenation-operator.md)  
 [Operátory zřetězení](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Aritmetické operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
