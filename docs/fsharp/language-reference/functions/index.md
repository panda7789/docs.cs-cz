---
title: Funkce
description: Další informace o funkcích v F# a jak F# podporuje běžné konstrukce funkčního programování.
ms.date: 05/16/2016
ms.openlocfilehash: 6e9ef916388745d2dd6874295d06dca656971b3f
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610915"
---
# <a name="functions"></a>Funkce

Funkce je základní jednotkou spuštění programu v jakémkoli programovacím jazyce. Stejně jako v jiných jazycích F# funkce s názvem, mohou mít parametry a argumenty vzít a má tělo. F#také podporuje konstrukce funkčního programování, jako je zpracování funkce jako hodnoty pomocí nepojmenované funkce ve výrazech, složení funkcí k vytvoření nové funkce, curryfikované funkce a implicitní definice funkce prostřednictvím částečnou použití argumentů funkce.

Definování funkcí s použitím `let` – klíčové slovo, nebo v případě, funkce je rekurzivní, `let rec` – kombinace klíčových slov.

## <a name="syntax"></a>Syntaxe

```fsharp
// Non-recursive function definition.
let [inline] function-name parameter-list [ : return-type ] = function-body
// Recursive function definition.
let rec function-name parameter-list = recursive-function-body
```

## <a name="remarks"></a>Poznámky

*Název funkce* je identifikátor, který představuje funkci. *Seznam parametrů* se skládá z po sobě jdoucích parametry, které jsou odděleny mezer. Explicitní typ pro každý parametr, můžete určit, jak je popsáno v oddílu parametry. Pokud nezadáte konkrétní argument typu, kompilátor se pokusí odvodit typ z těla funkce. *Tělo funkce* se skládá z výrazu. Výraz, který tvoří tělo funkce je obvykle ze složeného výrazu, který se skládá z počet výrazů, které přineslo výsledný výraz, který je návratová hodnota. *Návratový typ* dvojtečku následovanou typ a je volitelný. Pokud explicitně nezadáte typ vrácené hodnoty, kompilátor Určuje typ návratové hodnoty z: výsledný výraz.

Definice jednoduchý funkce vypadá přibližně takto:

```fsharp
let f x = x + 1
```

V předchozím příkladu je název funkce `f`, má argument hodnotu `x`, která má typ `int`, je tělo funkce `x + 1`, a návratová hodnota je typu `int`.

Funkce mohou být označeny `inline`. Informace o `inline`, naleznete v tématu [vložené funkce](../functions/inline-functions.md).

## <a name="scope"></a>Rozsah

Na libovolné úrovni oboru, než je rozsah modulu není chybu pro opětovné použití názvu hodnotě nebo funkci. Pokud je znovu použít název, název deklarován později zastiňuje název deklarovaný dříve. V oboru nejvyšší úrovně v modulu, musí být jedinečné názvy. Například následující kód vygeneruje chybu, když se objeví v oboru modulu, ale ne v případě, že se zobrazí uvnitř funkce:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet101.fs)]

Ale následující kód je přijatelné na libovolné úrovni rozsahu:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet102.fs)]

### <a name="parameters"></a>Parametry

Názvy parametrů jsou uvedeny za názvem funkce. Typ pro parametr, můžete určit, jak je znázorněno v následujícím příkladu:

```fsharp
let f (x : int) = x + 1
```

Pokud chcete zadat typ, následuje název parametru a od názvu oddělené dvojtečkou. Vynecháte-li typ pro parametr, typ parametru je odvozen kompilátorem. Například v následující definici funkce, argument `x` odvodit typ `int` protože 1 je typu `int`.

```fsharp
let f x = x + 1
```

Však kompilátor se pokusí provést funkci co je to možné. Například vezměte na vědomí následující kód:

```fsharp
let f x = (x, x)
```

Funkce vytvoří řazenou kolekci členů ze jedním argumentem libovolného typu. Protože není zadaný typ, funkci lze použít s žádným typem argumentu. Další informace najdete v tématu [Automatická generalizace](../generics/automatic-generalization.md).

## <a name="function-bodies"></a>Těla funkcí

Tělo funkce může obsahovat definice lokální proměnné a funkce. Tyto proměnné a funkce jsou v rozsahu aktuální funkce, ale ne mimo tělo. Až budete mít povolenou možností nenáročném syntaxi, musíte použít odsazení označuje, že definice v těle funkce, jak je znázorněno v následujícím příkladu:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet103.fs)]

Další informace najdete v tématu [pravidla formátování kódu](../code-formatting-guidelines.md) a [podrobná syntaxe](../verbose-syntax.md).

## <a name="return-values"></a>Návratové hodnoty

Kompilátor používá k určení návratovou hodnotu a typ výsledný výraz v těle funkce. Kompilátor může odvodit typ výrazu konečné z předchozích výrazů. Ve funkci `cylinderVolume`, jak je znázorněno v předchozí části, typ `pi` se určí na základě typu literál `3.14159` bude `float`. Kompilátor používá typ `pi` určit typ výrazu `h * pi * r * r` bude `float`. Proto celkové návratový typ funkce je `float`.

