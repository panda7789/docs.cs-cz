---
title: Třídy (F#)
description: 'Zjistěte, jak F # třídy jsou typy, které představují objekty, které mohou mít vlastnosti, metod a události.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 0bfb45b6481576729bfe8d4bd016fb151757660a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="classes"></a>Třídy

*Třídy* jsou typy, které představují objekty, které mohou mít vlastnosti, metod a události.


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
Třídy představují základní popis typy objektů .NET; Třída je koncept primární typ, který podporuje objektově orientované programování v F #.

V předchozím syntaxi `type-name` je libovolný platný identifikátor. `type-params` Popisuje parametry volitelné obecného typu. Obsahuje názvy parametrů typu a omezení uzavřené v lomených závorkách (`<` a `>`). Další informace najdete v tématu [obecné typy](generics/index.md) a [omezení](generics/constraints.md). `parameter-list` Popisuje parametry konstruktor. První – modifikátor přístupu se vztahují na typ; druhá se vztahují na primární konstruktoru. V obou případech se výchozí hodnota je `public`.

Zadejte základní třídu pro třídy pomocí `inherit` – klíčové slovo. Je třeba zadat argumenty, v závorkách, pro konstruktor základní třídy.

Deklarace pole nebo hodnoty, které jsou místní vzhledem k třídě pomocí funkce `let` vazby a musí postupovat podle obecná pravidla pro `let` vazby. `do-bindings` Část obsahuje být spuštěn při vytváření objektů.

`member-list` Se skládá z další konstruktory, instanci a statickou metodu deklarace, rozhraní deklarace, abstraktní vazby a deklarace vlastnosti a události. Tyto možnosti jsou popsány v [členy](members/index.md).

`identifier` Používané s nepovinným `as` – klíčové slovo poskytuje název pro proměnnou instance nebo vlastní identifikátor, který můžete použít v definici typu, který bude odkazovat na instanci typu. Další informace najdete v části identifikátory samoobslužné později v tomto tématu.

Klíčová slova `class` a `end` , označte začátku a konce definice jsou volitelné.

Vzájemně rekurzivní typy, které jsou typy, které odkazují na sobě navzájem, připojeni společně s `and` stejně jako vzájemně rekurzivní funkce jsou – klíčové slovo. Příklad najdete v části vzájemně rekurzivní typy.


## <a name="constructors"></a>Konstruktory
Konstruktor je kód, který vytvoří instanci typu třídy. Konstruktory pro třídy fungují v jazyce F # trochu jinak než v jinými jazyky rozhraní .NET. F # třídy, je vždy primární konstruktor jejichž argumenty jsou popsané v `parameter-list` , následuje název typu a jehož subjekt se skládá z `let` (a `let rec`) vazby na začátku deklaraci třídy a `do`vazby, které následují. Argumenty primární konstruktoru jsou v oboru v rámci deklaraci třídy.

Můžete přidat další konstruktory pomocí `new` – klíčové slovo přidání člena, následujícím způsobem:

`new`(`argument-list`) = `constructor-body`

Text nového konstruktor musí volat primární konstruktor, který je zadán v horní části deklaraci třídy.

Následující příklad ilustruje tento koncept. V následujícím kódu `MyClass` má dva konstruktory, primární konstruktor, který přebírá dva argumenty a jiný konstruktor, který nezadávaly žádné argumenty.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2401.fs)]
    
## <a name="let-and-do-bindings"></a>umožňují a do – vazby

`let` a `do` vazby v definici třídy tvoří text konstruktoru třídy primární, a proto spustit vždy, když se vytvoří instance třídy. Pokud `let` vazba je funkce, a potom se zkompiluje do člena. Pokud `let` vazba je hodnota, která se nepoužívá v libovolném funkce nebo člen a pak se zkompiluje do proměnné, která je místní pro konstruktor. Jinak je zkompilovat do pole třídy. `do` Výrazy, které následují kompilovány do primární konstruktor a spouštění kódu inicializace pro všechny instance. Vzhledem k tomu, že žádné další konstruktory vždy volat primární konstruktor, `let` vazby a `do` vazby vždy provést bez ohledu na to, které volání konstruktoru.

Pole, které jsou vytvořené pomocí `let` vazby je přístupná prostřednictvím metody a vlastnosti třídy; však budou nelze získat přístup z statických metod, i pokud statických metod proměnnou instance jako parametr. Nemůže být přistupovali pomocí vlastní identifikátor, pokud existuje.


## <a name="self-identifiers"></a>Self – identifikátory

A *vlastní identifikátor* je název, který představuje aktuální instanci. Self – identifikátory vypadat `this` – klíčové slovo v C# nebo C++ nebo `Me` v jazyce Visual Basic. Můžete definovat vlastní identifikátor dvěma různými způsoby v závislosti na tom, zda má být v oboru pro definici celou třídy nebo pouze pro jednotlivé metody vlastní identifikátor.

Chcete-li definovat vlastní identifikátor pro celou třídu, použijte `as` – klíčové slovo po zavření závorkách parametr konstruktoru seznamu a zadejte název identifikátoru.

K definování vlastní identifikátor pro právě jednu metodu, zadejte vlastní identifikátor v deklaraci člen, těsně před název metody a tečka (.) jako oddělovač.

Následující příklad kódu ukazuje dva způsoby vytvoření vlastní identifikátor. V prvním řádku `as` – klíčové slovo se používá k definování vlastní identifikátor. V páté řádku identifikátor `this` se používá k definování vlastní identifikátor, jejíž obor je omezen na metodu `PrintMessage`.

