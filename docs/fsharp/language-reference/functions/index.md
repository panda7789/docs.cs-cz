---
title: Funkce (F#)
description: 'Informace o funkcích v F # a jak F # podporuje společné funkční programovací konstrukce.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 4cdab85dd63cc74a4c6e7abf660f8f32cc088120
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="functions"></a>Funkce

Funkce jsou základní jednotkou spouštění programu v žádný programovací jazyk. Funkce F # jako v jiných jazycích, má název, může mít parametry a argumenty proveďte a má text. F # podporuje také funkční programovací konstrukce, jako je například replikace funkce jako hodnoty, pomocí nepojmenované funkcí na výrazy, složení funkcí k vytvoření nové funkce, curryfikované funkce a implicitní definici funkce prostřednictvím s částečným aplikace argumenty funkce.

Definování funkcí s použitím `let` – klíčové slovo, nebo, pokud je funkce rekurzivní, `let rec` – kombinace klíčových slov.


## <a name="syntax"></a>Syntaxe

```fsharp
// Non-recursive function definition.
let [inline] function-name parameter-list [ : return-type ] = function-body
// Recursive function definition.
let rec function-name parameter-list = recursive-function-body
```

## <a name="remarks"></a>Poznámky
*Název funkce* je identifikátor, který představuje funkci. *Seznam parametrů* se skládá z následných parametry, které jsou oddělené mezerami. Explicitní typ pro všechny parametry, můžete zadat, jak je popsáno v části parametry. Pokud nezadáte argument konkrétní typ, pokusí se kompilátor odvození typu z tělo funkce. *Tělo funkce* se skládá z výrazu. Výraz, který tvoří tělo funkce se obvykle ze složeného výrazu skládající se z počet výrazů, které případech v posledním výrazu, který je návratovou hodnotu. *Návratový typ* typu následovaný dvojtečkou a je volitelné. Pokud nezadáte žádný typ vrácené hodnoty explicitně, kompilátor určuje návratový typ z výsledný výraz.

Definice jednoduché funkce vypadá přibližně takto:

```fsharp
let f x = x + 1
```

V předchozím příkladu název funkce je `f`, argument je `x`, která má typ `int`, je tělo funkce `x + 1`, a vrácená hodnota je typu `int`.

Funkce mohou být označeny `inline`. Informace o `inline`, najdete v části [vložené funkce](../functions/inline-functions.md).


## <a name="scope"></a>Rozsah
Všechny úrovni oboru, než je rozsah modulu není chybu opakovaně použít název hodnotu nebo funkce. Pokud jste znovu použít název, stín později deklarovaný název název předtím deklarován. V oboru nejvyšší úrovně v modulu, musí být jedinečné názvy. Například následující kód vytvoří chybu, když se objeví v modulu oboru, ale ne v případě, že se zobrazí uvnitř funkce:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet101.fs)]

Ale následující kód je přijatelné žádné úrovni oboru:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet102.fs)]
    
#### <a name="parameters"></a>Parametry
Názvy parametrů jsou uvedeny po název funkce. Typ parametru, můžete určit, jak je znázorněno v následujícím příkladu:

```fsharp
let f (x : int) = x + 1
```

Pokud zadáte typu, odpovídá názvu parametru a je oddělené od názvu dvojtečkou. Pokud typ pro parametr vynecháte, je kompilátorem odvodit typ parametru. Například v následující definice funkce argument `x` je odvodit být typu `int` protože 1 je typu `int`.

```fsharp
let f x = x + 1
```

Kompilátor se však pokusí tomu, aby fungoval jako obecný nejblíže. Například vezměte na vědomí následující kód:

```fsharp
let f x = (x, x)
```

Funkce vytvoří řazenou kolekci členů z jeden argument libovolného typu. Protože není zadán typ, funkci lze použít s žádným typem argument. Další informace najdete v tématu [Automatická generalizace](../generics/automatic-generalization.md).


## <a name="function-bodies"></a>Těla funkcí
Tělo funkce může obsahovat definice místní proměnné a funkce. Tyto proměnné a funkce jsou v oboru v těle aktuální funkce ale není mimo něj. Pokud máte možnost prostá syntaxe povolena, je nutné použít odsazení označuje, že definice v tělo funkce, jak je znázorněno v následujícím příkladu:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet103.fs)]

Další informace najdete v tématu [pravidla formátování kódu](../code-formatting-guidelines.md) a [podrobná syntaxe](../verbose-syntax.md).


## <a name="return-values"></a>Návratové hodnoty
Kompilátor používá k určení návratovou hodnotu a typu výsledný výraz v tělo funkce. Kompilátor může odvodit typ výsledný výraz z předchozí výrazy. Ve funkci `cylinderVolume`, uvedené v předchozí části, typ `pi` se určí na základě typu literálové `3.14159` být `float`. Kompilátor používá typ `pi` určit typ výrazu `h * pi * r * r` být `float`. Proto je celkové návratový typ funkce `float`.

Pokud chcete explicitně zadat návratovou hodnotu, zápisu kód následujícím způsobem:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet105.fs)]

