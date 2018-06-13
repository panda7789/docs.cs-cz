---
title: Or – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Or
helpviewer_keywords:
- Or operator [Visual Basic]
- operators [Visual Basic], bitwise
- inclusive Or operator [Visual Basic]
- bitwise operators [Visual Basic], OR operator
- Or keyword [Visual Basic]
- operators [Visual Basic], inclusive or
- operators [Visual Basic], disjunction
- bitwise comparison [Visual Basic]
- logical disjunction
- disjunction operator [Visual Basic]
ms.assetid: 41ed6905-bf3d-468a-9e3b-03c10d461891
ms.openlocfilehash: 9e02f619a81ee3c15321dfd44963c1a7d29843ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604767"
---
# <a name="or-operator-visual-basic"></a>Or – operátor (Visual Basic)
Provede logické disjunkce dvou `Boolean` výrazů nebo bitovou disjunkci dvou numerických výrazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Požadováno. Všechny `Boolean` nebo číselný výraz. Pro `Boolean` porovnání, `result` je včetně logické disjunkce dvou `Boolean` hodnoty. Pro bitové operace `result` je číselná hodnota představující včetně bitovou disjunkci dvou bit číselná vzory.  
  
 `expression1`  
 Požadováno. Všechny `Boolean` nebo číselný výraz.  
  
 `expression2`  
 Požadováno. Všechny `Boolean` nebo číselný výraz.  
  
## <a name="remarks"></a>Poznámky  
 Pro `Boolean` porovnání, `result` je `False` případě a pouze v případě obou `expression1` a `expression2` vyhodnocení `False`. Následující tabulka popisuje, jak `result` je určen.  
  
|Pokud `expression1` je|A `expression2` je|Hodnota `result` je|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  V `Boolean` porovnání, `Or` operátor vždy vyhodnotí oba výrazy, které mohou zahrnovat volání procedury. [Orelse – operátor](../../../visual-basic/language-reference/operators/orelse-operator.md) provede *krátká smyčka*, což znamená, že pokud `expression1` je `True`, pak `expression2` , nebude hodnocen.  
  
 Pro bitové operace `Or` operátor provádí bitové porovnání stejně umístěných bitů ve dvou numerických výrazů a nastaví odpovídající chvíli v `result` podle následující tabulky.  
  
|Pokud bit v `expression1` je|A chvíli v `expression2` je|Bit v `result` je|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
>  Vzhledem k tomu, že logické a bitové operátory mít nižší prioritu než ostatní aritmetické a relační operátory, všechny bitové operace by se měla uvádět v závorkách a zajišťují přesné provádění.  
  
## <a name="data-types"></a>Datové typy  
 Pokud operandy skládá z jedné `Boolean` výraz a jeden číselného výrazu jazyka Visual Basic převede `Boolean` výraz na číselnou hodnotu (-1 pro `True` a 0 pro `False`) a provede se bitová operace.  
  
 Pro `Boolean` je datový typ výsledku porovnání, `Boolean`. Bitové porovnání, výsledek datový typ je vhodný pro datové typy číselného typu `expression1` a `expression2`. Podívejte se na tabulku "Relační bitový porovnání a" v [typy výsledků operátoru Data](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="overloading"></a>Přetížení  
 `Or` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura. Pokud váš kód používá tento operátor na takové třídu nebo strukturu, ujistěte se, že rozumíte své Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Or` operátor provést včetně logické disjunkce dvou výrazů. Výsledkem je, `Boolean` hodnotu, která představuje zda je jedna ze dvou výrazů `True`.  
  
 [!code-vb[VbVbalrOperators#35](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/or-operator_1.vb)]  
  
 V předchozím příkladu vytvoří výsledky `True`, `True`, a `False`, v uvedeném pořadí.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Or` operátor provést včetně logické disjunkce na jednotlivé bity dvou numerických výrazů. Pokud je buď odpovídající bity operandy nastavená na hodnotu 1, je nastaven bit ve vzoru výsledek.  
  
 [!code-vb[VbVbalrOperators#36](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/or-operator_2.vb)]  
  
 V předchozím příkladu vytvoří výsledky 10, 14 a 14, v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také  
 [Logické/bitové operátory (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operátor OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md)  
 [Logické a bitové operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
