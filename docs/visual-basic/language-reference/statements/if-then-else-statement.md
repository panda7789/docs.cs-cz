---
title: If...Then...Else – příkaz (Visual Basic)
ms.date: 04/16/2018
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
ms.openlocfilehash: 08d51326ee0c9f91eec02467ebcb116354b5033f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ifthenelse-statement-visual-basic"></a>If...Then...Else – příkaz (Visual Basic)
Podmíněně spustí skupinu příkazů v závislosti na hodnotě výrazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
' Multiline syntax:  
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

## <a name="quick-links-to-example-code"></a>Rychlé odkazy na ukázkový kód

Tento článek obsahuje několik příkladů, které ilustrují použití `If`... `Then`... `Else` příkaz:

* [Příklad Víceřádkový syntaxe](#multi-line)
* [Příklad vnořené syntaxe](#nested)
* [Příklad syntaxe jeden řádek](#single-line)

## <a name="parts"></a>Součásti  
 `condition`  
 Požadováno. Výraz. Se musí vyhodnotit `True` nebo `False`, nebo na datový typ, který je implicitně převést na `Boolean`.  
  
 Pokud je ve výrazu [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` proměnné, která vyhodnotí jako [nic](../../../visual-basic/language-reference/nothing.md), podmínka je zpracován jako výraz `False` a `Else` bloku se spustí.  
  
 `Then`  
 Požadované v jednom řádku syntaxi; volitelné v Víceřádkový syntaxi.  
  
 `statements`  
 Volitelné. Jeden nebo více následujících příkazů `If`... `Then` které jsou spouštěny, pokud `condition` vyhodnocuje `True`.  
  
 `elseifcondition`  
 Požadováno pokud `ElseIf` je k dispozici. Výraz. Se musí vyhodnotit `True` nebo `False`, nebo na datový typ, který je implicitně převést na `Boolean`.  
  
 `elseifstatements`  
 Volitelné. Jeden nebo více následujících příkazů `ElseIf`... `Then` které jsou spouštěny, pokud `elseifcondition` vyhodnocuje `True`.  
  
 `elsestatements`  
 Volitelné. Jeden nebo více příkazů, které jsou spouštěny, pokud žádné předchozí `condition` nebo `elseifcondition` výraz vyhodnocen jako `True`.  
  
 `End If`  
 Ukončí Víceřádkový verzi `If`... `Then`... `Else` bloku.  
  
## <a name="remarks"></a>Poznámky  
  
### <a name="multiline-syntax"></a>Víceřádkový syntaxe  
 Když `If`... `Then`... `Else` příkaz je zjistil, `condition` testování. Pokud `condition` je `True`, následující příkazy `Then` provedení. Pokud `condition` je `False`, každý `ElseIf` (pokud existují) vyhodnotí v pořadí. Když `True` `elseifcondition` nenajde, příkazy hned za přidruženého `ElseIf` provedení. Pokud žádné `elseifcondition` vyhodnotí jako `True`, nebo pokud nejsou žádné `ElseIf` příkazy, následující příkazy `Else` provedení. Po provedení následující příkazy `Then`, `ElseIf`, nebo `Else`, provádění pokračuje následující příkaz `End If`.  
  
 `ElseIf` a `Else` klauzule jsou obě volitelné. Může mít jako mnoho `ElseIf` klauzule jako je vhodné `If`... `Then`... `Else` příkaz, ale ne `ElseIf` klauzule může vyskytovat po `Else` klauzule. `If`... `Then`... `Else` příkazy můžete začlenit do jiné.  
  
 Víceřádkový syntaxe `If` příkaz musí být jediným příkazem v prvním řádku. `ElseIf`, `Else`, A `End If` příkazy lze předcházet pouze čáry popisku. `If`... `Then`... `Else` bloku musí končit `End If` příkaz.  
  
> [!TIP]
>  [Vyberte... Příkaz případ](../../../visual-basic/language-reference/statements/select-case-statement.md) může být užitečnější, pokud vyhodnotit jeden výraz, který má několik možných hodnot.  
  
### <a name="single-line-syntax"></a>Syntaxe jednoho řádku  
 Jeden řádek syntaxe pro jednu podmínku s kódem vám pomůže spustit, pokud to není pravda. Syntaxe více řádků však poskytuje další strukturu a flexibilitu a je jednodušší pro čtení, údržbu a ladění.  
  
 Jaké způsobem `Then` – klíčové slovo je prověřit, abyste zjistili, zda příkaz je jeden řádek `If`. Pokud jakoukoli jinou hodnotu než komentář se zobrazí po `Then` na stejném řádku příkaz považován za jeden řádek `If` příkaz. Pokud `Then` chybí, musí být spuštění více řádků `If`... `Then`... `Else`.  
  
 V syntaxi jeden řádek, může mít více příkazů provést v důsledku `If`... `Then` rozhodnutí. Všechny příkazy musí být na stejném řádku a být oddělené dvojtečkou.  

## <a name="multiline-syntax-example"></a>Příklad Víceřádkový syntaxe

<a name="multi-line"></a>
 
 Následující příklad ukazuje použití Víceřádkový syntaxe `If`... `Then`... `Else` příkaz.  
  
 [!code-vb[VbVbalrStatements#101](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_1.vb?highlight=11,14,17,19)]

## <a name="nested-syntax-example"></a>Příklad vnořené syntaxe

<a name="nested"></a>

 Následující příklad obsahuje vnořené `If`... `Then`... `Else` příkazy.  
  
 [!code-vb[VbVbalrStatements#102](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_2.vb?highlight=14,15,17,19,20,21,23,25,26,28)]

## <a name="single-line-syntax-example"></a>Příklad syntaxe jeden řádek
  
<a name="single-line"></a> Následující příklad ukazuje použití syntaxe jeden řádek.  
  
 [!code-vb[VbVbalrStatements#103](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_3.vb?highlight=18)]
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A>  
 <xref:Microsoft.VisualBasic.Interaction.Switch%2A>  
 [Direktivy #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Příkaz Select...Case](../../../visual-basic/language-reference/statements/select-case-statement.md)  
 [Vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Rozhodovací struktury](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [Logické a bitové operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [Operátor If](../../../visual-basic/language-reference/operators/if-operator.md)
