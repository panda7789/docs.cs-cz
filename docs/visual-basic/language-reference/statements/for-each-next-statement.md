---
title: For Each...Next – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ForEach
- vb.ForEachNext
- vb.Each
- ForEachNext
helpviewer_keywords:
- infinite loops
- Next statement [Visual Basic], For Each...Next
- endless loops
- loop structures [Visual Basic], For Each...Next
- loops, endless
- Each keyword [Visual Basic]
- instructions, repeating
- For Each statement [Visual Basic]
- collections, instruction repetition
- loops, infinite
- For Each...Next statements
- For keyword [Visual Basic], For Each...Next statements
- Exit statement [Visual Basic], For Each...Next statements
- iteration
ms.assetid: ebce3120-95c3-42b1-b70b-fa7da40c75e2
ms.openlocfilehash: ebfd05a39c290e379bea2b925e7ea30c40d303fe
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046318"
---
# <a name="for-eachnext-statement-visual-basic"></a>For Each...Next – příkaz (Visual Basic)

Opakuje skupinu příkazů pro každý prvek v kolekci.

## <a name="syntax"></a>Syntaxe

```
For Each element [ As datatype ] In group
    [ statements ]
    [ Continue For ]
    [ statements ]
    [ Exit For ]
    [ statements ]
Next [ element ]
```

## <a name="parts"></a>Součásti

|Termín|Definice|
|---|---|
|`element`|Vyžadováno v `For Each` příkazu. Volitelné v `Next` příkazu. Variabilní. Slouží k iterování prvků kolekce.|
|`datatype`|Volitelné, [`Option Infer`](option-infer-statement.md) Pokud je zapnuto (výchozí) `element` nebo je již deklarováno; `Option Infer` požadováno, pokud `element` je vypnuto a ještě není deklarováno. Datový typ `element`.|
|`group`|Povinný parametr. Proměnná s typem, který je typem kolekce nebo objektem. Odkazuje na kolekci, na které `statements` se mají opakovat.|
|`statements`|Volitelný parametr. Jeden nebo více příkazů mezi `For Each` a `Next` , které jsou spuštěny na `group`jednotlivých položkách v.|
|`Continue For`|Volitelný parametr. Přenese řízení na začátek `For Each` smyčky.|
|`Exit For`|Volitelný parametr. Přenese řízení ze `For Each` smyčky.|
|`Next`|Povinný parametr. Ukončí definici `For Each` smyčky.|

## <a name="simple-example"></a>Jednoduchý příklad

`For Each`Použít... `Next` smyčka, pokud chcete opakovat sadu příkazů pro každý prvek kolekce nebo pole.

> [!TIP]
> A [pro... Další příkaz](../../../visual-basic/language-reference/statements/for-next-statement.md) funguje dobře, když můžete přidružit každou iteraci smyčky s proměnnou ovládacího prvku a určit počáteční a konečné hodnoty této proměnné. Pokud však pracujete s kolekcí, koncept počátečních a konečných hodnot není smysluplný a Vy nevíte, kolik prvků kolekce má. V tomto druhu případu `For Each`... `Next` smyčka je často lepší volbou.

V následujícím příkladu `For Each`...`Next` příkaz prochází všechny prvky kolekce seznamů.

