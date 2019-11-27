---
title: And – operátor
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
ms.openlocfilehash: 78a65843a449bd15d5615710e1685f40d94c37f7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350258"
---
# <a name="and-operator-visual-basic"></a>And – operátor (Visual Basic)
Provede logickou kombinaci dvou `Boolean` výrazů nebo bitové spojení dvou numerických výrazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
result = expression1 And expression2  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Požadováno. Libovolný `Boolean` nebo číselný výraz. Pro logické porovnání je `result` logické spojení dvou hodnot `Boolean`. V případě bitových operací je `result` číselnou hodnotou reprezentující bitové spojení dvou číselných bitových vzorů.  
  
 `expression1`  
 Požadováno. Libovolný `Boolean` nebo číselný výraz.  
  
 `expression2`  
 Požadováno. Libovolný `Boolean` nebo číselný výraz.  
  
## <a name="remarks"></a>Poznámky  
 Pro logické porovnání je `result` `True` pouze v případě, že `expression1` i `expression2` vyhodnoceny jako `True`. Následující tabulka ukazuje, jak je určena `result`.  
  
|Pokud je `expression1`|A `expression2` je|Hodnota `result` je|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> V porovnání s logickou hodnotou operátor `And` vždy vyhodnocuje oba výrazy, které by mohly zahrnovat volání procedur. [Operátor AndAlso –](../../../visual-basic/language-reference/operators/andalso-operator.md) provádí *krátkodobé okruhy*, což znamená, že pokud je `expression1` `False`, `expression2` není vyhodnocena.  
  
 Při použití na číselné hodnoty, operátor `And` provádí bitové porovnání identicky umístěných bitů ve dvou numerických výrazech a nastaví odpovídající bit v `result` podle následující tabulky.  
  
|Pokud je bit v `expression1`|A bit ve `expression2` je|Bit ve `result` je|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
|0|0|0|  
  
> [!NOTE]
> Vzhledem k tomu, že logické a bitové operátory mají nižší prioritu než jiné aritmetické a relační operátory, měly by být všechny bitové operace uzavřeny v závorkách, aby se zajistily přesné výsledky.  
  
## <a name="data-types"></a>Datové typy  
 Pokud se operandy skládají z jednoho `Boolean` výrazu a jednoho číselného výrazu, Visual Basic převede výraz `Boolean` na číselnou hodnotu (– 1 pro `True` a 0 pro `False`) a provede bitovou operaci.  
  
 Pro logické porovnání je datový typ výsledku `Boolean`. Pro bitové porovnání je datový typ výsledku číselný typ, který je vhodný pro datové typy `expression1` a `expression2`. Podívejte se na tabulku "relačních a bitových porovnání" v [datových typech výsledků operátoru](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
> [!NOTE]
> Operátor `And` lze přetížit, což znamená, že třída nebo struktura může předefinovat své *chování, pokud*má operand typ této třídy nebo struktury. Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá operátor `And` k provedení logického spojení se dvěma výrazy. Výsledkem je `Boolean` hodnota, která představuje, zda jsou oba výrazy `True`.  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 Předchozí příklad vytvoří výsledky `True` a `False`v uvedeném pořadí.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá operátor `And` k provádění logických spojení na jednotlivých bitech dvou číselných výrazů. Bit ve vzorci výsledků je nastaven, pokud jsou odpovídající bity v operandech nastaveny na hodnotu 1.  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 Předchozí příklad vytvoří výsledky 8, 2 a 0 v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také:

- [Logické/bitové operátory (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operátor AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md)
- [Logické a bitové operátory v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
