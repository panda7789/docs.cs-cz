---
title: "If – operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c553da5abf5453ba881671806b976125355c1e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="if-operator-visual-basic"></a>If – operátor (Visual Basic)
Používá krátká smyčka – vyhodnocení podmíněně vrací jednu ze dvou hodnot. `If` Operátor lze volat tři argumenty nebo s dva argumenty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
If( [argument1,] argument2, argument3 )  
```  
  
## <a name="if-operator-called-with-three-arguments"></a>Pokud operátor volána s tři argumenty  
 Když `If` nazývá pomocí tři argumenty první argument se musí vyhodnotit na hodnotu, kterou lze převést jako `Boolean`. Aby `Boolean` hodnota určí, který dva argumenty je vyhodnocena a vrátil. V následujícím seznamu platí pouze tehdy, když `If` operátor nazývá pomocí tři argumenty.  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`argument1`|Požadováno. `Boolean`. Určuje, které další argumenty, které mají vyhodnotit a vrátit.|  
|`argument2`|Požadováno. `Object`. Vyhodnotí a vrácené v případě `argument1` vyhodnocuje `True`.|  
|`argument3`|Požadováno. `Object`. Vyhodnotí a vrácené v případě `argument1` vyhodnotí jako `False` nebo, pokud `argument1` je [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` proměnné, která vyhodnotí jako [nic](../../../visual-basic/language-reference/nothing.md).|  
  
 `If` Operátor, který je volán s tři argumenty funguje jako `IIf` funkce s tím rozdílem, že používá krátká smyčka – vyhodnocení. `IIf` Funkce vždy vyhodnotí všechny tři argumenty, zatímco `If` operátor, který má tři argumenty vyhodnotí pouze dvě z nich. První `If` vyhodnocování argumentu a výsledek je převedená `Boolean` hodnotu, `True` nebo `False`. Pokud je hodnota `True`, `argument2` je vyhodnocena a jeho hodnota se vrátí, ale `argument3` , nebude hodnocen. Pokud hodnota `Boolean` výraz je `False`, `argument3` je vyhodnocena a jeho hodnota se vrátí, ale `argument2` , nebude hodnocen. Následující příklady ilustrují použití `If` při použití tři argumenty:  
  
 [!code-vb[VbVbalrOperators#100](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_1.vb)]  
  
 Následující příklad ilustruje hodnotu krátká smyčka – vyhodnocení. Tento příklad ukazuje dva pokusy o rozdělení proměnná `number` proměnnou `divisor` s výjimkou při `divisor` je nulová. V takovém případě má být vrácen 0 a žádné by měl být pokusu provést rozdělení, protože by došlo k chybě spuštění. Protože `If` výraz používá krátká smyčka – vyhodnocení, vyhodnocuje druhý nebo třetí argument, v závislosti na hodnotě prvního argumentu. Je-li první argument hodnotu true, dělitel není nula a bezpečně vyhodnotit druhý argument a provádět rozdělení. Pokud první argument hodnotu false, pouze třetí argument je vyhodnocena a vrátí hodnotu 0. Proto pokud dělitel je 0, žádné pokus se uskuteční k provádění rozdělení a žádné výsledky chyby. Ale protože `IIf` nepoužívá krátká smyčka – vyhodnocení, druhý argument je vyhodnocena i v případě, že první argument je hodnota false. To způsobí, že ke spuštění chybě dělení nulou.  
  
 [!code-vb[VbVbalrOperators#101](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_2.vb)]  
  
## <a name="if-operator-called-with-two-arguments"></a>Pokud operátor volána s dva argumenty  
 První argument `If` lze vynechat. To umožňuje operátorovi volat pomocí pouze dva argumenty. V následujícím seznamu platí pouze tehdy, když `If` operátor je volán s dva argumenty.  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`argument2`|Požadováno. `Object`. Musí být odkaz nebo typ s možnou hodnotou Null. Vyhodnocení a vrátí vyhodnocení na nic jiné než `Nothing`.|  
|`argument3`|Požadováno. `Object`. Vyhodnotí a vrácené v případě `argument2` vyhodnocuje `Nothing`.|  
  
 Když `Boolean` je tento argument vynechán, první argument musí být odkaz nebo typ s možnou hodnotou Null. Pokud se vyhodnotí jako první argument `Nothing`, je vrácena hodnota druhý argument. Ve všech ostatních případech je vrácena hodnota prvního argumentu. Následující příklad ilustruje, jak toto testování funguje.  
  
 [!code-vb[VbVbalrOperators#102](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_3.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Interaction.IIf%2A>  
 [Typy hodnot s povolenou hodnotou Null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [Nic](../../../visual-basic/language-reference/nothing.md)
