---
title: Třídy
description: Zjistěte, F# jak třídy jsou typy reprezentující objekty, které mohou mít vlastnosti, metody a události.
ms.date: 05/16/2016
ms.openlocfilehash: 5c012d028bc1f89e3e9f5969b3461faab9aad3a0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630443"
---
# <a name="classes"></a>Třídy

*Třídy* jsou typy, které představují objekty, které mohou mít vlastnosti, metody a události.

## <a name="syntax"></a>Syntaxe

```fsharp
// Class definition:
type [access-modifier] type-name [type-params] [access-modifier] ( parameter-list ) [ as identifier ] =
[ class ]
[ inherit base-type-name(base-constructor-args) ]
[ let-bindings ]
[ do-bindings ]
member-list
...
[ end ]
// Mutually recursive class definitions:
type [access-modifier] type-name1 ...
and [access-modifier] type-name2 ...
...
```

## <a name="remarks"></a>Poznámky

Třídy reprezentují základní popis typů objektů .NET. Třída je primární typ koncept, který podporuje objektově orientované programování v F#.

V předchozí syntaxi `type-name` je platný identifikátor. `type-params` Popisuje volitelné parametry obecného typu. Skládá se z názvů parametrů typu a omezení uzavřených do lomených závorek `>`(`<` a). Další informace najdete v tématu [Obecné typy](./generics/index.md) a [omezení](./generics/constraints.md). `parameter-list` Popisuje parametry konstruktoru. První modifikátor přístupu se vztahuje k typu; druhý se vztahuje k primárnímu konstruktoru. V obou případech je `public`výchozí hodnota.

Základní třídu pro třídu určíte pomocí `inherit` klíčového slova. Pro konstruktor základní třídy je nutné dodat argumenty v závorkách.

Deklarujete pole nebo hodnoty funkcí, které jsou lokální pro třídu, pomocí `let` vazeb a musíte dodržovat obecná pravidla pro `let` vazby. `do-bindings` Oddíl obsahuje kód, který má být proveden při vytváření objektu.

`member-list` Obsahuje další konstruktory, instance a deklarace statických metod, deklarace rozhraní, abstraktní vazby a deklarace vlastností a událostí. Ty jsou popsány v tématu [members](./members/index.md).

Rozhraní `identifier` , které je použito s klíčovým slovem volitelné `as` , poskytuje název proměnné instance nebo identifikátor autotest, který lze použít v definici typu pro odkazování na instanci typu. Další informace najdete v části hlavní identifikátory níže v tomto tématu.

Klíčová `class` slova `end` , která označují začátek a konec definice, jsou volitelná.

Vzájemně se rekurzivní typy, které odkazují na sebe navzájem, spolu s `and` klíčovým slovem spojí stejně jako vzájemně rekurzivní funkce. Příklad naleznete v části vzájemně rekurzivní typy.

## <a name="constructors"></a>Konstruktory

Konstruktor je kód, který vytvoří instanci typu třídy. Konstruktory pro třídy fungují trochu jinak F# než v jiných jazycích .NET. Ve F# třídě je vždy primární konstruktor, jehož argumenty jsou popsány v `parameter-list` , které následují za názvem typu a jejichž `let` tělo se skládá z vazeb (a `let rec`) na začátku deklarace třídy a `do` následující vazby. Argumenty primárního konstruktoru jsou v oboru v rámci deklarace třídy.

Můžete přidat další konstruktory pomocí `new` klíčového slova pro přidání člena následujícím způsobem:

`new`(`argument-list`) = `constructor-body`

Tělo nového konstruktoru musí vyvolat primární konstruktor, který je určen v horní části deklarace třídy.

Následující příklad znázorňuje tento koncept. V následujícím kódu `MyClass` má dva konstruktory, primární konstruktor, který přebírá dva argumenty a jiný konstruktor, který nepřijímá žádné argumenty.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2401.fs)]

