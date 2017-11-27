---
title: "AndAlso – operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.AndAlso
- AndAlso
helpviewer_keywords:
- short-circuiting
- AndAlso operator [Visual Basic]
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], conjunction
- short-circuit evaluation
ms.assetid: bbc15191-b374-495b-9b8f-7b8c2f4388eb
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5f92f4ed226c2923c3d95a7b80db3872b7ac33dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="andalso-operator-visual-basic"></a>AndAlso – operátor (Visual Basic)
Provede zkrácenou logickou konjunkci dvou výrazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`result`|Požadováno. Všechny `Boolean` výraz. Výsledkem je `Boolean` výsledku porovnání řetězců dvou výrazů.|  
|`expression1`|Požadováno. Všechny `Boolean` výraz.|  
|`expression2`|Požadováno. Všechny `Boolean` výraz.|  
  
## <a name="remarks"></a>Poznámky  
 Logický provoz se říká, že *krátká smyčka* Pokud zkompilovaný kód můžete vynechat vyhodnocení jeden výraz v závislosti na výsledku další výraz. Pokud výsledek první výrazu vyhodnoceného Určuje konečný výsledek operace, není třeba vyhodnotit druhý výraz, protože jej nelze změnit konečný výsledek. Krátká smyčka může zlepšit výkon, pokud přeskočených výrazu je složité, nebo pokud se týká volání procedur.  
  
 Pokud jsou oba výrazy vyhodnoceny `True`, `result` je `True`. Následující tabulka popisuje, jak `result` je určen.  
  
|Pokud `expression1` je|A `expression2` je|Hodnota `result` je|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|(není vyhodnotit)|`False`|  
  
## <a name="data-types"></a>Datové typy  
 `AndAlso` Operátor je určená jenom pro [datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Visual Basic převede každý operand podle potřeby k `Boolean` a provede operaci zcela v `Boolean`. Chcete-li přiřadit výsledek na číselný typ, Visual Basic převede z `Boolean` do daného typu. To by mohla vést k neočekávanému chování. Například `5 AndAlso 12` výsledkem `–1` při převodu do `Integer`.  
  
## <a name="overloading"></a>Přetížení  
 [a operátor](../../../visual-basic/language-reference/operators/and-operator.md) a [IsFalse – operátor](../../../visual-basic/language-reference/operators/isfalse-operator.md) může být *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat jejich chování při operand má typ této třídu nebo strukturu. Přetížení `And` a `IsFalse` operátory má vliv na chování `AndAlso` operátor. Pokud váš kód používá `AndAlso` na třídu nebo strukturu, která přetížení `And` a `IsFalse`, ujistěte se, rozumíte jejich Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `AndAlso` operátor provést logickou konjunkci dvou výrazů. Výsledkem je, `Boolean` hodnotu, která udává, zda celý conjoined výraz hodnotu true. Pokud je první výraz `False`, druhá, nebude hodnocen.  
  
 [!code-vb[VbVbalrOperators#24](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/andalso-operator_1.vb)]  
  
 V předchozím příkladu vytvoří výsledky `True`, `False`, a `False`, v uvedeném pořadí. Při výpočtu `secondCheck`, druhý výraz není vyhodnotit, protože první je již `False`. Ale druhý výraz vyhodnotí při výpočtu `thirdCheck`.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `Function` procedury, která hledá dané hodnoty mezi elementy pole. Pokud je pole prázdné, nebo pokud byla překročena délka pole, `While` příkaz testování elementu pole proti hledanou hodnotu.  
  
 [!code-vb[VbVbalrOperators#25](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/andalso-operator_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Logické/bitové operátory (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [And – operátor](../../../visual-basic/language-reference/operators/and-operator.md)  
 [IsFalse – operátor](../../../visual-basic/language-reference/operators/isfalse-operator.md)  
 [Logické a bitové operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