```fsharp
type MyClass2(dataIn) as self =
    let data = dataIn
    do
        self.PrintMessage()
    member this.PrintMessage() =
        printf "Creating MyClass2 with Data %d" data
```

Na rozdíl od v jiných jazyků .NET, můžete pojmenovat vlastní identifikátor ale chcete; nejsou omezena na názvy, jako `self`, `Me`, nebo `this`.

Vlastní identifikátor, který je deklarovaný s `as` – klíčové slovo není inicializován až po `let` provedení vazby. Proto jej nelze použít v `let` vazby. Můžete použít vlastní identifikátor v `do` části vazby.


## <a name="generic-type-parameters"></a>Parametry obecného typu

Parametry obecného typu jsou určené v lomené závorky (`<` a `>`), ve formě jednoduché uvozovky, za nímž následuje identifikátor elementu. Několik parametrů obecného typu jsou oddělené čárkami. Parametr obecného typu je v oboru v celém prohlášení. Následující příklad kódu ukazuje, jak zadat parametry obecného typu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2403.fs)]

Argumenty typu jsou odvodit při použití typu. V následujícím kódu je odvozeném typu pořadí řazené kolekce členů.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24031.fs)]
    
## <a name="specifying-inheritance"></a>Určení dědičnosti

`inherit` Klauzule identifikuje přímé základní třídy, pokud existuje. V F # je povolen pouze jeden přímé základní třídy. Rozhraní, která implementuje třídu nejsou považovány za základní třídy. Rozhraní, které jsou popsané v [rozhraní](Interfaces.md) tématu.

Metody a vlastnosti základní třídy můžete přistupovat z odvozené třídy pomocí klíčové slovo jazyka `base` jako identifikátor, za nímž následuje tečka (.) a název člena.

Další informace najdete v tématu [dědičnosti](inheritance.md).


## <a name="members-section"></a>Oddíl členové
V této části můžete definovat statické nebo instanci metody, vlastnosti, implementace rozhraní, abstraktní členy, událostí prohlášení a další konstruktory. Umožňují a provést vazby nemůže vyskytovat v této části. Vzhledem k tomu, že členové mohou být přidány do různých typů F # kromě třídy, jsou popsané v samostatném tématu, [členy](members/index.md).


## <a name="mutually-recursive-types"></a>Vzájemně rekurzivní typy
Když definujete typy, které vzájemně odkazovat cyklické způsobem, můžete řetězec společně definic typů pomocí `and` – klíčové slovo. `and` Nahrazuje – klíčové slovo `type` – klíčové slovo na všech kromě první definice, následujícím způsobem.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2404.fs)]

Výstup je seznam všech souborů v aktuálním adresáři.


## <a name="when-to-use-classes-unions-records-and-structures"></a>Kdy použít třídy, sjednocení, záznamy a struktury
Zadána řadu typů na výběr, je potřeba mít dobrou znalost jazyka co každý typ je určen pro vyberte odpovídající typ pro konkrétní situaci. Třídy jsou navrženy pro použití v objektově orientované programování kontexty. Objektově orientované programování je dominantní zlepší používat v aplikacích, které jsou napsané pro rozhraní .NET Framework. Pokud má váš kód F # úzce spolupracovat rozhraní .NET Framework nebo jiné knihovny objektově orientované a obzvláště pokud máte rozšíření z objektově orientované typ systému, jako je například knihovna uživatelského rozhraní, třídy jsou pravděpodobně vhodné.

Pokud nejsou úzce spolupráce s objektově orientované kód, nebo pokud píšete kód, který je samostatný a proto chráněný před časté interakci s objektově orientované kódu, byste měli zvážit použití záznamů a rozlišované sjednocení. Jedinou dobře myšlenku – out rozlišovaná sjednocení, společně s odpovídající vzor odpovídající kód, můžete často použít jako jednodušší alternativní hierarchii objektu. Další informace o rozlišovaná sjednocení najdete v tématu [Rozlišované sjednocení](discriminated-unions.md).

Výhodou je jednodušší než třídy jsou záznamy, ale záznamy nejsou vhodné, pokud jsou požadavky typ překročit, co můžete udělat s jejich jednoduchost. Záznamy jsou v podstatě jednoduché agregace hodnot, bez samostatné konstruktory, které můžete provést vlastní akci, bez skrytá pole a bez implementace dědičnosti nebo rozhraní. Členy například vlastnosti a metody, je možné přidat záznamy, aby jejich chování složitější, pole uložené v záznamu jsou stále jednoduché agregace hodnot. Další informace o záznamech najdete v tématu [záznamy](records.md).

Struktury jsou užitečné i pro malý agregace dat, ale se liší od třídy a záznamy, protože se typy hodnotu .NET. Třídy a záznamy jsou referenční typy .NET. Sémantika typy hodnot a typy odkazu se liší, že jsou typy hodnot předaná hodnota. To znamená, že se kopírují bit pro bit, pokud jsou předána jako parametr nebo vrácená z funkce. Jsou také uloženy v zásobníku nebo, pokud se používají jako pole, vložený v nadřazeném objektu místo, které jsou uložené v vlastní samostatné umístění v haldě. Proto jsou vhodné pro často používaná data struktury, když nároky na přístup k haldě k potížím. Další informace o struktury najdete v tématu [struktury](structures.md).


## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F#](index.md)

[Členové](members/index.md)

[Dědičnost](inheritance.md)

[Rozhraní](interfaces.md)

