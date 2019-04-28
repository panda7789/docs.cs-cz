---
title: For...Next – příkaz (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 5d47d57b75005d5c13dbf8633981dfb2d57d3e90
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638052"
---
# <a name="fornext-statement-visual-basic"></a>For...Next – příkaz (Visual Basic)
Opakuje skupinu příkazů zadaného počtu opakování.  
  
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
|`counter`|Vyžaduje `For` příkazu. Číselné proměnné. Řídicí proměnná smyčky. Další informace najdete v tématu [čítač Argument](#BKMK_Counter) dále v tomto tématu.|  
|`datatype`|Volitelné. Datový typ `counter`. Další informace najdete v tématu [čítač Argument](#BKMK_Counter) dále v tomto tématu.|  
|`start`|Povinný parametr. Číselný výraz. Počáteční hodnota `counter`.|  
|`end`|Povinný parametr. Číselný výraz. Konečná hodnota `counter`.|  
|`step`|Volitelné. Číselný výraz. Rozsah, pomocí kterého `counter` se zvýší pokaždé, když pomocí smyčky.|  
|`statements`|Volitelné. Jeden nebo více příkazů mezi `For` a `Next` , na kterých běží zadaný počet.|  
|`Continue For`|Volitelné. Předá řízení další iteraci smyčky.|  
|`Exit For`|Volitelné. Přenese ovládací prvek z celkového počtu `For` smyčky.|  
|`Next`|Povinný parametr. Ukončí definici `For` smyčky.|  
  
> [!NOTE]
>  `To` – Klíčové slovo se používá v tomto prohlášení k určení rozsahu čítače. Můžete také použít toto klíčové slovo v [vyberte... Case – příkaz](../../../visual-basic/language-reference/statements/select-case-statement.md) a v deklaracích pole. Další informace o deklarace pole najdete v tématu [příkazu Dim](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
## <a name="simple-examples"></a>Jednoduché příklady  
 Můžete použít `For`... `Next` struktury, pokud má být opakován sadu příkazů do sady počtu opakování.  
  
 V následujícím příkladu `index` proměnné začíná určitou hodnotou 1 a se zvýší při každé iteraci smyčky, končí po hodnotu `index` dosáhne 5.  
  
 [!code-vb[VbVbalrStatements#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#111)]  
  
 V následujícím příkladu `number` proměnné začíná na 2 a je sníží 0,25 při každé iteraci smyčky, končí po hodnotu `number` dosáhne hodnoty 0. `Step` Argument `-.25` snižuje hodnotu podle 0,25 při každé iteraci smyčky.  
  
 [!code-vb[VbVbalrStatements#112](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#112)]  
  
> [!TIP]
>  A [během... End While – příkaz](../../../visual-basic/language-reference/statements/while-end-while-statement.md) nebo [udělat... Příkaz LOOP](../../../visual-basic/language-reference/statements/do-loop-statement.md) dobře funguje i když nevíte předem jak často Pokud chcete spouštět příkazy ve smyčce. Ale očekáváte-li spustit s konkrétním počtem opakování, smyčky `For`... `Next` smyčky je lepší volbou. Když poprvé vstoupíte smyčky určíte počet iterací.  
  
## <a name="nesting-loops"></a>Vnoření smyčky  
 Je možné vnořovat `For` smyčky vložením v jednom průchodu v rámci jiného. Následující příklad ukazuje vnořené `For`... `Next` struktury, které mají různé krok hodnoty. Vnější smyčka vytvoří řetězec pro každou iteraci smyčky. Jako vnitřní smyčka dekrementuje proměnnou čítače smyčky pro každou iteraci smyčky.  
  
 [!code-vb[VbVbalrStatements#113](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#113)]  
  
 Při vnoření smyčky, každé smyčce musí mít jedinečný `counter` proměnné.  
  
 Lze také vnořit různé druhy řídicích struktur do jiné. Další informace najdete v tématu [vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-for-and-continue-for"></a>Pro ukončení a pokračovat pro  
 `Exit For` Příkazu se okamžitě ukončí `For`...`Next` řízení smyčky a přenosy příkazu, který následuje `Next` příkazu.  
  
 `Continue For` Ovládací prvek příkaz okamžitě přenese na další iteraci smyčky. Další informace najdete v tématu [pokračovat příkaz](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
 Následující příklad ukazuje použití `Continue For` a `Exit For` příkazy.  
  
 [!code-vb[VbVbalrStatements#115](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#115)]  
  
 Můžete vložit libovolný počet `Exit For` příkazů v `For`...`Next` Smyčka. Při použití v rámci vnořené `For`...`Next` smyčky, `Exit For` ukončení vnitřní smyčky a přenese ovládací prvek na další vyšší úroveň vnoření.  
  
 `Exit For` často se používá po vyhodnocení některé podmínky (třeba v `If`... `Then`... `Else` struktura). Můžete chtít použít `Exit For` byly splněny následující podmínky:  
  
- Pokračování k iteraci je zbytečné nebo nemožné. K tomuto stavu může vytvořit chybnou hodnotu nebo žádost o ukončení.  
  
- A `Try`... `Catch`... `Finally` příkaz zachytí výjimku. Můžete použít `Exit For` na konci `Finally` bloku.  
  
- Máte nekonečné smyčky, což je smyčku, která může běžet velká, nebo dokonce neomezený počet pokusů. Pokud zjistíte takové podmínky, můžete použít `Exit For` dostala mimo smyčku. Další informace najdete v tématu [udělat... Smyčky příkaz](../../../visual-basic/language-reference/statements/do-loop-statement.md).  
  
## <a name="technical-implementation"></a>Technická implementace  
 Když `For`... `Next` spuštění cyklu, Visual Basic vyhodnotí `start`, `end`, a `step`. Visual Basic vyhodnotí tyto hodnoty pouze v této době a pak přiřadí `start` k `counter`. Před příkazem blok spustí, Visual Basic porovná `counter` k `end`. Pokud `counter` je větší než `end` hodnotu (nebo menší, pokud `step` záporné), `For` skončení smyčky a řízení se předá příkazu, který následuje `Next` příkazu. V opačném případě spouští blok příkazů.  
  
 Pokaždé, když zjistí jazyka Visual Basic `Next` prohlášení, zvýší `counter` podle `step` a vrátí `For` příkazu. Znovu porovná `counter` k `end`, a znovu ho spouští bloku nebo ukončení smyčky, v závislosti na výsledek. Tento proces pokračuje, dokud `counter` předá `end` nebo `Exit For` příkaz dochází.  
  
 Smyčky nezastaví až do `counter` uplynutí `end`. Pokud `counter` rovná `end`, pokračuje smyčky. Porovnání, která určuje, jestli se má spustit blok `counter`  <=  `end` Pokud `step` kladné a `counter`  >=  `end` Pokud `step` je záporný.  
  
 Pokud se změní hodnota `counter` uvnitř smyčka, může být obtížnější ke čtení a ladění kódu. Změna hodnoty `start`, `end`, nebo `step` nemá vliv na hodnoty iterace, které byly určeny při prvním zadání smyčky.  
  
 Pokud byste vnořit smyčky, kompilátor signály chybě pokud narazí `Next` příkazu vnější úroveň vnoření před `Next` příkaz vnitřní úroveň. Však kompilátor to zjistit překrývající se chyby pouze v případě, že zadáte `counter` v každé `Next` příkazu.  
  
### <a name="step-argument"></a>Argument kroku  
 Hodnota `step` může být pozitivní nebo negativní. Tento parametr určuje zpracování smyčky podle následující tabulky:  
  
|**Hodnota kroku**|**Cyklus se opakuje, pokud**|  
|--------------------|--------------------------|  
|Kladná nebo nula.|`counter` <= `end`|  
|Záporný|`counter` >= `end`|  
  
 Výchozí hodnota `step` 1.  
  
### <a name="BKMK_Counter"></a> Argument čítače  
 Následující tabulka uvádí, zda `counter` definuje nová místní proměnná, které budou platit pro celou `For…Next` smyčky. Toto rozhodnutí závisí na tom, zda `datatype` existuje a zda `counter` je již definován.  
  
|Je `datatype` k dispozici?|Je `counter` již definována?|Výsledek (ať už `counter` definuje nová místní proměnná, které budou platit pro celou `For...Next` smyčky)|  
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|  
|Ne|Ano|Ne, protože `counter` je již definován. Pokud obor `counter` není místní k postupu, dojde k upozornění kompilace.|  
|Ne|Ne|Ano. Datový typ je odvozen z `start`, `end`, a `step` výrazy. Informace o odvození typu, najdete v části [Option Infer – příkaz](../../../visual-basic/language-reference/statements/option-infer-statement.md) a [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).|  
|Ano|Ano|Ano, ale pouze tehdy, pokud existující `counter` proměnná je definována mimo proces. Tato proměnná zůstane samostatnou. Pokud obor existující `counter` proměnná je lokální vzhledem k postupu, dojde k chybě kompilace.|  
|Ano|Ne|Ano.|  
  
 Datový typ `counter` Určuje typ iterace, který musí být jeden z následujících typů:  
  
- A `Byte`, `SByte`, `UShort`, `Short`, `UInteger`, `Integer`, `ULong`, `Long`, `Decimal`, `Single`, nebo `Double`.  
  
- Výčet, který je deklarovat s použitím [Enum – příkaz](../../../visual-basic/language-reference/statements/enum-statement.md).  
  
- `Object`.  
  
- Typ `T` , který má následující operátory, kde `B` je typ, který lze použít v `Boolean` výrazu.  
  
     `Public Shared Operator >= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator <= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator - (op1 As T, op2 As T) As T`  
  
     `Public Shared Operator + (op1 As T, op2 As T) As T`  
  
 Volitelně můžete zadat `counter` proměnné v `Next` příkazu. Tato syntaxe zlepšuje čitelnost programu, zejména v případě, že budete mít člověk vnořené `For` smyčky. Je nutné zadat proměnné, která se zobrazí v odpovídající `For` příkazu.  
  
 `start`, `end`, A `step` výrazy lze vyhodnotit na libovolný typ dat, která rozšiřuje na typ `counter`. Pokud používáte uživatelem definovaný typ pro `counter`, možná budete muset definovat `CType` operátor převodu k převedení typů `start`, `end`, nebo `step` typu `counter`.  
  
## <a name="example"></a>Příklad  
 Následující příklad odebere všechny prvky z obecného seznamu. Místo [For Each... Další příkaz](../../../visual-basic/language-reference/statements/for-each-next-statement.md), ukazuje příklad `For`... `Next` itinerací v sestupném pořadí. V příkladu používá tuto techniku, protože `removeAt` metoda způsobí, že prvky po odebraném prvku mají nižší hodnotu indexu.  
  
 [!code-vb[VbVbalrStatements#114](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#114)]  
  
## <a name="example"></a>Příklad  
 Následující příklad provede iteraci výčet, který je deklarován s použitím [Enum – příkaz](../../../visual-basic/language-reference/statements/enum-statement.md).  
  
 [!code-vb[VbVbalrStatements#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#116)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu, použijte parametry příkazu, který má přetížení operátoru pro třídu `+`, `-`, `>=`, a `<=` operátory.  
  
 [!code-vb[VbVbalrStatements#117](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#117)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic.List%601>
- [Struktury smyčky](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Příkaz While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Příkaz Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Příkaz Exit](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Kolekce](../../programming-guide/concepts/collections.md)
