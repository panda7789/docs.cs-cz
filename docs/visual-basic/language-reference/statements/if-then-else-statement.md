---
title: "If...Then...Else – příkaz (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ElseIf
- vb.Then
- vb.If
- vb.EndIf
helpviewer_keywords:
- ElseIf statement [Visual Basic], If...Then...Else
- Then statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], branching
- execution [Visual Basic], conditional
- TypeOf...Is expression, and If...Then...Else statements
- If...Then...Else statements
- If statement [Visual Basic], If...Then...Else
- If statement [Visual Basic]
- Is operator [Visual Basic], in If...Then...Else statements
- If Operator [Visual Basic]
- branching [Visual Basic], conditional
- If function [Visual Basic], and If...Then...Else statements
- Else statement [Visual Basic]
ms.assetid: 790068a2-1307-4e28-8a72-be5ebda099e9
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 898b72055345e88ca35f805de211c0c57cd74200
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ifthenelse-statement-visual-basic"></a>If...Then...Else – příkaz (Visual Basic)
Podmíněně spustí skupinu příkazů v závislosti na hodnotě výrazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
' Multiple-line syntax:  
If condition [ Then ]  
    [ statements ]  
[ ElseIf elseifcondition [ Then ]  
    [ elseifstatements ] ]  
[ Else  
    [ elsestatements ] ]  
End If  
  
' Single-line syntax:  
If condition Then [ statements ] [ Else [ elsestatements ] ]  
```  
  
## <a name="parts"></a>Součásti  
 `condition`  
 Požadováno. Výraz. Se musí vyhodnotit `True` nebo `False`, nebo na datový typ, který je implicitně převést na `Boolean`.  
  
 Pokud je ve výrazu [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` proměnné, která vyhodnotí jako [nic](../../../visual-basic/language-reference/nothing.md), podmínka je zpracován jako výraz není `True`a `Else` blok je spustit.  
  
 `Then`  
 Požadované v jednom řádku syntaxi; volitelné v syntaxi více řádků.  
  
 `statements`  
 Volitelné. Jeden nebo více následujících příkazů `If`... `Then` které jsou spouštěny, pokud `condition` vyhodnocuje `True`.  
  
 `elseifcondition`  
 Požadováno pokud `ElseIf` je k dispozici. Výraz. Se musí vyhodnotit `True` nebo `False`, nebo na datový typ, který je implicitně převést na `Boolean`.  
  
 `elseifstatements`  
 Volitelné. Jeden nebo více následujících příkazů `ElseIf`... `Then` které jsou spouštěny, pokud `elseifcondition` vyhodnocuje `True`.  
  
 `elsestatements`  
 Volitelné. Jeden nebo více příkazů, které jsou spouštěny, pokud žádné předchozí `condition` nebo `elseifcondition` výraz vyhodnocen jako `True`.  
  
 `End If`  
 Ukončí `If`... `Then`... `Else` bloku.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="multiple-line-syntax"></a>Syntaxe více řádků  
 Když `If`... `Then`... `Else` příkaz je zjistil, `condition` testování. Pokud `condition` je `True`, následující příkazy `Then` provedení. Pokud `condition` je `False`, každý `ElseIf` (pokud existují) vyhodnotí v pořadí. Když `True``elseifcondition` nenajde, příkazy hned za přidruženého `ElseIf` provedení. Pokud žádné `elseifcondition` vyhodnotí jako `True`, nebo pokud nejsou žádné `ElseIf` příkazy, následující příkazy `Else` provedení. Po provedení následující příkazy `Then`, `ElseIf`, nebo `Else`, provádění pokračuje následující příkaz `End If`.  
  
 `ElseIf` a `Else` klauzule jsou obě volitelné. Může mít jako mnoho `ElseIf` klauzule jako je vhodné `If`... `Then`... `Else` příkaz, ale ne `ElseIf` klauzule může vyskytovat po `Else` klauzule. `If`... `Then`... `Else` příkazy můžete začlenit do jiné.  
  
 V syntaxi více řádků `If` příkaz musí být jediným příkazem v prvním řádku. `ElseIf`, `Else`, A `End If` příkazy lze předcházet pouze čáry popisku. `If`... `Then`... `Else` bloku musí končit `End If` příkaz.  
  
> [!TIP]
>  [Vyberte... Příkaz případ](../../../visual-basic/language-reference/statements/select-case-statement.md) může být užitečnější, pokud vyhodnotit jeden výraz, který má několik možných hodnot.  
  
## <a name="single-line-syntax"></a>Syntaxe jednoho řádku  
 Pomocí syntaxe jeden řádek pro krátké, jednoduché testy. Syntaxe více řádků však poskytuje další strukturu a flexibilitu a je obvykle jednodušší pro čtení, údržbu a ladění.  
  
 Jaké způsobem `Then` – klíčové slovo je prověřit, abyste zjistili, zda příkaz je jeden řádek `If`. Pokud jakoukoli jinou hodnotu než komentář se zobrazí po `Then` na stejném řádku příkaz považován za jeden řádek `If` příkaz. Pokud `Then` chybí, musí být spuštění více řádků `If`... `Then`... `Else`.  
  
 V syntaxi jeden řádek, může mít více příkazů provést v důsledku `If`... `Then` rozhodnutí. Všechny příkazy musí být na stejném řádku a být oddělené dvojtečkou.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje použití syntaxe více řádků `If`... `Then`... `Else` příkaz.  
  
 [!code-vb[VbVbalrStatements#101](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_1.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje vnořené `If`... `Then`... `Else` příkazy.  
  
 [!code-vb[VbVbalrStatements#102](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_2.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje použití syntaxe jeden řádek.  
  
 [!code-vb[VbVbalrStatements#103](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_3.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A>  
 <xref:Microsoft.VisualBasic.Interaction.Switch%2A>  
 [#If... Then... #Else – direktivy](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Vyberte... Case – příkaz](../../../visual-basic/language-reference/statements/select-case-statement.md)  
 [Vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Rozhodovací struktury](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [Logické a bitové operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [Pokud operátor](../../../visual-basic/language-reference/operators/if-operator.md)
