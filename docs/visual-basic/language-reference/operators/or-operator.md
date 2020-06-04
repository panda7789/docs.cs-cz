---
title: Or – operátor
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
ms.openlocfilehash: 657b2a473b23789a8ba25fbd11c6b83538fa7803
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401417"
---
# <a name="or-operator-visual-basic"></a>Or – operátor (Visual Basic)
Provede logickou disjunkci dvou `Boolean` výrazů nebo bitovou disjunkci dvou numerických výrazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Povinná hodnota. Libovolný `Boolean` nebo numerický výraz. Pro `Boolean` porovnání `result` je celková logická disjunkce dvou `Boolean` hodnot. U bitových operací `result` je číselná hodnota, která představuje celkové disjunkci dvou číselných bitových vzorů.  
  
 `expression1`  
 Povinná hodnota. Libovolný `Boolean` nebo numerický výraz.  
  
 `expression2`  
 Povinná hodnota. Libovolný `Boolean` nebo numerický výraz.  
  
## <a name="remarks"></a>Poznámky  
 Pro `Boolean` porovnání `result` je `False` if a jenom v případě, že `expression1` a `expression2` vyhodnotí `False` . Následující tabulka ukazuje, jak `result` je určena.  
  
|Pokud `expression1` je|A `expression2` je|Hodnota `result` je|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> V `Boolean` porovnání, `Or` operátor vždy vyhodnocuje oba výrazy, které by mohly zahrnovat volání procedur. [Operátor OrElse](orelse-operator.md) provádí *krátkodobé okruhy*, což znamená, že pokud `expression1` je `True` , pak není `expression2` vyhodnocen.  
  
 U bitových operací `Or` operátor provádí bitové porovnání identicky umístěných bitů ve dvou numerických výrazech a nastavuje odpovídající bit v `result` závislosti na následující tabulce.  
  
|Pokud je bit v `expression1`|A bit v `expression2` je|Bit v `result` je|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
> Vzhledem k tomu, že logické a bitové operátory mají nižší prioritu než jiné aritmetické a relační operátory, měly by být všechny bitové operace uzavřeny v závorkách, aby bylo zajištěno přesné provedení.  
  
## <a name="data-types"></a>Typy dat  
 Pokud se operandy skládají z jednoho `Boolean` výrazu a jednoho číselného výrazu, Visual Basic převede `Boolean` výraz na číselnou hodnotu (– 1 pro `True` a 0 pro `False` ) a provede bitovou operaci.  
  
 Pro `Boolean` porovnání je datový typ výsledku `Boolean` . Pro bitové porovnání je výsledný datový typ číselný typ vhodný pro datové typy `expression1` a `expression2` . Podívejte se na tabulku "relačních a bitových porovnání" v [datových typech výsledků operátoru](data-types-of-operator-results.md).  
  
## <a name="overloading"></a>Přetížení  
 `Or`Operátor může být *přetížen*, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury. Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Or` operátor k provedení logické disjunkce dvou výrazů. Výsledkem je `Boolean` hodnota, která představuje, zda je jeden z obou výrazů `True` .  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 Předchozí příklad vytvoří výsledky `True` , a v `True` `False` uvedeném pořadí.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Or` operátor k provedení celkového logického disjunkce na jednotlivých bitech dvou číselných výrazů. Bit ve vzorci výsledků je nastaven, pokud je jeden z odpovídajících bitů v operandech nastaven na hodnotu 1.  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 Předchozí příklad vytvoří výsledky 10, 14 a 14 v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také

- [Logické/bitové operátory (Visual Basic)](logical-bitwise-operators.md)
- [Priorita operátorů v jazyce Visual Basic](operator-precedence.md)
- [Operátory uvedené podle funkce](operators-listed-by-functionality.md)
- [OrElse – operátor](orelse-operator.md)
- [Logické a bitové operátory v jazyce Visual Basic](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
