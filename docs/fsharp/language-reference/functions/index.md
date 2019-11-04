---
title: Funkce
description: Přečtěte si o F# funkcích v F# tématu a o tom, jak podporují běžné konstrukce funkčního programování.
ms.date: 05/16/2016
ms.openlocfilehash: c6b8307f51ffcdc77fe4352b2305fca1f247ccbb
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423956"
---
# <a name="functions"></a>Funkce

Funkce jsou základní jednotkou spuštění programu v jakémkoli programovacím jazyce. Stejně jako v jiných jazycích má F# funkce název, může mít parametry a přebírat argumenty a má tělo. F#také podporuje konstrukce funkčního programování, jako je zpracování funkcí jako hodnot, použití nepojmenovaných funkcí ve výrazech, složení funkcí pro vytváření nových funkcí, funkcí curryfikované a implicitní definice funkcí pomocí možností částečného. použití argumentů funkce.

Funkce definujete pomocí klíčového slova `let`, nebo pokud je funkce rekurzivní, kombinace klíčového slova `let rec`.

## <a name="syntax"></a>Syntaxe

```fsharp
// Non-recursive function definition.
let [inline] function-name parameter-list [ : return-type ] = function-body
// Recursive function definition.
let rec function-name parameter-list = recursive-function-body
```

## <a name="remarks"></a>Poznámky

*Název funkce* je identifikátor, který představuje funkci. *Seznam parametrů* se skládá z dalších parametrů, které jsou odděleny mezerami. Můžete zadat explicitní typ pro každý parametr, jak je popsáno v oddílu Parameters. Pokud nezadáte konkrétní typ argumentu, kompilátor se pokusí odvodit typ z těla funkce. *Tělo funkce* se skládá z výrazu. Výraz, který tvoří tělo funkce, je typicky složený výraz sestávající z řady výrazů, který je ukončen finálním výrazem, který je návratovou hodnotou. *Návratový typ* je dvojtečka následovaná typem a je volitelná. Pokud nezadáte typ vrácené hodnoty explicitně, kompilátor určí návratový typ z finálního výrazu.

Jednoduchá definice funkce se podobá následující:

```fsharp
let f x = x + 1
```

V předchozím příkladu je název funkce `f`, argument je `x`, který má typ `int`, tělo funkce `x + 1`a návratová hodnota je typu `int`.

Funkce mohou být označeny `inline`. Informace o `inline`naleznete v tématu [inline Functions](../functions/inline-functions.md).

## <a name="scope"></a>Rozsah

Na jakékoli úrovni oboru jiné než obor modulu není k dispozici chyba pro opakované použití hodnoty nebo názvu funkce. Pokud použijete název znovu, název deklarovaný později vystínuje dříve deklarovaný název. Nicméně v oboru nejvyšší úrovně v modulu musí být názvy jedinečné. Například následující kód vyvolá chybu, když se zobrazí v oboru modulu, ale ne, pokud se zobrazí uvnitř funkce:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet101.fs)]

Ale následující kód je přijatelný na libovolné úrovni oboru:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet102.fs)]

### <a name="parameters"></a>Parametry

Názvy parametrů jsou uvedeny za názvem funkce. Můžete určit typ pro parametr, jak je znázorněno v následujícím příkladu:

```fsharp
let f (x : int) = x + 1
```

Pokud zadáte typ, následuje za názvem parametru a je oddělen od názvu dvojtečkou. Pokud vynecháte typ pro parametr, typ parametru je odvozen kompilátorem. Například v následující definici funkce je argument `x` odvozený tak, aby byl typu `int`, protože 1 je typ `int`.

```fsharp
let f x = x + 1
```

Kompilátor se ale pokusí tuto funkci nastavit jako obecnou. Poznamenejte si například následující kód:

```fsharp
let f x = (x, x)
```

Funkce vytvoří řazenou kolekci členů z jednoho argumentu libovolného typu. Vzhledem k tomu, že není zadán typ, lze funkci použít s libovolným typem argumentu. Další informace najdete v tématu [Automatická generalizace](../generics/automatic-generalization.md).

## <a name="function-bodies"></a>Těla funkcí

Tělo funkce může obsahovat definice místních proměnných a funkcí. Tyto proměnné a funkce jsou v rozsahu v těle aktuální funkce, ale nejsou mimo ni. Pokud máte povolenou možnost odlehčené syntaxe, je nutné použít odsazení k označení, že definice je v těle funkce, jak je znázorněno v následujícím příkladu:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet103.fs)]

Další informace najdete v tématu [pokyny pro formátování kódu](../../style-guide/formatting.md) a [podrobnou syntaxi](../verbose-syntax.md).

## <a name="return-values"></a>Návratové hodnoty

Kompilátor používá konečný výraz v těle funkce k určení návratové hodnoty a typu. Kompilátor může odvodit typ finálního výrazu z předchozích výrazů. V `cylinderVolume`funkce uvedené v předchozí části je typ `pi` určen z typu `3.14159` literálu, který má být `float`. Kompilátor používá typ `pi` k určení typu výrazu `h * pi * r * r` `float`. Proto je celkový návratový typ funkce `float`.

Chcete-li zadat návratovou hodnotu explicitně, napište kód následujícím způsobem:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet105.fs)]

Jak je kód uveden výše, kompilátor použije **float** na celou funkci; Pokud je to vhodné pro použití s typy parametrů, použijte následující kód:

```fsharp
let cylinderVolume (radius : float) (length : float) : float
```

## <a name="calling-a-function"></a>Volání funkce

Zavoláte funkce zadáním názvu funkce následovaného mezerou a následnými argumenty, které jsou oddělené mezerami. Například pro volání funkce **cylinderVolume** a přiřazení výsledku k hodnotě **Vol**, napíšete následující kód:

