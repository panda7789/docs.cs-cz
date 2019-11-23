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
ms.openlocfilehash: f56e5defa2328011d222bfca05334b610e805055
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332778"
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

|Termín|Definice|
|---|---|
|`element`|Vyžaduje se v příkazu `For Each`. Volitelné v příkazu `Next`. Variabilní. Slouží k iterování prvků kolekce.|
|`datatype`|Volitelné, pokud je [`Option Infer`](option-infer-statement.md) zapnutá (výchozí) nebo `element` už je deklarovaná; vyžaduje se, pokud je `Option Infer` vypnuto a `element` ještě není deklarované. Datový typ `element`.|
|`group`|Požadováno. Proměnná s typem, který je typem kolekce nebo objektem. Odkazuje na kolekci, pro kterou se `statements` opakovat.|
|`statements`|Volitelné. Jeden nebo více příkazů mezi `For Each` a `Next`, které se spouštějí na každé položce v `group`.|
|`Continue For`|Volitelné. Přenese řízení na začátek smyčky `For Each`.|
|`Exit For`|Volitelné. Přenáší řízení ze smyčky `For Each`.|
|`Next`|Požadováno. Ukončí definici smyčky `For Each`.|

## <a name="simple-example"></a>Jednoduchý příklad

Pokud chcete opakovat sadu příkazů pro každý prvek kolekce nebo pole, použijte smyčku `For Each`...`Next`.

> [!TIP]
> A [pro... Další příkaz](../../../visual-basic/language-reference/statements/for-next-statement.md) funguje dobře, když můžete přidružit každou iteraci smyčky s proměnnou ovládacího prvku a určit počáteční a konečné hodnoty této proměnné. Pokud však pracujete s kolekcí, koncept počátečních a konečných hodnot není smysluplný a Vy nevíte, kolik prvků kolekce má. V tomto typu případu je často lepší volbou `For Each`...`Next` smyčka.

V následujícím příkladu `For Each`...`Next` příkaz prochází všechny prvky kolekce seznamů.

