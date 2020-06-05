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
ms.openlocfilehash: c2b135d27e14816c011a4f70793543aa835d960a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371944"
---
# <a name="and-operator-visual-basic"></a>And – operátor (Visual Basic)
Provede logickou kombinaci dvou `Boolean` výrazů nebo bitové spojení dvou numerických výrazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
result = expression1 And expression2  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Povinná hodnota. Libovolný `Boolean` nebo numerický výraz. Pro logické porovnání `result` je logické spojení dvou `Boolean` hodnot. U bitových operací `result` je číselná hodnota představující bitovou kombinaci dvou číselných bitových vzorů.  
  
 `expression1`  
 Povinná hodnota. Libovolný `Boolean` nebo numerický výraz.  
  
 `expression2`  
 Povinná hodnota. Libovolný `Boolean` nebo numerický výraz.  
  
## <a name="remarks"></a>Poznámky  
 Pro logické porovnání `result` je `True` if a jenom v případě, že `expression1` a `expression2` vyhodnocuje `True` . Následující tabulka ukazuje, jak `result` je určena.  
  
|Pokud `expression1` je|A `expression2` je|Hodnota `result` je|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> V porovnání s logickou hodnotou `And` operátor vždy vyhodnocuje oba výrazy, které by mohly zahrnovat volání procedur. [Operátor AndAlso –](andalso-operator.md) provádí *krátkodobé okruhy*, což znamená, že pokud `expression1` je `False` , pak není `expression2` vyhodnocen.  
  
 Při použití na číselné hodnoty používá `And` operátor bitové porovnání identicky umístěných bitů ve dvou numerických výrazech a nastaví odpovídající bit v `result` závislosti na následující tabulce.  
  
|Pokud je bit v `expression1`|A bit v `expression2` je|Bit v `result` je|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
|0|0|0|  
  
> [!NOTE]
> Vzhledem k tomu, že logické a bitové operátory mají nižší prioritu než jiné aritmetické a relační operátory, měly by být všechny bitové operace uzavřeny v závorkách, aby se zajistily přesné výsledky.  
  
## <a name="data-types"></a>Typy dat  
 Pokud se operandy skládají z jednoho `Boolean` výrazu a jednoho číselného výrazu, Visual Basic převede `Boolean` výraz na číselnou hodnotu (– 1 pro `True` a 0 pro `False` ) a provede bitovou operaci.  
  
 Pro logické porovnání je datový typ výsledku `Boolean` . Pro bitové porovnání je výsledný datový typ číselný typ vhodný pro datové typy `expression1` a `expression2` . Podívejte se na tabulku "relačních a bitových porovnání" v [datových typech výsledků operátoru](data-types-of-operator-results.md).  
  
> [!NOTE]
> `And`Operátor může být *přetížen*, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury. Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `And` operátor k provedení logického spojení se dvěma výrazy. Výsledkem je `Boolean` hodnota, která představuje, zda jsou oba výrazy `True` .  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 Předchozí příklad vytvoří výsledky a v `True` `False` uvedeném pořadí.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `And` operátor k provedení logického spojení na jednotlivých bitech dvou číselných výrazů. Bit ve vzorci výsledků je nastaven, pokud jsou odpovídající bity v operandech nastaveny na hodnotu 1.  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 Předchozí příklad vytvoří výsledky 8, 2 a 0 v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také

- [Logické/bitové operátory (Visual Basic)](logical-bitwise-operators.md)
- [Priorita operátorů v jazyce Visual Basic](operator-precedence.md)
- [Operátory uvedené podle funkce](operators-listed-by-functionality.md)
- [AndAlso – operátor](andalso-operator.md)
- [Logické a bitové operátory v jazyce Visual Basic](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
