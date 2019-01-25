---
title: Not – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
ms.openlocfilehash: cd93316ada1fcf0997922f71a8efc5a3cf411d09
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614569"
---
# <a name="not-operator-visual-basic"></a>Not – operátor (Visual Basic)
Provede logickou negaci `Boolean` výrazu nebo bitovou negaci numerického výrazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = Not expression  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Povinný parametr. Žádné `Boolean` nebo číselný výraz.  
  
 `expression`  
 Povinný parametr. Žádné `Boolean` nebo číselný výraz.  
  
## <a name="remarks"></a>Poznámky  
 Pro `Boolean` výrazy, následující tabulka ukazuje, jak `result` je určen.  
  
|Pokud `expression` je|Hodnota `result` je|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 Pro numerických výrazů `Not` operátor Invertuje bitové hodnoty jakýkoli číselný výraz a nastaví odpovídající bit v `result` podle následující tabulky.  
  
|Pokud bit v `expression` je|Bit v `result` je|  
|-------------------------------|----------------------------|  
|1|0|  
|0|1|  
  
> [!NOTE]
>  Protože logické a bitové operátory mají nižší prioritu než ostatní aritmetické a relační operátory, všechny bitové operace by měl být uzavřen v závorkách zajistit správné spuštění.  
  
## <a name="data-types"></a>Datové typy  
 Logická negace, datový typ výsledku je `Boolean`. Pro bitovou negaci datový typ výsledku je stejný jako u `expression`. Nicméně pokud je výraz `Decimal`, výsledkem je `Long`.  
  
## <a name="overloading"></a>Přetížení  
 `Not` Operátor může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při jeho operand má typ této třídě nebo struktuře. Pokud váš kód používá tento operátor na takové třídy nebo struktury, ujistěte se, že rozumíte jeho Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Not` operátor logické negace na `Boolean` výrazu. Výsledkem je `Boolean` hodnotu, která představuje naopak hodnota výrazu.  
  
 [!code-vb[VbVbalrOperators#33](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_1.vb)]  
  
 Předchozí příklad vytváří výsledky `False` a `True`v uvedeném pořadí.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Not` operátor logické negace jednotlivých bitů číselného výrazu. Bitového vzoru výsledek je nastavena pro stornování odpovídající bit v operandu modelu, včetně bit znaménka.  
  
 [!code-vb[VbVbalrOperators#34](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_2.vb)]  
  
 V předchozím příkladu vytvoří výsledky – 11, –9 a –7, v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také:
- [Logické/bitové operátory (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Logické a bitové operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