[!code-vb[VbVbalrStatements#121](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#121)]

Další příklady najdete v tématu [kolekce](../../../standard/collections/index.md) a [pole](../../../visual-basic/programming-guide/language-features/arrays/index.md).

## <a name="nested-loops"></a>Vnořené smyčky

Smyčky můžete vnořovat `For Each` vložením jedné smyčky do jiné.

Následující příklad ukazuje vnořený `For Each`...`Next` struktury.

[!code-vb[VbVbalrStatements#122](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#122)]

Při vnořování smyček musí mít každá smyčka jedinečnou `element` proměnnou.

Můžete také vnořit různé druhy řídicích struktur mezi sebou. Další informace najdete v tématu [vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).

## <a name="exit-for-and-continue-for"></a>Ukončit po a pokračovat pro

Příkaz [Exit for](../../../visual-basic/language-reference/statements/exit-statement.md) způsobí, že `For`provádění skončí...`Next` Loop a přenáší řízení příkazu, který následuje po `Next` příkazu.

`Continue For` Příkaz přenáší řízení okamžitě na další iteraci smyčky. Další informace najdete v tématu [příkaz Continue](../../../visual-basic/language-reference/statements/continue-statement.md).

Následující příklad ukazuje, jak použít `Continue For` příkazy a. `Exit For`

[!code-vb[VbVbalrStatements#123](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#123)]

Do smyčky můžete vložit libovolný počet `Exit For` příkazů. `For Each` Při použití v rámci `For Each` vnořených smyček `Exit For` způsobí, že provádění ukončí vnitřní smyčku a přenáší řízení na další vyšší úroveň vnoření.

`Exit For`se často používá po vyhodnocení nějaké podmínky, například v `If`... `Then`... `Else` struktura. Je možné, že budete `Exit For` chtít použít následující podmínky:

- Pokračování iterace je zbytečné nebo nemožné. To může být způsobeno chybnou hodnotou nebo žádostí o ukončení.

- Výjimka je zachycena v `Try`... `Catch`... `Finally`. Můžete použít `Exit For` na konci `Finally` bloku.

- Existuje nekonečné smyčka, což je smyčka, která by mohla běžet velkým nebo dokonce nekonečným počtem výskytů. Pokud tuto podmínku zjistíte, můžete ji použít `Exit For` k řídicímu panelu smyčky. Další informace najdete v části [do... Příkaz LOOP](../../../visual-basic/language-reference/statements/do-loop-statement.md)

## <a name="iterators"></a>Iterátory

Pomocí iterátoru můžete provést vlastní iteraci v kolekci. Iterátor může být funkce nebo `Get` přistupující objekt. Pomocí `Yield` příkazu vrátí každý prvek kolekce po jednom.

Zavoláte iterátor pomocí `For Each...Next` příkazu. Každá iterace `For Each` smyčky volá iterátor. Při dosažení `Yield` příkazu v iterátoru je vrácen výraz v příkazu a aktuální umístění v kódu je uchováno. `Yield` Spuštění je restartováno z tohoto umístění při příštím volání iterátoru.

V následujícím příkladu je použita funkce iterátoru. Funkce iterátoru obsahuje `Yield` příkaz, který je uvnitř [... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) smyčka V metodě Každá iterace `For Each` těla příkazu vytvoří volání funkce iterátoru, která pokračuje k dalšímu `Yield` příkazu. `ListEvenNumbers`

[!code-vb[VbVbalrStatements#127](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#127)]

Další informace naleznete v tématu [iterátory](../../programming-guide/concepts/iterators.md), [příkazy yield](../../../visual-basic/language-reference/statements/yield-statement.md)a [iterátor](../../../visual-basic/language-reference/modifiers/iterator.md).

## <a name="technical-implementation"></a>Technická implementace

`For Each`Když...`Next` příkaz se spustí, Visual Basic vyhodnocuje kolekci pouze jednou, a to před spuštěním smyčky. Pokud váš příkaz zablokuje `group`změny `element` nebo tyto změny neovlivňují iteraci smyčky.

Po úspěšném přiřazení `element`všech prvků v kolekci se `For Each` smyčka zastaví a řízení projde příkazem, který následuje `Next` za příkazem.

Pokud je nastavená [možnost odvodit](option-infer-statement.md) (výchozí nastavení), kompilátor Visual Basic může odvodit datový typ `element`. Pokud je vypnutá a `element` nebyla deklarována vně smyčky, je nutné ji deklarovat `For Each` v příkazu. Chcete-li `element` explicitně deklarovat datový typ, `As` použijte klauzuli. Není-li datový typ elementu definován mimo `For Each`... `Next` konstrukce, její obor je tělo smyčky. Všimněte si, že nemůžete deklarovat `element` vnější i uvnitř smyčky.

Volitelně můžete zadat `element` `Next` v příkazu. To zlepšuje čitelnost vašeho programu, zejména v případě, že máte vnořené `For Each` smyčky. Je nutné zadat stejnou proměnnou jako ta, která se zobrazí v příslušném `For Each` příkazu.

Je možné, že se nebudete muset `element` vyhnout změnám hodnoty uvnitř smyčky. To může ztížit čtení a ladění kódu. Změna hodnoty `group` nemá vliv na kolekci nebo její prvky, které byly určeny při prvním zadání smyčky.

Při vnořování smyček se při výskytu `Next` příkazu na úrovni vnějšího vnoření vyskytne v případě, že došlo `Next` k chybě, kompilátor signalizuje chybu. Kompilátor však může tuto chybu překrývají pouze v případě, že zadáte `element` příkaz v `Next` každém příkazu.

Pokud váš kód závisí na procházení kolekce v určitém pořadí, `For Each`... `Next` smyčka není nejlepší volbou, pokud neznáte charakteristiky objektu Enumerator, které kolekce zpřístupňuje. Pořadí průchodu není určeno Visual Basic, ale <xref:System.Collections.IEnumerator.MoveNext%2A> metodou objektu Enumerator. Proto možná nebudete moci předpovědět, který prvek kolekce je první, který má být vrácen v `element`nebo který je další, který bude vrácen po daném prvku. Můžete dosáhnout spolehlivější výsledků pomocí jiné struktury smyčky, například `For`... `Next` nebo`Do`... `Loop`.

Modul runtime musí být schopný převést elementy v `group` na. `element` Příkaz [`Option Strict`] řídí, zda jsou povoleny rozšiřující i zúžené převody (`Option Strict` je vypnutý, její výchozí hodnota) nebo zda jsou povoleny`Option Strict` pouze rozšiřující převody. Další informace najdete v tématu [zúžení převodů](#narrowing-conversions).

Datový typ `group` musí být odkazový typ, který odkazuje na kolekci nebo pole, které je vyčíslitelné. Nejčastěji to znamená, že `group` odkazuje na objekt, který <xref:System.Collections.IEnumerable> implementuje rozhraní `System.Collections` oboru názvů nebo <xref:System.Collections.Generic.IEnumerable%601> rozhraní `System.Collections.Generic` oboru názvů. `System.Collections.IEnumerable`<xref:System.Collections.IEnumerable.GetEnumerator%2A> definuje metodu, která vrací objekt enumerátoru pro kolekci. Objekt `System.Collections.IEnumerator` enumerátoru implementuje rozhraní <xref:System.Collections.IEnumerator.Current%2A> `System.Collections` oboru názvů a <xref:System.Collections.IEnumerator.Reset%2A> zpřístupňuje vlastnost a metody a <xref:System.Collections.IEnumerator.MoveNext%2A> . Visual Basic je používá k procházení kolekce.

### <a name="narrowing-conversions"></a>Zužující převody

Pokud `Option Strict` je nastaven na `On`, zužující převody obvykle způsobují chyby kompilátoru. V příkazu však převod z prvků v `group` na `element` je vyhodnocován a proveden v době běhu a chyby kompilátoru způsobené zužujícími převody jsou potlačeny. `For Each`

V následujícím příkladu přiřazení `m` jako počáteční hodnotu pro `n` není zkompilováno, pokud `Option Strict` je `Integer` zapnuto, protože převod typu `Long` na je zužující převod. V příkazu však není hlášena žádná chyba kompilátoru, i když `number` přiřazení vyžaduje stejný převod z `Long` na `Integer`. `For Each` V příkazu, který obsahuje velké číslo, dojde k chybě za běhu při <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A> použití na velké číslo. `For Each`

[!code-vb[VbVbalrStatements#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class3.vb#89)]

### <a name="ienumerator-calls"></a>Volání IEnumerator

Při provádění `For Each`... Spustí se smyčka, Visual Basic ověří `group` , zda odkazuje na platný objekt kolekce. `Next` V takovém případě vyvolá výjimku. V opačném případě volá <xref:System.Collections.IEnumerator.MoveNext%2A> metodu <xref:System.Collections.IEnumerator.Current%2A> a vlastnost objektu Enumerator pro návrat prvního prvku. Pokud `MoveNext` znamená, že neexistuje žádný další prvek, tedy pokud je kolekce prázdná `For Each` , smyčka se zastaví a ovládací prvek projde příkazem, který následuje `Next` za příkazem. V opačném případě `element` Visual Basic nastaví na první prvek a spustí blok příkazu.

Pokaždé, když Visual Basic nalezne `Next` příkaz, vrátí `For Each` se do příkazu. Znovu volá `MoveNext` a `Current` vrátí další prvek a znovu buď spustí blok, nebo zastaví smyčku v závislosti na výsledku. Tento proces pokračuje, `MoveNext` dokud neindikuje, že není k dispozici `Exit For` žádný další prvek nebo příkaz.

**Úprava kolekce.** Objekt enumerátoru vrácený <xref:System.Collections.IEnumerable.GetEnumerator%2A> normálně neumožňuje změnit kolekci přidáním, odstraněním, nahrazením nebo změnou pořadí všech prvků. Pokud kolekci změníte po zahájení `For Each`... smyčka, objekt enumerátoru se stala neplatnou a další pokus o přístup k elementu <xref:System.InvalidOperationException> způsobí výjimku. `Next`

Toto blokování úprav však není určeno Visual Basic, ale spíše implementací <xref:System.Collections.IEnumerable> rozhraní. Je možné implementovat `IEnumerable` způsobem, který umožňuje úpravu během iterace. Pokud zvažujete, že provádíte tuto dynamickou úpravu, ujistěte se, že rozumíte charakteristikám `IEnumerable` implementace v kolekci, kterou používáte.

**Úpravy prvků kolekce.** Vlastnost objektu Enumerator je určena [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md)a vrátí místní kopii každého prvku kolekce. <xref:System.Collections.IEnumerator.Current%2A> To znamená, že nemůžete upravit prvky samotné v `For Each`... `Next` smyčka. Všechny změny, které provedete, ovlivní jenom `Current` místní kopii z a nereflektují se zpátky do příslušné kolekce. Nicméně pokud je prvek odkazový typ, můžete upravit členy instance, na kterou odkazuje. Následující příklad upravuje `BackColor` člena každého `thisControl` prvku. Nemůžete však změnit `thisControl` sám sebe.

```vb
Sub lightBlueBackground(ByVal thisForm As System.Windows.Forms.Form)
    For Each thisControl As System.Windows.Forms.Control In thisForm.Controls
        thisControl.BackColor = System.Drawing.Color.LightBlue
    Next thisControl
End Sub
```

Předchozí příklad může změnit `BackColor` člena každého `thisControl` prvku, i když nemůže sám změnit `thisControl` .

**Procházení polí.** Vzhledem k tomu <xref:System.Collections.IEnumerable> <xref:System.Array> ,žetřídaimplementujerozhraní,všechnapole<xref:System.Array.GetEnumerator%2A> zpřístupňují metodu. To znamená, že můžete iterovat přes pole s `For Each`... `Next` smyčka. Lze však číst pouze prvky pole. Nemůžete je změnit.

## <a name="example"></a>Příklad

Následující příklad zobrazí seznam všech složek v C:\. adresáře pomocí <xref:System.IO.DirectoryInfo> třídy.

[!code-vb[VbVbalrStatements#124](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#124)]

## <a name="example"></a>Příklad

Následující příklad znázorňuje postup pro řazení kolekce. Příklad řadí instance `Car` třídy, které jsou uloženy <xref:System.Collections.Generic.List%601>v. Třída implementuje rozhraní, které vyžaduje implementaci metody. <xref:System.IComparable%601.CompareTo%2A> `Car` <xref:System.IComparable%601>

Každé volání <xref:System.IComparable%601.CompareTo%2A> metody provede jedno porovnání, které se používá k řazení. Uživatelsky psaný kód v `CompareTo` metodě vrátí hodnotu pro každé porovnání aktuálního objektu s jiným objektem. Vrácená hodnota je menší než nula, pokud je aktuální objekt menší než druhý objekt, větší než nula, pokud je aktuální objekt větší než druhý objekt a nula, pokud jsou stejné. To umožňuje definovat v kódu kritéria pro větší než, menší než a rovno.

`ListCars` V metodě `cars.Sort()` příkaz seřadí seznam. Toto <xref:System.Collections.Generic.List%601.Sort%2A> volání metody metody <xref:System.Collections.Generic.List%601> způsobí, že `CompareTo` `Car` Metoda`List`bude automaticky volána pro objekty v.

[!code-vb[VbVbalrStatements#125](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#125)]

## <a name="see-also"></a>Viz také:

- [Kolekce](../../../standard/collections/index.md)
- [Příkaz For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Struktury smyčky](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Příkaz While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Příkaz Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Rozšíření a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Inicializátory objektů: Pojmenované a anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Inicializátory kolekcí](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Pole](../../../visual-basic/programming-guide/language-features/arrays/index.md)
