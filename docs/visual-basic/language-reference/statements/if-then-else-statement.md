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
ms.openlocfilehash: d91a913d515f36a6b974850bc30079b000a919b4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842691"
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

Tento článek obsahuje několik příkladů, které ilustrují použití `If`... `Then`... `Else` – příkaz:

* [Příklad víceřádkové syntaxe](#multi-line)
* [Příklad vnořené syntaxe](#nested)
* [Příklad syntaxe jedním řádkem](#single-line)

## <a name="parts"></a>Součásti  
 `condition`  
 Povinný parametr. výraz. Musí být vyhodnocen `True` nebo `False`, nebo na datový typ, který je implicitně převést na `Boolean`.  
  
 Pokud má výraz hodnotu [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` proměnné, která se vyhodnotí jako [nic](../../../visual-basic/language-reference/nothing.md), podmínka je zpracováván stejně, jako je výraz `False` a `Else` je blok proveden.  
  
 `Then`  
 Vyžaduje v syntaxi jedním řádkem; nepovinné v syntaxi víceřádkový.  
  
 `statements`  
 Volitelné. Jeden nebo více následujících příkazů `If`... `Then` , která se spustí, pokud `condition` vyhodnotí jako `True`.  
  
 `elseifcondition`  
 Požadováno pokud `ElseIf` je k dispozici. výraz. Musí být vyhodnocen `True` nebo `False`, nebo na datový typ, který je implicitně převést na `Boolean`.  
  
 `elseifstatements`  
 Volitelné. Jeden nebo více následujících příkazů `ElseIf`... `Then` , která se spustí, pokud `elseifcondition` vyhodnotí jako `True`.  
  
 `elsestatements`  
 Volitelné. Jeden nebo více příkazů, které jsou spouštěny, pokud žádné předchozí `condition` nebo `elseifcondition` výraz vyhodnocen jako `True`.  
  
 `End If`  
 Ukončí víceřádkové verzi `If`... `Then`... `Else` bloku.  
  
## <a name="remarks"></a>Poznámky  
  
### <a name="multiline-syntax"></a>Multiline – syntaxe  
 Když `If`... `Then`... `Else` příkazu nalezen, `condition` je testován. Pokud `condition` je `True`, příkazy po `Then` provádějí. Pokud `condition` je `False`každá `ElseIf` – příkaz (Pokud tam nějaké jsou) se vyhodnocuje podle pořadí. Když `True` `elseifcondition` se nachází bezprostředně následující přidružené příkazy `ElseIf` provádějí. Pokud ne `elseifcondition` vyhodnotí jako `True`, nebo pokud nejsou žádné `ElseIf` příkazy, příkazy po `Else` provádějí. Po provedení následující příkazy `Then`, `ElseIf`, nebo `Else`, pokračuje se příkaz následující `End If`.  
  
 `ElseIf` a `Else` klauzule jsou volitelné. Můžete mít kolik `ElseIf` klauzulí je vhodné `If`... `Then`... `Else` příkazu, ale ne `ElseIf` klauzule může být po `Else` klauzuli. `If`... `Then`... `Else` příkazy mohou být vnořené do jiné.  
  
 Víceřádkový syntaxe `If` příkaz musí být jediným příkazem v prvním řádku. `ElseIf`, `Else`, A `End If` příkazy nesmí následovat pouze po popisku řádku. `If`... `Then`... `Else` bloku musí končit `End If` příkazu.  
  
> [!TIP]
>  [Vyberte... Case – příkaz](../../../visual-basic/language-reference/statements/select-case-statement.md) může být užitečnější, pokud vyhodnotíte jediný výraz, který má několik možných hodnot.  
  
### <a name="single-line-syntax"></a>Syntaxe jednoho řádku  
 Syntaxe jedním řádkem pro jednu podmínku s kódem můžete spustit, pokud je to možné. Více řádků syntaxe však poskytuje další struktury a flexibilitu a je jednodušší pro čtení, spravovat a ladit.  
  
 Jaké způsobem `Then` – klíčové slovo je prověřit, abyste zjistili, zda je příkaz jedním řádkem `If`. Pokud nic jiného než komentář se zobrazí po `Then` na stejném řádku, příkaz je považován za jeden řádek `If` příkazu. Pokud `Then` chybí, musí být začátek řádku více `If`... `Then`... `Else`.  
  
 V syntaxi jedním řádkem, může mít více příkazů provést, protože výsledek `If`... `Then` rozhodnutí. Všechny příkazy se musí nacházet na stejném řádku a být odděleny dvojtečkami.  

## <a name="multiline-syntax-example"></a>Příklad víceřádkové syntaxe

<a name="multi-line"></a>
 
 Následující příklad ukazuje použití víceřádkové syntaxe `If`... `Then`... `Else` příkazu.  
  
 [!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a>Příklad vnořené syntaxe

<a name="nested"></a>

 Následující příklad obsahuje vnořené `If`... `Then`... `Else` příkazy.  
  
 [!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a>Příklad syntaxe jedním řádkem
  
<a name="single-line"></a> Následující příklad ukazuje použití syntaxe jedním řádkem.  
  
 [!code-vb[VbVbalrStatements#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#103)]
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [Direktivy #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Příkaz Select...Case](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [Vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Rozhodovací struktury](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Logické a bitové operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [Operátor If](../../../visual-basic/language-reference/operators/if-operator.md)
