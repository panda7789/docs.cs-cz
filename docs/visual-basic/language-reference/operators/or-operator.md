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
ms.openlocfilehash: 0277b6f24e62ed5f0cad3dae225c86fffc4c09b9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58835294"
---
# <a name="or-operator-visual-basic"></a>Or – operátor (Visual Basic)
Provede logickou disjunkci dvou `Boolean` výrazů nebo bitovou disjunkci dvou numerických výrazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Povinný parametr. Žádné `Boolean` nebo číselný výraz. Pro `Boolean` porovnání, `result` je inkluzivní logickou disjunkci dvou `Boolean` hodnoty. Pro bitové operace `result` číselná hodnota představující včetně bitovou disjunkci dvou číselných bitové vzory.  
  
 `expression1`  
 Povinný parametr. Žádné `Boolean` nebo číselný výraz.  
  
 `expression2`  
 Povinný parametr. Žádné `Boolean` nebo číselný výraz.  
  
## <a name="remarks"></a>Poznámky  
 Pro `Boolean` porovnání, `result` je `False` Pokud a pouze pokud oba `expression1` a `expression2` vyhodnotit `False`. Následující tabulka ukazuje, jak `result` je určen.  
  
|Pokud `expression1` je|A `expression2` je|Hodnota `result` je|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  V `Boolean` porovnání, `Or` operátor vždy vyhodnotí oba výrazy, které mohou zahrnovat volání procedury. [OrElse – operátor](../../../visual-basic/language-reference/operators/orelse-operator.md) provádí *zkrácenou*, což znamená, že pokud `expression1` je `True`, pak `expression2` , nebude hodnocen.  
  
 Pro bitové operace `Or` operátor provádí porovnání bitového stejně umístěných bitů ve dvou numerických výrazů a nastaví odpovídající bit v `result` podle následující tabulky.  
  
|Pokud bit v `expression1` je|A bitu v `expression2` je|Bit v `result` je|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
>  Protože logické a bitové operátory mají nižší prioritu než ostatní aritmetické a relační operátory, všechny bitové operace by měl být uzavřen v závorkách zajistit správné spuštění.  
  
## <a name="data-types"></a>Datové typy  
 Pokud operandy se skládá z jedné `Boolean` výraz a jeden číselný výraz jazyka Visual Basic převede `Boolean` výraz na číselnou hodnotu (– 1 pro `True` a 0 pro `False`) a provádí logické bitové operace.  
  
 Pro `Boolean` porovnání, datový typ výsledku je `Boolean`. Bitové porovnání, datový typ výsledku je vhodný pro datové typy číselného typu `expression1` a `expression2`. Viz tabulka "Relační a bitový operátor porovnání" [typy výsledků operátoru Data](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="overloading"></a>Přetížení  
 `Or` Operátor může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře. Pokud váš kód používá tento operátor na takové třídy nebo struktury, ujistěte se, že rozumíte jeho Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Or` operátor inkluzivní logickou disjunkci dvou výrazů. Výsledkem je `Boolean` hodnotu, která udává, zda je jedna ze dvou výrazů `True`.  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 Předchozí příklad vytváří výsledky `True`, `True`, a `False`v uvedeném pořadí.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Or` operátor inkluzivní logickou disjunkci na jednotlivé bity dvou numerických výrazů. Pokud některý z odpovídající bitů v operandů je nastavená na 1, je nastaven bit vzoru výsledek.  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 V předchozím příkladu vytvoří výsledky 10, 14 a 14, v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také:

- [Logické/bitové operátory (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operátor OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md)
- [Logické a bitové operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
