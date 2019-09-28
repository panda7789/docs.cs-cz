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
ms.openlocfilehash: bd6ebbf5f53a7cf187b5d8ce7630080d44d46df2
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591619"
---
# <a name="and-operator-visual-basic"></a>And – operátor (Visual Basic)
Provede logickou kombinaci dvou `Boolean` výrazů nebo bitové spojení dvou numerických výrazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
result = expression1 And expression2  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Povinný parametr. Libovolný `Boolean` nebo číselný výraz. Pro logické porovnání `result` je logické spojení dvou hodnot `Boolean`. U bitových operací je `result` číselná hodnota představující bitovou kombinaci dvou číselných bitových vzorů.  
  
 `expression1`  
 Povinný parametr. Libovolný `Boolean` nebo číselný výraz.  
  
 `expression2`  
 Povinný parametr. Libovolný `Boolean` nebo číselný výraz.  
  
## <a name="remarks"></a>Poznámky  
 V případě logického porovnání je `result` `True`, pokud je hodnota `expression1` a `expression2` vyhodnocena jako `True`. Následující tabulka ukazuje, jak je určena `result`.  
  
|Pokud `expression1` je|A `expression2` je|Hodnota `result` je|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> V logickém porovnání operátor `And` vždy vyhodnocuje oba výrazy, které by mohly zahrnovat volání procedur. [Operátor AndAlso –](../../../visual-basic/language-reference/operators/andalso-operator.md) provádí *krátkodobé okruhy*, což znamená, že pokud `expression1` je `False`, pak `expression2` se nevyhodnotí.  
  
 Při použití na číselné hodnoty provede operátor `And` bitové porovnání identicky umístěných bitů ve dvou numerických výrazech a nastaví odpovídající bit v `result` podle následující tabulky.  
  
|If bit v `expression1` je|A bit v `expression2` je|Bit v `result` je|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
|0|0|0|  
  
> [!NOTE]
> Vzhledem k tomu, že logické a bitové operátory mají nižší prioritu než jiné aritmetické a relační operátory, měly by být všechny bitové operace uzavřeny v závorkách, aby se zajistily přesné výsledky.  
  
## <a name="data-types"></a>Datové typy  
 Pokud se operandy skládají z jednoho `Boolean` a jednoho číselného výrazu, Visual Basic převede výraz `Boolean` na číselnou hodnotu (– 1 pro `True` a 0 pro `False`) a provede bitovou operaci.  
  
 Pro porovnání typu Boolean je datový typ výsledku `Boolean`. Pro bitové porovnání je datový typ výsledku číselný typ, který je vhodný pro datové typy `expression1` a `expression2`. Podívejte se na tabulku "relačních a bitových porovnání" v [datových typech výsledků operátoru](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
> [!NOTE]
> Operátor `And` lze přetížit, což znamená, že třída nebo struktura může předefinovat *chování, pokud*operand má typ této třídy nebo struktury. Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá operátor `And` k provedení logického spojení se dvěma výrazy. Výsledkem je hodnota @no__t 0, která představuje, zda jsou oba výrazy `True`.  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 Předchozí příklad vytvoří výsledky `True` a `False` v uvedeném pořadí.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá operátor `And` k provedení logického spojení na jednotlivých bitech dvou číselných výrazů. Bit ve vzorci výsledků je nastaven, pokud jsou odpovídající bity v operandech nastaveny na hodnotu 1.  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 Předchozí příklad vytvoří výsledky 8, 2 a 0 v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také:

- [Logické/bitové operátory (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operátor AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md)
- [Logické a bitové operátory v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
