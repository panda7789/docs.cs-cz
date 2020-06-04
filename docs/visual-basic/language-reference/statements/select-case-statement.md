---
title: Select...Case – příkaz
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
ms.openlocfilehash: 3dedd43f920b493a0aca9ce48460b00815e1af5c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404236"
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
  
|Pojem|Definice|  
|---|---|  
|`testexpression`|Povinná hodnota. Vyjádření. Musí se vyhodnotit jako jeden ze základních datových typů ( `Boolean` , `Byte` ,, `Char` `Date` , `Double` , `Decimal` , `Integer` , `Long` ,,,, `Object` `SByte` `Short` `Single` , `String` ,, a `UInteger` `ULong` `UShort` ).|  
|`expressionlist`|Vyžadováno v `Case` příkazu. Seznam klauzulí výrazů, které představují hodnoty shody pro `testexpression` . Vícenásobné klauzule výrazu jsou odděleny čárkami. Každá klauzule může mít jednu z následujících forem:<br /><br /> -   *Výraz1* `To` *Výraz2*<br />-[ `Is` ] *comparisonoperator* *výraz* ComparisonOperator<br />-   *vyjádření*<br /><br /> Pomocí `To` klíčového slova určete hranice rozsahu hodnot shody pro `testexpression` . Hodnota `expression1` musí být menší nebo rovna hodnotě `expression2` .<br /><br /> Použijte `Is` klíčové slovo s operátorem porovnání ( `=` , `<>` ,,, `<` `<=` `>` nebo `>=` ) a určete omezení pro hodnoty shody pro `testexpression` . Pokud `Is` klíčové slovo není zadáno, je automaticky vloženo před *ComparisonOperator*.<br /><br /> Formulář, který určuje pouze, `expression` se považuje za zvláštní případ `Is` formuláře, kde *ComparisonOperator* je rovnítko ( `=` ). Tento formulář je vyhodnocen jako `testexpression`  =  `expression` .<br /><br /> Výrazy v `expressionlist` můžou být libovolného datového typu, za předpokladu, že jsou implicitně převoditelné na typ `testexpression` a příslušné `comparisonoperator` jsou platné pro dva typy, se kterými se používá.|  
|`statements`|Nepovinný parametr. Jeden nebo více příkazů, které následují za `Case` běhu, pokud `testexpression` odpovídají libovolné klauzuli v `expressionlist` .|  
|`elsestatements`|Nepovinný parametr. Jeden nebo více příkazů, které následují za `Case Else` běhu, pokud `testexpression` neodpovídají žádné klauzuli v `expressionlist` žádné z `Case` příkazů.|  
|`End Select`|Ukončí definici `Select` konstrukce.... `Case`|  
  
## <a name="remarks"></a>Poznámky  
 Pokud `testexpression` odpovídá `Case` `expressionlist` klauzuli any, příkazy, které následují za tímto příkazem, se `Case` spustí až do následujícího `Case` `Case Else` příkazu, nebo `End Select` . Řízení pak předá následujícímu příkazu `End Select` . Pokud `testexpression` se shoduje s `expressionlist` klauzulí ve více než jedné `Case` klauzuli, spustí se jenom příkazy, které následují po první shodě.  
  
 `Case Else`Příkaz slouží k zavedení příkazu `elsestatements` ke spuštění, pokud není nalezena shoda mezi `testexpression` klauzulí a a `expressionlist` v žádném z ostatních `Case` příkazů. I když to není vyžadováno, je vhodné mít `Case Else` příkaz ve vaší `Select Case` konstrukci pro zpracování nepředvídatelných `testexpression` hodnot. Pokud `Case` `expressionlist` se neshoduje žádná klauzule `testexpression` a neexistuje žádný `Case Else` příkaz, ovládací prvek předá příkaz následujícímu příkazu `End Select` .  
  
 V každé klauzuli můžete použít více výrazů nebo rozsahů `Case` . Například následující řádek je platný.  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
> `Is`Klíčové slovo použité v `Case` `Case Else` příkazech a není stejné jako [operátor is](../operators/is-operator.md), který se používá pro porovnání odkazů na objekty.  
  
 Pro řetězce znaků lze zadat rozsahy a více výrazů. V následujícím příkladu `Case` odpovídá jakémukoli řetězci, který je přesně roven "jablk", má hodnotu mezi "NUTS" a "polévka" v abecedním pořadí nebo obsahuje přesně stejnou hodnotu jako aktuální hodnota `testItem` .  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 Nastavení `Option Compare` může ovlivnit porovnávání řetězců. V části jsou `Option Compare Text` řetězce "jablka" a "jablka" porovnány jako stejné, ale v nástroji `Option Compare Binary` .  
  
> [!NOTE]
> `Case`Příkaz s více klauzulemi může vykazovat chování označované jako *krátkodobé okruhy*. Visual Basic vyhodnocuje klauzule zleva doprava a pokud jedna vytvoří shodu s `testexpression` , zbývající klauzule nejsou vyhodnocovány. Krátkodobé okruhy mohou zvýšit výkon, ale může dojít k neočekávaným výsledkům, pokud očekáváte, že se každý výraz v `expressionlist` má vyhodnotit. Další informace o krátkodobém okruhu naleznete v tématu [Boolean Expressions](../../programming-guide/language-features/operators-and-expressions/boolean-expressions.md).  
  
 Pokud kód v rámci `Case` `Case Else` bloku příkazu nebo není nutné spouštět žádné další příkazy v bloku, může tento blok opustit pomocí `Exit Select` příkazu. Tím se ovládací prvek přenáší hned na následující příkaz `End Select` .  
  
 `Select Case`konstrukce můžou být vnořené. Každá vnořená `Select Case` konstrukce musí mít `End Select` příkaz, který musí být zcela obsažen v rámci jednoho `Case` nebo více `Case Else` příkazů bloku vnější `Select Case` konstrukce, v rámci které je vnořena.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je použita `Select Case` konstrukce pro zápis řádku, který odpovídá hodnotě proměnné `number` . Druhý `Case` příkaz obsahuje hodnotu, která odpovídá aktuální hodnotě `number` , takže příkaz, který zapisuje "mezi 6 a 8 včetně", se spouští.  
  
 [!code-vb[VbVbalrStatements#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#54)]  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- [Příkaz end](end-statement.md)
- [If...Then...Else – příkaz](if-then-else-statement.md)
- [Option Compare – příkaz](option-compare-statement.md)
- [Exit – příkaz](exit-statement.md)
