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
ms.openlocfilehash: 03decb4ad32e8ff2c03e3b64a272bce779282973
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701241"
---
# <a name="or-operator-visual-basic"></a>Or – operátor (Visual Basic)
Provede logickou disjunkci dvou @no__t 0 nebo bitovou disjunkci dvou numerických výrazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Požadováno. Libovolný `Boolean` nebo číselný výraz. U porovnání `Boolean` je `result` celková logická disjunkce dvou hodnot `Boolean`. U bitových operací je `result` číselná hodnota představující celkovou bitovou disjunkci dvou číselných bitových vzorů.  
  
 `expression1`  
 Požadováno. Libovolný `Boolean` nebo číselný výraz.  
  
 `expression2`  
 Požadováno. Libovolný `Boolean` nebo číselný výraz.  
  
## <a name="remarks"></a>Poznámky  
 U porovnání `Boolean` je `result` `False` pouze v případě, že `expression1` a `expression2` se vyhodnotí jako `False`. Následující tabulka ukazuje, jak je určena `result`.  
  
|Pokud `expression1` je|A `expression2` je|Hodnota `result` je|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> V porovnání `Boolean` operátor `Or` vždy vyhodnocuje oba výrazy, které by mohly zahrnovat volání procedur. [Operátor OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md) provádí *krátkodobé okruhy*, což znamená, že pokud `expression1` je `True`, pak `expression2` se nevyhodnotí.  
  
 U bitových operací operátor `Or` provádí bitové porovnání identicky umístěných bitů ve dvou numerických výrazech a nastaví odpovídající bit v `result` podle následující tabulky.  
  
|If bit v `expression1` je|A bit v `expression2` je|Bit v `result` je|  
|--------------------------------|---------------------------------|----------------------------|  
|první|první|první|  
|první|0,8|první|  
|0,8|první|první|  
|0,8|0,8|0,8|  
  
> [!NOTE]
> Vzhledem k tomu, že logické a bitové operátory mají nižší prioritu než jiné aritmetické a relační operátory, měly by být všechny bitové operace uzavřeny v závorkách, aby bylo zajištěno přesné provedení.  
  
## <a name="data-types"></a>Datové typy  
 Pokud se operandy skládají z jednoho `Boolean` a jednoho číselného výrazu, Visual Basic převede výraz `Boolean` na číselnou hodnotu (– 1 pro `True` a 0 pro `False`) a provede bitovou operaci.  
  
 U porovnání `Boolean` je datový typ výsledku `Boolean`. Pro bitové porovnání je datový typ výsledku číselný typ, který je vhodný pro datové typy `expression1` a `expression2`. Podívejte se na tabulku "relačních a bitových porovnání" v [datových typech výsledků operátoru](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="overloading"></a>Přetížení  
 Operátor `Or` lze přetížit, což znamená, že třída nebo struktura může předefinovat *chování, pokud*operand má typ této třídy nebo struktury. Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá operátor `Or` k provedení logické disjunkce dvou výrazů. Výsledkem je hodnota @no__t 0, která představuje, zda je jeden z obou výrazů `True`.  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 Předchozí příklad vytvoří výsledky `True`, `True` a `False` v uvedeném pořadí.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je použit operátor `Or` k provedení celkového logického disjunkce na jednotlivých bitech dvou číselných výrazů. Bit ve vzorci výsledků je nastaven, pokud je jeden z odpovídajících bitů v operandech nastaven na hodnotu 1.  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 Předchozí příklad vytvoří výsledky 10, 14 a 14 v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také:

- [Logické/bitové operátory (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operátor OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md)
- [Logické a bitové operátory v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