## <a name="let-and-do-bindings"></a>Vazby let a dělat

Vazby `let` a`do` v definici třídy tvoří tělo konstruktoru primární třídy, a proto jsou spouštěny pokaždé, když je vytvořena instance třídy. Pokud je `let` vazba funkce, je zkompilována do členu. Pokud je `let` vazba hodnota, která není použita v žádné funkci nebo členu, je zkompilována do proměnné, která je místní pro konstruktor. V opačném případě je zkompilována do pole třídy. `do` Výrazy, které následují, jsou zkompilovány do primárního konstruktoru a spouštějí inicializační kód pro každou instanci. Vzhledem k tomu, že všechny další konstruktory vždy volají primární `let` konstruktor, `do` vazby a vazby se vždy spouštějí bez ohledu na to, který konstruktor je volán.

Pole, která jsou vytvořena `let` pomocí vazeb, mohou být k dispozici v rámci metod a vlastností třídy. nelze je však získat z statických metod, i když statické metody přebírají proměnnou instance jako parametr. K nim nelze přistupovat pomocí automatického identifikátoru, pokud existuje.

## <a name="self-identifiers"></a>Osobní identifikátory

*Samotný identifikátor* je název, který představuje aktuální instanci. `this` Identifikátory sebe připomínají klíčové slovo v C# nebo C++ nebo `Me` v Visual Basic. Vlastní identifikátor můžete definovat dvěma různými způsoby, v závislosti na tom, zda chcete, aby byl vlastní identifikátor v rozsahu pro celou definici třídy nebo pouze pro jednotlivé metody.

Chcete-li definovat identifikátor osobníku pro celou třídu, použijte `as` klíčové slovo za pravou závorku seznamu parametrů konstruktoru a zadejte název identifikátoru.

Chcete-li definovat identifikátor sebe samo pro jednu metodu, zadejte identifikátor samotné v deklaraci členu, těsně před názvem metody a tečkou (.) jako oddělovač.

Následující příklad kódu ukazuje dva způsoby, jak vytvořit identifikátor sebe. Na prvním řádku `as` se klíčové slovo používá k definování identifikátoru sebe. Na pátém řádku je identifikátor `this` použit k definování identifikátoru samočinného rozsahu, jehož rozsah je omezen na metodu. `PrintMessage`

```fsharp
type MyClass2(dataIn) as self =
    let data = dataIn
    do
        self.PrintMessage()
    member this.PrintMessage() =
        printf "Creating MyClass2 with Data %d" data
```

Na rozdíl od jiných jazyků .NET můžete sami pojmenovat identifikátor, který chcete, ale. Nejste omezeni na názvy `self`, `Me`například, nebo `this`.

Identifikátor autotest, který je deklarován s `as` klíčovým slovem, není inicializován `let` až po provedení vazeb. Proto jej nelze použít ve `let` vazbách. V `do` části Bindings (vazby) můžete použít samotný identifikátor.

## <a name="generic-type-parameters"></a>Parametry obecného typu

Parametry obecného typu jsou zadány v lomených`<` závorkách (a `>`) ve formě jednoduché uvozovky následované identifikátorem. Více parametrů obecného typu je odděleno čárkami. Parametr obecného typu je v oboru v celé deklaraci. Následující příklad kódu ukazuje, jak určit parametry obecného typu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2403.fs)]

Argumenty typu jsou odvozeny při použití typu. V následujícím kódu je odvozený typ sekvencí řazených kolekcí členů.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet24031.fs)]

## <a name="specifying-inheritance"></a>Určení dědičnosti

`inherit` Klauzule identifikuje přímou základní třídu, pokud existuje. V F#nástroji je povolena pouze jedna přímá základní třída. Rozhraní, která třída implementuje, nejsou považovány za základní třídy. Rozhraní jsou popsána v tématu [rozhraní](Interfaces.md) .