K určení návratovou hodnotu explicitně, napište kód následujícím způsobem:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet105.fs)]

Kód je uvedená výše, použije kompilátor **float** na celou funkci; Pokud jste v úmyslu použít typům parametrů, použijte následující kód:

```fsharp
let cylinderVolume (radius : float) (length : float) : float
```

## <a name="calling-a-function"></a>Volání funkce

Volání funkce tak, že zadáte název funkce, za nímž následuje mezera a potom všechny argumenty oddělené mezerami. Například volání funkce **cylinderVolume** a výsledek přiřaďte hodnotu **. denní obj.**, napište následující kód:

```fsharp
let vol = cylinderVolume 2.0 3.0
```

## <a name="partial-application-of-arguments"></a>Částečné použití argumentů

Pokud zadáte méně než zadaný počet argumentů, vytvoříte novou funkci, která očekává zbývajících argumentů. Tento způsob zpracování argumentů se označuje jako *curryfikace* a je znakem funkčních programovacích jazyků, jako je F#. Předpokládejme například, že pracujete s dvou velikostech kanálu: jeden má poloměr **2.0** a druhý má poloměr **3.0**. Můžete například vytvořit funkce, které určují objem kanálu následujícím způsobem:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet106.fs)]

Další argument by pak poskytnete podle potřeby pro různé délky kanálu pro dvě různé velikosti:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet107.fs)]

## <a name="recursive-functions"></a>Rekurzivní funkce

*Rekurzivní funkce* jsou funkce, které volání sebe sama. Vyžadují, abyste určili **rec** následující klíčové slovo **nechat** – klíčové slovo. Volání rekurzivní funkce v rámci těla funkce stejně, jako by volání jakékoli volání funkce. Následující rekurzivní funkce vypočítá *n*<sup>th</sup> Fibonacciho číslo. Pořadí Fibonacciho číslo bylo zjištěno od antiquity a je pořadí, ve kterém je každý po sobě jdoucí čísla součtu předchozích dvou čísel v sekvenci.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet108.fs)]

Některé rekurzivní funkce mohou přetečení zásobníku programu nebo provést neefektivně, pokud nenapíšete je s opatrností a s povědomí o speciální techniky, jako je například používání průběžné součty a pokračování.

## <a name="function-values"></a>Hodnoty funkcí

V F#, všechny funkce jsou považovány za hodnot. ve skutečnosti jsou označovány jako *funkce hodnoty*. Protože funkce jsou hodnoty, se může sloužit jako argumenty dalších funkcí nebo v jiném kontextu použití hodnot. Tady je příklad, který přijímá hodnotu funkce jako argument funkce:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet109.fs)]

Určení typu hodnota funkce s použitím `->` token. Na levé straně tohoto tokenu je typ argumentu a na pravé straně je návratová hodnota. V předchozím příkladu `apply1` je funkce, která má funkci `transform` jako argument, ve kterém `transform` je funkce, která přebírá celé číslo a vrátí jinou celé číslo. Následující kód ukazuje, jak používat `apply1`:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet110.fs)]

Hodnota `result` bude 101 po spuštění předchozího kódu.

Více argumentů jsou odděleny po sobě jdoucích `->` tokeny, jak je znázorněno v následujícím příkladu:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet111.fs)]

Výsledkem je 200.

## <a name="lambda-expressions"></a>Výrazy lambda

A *výraz lambda* je nepojmenovaný funkce. V předchozích příkladech místo definování pojmenované funkce **přírůstek** a **mul**, můžete použít výrazy lambda následujícím způsobem:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet112.fs)]

Můžete definovat pomocí výrazů lambda `fun` – klíčové slovo. Výraz lambda se podobá definici funkce, s výjimkou, že místo `=` token, `->` token se používá k oddělení seznamu argumentů z těla funkce. Stejně jako v definici normální funkce typy argumentů lze odvodit nebo zadat explicitně a návratový typ výrazu lambda je odvozen z typu posledního výrazu v textu. Další informace najdete v tématu [výrazy Lambda: `fun` – Klíčové slovo](../functions/lambda-expressions-the-fun-keyword.md).

## <a name="function-composition-and-pipelining"></a>Skládání a paralelní zpracování funkcí

Funkce v F# může skládat z dalších funkcí. Složení dvou funkcí **function1** a **function2** je další funkci, která představuje použití **function1** a potom aplikaci **function2**:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet113.fs)]

Výsledkem je 202.

Paralelní zpracování volání funkce umožňuje být zřetězen dohromady jako následných operací. Paralelní zpracování funguje takto:

```fsharp
let result = 100 |> function1 |> function2
```

Výsledkem je znovu 202.

Operátory složení dvou funkcí používají a vrací funkci. operátory kanálu oproti tomu funkce a argument a vrátí hodnotu. Následující příklad kódu ukazuje rozdíl mezi operátory kanálu a skládání tím, že zobrazuje rozdíly v podpisech funkcí a využití.

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

## <a name="see-also"></a>Viz také:

- [Hodnoty](../values/index.md)
- [Referenční dokumentace jazyka F#](../index.md)