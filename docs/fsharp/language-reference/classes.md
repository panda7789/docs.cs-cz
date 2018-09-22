---
title: Třídy (F#)
description: 'Zjistěte, jak třídy F # jsou typy, které představují objekty, které mohou mít vlastnosti, metody a události.'
ms.date: 05/16/2016
ms.openlocfilehash: 71cd713d192d28565e879b79b2fc9e0530e5f841
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46577370"
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

Třídy představují základní popis typů objektů .NET; Třída je koncept primární typ, který podporuje objektově orientované programování v jazyce F #.

V předchozí syntaxi `type-name` je libovolný platný identifikátor. `type-params` Popisuje volitelné obecné parametry typu. Zahrnuje názvy parametrů typů a omezením uzavřen do lomených závorek (`<` a `>`). Další informace najdete v tématu [obecných typů](generics/index.md) a [omezení](generics/constraints.md). `parameter-list` Popisuje parametry konstruktoru. První modifikátor přístupu vztahují na daný typ druhý se vztahují k primárnímu konstruktoru. V obou případech se výchozí hodnota je `public`.

Zadejte základní třídu pro třídy pomocí `inherit` – klíčové slovo. Je nutné zadat argumenty, v závorkách, pro konstruktor základní třídy.

Deklarace pole nebo hodnoty, které jsou místní pro třídu pomocí funkce `let` vazby a musí následovat po obecná pravidla pro `let` vazby. `do-bindings` Části obsahuje kód, který se spustí při vytváření objektu.

`member-list` Se skládá z dalších konstruktory, instanci a deklarace statické metody, deklarace rozhraní, abstraktní vazby a deklaracích vlastností a událostí. Tyto možnosti jsou popsány v [členy](members/index.md).

`identifier` , Který se používá s nepovinným `as` – klíčové slovo udává název proměnnou instance nebo vlastní identifikátor, který je možné odkazovat na instanci typu v definici typu. Další informace najdete v části identifikátory Self dále v tomto tématu.

Klíčová slova `class` a `end` toto označení začátku a konce definice jsou volitelné.

Vzájemně rekurzivních typů, které jsou typy, které odkazují na sobě navzájem, jsou spojeny spolu s `and` – klíčové slovo pouze jsou vzájemně rekurzivní funkce. Příklad najdete v části vzájemně rekurzivních typů.

## <a name="constructors"></a>Konstruktory

Konstruktor je kód, který vytvoří instanci typu třídy. Konstruktory pro třídy fungují v jazyce F # trochu jinak než v jiných jazycích rozhraní .NET. V F # třídy, je vždy primární konstruktor, jehož argumenty jsou popsány v `parameter-list` , který následuje název typu a jehož subjekt se skládá z `let` (a `let rec`) vazby na začátku deklarace třídy a `do`vazby, které následují. Argumenty konstruktoru primární jsou v oboru v rámci deklarace třídy.

Můžete přidat další konstruktory pomocí `new` – klíčové slovo přidání člena, následujícím způsobem:

`new`(`argument-list`) = `constructor-body`

Tělo konstruktoru new musí vyvolat primární konstruktor, který je zadán v horní části deklarace třídy.

Tento koncept znázorňuje následující příklad. V následujícím kódu `MyClass` má dva konstruktory, primárního konstruktoru, který přebírá dva argumenty a jiného konstruktoru, který nepřijímá žádné argumenty.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2401.fs)]

## <a name="let-and-do-bindings"></a>let a do – vazby

`let` a `do` vazby v definici třídy formuláře těla konstruktoru třídy primární, a spouští se proto vždy, když je vytvořena instance třídy. Pokud `let` vazby je funkce, pak se zkompiluje do člena. Pokud `let` vazby má hodnotu, která se nepoužívá žádné funkce nebo člen, bude se zkompiluje do proměnné, která je místní pro konstruktor. V opačném případě je zkompilován do pole třídy. `do` Výrazy, které následují jsou kompilovány do primárního konstruktoru a spustit kód inicializace pro každou instanci. Protože žádné další konstruktory vždy volat primárnímu konstruktoru `let` vazby a `do` vazby vždy bude provedena bez ohledu na to, které se nazývá konstruktor.

Pole, která vytvořila `let` vazby je přístupná v rámci metody a vlastnosti třídy, ale jsou přístupné z statické metody, i v případě, že statické metody přijímají proměnnou instance jako parametr. K nim nelze přistupovat pomocí identifikátoru samotného, pokud existuje.

## <a name="self-identifiers"></a>Self – identifikátory

A *identifikátoru samotného* je název, který představuje aktuální instanci. Self – identifikátory vypadat podobně jako `this` – klíčové slovo v jazyce C# nebo C++ nebo `Me` v jazyce Visual Basic. Můžete definovat vlastní identifikátor dvěma různými způsoby v závislosti na tom, zda chcete identifikátoru samotného v oboru pro definici celé jedné třídy nebo pouze pro jednotlivé metody.

Chcete-li definovat vlastní identifikátor pro celou třídu, použijte `as` – klíčové slovo po pravých závorek parametru konstruktoru seznamu a zadejte název identifikátoru.

Pokud chcete definovat vlastní identifikátor pro právě jedna metoda, poskytují identifikátoru samotného v deklaraci člena, těsně před název metody a tečku (.) jako oddělovač.

Následující příklad kódu ukazuje dva způsoby vytvoření identifikátoru samotného. V prvním řádku `as` – klíčové slovo se používá k definování vlastní identifikátor. V pátém řádku identifikátor `this` se používá k definování vlastní identifikátor, jejichž rozsah je omezen na metodu `PrintMessage`.

