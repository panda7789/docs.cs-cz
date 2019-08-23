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
ms.openlocfilehash: 627318677270ba4ffa8ee430febea7ddf83bd245
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957641"
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
|`testexpression`|Povinný parametr. Vyjádření. Musí se vyhodnotit na jeden ze základních datových`Boolean`typů `Byte`( `Char`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, `Short`,,, `Single`, ,`String` ,a`UShort`). `UInteger` `ULong`|  
|`expressionlist`|Vyžadováno v `Case` příkazu. Seznam klauzulí výrazů, které představují hodnoty shody `testexpression`pro. Vícenásobné klauzule výrazu jsou odděleny čárkami. Každá klauzule může mít jednu z následujících forem:<br /><br /> -   *Výraz1* `To` *Výraz2*<br />-[ `Is` ] *výraz* ComparisonOperator<br />-   *vyjádření*<br /><br /> Pomocí klíčového slova určete hranice rozsahu hodnot shody pro `testexpression`. `To` Hodnota `expression1` musí být menší nebo rovna `expression2`hodnotě.<br /><br /> `<=` `<>` `<` `>=` `testexpression`Použijte klíčové slovo s operátorem porovnání (`=`, ,`>`,, nebo) a určete omezení pro hodnoty shody pro. `Is` Pokud klíčové slovo není zadáno, je automaticky vloženo před *ComparisonOperator.* `Is`<br /><br /> Formulář, který určuje `expression` pouze, se považuje za zvláštní případ `Is` formuláře, kde *ComparisonOperator* je rovnítko (`=`). Tento formulář je vyhodnocen `testexpression`jako  =  `expression`.<br /><br /> Výrazy v `expressionlist` můžou být libovolného datového typu, za předpokladu, že jsou implicitně převoditelné na `testexpression` typ a příslušné `comparisonoperator` jsou platné pro dva typy, se kterými se používá.|  
|`statements`|Volitelný parametr. Jeden nebo více příkazů, `Case` které následují `testexpression` za běhu, pokud `expressionlist`odpovídají libovolné klauzuli v.|  
|`elsestatements`|Volitelný parametr. Jeden nebo více příkazů, `Case Else` které následují `testexpression` za běhu, pokud `expressionlist` neodpovídají žádné klauzuli v žádné z `Case` příkazů.|  
|`End Select`|Ukončí definici `Select`... `Case` konstrukce.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud `testexpression` odpovídá klauzuli `Case` Any `Case` `Case` `End Select` `Case Else`, příkazy, které následují za tímto příkazem, se spustí až do následujícího příkazu, nebo. `expressionlist` Řízení pak předá následujícímu `End Select`příkazu. Pokud `testexpression` se shoduje `expressionlist` s klauzulí ve více než `Case` jedné klauzuli, spustí se jenom příkazy, které následují po první shodě.  
  
 `testexpression` `elsestatements` `Case` `expressionlist` Příkaz slouží k zavedení příkazu ke spuštění, pokud není nalezena shoda mezi klauzulí a a v žádném z ostatních příkazů. `Case Else` I když to není vyžadováno, je vhodné mít `Case Else` příkaz ve vaší `Select Case` konstrukci pro zpracování nepředvídatelných `testexpression` hodnot. Pokud se `Case` neshoduje `testexpression` žádná `expressionlist` klauzule a `Case Else` neexistuje žádný příkaz, ovládací prvek předá `End Select`příkaz následujícímu příkazu.  
  
 V každé `Case` klauzuli můžete použít více výrazů nebo rozsahů. Například následující řádek je platný.  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
> Klíčové slovo použité `Case` v příkazech `Case Else` a není stejné jako [operátor is](../../../visual-basic/language-reference/operators/is-operator.md), který se používá pro porovnání odkazů na objekty. `Is`  
  
 Pro řetězce znaků lze zadat rozsahy a více výrazů. V následujícím příkladu `Case` odpovídá jakémukoli řetězci, který je přesně roven "jablk", má hodnotu mezi "NUTS" a "polévka" v abecedním pořadí nebo obsahuje přesně stejnou hodnotu jako aktuální `testItem`hodnota.  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 Nastavení `Option Compare` může ovlivnit porovnávání řetězců. V `Option Compare Text`části jsou řetězce "jablka" a "jablka" porovnány jako stejné `Option Compare Binary`, ale v nástroji.  
  
> [!NOTE]
> Příkaz s více klauzulemi může vykazovat chování označované jako *krátkodobé okruhy.* `Case` Visual Basic vyhodnocuje klauzule zleva doprava a pokud jedna vytvoří shodu s `testexpression`, zbývající klauzule nejsou vyhodnocovány. Krátkodobé okruhy mohou zvýšit výkon, ale může dojít k neočekávaným výsledkům, pokud očekáváte, že `expressionlist` se každý výraz v má vyhodnotit. Další informace o krátkodobém okruhu naleznete v tématu [Boolean Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md).  
  
 Pokud kód v rámci `Case` bloku příkazu nebo `Case Else` není nutné spouštět žádné další příkazy v bloku, může `Exit Select` tento blok opustit pomocí příkazu. Tím se ovládací prvek přenáší hned na `End Select`následující příkaz.  
  
 `Select Case`konstrukce můžou být vnořené. `Select Case` Každá vnořená `Select Case` konstrukce musí mít `End Select` příkaz, který musí být zcela obsažen v rámci jednoho `Case` nebo `Case Else` více příkazů bloku vnější konstrukce, v rámci které je vnořena.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je použita `Select Case` konstrukce pro zápis řádku, který odpovídá hodnotě proměnné. `number` Druhý `Case` příkaz obsahuje hodnotu, která odpovídá aktuální `number`hodnotě, takže příkaz, který zapisuje "mezi 6 a 8 včetně", se spouští.  
  
 [!code-vb[VbVbalrStatements#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#54)]  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- [Příkaz End](../../../visual-basic/language-reference/statements/end-statement.md)
- [Příkaz If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Příkaz Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Příkaz Exit](../../../visual-basic/language-reference/statements/exit-statement.md)
