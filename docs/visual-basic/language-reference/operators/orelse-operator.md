---
title: OrElse – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- OrElse
- vb.OrElse
helpviewer_keywords:
- short-circuiting
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], disjunction
- short-circuit evaluation
- OrElse operator [Visual Basic]
ms.assetid: 253803d8-05b0-47d7-b213-abd222847779
ms.openlocfilehash: 1ee3c1a5b6089f44742281eb40e2a7e9cb3e2812
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="orelse-operator-visual-basic"></a>OrElse – operátor (Visual Basic)
Provede zkrácenou včetně logické disjunkce dvou výrazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Požadováno. Všechny `Boolean` výraz.  
  
 `expression1`  
 Požadováno. Všechny `Boolean` výraz.  
  
 `expression2`  
 Požadováno. Všechny `Boolean` výraz.  
  
## <a name="remarks"></a>Poznámky  
 Logický provoz se říká, že *krátká smyčka* Pokud zkompilovaný kód můžete vynechat vyhodnocení jeden výraz v závislosti na výsledku další výraz. Pokud výsledek první výrazu vyhodnoceného Určuje konečný výsledek operace, není třeba vyhodnotit druhý výraz, protože jej nelze změnit konečný výsledek. Krátká smyčka může zlepšit výkon, pokud přeskočených výrazu je složité, nebo pokud se týká volání procedur.  
  
 Pokud nebo oba výrazy vyhodnocení `True`, `result` je `True`. Následující tabulka popisuje, jak `result` je určen.  
  
|Pokud `expression1` je|A `expression2` je|Hodnota `result` je|  
|-------------------------|--------------------------|------------------------------|  
|`True`|(není vyhodnotit)|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a>Datové typy  
 `OrElse` Operátor je určená jenom pro [datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Visual Basic převede každý operand podle potřeby k `Boolean` a provede operaci zcela v `Boolean`. Chcete-li přiřadit výsledek na číselný typ, Visual Basic převede z `Boolean` do daného typu. To by mohla vést k neočekávanému chování. Například `5 OrElse 12` výsledkem `–1` při převodu do `Integer`.  
  
## <a name="overloading"></a>Přetížení  
 [Operátor nebo](../../../visual-basic/language-reference/operators/or-operator.md) a [IsTrue – operátor](../../../visual-basic/language-reference/operators/istrue-operator.md) může být *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat jejich chování při operand má typ této třídy nebo strukturu. Přetížení `Or` a `IsTrue` operátory má vliv na chování `OrElse` operátor. Pokud váš kód používá `OrElse` na třídu nebo strukturu, která přetížení `Or` a `IsTrue`, ujistěte se, rozumíte jejich Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `OrElse` operátor provést logické disjunkce dvou výrazů. Výsledkem je, `Boolean` hodnotu, která představuje zda je splněna jedna ze dvou výrazů. Pokud je první výraz `True`, druhá, nebude hodnocen.  
  
 [!code-vb[VbVbalrOperators#37](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/orelse-operator_1.vb)]  
  
 V předchozím příkladu vytvoří výsledky `True`, `True`, a `False` v uvedeném pořadí. Při výpočtu `firstCheck`, druhý výraz není vyhodnotit, protože první je již `True`. Ale druhý výraz vyhodnotí při výpočtu `secondCheck`.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `If`... `Then` příkazu, který obsahuje dva volání procedur. Pokud vrátí první volání `True`, druhý postup není volán. Pokud se druhý postup provádí důležité úlohy, které mají být provedeny vždy při spuštění této části kódu, může vést k neočekávaným výsledkům.  
  
 [!code-vb[VbVbalrOperators#38](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/orelse-operator_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Logické/bitové operátory (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operátor Or](../../../visual-basic/language-reference/operators/or-operator.md)  
 [Operátor IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md)  
 [Logické a bitové operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
