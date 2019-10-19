---
title: Select...Case – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Select
- vb.Case
helpviewer_keywords:
- Select statement [Visual Basic]
- Case statement [Visual Basic]
- Select...Case statements
- conditional statements [Visual Basic], Select Case
- control flow [Visual Basic], branching
- Else keyword [Visual Basic], in Select...Case statements
- execution [Visual Basic], conditional
- To keyword [Visual Basic], in Select...Case statements
- Select Case statement [Visual Basic], Select...Case
- Select statement [Visual Basic], Select...Case
- Is operator [Visual Basic], in Select...Case statements
- branching [Visual Basic], conditional
- Case Else statement [Visual Basic], Select...Case
- End keyword [Visual Basic], Select Case statements
- Case statement [Visual Basic], Select...Case
ms.assetid: 68877b65-5419-4bf0-a465-20cd0e4c7d44
ms.openlocfilehash: d035118febc5ea9d1ea8e5cc0145cb030626b030
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583241"
---
# <a name="selectcase-statement-visual-basic"></a>Select...Case – příkaz (Visual Basic)
Spustí jednu z několika skupin příkazů, v závislosti na hodnotě výrazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Select [ Case ] testexpression  
    [ Case expressionlist  
        [ statements ] ]  
    [ Case Else  
        [ elsestatements ] ]  
End Select  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`testexpression`|Požadováno. Vyjádření. Musí se vyhodnotit jako jeden ze základních datových typů (`Boolean`, `Byte`, `Char`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, 0, 1, 2 , 3, 4 a 5).|  
|`expressionlist`|Vyžadováno v příkazu `Case`. Seznam klauzulí výrazů, které představují hodnoty shody pro `testexpression`. Vícenásobné klauzule výrazu jsou odděleny čárkami. Každá klauzule může mít jednu z následujících forem:<br /><br /> -   *výraz1* `To` *Výraz2*<br />-[`Is`] *výraz* ComparisonOperator<br />*výraz* -   <br /><br /> Pomocí klíčového slova `To` můžete určit hranice rozsahu hodnot shody pro `testexpression`. Hodnota `expression1` musí být menší nebo rovna hodnotě `expression2`.<br /><br /> Použijte klíčové slovo `Is` s operátorem porovnání (`=`, `<>`, `<`, `<=`, `>` nebo `>=`) a určete omezení pro hodnoty shody pro `testexpression`. Pokud klíčové slovo `Is` není zadáno, je automaticky vloženo před *ComparisonOperator*.<br /><br /> Formulář, který určuje pouze `expression`, se považuje za zvláštní případ `Is` formuláře, kde *ComparisonOperator* je znak rovná se (`=`). Tento formulář je vyhodnocen jako `testexpression`  =  `expression`.<br /><br /> Výrazy v `expressionlist` můžou být libovolného datového typu, za předpokladu, že jsou implicitně převoditelné na typ `testexpression` a příslušný `comparisonoperator` je platný pro dva typy, se kterými se používá.|  
|`statements`|Volitelné. Jeden nebo více příkazů následujících `Case`, které se spustí, pokud `testexpression` odpovídá libovolné klauzuli v `expressionlist`.|  
|`elsestatements`|Volitelné. Jeden nebo více příkazů následujících `Case Else`, které se spustí, pokud `testexpression` neodpovídají žádné klauzuli v `expressionlist` žádného `Case` příkazů.|  
|`End Select`|Ukončí definici `Select`... vytváření `Case`.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud `testexpression` odpovídá jakékoli klauzuli `expressionlist` `Case`, příkazy následující po `Case` příkazu se spustí až k dalšímu `Case`, `Case Else` nebo `End Select`mu příkazu. Řízení poté předává příkaz následující `End Select`. Pokud `testexpression` odpovídá klauzuli `expressionlist` ve více než jedné klauzuli `Case`, spustí se pouze příkazy po prvním porovnání.  
  
 Příkaz `Case Else` slouží k zavedení `elsestatements` ke spuštění, pokud není nalezena shoda mezi `testexpression` a klauzulí `expressionlist` v žádném z ostatních příkazů `Case`. I když to není nutné, je vhodné mít v konstrukci `Select Case` `Case Else` příkaz pro zpracování neočekávaných hodnot `testexpression`. Pokud žádná klauzule `Case` `expressionlist` neodpovídá `testexpression` a neexistuje žádný `Case Else` příkaz, řízení se předá do příkazu následujícího po `End Select`.  
  
 V každé klauzuli `Case` můžete použít více výrazů nebo rozsahů. Například následující řádek je platný.  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
> Klíčové slovo `Is` používané v příkazech `Case` a `Case Else` není stejné jako [operátor is](../../../visual-basic/language-reference/operators/is-operator.md), který se používá pro porovnání odkazů na objekty.  
  
 Pro řetězce znaků lze zadat rozsahy a více výrazů. V následujícím příkladu `Case` odpovídá jakémukoli řetězci, který je přesně roven "jablk", má hodnotu mezi "NUTS" a "polévka" v abecedním pořadí nebo obsahuje přesně stejnou hodnotu jako aktuální hodnota `testItem`.  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 Nastavení `Option Compare` může ovlivnit porovnávání řetězců. V části `Option Compare Text` jsou řetězce "jablka" a "jablka" porovnány jako stejné, ale v rámci `Option Compare Binary`.  
  
> [!NOTE]
> Příkaz `Case` s více klauzulemi může vykazovat chování označované jako *krátkodobé okruhy*. Visual Basic vyhodnocuje klauzule zleva doprava a pokud jedna vytvoří shodu s `testexpression`, zbývající klauzule nejsou vyhodnocovány. Krátkodobé okruhy můžou zlepšit výkon, ale můžou způsobit neočekávané výsledky, pokud očekáváte, že se všechny výrazy v `expressionlist` vyhodnotí. Další informace o krátkodobém okruhu naleznete v tématu [Boolean Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md).  
  
 Pokud kód v rámci bloku příkazu `Case` nebo `Case Else` nemusí spouštět žádné další příkazy v bloku, může tento blok opustit pomocí příkazu `Exit Select`. Tím se ovládací prvek přenáší hned do příkazu, který následuje po `End Select`.  
  
 konstrukce `Select Case` můžou být vnořené. Každá vnořená `Select Case` konstrukce musí mít příkaz, který by měl `End Select` odpovídat, a musí být zcela obsažena v rámci jednoho `Case` nebo `Case Else` bloku vnějšího `Select Case` konstrukce, ve kterém je vnořená.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je použita konstrukce `Select Case` k zápisu řádku, který odpovídá hodnotě proměnné `number`. Druhý příkaz `Case` obsahuje hodnotu, která odpovídá aktuální hodnotě `number`, takže příkaz, který zapisuje "mezi 6 a 8 včetně" běhy ".  
  
 [!code-vb[VbVbalrStatements#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#54)]  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- [Příkaz End](../../../visual-basic/language-reference/statements/end-statement.md)
- [Příkaz If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Příkaz Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Příkaz Exit](../../../visual-basic/language-reference/statements/exit-statement.md)
