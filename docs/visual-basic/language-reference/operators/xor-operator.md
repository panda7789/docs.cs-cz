---
title: Xor – operátor
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
ms.openlocfilehash: 999050314d674fa98833083d84796e471c22971d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406337"
---
# <a name="xor-operator-visual-basic"></a>Xor – operátor (Visual Basic)
Provede logické vyloučení dvou `Boolean` výrazů nebo bitové vyloučení dvou numerických výrazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Povinná hodnota. Jakákoli `Boolean` nebo číselná proměnná. Pro logické porovnání `result` je logické vyloučení (exkluzivní logická disjunkce) dvou `Boolean` hodnot. U bitových operací `result` je číselná hodnota, která představuje bitové vyloučení (exkluzivní bitovou disjunkci) dvou číselných bitových vzorů.  
  
 `expression1`  
 Povinná hodnota. Libovolný `Boolean` nebo numerický výraz.  
  
 `expression2`  
 Povinná hodnota. Libovolný `Boolean` nebo numerický výraz.  
  
## <a name="remarks"></a>Poznámky  
 Pro logické porovnání `result` je `True` if a pouze, pokud je přesně jeden z `expression1` a `expression2` vyhodnocen jako `True` . To znamená, že pokud a `expression1` `expression2` vyhodnotí na opačné `Boolean` hodnoty. Následující tabulka ukazuje, jak `result` je určena.  
  
|Pokud `expression1` je|A `expression2` je|Hodnota `result` je|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> V porovnání s logickou hodnotou `Xor` operátor vždy vyhodnocuje oba výrazy, které by mohly zahrnovat volání procedur. Neexistují žádné krátkodobé protějšky k `Xor` , protože výsledek vždy závisí na obou operandech. Pro logické operátory *krátkodobého okruhu* , viz [operátor AndAlso –](andalso-operator.md) a [operátor OrElse](orelse-operator.md).  
  
 U bitových operací `Xor` operátor provádí bitové porovnání identicky umístěných bitů ve dvou numerických výrazech a nastavuje odpovídající bit v `result` závislosti na následující tabulce.  
  
|Pokud je bit v `expression1`|A bit v `expression2` je|Bit v `result` je|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|0|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
> Vzhledem k tomu, že logické a bitové operátory mají nižší prioritu než jiné aritmetické a relační operátory, měly by být všechny bitové operace uzavřeny v závorkách, aby bylo zajištěno přesné provedení.  
  
 Například 5 `Xor` 3 je 6. Chcete-li zjistit, proč je to tak, převeďte 5 a 3 na jejich binární reprezentace, 101 a 011. Pak pomocí předchozí tabulky určete, že 101 XOR 011 je 110, což je binární reprezentace desítkového čísla 6.  
  
## <a name="data-types"></a>Typy dat  
 Pokud se operandy skládají z jednoho `Boolean` výrazu a jednoho číselného výrazu, Visual Basic převede `Boolean` výraz na číselnou hodnotu (– 1 pro `True` a 0 pro `False` ) a provede bitovou operaci.  
  
 Pro `Boolean` porovnání je datový typ výsledku `Boolean` . Pro bitové porovnání je výsledný datový typ číselný typ vhodný pro datové typy `expression1` a `expression2` . Podívejte se na tabulku "relačních a bitových porovnání" v [datových typech výsledků operátoru](data-types-of-operator-results.md).  
  
## <a name="overloading"></a>Přetížení  
 `Xor`Operátor může být *přetížen*, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury. Pokud váš kód používá tento operátor v takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Xor` operátor k provedení logického vyloučení (exkluzivní logická disjunkce) na dvou výrazech. Výsledkem je `Boolean` hodnota, která představuje, zda je přesně jeden z výrazů `True` .  
  
 [!code-vb[VbVbalrOperators#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#40)]  
  
 Předchozí příklad vytvoří výsledky `False` , a v `True` `False` uvedeném pořadí.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Xor` operátor k provedení logického vyloučení (exkluzivní logická disjunkce) na jednotlivých bitech dvou číselných výrazů. Bit ve vzorci výsledků je nastaven, pokud je přesně jeden z odpovídajících bitů v operandech nastaven na hodnotu 1.  
  
 [!code-vb[VbVbalrOperators#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#41)]  
  
 Předchozí příklad vytvoří výsledky 2, 12 a 14 v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také

- [Logické/bitové operátory (Visual Basic)](logical-bitwise-operators.md)
- [Priorita operátorů v jazyce Visual Basic](operator-precedence.md)
- [Operátory uvedené podle funkce](operators-listed-by-functionality.md)
- [Logické a bitové operátory v jazyce Visual Basic](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