```fsharp
type MyClass2(dataIn) as self =
    let data = dataIn
    do
        self.PrintMessage()
    member this.PrintMessage() =
        printf "Creating MyClass2 with Data %d" data
```

Na rozdíl od v jiných jazycích technologie .NET můžete pojmenovat identifikátoru samotného představ; můžete omezit na názvy, jako `self`, `Me`, nebo `this`.

Vlastní identifikátor, který je deklarován s `as` – klíčové slovo není inicializována až po `let` vazby jsou spouštěny. Proto jej nelze použít v `let` vazby. Můžete použít vlastní identifikátor v `do` část vazby.

## <a name="generic-type-parameters"></a>Parametry obecného typu

Parametry obecného typu jsou určené v lomených závorkách (`<` a `>`), ve formě jednoduché uvozovky, za nímž následuje identifikátor. Více parametrů obecného typu jsou odděleny čárkami. Parametr obecného typu je v oboru v celém deklarace. Následující příklad kódu ukazuje, jak zadat parametry obecného typu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2403.fs)]

Argumenty typu jsou odvozeny při použití typu. V následujícím kódu je odvozený typ posloupnost řazené kolekce členů.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24031.fs)]

## <a name="specifying-inheritance"></a>Určení dědičnosti

`inherit` Klauzule určuje přímou základní třídu, pokud existuje. V jazyce F # je povolen pouze jednu přímou základní třídu. Rozhraní, která třída implementuje nejsou považovány za základní třídy. Rozhraní jsou popsány v [rozhraní](Interfaces.md) tématu.

Metody a vlastnosti ze základní třídy lze přistupovat z odvozené třídy pomocí klíčového slova jazyka `base` jako identifikátor, následované tečkou (.) a název členu.

Další informace najdete v tématu [dědičnosti](inheritance.md).

## <a name="members-section"></a>Oddíl členové

V této části můžete definovat statické nebo instanci metody, vlastnosti, implementace rozhraní, abstraktní členy, deklarace události a další konstruktory. Umožní a proveďte vazby nemůže být použit v této části. Vzhledem k tomu, že členové mohou být přidány do různých typů F # kromě třídy, jsou popsány v samostatném tématu [členy](members/index.md).

## <a name="mutually-recursive-types"></a>Vzájemně rekurzivní typy

Při definování typů, které odkazovat na sebe navzájem cyklické způsobem je řetězec společně definice typu s použitím `and` – klíčové slovo. `and` Nahradí – klíčové slovo `type` – klíčové slovo pro všechny s výjimkou první definici následujícím způsobem.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2404.fs)]

Výstupem je seznam všech souborů v aktuálním adresáři.

## <a name="when-to-use-classes-unions-records-and-structures"></a>Kdy použít třídy, sjednocení, záznamů a struktury

S ohledem na celou řadu typů lze vybírat, musíte mít dostatečné povědomí o co každý typ je určen pro vyberte požadovaný typ pro konkrétní situaci. Třídy jsou určeny k použití v objektově orientované programování kontextech. Objektově orientované programování je dominantní paradigma použít v aplikacích, které jsou určeny pro rozhraní .NET Framework. Pokud je váš kód F # těsná spolupráce s rozhraní .NET Framework nebo jiné objektově orientované knihovny a zejména v případě, že budete muset rozšířit z objektově orientované typu systému, jako je například knihovna uživatelského rozhraní, třídy jsou pravděpodobně vhodné.

Pokud nejsou úzce spolupráce s objektově orientované kódu nebo pokud píšete kód, který je samostatná a proto chráněný před častá interakce s kódem objektově orientované, zvažte použití záznamů a rozlišovaná sjednocení. Jediné, dobře přiměje – out jako jednodušší alternativu k hierarchii objektů lze často použít diskriminované sjednocení, společně s odpovídající vzor odpovídající kód. Další informace o rozlišovaná sjednocení, naleznete v tématu [Rozlišované sjednocení](discriminated-unions.md).

Výhodou je jednodušší než třídy jsou záznamy, ale záznamy nejsou vhodné, když požadavky typu překročí, co lze provést pomocí jejich jednoduchost. Záznamy jsou v podstatě jednoduchá agregace hodnot, bez samostatné konstruktory, které můžete provést vlastní akce, bez skrytých polí a bez implementace dědičnosti nebo rozhraní. Pro záznamy, aby bylo mnohem složitější jejich chování je možné přidat členy jako jsou vlastnosti a metody, pole, uložená v záznamu jsou stále jednoduché agregace hodnot. Další informace o záznamech najdete v tématu [záznamy](records.md).

Struktury jsou také užitečné pro malá agregace dat, ale liší od třídy a záznamy, že jsou typy hodnot .NET. Záznamy a třídy jsou odkazové typy .NET. Sémantika typy hodnot a odkazové typy se liší v tom, že typy hodnot jsou předávány hodnotou. To znamená, že se zkopírují bit bitu, když se předá jako parametr nebo vrácená z funkce. Jsou také uloženy do zásobníku nebo, pokud jsou použity jako pole, vložená do nadřazeného objektu namísto uložené v samostatném umístění na haldě. Struktury jsou proto vhodné pro často používaná data při režijní náklady na přístup k haldě je nějaký problém. Další informace o strukturách naleznete v tématu [struktury](structures.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Členové](members/index.md)
- [Dědičnost](inheritance.md)
- [Rozhraní](interfaces.md)
