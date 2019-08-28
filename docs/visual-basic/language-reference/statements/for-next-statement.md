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
ms.openlocfilehash: cafd59482036a598814dcd4815fa67a791580045
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046302"
---
# <a name="fornext-statement-visual-basic"></a>For...Next – příkaz (Visual Basic)

Opakuje skupinu příkazů v zadaném počtu opakování.

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

|Částí|Popis|
|----------|-----------------|
|`counter`|Vyžadováno v `For` příkazu. Číselná proměnná. Řídicí proměnná pro smyčku. Další informace najdete v části [argument čítače](#BKMK_Counter) dále v tomto tématu.|
|`datatype`|Volitelný parametr. Datový typ `counter`. Další informace najdete v části [argument čítače](#BKMK_Counter) dále v tomto tématu.|
|`start`|Povinný parametr. Číselný výraz. Počáteční hodnota `counter`.|
|`end`|Povinný parametr. Číselný výraz. Konečná hodnota `counter`.|
|`step`|Volitelný parametr. Číselný výraz. Hodnota, o kterou `counter` se při každém průchodu smyčkou zvýší.|
|`statements`|Volitelný parametr. Jeden nebo více příkazů mezi `For` a `Next` , které spouštějí zadaný počet opakování.|
|`Continue For`|Volitelný parametr. Převede řízení na další iteraci smyčky.|
|`Exit For`|Volitelný parametr. Přenese řízení ze `For` smyčky.|
|`Next`|Povinný parametr. Ukončí definici `For` smyčky.|

> [!NOTE]
> `To` Klíčové slovo se používá v tomto příkazu k určení rozsahu čítače. Toto klíčové slovo lze použít také v poli [Vybrat... Příkaz Case](../../../visual-basic/language-reference/statements/select-case-statement.md) a v deklaracích Array. Další informace o deklaracích pole naleznete v tématu [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).

## <a name="simple-examples"></a>Jednoduché příklady

Použijete `For`... `Next` struktura, pokud chcete zopakovat sadu příkazů a nastavit počet opakování.

V následujícím příkladu `index` proměnná začíná hodnotou 1 a je zvyšována s každou iterací smyčky, která končí po `index` hodnotě 5.

[!code-vb[VbVbalrStatements#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#111)]

V následujícím příkladu `number` proměnná začíná 2 a při každé iteraci smyčky je snížena o 0,25 až po `number` hodnotě dosáhne 0. `Step` Argumentsnižujehodnotuo0,25při`-.25` každé iteraci smyčky.

[!code-vb[VbVbalrStatements#112](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#112)]

> [!TIP]
> A [while... Příkaz End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md) nebo [do... Příkaz LOOP](../../../visual-basic/language-reference/statements/do-loop-statement.md) funguje dobře, Pokud nevíte, jak dlouho chcete spustit příkazy ve smyčce. Nicméně pokud očekáváte, že smyčka spustí určitou dobu, a `For`... `Next` smyčka je lepší volbou. Určíte počet iterací při prvním zadání smyčky.

## <a name="nesting-loops"></a>Vnořování smyček

Smyčky můžete vnořovat `For` vložením jedné smyčky do jiné. Následující příklad ukazuje vnořený `For`... `Next` struktury, které mají různé hodnoty kroku. Vnější smyčka vytvoří řetězec pro každou iteraci smyčky. Vnitřní smyčka snižuje proměnnou počítadla smyčky pro každou iteraci smyčky.

[!code-vb[VbVbalrStatements#113](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#113)]

Při vnořování smyček musí mít každá smyčka jedinečnou `counter` proměnnou.

Různé struktury ovládacích prvků lze také vnořovat mezi sebou. Další informace najdete v tématu [vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).

## <a name="exit-for-and-continue-for"></a>Ukončit po a pokračovat pro

Příkaz okamžitě ukončí `For`... `Exit For``Next` Loop a přenáší řízení příkazu, který následuje po `Next` příkazu.

`Continue For` Příkaz přenáší řízení okamžitě na další iteraci smyčky. Další informace najdete v tématu [příkaz Continue](../../../visual-basic/language-reference/statements/continue-statement.md).

Následující příklad ilustruje použití `Continue For` příkazů a. `Exit For`

[!code-vb[VbVbalrStatements#115](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#115)]

Do... můžete vložit `Exit For` libovolný počet příkazů... `For``Next` Procházet. Při použití v rámci `For`vnořeného...`Next` smyčky, `Exit For` ukončí vnitřní smyčku a přenáší řízení na další vyšší úroveň vnoření.

`Exit For`se často používá po vyhodnocení nějaké podmínky (například v `If`... `Then`... `Else` struktura). Je možné, že budete `Exit For` chtít použít následující podmínky:

- Pokračování iterace je zbytečné nebo nemožné. Tato podmínka může vytvořit chybná hodnota nebo žádost o ukončení.

- A `Try`... `Catch`... `Finally` příkaz zachytí výjimku. Můžete použít `Exit For` na konci `Finally` bloku.

- Máte nekonečné smyčky, což je smyčka, která by mohla běžet velkým nebo dokonce nekonečným počtem výskytů. Pokud tuto podmínku zjistíte, můžete ji použít `Exit For` k řídicímu panelu smyčky. Další informace najdete v části [do... Příkaz LOOP](../../../visual-basic/language-reference/statements/do-loop-statement.md)

## <a name="technical-implementation"></a>Technická implementace

`For`Když... Spustí se smyčka, Visual Basic `start`vyhodnotí `step`, `end`a. `Next` Visual Basic vyhodnotí tyto hodnoty pouze v tuto chvíli a pak `start` je `counter`přiřadí. Před spuštěním bloku příkazu Visual Basic porovnává `counter`. `end` Pokud `counter` je již větší `end` než hodnota (nebo menší, pokud `step` je záporná), `For` cyklus končí a ovládací prvek projde příkazu, který následuje po `Next` příkazu. V opačném případě se spustí blok příkazu.

Pokaždé, když Visual Basic nalezne `Next` příkaz, se `counter` zvýší `For` o `step` a vrátí se k příkazu. Znovu porovná `counter` s `end`a znovu buď spustí blok, nebo ukončí smyčku v závislosti na výsledku. Tento proces pokračuje do `counter` doby `end` , než `Exit For` se dokončí nebo dojde k příkazu.

Smyčka se neukončí `counter` , dokud `end`nebyla úspěšná. Pokud `counter` je`end`rovno, smyčka pokračuje. Porovnání, které určuje, zda má být blok spuštěn `counter` , `step` je  >=  `end` `counter`  <=  `end` -li kladné `step` a pokud je záporné.

Pokud změníte hodnotu `counter` uvnitř smyčky, váš kód může být obtížnější číst a ladit. Změna hodnoty `start`, `end`nebo `step` nemá vliv na hodnoty iterace, které byly určeny při prvním zadání smyčky.

Pokud vnořování smyček, kompilátor signalizuje chybu, pokud nalezne `Next` příkaz vnější úrovně vnořování `Next` před příkazem vnitřní úrovně. Kompilátor však může tuto chybu překrývají pouze v případě, že zadáte `counter` příkaz v `Next` každém příkazu.

### <a name="step-argument"></a>Argument kroku

Hodnota `step` může být buď kladná, nebo záporná. Tento parametr určuje zpracování smyčky podle následující tabulky:

|**Hodnota kroku**|**Smyčka se spustí, pokud**|
|--------------------|--------------------------|
|Kladná nebo nulová|`counter` <= `end`|
|Záporný|`counter` >= `end`|

Výchozí hodnota `step` je 1.

### <a name="BKMK_Counter"></a>Argument čítače

Následující tabulka uvádí, zda `counter` definuje novou místní proměnnou, která je vymezena na celou `For…Next` smyčku. Toto určení závisí na tom `datatype` , zda je přítomno a zda `counter` je již definován.

|Je `datatype` k dispozici?|Je `counter` již definováno?|Výsledek (určuje `counter` , zda je definována Nová místní proměnná, která je vymezena `For...Next` na celou smyčku)|
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|
|Ne|Ano|Ne, protože `counter` je již definován. Pokud rozsah `counter` není pro proceduru místní, dojde k upozornění při kompilaci.|
|Ne|Ne|Ano. Datový typ je odvozený z `start`výrazů, `end`a `step` . Informace o odvození typu naleznete v tématu [Option include Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) a [místní typ odvození](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).|
|Ano|Ano|Ano, ale pouze v případě, `counter` že je existující proměnná definována mimo proceduru. Tato proměnná zůstane oddělená. Pokud je rozsah existující `counter` proměnné místní pro proceduru, dojde k chybě při kompilaci.|
|Ano|Ne|Ano.|

Datový typ `counter` určuje typ iterace, který musí být jeden z následujících typů:

- A `Byte`, `SByte`, ,`UShort` ,`UInteger`, ,`ULong`,,,, nebo`Double`. `Short` `Integer` `Long` `Decimal` `Single`

- Výčet, který deklarujete pomocí [příkazu enum](../../../visual-basic/language-reference/statements/enum-statement.md).

- A `Object`.

- Typ `T` , který má následující operátory, kde `B` je typ, který `Boolean` lze použít ve výrazu.

  `Public Shared Operator >= (op1 As T, op2 As T) As B`

  `Public Shared Operator <= (op1 As T, op2 As T) As B`

  `Public Shared Operator - (op1 As T, op2 As T) As T`

  `Public Shared Operator + (op1 As T, op2 As T) As T`

Volitelně můžete zadat `counter` proměnnou `Next` v příkazu. Tato syntaxe vylepšuje čitelnost vašeho programu, zejména v případě, že máte vnořené `For` smyčky. Je nutné zadat proměnnou, která se zobrazí v příslušném `For` příkazu.

Výrazy `start` `counter`, `end`a mohoubýtvyhodnocenyjakolibovolnýdatovýtyp,kterýserozšiřujenatyp.`step` `counter`Použijete-li uživatelem definovaný typ pro, bude pravděpodobně nutné `CType` definovat operátor převodu `start`pro převod typů, `end`nebo `step` na typ `counter`.

## <a name="example"></a>Příklad

Následující příklad odebere všechny prvky z obecného seznamu. Místo [pro každý... Další příkaz](../../../visual-basic/language-reference/statements/for-each-next-statement.md), příklad ukazuje `For`... `Next` příkaz, který se opakuje v sestupném pořadí. Tento příklad používá tuto techniku, protože `removeAt` metoda způsobí, že prvky po odebraném elementu budou mít nižší hodnotu indexu.

[!code-vb[VbVbalrStatements#114](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#114)]

## <a name="example"></a>Příklad

Následující příklad prochází výčet deklarovaný pomocí [příkazu enum](../../../visual-basic/language-reference/statements/enum-statement.md).

[!code-vb[VbVbalrStatements#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#116)]

## <a name="example"></a>Příklad

V následujícím příkladu parametry příkazu používají třídu, `+`která má přetížení operátoru pro `<=` operátory, `-`, `>=`a.

[!code-vb[VbVbalrStatements#117](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#117)]

## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic.List%601>
- [Struktury smyčky](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Příkaz While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Příkaz Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Příkaz Exit](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Kolekce](../../programming-guide/concepts/collections.md)
