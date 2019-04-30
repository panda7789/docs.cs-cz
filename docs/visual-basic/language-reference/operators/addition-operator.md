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
ms.openlocfilehash: 4fc8ce96caea436b63fe346139e27ec8dd048f10
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778603"
---
# <a name="-operator-visual-basic"></a>+ – operátor (Visual Basic)
Přidá dvou čísel nebo kladnou hodnotu číselného výrazu. Můžete také použít ke zřetězení dvou výrazů řetězec.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb
expression1 + expression2  
- or -  
+ expression1  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`expression1`|Povinný parametr. Číselné nebo řetězcové výrazu.|  
|`expression2`|Vyžaduje se, pokud `+` operátor je výpočet zápornou hodnotu. Číselné nebo řetězcové výrazu.|  
  
## <a name="result"></a>Výsledek  
 Pokud `expression1` a `expression2` jsou číselné hodnoty a výsledkem je aritmetický součtem.  
  
 Pokud `expression2` chybí, `+` operátor je *unární* operátor identity pro beze změny hodnotě výrazu. V tomto smyslu operace se skládá z zachování znaménko `expression1`, takže výsledek je záporný, pokud `expression1` je záporný.  
  
 Pokud `expression1` a `expression2` jsou obou řetězců, výsledkem je zřetězení jejich hodnoty.  
  
 Pokud `expression1` a `expression2` jsou smíšené typů provedená akce závisí na jejich typy, jejich obsah a nastavení [Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md). Další informace najdete v tabulkách v "Poznámky".  
  
## <a name="supported-types"></a>Podporované typy  
 Všechny číselné typy, včetně typů bez znaménka a s plovoucí desetinnou čárkou a `Decimal`, a `String`.  
  
## <a name="remarks"></a>Poznámky  
 Obecně platí `+` provádí aritmetické sčítání, pokud je to možné a zřetězí, pouze pokud jsou oba výrazy řetězce.  
  
 Pokud žádný výraz `Object`, Visual Basic provede následující akce.  
  
|Datové typy výrazů|Akce kompilátorem|  
|---|---|  
|Číselné datové typy jsou oba výrazy (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, nebo `Double`)|Přidáte. Datový typ výsledku je vhodný pro datové typy číselného typu `expression1` a `expression2`. Viz "Celočíselné aritmetiky" tabulky v [typy výsledků operátoru Data](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).|  
|Jsou oba výrazy typu `String`|Zřetězíte.|  
|Jeden výraz je číselný datový typ a druhý je řetězec|Pokud `Option Strict` je `On`, potom generovat chybu kompilátoru.<br /><br /> Pokud `Option Strict` je `Off`, implicitně převést `String` k `Double` a přidat.<br /><br /> Pokud `String` nelze převést na `Double`, poté vyvolají <xref:System.InvalidCastException> výjimky.|  
|Jeden výraz je číselný datový typ a druhý je [nic](../../../visual-basic/language-reference/nothing.md)|Přidat, s `Nothing` s hodnotou nula.|  
|Jeden výraz je řetězec, a druhá je `Nothing`|CONCATENATE s `Nothing` Vážíme si toho jako "".|  
  
 Pokud je jeden výraz `Object` výraz jazyka Visual Basic provede následující akce.  
  
|Datové typy výrazů|Akce kompilátorem|  
|---|---|  
|`Object` výraz obsahuje číselná hodnota a druhý je číselný datový typ|Pokud `Option Strict` je `On`, potom generovat chybu kompilátoru.<br /><br /> Pokud `Option Strict` je `Off`, pak přidejte.|  
|`Object` výraz obsahuje číselná hodnota a druhý je typu `String`|Pokud `Option Strict` je `On`, potom generovat chybu kompilátoru.<br /><br /> Pokud `Option Strict` je `Off`, implicitně převést `String` k `Double` a přidat.<br /><br /> Pokud `String` nelze převést na `Double`, poté vyvolají <xref:System.InvalidCastException> výjimky.|  
|`Object` výraz obsahuje řetězec a druhý je číselný datový typ|Pokud `Option Strict` je `On`, potom generovat chybu kompilátoru.<br /><br /> Pokud `Option Strict` je `Off`, implicitně převést řetězec `Object` k `Double` a přidat.<br /><br /> Pokud řetězec `Object` nelze převést na `Double`, poté vyvolají <xref:System.InvalidCastException> výjimky.|  
|`Object` výraz obsahuje řetězec a druhý je typu `String`|Pokud `Option Strict` je `On`, potom generovat chybu kompilátoru.<br /><br /> Pokud `Option Strict` je `Off`, implicitně převést `Object` k `String` a zřetězení.|  
  
 Pokud jsou oba výrazy `Object` výrazy, Visual Basic provede následující akce (`Option Strict Off` pouze).  
  
|Datové typy výrazů|Akce kompilátorem|  
|---|---|  
|Obě `Object` výrazy uložení číselné hodnoty|Přidáte.|  
|Obě `Object` výrazy jsou typu `String`|Zřetězíte.|  
|Jeden `Object` výraz obsahuje číselná hodnota a druhý obsahuje řetězec|Implicitně převést řetězec `Object` k `Double` a přidat.<br /><br /> Pokud řetězec `Object` nelze převést na číselnou hodnotu a pak vyvolejte <xref:System.InvalidCastException> výjimky.|  
  
 Pokud `Object` výraz vyhodnocen jako [nic](../../../visual-basic/language-reference/nothing.md) nebo <xref:System.DBNull>, `+` operátor považuje za `String` s hodnotou "".  
  
> [!NOTE]
>  Při použití `+` operátoru, nemusí být schopní určit, zda dojde k přidání nebo řetězec zřetězení. Použití `&` operátoru pro zřetězení, chcete-li odstranit nejednoznačnost a k poskytování samoobslužných dokumentace kódu.  
  
## <a name="overloading"></a>Přetížení  
 `+` Operátor může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře. Pokud váš kód používá tento operátor na takové třídy nebo struktury, ujistěte se, že rozumíte jeho Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `+` operátor pro přidání čísel. Pokud jsou operandy číselné, Visual Basic vypočítá aritmetický výsledek. Výsledek aritmetické představuje součet dvou operandů.  
  
 [!code-vb[VbVbalrOperators#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#6)]  
  
 Můžete také použít `+` operátoru pro zřetězení řetězců. Pokud jsou operandy obou řetězců, Visual Basic je zřetězí. Zřetězení výsledek představuje jeden řetězec sestávající z obsah dva operandy jednu po druhé.  
  
 Pokud operandy jsou smíšené typy, výsledek závisí na nastavení [Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md). Následující příklad ukazuje výsledek při `Option Strict` je `On`.  
  
 [!code-vb[VbVbalrOperators#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class3.vb#53)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#51)]  
  
 Následující příklad ukazuje výsledek při `Option Strict` je `Off`.  
  
 [!code-vb[VbVbalrOperators#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#54)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#52)]  
  
 Chcete-li odstranit nejednoznačnost, používejte `&` namísto `+` pro zřetězení.  
  
## <a name="see-also"></a>Viz také:

- [& – operátor](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [Operátory zřetězení](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Aritmetické operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