K metodám a vlastnostem základní třídy můžete přistupovat z odvozené třídy pomocí klíčového slova `base` Language jako identifikátoru následovaného tečkou (.) a názvem člena.

Další informace najdete v tématu [Dědičnost](inheritance.md).

## <a name="members-section"></a>Oddíl members

V této části můžete definovat statické nebo instanční metody, vlastnosti, implementace rozhraní, abstraktní členy, deklarace událostí a další konstruktory. V této části se nemůžou objevit vazby let a do. Vzhledem k tomu, že členy mohou být přidány F# do různých typů kromě tříd, jsou popsány v samostatném tématu, [členy](./members/index.md).

## <a name="mutually-recursive-types"></a>Vzájemně rekurzivní typy

Při definování typů, které na sobě navzájem odkazují, se řetězcem spojí definice typu pomocí `and` klíčového slova. `and` Klíčové slovo `type` nahrazuje klíčové slovo pro všechny kromě první definice, a to následujícím způsobem.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2404.fs)]

Výstupem je seznam všech souborů v aktuálním adresáři.

## <a name="when-to-use-classes-unions-records-and-structures"></a>Kdy použít třídy, sjednocení, záznamy a struktury

Vzhledem k nejrůznějším typům, ze kterých si můžete vybrat, je potřeba mít dobré znalosti o tom, k čemu je každý typ navržený, aby se dal vybrat vhodný typ pro konkrétní situaci. Třídy jsou navrženy pro použití v objektově orientovaných kontextech programování. Objektově orientované programování je dominantní paradigma používaný v aplikacích, které jsou zapsány pro .NET Framework. Pokud váš F# kód musí úzce fungovat s .NET Framework nebo jinou knihovnou orientovanou na objekt, a zejména v případě, že je nutné roztáhnout z objektově orientovaného systému typů, jako je například knihovna uživatelského rozhraní, třídy jsou pravděpodobně vhodné.

Pokud nejste úzce spolupracujete s objektově orientovaným kódem, nebo pokud píšete kód, který je samostatný a je proto chráněn před častými interakcemi s objektově orientovaným kódem, měli byste zvážit použití záznamů a rozlišených sjednocení. Jedno, dobře považované za rozlišené sjednocení spolu s odpovídajícím kódem odpovídajícím vzoru lze často použít jako jednodušší alternativu k hierarchii objektů. Další informace o rozlišených sjednoceních naleznete v tématu [rozlišené sjednocení](discriminated-unions.md).

Záznamy mají výhodu, že je jednodušší než třídy, ale záznamy nejsou vhodné, pokud požadavky typu překračují, co je možné dosáhnout s jejich jednoduchostí. Záznamy jsou v podstatě jednoduché agregace hodnot bez samostatných konstruktorů, které mohou provádět vlastní akce, bez skrytých polí a bez implementace dědičnosti nebo rozhraní. I když mohou být členy, jako jsou vlastnosti a metody, přidány do záznamů, aby jejich chování bylo složitější, pole uložená v záznamu jsou stále jednoduchou agregací hodnot. Další informace o záznamech najdete v tématu [záznamy](records.md).

Struktury jsou také užitečné pro malé agregované údaje, ale liší se od tříd a záznamů v tom, že jsou typy hodnot .NET. Třídy a záznamy jsou typy odkazů .NET. Sémantika typů hodnot a odkazových typů se liší v tom, že typy hodnot jsou předány hodnotou. To znamená, že se kopírují bit pro bitovou kopii, když jsou předány jako parametr nebo vráceny z funkce. Jsou také uloženy v zásobníku nebo, jsou-li použity jako pole, vloženy do nadřazeného objektu místo uložení do jejich samostatného umístění v haldě. Proto jsou struktury vhodné pro často používaná data v případě, že režie přístupu k haldě je problém. Další informace o strukturách naleznete v tématu [struktury](structures.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Členové](./members/index.md)
- [Dědičnost](inheritance.md)
- [Rozhraní](interfaces.md)
