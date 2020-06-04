---
title: For Each...Next – příkaz
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
ms.openlocfilehash: 0feb938121a97b06509b472652e6a753841ab2b8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404651"
---
# <a name="for-eachnext-statement-visual-basic"></a>For Each...Next – příkaz (Visual Basic)

Opakuje skupinu příkazů pro každý prvek v kolekci.

## <a name="syntax"></a>Syntaxe

```vb
For Each element [ As datatype ] In group
    [ statements ]
    [ Continue For ]
    [ statements ]
    [ Exit For ]
    [ statements ]
Next [ element ]
```

## <a name="parts"></a>Součásti

|Pojem|Definice|
|---|---|
|`element`|Vyžadováno v `For Each` příkazu. Volitelné v `Next` příkazu. Variabilní. Slouží k iterování prvků kolekce.|
|`datatype`|Volitelné [`Option Infer`](option-infer-statement.md) , pokud je zapnuto (výchozí) nebo `element` je již deklarováno; požadováno, pokud `Option Infer` je vypnuto a `element` ještě není deklarováno. Datový typ `element` .|
|`group`|Povinná hodnota. Proměnná s typem, který je typem kolekce nebo objektem. Odkazuje na kolekci, na které se `statements` mají opakovat.|
|`statements`|Nepovinný parametr. Jeden nebo více příkazů mezi `For Each` a `Next` , které jsou spuštěny na jednotlivých položkách v `group` .|
|`Continue For`|Nepovinný parametr. Přenese řízení na začátek `For Each` smyčky.|
|`Exit For`|Nepovinný parametr. Přenese řízení ze `For Each` smyčky.|
|`Next`|Povinná hodnota. Ukončí definici `For Each` smyčky.|

## <a name="simple-example"></a>Jednoduchý příklad

Použijte `For Each` smyčku..., `Next` Pokud chcete opakovat sadu příkazů pro každý prvek kolekce nebo pole.

> [!TIP]
> A [pro... Další příkaz](for-next-statement.md) funguje dobře, když můžete přidružit každou iteraci smyčky s proměnnou ovládacího prvku a určit počáteční a konečné hodnoty této proměnné. Pokud však pracujete s kolekcí, koncept počátečních a konečných hodnot není smysluplný a Vy nevíte, kolik prvků kolekce má. V tomto typu případu `For Each` je smyčka... `Next` často lepší volbou.

V následujícím příkladu `For Each` ...`Next` příkaz prochází všechny prvky kolekce seznamů.

