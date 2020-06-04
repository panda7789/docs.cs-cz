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
ms.openlocfilehash: 6896c6cfb4ec5d6207011e56b72639c459120e53
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404638"
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

|Část|Description|
|----------|-----------------|
|`counter`|Vyžadováno v `For` příkazu. Číselná proměnná. Řídicí proměnná pro smyčku. Další informace najdete v části [argument čítače](#BKMK_Counter) dále v tomto tématu.|
|`datatype`|Nepovinný parametr. Datový typ `counter` . Další informace najdete v části [argument čítače](#BKMK_Counter) dále v tomto tématu.|
|`start`|Povinná hodnota. Číselný výraz. Počáteční hodnota `counter` .|
|`end`|Povinná hodnota. Číselný výraz. Konečná hodnota `counter` .|
|`step`|Nepovinný parametr. Číselný výraz. Hodnota, o kterou `counter` se při každém průchodu smyčkou zvýší.|
|`statements`|Nepovinný parametr. Jeden nebo více příkazů mezi `For` a `Next` , které spouštějí zadaný počet opakování.|
|`Continue For`|Nepovinný parametr. Převede řízení na další iteraci smyčky.|
|`Exit For`|Nepovinný parametr. Přenese řízení ze `For` smyčky.|
|`Next`|Povinná hodnota. Ukončí definici `For` smyčky.|

> [!NOTE]
> `To`Klíčové slovo se používá v tomto příkazu k určení rozsahu čítače. Toto klíčové slovo lze použít také v poli [Vybrat... Příkaz Case](select-case-statement.md) a v deklaracích Array. Další informace o deklaracích pole naleznete v tématu [Dim Statement](dim-statement.md).

## <a name="simple-examples"></a>Jednoduché příklady

`For`Strukturu... použijete, `Next` Pokud chcete zopakovat sadu příkazů a nastavit počet opakování.

V následujícím příkladu `index` Proměnná začíná hodnotou 1 a je zvyšována s každou iterací smyčky, která končí po hodnotě `index` 5.

[!code-vb[VbVbalrStatements#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#111)]

V následujícím příkladu `number` Proměnná začíná 2 a při každé iteraci smyčky je snížena o 0,25 až po hodnotě `number` dosáhne 0. `Step`Argument `-.25` snižuje hodnotu o 0,25 při každé iteraci smyčky.

[!code-vb[VbVbalrStatements#112](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#112)]

> [!TIP]
> A [while... Příkaz End While](while-end-while-statement.md) nebo [do... Příkaz LOOP](do-loop-statement.md) funguje dobře, Pokud nevíte, jak dlouho chcete spustit příkazy ve smyčce. Nicméně pokud očekáváte, že se má smyčka spustit určitou dobu, `For` `Next` je lepší volbou smyčka.... Určíte počet iterací při prvním zadání smyčky.

## <a name="nesting-loops"></a>Vnořování smyček

Smyčky můžete vnořovat vložením `For` jedné smyčky do jiné. Následující příklad ukazuje vnořené `For` ... `Next` struktury, které mají různé hodnoty kroku. Vnější smyčka vytvoří řetězec pro každou iteraci smyčky. Vnitřní smyčka snižuje proměnnou počítadla smyčky pro každou iteraci smyčky.

[!code-vb[VbVbalrStatements#113](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#113)]

Při vnořování smyček musí mít každá smyčka jedinečnou `counter` proměnnou.

Různé struktury ovládacích prvků lze také vnořovat mezi sebou. Další informace najdete v tématu [vnořené řídicí struktury](../../programming-guide/language-features/control-flow/nested-control-structures.md).

## <a name="exit-for-and-continue-for"></a>Ukončit po a pokračovat pro

`Exit For`Příkaz okamžitě ukončí `For` ...`Next` Loop a přenáší řízení příkazu, který následuje po `Next` příkazu.

`Continue For`Příkaz přenáší řízení okamžitě na další iteraci smyčky. Další informace najdete v tématu [příkaz Continue](continue-statement.md).

Následující příklad ilustruje použití `Continue For` `Exit For` příkazů a.

[!code-vb[VbVbalrStatements#115](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#115)]

Do... můžete vložit libovolný počet `Exit For` příkazů `For` ...`Next` Procházet. Při použití v rámci vnořeného `For` ...`Next` smyčky, `Exit For` ukončí vnitřní smyčku a přenáší řízení na další vyšší úroveň vnoření.

`Exit For`se často používá po vyhodnocení nějaké podmínky (například v `If` ... `Then` ...`Else` struktura). Je možné, že budete chtít použít `Exit For` následující podmínky:

- Pokračování iterace je zbytečné nebo nemožné. Tato podmínka může vytvořit chybná hodnota nebo žádost o ukončení.

- A.. `Try` . `Catch` ...`Finally` příkaz zachytí výjimku. Můžete použít `Exit For` na konci `Finally` bloku.

- Máte nekonečné smyčky, což je smyčka, která by mohla běžet velkým nebo dokonce nekonečným počtem výskytů. Pokud tuto podmínku zjistíte, můžete ji použít `Exit For` k řídicímu panelu smyčky. Další informace najdete v části [do... Příkaz LOOP](do-loop-statement.md)

## <a name="technical-implementation"></a>Technická implementace

Při `For` spuštění smyčky... `Next` Visual Basic vyhodnotí `start` , `end` a `step` . Visual Basic vyhodnotí tyto hodnoty pouze v tuto chvíli a pak je přiřadí `start` `counter` . Před spuštěním bloku příkazu Visual Basic porovnává `counter` `end` . Pokud `counter` je již větší než `end` hodnota (nebo menší, pokud `step` je záporná), `For` cyklus končí a ovládací prvek projde příkazu, který následuje po `Next` příkazu. V opačném případě se spustí blok příkazu.

Pokaždé, když Visual Basic nalezne `Next` příkaz, se zvýší `counter` o `step` a vrátí se k `For` příkazu. Znovu porovná `counter` s `end` a znovu buď spustí blok, nebo ukončí smyčku v závislosti na výsledku. Tento proces pokračuje do doby, než se dokončí `counter` `end` nebo dojde `Exit For` k příkazu.

Smyčka se neukončí `counter` , dokud nebyla úspěšná `end` . Pokud `counter` je rovno `end` , smyčka pokračuje. Porovnání, které určuje, zda má být blok spuštěn, je- `counter`  <=  `end` li `step` kladné a `counter`  >=  `end` Pokud `step` je záporné.

Pokud změníte hodnotu `counter` uvnitř smyčky, váš kód může být obtížnější číst a ladit. Změna hodnoty `start` , `end` nebo `step` nemá vliv na hodnoty iterace, které byly určeny při prvním zadání smyčky.

Pokud vnořování smyček, kompilátor signalizuje chybu, pokud nalezne `Next` příkaz vnější úrovně vnořování před `Next` příkazem vnitřní úrovně. Kompilátor však může tuto chybu překrývají pouze v případě, že zadáte `counter` příkaz v každém `Next` příkazu.

### <a name="step-argument"></a>Argument kroku

Hodnota `step` může být buď kladná, nebo záporná. Tento parametr určuje zpracování smyčky podle následující tabulky:

|**Hodnota kroku**|**Smyčka se spustí, pokud**|
|--------------------|--------------------------|
|Kladná nebo nulová|`counter` <= `end`|
|Záporný|`counter` >= `end`|

Výchozí hodnota `step` je 1 MB.

### <a name="counter-argument"></a><a name="BKMK_Counter"></a>Argument čítače

Následující tabulka uvádí, zda `counter` definuje novou místní proměnnou, která je vymezena na celou `For…Next` smyčku. Toto určení závisí na tom, zda `datatype` je přítomno a zda `counter` je již definován.

|Je k `datatype` dispozici?|Je `counter` již definováno?|Výsledek (určuje, zda je `counter` definována Nová místní proměnná, která je vymezena na celou `For...Next` smyčku)|
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|
|Ne|Ano|Ne, protože `counter` je již definován. Pokud rozsah `counter` není pro proceduru místní, dojde k upozornění při kompilaci.|
|Ne|Ne|Yes. Datový typ je odvozený z `start` `end` výrazů, a `step` . Informace o odvození typu naleznete v tématu [Option include Statement](option-infer-statement.md) a [místní typ odvození](../../programming-guide/language-features/variables/local-type-inference.md).|
|Ano|Ano|Ano, ale pouze v případě, že `counter` je existující proměnná definována mimo proceduru. Tato proměnná zůstane oddělená. Pokud je rozsah existující `counter` proměnné místní pro proceduru, dojde k chybě při kompilaci.|
|Ano|No|Yes.|

Datový typ `counter` Určuje typ iterace, který musí být jeden z následujících typů:

- A `Byte` , `SByte` , `UShort` , `Short` , `UInteger` , `Integer` , `ULong` , `Long` , `Decimal` , `Single` , nebo `Double` .

- Výčet, který deklarujete pomocí [příkazu enum](enum-statement.md).

- A `Object` .

- Typ `T` , který má následující operátory, kde `B` je typ, který lze použít ve `Boolean` výrazu.

  `Public Shared Operator >= (op1 As T, op2 As T) As B`

  `Public Shared Operator <= (op1 As T, op2 As T) As B`

  `Public Shared Operator - (op1 As T, op2 As T) As T`

  `Public Shared Operator + (op1 As T, op2 As T) As T`

Volitelně můžete zadat `counter` proměnnou v `Next` příkazu. Tato syntaxe vylepšuje čitelnost vašeho programu, zejména v případě, že máte vnořené `For` smyčky. Je nutné zadat proměnnou, která se zobrazí v příslušném `For` příkazu.

`start`Výrazy, `end` a `step` mohou být vyhodnoceny jako libovolný datový typ, který se rozšiřuje na typ `counter` . Použijete-li uživatelem definovaný typ pro `counter` , bude pravděpodobně nutné definovat `CType` operátor převodu pro převod typů `start` , `end` nebo `step` na typ `counter` .

## <a name="example"></a>Příklad

Následující příklad odebere všechny prvky z obecného seznamu. Místo [pro každý... V následujícím příkazu](for-each-next-statement.md)příklad ukazuje `For` příkaz... `Next` , který se opakuje v sestupném pořadí. Tento příklad používá tuto techniku, protože `removeAt` metoda způsobí, že prvky po odebraném elementu budou mít nižší hodnotu indexu.

[!code-vb[VbVbalrStatements#114](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#114)]

## <a name="example"></a>Příklad

Následující příklad prochází výčet deklarovaný pomocí [příkazu enum](enum-statement.md).

[!code-vb[VbVbalrStatements#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#116)]

## <a name="example"></a>Příklad

V následujícím příkladu parametry příkazu používají třídu, která má přetížení operátoru pro `+` `-` operátory,, a `>=` `<=` .

[!code-vb[VbVbalrStatements#117](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#117)]

## <a name="see-also"></a>Viz také

- <xref:System.Collections.Generic.List%601>
- [Struktury smyčky](../../programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While – příkaz](while-end-while-statement.md)
- [Do...Loop – příkaz](do-loop-statement.md)
- [Vnořené řídicí struktury](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit – příkaz](exit-statement.md)
- [Kolekce](../../programming-guide/concepts/collections.md)
