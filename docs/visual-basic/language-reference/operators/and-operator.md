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
ms.openlocfilehash: 090ae67c1e5f04c5d9c4f6aed7f8131d8f830166
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968852"
---
# <a name="and-operator-visual-basic"></a>And – operátor (Visual Basic)
Provede logickou konjunkci dvou `Boolean` výrazů nebo bitové spojení dvou numerických výrazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = expression1 And expression2  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Povinný parametr. Žádné `Boolean` nebo číselný výraz. Logická porovnání `result` je logickou konjunkci dvou `Boolean` hodnoty. Pro bitové operace `result` číselná hodnota představující bitové spojení dvou číselných bitové vzory.  
  
 `expression1`  
 Povinný parametr. Žádné `Boolean` nebo číselný výraz.  
  
 `expression2`  
 Povinný parametr. Žádné `Boolean` nebo číselný výraz.  
  
## <a name="remarks"></a>Poznámky  
 Logická porovnání `result` je `True` Pokud a pouze pokud oba `expression1` a `expression2` vyhodnotit `True`. Následující tabulka ukazuje, jak `result` je určen.  
  
|Pokud `expression1` je|A `expression2` je|Hodnota `result` je|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  Logická porovnání `And` operátor vždy vyhodnotí oba výrazy, které mohou zahrnovat volání procedury. [AndAlso – operátor](../../../visual-basic/language-reference/operators/andalso-operator.md) provádí *zkrácenou*, což znamená, že pokud `expression1` je `False`, pak `expression2` , nebude hodnocen.  
  
 Při použití u číselných hodnot `And` operátor provádí porovnání bitového stejně umístěných bitů ve dvou numerických výrazů a nastaví odpovídající bit v `result` podle následující tabulky.  
  
|Pokud bit v `expression1` je|A bitu v `expression2` je|Bit v `result` je|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
|0|0|0|  
  
> [!NOTE]
>  Protože logické a bitové operátory mají nižší prioritu než ostatní aritmetické a relační operátory, všechny bitové operace by měl být uzavřen v závorkách k zajištění přesné výsledky.  
  
## <a name="data-types"></a>Datové typy  
 Pokud operandy se skládá z jedné `Boolean` výraz a jeden číselný výraz jazyka Visual Basic převede `Boolean` výraz na číselnou hodnotu (– 1 pro `True` a 0 pro `False`) a provádí logické bitové operace.  
  
 Logická porovnání, datový typ výsledku je `Boolean`. Bitové porovnání, datový typ výsledku je vhodný pro datové typy číselného typu `expression1` a `expression2`. Viz tabulka "Relační a bitový operátor porovnání" [typy výsledků operátoru Data](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
> [!NOTE]
>  `And` Operátor může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře. Pokud váš kód používá tento operátor na takové třídy nebo struktury, ujistěte se, že rozumíte jeho Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `And` operátor logickou konjunkci dvou výrazů. Výsledkem je `Boolean` hodnotu, která udává, zda jsou oba výrazy `True`.  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 Předchozí příklad vytváří výsledky `True` a `False`v uvedeném pořadí.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `And` operátor logickou konjunkci na jednotlivé bity dvou numerických výrazů. Pokud odpovídající bitů v operandy jsou nastaveny na 1, je nastaven bit vzoru výsledek.  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 V předchozím příkladu vytvoří výsledky 8, 2 a 0, v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také:
- [Logické/bitové operátory (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operátor AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md)
- [Logické a bitové operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
