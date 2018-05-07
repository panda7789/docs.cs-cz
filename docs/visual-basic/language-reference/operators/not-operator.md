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
ms.openlocfilehash: 332cee57c8d25d7f51737e01e70ba515d50bd6e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="not-operator-visual-basic"></a>Not – operátor (Visual Basic)
Provede logickou negaci `Boolean` výrazu nebo bitovou negaci numerického výrazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = Not expression  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Požadováno. Všechny `Boolean` nebo číselný výraz.  
  
 `expression`  
 Požadováno. Všechny `Boolean` nebo číselný výraz.  
  
## <a name="remarks"></a>Poznámky  
 Pro `Boolean` výrazy, následující tabulka popisuje, jak `result` je určen.  
  
|Pokud `expression` je|Hodnota `result` je|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 Pro hodnotu numerické výrazy `Not` operátor Invertuje výběr hodnoty bit žádné číselného výrazu a nastaví odpovídající chvíli v `result` podle následující tabulky.  
  
|Pokud bit v `expression` je|Bit v `result` je|  
|-------------------------------|----------------------------|  
|1|0|  
|0|1|  
  
> [!NOTE]
>  Vzhledem k tomu, že logické a bitové operátory mít nižší prioritu než ostatní aritmetické a relační operátory, všechny bitové operace by se měla uvádět v závorkách a zajišťují přesné provádění.  
  
## <a name="data-types"></a>Datové typy  
 Logická negace, je datový typ výsledku `Boolean`. Pro bitovou negaci výsledný typ dat je stejný jako u `expression`. Ale pokud je výraz `Decimal`, výsledkem je `Long`.  
  
## <a name="overloading"></a>Přetížení  
 `Not` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při jeho operand má typ třídy nebo struktura. Pokud váš kód používá tento operátor na takové třídu nebo strukturu, ujistěte se, že rozumíte své Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Not` operátor k plnění Logická negace `Boolean` výraz. Výsledkem je, `Boolean` hodnotu, která představuje zpětného hodnota výrazu.  
  
 [!code-vb[VbVbalrOperators#33](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_1.vb)]  
  
 V předchozím příkladu vytvoří výsledky `False` a `True`, v uvedeném pořadí.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Not` operátor provést Logická negace jednotlivých bitů číselného výrazu. Bit ve vzoru výsledek nastaven na naopak odpovídající bit ve vzoru operand, včetně bit přihlášení.  
  
 [!code-vb[VbVbalrOperators#34](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_2.vb)]  
  
 V předchozím příkladu vytvoří výsledky –11, –9 a –7, v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také  
 [Logické/bitové operátory (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Logické a bitové operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
