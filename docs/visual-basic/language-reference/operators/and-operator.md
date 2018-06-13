---
title: And – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.And
helpviewer_keywords:
- operators [Visual Basic], bitwise
- logical conjunction
- bitwise AND operator [Visual Basic]
- conjunction operator [Visual Basic]
- And operator [Visual Basic]
- bitwise operators [Visual Basic], AND operator
- operators [Visual Basic], conjunction
- bitwise comparison [Visual Basic]
ms.assetid: 2ea711f3-439a-4c7c-9e3a-1ffe3b0d6046
ms.openlocfilehash: e14dfd8ba200598084cad04d1faa05f3561f8dab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604638"
---
# <a name="and-operator-visual-basic"></a>And – operátor (Visual Basic)
Provede logickou konjunkci dvou `Boolean` výrazů nebo bitové spojení dvou numerických výrazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = expression1 And expression2  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Požadováno. Všechny `Boolean` nebo číselný výraz. Pro logickou porovnání `result` je logickou konjunkci dvou `Boolean` hodnoty. Pro bitové operace `result` je číselná hodnota představující bitové spojení dvou bit číselná vzory.  
  
 `expression1`  
 Požadováno. Všechny `Boolean` nebo číselný výraz.  
  
 `expression2`  
 Požadováno. Všechny `Boolean` nebo číselný výraz.  
  
## <a name="remarks"></a>Poznámky  
 Pro logickou porovnání `result` je `True` případě a pouze v případě obou `expression1` a `expression2` vyhodnocení `True`. Následující tabulka popisuje, jak `result` je určen.  
  
|Pokud `expression1` je|A `expression2` je|Hodnota `result` je|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  Logická hodnota porovnání `And` operátor vždy vyhodnotí oba výrazy, které mohou zahrnovat volání procedury. [AndAlso – operátor](../../../visual-basic/language-reference/operators/andalso-operator.md) provede *krátká smyčka*, což znamená, že pokud `expression1` je `False`, pak `expression2` , nebude hodnocen.  
  
 Při použití číselné hodnoty, `And` operátor provádí bitové porovnání stejně umístěných bitů ve dvou numerických výrazů a nastaví odpovídající chvíli v `result` podle následující tabulky.  
  
|Pokud bit v `expression1` je|A chvíli v `expression2` je|Bit v `result` je|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
|0|0|0|  
  
> [!NOTE]
>  Vzhledem k tomu, že logické a bitové operátory mít nižší prioritu než ostatní aritmetické a relační operátory, všechny bitové operace by se měla uvádět v závorkách zajistit přesné výsledky.  
  
## <a name="data-types"></a>Datové typy  
 Pokud operandy skládá z jedné `Boolean` výraz a jeden číselného výrazu jazyka Visual Basic převede `Boolean` výraz na číselnou hodnotu (-1 pro `True` a 0 pro `False`) a provede se bitová operace.  
  
 Logická hodnota porovnání, datový typ výsledku je `Boolean`. Bitové porovnání, výsledek datový typ je vhodný pro datové typy číselného typu `expression1` a `expression2`. Podívejte se na tabulku "Relační bitový porovnání a" v [typy výsledků operátoru Data](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
> [!NOTE]
>  `And` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura. Pokud váš kód používá tento operátor na takové třídu nebo strukturu, ujistěte se, že rozumíte své Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `And` operátor provést logickou konjunkci dvou výrazů. Výsledkem je, `Boolean` hodnotu, která udává, zda jsou obě výrazy `True`.  
  
 [!code-vb[VbVbalrOperators#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-operator_1.vb)]  
  
 V předchozím příkladu vytvoří výsledky `True` a `False`, v uvedeném pořadí.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `And` operátor k provedení logické spojení na jednotlivé bity dvou numerických výrazů. Pokud odpovídající bity v operandy jsou obě nastavena na hodnotu 1, je nastaven bit ve vzoru výsledek.  
  
 [!code-vb[VbVbalrOperators#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-operator_2.vb)]  
  
 V předchozím příkladu poskytuje výsledky 8, 2 a 0, v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také  
 [Logické/bitové operátory (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operátor AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md)  
 [Logické a bitové operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
