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
ms.openlocfilehash: 8f28026b526c29a6122725b2689e53b7f6ee7327
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348254"
---
# <a name="or-operator-visual-basic"></a>Or – operátor (Visual Basic)
Provede logickou disjunkci dvou `Boolean` výrazů nebo bitovou disjunkci dvou numerických výrazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Požadováno. Libovolný `Boolean` nebo číselný výraz. Pro účely porovnání `Boolean` `result` je logickým disjunkci dvou `Boolean` hodnot. V případě bitových operací je `result` číselná hodnota představující celkovou bitovou disjunkci dvou číselných bitových vzorů.  
  
 `expression1`  
 Požadováno. Libovolný `Boolean` nebo číselný výraz.  
  
 `expression2`  
 Požadováno. Libovolný `Boolean` nebo číselný výraz.  
  
## <a name="remarks"></a>Poznámky  
 Pro porovnání `Boolean` `result` je `False` pouze v případě, že `expression1` a `expression2` vyhodnocena jako `False`. Následující tabulka ukazuje, jak je určena `result`.  
  
|Pokud je `expression1`|A `expression2` je|Hodnota `result` je|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> V porovnání `Boolean` operátor `Or` vždy vyhodnocuje oba výrazy, které by mohly zahrnovat volání procedur. [Operátor OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md) provádí *krátkodobé okruhy*, což znamená, že pokud je `expression1` `True`, `expression2` není vyhodnocena.  
  
 U bitových operací operátor `Or` provádí bitové porovnání identicky umístěných bitů ve dvou numerických výrazech a nastavuje odpovídající bit v `result` podle následující tabulky.  
  
|Pokud je bit v `expression1`|A bit ve `expression2` je|Bit ve `result` je|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
> Vzhledem k tomu, že logické a bitové operátory mají nižší prioritu než jiné aritmetické a relační operátory, měly by být všechny bitové operace uzavřeny v závorkách, aby bylo zajištěno přesné provedení.  
  
## <a name="data-types"></a>Datové typy  
 Pokud se operandy skládají z jednoho `Boolean` výrazu a jednoho číselného výrazu, Visual Basic převede výraz `Boolean` na číselnou hodnotu (– 1 pro `True` a 0 pro `False`) a provede bitovou operaci.  
  
 Pro porovnání `Boolean` je datový typ výsledku `Boolean`. Pro bitové porovnání je datový typ výsledku číselný typ, který je vhodný pro datové typy `expression1` a `expression2`. Podívejte se na tabulku "relačních a bitových porovnání" v [datových typech výsledků operátoru](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="overloading"></a>Přetížení  
 Operátor `Or` lze přetížit, což znamená, že třída nebo struktura může předefinovat své *chování, pokud*má operand typ této třídy nebo struktury. Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá operátor `Or` k provedení celkové logické disjunkce dvou výrazů. Výsledkem je `Boolean` hodnota, která představuje, zda je jeden z obou výrazů `True`.  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 Předchozí příklad vytvoří výsledky `True`, `True`a `False`v uvedeném pořadí.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá operátor `Or` k provedení celkového logického disjunkce na jednotlivých bitech dvou číselných výrazů. Bit ve vzorci výsledků je nastaven, pokud je jeden z odpovídajících bitů v operandech nastaven na hodnotu 1.  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 Předchozí příklad vytvoří výsledky 10, 14 a 14 v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také:

- [Logické/bitové operátory (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operátor OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md)
- [Logické a bitové operátory v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