[!code-vb[VbVbalrStatements#121](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#121)]

Další příklady najdete v tématu [kolekce](../../../standard/collections/index.md) a [pole](../../programming-guide/language-features/arrays/index.md).

## <a name="nested-loops"></a>Vnořené smyčky

Smyčky můžete vnořovat vložením `For Each` jedné smyčky do jiné.

Následující příklad ukazuje vnořený `For Each` ...`Next` struktury.

[!code-vb[VbVbalrStatements#122](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#122)]

Při vnořování smyček musí mít každá smyčka jedinečnou `element` proměnnou.

Můžete také vnořit různé druhy řídicích struktur mezi sebou. Další informace najdete v tématu [vnořené řídicí struktury](../../programming-guide/language-features/control-flow/nested-control-structures.md).

## <a name="exit-for-and-continue-for"></a>Ukončit po a pokračovat pro

Příkaz [Exit for](exit-statement.md) způsobí, že provádění skončí `For` ...`Next` Loop a přenáší řízení příkazu, který následuje po `Next` příkazu.

`Continue For`Příkaz přenáší řízení okamžitě na další iteraci smyčky. Další informace najdete v tématu [příkaz Continue](continue-statement.md).

Následující příklad ukazuje, jak použít `Continue For` `Exit For` příkazy a.

[!code-vb[VbVbalrStatements#123](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#123)]

Do smyčky můžete vložit libovolný počet `Exit For` příkazů `For Each` . Při použití v rámci vnořených `For Each` smyček `Exit For` způsobí, že provádění ukončí vnitřní smyčku a přenáší řízení na další vyšší úroveň vnoření.

`Exit For`se často používá po vyhodnocení nějaké podmínky, například v `If` ... `Then` ...`Else` strukturované. Je možné, že budete chtít použít `Exit For` následující podmínky:

- Pokračování iterace je zbytečné nebo nemožné. To může být způsobeno chybnou hodnotou nebo žádostí o ukončení.

- Výjimka je zachycena v `Try` ... `Catch` ...`Finally`. Můžete použít `Exit For` na konci `Finally` bloku.

- Existuje nekonečné smyčka, což je smyčka, která by mohla běžet velkým nebo dokonce nekonečným počtem výskytů. Pokud tuto podmínku zjistíte, můžete ji použít `Exit For` k řídicímu panelu smyčky. Další informace najdete v části [do... Příkaz LOOP](do-loop-statement.md)

## <a name="iterators"></a>Iterátory

Pomocí *iterátoru* můžete provést vlastní iteraci v kolekci. Iterátor může být funkce nebo `Get` přistupující objekt. Pomocí `Yield` příkazu vrátí každý prvek kolekce po jednom.

Zavoláte iterátor pomocí `For Each...Next` příkazu. Každá iterace `For Each` smyčky volá iterátor. Při `Yield` dosažení příkazu v iterátoru `Yield` je vrácen výraz v příkazu a aktuální umístění v kódu je uchováno. Spuštění je restartováno z tohoto umístění při příštím volání iterátoru.

V následujícím příkladu je použita funkce iterátoru. Funkce iterátoru obsahuje `Yield` příkaz, který je uvnitř [... Další](for-next-statement.md) smyčka V `ListEvenNumbers` metodě Každá iterace `For Each` těla příkazu vytvoří volání funkce iterátoru, která pokračuje k dalšímu `Yield` příkazu.

[!code-vb[VbVbalrStatements#127](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#127)]

Další informace naleznete v tématu [iterátory](../../programming-guide/concepts/iterators.md), [příkazy yield](yield-statement.md)a [iterátor](../modifiers/iterator.md).

## <a name="technical-implementation"></a>Technická implementace

Když `For Each` ...`Next` příkaz se spustí, Visual Basic vyhodnocuje kolekci pouze jednou, a to před spuštěním smyčky. Pokud váš příkaz zablokuje změny `element` nebo `group` tyto změny neovlivňují iteraci smyčky.

Po úspěšném přiřazení všech prvků v kolekci se `element` `For Each` smyčka zastaví a řízení projde příkazem, který následuje za `Next` příkazem.

Pokud je nastavená [možnost odvodit](option-infer-statement.md) (výchozí nastavení), kompilátor Visual Basic může odvodit datový typ `element` . Pokud je vypnutá a `element` nebyla deklarována vně smyčky, je nutné ji deklarovat v `For Each` příkazu. Chcete-li explicitně deklarovat datový typ `element` , použijte `As` klauzuli. Není-li datový typ elementu definován mimo `For Each` konstruktor... `Next` konstrukce, je jeho rozsah hlavním prvkem smyčky. Všimněte si, že nemůžete deklarovat `element` vnější i uvnitř smyčky.

Volitelně můžete zadat `element` v `Next` příkazu. To zlepšuje čitelnost vašeho programu, zejména v případě, že máte vnořené `For Each` smyčky. Je nutné zadat stejnou proměnnou jako ta, která se zobrazí v příslušném `For Each` příkazu.

Je možné, že se nebudete muset vyhnout změnám hodnoty `element` uvnitř smyčky. To může ztížit čtení a ladění kódu. Změna hodnoty `group` nemá vliv na kolekci nebo její prvky, které byly určeny při prvním zadání smyčky.

Při vnořování smyček se při výskytu `Next` příkazu na úrovni vnějšího vnoření vyskytne v případě `Next` , že došlo k chybě, kompilátor signalizuje chybu. Kompilátor však může tuto chybu překrývají pouze v případě, že zadáte `element` příkaz v každém `Next` příkazu.

Pokud váš kód závisí na průchodu v kolekci v určitém pořadí, `For Each` smyčka... `Next` není nejlepší volbou, pokud neznáte charakteristiky objektu Enumerator, které kolekce zpřístupňuje. Pořadí průchodu není určeno Visual Basic, ale <xref:System.Collections.IEnumerator.MoveNext%2A> metodou objektu Enumerator. Proto možná nebudete moci předpovědět, který prvek kolekce je první, který má být vrácen v `element` nebo který je další, který bude vrácen po daném prvku. Můžete dosáhnout spolehlivější výsledků pomocí jiné struktury smyčky, například `For` ... `Next` nebo `Do` ... `Loop` .

Modul runtime musí být schopný převést elementy v `group` na `element` . Příkaz [ `Option Strict` ] řídí, zda jsou povoleny rozšiřující i zúžené převody ( `Option Strict` je vypnutý, její výchozí hodnota) nebo zda jsou povoleny pouze rozšiřující převody `Option Strict` . Další informace najdete v tématu [zúžení převodů](#narrowing-conversions).

Datový typ `group` musí být odkazový typ, který odkazuje na kolekci nebo pole, které je vyčíslitelné. Nejčastěji to znamená, že `group` odkazuje na objekt, který implementuje <xref:System.Collections.IEnumerable> rozhraní `System.Collections` oboru názvů nebo <xref:System.Collections.Generic.IEnumerable%601> rozhraní `System.Collections.Generic` oboru názvů. `System.Collections.IEnumerable`definuje <xref:System.Collections.IEnumerable.GetEnumerator%2A> metodu, která vrací objekt enumerátoru pro kolekci. Objekt enumerátoru implementuje `System.Collections.IEnumerator` rozhraní `System.Collections` oboru názvů a zpřístupňuje <xref:System.Collections.IEnumerator.Current%2A> vlastnost a <xref:System.Collections.IEnumerator.Reset%2A> <xref:System.Collections.IEnumerator.MoveNext%2A> metody a. Visual Basic je používá k procházení kolekce.

### <a name="narrowing-conversions"></a>Zužující převody

Pokud `Option Strict` je nastaven na `On` , zužující převody obvykle způsobují chyby kompilátoru. V `For Each` příkazu však převod z prvků v `group` na `element` je vyhodnocován a proveden v době běhu a chyby kompilátoru způsobené zužujícími převody jsou potlačeny.

V následujícím příkladu přiřazení `m` jako počáteční hodnotu pro není `n` zkompilováno, pokud `Option Strict` je zapnuto, protože převod typu `Long` na `Integer` je zužující převod. V `For Each` příkazu však není hlášena žádná chyba kompilátoru, i když přiřazení `number` vyžaduje stejný převod z `Long` na `Integer` . V `For Each` příkazu, který obsahuje velké číslo, dojde k chybě za běhu při <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A> použití na velké číslo.

[!code-vb[VbVbalrStatements#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class3.vb#89)]

### <a name="ienumerator-calls"></a>Volání IEnumerator

Při spuštění `For Each` smyčky... `Next` Visual Basic ověří, zda `group` odkazuje na platný objekt kolekce. V takovém případě vyvolá výjimku. V opačném případě volá <xref:System.Collections.IEnumerator.MoveNext%2A> metodu a <xref:System.Collections.IEnumerator.Current%2A> vlastnost objektu Enumerator pro návrat prvního prvku. Pokud `MoveNext` znamená, že neexistuje žádný další prvek, tedy pokud je kolekce prázdná, `For Each` smyčka se zastaví a ovládací prvek projde příkazem, který následuje za `Next` příkazem. V opačném případě Visual Basic nastaví `element` na první prvek a spustí blok příkazu.

Pokaždé, když Visual Basic nalezne `Next` příkaz, vrátí se do `For Each` příkazu. Znovu volá `MoveNext` a `Current` vrátí další prvek a znovu buď spustí blok, nebo zastaví smyčku v závislosti na výsledku. Tento proces pokračuje `MoveNext` , dokud neindikuje, že není k dispozici žádný další prvek nebo `Exit For` příkaz.

**Úprava kolekce.** Objekt enumerátoru vrácený <xref:System.Collections.IEnumerable.GetEnumerator%2A> normálně neumožňuje změnit kolekci přidáním, odstraněním, nahrazením nebo změnou pořadí všech prvků. Změníte-li kolekci poté, co jste spustili `For Each` smyčku... `Next` , objekt enumerátoru se změní na neplatný a další pokus o přístup k elementu způsobí <xref:System.InvalidOperationException> výjimku.

Toto blokování úprav však není určeno Visual Basic, ale spíše implementací <xref:System.Collections.IEnumerable> rozhraní. Je možné implementovat `IEnumerable` způsobem, který umožňuje úpravu během iterace. Pokud zvažujete, že provádíte tuto dynamickou úpravu, ujistěte se, že rozumíte charakteristikám `IEnumerable` implementace v kolekci, kterou používáte.

**Úpravy prvků kolekce.** <xref:System.Collections.IEnumerator.Current%2A>Vlastnost objektu Enumerator je určena [jen pro čtení](../modifiers/readonly.md)a vrátí místní kopii každého prvku kolekce. To znamená, že nemůžete změnit samotné prvky ve `For Each` smyčce.... `Next` Všechny změny, které provedete, ovlivní jenom místní kopii z `Current` a nereflektují se zpátky do příslušné kolekce. Nicméně pokud je prvek odkazový typ, můžete upravit členy instance, na kterou odkazuje. Následující příklad upravuje `BackColor` člena každého `thisControl` prvku. Nemůžete však změnit `thisControl` sám sebe.

```vb
Sub LightBlueBackground(thisForm As System.Windows.Forms.Form)
    For Each thisControl In thisForm.Controls
        thisControl.BackColor = System.Drawing.Color.LightBlue
    Next thisControl
End Sub
```

Předchozí příklad může změnit `BackColor` člena každého `thisControl` prvku, i když nemůže `thisControl` sám změnit.

**Procházení polí.** Vzhledem k tomu <xref:System.Array> , že třída implementuje <xref:System.Collections.IEnumerable> rozhraní, všechna pole zpřístupňují <xref:System.Array.GetEnumerator%2A> metodu. To znamená, že můžete iterovat přes pole pomocí `For Each` smyčky.... `Next` Lze však číst pouze prvky pole. Nemůžete je změnit.

## <a name="example"></a>Příklad

Následující příklad zobrazí seznam všech složek v C:\. adresáře pomocí <xref:System.IO.DirectoryInfo> třídy.

[!code-vb[VbVbalrStatements#124](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#124)]

## <a name="example"></a>Příklad

Následující příklad znázorňuje postup pro řazení kolekce. Příklad řadí instance `Car` třídy, které jsou uloženy v <xref:System.Collections.Generic.List%601> . `Car`Třída implementuje <xref:System.IComparable%601> rozhraní, které vyžaduje <xref:System.IComparable%601.CompareTo%2A> implementaci metody.

Každé volání <xref:System.IComparable%601.CompareTo%2A> metody provede jedno porovnání, které se používá k řazení. Uživatelsky psaný kód v `CompareTo` metodě vrátí hodnotu pro každé porovnání aktuálního objektu s jiným objektem. Vrácená hodnota je menší než nula, pokud je aktuální objekt menší než druhý objekt, větší než nula, pokud je aktuální objekt větší než druhý objekt a nula, pokud jsou stejné. To umožňuje definovat v kódu kritéria pro větší než, menší než a rovno.

V `ListCars` metodě `cars.Sort()` příkaz seřadí seznam. Toto volání <xref:System.Collections.Generic.List%601.Sort%2A> metody metody <xref:System.Collections.Generic.List%601> způsobí, že `CompareTo` Metoda bude automaticky volána pro `Car` objekty v `List` .

[!code-vb[VbVbalrStatements#125](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#125)]

## <a name="see-also"></a>Viz také

- [Kolekce](../../../standard/collections/index.md)
- [For...Next – příkaz](for-next-statement.md)
- [Struktury smyčky](../../programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While – příkaz](while-end-while-statement.md)
- [Do...Loop – příkaz](do-loop-statement.md)
- [Rozšíření a zúžení převodů](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Inicializátory objektů: pojmenované a anonymní typy](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Inicializátory kolekcí](../../programming-guide/language-features/collection-initializers/index.md)
- [Pole](../../programming-guide/language-features/arrays/index.md)
