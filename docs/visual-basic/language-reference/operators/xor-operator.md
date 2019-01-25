---
title: Xor – operátor (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: af6589206232f01b572cd2b965ba1a0f36d462e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527117"
---
# <a name="xor-operator-visual-basic"></a>Xor – operátor (Visual Basic)
Provede logické vyloučení dvou `Boolean` výrazů nebo bitové vyloučení dvou numerických výrazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Povinný parametr. Žádné `Boolean` nebo číselné proměnné. Logická porovnání `result` je logická exkluze (exkluzivní disjunkce logické) ze dvou `Boolean` hodnoty. Pro bitové operace `result` číselná hodnota, která představuje bitové vyloučení dvou číselných bitové vzory (bitový exkluzivní disjunkce).  
  
 `expression1`  
 Povinný parametr. Žádné `Boolean` nebo číselný výraz.  
  
 `expression2`  
 Povinný parametr. Žádné `Boolean` nebo číselný výraz.  
  
## <a name="remarks"></a>Poznámky  
 Logická porovnání `result` je `True` pouze v případě právě jeden z `expression1` a `expression2` vyhodnotí jako `True`. To znamená pouze v případě `expression1` a `expression2` vyhodnotit na opačnou `Boolean` hodnoty. Následující tabulka ukazuje, jak `result` je určen.  
  
|Pokud `expression1` je|A `expression2` je|Hodnota `result` je|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  Logická porovnání `Xor` operátor vždy vyhodnotí oba výrazy, které mohou zahrnovat volání procedury. Neexistuje žádná short-circuiting protějškem `Xor`, protože výsledek je vždy závisí na oba operandy. Pro *zkrácenou* logické operátory, naleznete v tématu [AndAlso – operátor](../../../visual-basic/language-reference/operators/andalso-operator.md) a [OrElse – operátor](../../../visual-basic/language-reference/operators/orelse-operator.md).  
  
 Pro bitové operace `Xor` operátor provádí porovnání bitového stejně umístěných bitů ve dvou numerických výrazů a nastaví odpovídající bit v `result` podle následující tabulky.  
  
|Pokud bit v `expression1` je|A bitu v `expression2` je|Bit v `result` je|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|0|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
>  Protože logické a bitové operátory mají nižší prioritu než ostatní aritmetické a relační operátory, všechny bitové operace by měl být uzavřen v závorkách zajistit správné spuštění.  
  
 Například 5 `Xor` 3 je 6. Proč je to proto, převést na binární reprezentace 101 a 011 5 a 3. V předchozí tabulce se pak použije k určení, že 101 Xor 011 je 110, což je binární reprezentace desetinné číslo 6.  
  
## <a name="data-types"></a>Datové typy  
 Pokud operandy se skládá z jedné `Boolean` výraz a jeden číselný výraz jazyka Visual Basic převede `Boolean` výraz na číselnou hodnotu (– 1 pro `True` a 0 pro `False`) a provádí logické bitové operace.  
  
 Pro `Boolean` porovnání, datový typ výsledku je `Boolean`. Bitové porovnání, datový typ výsledku je vhodný pro datové typy číselného typu `expression1` a `expression2`. Viz tabulka "Relační a bitový operátor porovnání" [typy výsledků operátoru Data](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="overloading"></a>Přetížení  
 `Xor` Operátor může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře. Pokud váš kód používá tento operátor na takové třídy nebo struktury, ujistěte se, že rozumíte jeho Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Xor` operátor (exkluzivní disjunkce logické) logické vyloučení dvou výrazů. Výsledkem je `Boolean` hodnotu, která udává, jestli přesně jeden z výrazů je `True`.  
  
 [!code-vb[VbVbalrOperators#40](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xor-operator_1.vb)]  
  
 Předchozí příklad vytváří výsledky `False`, `True`, a `False`v uvedeném pořadí.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Xor` operátor logická exkluze (exkluzivní disjunkce logické) na jednotlivé bity dvou numerických výrazů. Je-li přesně odpovídající bity operandy nastavena na hodnotu 1, je nastaven bit vzoru výsledek.  
  
 [!code-vb[VbVbalrOperators#41](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xor-operator_2.vb)]  
  
 Předchozí příklad vytváří výsledky 2, 12 a 14, v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také:
- [Logické/bitové operátory (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Logické a bitové operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