Jak je kód je uvedeno výše, kompilátor použije **float** celou funkci; Pokud jste na mysli ji použít také typy parametrů, použijte následující kód:

```fsharp
let cylinderVolume (radius : float) (length : float) : float
```

## <a name="calling-a-function"></a>Volání funkce
Volat funkce tak, že zadáte název funkce následované mezerou a potom všechny argumenty, které jsou oddělené mezerami. Chcete-li například volání funkce **cylinderVolume** a výsledek přiřadit hodnotu **. denní obj.**, zápis následující kód:

```fsharp
let vol = cylinderVolume 2.0 3.0
```

## <a name="partial-application-of-arguments"></a>Částečné použití argumentů
Pokud zadáte menší než zadaný počet argumentů, vytvoříte nové funkce, která očekává zbývající argumenty. Zpracování argumentů tato metoda se označuje jako *currying* a tohoto funkční programovací jazyky jako F #. Předpokládejme například, že pracujete s dvěma velikosti kanálu: jeden má okruhu **2.0** a dalších má okruhu **3.0**. Můžete vytvořit funkce, které určit objem kanálu následujícím způsobem:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet106.fs)]

By pak zadáte další argument podle potřeby pro různých délek kanálu pro dva různé velikosti:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet107.fs)]
    
## <a name="recursive-functions"></a>Rekurzivní funkce
*Rekurzivní funkce* jsou funkce, které volání sebe sama. Potřebují, zda jste zadali **rec** následující – klíčové slovo **let** – klíčové slovo. Vyvolání funkce rekurzivní z v textu funkce stejně, jako by vyvolání jakékoli volání funkce. Následující funkce rekurzivní vypočítá *n*tý Fibonacciho číslo. Pořadí Fibonacciho číslo je známo, od antiquity a je pořadí, ve kterém všechna po sobě jdoucí čísla je součet hodnot předchozích dvou čísel v pořadí.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet108.fs)]

Některé funkce rekurzivní může přetečení zásobníku program nebo proveďte neefektivnímu v případě, že jste Nezapisovat je dát pozor a povědomí o speciální technik, jako je například použití akumulátorů a pokračování.


## <a name="function-values"></a>Hodnoty funkcí
V jazyce F # všechny funkce jsou považovány za hodnoty; ve skutečnosti se označují jako *funkce hodnoty*. Protože funkce jsou hodnoty, použitím jako argumenty dalších funkcí, nebo v jiných kontextech kde se používají. Tady je příklad, který přebírá hodnotu funkce jako argument funkce:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet109.fs)]

Zadejte typ hodnoty funkce pomocí `->` tokenu. Na levé straně tohoto tokenu je typ argumentu a na pravé straně je návratovou hodnotu. V předchozím příkladu `apply1` je funkce, která přebírá funkci `transform` jako argument, kde `transform` je funkce, která přebírá celé číslo a vrátí jiné číslo. Následující kód ukazuje, jak používat `apply1`:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet110.fs)]

Hodnota `result` bude 101 po spuštění předchozí kód.

Více argumentů jsou odděleny následných `->` tokeny, jak je znázorněno v následujícím příkladu:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet111.fs)]

Výsledkem je 200.


## <a name="lambda-expressions"></a>Výrazy lambda
A *výrazu lambda* nepojmenované funkcí. V předchozích příkladech místo definice funkce s názvem **přírůstek** a **mul**, může použití výrazů lambda následujícím způsobem:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet112.fs)]

Můžete definovat pomocí výrazů lambda `fun` – klíčové slovo. Výraz lambda vypadá takto: definice funkce, vyjma toho, že místo `=` token, `->` token slouží k oddělení od tělo funkce seznam argumentů. V definici regulární funkce lze odvodit nebo explicitně zadané typy argumentů a návratový typ výrazu lambda je odvozen od typu poslední výrazu v textu. Další informace najdete v tématu [výrazy Lambda: `fun` – klíčové slovo](../functions/lambda-expressions-the-fun-keyword.md).


## <a name="function-composition-and-pipelining"></a>Skládání a paralelní zpracování funkcí
Funkce v jazyce F # se může skládat z dalších funkcí. Složení dvě funkce **function1** a **funkce2** je jiné funkce, která představuje použití **function1** a potom aplikaci **funkce2**:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet113.fs)]

Výsledkem je 202.

Použití kanálů umožňuje funkce volání společně jako po sobě jdoucích operací. Paralelní zpracování funguje takto:

```fsharp
let result = 100 |> function1 |> function2
```

Výsledkem je znovu 202.

Operátory složení trvat dvě funkce a vrátit funkci; naopak operátorů kanálů funkci a argument a vrátit hodnotu. Následující příklad kódu ukazuje rozdíl mezi operátory kanálu a složení zobrazením rozdíly v signatury funkce a využití.

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
Můžete použít přetížení metody typu, ale není funkce. Další informace najdete v tématu [metody](../members/methods.md).


## <a name="see-also"></a>Viz také
[Hodnoty](../values/index.md)

[Referenční dokumentace jazyka F#](../index.md)
