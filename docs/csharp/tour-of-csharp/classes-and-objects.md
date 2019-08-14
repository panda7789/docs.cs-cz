---
title: Třídy a objekty v C# -A prohlídku C# jazyka
description: Začínáte C#? Přečtěte si tento přehled tříd, objektů a dědičnosti.
ms.date: 08/10/2016
ms.assetid: 63a89bde-0f05-4bc4-b0cd-4f693854f0cd
ms.openlocfilehash: ff83a3198c6c9fb4c4a438d2486614a211c913ec
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971460"
---
# <a name="classes-and-objects"></a>Třídy a objekty

*Třídy* jsou základem C#typů. Třída je datová struktura, která kombinuje stav (pole) a akce (metody a další členy funkce) v jedné jednotce. Třída poskytuje definici pro dynamicky vytvořené *instance* třídy, označované také jako *objekty*. Třídy podporují *Dědičnost* a *polymorfismus*, mechanismy, kterými mohou *odvozené třídy* roztáhnout a specializovat *základní třídy*.

Nové třídy jsou vytvářeny pomocí deklarací třídy. Deklarace třídy začíná hlavičkou, která určuje atributy a modifikátory třídy, název třídy, základní třídu (Pokud je daná) a rozhraní implementovaná třídou. Pod hlavičkou následuje tělo třídy, které se skládá ze seznamu deklarací členů napsaných mezi oddělovači `{` a. `}`

Následuje deklarace jednoduché třídy s názvem `Point`:

