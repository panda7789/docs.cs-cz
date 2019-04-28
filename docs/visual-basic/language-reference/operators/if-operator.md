---
title: If – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.IfOperator
- IfOperator
helpviewer_keywords:
- ternary operators [Visual Basic]
- conditional execution
- If expressions [Visual Basic]
- conditional operator [Visual Basic]
- If Operator [Visual Basic]
ms.assetid: dd56c9df-7cd4-442c-9ba6-20c70ee44c8f
ms.openlocfilehash: 9ab01755d75c91ce87acf83e7f406b26c466aef6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663502"
---
# <a name="if-operator-visual-basic"></a>If – operátor (Visual Basic)
Použití krátká smyčka – vyhodnocení podmíněně vrací jednu ze dvou hodnot. `If` Operátor může být volána, s třemi argumenty nebo dva argumenty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
If( [argument1,] argument2, argument3 )  
```  
  
## <a name="if-operator-called-with-three-arguments"></a>Je-li volat operátor tří argumentů  
 Když `If` je volána pomocí tří argumentů první argument se musí vyhodnotit na hodnotu, která můžete přetypovat jako `Boolean`. Že `Boolean` hodnota se určí, které ze dvou argumentů je vyhodnocena a vrátila. Následující seznam platí pouze tehdy, když `If` operátor je volána za použití tři argumenty.  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`argument1`|Povinný parametr. `Boolean`. Určuje, které další argumenty, které mají vyhodnotí a vrátí.|  
|`argument2`|Povinný parametr. `Object`. Pokud vyhodnocený a vrátilo `argument1` vyhodnotí jako `True`.|  
|`argument3`|Povinný parametr. `Object`. Vyhodnocený a vrácené v případě `argument1` vyhodnotí jako `False` nebo, pokud `argument1` je [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` proměnné, která se vyhodnotí jako [nic](../../../visual-basic/language-reference/nothing.md).|  
  
 `If` Operátor, který se nazývá tří argumentů funguje jako `IIf` funkce s tím rozdílem, že používá krátká smyčka – vyhodnocení. `IIf` Funkce vždy vyhodnotí všechny tři argumenty, že `If` pouze dva z nich vyhodnotí operátor, který má tři argumenty. První `If` argument je vyhodnocen a výsledek je typovaná jako `Boolean` hodnotu `True` nebo `False`. Pokud je hodnota `True`, `argument2` je vyhodnocen a její hodnota se vrátí, ale `argument3` , nebude hodnocen. Pokud hodnota `Boolean` výraz je `False`, `argument3` je vyhodnocen a její hodnota se vrátí, ale `argument2` , nebude hodnocen. Následující příklady ilustrují použití `If` při použití tři argumenty:  
  
 [!code-vb[VbVbalrOperators#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#100)]  
  
 Následující příklad ukazuje hodnotu krátká smyčka – vyhodnocení. Příklad ukazuje dva pokusy o rozdělení proměnné `number` proměnnou `divisor` s výjimkou, kdy `divisor` je nula. V takovém případě by měl vrátit hodnotu 0 a by měl být proveden žádný pokus o provést rozdělení, protože by výsledkem chyba za běhu. Vzhledem k tomu, `If` výraz používá krátká smyčka – vyhodnocení, je vyhodnocen jako druhý nebo třetí argument, v závislosti na hodnotě prvního argumentu. Pokud první argument hodnotu true, dělitel není nula a bezpečně vyhodnotit druhý argument a provádět dělení. Pokud první argument hodnotu false, vyhodnotí se pouze třetí argument a vrátí hodnotu 0. Proto když dělitel je 0, je proveden žádný pokus o provádět dělení a chyba se žádné výsledky. Ale protože `IIf` nepoužívá krátká smyčka – vyhodnocení, i když je první argument hodnotu false, vyhodnotí se druhý argument. To způsobí chybu za běhu dělení nulou.  
  
 [!code-vb[VbVbalrOperators#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#101)]  
  
## <a name="if-operator-called-with-two-arguments"></a>Pokud operátor volat se dvěma argumenty.  
 První argument `If` lze vynechat. To umožňuje operátor má být volána za použití pouze dva argumenty. Následující seznam platí pouze tehdy, když `If` operátor se nazývá se dvěma argumenty.  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`argument2`|Povinný parametr. `Object`. Musí být typu odkaz nebo typ připouštějící hodnotu Null. Vyhodnotí a vrátí, když je vyhodnocen jako cokoli jiného než `Nothing`.|  
|`argument3`|Povinný parametr. `Object`. Pokud vyhodnocený a vrátilo `argument2` vyhodnotí jako `Nothing`.|  
  
 Když `Boolean` je tento argument vynechán, první argument musí být odkaz nebo typ připouštějící hodnotu Null. Pokud je vyhodnocen jako první argument `Nothing`, je vrácena hodnota druhý argument. Ve všech ostatních případech vrátí se hodnota prvního argumentu. Následující příklad ukazuje, jak toto vyhodnocení funguje.  
  
 [!code-vb[VbVbalrOperators#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#102)]  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Interaction.IIf%2A>
- [Typy hodnot s povolenou hodnotou Null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Nothing](../../../visual-basic/language-reference/nothing.md)
