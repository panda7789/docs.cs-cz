---
title: "For...Next – příkaz (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Step
- vb.Next
- vb.To
- vb.for
helpviewer_keywords:
- infinite loops
- Next keyword [Visual Basic], For...Next statements
- For keyword [Visual Basic], For...Next statements
- Step keyword [Visual Basic], For...Next statements
- operator overloading, For...Next statement
- To keyword [Visual Basic], For...Next statements
- endless loops
- loops, endless
- instructions, repeating
- Next statement [Visual Basic], For...Next
- For...Next statements
- loop structures [Visual Basic], For...Next
- loops, infinite
- Exit statement [Visual Basic], For...Next statements
- For statement [Visual Basic]
ms.assetid: f5fc0d51-67ce-4c36-9f09-31c9a91c94e9
caps.latest.revision: "64"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8a50f44a167952c735c6ed2830ca87105413401b
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fornext-statement-visual-basic"></a>For...Next – příkaz (Visual Basic)
Opakuje skupinu příkazy zadaného počtu opakování.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
For counter [ As datatype ] = start To end [ Step step ]  
    [ statements ]  
    [ Continue For ]  
    [ statements ]  
    [ Exit For ]  
    [ statements ]  
Next [ counter ]  
```  
  
## <a name="parts"></a>Součásti  
  
|Část|Popis|  
|----------|-----------------|  
|`counter`|V požadované `For` příkaz. Číselné proměnné. Řídicí proměnná smyčky. Další informace najdete v tématu [čítač Argument](#BKMK_Counter) dál v tomto tématu.|  
|`datatype`|Volitelné. Datový typ `counter`. Další informace najdete v tématu [čítač Argument](#BKMK_Counter) dál v tomto tématu.|  
|`start`|Požadováno. Číselný výraz. Počáteční hodnota `counter`.|  
|`end`|Požadováno. Číselný výraz. Konečná hodnota `counter`.|  
|`step`|Volitelné. Číselný výraz. Hodnota, o kterou `counter` se zvýší pokaždé, když pomocí smyčky.|  
|`statements`|Volitelné. Jeden nebo více příkazů mezi `For` a `Next` , na kterých běží zadaného počtu opakování.|  
|`Continue For`|Volitelné. Přenosy ovládacího prvku do další iterace smyčky.|  
|`Exit For`|Volitelné. Přenosy ovládacího prvku mimo `For` smyčky.|  
|`Next`|Požadováno. Ukončí definice `For` smyčky.|  
  
> [!NOTE]
>  `To` – Klíčové slovo v tomto příkazu slouží k určení rozsahu čítače. Můžete také použít toto klíčové slovo v [vyberte... Příkaz případ](../../../visual-basic/language-reference/statements/select-case-statement.md) a v deklaracích pole. Další informace o deklaracích pole najdete v tématu [Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
## <a name="simple-examples"></a>Jednoduché příklady  
 Můžete použít `For`... `Next` struktury, pokud má být opakován sadu příkazy set stanovený počet.  
  
 V následujícím příkladu `index` proměnnou začíná na hodnotu 1 a je zvýšen při každé iteraci smyčky, končí po hodnotu `index` dosáhne 5.  
  
 [!code-vb[VbVbalrStatements#111](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_1.vb)]  
  
 V následujícím příkladu `number` proměnnou spustí na 2 a je snížit 0,25 na každé iteraci smyčky, končí po hodnotu `number` dosáhne 0. `Step` Argument `-.25` snižuje hodnotu podle 0,25 na každé iteraci smyčky.  
  
 [!code-vb[VbVbalrStatements#112](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_2.vb)]  
  
> [!TIP]
>  A [při... End While – příkaz](../../../visual-basic/language-reference/statements/while-end-while-statement.md) nebo [provést... Příkaz LOOP](../../../visual-basic/language-reference/statements/do-loop-statement.md) funguje dobře, pokud neznáte předem jak často má spustit příkazy ve smyčce. Ale očekáváte-li spustit konkrétní počet opakování, smyčky `For`... `Next` smyčka je lepší volbou. Když poprvé vstoupíte smyčky určíte počet iterací.  
  
## <a name="nesting-loops"></a>Vnoření smyčky  
 Lze vnořit `For` smyčky umístěním jednoho smyčky v rámci jiného. Následující příklad ukazuje vnořené `For`... `Next` struktury, které mají různé krok hodnoty. Vnější smyčky vytvoří řetězec pro každou iteraci smyčky. Vnitřní smyčka snižuje proměnnou smyčky čítače pro každou iteraci smyčky.  
  
 [!code-vb[VbVbalrStatements#113](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_3.vb)]  
  
 Při vnoření smyčky, musí mít jedinečnou každou smyčku `counter` proměnné.  
  
 Můžete také vnořovat různých druhů řídicí struktury v rámci navzájem. Další informace najdete v tématu [vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-for-and-continue-for"></a>Pro ukončení a pokračovat pro  
 `Exit For` Příkazu se okamžitě ukončí `For`...`Next` smyčky a přenosy ovládacího prvku do příkazu, který odpovídá `Next` příkaz.  
  
 `Continue For` Řízení příkaz okamžitě přenese do další iterace smyčky. Další informace najdete v tématu [pokračovat příkaz](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
 Následující příklad ukazuje použití `Continue For` a `Exit For` příkazy.  
  
 [!code-vb[VbVbalrStatements#115](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_4.vb)]  
  
 Můžete použít a zadat libovolný počet `Exit For` příkazy v `For`...`Next` Smyčky. Při použití uvnitř vnořené `For`...`Next` smyčky, `Exit For` ukončí nejvnitřnější smyčky a předá řízení další vyšší úroveň vnoření.  
  
 `Exit For`Po vyhodnocení nějaká podmínka se často používá (například v `If`... `Then`... `Else` struktura). Můžete chtít použít `Exit For` byly splněny následující podmínky:  
  
-   Pokračovat v procházení je zbytečné nebo dokonce znemožňují. Chybná hodnota nebo žádost o ukončení může vytvořit tuto podmínku.  
  
-   A `Try`... `Catch`... `Finally` příkaz zachytí výjimku. Můžete použít `Exit For` na konci `Finally` bloku.  
  
-   Máte nekonečnou smyčku, což je smyčku, který by mohl spustit velký, nebo i nekonečné stanovený počet. Pokud zjistíte takové podmínky, můžete použít `Exit For` abyste se vyhnuli smyčky. Další informace najdete v tématu [provést... Cykly příkaz](../../../visual-basic/language-reference/statements/do-loop-statement.md).  
  
## <a name="technical-implementation"></a>Technická implementace  
 Když `For`... `Next` spuštění cyklu, vyhodnotí jazyka Visual Basic `start`, `end`, a `step`. Visual Basic vyhodnotí tyto hodnoty pouze v tento čas a potom přiřadí `start` k `counter`. Před příkaz bloku spustí, Visual Basic porovná `counter` k `end`. Pokud `counter` je větší než `end` hodnotu (nebo menší, pokud `step` záporné), `For` cykly končí a řídit předává do příkazu, který odpovídá `Next` příkaz. Jinak spustí příkaz bloku.  
  
 Pokaždé, když komunikaci jazyka Visual Basic `Next` prohlášení, navýší `counter` podle `step` a vrátí do `For` příkaz. Znovu porovná `counter` k `end`, a znovu ji buď běží bloku nebo ukončení smyčky, v závislosti na výsledku. Tento proces pokračuje, dokud `counter` předá `end` nebo `Exit For` příkaz je zjistil.  
  
 Dokud nebude zastavit smyčky `counter` uplynutí `end`. Pokud `counter` rovná `end`, že opakování ve smyčce bude pokračovat. Porovnání, které určuje, jestli se má spustit blok je `counter`  <=  `end` Pokud `step` kladné a `counter`  >=  `end` Pokud `step` záporné.  
  
 Pokud změníte hodnotu `counter` při uvnitř smyčku, může být obtížné číst a ladění kódu. Změna hodnoty `start`, `end`, nebo `step` nemá vliv iterace hodnoty, které se zjistilo, že při prvním zadání smyčky.  
  
 Pokud je vnořovat smyčky, kompilátor signály chybu pokud zjistí `Next` příkaz vnější úroveň vnoření před `Next` prohlášení o informacích o vnitřní úroveň. Ale kompilátor to zjistit překrývající se chyby pouze v případě, že zadáte `counter` v každé `Next` příkaz.  
  
### <a name="step-argument"></a>Argument krok  
 Hodnota `step` může být kladná nebo záporná. Tento parametr určuje zpracování smyčky podle následující tabulky:  
  
|**Hodnota kroku**|**Smyčky provede Pokud**|  
|--------------------|--------------------------|  
|Kladné nebo nula.|`counter` <= `end`|  
|Záporný|`counter` >= `end`|  
  
 Výchozí hodnota `step` je 1.  
  
###  <a name="BKMK_Counter"></a>Argument čítače  
 Následující tabulka udává, zda `counter` definuje novou místní proměnné, která je vymezen na celou `For…Next` smyčky. Toto rozhodnutí závisí na tom, zda `datatype` je k dispozici a zda `counter` je již definován.  
  
|Je `datatype` přítomen?|Je `counter` již definována?|Výsledek (jestli `counter` definuje novou místní proměnné, která je vymezen na celou `For...Next` smyčky)|  
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|  
|Ne|Ano|Ne, protože `counter` je již definován. Pokud obor `counter` není místní k postupu, dojde k upozornění kompilace.|  
|Ne|Ne|Ano. Datový typ je odvozeno z `start`, `end`, a `step` výrazy. Informace o odvození typu najdete v tématu [Option Infer – příkaz](../../../visual-basic/language-reference/statements/option-infer-statement.md) a [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).|  
|Ano|Ano|Ano, ale jenom v případě existující `counter` proměnná je definována mimo proces. Tuto proměnnou zůstane samostatné. Pokud obor existující `counter` proměnné je místní k postupu, dojde k chybě kompilace.|  
|Ano|Ne|Ano.|  
  
 Datový typ `counter` Určuje typ iterace, které musí mít jednu z následujících typů:  
  
-   A `Byte`, `SByte`, `UShort`, `Short`, `UInteger`, `Integer`, `ULong`, `Long`, `Decimal`, `Single`, nebo `Double`.  
  
-   Výčet, který je deklarovat pomocí [Enum – příkaz](../../../visual-basic/language-reference/statements/enum-statement.md).  
  
-   `Object`.  
  
-   Typ `T` má následující operátory, kde `B` je typ, který lze použít v `Boolean` výraz.  
  
     `Public Shared Operator >= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator <= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator - (op1 As T, op2 As T) As T`  
  
     `Public Shared Operator + (op1 As T, op2 As T) As T`  
  
 Volitelně můžete zadat `counter` proměnné v `Next` příkaz. Tuto syntaxi zlepšuje čitelnost vašeho programu, zejména v případě, že budete mít člověk vnořené `For` smyčky. Musíte zadat proměnné, která se zobrazí v odpovídající `For` příkaz.  
  
 `start`, `end`, A `step` výrazy lze vyhodnotit na datový typ, který rozšiřuje typu `counter`. Pokud používáte uživatelsky definovaný typ. pro `counter`, možná budete muset definovat `CType` operátor převodu převést typy `start`, `end`, nebo `step` typu `counter`.  
  
## <a name="example"></a>Příklad  
 Následující příklad odebere všechny elementy obecné seznamu. Místo [pro každou... Další příkaz](../../../visual-basic/language-reference/statements/for-each-next-statement.md), příklad ukazuje `For`... `Next` příkaz, který iteruje v sestupném pořadí. Tento příklad používá tato technika, protože `removeAt` metoda způsobí, že prvky po odebrané elementu, který chcete mít nižší hodnotu indexu.  
  
 [!code-vb[VbVbalrStatements#114](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_5.vb)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu prochází výčet, který je deklarovaný s použitím [Enum – příkaz](../../../visual-basic/language-reference/statements/enum-statement.md).  
  
 [!code-vb[VbVbalrStatements#116](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_6.vb)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu příkaz parametry použití třídy, která má přetížení operátoru pro `+`, `-`, `>=`, a `<=` operátory.  
  
 [!code-vb[VbVbalrStatements#117](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_7.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Generic.List%601>  
 [Struktury smyčky](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Příkaz While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [Příkaz Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [Vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Příkaz Exit](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [Kolekce](../../programming-guide/concepts/collections.md)
