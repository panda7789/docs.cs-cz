---
title: '&lt;&lt; – Operátor (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: d39a134390591e3c72887a38e8aacb4631c71d87
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539035"
---
# <a name="ltlt-operator-visual-basic"></a>&lt;&lt; – Operátor (Visual Basic)
Provede aritmetický operátor posunu vlevo bitový vzor.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = pattern << amount  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Povinný parametr. Integrální číselné hodnoty. Výsledek posunu bitový vzor. Datový typ je stejné jako u `pattern`.  
  
 `pattern`  
 Povinný parametr. Integrální číselný výraz. Bitový vzor posunutí. Datový typ musí být celočíselného typu (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, nebo `ULong`).  
  
 `amount`  
 Povinný parametr. Číselný výraz. Počet bitů, chcete-li posunout bitový vzor. Datový typ musí být `Integer` nebo rozšířit na `Integer`.  
  
## <a name="remarks"></a>Poznámky  
 Aritmetické staffhubu nejsou cyklické, což znamená, že nejsou na druhém konci znovuzavedeno bity posunuly jeden konec výsledek. V aritmetických posunutí doleva bity posunuta mimo rozsah datového typu výsledku ignorovány a bitové pozice uvolněné na pravé straně jsou nastaveny na hodnotu nula.  
  
 Aby shift ve více bitů než výsledek může obsahovat jazyka Visual Basic zakrývá hodnotu `amount` s maskou velikost, která odpovídá datovému typu `pattern`. Binární a tyto hodnoty se používá pro hodnota shift. Velikost masky jsou následující:  
  
|Datový typ `pattern`|Maska velikost (decimální)|Maska velikost (v šestnáctkové hodnotě)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|&H00000007|  
|`Short`, `UShort`|15|&H0000000F|  
|`Integer`, `UInteger`|31|&H0000001F|  
|`Long`, `ULong`|63|&H0000003F|  
  
 Pokud `amount` je nula, hodnota `result` je stejná jako hodnota `pattern`. Pokud `amount` je záporný, je provedena jako hodnoty bez znaménka a maskována pomocí masky odpovídající velikost.  
  
 Aritmetické staffhubu nikdy generovat výjimky přetečení.  
  
> [!NOTE]
>  `<<` Operátor může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře. Pokud váš kód používá tento operátor na takové třídy nebo struktury, ujistěte se, že rozumíte jeho Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `<<` operátor aritmetické operace na integrální hodnoty posune doleva. Výsledek je vždy stejný datový typ jako, který se posune výrazu.  
  
 [!code-vb[VbVbalrOperators#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-operator_1.vb)]  
  
 Výsledky v předchozím příkladu jsou následující:  
  
-   `result1` is 192 (0000 0000 1100 0000).  
  
-   `result2` is 3072 (0000 1100 0000 0000).  
  
-   `result3` is -32768 (1000 0000 0000 0000).  
  
-   `result4` is 384 (0000 0001 1000 0000).  
  
-   `result5` je 0 (posunuté 15 míst na levé straně).  
  
 Hodnota shift pro `result4` se vypočte takto: 17 a 15, které se rovná 1.  
  
## <a name="see-also"></a>Viz také:
- [Operátory bitového posunu](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<<= – operátor](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)
- [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Aritmetické operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
