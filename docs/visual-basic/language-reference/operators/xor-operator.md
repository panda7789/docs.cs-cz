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
ms.openlocfilehash: d82018a3018e2cf4362b9904ed127c20f56f6f0c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701275"
---
# <a name="xor-operator-visual-basic"></a>Xor – operátor (Visual Basic)
Provede logické vyloučení dvou `Boolean` výrazů nebo bitové vyloučení dvou numerických výrazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Požadováno. Jakákoli `Boolean` nebo číselná proměnná. Pro logické porovnání je `result` logické vyloučení (exkluzivní logická disjunkce) dvou hodnot `Boolean`. U bitových operací je `result` číselná hodnota, která představuje bitové vyloučení (exkluzivní bitovou disjunkci) dvou číselných bitových vzorů.  
  
 `expression1`  
 Požadováno. Libovolný `Boolean` nebo číselný výraz.  
  
 `expression2`  
 Požadováno. Libovolný `Boolean` nebo číselný výraz.  
  
## <a name="remarks"></a>Poznámky  
 Pro účely logického porovnání je `result` `True`, pokud je přesně jedna z `expression1` a `expression2` vyhodnocena jako `True`. To znamená, že pokud a pouze pokud `expression1` a `expression2` vyhodnoceny na opak `Boolean` hodnoty. Následující tabulka ukazuje, jak je určena `result`.  
  
|Pokud je `expression1`|A `expression2` je|Hodnota `result` je|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> V porovnání s logickou hodnotou operátor `Xor` vždy vyhodnocuje oba výrazy, které by mohly zahrnovat volání procedur. Neexistují žádné krátkodobé protějšky, které by bylo možné `Xor`, protože výsledek vždy závisí na obou operandech. Pro logické operátory *krátkodobého okruhu* , viz [operátor AndAlso –](../../../visual-basic/language-reference/operators/andalso-operator.md) a [operátor OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md).  
  
 U bitových operací operátor `Xor` provádí bitové porovnání identicky umístěných bitů ve dvou numerických výrazech a nastavuje odpovídající bit v `result` podle následující tabulky.  
  
|Pokud je bit v `expression1`|A bit ve `expression2` je|Bit ve `result` je|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|0|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
> Vzhledem k tomu, že logické a bitové operátory mají nižší prioritu než jiné aritmetické a relační operátory, měly by být všechny bitové operace uzavřeny v závorkách, aby bylo zajištěno přesné provedení.  
  
 Například 5 `Xor` 3 je 6. Chcete-li zjistit, proč je to tak, převeďte 5 a 3 na jejich binární reprezentace, 101 a 011. Pak pomocí předchozí tabulky určete, že 101 XOR 011 je 110, což je binární reprezentace desítkového čísla 6.  
  
## <a name="data-types"></a>Datové typy  
 Pokud se operandy skládají z jednoho `Boolean` výrazu a jednoho číselného výrazu, Visual Basic převede výraz `Boolean` na číselnou hodnotu (– 1 pro `True` a 0 pro `False`) a provede bitovou operaci.  
  
 Pro porovnání `Boolean` je datový typ výsledku `Boolean`. Pro bitové porovnání je datový typ výsledku číselný typ, který je vhodný pro datové typy `expression1` a `expression2`. Podívejte se na tabulku "relačních a bitových porovnání" v [datových typech výsledků operátoru](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="overloading"></a>Přetížení  
 Operátor `Xor` lze přetížit, což znamená, že třída nebo struktura může předefinovat své *chování, pokud*má operand typ této třídy nebo struktury. Pokud váš kód používá tento operátor v takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá operátor `Xor` k provedení logického vyloučení (exkluzivní logická disjunkce) na dvou výrazech. Výsledkem je `Boolean` hodnota, která představuje, zda je právě jeden z výrazů `True`.  
  
 [!code-vb[VbVbalrOperators#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#40)]  
  
 Předchozí příklad vytvoří výsledky `False`, `True`a `False`v uvedeném pořadí.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá operátor `Xor` k provedení logického vyloučení (exkluzivní logická disjunkce) na jednotlivých bitech dvou číselných výrazů. Bit ve vzorci výsledků je nastaven, pokud je přesně jeden z odpovídajících bitů v operandech nastaven na hodnotu 1.  
  
 [!code-vb[VbVbalrOperators#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#41)]  
  
 Předchozí příklad vytvoří výsledky 2, 12 a 14 v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také:

- [Logické/bitové operátory (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Logické a bitové operátory v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
