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
ms.openlocfilehash: 244c0598c65ba691decc09c36293799571211a40
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701158"
---
# <a name="if-operator-visual-basic"></a>If – operátor (Visual Basic)
Nástroj používá k podmíněnému vrácení jedné ze dvou hodnot hodnocení krátkodobého okruhu. Operátor `If` lze volat se třemi argumenty nebo dvěma argumenty.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
If( [argument1,] argument2, argument3 )  
```  
  
## <a name="if-operator-called-with-three-arguments"></a>If volal operátor se třemi argumenty  
 Když je `If` volána pomocí tří argumentů, první argument musí být vyhodnocen na hodnotu, která může být převedena jako `Boolean`. Hodnota `Boolean` určí, který z dalších dvou argumentů bude vyhodnocen a vrácen. Následující seznam platí pouze v případě, že je operátor `If` volán pomocí tří argumentů.  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`argument1`|Požadováno. `Boolean`. Určuje, který z dalších argumentů má být vyhodnocen a vrácen.|  
|`argument2`|Požadováno. `Object`. Vyhodnoceno a vráceno, pokud `argument1` se vyhodnotí jako `True`.|  
|`argument3`|Požadováno. `Object`. Vyhodnoceno a vráceno, pokud `argument1` se vyhodnotí jako `False` nebo pokud `argument1` je proměnná s [možnou @no__t hodnotou null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md), která je vyhodnocena jako [Nothing](../../../visual-basic/language-reference/nothing.md).|  
  
 Operátor `If`, který se volá se třemi argumenty, funguje jako funkce `IIf` s tím rozdílem, že používá vyhodnocování krátkých okruhů. Funkce `IIf` vždy vyhodnocuje všechny tři argumenty, zatímco operátor `If`, který má tři argumenty, vyhodnocuje pouze dva z nich. Vyhodnotí se první argument `If` a výsledek se přetypování jako hodnota `Boolean`, `True` nebo `False`. Pokud je hodnota `True`, vyhodnotí se `argument2` a vrátí se její hodnota, ale `argument3` se nevyhodnotí. Pokud je hodnota výrazu `Boolean` `False`, vyhodnotí `argument3` a vrátí se jeho hodnota, ale `argument2` není vyhodnocena. Následující příklady ilustrují použití `If`, když se používají tři argumenty:  
  
 [!code-vb[VbVbalrOperators#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#100)]  
  
 Následující příklad znázorňuje hodnotu vyhodnocování krátkodobého okruhu. Příklad ukazuje dva pokusy o dělení proměnné `number` podle proměnné `divisor` s výjimkou, kdy je hodnota `divisor` nulová. V takovém případě by měl být vrácen 0 a žádný pokus o provedení dělení, protože by došlo k chybě za běhu. Vzhledem k tomu, že výraz `If` používá vyhodnocování krátkých okruhů, vyhodnocuje buď druhý, nebo třetí argument v závislosti na hodnotě prvního argumentu. Pokud je první argument true, dělitel není nula a je bezpečné vyhodnotit druhý argument a provést dělení. Pokud je první argument false, je vyhodnocen pouze třetí argument a je vrácena hodnota 0. Proto pokud je dělitel 0, není proveden žádný pokus o provedení dělení a žádné výsledky chyby. Vzhledem k tomu, že `IIf` nepoužívá vyhodnocování krátkých okruhů, je druhý argument vyhodnocen i v případě, že je první argument nepravdivý. Tím dojde k chybě dělení nulou v době běhu.  
  
 [!code-vb[VbVbalrOperators#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#101)]  
  
## <a name="if-operator-called-with-two-arguments"></a>If volal operátor se dvěma argumenty  
 První argument `If` lze vynechat. To umožňuje operátorovi zavolat pouze pomocí dvou argumentů. Následující seznam platí pouze v případě, že je volán operátor `If` se dvěma argumenty.  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`argument2`|Požadováno. `Object`. Musí se jednat o odkaz nebo typ s možnou hodnotou null. Vyhodnoceno a vráceno, když se vyhodnotí jako cokoli jiného než `Nothing`.|  
|`argument3`|Požadováno. `Object`. Vyhodnoceno a vráceno, pokud `argument2` se vyhodnotí jako `Nothing`.|  
  
 Při vynechání argumentu `Boolean` musí být prvním argumentem odkaz nebo typ s možnou hodnotou null. Pokud je první argument vyhodnocen jako `Nothing`, vrátí se hodnota druhého argumentu. Ve všech ostatních případech je vrácena hodnota prvního argumentu. Následující příklad znázorňuje, jak Toto vyhodnocení funguje.  
  
 [!code-vb[VbVbalrOperators#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#102)]  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Interaction.IIf%2A>
- [Typy hodnot s povolenou hodnotou Null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Nothing](../../../visual-basic/language-reference/nothing.md)
