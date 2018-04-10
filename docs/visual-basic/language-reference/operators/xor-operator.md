---
title: Xor – operátor (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Xor
helpviewer_keywords:
- exclusive OR operator [Visual Basic]
- logical exclusion
- operators [Visual Basic], exclusive or
- exclusion operator [Visual Basic]
- operators [Visual Basic], bitwise
- bitwise operators [Visual Basic], XOR operator
- Xor operator [Visual Basic]
- Xor keyword [Visual Basic]
- bitwise comparison [Visual Basic]
ms.assetid: 036000a9-3934-4e7f-a9d0-a816de3d84a6
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b14f11f2df2df9c29e88e9188390cfe245d2cb58
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="xor-operator-visual-basic"></a>Xor – operátor (Visual Basic)
Provede logické vyloučení dvou `Boolean` výrazů nebo bitové vyloučení dvou numerických výrazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Požadováno. Všechny `Boolean` nebo číselné proměnné. Pro logickou porovnání `result` je logická exkluze (exkluzivní disjunkce logické) ze dvou `Boolean` hodnoty. Pro bitové operace `result` je číselná hodnota, která představuje bitové vyloučení dvou bit číselná vzory (výhradní bitovou disjunkci).  
  
 `expression1`  
 Požadováno. Všechny `Boolean` nebo číselný výraz.  
  
 `expression2`  
 Požadováno. Všechny `Boolean` nebo číselný výraz.  
  
## <a name="remarks"></a>Poznámky  
 Pro logickou porovnání `result` je `True` jenom v případě právě jeden z `expression1` a `expression2` vyhodnocuje `True`. To znamená jenom v případě `expression1` a `expression2` vyhodnocení na opačné `Boolean` hodnoty. Následující tabulka popisuje, jak `result` je určen.  
  
|Pokud `expression1` je|A `expression2` je|Hodnota `result` je|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  Logická hodnota porovnání `Xor` operátor vždy vyhodnotí oba výrazy, které mohou zahrnovat volání procedury. Neexistuje žádné short-circuiting protějškem `Xor`, protože výsledek je vždy závisí na oba operandy. Pro *krátká smyčka* najdete v části logické operátory [AndAlso – operátor](../../../visual-basic/language-reference/operators/andalso-operator.md) a [orelse – operátor](../../../visual-basic/language-reference/operators/orelse-operator.md).  
  
 Pro bitové operace `Xor` operátor provádí bitové porovnání stejně umístěných bitů ve dvou numerických výrazů a nastaví odpovídající chvíli v `result` podle následující tabulky.  
  
|Pokud bit v `expression1` je|A chvíli v `expression2` je|Bit v `result` je|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|0|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
>  Vzhledem k tomu, že logické a bitové operátory mít nižší prioritu než ostatní aritmetické a relační operátory, všechny bitové operace by se měla uvádět v závorkách a zajišťují přesné provádění.  
  
 Například 5 `Xor` 3 je 6. Zjistěte, proč to tedy převést na binární reprezentace 101 a 011 5 a 3. V předchozí tabulce pak použije k určení, že 101 Xor 011 je 110, což je binární reprezentace desetinné číslo 6.  
  
## <a name="data-types"></a>Datové typy  
 Pokud operandy skládá z jedné `Boolean` výraz a jeden číselného výrazu jazyka Visual Basic převede `Boolean` výraz na číselnou hodnotu (-1 pro `True` a 0 pro `False`) a provede se bitová operace.  
  
 Pro `Boolean` je datový typ výsledku porovnání, `Boolean`. Bitové porovnání, výsledek datový typ je vhodný pro datové typy číselného typu `expression1` a `expression2`. Podívejte se na tabulku "Relační bitový porovnání a" v [typy výsledků operátoru Data](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="overloading"></a>Přetížení  
 `Xor` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura. Pokud váš kód používá tento operátor. v takových třídu nebo strukturu, ujistěte se, že rozumíte své Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Xor` operátor provést (exkluzivní disjunkce logické) logické vyloučení dvou výrazů. Výsledkem je, `Boolean` hodnotu, která udává, zda přesně jeden z výrazů je `True`.  
  
 [!code-vb[VbVbalrOperators#40](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xor-operator_1.vb)]  
  
 Předchozí příklad vytvoří výsledky `False`, `True`, a `False`, v uvedeném pořadí.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Xor` operátor k provedení logické vyloučení (exkluzivní disjunkce logické) na jednotlivé bity dvou numerických výrazů. Je-li přesně odpovídající bity operandy nastavena na hodnotu 1, je nastaven bit ve vzoru výsledek.  
  
 [!code-vb[VbVbalrOperators#41](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xor-operator_2.vb)]  
  
 Předchozí příklad vytvoří výsledky 2, 12 a 14, v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také  
 [Logické/bitové operátory (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Logické a bitové operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