[!code-csharp[PointClass](~/samples/snippets/csharp/tour/classes-and-objects/Point.cs#L3-L11)]

Instance tříd jsou vytvořeny pomocí `new` operátoru, který přiděluje paměť pro novou instanci, vyvolá konstruktor pro inicializaci instance a vrátí odkaz na instanci. Následující příkazy vytvoří dva objekty Point a ukládají odkazy na tyto objekty ve dvou proměnných:

[!code-csharp[PointExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L9-L10)]

Paměť obsazená objektem je automaticky uvolněna v případě, že objekt již není dostupný. Není ani možné explicitně zrušit přidělení objektů v C#.

## <a name="members"></a>Členové

Členy třídy jsou buď statické členy, nebo členy instance. Statické členy patří ke třídám a členy instance patří do objektů (instance tříd).

Následující příklad obsahuje přehled druhů členů, které třída může obsahovat.

* Konstanty
  - Konstantní hodnoty přidružené ke třídě
* Pole
  - Proměnné třídy
* Metody
  - Výpočty a akce, které mohou být provedeny třídou
* Vlastnosti
  - Akce spojené s čtením a zápisem s názvem vlastnosti třídy
* Indexery
  - Akce přidružené k indexování instancí třídy, jako je pole
* Události
  - Oznámení, která mohou být vygenerována třídou
* Operátory
  - Převody a operátory výrazů podporované třídou
* Konstruktory
  - Akce vyžadované pro inicializaci instancí třídy nebo samotné třídy
* Finalizační metody
  - Akce, které se mají provést před tím, než se instance třídy trvale zahodí
* Typy
  - Vnořené typy deklarované třídou

## <a name="accessibility"></a>Usnadnění

Každý člen třídy má přidruženou přístupnost, která řídí oblasti textu programu, které mají přístup k členu. Existuje šest možných forem usnadnění přístupu. Tyto jsou shrnuté níže.

* `public`
  - Přístup není omezený
* `protected`
  - Přístup omezený na tuto třídu nebo třídy odvozené z této třídy
* `internal`
  - Přístup omezený na aktuální sestavení (. exe,. dll atd.)
* `protected internal`
  - Přístup omezený na obsahující třídu, třídy odvozené od obsahující třídy nebo třídy v rámci stejného sestavení
* `private`
  - Přístup omezený na tuto třídu
* `private protected`
  - Přístup omezený na obsahující třídu nebo třídy odvozené z nadřazeného typu v rámci stejného sestavení

## <a name="type-parameters"></a>Parametry typu

Definice třídy může určovat sadu parametrů typu za názvem třídy a lomenými závorkami ohraničující seznam názvů parametrů typu. Parametry typu lze potom použít v těle deklarací třídy k definování členů třídy. V následujícím příkladu parametry `Pair` typu jsou `TFirst` a `TSecond`:

[!code-csharp[Pair](~/samples/snippets/csharp/tour/classes-and-objects/Pair.cs#L3-L7)]

Typ třídy, která je deklarována pro přijetí parametrů typu, se nazývá *typ obecné třídy*. Typy struktury, rozhraní a delegátů můžou být také obecné.
Při použití obecné třídy je nutné zadat argumenty typu pro každý z parametrů typu:

[!code-csharp[PairExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L15-L17)]

Obecný typ s poskytnutými argumenty typu, jako `Pair<int,string>` je například výše, se označuje jako *konstruovaný typ*.

## <a name="base-classes"></a>Základní třídy

Deklarace třídy může specifikovat základní třídu za názvem třídy a parametry typu s dvojtečkou a názvem základní třídy. Vynechání specifikace základní třídy je stejné jako odvození z typu `object`. V následujícím příkladu `Point3D` je základní třída třídy `Point` `Point` a základní třída `object`:

[!code-csharp[Point3DClass](~/samples/snippets/csharp/tour/classes-and-objects/Point.cs#L3-L20)]

Třída dědí členy své základní třídy. Dědičnost znamená, že třída implicitně obsahuje všechny členy své základní třídy, s výjimkou instancí a statických konstruktorů a finalizační metody základní třídy. Odvozená třída může přidat nové členy do těch, které dědí, ale nemůže odebrat definici zděděného člena. V předchozím příkladu `Point3D` `x` dědí pole a `y` z `Point`a každá `Point3D` instance obsahuje tři pole, `x`, `y`a `z`.

Implicitní převod existuje z typu třídy na libovolný z jeho základních typů třídy. Proto proměnná typu třídy může odkazovat na instanci této třídy nebo instanci jakékoli odvozené třídy. Například s ohledem na předchozí deklarace třídy může proměnná typu `Point` odkazovat buď na `Point` , nebo `Point3D`:

[!code-csharp[Point3DExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L22-L23)]

## <a name="fields"></a>Pole

*Pole* je proměnná, která je přidružena ke třídě nebo s instancí třídy.

Pole deklarované pomocí statického modifikátoru definuje statické pole. Statické pole identifikuje právě jedno umístění úložiště. Bez ohledu na to, kolik instancí třídy je vytvořeno, existuje pouze jedna kopie statického pole.

Pole deklarované bez statického modifikátoru definuje pole instance. Každá instance třídy obsahuje samostatnou kopii všech polí instance této třídy.

V následujícím příkladu má `Color` každá instance třídy samostatnou kopii `r`polí `Black`instance, `g`a `b` `Red`, ale je k dispozici pouze jedna kopie, `White`,, `Green` a`Blue` statická pole:

[!code-csharp[ColorClass](~/samples/snippets/csharp/tour/classes-and-objects/Color.cs#L3-L17)]

Jak je znázorněno v předchozím příkladu, *pole jen pro čtení* mohou být deklarována `readonly` s modifikátorem. Přiřazení k `readonly` poli může být provedeno pouze v rámci deklarace pole nebo v konstruktoru ve stejné třídě.

## <a name="methods"></a>Metody

*Metoda* je člen, který implementuje výpočet nebo akci, kterou lze provést pomocí objektu nebo třídy. *Statické metody* jsou k dispozici prostřednictvím třídy. *Metody instance* jsou k dispozici prostřednictvím instancí třídy.

Metody mohou mít seznam *parametrů*, které reprezentují hodnoty nebo odkazy na proměnné předané metodě a *návratový typ*, který určuje typ počítané hodnoty a vrácený metodou. Návratový typ metody je `void` , pokud nevrací hodnotu.

Podobně jako typy mohou metody mít také sadu parametrů typu, pro které argumenty typu musí být zadány při volání metody. Na rozdíl od typů lze argumenty typu často odvodit z argumentů volání metody a nemusí být explicitně předány.

*Signatura* metody musí být jedinečná ve třídě, ve které je metoda deklarovaná. Signatura metody se skládá z názvu metody, počtu parametrů typu a počtu, modifikátorů a typů jeho parametrů. Podpis metody nezahrnuje návratový typ.

### <a name="parameters"></a>Parametry

Parametry slouží k předání hodnot nebo odkazů na proměnné metody. Parametry metody získají jejich skutečné hodnoty z *argumentů* , které jsou zadány při volání metody. Existují čtyři typy parametrů: parametry hodnoty, parametry odkazu, výstupní parametry a pole parametrů.

*Parametr hodnoty* se používá pro předávání vstupních argumentů. Parametr hodnoty odpovídá místní proměnné, která vrací počáteční hodnotu z argumentu předaného pro parametr. Úpravy parametru hodnoty neovlivňují argument, který byl předán parametru.

Parametry hodnoty mohou být volitelné, zadáním výchozí hodnoty, aby bylo možné vynechat odpovídající argumenty.

*Parametr reference* se používá pro předávání argumentů odkazem. Argument předaný parametru reference musí být proměnná s určitou hodnotou a během provádění metody představuje parametr reference stejné umístění úložiště jako proměnná argumentu. Parametr reference je deklarován s `ref` modifikátorem. Následující příklad ukazuje použití `ref` parametrů.

[!code-csharp[swapExample](~/samples/snippets/csharp/tour/classes-and-objects/RefExample.cs#L3-L18)]

*Výstupní parametr* se používá pro předávání argumentů odkazem. Je podobná referenčnímu parametru, s tím rozdílem, že nevyžaduje explicitně přiřadit hodnotu k argumentu, který je k dispozici volajícímu. Výstupní parametr je deklarován s `out` modifikátorem. Následující příklad ukazuje použití `out` parametrů pomocí syntaxe představené v C# 7.

[!code-csharp[OutExample](~/samples/snippets/csharp/tour/classes-and-objects/OutExample.cs#L3-L17)]

*Pole parametrů* povoluje proměnný počet argumentů, které mají být předány metodě. Pole parametrů je deklarováno s `params` modifikátorem. Pouze poslední parametr metody může být pole parametrů a typ pole parametrů musí být jednorozměrné pole. Metody Write a WriteLine <xref:System.Console?displayProperty=nameWithType> třídy jsou vhodnými příklady použití pole parametrů. Jsou deklarovány následujícím způsobem.

[!code-csharp[ConsoleExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L78-L83)]

V rámci metody, která používá pole parametrů, se pole parametru chová stejně jako regulární parametr typu pole. Při vyvolání metody s parametrem pole je však možné předat buď jeden argument typu pole parametru, nebo libovolný počet argumentů typu prvku pole parametrů. V druhém případě je instance pole automaticky vytvořena a inicializována s danými argumenty. Tento příklad

[!code-csharp[StringFormat](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L55-L55)]

je ekvivalentem zápisu následujícího.

[!code-csharp[StringFormat2](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L30-L35)]

### <a name="method-body-and-local-variables"></a>Tělo metody a místní proměnné

Tělo metody Určuje příkazy, které mají být provedeny při volání metody.

Tělo metody může deklarovat proměnné, které jsou specifické pro vyvolání metody. Tyto proměnné se nazývají *místní proměnné*. Místní deklarace proměnné Určuje název typu, název proměnné a pravděpodobně počáteční hodnotu. Následující příklad deklaruje místní proměnnou `i` s počáteční hodnotou nula a místní proměnnou `j` bez počáteční hodnoty.

[!code-csharp[Squares](~/samples/snippets/csharp/tour/classes-and-objects/Squares.cs#L3-L17)]

C#aby bylo možné získat hodnotu, musí být místní proměnná *jednoznačně přiřazena* . Například pokud deklarace předchozí `i` nezahrnuje počáteční hodnotu, kompilátor by nahlásil chybu pro následné použití `i` , protože `i` by se v těchto bodech v programu nedala jednoznačně přiřadit.

Metoda může použít `return` příkazy pro vrácení řízení volajícímu. V metodách, `void`které `return` vracejí, příkazy nemohou určovat výraz. V metodě, která vrací typ non- `return` void, musí příkazy zahrnovat výraz, který vypočítá vrácenou hodnotu.

### <a name="static-and-instance-methods"></a>Statické a instanční metody

Metoda deklarovaná pomocí statického modifikátoru je *statická metoda*. Statická metoda nepracuje na konkrétní instanci a může přímo přistupovat ke statickým členům.

Metoda deklarovaná bez statického modifikátoru je *Metoda instance*. Metoda instance pracuje na konkrétní instanci a může přistupovat ke statickým i instancím členů. Instance, na které byla vyvolána metoda instance, může být explicitně k dispozici jako `this`. V případě, že se odkazuje na `this` statickou metodu, se jedná o chybu.

Následující `Entity` třída má členy statických i instancí.

[!code-csharp[Entity](~/samples/snippets/csharp/tour/classes-and-objects/Entity.cs#L16-L36)]

Každá `Entity` instance obsahuje sériové číslo (a předpokládá se, že některé další informace nejsou zde uvedeny). `Entity` Konstruktor (který je jako metoda instance) Inicializuje novou instanci s dalším dostupným sériovým číslem. Vzhledem k tomu, že je konstruktor členem instance, je povolen přístup `serialNo` k poli instance i k `nextSerialNo` statickému poli.

Statické metody `SetNextSerialNo`amůžou přistupovat ke `serialNo` statickému poli, ale při přímém přístupu k poli instance by to byla chyba. `nextSerialNo` `GetNextSerialNo`

Následující příklad ukazuje použití třídy entity.

[!code-csharp[EntityExample](~/samples/snippets/csharp/tour/classes-and-objects/Entity.cs#L3-L15)]

Všimněte si, `SetNextSerialNo` že `GetNextSerialNo` statické metody a jsou vyvolány `GetSerialNo` ve třídě, zatímco metoda instance je vyvolána na instancích třídy.

### <a name="virtual-override-and-abstract-methods"></a>Virtuální, přepisování a abstraktní metody

Pokud deklarace metody instance obsahuje `virtual` modifikátor, metoda je označována jako *virtuální metoda*. Pokud není k dispozici žádný modifikátor Virtual, metoda je označována jako *nevirtuální metoda*.

Když je vyvolána virtuální metoda, je *typ běhu* instance, pro kterou probíhá vyvolání, určuje vlastní implementaci metody, která má být vyvolána. V nevirtuálním volání metody je *Typ doby kompilace* instance určujícím faktorem.

Virtuální metoda může být přepsána v odvozené třídě. Pokud deklarace metody instance obsahuje modifikátor přepsání, metoda přepíše zděděnou virtuální metodu se stejnou signaturou. Zatímco deklarace virtuální metody zavádí novou metodu, deklarace metody přepsání specializuje existující zděděnou virtuální metodu tím, že poskytuje novou implementaci této metody.

*Abstraktní metoda* je virtuální metoda bez implementace. Abstraktní metoda je deklarována s modifikátorem abstract a je povolena pouze ve třídě, která je také deklarována jako abstraktní. Abstraktní metoda musí být přepsána v každé neabstraktní odvozené třídě.

Následující příklad deklaruje abstraktní `Expression`třídu,, která představuje uzel stromu výrazu, a tři odvozené třídy, `Constant`, `VariableReference`, a `Operation`, které implementují uzly stromu výrazů pro konstanty, proměnnou odkazy a aritmetické operace. (To je podobné, ale nelze je zaměňovat s typy stromu výrazů).

[!code-csharp[ExpressionClass](~/samples/snippets/csharp/tour/classes-and-objects/Expressions.cs#L3-L61)]

K modelování aritmetických výrazů lze použít předchozí čtyři třídy. Například pomocí instancí těchto tříd může být výraz `x + 3` reprezentován následujícím způsobem.

[!code-csharp[ExpressionExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L40-L43)]

Metoda instance je vyvolána pro vyhodnocení `double` daného výrazu a vytvoření hodnoty. `Expression` `Evaluate` Metoda přebírá `Dictionary` argument, který obsahuje názvy proměnných (jako klíče záznamů) a hodnoty (jako hodnoty položek). Protože `Evaluate` je abstraktní metoda, neabstraktní třídy odvozené z `Expression` musí být přepsány `Evaluate`.

`Constant` Implementacejednoduševrátí`Evaluate` uloženou konstantu. Implementace `VariableReference`objektu vyhledá název proměnné ve slovníku a vrátí výslednou hodnotu. Implementace nejprve vyhodnotí levý a pravý operand (rekurzivním `Evaluate` voláním metod) a poté provede danou aritmetickou operaci. `Operation`

Následující program používá `Expression` třídy pro vyhodnocení výrazu `x * (y + 2)` pro různé hodnoty `x` a `y`.

[!code-csharp[ExpressionUsage](~/samples/snippets/csharp/tour/classes-and-objects/Expressions.cs#L66-L89)]

### <a name="method-overloading"></a>Přetížení metody

*Přetížení* metody umožňuje, aby více metod ve stejné třídě měl stejný název, pokud mají jedinečné podpisy. Při kompilování volání přetížené metody kompilátor používá *řešení přetížení* k určení konkrétní metody, která má být vyvolána. Řešení přetížení najde jednu metodu, která nejlépe odpovídá argumentům, nebo hlásí chybu, pokud nelze najít žádnou nejlepší shodu. Následující příklad ukazuje rozlišení přetížení v platnosti. Komentář pro každé vyvolání v `UsageExample` metodě ukazuje, která metoda je skutečně vyvolána.

[!code-csharp[OverloadUsage](~/samples/snippets/csharp/tour/classes-and-objects/Overloading.cs#L3-L41)]

Jak je znázorněno v příkladu, konkrétní metodu lze vždy vybrat explicitním přetypováním argumentů na přesné typy parametrů a/nebo explicitním zadáním argumentů typu.

## <a name="other-function-members"></a>Další členové funkcí

Členy, které obsahují spustitelný kód, jsou souhrnně označovány jako *Členové funkce* třídy. Předchozí část popisuje metody, které jsou hlavním typem členů funkce. Tato část popisuje další typy členů funkce, které C#podporuje: konstruktory, vlastnosti, indexery, události, operátory a finalizační metody.

Následující příklad ukazuje obecnou třídu nazvanou `MyList<T>`, která implementuje zvětšený seznam objektů. Třída obsahuje několik příkladů nejběžnějších druhů členů funkce.

> [!NOTE]
> Tento příklad vytvoří `MyList` třídu, která není stejná jako standard <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.NET. Ilustruje koncepty potřebné pro tuto prohlídku, ale není náhradou za tuto třídu.

[!code-csharp[ListClass](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L4-L89)]

### <a name="constructors"></a>Konstruktory

C#podporuje jak instance, tak statické konstruktory. *Konstruktor instance* je člen, který implementuje akce vyžadované pro inicializaci instance třídy. *Statický konstruktor* je člen, který implementuje akce vyžadované k inicializaci samotné třídy při prvním načtení.

Konstruktor je deklarovaný jako metoda bez návratového typu a stejný název jako obsahující třída. Pokud deklarace konstruktoru obsahuje statický modifikátor, deklaruje statický konstruktor. V opačném případě deklaruje konstruktor instance.

Konstruktory instancí můžou být přetížené a můžou mít volitelné parametry. Například `MyList<T>` třída deklaruje jeden konstruktor instance s jedním volitelným `int` parametrem. Konstruktory instancí jsou vyvolány `new` pomocí operátoru. Následující příkazy přidělují dvě `MyList<string>` instance pomocí konstruktoru `MyList` třídy s nepovinným argumentem a bez něj.

[!code-csharp[ListExample1](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L95-L96)]

Na rozdíl od jiných členů nejsou konstruktory instancí zděděny a třída nemá žádné konstruktory instancí jiné než ty, které jsou ve třídě skutečně deklarovány. Pokud pro třídu není zadán konstruktor instance, bude automaticky zadáno prázdné číslo bez parametrů.

### <a name="properties"></a>Vlastnosti

*Vlastnosti* jsou přirozené rozšíření polí. Oba se nazývají členové s přidruženými typy a syntaxe pro přístup k polím a vlastnostem je stejná. Na rozdíl od polí ale vlastnosti neoznačují umístění úložiště. Místo toho mají vlastnosti *přistupující objekty* , které určují příkazy, které mají být provedeny, když jsou jejich hodnoty čteny nebo zapsány.

Vlastnost je deklarována jako pole s tím rozdílem, že deklarace končí pomocí přístupového objektu Get nebo pomocí přístupového objektu sady zapsaného mezi `{` oddělovači a `}` místo konci středníku. Vlastnost, která má přistupující objekt get i přístupový objekt set, je *vlastnost pro čtení i zápis*, vlastnost, která má pouze přistupující objekt get, je *vlastnost jen pro čtení*a vlastnost, která má pouze přístupový objekt set, je *vlastnost pouze pro zápis*.

Přístupový objekt get odpovídá metodě bez parametrů s návratovou hodnotou typu vlastnosti. S výjimkou cíle přiřazení, při odkazování na vlastnost ve výrazu, je vyvolána přístupová metoda get vlastnosti pro výpočet hodnoty vlastnosti.

Přístupový objekt set odpovídá metodě s jedním parametrem s názvem Value a bez návratového typu. Když se na vlastnost odkazuje jako na cíl přiřazení nebo jako operand + + nebo--, přistupující objekt set je vyvolán s argumentem, který poskytuje novou hodnotu.

Třída deklaruje dvě vlastnosti `Count` `Capacity`, které jsou jen pro čtení a pro čtení i zápis, v uvedeném pořadí. `MyList<T>` Následuje příklad použití těchto vlastností:

[!code-csharp[ListExample2](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L101-L104)]

Podobně jako pole a metody C# podporuje vlastnosti instance i statické vlastnosti. Statické vlastnosti jsou deklarovány se statickým modifikátorem a vlastnosti instance jsou deklarovány bez ní.

Přístupové objekty vlastnosti mohou být virtuální. Pokud deklarace vlastnosti obsahuje `virtual`modifikátor, `abstract`nebo `override` , vztahuje se na přístupový objekt (y) vlastnosti.

### <a name="indexers"></a>Indexery

*Indexer* je člen, který umožňuje, aby objekty byly indexovány stejným způsobem jako pole. Indexer je deklarován jako vlastnost s tím rozdílem, že název člena je `this` následován seznamem parametrů napsaným mezi `[` oddělovači a `]`. Parametry jsou k dispozici v přistupujícím objektu indexeru. Podobně jako u vlastností mohou být indexery pro čtení i zápis, jen pro čtení a přístup k nástroji indexeru, které mohou být virtuální.

Třída deklaruje jeden indexer pro čtení a zápis, který `int` přebírá parametr. `MyList<T>` Indexer umožňuje indexovat `MyList<T>` instance s `int` hodnotami. Příklad:

[!code-csharp[ListExample3](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L109-L117)]

Indexery mohou být přetíženy, což znamená, že třída může deklarovat více indexerů za předpokladu, že počet nebo typy jejich parametrů se liší.

### <a name="events"></a>Události

*Událost* je člen, který umožňuje třídě nebo objektu poskytovat oznámení. Událost je deklarována jako pole s tím rozdílem, že deklarace zahrnuje klíčové slovo události a typ musí být delegát typu.

V rámci třídy, která deklaruje člena události, se událost chová stejně jako pole typu delegáta (za předpokladu, že událost není abstraktní a nedeklaruje přistupující objekty). Pole ukládá odkaz na delegáta, který představuje obslužné rutiny událostí, které byly přidány do události. Pokud nejsou k dispozici žádné obslužné rutiny událostí `null`, pole je.

Třída deklaruje jeden člen události s názvem `Changed`, který indikuje, že do seznamu byla přidána nová položka. `MyList<T>` Změněná událost je vyvolána `OnChanged` virtuální metodou, která nejprve kontroluje, zda je `null` událost (to znamená, že nejsou přítomny žádné obslužné rutiny). Pojem vyvolání události je přesně shodný s voláním delegáta reprezentovaného událostí, takže neexistují žádné speciální jazykové konstrukce pro vyvolání událostí.

Klienti reagují na události prostřednictvím *obslužných rutin událostí*. Obslužné rutiny událostí jsou připojeny `+=` pomocí operátoru a odebrány `-=` pomocí operátoru. Následující příklad připojí obslužnou rutinu události k `Changed` události. `MyList<string>`

[!code-csharp[EventExample](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L132-L148)]

Pro pokročilé scénáře, kde je požadováno řízení základního úložiště události, může deklarace události explicitně poskytnout `add` a `remove` přistupující objekty, které `set` jsou poněkud podobné přístupovému objektu vlastnosti.

### <a name="operators"></a>Operátory

*Operátor* je člen, který definuje význam použití konkrétního operátoru výrazu na instance třídy. Lze definovat tři typy operátorů: unární operátory, binární operátory a operátory převodu. Všechny operátory musí být deklarovány `public` jako `static`a.

Třída deklaruje dva operátory `operator ==` `MyList` , a, a poskytuje tak nový význam pro výrazy, které tyto operátory aplikují na instance. `operator !=` `MyList<T>` Konkrétně operátory definují rovnost dvou `MyList<T>` instancí jako porovnávání každého z obsažených objektů pomocí jejich stejných metod. Následující příklad používá `==` operátor k porovnání dvou `MyList<int>` instancí.

[!code-csharp[OperatorExample](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L121-L129)]

První `Console.WriteLine` výstupy `True` , protože dva seznamy obsahují stejný počet objektů se stejnými hodnotami ve stejném pořadí. `a` `MyList<int>` Nebyl definován `operator ==`, `False` první `Console.WriteLine` by měl výstup, protože a`b` odkazují na různé instance. `MyList<T>`

### <a name="finalizers"></a>Finalizační metody

*Finalizační metoda* je člen, který implementuje akce vyžadované k finalizaci instance třídy. Finalizační metody nemohou mít parametry, nemohou mít modifikátory dostupnosti a nelze je volat explicitně. Finalizační metoda pro instanci je vyvolána automaticky během uvolňování paměti.

Uvolňování paměti je povolená rozsáhlá Zeměpisná šířka při rozhodování o shromažďování objektů a spouštění finalizační metody. Konkrétně časování volání finalizační metody není deterministické a v jakémkoli vlákně mohou být provedeny finalizační metody. Z těchto a dalších důvodů by třídy měly implementovat finalizační metody pouze v případě, že žádná jiná řešení nejsou proveditelná.

`using` Příkaz poskytuje lepší přístup k zničení objektu.

> [!div class="step-by-step"]
> [Předchozí](statements.md)Další
> [](structs.md)
