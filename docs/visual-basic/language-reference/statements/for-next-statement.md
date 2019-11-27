---
title: For...Next – příkaz
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
ms.openlocfilehash: 3cae44abb8e790542f11e6c5a5f1e317675ff988
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351185"
---
# <a name="fornext-statement-visual-basic"></a>For...Next – příkaz (Visual Basic)

Opakuje skupinu příkazů v zadaném počtu opakování.

## <a name="syntax"></a>Syntaxe

```vb
For counter [ As datatype ] = start To end [ Step step ]
    [ statements ]
    [ Continue For ]
    [ statements ]
    [ Exit For ]
    [ statements ]
Next [ counter ]
```

## <a name="parts"></a>Součásti

|Částí|Popis|
|----------|-----------------|
|`counter`|Vyžaduje se v příkazu `For`. Číselná proměnná. Řídicí proměnná pro smyčku. Další informace najdete v části [argument čítače](#BKMK_Counter) dále v tomto tématu.|
|`datatype`|Volitelná. Datový typ `counter`. Další informace najdete v části [argument čítače](#BKMK_Counter) dále v tomto tématu.|
|`start`|Požadováno. Číselný výraz. Počáteční hodnota `counter`.|
|`end`|Požadováno. Číselný výraz. Konečná hodnota `counter`.|
|`step`|Volitelná. Číselný výraz. Hodnota, o kterou `counter` se při každém průchodu smyčkou zvýší.|
|`statements`|Volitelná. Jeden nebo více příkazů mezi `For` a `Next`, které spouští zadaný počet opakování.|
|`Continue For`|Volitelná. Převede řízení na další iteraci smyčky.|
|`Exit For`|Volitelná. Přenáší řízení ze smyčky `For`.|
|`Next`|Požadováno. Ukončí definici smyčky `For`.|

> [!NOTE]
> Klíčové slovo `To` se v tomto příkazu používá k určení rozsahu čítače. Toto klíčové slovo lze použít také v poli [Vybrat... Příkaz Case](../../../visual-basic/language-reference/statements/select-case-statement.md) a v deklaracích Array. Další informace o deklaracích pole naleznete v tématu [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).

## <a name="simple-examples"></a>Jednoduché příklady

`Next` strukturu `For`... použijte v případě, že chcete zopakovat sadu příkazů, která je nastavená kolikrát.

V následujícím příkladu `index` proměnná začíná hodnotou 1 a při každé iteraci smyčky se zvyšuje s každou iterací smyčky, po jejichž uplynutí hodnota `index` dosáhne 5.

[!code-vb[VbVbalrStatements#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#111)]

V následujícím příkladu `number` proměnná začíná 2 a při každé iteraci smyčky se zkrátí 0,25 a po hodnotě `number` dosáhne 0. Argument `Step` `-.25` snižuje hodnotu 0,25 na každé iteraci smyčky.

[!code-vb[VbVbalrStatements#112](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#112)]

> [!TIP]
> A [while... Příkaz End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md) nebo [do... Příkaz LOOP](../../../visual-basic/language-reference/statements/do-loop-statement.md) funguje dobře, Pokud nevíte, jak dlouho chcete spustit příkazy ve smyčce. Nicméně pokud očekáváte, že smyčka spustí určitou dobu, `For`...`Next` smyčka je lepší volbou. Určíte počet iterací při prvním zadání smyčky.

## <a name="nesting-loops"></a>Vnořování smyček

Smyčky `For` můžete vnořovat vložením jedné smyčky do jiné. Následující příklad ukazuje vnořené `For`...`Next` struktury, které mají různé hodnoty kroku. Vnější smyčka vytvoří řetězec pro každou iteraci smyčky. Vnitřní smyčka snižuje proměnnou počítadla smyčky pro každou iteraci smyčky.

[!code-vb[VbVbalrStatements#113](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#113)]

Při vnořování smyček musí mít každá smyčka jedinečnou `counter` proměnnou.

Různé struktury ovládacích prvků lze také vnořovat mezi sebou. Další informace najdete v tématu [vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).

## <a name="exit-for-and-continue-for"></a>Ukončit po a pokračovat pro

Příkaz `Exit For` okamžitě ukončí `For`...`Next` Loop a přenáší řízení příkazu, který následuje po příkazu `Next`.

Příkaz `Continue For` přenáší řízení okamžitě na další iteraci smyčky. Další informace najdete v tématu [příkaz Continue](../../../visual-basic/language-reference/statements/continue-statement.md).

Následující příklad ukazuje použití příkazů `Continue For` a `Exit For`.

[!code-vb[VbVbalrStatements#115](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#115)]

Do `For`můžete přidat libovolný počet příkazů `Exit For`...`Next` Procházet. Při použití v rámci vnořených `For`...`Next` smyčky, `Exit For` ukončí vnitřní smyčku a přenáší řízení na další vyšší úroveň vnoření.

`Exit For` se často používá po vyhodnocení nějaké podmínky (například ve struktuře `If`...`Then`...`Else`). Můžete chtít použít `Exit For` pro následující podmínky:

- Pokračování iterace je zbytečné nebo nemožné. Tato podmínka může vytvořit chybná hodnota nebo žádost o ukončení.

- Příkaz `Try`...`Catch`...`Finally` zachytává výjimku. `Exit For` můžete použít na konci bloku `Finally`.

- Máte nekonečné smyčky, což je smyčka, která by mohla běžet velkým nebo dokonce nekonečným počtem výskytů. Pokud tuto podmínku zjistíte, můžete ji použít `Exit For` a řídicí smyčku. Další informace najdete v části [do... Příkaz LOOP](../../../visual-basic/language-reference/statements/do-loop-statement.md)

## <a name="technical-implementation"></a>Technická implementace

Když se spustí `For`...`Next` smyčka Visual Basic vyhodnocuje `start`, `end`a `step`. Visual Basic vyhodnotí tyto hodnoty pouze v tuto chvíli a potom přiřadí `start` k `counter`. Než se spustí blok příkazu, Visual Basic porovná `counter` s `end`. Pokud je již `counter` větší než hodnota `end` (nebo menší, pokud je `step` záporné), cyklus `For` končí a řízení projde příkazu, který následuje po příkazu `Next`. V opačném případě se spustí blok příkazu.

Pokaždé, když Visual Basic nalezne `Next` příkaz, zvýší `counter` `step` a vrátí se do příkazu `For`. Znovu porovná `counter` `end`a znovu buď spustí blok, nebo ukončí smyčku v závislosti na výsledku. Tento proces pokračuje, dokud `counter` neprojde `end` nebo byl zjištěn příkaz `Exit For`.

Smyčka se neukončí, dokud `counter` neprojde `end`. Pokud je `counter` rovna `end`, smyčka pokračuje. Porovnání, které určuje, zda je možné spustit blok, je `counter` <= `end` Pokud `step` kladné a `counter` >= `end`, pokud je `step` záporné.

Pokud změníte hodnotu `counter` dovnitř smyčky, váš kód může být obtížnější číst a ladit. Změna hodnoty `start`, `end`nebo `step` nemá vliv na hodnoty iterace, které byly určeny při prvním zadání smyčky.

Pokud vnořování smyček, kompilátor signalizuje chybu, pokud nalezne příkaz `Next` úrovně vnějšího vnoření před příkaz `Next` vnitřní úrovně. Kompilátor však může tuto chybu překrývají pouze v případě, že zadáte `counter` v každém příkazu `Next`.

### <a name="step-argument"></a>Argument kroku

Hodnota `step` může být buď kladná, nebo záporná. Tento parametr určuje zpracování smyčky podle následující tabulky:

|**Hodnota kroku**|**Smyčka se spustí, pokud**|
|--------------------|--------------------------|
|Kladná nebo nulová|`counter` <= `end`|
|Záporný|`counter` >= `end`|

Výchozí hodnota `step` je 1.

### <a name="BKMK_Counter"></a>Argument čítače

Následující tabulka uvádí, zda `counter` definuje novou místní proměnnou vymezenou na celou `For…Next` smyčku. Toto určení závisí na tom, zda je `datatype` k dispozici a zda `counter` již byla definována.

|Je `datatype` k dispozici?|Je `counter` již definováno?|Výsledek (bez ohledu na to, zda `counter` definuje novou místní proměnnou vymezenou na celou `For...Next` smyčku)|
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|
|Ne|Ano|Ne, protože `counter` je již definován. Pokud rozsah `counter` není místní s postupem, dojde k upozornění v době kompilace.|
|Ne|Ne|Ano. Datový typ je odvozený z výrazů `start`, `end`a `step`. Informace o odvození typu naleznete v tématu [Option include Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) a [místní typ odvození](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).|
|Ano|Ano|Ano, ale pouze v případě, že je existující proměnná `counter` definovaná mimo proceduru. Tato proměnná zůstane oddělená. Pokud je rozsah existující proměnné `counter` místní pro proceduru, dojde k chybě při kompilaci.|
|Ano|Ne|Ano.|

Datový typ `counter` určuje typ iterace, který musí být jeden z následujících typů:

- `Byte`, `SByte`, `UShort``Short`, `UInteger`, `Integer`, `ULong`, `Long`, `Decimal`, `Single`nebo `Double`.

- Výčet, který deklarujete pomocí [příkazu enum](../../../visual-basic/language-reference/statements/enum-statement.md).

- `Object`.

- Typ `T`, který má následující operátory, kde `B` je typ, který lze použít ve výrazu `Boolean`.

  `Public Shared Operator >= (op1 As T, op2 As T) As B`

  `Public Shared Operator <= (op1 As T, op2 As T) As B`

  `Public Shared Operator - (op1 As T, op2 As T) As T`

  `Public Shared Operator + (op1 As T, op2 As T) As T`

Volitelně můžete zadat `counter` proměnnou v příkazu `Next`. Tato syntaxe vylepšuje čitelnost vašeho programu, zejména v případě, že máte vnořené `For` smyčky. Je nutné zadat proměnnou, která se zobrazí v příslušném příkazu `For`.

Výrazy `start`, `end`a `step` lze vyhodnotit na libovolný datový typ, který se rozšíří na typ `counter`. Použijete-li uživatelem definovaný typ pro `counter`, bude pravděpodobně nutné definovat `CType` operátor převodu pro převod typů `start`, `end`nebo `step` na typ `counter`.

## <a name="example"></a>Příklad

Následující příklad odebere všechny prvky z obecného seznamu. Místo [pro každý... V následujícím příkazu](../../../visual-basic/language-reference/statements/for-each-next-statement.md)příklad ukazuje příkaz `For`...`Next`, který se opakuje v sestupném pořadí. Tento příklad používá tuto techniku, protože metoda `removeAt` způsobí, že prvky po odebraném prvku budou mít nižší hodnotu indexu.

[!code-vb[VbVbalrStatements#114](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#114)]

## <a name="example"></a>Příklad

Následující příklad prochází výčet deklarovaný pomocí [příkazu enum](../../../visual-basic/language-reference/statements/enum-statement.md).

[!code-vb[VbVbalrStatements#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#116)]

## <a name="example"></a>Příklad

V následujícím příkladu parametry příkazu používají třídu, která má přetížení operátoru pro operátory `+`, `-`, `>=`a `<=`.

[!code-vb[VbVbalrStatements#117](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#117)]

## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic.List%601>
- [Struktury smyčky](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Příkaz While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Příkaz Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Příkaz Exit](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Kolekce](../../programming-guide/concepts/collections.md)