```fsharp
let vol = cylinderVolume 2.0 3.0
```

## <a name="partial-application-of-arguments"></a>Částečné použití argumentů

Pokud zadáte méně, než je zadaný počet argumentů, vytvoříte novou funkci, která očekává zbývající argumenty. Tato metoda zpracování argumentů je označována jako *procesu curryfikace* a je charakteristická charakteristika funkčních programovacích F#jazyků, jako je. Předpokládejme například, že pracujete se dvěma velikostmi kanálu: jeden má poloměr **2,0** a druhý má poloměr **3,0**. Mohli byste vytvořit funkce, které určí objem kanálu následujícím způsobem:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet106.fs)]

Pak zadejte další argument potřebný pro různé délky kanálu dvou různých velikostí:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet107.fs)]

## <a name="recursive-functions"></a>Rekurzivní funkce

*Rekurzivní funkce* jsou funkce, které volají samy sebe. Vyžadují, abyste zadali klíčové slovo **REC** za klíčovým slovem **let** . Vyvolejte rekurzivní funkci z těla funkce stejně, jako byste vyvolali jakékoli volání funkce. Následující rekurzivní funkce vypočítá *n*-<sup>tý</sup> Fibonacci číslo. Sekvenci Fibonacci Number bylo známo od poslední chvíle a je sekvence, ve které je každé z následných čísel součtem předchozích dvou čísel v sekvenci.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet108.fs)]

Některé rekurzivní funkce mohou přetečení zásobníku programu nebo provádět neefektivně, pokud je nezapisujete se péči a s vědomím speciálních technik, jako je například použití akumulátorů a pokračování.

## <a name="function-values"></a>Hodnoty funkcí

V F#platí, že všechny funkce jsou považovány za hodnoty; ve skutečnosti jsou známé jako *hodnoty funkcí*. Vzhledem k tomu, že funkce jsou hodnoty, mohou být použity jako argumenty pro jiné funkce nebo v jiných kontextech, kde jsou použity hodnoty. Následuje příklad funkce, která přebírá hodnotu funkce jako argument:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet109.fs)]

Zadejte typ hodnoty funkce pomocí tokenu `->`. Na levé straně tohoto tokenu je typ argumentu a na pravé straně je návratová hodnota. V předchozím příkladu je `apply1` funkce, která přebírá funkci `transform` jako argument, kde `transform` je funkce, která přebírá celé číslo a vrací jiné celé číslo. Následující kód ukazuje, jak použít `apply1`:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet110.fs)]

Hodnota `result` bude 101 po spuštění předchozího kódu.

Více argumentů je odděleno pomocí `->` tokeny po sobě, jak je znázorněno v následujícím příkladu:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet111.fs)]

Výsledek je 200.

## <a name="lambda-expressions"></a>Lambda – výrazy

*Výraz lambda* je nepojmenovaná funkce. V předchozích příkladech se místo definování pojmenovaných funkcí **zvýší** a **mul**můžete použít lambda výrazy následujícím způsobem:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet112.fs)]

Lambda výrazy definujete pomocí klíčového slova `fun`. Výraz lambda se podobá definici funkce, s tím rozdílem, že místo tokenu `=` je `->` tokenu použit k oddělení seznamu argumentů od těla funkce. Stejně jako v definici regulární funkce lze typy argumentů odvodit nebo zadat explicitně a návratový typ výrazu lambda je odvozený od typu posledního výrazu v těle. Další informace naleznete v tématu [výrazy lambda: klíčové slovo `fun`](../functions/lambda-expressions-the-fun-keyword.md).

## <a name="function-composition-and-pipelining"></a>Skládání a paralelní zpracování funkcí

Funkce v F# můžou být složené z jiných funkcí. Složení dvou funkcí **Function1** a **function2** je další funkce, která představuje aplikaci **Function1** , která následuje po použití **function2**:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet113.fs)]

Výsledek je 202.

Přesměrování umožňuje zřetězení volání funkcí jako po sobě jdoucích operací. Přesměrování funguje následujícím způsobem:

```fsharp
let result = 100 |> function1 |> function2
```

Výsledek je znovu 202.

Operátory kompozice přijímají dvě funkce a vracejí funkci. Naproti tomu operátory kanálu přebírají funkci a argument a vracejí hodnotu. Následující příklad kódu ukazuje rozdíl mezi operátory kanálu a sestavování zobrazením rozdílů v části signatury a využití funkce.

```fsharp
// Function composition and pipeline operators compared.

let addOne x = x + 1
let timesTwo x = 2 * x

// Composition operator
// ( >> ) : ('T1 -> 'T2) -> ('T2 -> 'T3) -> 'T1 -> 'T3
let Compose2 = addOne >> timesTwo

// Backward composition operator
// ( << ) : ('T2 -> 'T3) -> ('T1 -> 'T2) -> 'T1 -> 'T3
let Compose1 = addOne << timesTwo

// Result is 5
let result1 = Compose1 2

// Result is 6
let result2 = Compose2 2

// Pipelining
// Pipeline operator
// ( |> ) : 'T1 -> ('T1 -> 'U) -> 'U
let Pipeline2 x = addOne x |> timesTwo

// Backward pipeline operator
// ( <| ) : ('T -> 'U) -> 'T -> 'U
let Pipeline1 x = addOne <| timesTwo x

// Result is 5
let result3 = Pipeline1 2

// Result is 6
let result4 = Pipeline2 2
```

## <a name="overloading-functions"></a>Přetížení funkcí

Můžete přetížit metody typu, ale ne funkce. Další informace naleznete v tématu [metody](../members/methods.md).

## <a name="see-also"></a>Viz také:

- [Hodnoty](../values/index.md)
- [Referenční dokumentace jazyka F#](../index.md)