[!code-vb[VbVbalrStatements#121](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#121)]

Další příklady najdete v tématu [kolekce](../../../standard/collections/index.md) a [pole](../../../visual-basic/programming-guide/language-features/arrays/index.md).

## <a name="nested-loops"></a>Vnořené smyčky

Smyčky `For Each` můžete vnořovat vložením jedné smyčky do jiné.

Následující příklad ukazuje vnořené `For Each`...`Next` Struktury.

[!code-vb[VbVbalrStatements#122](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#122)]

Při vnořování smyček musí mít každá smyčka jedinečnou `element` proměnnou.

Můžete také vnořit různé druhy řídicích struktur mezi sebou. Další informace najdete v tématu [vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).

## <a name="exit-for-and-continue-for"></a>Ukončit po a pokračovat pro

Příkaz [Exit for](../../../visual-basic/language-reference/statements/exit-statement.md) způsobí, že spuštění ukončí `For`...`Next` Loop a přenáší řízení příkazu, který následuje po příkazu `Next`.

Příkaz `Continue For` přenáší řízení okamžitě na další iteraci smyčky. Další informace najdete v tématu [příkaz Continue](../../../visual-basic/language-reference/statements/continue-statement.md).

Následující příklad ukazuje, jak použít příkazy `Continue For` a `Exit For`.

[!code-vb[VbVbalrStatements#123](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#123)]

Do `For Each` smyčky můžete vložit libovolný počet `Exit For` příkazů. Při použití ve vnořených cyklech `For Each` `Exit For` způsobí, že provádění ukončí vnitřní smyčku a přenáší řízení na další vyšší úroveň vnoření.

`Exit For` se často používá po vyhodnocení nějaké podmínky, například ve struktuře `If`...`Then`...`Else`. Můžete chtít použít `Exit For` pro následující podmínky:

- Pokračování iterace je zbytečné nebo nemožné. To může být způsobeno chybnou hodnotou nebo žádostí o ukončení.

- Výjimka je zachycena v `Try`...`Catch`...`Finally`. `Exit For` můžete použít na konci bloku `Finally`.

- Existuje nekonečné smyčka, což je smyčka, která by mohla běžet velkým nebo dokonce nekonečným počtem výskytů. Pokud tuto podmínku zjistíte, můžete ji použít `Exit For` a řídicí smyčku. Další informace najdete v části [do... Příkaz LOOP](../../../visual-basic/language-reference/statements/do-loop-statement.md)

## <a name="iterators"></a>Iterátory

Pomocí *iterátoru* můžete provést vlastní iteraci v kolekci. Iterátor může být funkce nebo přistupující objekt `Get`. Používá příkaz `Yield` k vrácení každého prvku kolekce po jednom.

Můžete zavolat iterátor pomocí příkazu `For Each...Next`. Každá iterace `For Each` smyčky volá iterátor. Při dosažení příkazu `Yield` v iterátoru se vrátí výraz v příkazu `Yield` a aktuální umístění v kódu je zachováno. Spuštění je restartováno z tohoto umístění při příštím volání iterátoru.

V následujícím příkladu je použita funkce iterátoru. Funkce iterátoru má příkaz `Yield`, který je uvnitř a [pro... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) smyčka V metodě `ListEvenNumbers` Každá iterace těla příkazu `For Each` vytvoří volání funkce iterátoru, která pokračuje k dalšímu příkazu `Yield`.

[!code-vb[VbVbalrStatements#127](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#127)]

Další informace naleznete v tématu [iterátory](../../programming-guide/concepts/iterators.md), [příkazy yield](../../../visual-basic/language-reference/statements/yield-statement.md)a [iterátor](../../../visual-basic/language-reference/modifiers/iterator.md).

## <a name="technical-implementation"></a>Technická implementace

Když `For Each`...`Next` příkaz se spustí, Visual Basic vyhodnocuje kolekci pouze jednou, a to před spuštěním smyčky. Pokud váš příkaz zablokuje změny `element` nebo `group`, tyto změny neovlivňují iteraci smyčky.

Po úspěšném přiřazení všech prvků v kolekci `element`se smyčka `For Each` zastaví a řízení projde příkazem, který následuje po příkazu `Next`.

Pokud je nastavená [možnost odvodit](option-infer-statement.md) (výchozí nastavení), kompilátor Visual Basic může odvodit datový typ `element`. Je-li vypnuta a `element` nebyla deklarována vně smyčky, je nutné ji deklarovat v příkazu `For Each`. Chcete-li deklarovat datový typ `element` explicitně, použijte klauzuli `As`. Pokud není datový typ elementu definován mimo `For Each`...`Next` konstrukce, je jeho rozsah hlavním prvkem smyčky. Všimněte si, že nelze deklarovat `element` vně a uvnitř smyčky.

Volitelně můžete zadat `element` v příkazu `Next`. To zlepšuje čitelnost vašeho programu, zejména v případě, že máte vnořené `For Each` smyčky. Je nutné zadat stejnou proměnnou jako ta, která se zobrazí v příslušném příkazu `For Each`.

Je možné, že se nebudete muset vyhnout změnám hodnoty `element` uvnitř smyčky. To může ztížit čtení a ladění kódu. Změna hodnoty `group` nemá vliv na kolekci nebo její prvky, které byly určeny při prvním zadání smyčky.

Při vnořování smyček, pokud je před `Next` vnitřní úrovně zjištěn příkaz `Next` úrovně vnějšího vnoření, kompilátor signalizuje chybu. Kompilátor však může tuto chybu překrývají pouze v případě, že zadáte `element` v každém příkazu `Next`.

Pokud váš kód závisí na procházení kolekce v určitém pořadí, není nejlepší volbou `For Each`...`Next` smyčka, pokud neznáte charakteristiky objektu Enumerator, které kolekce zpřístupňuje. Pořadí průchodu není určeno Visual Basic, ale metodou <xref:System.Collections.IEnumerator.MoveNext%2A> objektu Enumerator. Proto možná nebude možné předpovědět, který prvek kolekce je první, který má být vrácen v `element`, nebo který je další, který bude vrácen po daném prvku. Můžete dosáhnout spolehlivější výsledků pomocí jiné struktury smyčky, například `For`...`Next` nebo `Do`...`Loop`.

Modul runtime musí být schopný převést elementy v `group` na `element`. Příkaz [`Option Strict`] řídí, zda jsou povoleny rozšiřující i zúžené převody (`Option Strict` je vypnutý, její výchozí hodnota), nebo zda jsou povoleny pouze rozšiřující převody (`Option Strict` je zapnuto). Další informace najdete v tématu [zúžení převodů](#narrowing-conversions).

Datový typ `group` musí být odkazový typ, který odkazuje na kolekci nebo pole, které je vyčíslitelné. Nejčastěji to znamená, že `group` odkazuje na objekt, který implementuje rozhraní <xref:System.Collections.IEnumerable> `System.Collections` oboru názvů nebo <xref:System.Collections.Generic.IEnumerable%601> rozhraní oboru názvů `System.Collections.Generic`. `System.Collections.IEnumerable` definuje metodu <xref:System.Collections.IEnumerable.GetEnumerator%2A>, která vrací objekt enumerátoru pro kolekci. Objekt enumerátoru implementuje rozhraní `System.Collections.IEnumerator` `System.Collections` oboru názvů a zpřístupňuje vlastnost <xref:System.Collections.IEnumerator.Current%2A> a metody <xref:System.Collections.IEnumerator.Reset%2A> a <xref:System.Collections.IEnumerator.MoveNext%2A>. Visual Basic je používá k procházení kolekce.

### <a name="narrowing-conversions"></a>Zužující převody

Když je `Option Strict` nastaveno na `On`, zužující převody obvykle způsobují chyby kompilátoru. V příkazu `For Each` jsou však převody z prvků v `group` na `element` vyhodnoceny a provedeny za běhu a chyby kompilátoru způsobené zužujícími převody jsou potlačeny.

V následujícím příkladu je přiřazení `m` jako počáteční hodnota pro `n` zkompilováno, je-li `Option Strict` zapnuto, protože převod `Long` na `Integer` je zužující převod. V příkazu `For Each` však není hlášena žádná chyba kompilátoru, i když přiřazení `number` vyžaduje stejný převod z `Long` na `Integer`. V příkazu `For Each`, který obsahuje velké číslo, dojde k chybě za běhu při použití <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A> na velké číslo.

[!code-vb[VbVbalrStatements#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class3.vb#89)]

### <a name="ienumerator-calls"></a>Volání IEnumerator

Při spuštění `For Each`...`Next` smyčka spustí Visual Basic ověří, zda `group` odkazuje na platný objekt kolekce. V takovém případě vyvolá výjimku. V opačném případě zavolá metodu <xref:System.Collections.IEnumerator.MoveNext%2A> a vlastnost <xref:System.Collections.IEnumerator.Current%2A> objektu Enumerator pro vrácení prvního prvku. Pokud `MoveNext` označuje, že neexistuje žádný další prvek, to znamená, pokud je kolekce prázdná, cyklus `For Each` se zastaví a řízení projde příkazem, který následuje po příkazu `Next`. V opačném případě Visual Basic nastaví `element` na první prvek a spustí blok příkazu.

Pokaždé, když Visual Basic nalezne příkaz `Next`, vrátí se do příkazu `For Each`. Znovu volá `MoveNext` a `Current`, aby vrátil další prvek, a znovu buď spustí blok, nebo zastaví smyčku v závislosti na výsledku. Tento proces pokračuje, dokud `MoveNext` nezjistí, že není k dispozici žádný další prvek nebo příkaz `Exit For`.

**Úprava kolekce.** Objekt enumerátoru vrácený <xref:System.Collections.IEnumerable.GetEnumerator%2A> obvykle neumožňuje změnit kolekci přidáním, odstraněním, nahrazením nebo změnou pořadí všech prvků. Pokud kolekci změníte po spuštění `For Each`...`Next` smyčka, objekt enumerátoru se změní na neplatnou a další pokus o přístup k elementu způsobí výjimku <xref:System.InvalidOperationException>.

Toto blokování úprav však není určeno Visual Basic, ale spíše implementací rozhraní <xref:System.Collections.IEnumerable>. Je možné implementovat `IEnumerable` způsobem, který umožňuje úpravu během iterace. Pokud zvažujete takovou dynamickou úpravu, ujistěte se, že rozumíte charakteristikám `IEnumerable` implementace v kolekci, kterou používáte.

**Úpravy prvků kolekce.** Vlastnost <xref:System.Collections.IEnumerator.Current%2A> objektu Enumerator je určena [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md)a vrátí místní kopii každého elementu kolekce. To znamená, že nemůžete změnit samotné prvky ve `For Each`...`Next` smyčka. Všechny změny, které provedete, ovlivní jenom místní kopii z `Current` a nereflektují se zpátky do příslušné kolekce. Nicméně pokud je prvek odkazový typ, můžete upravit členy instance, na kterou odkazuje. Následující příklad upraví `BackColor` člen každého prvku `thisControl`. Nemůžete však změnit `thisControl` sám sebe.

```vb
Sub LightBlueBackground(thisForm As System.Windows.Forms.Form)
    For Each thisControl In thisForm.Controls
        thisControl.BackColor = System.Drawing.Color.LightBlue
    Next thisControl
End Sub
```

Předchozí příklad může změnit `BackColor` člen každého prvku `thisControl`, i když nemůže změnit `thisControl` sám sebe.

**Procházení polí.** Vzhledem k tomu, že třída <xref:System.Array> implementuje rozhraní <xref:System.Collections.IEnumerable>, všechna pole zpřístupňují metodu <xref:System.Array.GetEnumerator%2A>. To znamená, že můžete iterovat přes pole pomocí smyčky `For Each`...`Next`. Lze však číst pouze prvky pole. Nemůžete je změnit.

## <a name="example"></a>Příklad

Následující příklad zobrazí seznam všech složek v C:\. adresáře pomocí třídy <xref:System.IO.DirectoryInfo>.

[!code-vb[VbVbalrStatements#124](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#124)]

## <a name="example"></a>Příklad

Následující příklad znázorňuje postup pro řazení kolekce. Příklad řadí instance `Car` třídy, které jsou uloženy v <xref:System.Collections.Generic.List%601>. Třída `Car` implementuje rozhraní <xref:System.IComparable%601>, které vyžaduje, aby byla metoda <xref:System.IComparable%601.CompareTo%2A> implementovaná.

Každé volání metody <xref:System.IComparable%601.CompareTo%2A> provede jedno porovnání, které se používá k řazení. Uživatelsky psaný kód v metodě `CompareTo` vrátí hodnotu pro každé porovnání aktuálního objektu s jiným objektem. Vrácená hodnota je menší než nula, pokud je aktuální objekt menší než druhý objekt, větší než nula, pokud je aktuální objekt větší než druhý objekt a nula, pokud jsou stejné. To umožňuje definovat v kódu kritéria pro větší než, menší než a rovno.

V metodě `ListCars` seřadí příkaz `cars.Sort()` seznam. Toto volání metody <xref:System.Collections.Generic.List%601.Sort%2A> <xref:System.Collections.Generic.List%601> způsobí, že metoda `CompareTo` bude automaticky volána pro objekty `Car` v `List`.

[!code-vb[VbVbalrStatements#125](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#125)]

## <a name="see-also"></a>Viz také:

- [Kolekce](../../../standard/collections/index.md)
- [Příkaz For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Struktury smyčky](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Příkaz While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Příkaz Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Rozšíření a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Inicializátory objektů: pojmenované a anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Inicializátory kolekcí](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Pole](../../../visual-basic/programming-guide/language-features/arrays/index.md)
