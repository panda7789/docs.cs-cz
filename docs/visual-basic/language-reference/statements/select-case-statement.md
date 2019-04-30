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
ms.openlocfilehash: f99db4f1dc224e5f75ee67ba94c3745f28438724
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783887"
---
# <a name="selectcase-statement-visual-basic"></a>Select...Case – příkaz (Visual Basic)
Spustí jednu z několika skupin příkazů, v závislosti na hodnotě výrazu.  
  
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
|`testexpression`|Povinný parametr. výraz. Se musí vyhodnotit na jednu základní datové typy (`Boolean`, `Byte`, `Char`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, a `UShort`).|  
|`expressionlist`|Vyžaduje `Case` příkazu. Seznam klauzulí výraz představující shody hodnoty pro `testexpression`. Více klauzulí výrazu jsou odděleny čárkami. Každá klauzule můžete provést jednu z následujících forem:<br /><br /> -   *Expression1* `To` *expression2*<br />-[ `Is` ] *comparisonoperator* *výraz*<br />-   *Výraz*<br /><br /> Použití `To` – klíčové slovo k určení hranic rozsahu shody hodnoty `testexpression`. Hodnota `expression1` musí být menší nebo rovna hodnotě `expression2`.<br /><br /> Použití `Is` – klíčové slovo operátoru porovnání (`=`, `<>`, `<`, `<=`, `>`, nebo `>=`) k určení omezení pro porovnání hodnoty `testexpression`. Pokud `Is` – klíčové slovo není zadán, je automaticky vložen před *comparisonoperator*.<br /><br /> Formulář, určete pouze `expression` je považován za zvláštní případ `Is` tvoří where *comparisonoperator* je znak rovná se (`=`). Tento formulář je vyhodnocen jako `testexpression`  =  `expression`.<br /><br /> Výrazy v `expressionlist` může být libovolného datového typu, pokud jsou implicitně převést na typ `testexpression` a odpovídající `comparisonoperator` je platný pro tyto dva typy se používá se.|  
|`statements`|Volitelné. Jeden nebo více následujících příkazů `Case` , že pokud spuštění `testexpression` odpovídá jakékoli klauzule `expressionlist`.|  
|`elsestatements`|Volitelné. Jeden nebo více následujících příkazů `Case Else` , že pokud spuštění `testexpression` se neshoduje s žádnou klauzuli v `expressionlist` u všech `Case` příkazy.|  
|`End Select`|Ukončí definici `Select`... `Case` konstrukce.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud `testexpression` odpovídá některému `Case` `expressionlist` klauzule, příkazy po `Case` příkaz provozovat až do dalšího `Case`, `Case Else`, nebo `End Select` příkazu. Ovládací prvek pak předá do příkaz následující `End Select`. Pokud `testexpression` odpovídá `expressionlist` klauzule ve více než jeden `Case` klauzule, spusťte jenom příkazy po první shoda.  
  
 `Case Else` Prohlášení se používá k uvození `elsestatements` ke spouštění, pokud není nalezena žádná shoda mezi `testexpression` a `expressionlist` klauzule v některé z nich `Case` příkazy. Ačkoli není vyžadována, je dobré mít `Case Else` příkaz v vaše `Select Case` konstrukce pro zpracování nepředvídaných `testexpression` hodnoty. Pokud ne `Case` `expressionlist` klauzule odpovídá `testexpression` a neexistuje žádná `Case Else` příkazu, předá řízení následující příkaz `End Select`.  
  
 Můžete použít několik rozsahů nebo výrazy v každém `Case` klauzuli. Například následující řádek je platný.  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
>  `Is` – Klíčové slovo používané `Case` a `Case Else` příkazů není stejný jako [je operátor](../../../visual-basic/language-reference/operators/is-operator.md), který se používá pro objekt k porovnání.  
  
 Můžete určit rozsahy a několik výrazů pro řetězce znaků. V následujícím příkladu `Case` odpovídá jakémukoliv řetězci, který se rovná "apples", má hodnotu mezi "nuts" a "polévky" v abecedním pořadí nebo obsahuje přesně stejnou hodnotu jako aktuální hodnota `testItem`.  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 Nastavení `Option Compare` může ovlivnit porovnávání řetězců. V části `Option Compare Text`, porovnat řetězce "Apples" a "apples" jako rovnocenné, ale v nabídce `Option Compare Binary`, tomu tak není.  
  
> [!NOTE]
>  A `Case` příkazu s více klauzulemi může chovat říká *zkrácenou*. Visual Basic vyhodnotí klauzule zleva doprava a pokud vytváří a najděte shody s `testexpression`, není u nich vyhodnoceno zbývající klauzule. Krátký cyklus může zlepšit výkon, ale mohou způsobit neočekávané výsledky, pokud očekáváte každý výraz v `expressionlist` k vyhodnocení. Další informace o zkrácenou najdete v tématu [logické výrazy](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md).  
  
 Pokud kód v rámci `Case` nebo `Case Else` blok příkazů není nutné ke spuštění všech dalších příkazů v bloku, blok ho můžete ukončit pomocí `Exit Select` příkazu. Tento ovládací prvek okamžitě přenese příkaz následující `End Select`.  
  
 `Select Case` mohou být vnořené konstrukce. Každá vnořená `Select Case` konstrukce musí mít odpovídající `End Select` příkazu a musí být zcela obsažen v jednom `Case` nebo `Case Else` vnější blok příkazu `Select Case` konstrukce, ve kterém je vnořená.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Select Case` konstrukce zapsat řádek odpovídající hodnotě proměnné `number`. Druhá `Case` příkaz obsahuje hodnotu, která odpovídá aktuální hodnotě `number`, takže příkaz, který zapíše "mezi 6 a 8, včetně" spustí.  
  
 [!code-vb[VbVbalrStatements#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#54)]  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- [Příkaz End](../../../visual-basic/language-reference/statements/end-statement.md)
- [Příkaz If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Příkaz Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Příkaz Exit](../../../visual-basic/language-reference/statements/exit-statement.md)
