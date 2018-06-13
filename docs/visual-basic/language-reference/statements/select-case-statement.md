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
ms.openlocfilehash: 9d24b455d92cbd00b268df26283aab082b7703a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604572"
---
# <a name="selectcase-statement-visual-basic"></a>Select...Case – příkaz (Visual Basic)
Používá jednu z několika skupin příkazů, v závislosti na hodnotě výrazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`testexpression`|Požadováno. Výraz. Musí být vyhodnocen jako jeden z základní datové typy (`Boolean`, `Byte`, `Char`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, a `UShort`).|  
|`expressionlist`|V požadován `Case` příkaz. Seznam výraz klauzule představující shody hodnoty pro `testexpression`. Více klauzulí výraz se oddělují čárkami. Každý klauzule můžete provést jednu z následujících podob:<br /><br /> -   *Expression1* `To` *Výraz2*<br />-[ `Is` ] *porovnávací operátor* *výraz*<br />-   *výraz*<br /><br /> Použití `To` – klíčové slovo hranice rozsahu odpovídal zadat hodnoty pro `testexpression`. Hodnota `expression1` musí být menší než nebo rovna hodnotě `expression2`.<br /><br /> Použití `Is` – klíčové slovo pomocí operátoru porovnání (`=`, `<>`, `<`, `<=`, `>`, nebo `>=`) nastavit omezení u shody hodnoty pro `testexpression`. Pokud `Is` – klíčové slovo není zadána, bude automaticky vložen před *porovnávací operátor*.<br /><br /> Formulář zadání pouze `expression` je považován za zvláštní případ `Is` formuláři kde *porovnávací operátor* je znak rovná se (`=`). Tento formulář je vyhodnoceno jako `testexpression`  =  `expression`.<br /><br /> Výrazy v `expressionlist` mohou být jakéhokoli typu dat předpokladu, že jsou implicitně převést na typ `testexpression` a odpovídající `comparisonoperator` je platný pro dva typy je používán s.|  
|`statements`|Volitelné. Jeden nebo více následujících příkazů `Case` že spuštění Pokud `testexpression` odpovídá všechny klauzule v `expressionlist`.|  
|`elsestatements`|Volitelné. Jeden nebo více následujících příkazů `Case Else` že spuštění Pokud `testexpression` neodpovídá žádné klauzule v `expressionlist` každého `Case` příkazy.|  
|`End Select`|Ukončí definice `Select`... `Case` konstrukce.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud `testexpression` odpovídá některému `Case` `expressionlist` klauzuli, která následující příkazy `Case` příkaz spustit na další `Case`, `Case Else`, nebo `End Select` příkaz. Řízení potom předává pro následující příkaz `End Select`. Pokud `testexpression` odpovídá `expressionlist` klauzule ve více než jeden `Case` klauzuli spustit jenom příkazy následující na první shodu.  
  
 `Case Else` Příkaz se používá k zavedení `elsestatements` ke spouštění, pokud není nalezena žádná shoda mezi `testexpression` a `expressionlist` klauzule některý z dalších `Case` příkazy. Ačkoli to není vyžadováno, je vhodné mít `Case Else` příkaz v vaše `Select Case` konstrukce pro zpracování nepředpokládaného `testexpression` hodnoty. Pokud žádné `Case` `expressionlist` klauzule odpovídá `testexpression` a neexistuje žádné `Case Else` prohlášení, předává řízení pro následující příkaz `End Select`.  
  
 Můžete použít více výrazů ani rozsahů v každé `Case` klauzule. Například následující řádek je platný.  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
>  `Is` Klíčové slovo používané v `Case` a `Case Else` příkazy není stejný jako [je operátor](../../../visual-basic/language-reference/operators/is-operator.md), který se používá pro porovnání odkaz na objekt.  
  
 Můžete určit rozsahy a více výrazů pro řetězce znaků. V následujícím příkladu `Case` odpovídá jakémukoli řetězci, který se rovná "jablka", má hodnotu mezi "nuts" a "polévky" v abecedním pořadí nebo obsahuje přesně stejnou hodnotu jako aktuální hodnota `testItem`.  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 Nastavení `Option Compare` může ovlivnit porovnání řetězců. V části `Option Compare Text`, porovnat řetězce "Jablka" a "jablka" jako rovnocenné, ale v části `Option Compare Binary`, ne.  
  
> [!NOTE]
>  A `Case` příkaz s více klauzulí může vykazovat chování známé jako *krátká smyčka*. Visual Basic vyhodnotí klauzule zleva doprava a pokud vytváří shody s `testexpression`, zbývající klauzule nevyhodnocují. Krátká smyčka může zlepšit výkon, ale může způsobit neočekávaný výsledek, pokud očekáváte každých výrazu v `expressionlist` k vyhodnocení. Další informace o krátká smyčka najdete v tématu [logické výrazy](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md).  
  
 Pokud kód v rámci `Case` nebo `Case Else` blok příkazu není nutné spustit všechny více příkazy v bloku, blok ho můžete ukončit pomocí `Exit Select` příkaz. Toto okamžitě převede řízení pro následující příkaz `End Select`.  
  
 `Select Case` konstrukce mohou být použity. Všechny vnořené `Select Case` konstrukce musí mít odpovídající `End Select` příkaz a musí být zcela obsažen v rámci jednoho `Case` nebo `Case Else` příkaz blok vnější `Select Case` konstrukce, ve kterém je vnořený.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Select Case` konstrukce k zápisu řádku odpovídající hodnotě proměnné `number`. Druhý `Case` příkaz obsahuje hodnotu, která odpovídá aktuální hodnota `number`, takže příkaz, který zapíše "6 až 8, včetně" spustí.  
  
 [!code-vb[VbVbalrStatements#54](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/select-case-statement_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A>  
 [Příkaz End](../../../visual-basic/language-reference/statements/end-statement.md)  
 [Příkaz If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [Příkaz Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [Příkaz Exit](../../../visual-basic/language-reference/statements/exit-statement.md)
