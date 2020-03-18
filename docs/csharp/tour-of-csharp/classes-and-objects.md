---
title: Třídy a objekty v jazyce C# – prohlídka jazyka C#
description: Začínáte s C#? Přečtěte si tento přehled tříd, objektů a dědičnosti
ms.date: 02/27/2020
ms.assetid: 63a89bde-0f05-4bc4-b0cd-4f693854f0cd
ms.openlocfilehash: c178e11b5667905f75538555c8a309e2fdb4a9ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159179"
---
# <a name="classes-and-objects"></a>Třídy a objekty

*Třídy* jsou nejzákladnější c#'s typy. Třída je datová struktura, která kombinuje stav (pole) a akce (metody a další členy funkce) v jedné jednotce. Třída poskytuje definici dynamicky vytvořených *instancí třídy,* označované také jako *objekty*. Třídy podporují *dědičnost* a *polymorfismus*, mechanismy, kterými *odvozené třídy* mohou rozšířit a specializovat *základní třídy*.

Nové třídy jsou vytvářeny pomocí deklarací tříd. Deklarace třídy začíná hlavičkou, která určuje atributy a modifikátory třídy, název třídy, základní třídu (pokud je zadána) a rozhraní implementovaná třídou. Záhlaví následuje tělo třídy, které se skládá ze seznamu deklarací členů `{` napsaných mezi oddělovači a `}`.

Následující kód ukazuje deklaraci jednoduché `Point`třídy s názvem :

[!code-csharp[PointClass](~/samples/snippets/csharp/tour/classes-and-objects/Point.cs#L3-L11)]

Instance tříd jsou vytvořeny `new` pomocí operátoru, který přiděluje paměť pro novou instanci, vyvolá konstruktor pro inicializaci instance a vrátí odkaz na instanci. Následující příkazy vytvářejí dva pointové objekty a ukládají odkazy na tyto objekty ve dvou proměnných:

[!code-csharp[PointExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L9-L10)]

Paměť obsazená objektem je automaticky vyvolána, když objekt již není dostupný. Není nutné ani možné explicitně navrátit objekty v c#.

## <a name="members"></a>Členové

Členy třídy jsou statické členy nebo členy instance. Statické členy patří do tříd a členové instance patří k objektům (instance tříd).

Následující seznam obsahuje přehled druhů členů, které může třída obsahovat.

- Konstanty
  - Konstantní hodnoty přidružené ke třídě
- Fields (Pole)
  - Proměnné třídy
- Metody
  - Výpočty a akce, které mohou být provedeny třídou
- Vlastnosti
  - Akce spojené se čtením a zápisem pojmenovaných vlastností třídy
- Indexery
  - Akce přidružené k indexování instancí třídy, jako je pole
- Akce
  - Oznámení, která mohou být generována třídou
- Operátory
  - Převody a operátory výrazů podporované třídou
- Konstruktory
  - Akce potřebné k inicializaci instancí třídy nebo samotné třídy
- Finalizační metody
  - Akce, které je třeba provést před instancemi třídy, jsou trvale zahozeny
- Typy
  - Vnořené typy deklarované třídou

## <a name="accessibility"></a>Přístupnost

Každý člen třídy má přidruženou usnadnění přístupu, která řídí oblasti textu programu, který má přístup k členu. Existuje šest možných forem přístupnosti. Modifikátory přístupu jsou shrnuty níže.

- `public`
  - Přístup není omezen.
- `protected`
  - Přístup je omezen na tuto třídu nebo třídy odvozené z této třídy.
- `internal`
  - Přístup je omezen na aktuální sestavení (.exe, .dll a tak dále.).
- `protected internal`
  - Přístup je omezen na obsahující třídy, třídy odvozené z obsahující třídy nebo třídy v rámci stejného sestavení.
- `private`
  - Přístup je omezen na tuto třídu.
- `private protected`
  - Přístup je omezen na obsahující třídy nebo třídy odvozené z obsahující typ v rámci stejného sestavení.

## <a name="type-parameters"></a>Parametry typu

Definice třídy může určit sadu parametrů typu podle názvu třídy s úhlovými závorkami, které ohraničují seznam názvů parametrů typu. Parametry typu pak lze použít v těle deklarace třídy k definování členů třídy. V následujícím příkladu jsou `Pair` `TFirst` parametry `TSecond`typu a :

[!code-csharp[Pair](~/samples/snippets/csharp/tour/classes-and-objects/Pair.cs#L3-L7)]

Typ třídy, který je deklarován pro převzetí parametrů typu, se nazývá *obecný typ třídy*. Struct, rozhraní a delegát typy mohou být také obecné.
Při použití obecné třídy musí být pro každý parametr typu uvedeny argumenty typu:

[!code-csharp[PairExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L15-L17)]

Obecný typ s argumenty typu, `Pair<int,string>` jako je výše, se nazývá *konstruovaný typ*.

## <a name="base-classes"></a>Základní třídy

Deklarace třídy může určit základní třídu podle parametrů názvu třídy a typu s dvojtečkou a názvem základní třídy. Vynechání specifikace základní třídy je stejné jako odvození od typu `object`. V následujícím `Point3D` příkladu je základní `Point`třída je a `Point` `object`základní třída je :

[!code-csharp[Point3DClass](~/samples/snippets/csharp/tour/classes-and-objects/Point.cs#L3-L20)]

Třída zdědí členy své základní třídy. Dědičnost znamená, že třída implicitně obsahuje všechny členy své základní třídy, s výjimkou instance a statických konstruktorů a finalizačních metod základní třídy. Odvozená třída může přidat nové členy k těm členům, které dědí, ale nemůže odebrat definici zděděného člena. `Point3D` V předchozím příkladu dědí pole `x` a `y` z `Point`, a každá `Point3D` instance obsahuje tři pole , `x` `y`a `z`.

Implicitní převod existuje z typu třídy na některý z jeho typů základních tříd. Proměnná typu třídy může odkazovat na instanci této třídy nebo na instanci libovolné odvozené třídy. Například vzhledem k předchozí deklaraci třídy může proměnná typu `Point` odkazovat buď na a `Point` nebo a `Point3D`:

[!code-csharp[Point3DExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L22-L23)]

## <a name="fields"></a>Fields (Pole)

*Pole* je proměnná, která je přidružena ke třídě nebo k instanci třídy.

Pole deklarované statickým modifikátorem definuje statické pole. Statické pole identifikuje přesně jedno umístění úložiště. Bez ohledu na to, kolik instancí třídy jsou vytvořeny, je tam jen jedna kopie staticképole.

Pole deklarované bez statického modifikátoru definuje pole instance. Každá instance třídy obsahuje samostatnou kopii všech polí instance této třídy.

V následujícím příkladu má `Color` každá instance třídy `r`samostatnou kopii polí `g`, a `b` instance, `Black`ale `White` `Red`existuje `Green`pouze `Blue` jedna kopie statických polí , , a statická:

[!code-csharp[ColorClass](~/samples/snippets/csharp/tour/classes-and-objects/Color.cs#L3-L17)]

Jak je znázorněno v předchozím příkladu, pole `readonly` jen pro *čtení* mohou být deklarována pomocí modifikátoru. Přiřazení k `readonly` poli může nastat pouze jako součást deklarace pole nebo v konstruktoru ve stejné třídě.

## <a name="methods"></a>Metody

*Metoda* je člen, který implementuje výpočtu nebo akce, které mohou být provedeny objektem nebo třídou. *Statické metody* jsou přístupné prostřednictvím třídy. *Metody instance* jsou přístupné prostřednictvím instancí třídy.

Metody mohou mít seznam *parametrů*, které představují hodnoty nebo odkazy na proměnné předané metodě, a *návratový typ*, který určuje typ hodnoty vypočítané a vrácené metodou. Návratový typ metody `void` je, pokud nevrátí hodnotu.

Stejně jako typy, metody mohou mít také sadu parametrů typu, pro které musí být zadány argumenty typu při volání metody. Na rozdíl od typů mohou být argumenty typu často odvozeny z argumentů volání metody a nemusí být explicitně zadány.

*Podpis* metody musí být jedinečný ve třídě, ve které je metoda deklarována. Podpis metody se skládá z názvu metody, počtu parametrů typu a čísla, modifikátorů a typů jejích parametrů. Podpis metody neobsahuje návratový typ.

### <a name="parameters"></a>Parametry

Parametry se používají k předávání hodnot nebo proměnných odkazů na metody. Parametry metody získat jejich skutečné hodnoty z *argumentů,* které jsou určeny při vyvolání metody. Existují čtyři druhy parametrů: parametry hodnoty, referenční parametry, výstupní parametry a pole parametrů.

*Parametr hodnoty* se používá pro předávání vstupních argumentů. Parametr hodnoty odpovídá místní proměnné, která získá jeho počáteční hodnotu z argumentu, který byl předán pro parametr. Změny parametru hodnoty nemají vliv na argument, který byl předán pro parametr.

Parametry hodnoty mohou být volitelné zadáním výchozí hodnoty, aby bylo možné vynechat odpovídající argumenty.

*Referenční parametr* se používá pro předávání argumentů odkazem. Argument předaný pro referenční parametr musí být proměnná s určitou hodnotou a během provádění metody představuje referenční parametr stejné umístění úložiště jako proměnná argumentu. Referenční parametr je deklarován pomocí modifikátoru. `ref` Následující příklad ukazuje použití `ref` parametrů.

[!code-csharp[swapExample](~/samples/snippets/csharp/tour/classes-and-objects/RefExample.cs#L3-L18)]

*Výstupní parametr* se používá pro předávání argumentů odkazem. Je podobný referenční parametr, s tím rozdílem, že nevyžaduje, že explicitně přiřadit hodnotu argument za předpokladu volajícího. Výstupní parametr je deklarován s modifikátorem. `out` Následující příklad ukazuje použití `out` parametrů pomocí syntaxe zavedené v C# 7.

[!code-csharp[OutExample](~/samples/snippets/csharp/tour/classes-and-objects/OutExample.cs#L3-L17)]

*Pole parametrů* umožňuje metodě předat proměnný počet argumentů. Pole parametrů je deklarováno pomocí modifikátoru. `params` Pouze poslední parametr metody může být pole parametrů a typ pole parametrů musí být jednorozměrný typ pole. Write a WriteLine metody <xref:System.Console?displayProperty=nameWithType> třídy jsou dobrým příkladem použití pole parametru. Jsou deklarovány následovně.

[!code-csharp[ConsoleExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L78-L83)]

V rámci metody, která používá pole parametrů, se pole parametrů chová přesně jako běžný parametr typu pole. Však při vyvolání metody s polem parametrů je možné předat buď jeden argument typu pole parametru nebo libovolný počet argumentů typu prvku pole parametru. V druhém případě je instance pole automaticky vytvořena a inicializována s danými argumenty. Tento příklad

[!code-csharp[StringFormat](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L55-L55)]

je ekvivalentní k napsání následujícího.

[!code-csharp[StringFormat2](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L30-L35)]

### <a name="method-body-and-local-variables"></a>Tělo metody a místní proměnné

Tělo metody určuje příkazy, které mají být provedeny při vyvolání metody.

Tělo metody může deklarovat proměnné, které jsou specifické pro vyvolání metody. Tyto proměnné se nazývají *místní proměnné*. Deklarace místní proměnné určuje název typu, název proměnné a případně počáteční hodnotu. Následující příklad deklaruje místní proměnnou `i` s počáteční `j` hodnotou nula a místní proměnnou bez počáteční hodnoty.

[!code-csharp[Squares](~/samples/snippets/csharp/tour/classes-and-objects/Squares.cs#L3-L17)]

C# vyžaduje, aby byla místní proměnná *určitě přiřazena* před získáním její hodnoty. Například pokud deklarace předchozí `i` neobsahuje počáteční hodnotu, kompilátor by hlásit chybu pro `i` `i` následné použití, protože by nebyl a definitivně přiřazen v těchto bodech v programu.

Metoda můžete `return` použít příkazy vrátit řízení jeho volajícího. Při vracení metody `void` `return` nelze příkazy zadat výraz. V metodě vrácení nevoid, `return` příkazy musí obsahovat výraz, který vypočítá vrácenou hodnotu.

### <a name="static-and-instance-methods"></a>Statické metody a metody instance

Metoda deklarovaná statickým modifikátorem je *statická metoda*. Statická metoda nefunguje na konkrétní instanci a může přistupovat pouze přímo ke statickým členům.

Metoda deklarovaná bez statického modifikátoru je *metoda instance*. Metoda instance pracuje na konkrétní instanci a může přistupovat k statickým i instančním členům. Instance, na které byla vyvolána metoda instance `this`lze explicitně přistupovat jako . Je to chyba odkazovat `this` se na ve statické metodě.

Následující `Entity` třída má statické členy a členy instance.

[!code-csharp[Entity](~/samples/snippets/csharp/tour/classes-and-objects/Entity.cs#L16-L36)]

Každá `Entity` instance obsahuje sériové číslo (a pravděpodobně některé další informace, které zde nejsou zobrazeny). Konstruktor `Entity` (který je jako metoda instance) inicializuje novou instanci s dalším dostupným sériovým číslem. Vzhledem k tomu, že konstruktor je členem instance, je povoleno přístup k poli `serialNo` instance i statickému `nextSerialNo` poli.

A `GetNextSerialNo` `SetNextSerialNo` statické metody mohou `nextSerialNo` přistupovat ke statickému poli, ale bylo `serialNo` by chybou pro ně přímý přístup k poli instance.

Následující příklad ukazuje použití entity třídy.

[!code-csharp[EntityExample](~/samples/snippets/csharp/tour/classes-and-objects/Entity.cs#L3-L15)]

A `SetNextSerialNo` `GetNextSerialNo` statické metody jsou vyvolány na `GetSerialNo` třídu vzhledem k tomu, že metoda instance je vyvolána na instance třídy.

### <a name="virtual-override-and-abstract-methods"></a>Virtuální, přepsání a abstraktní metody

Pokud deklarace metody `virtual` instance obsahuje modifikátor, metoda se říká, že je *virtuální metoda*. Pokud není k dispozici žádný virtuální modifikátor, metoda se říká, že je *nevirtuální metoda*.

Při vyvolání virtuální metody *typ run-time* instance, pro které dojde k vyvolání, určuje implementaci skutečné metody, kterou chcete vyvolat. V vyvolání nevirtuální metody je určujícím faktorem typ instance v *době kompilace.*

Virtuální metoda může být *přepsána* v odvozené třídě. Pokud deklarace metody instance obsahuje modifikátor přepsání, metoda přepíše zděděnou virtuální metodu se stejným podpisem. Vzhledem k tomu, že deklarace virtuální metody zavádí novou metodu, deklarace metody přepsání se specializuje na existující zděděnou virtuální metodu tím, že poskytuje novou implementaci této metody.

*Abstraktní metoda* je virtuální metoda bez implementace. Abstraktní metoda je deklarována s abstraktnímodifikátor a je povoleno pouze ve třídě, která je také deklarována abstraktní. Abstraktní metoda musí být přepsána v každé neabstraktní odvozené třídě.

Následující příklad deklaruje `Expression`abstraktní třídu , která představuje uzel stromu výrazu, a tři odvozené třídy `Constant`, , `VariableReference`a `Operation`, které implementují uzly stromu výrazů pro konstanty, odkazy na proměnné a aritmetické operace. (Tento příklad je podobný, ale nesmí být zaměňována s typy stromu výrazu).

[!code-csharp[ExpressionClass](~/samples/snippets/csharp/tour/classes-and-objects/Expressions.cs#L3-L61)]

Předchozí čtyři třídy lze modelovat aritmetické výrazy. Například pomocí instancí těchto tříd `x + 3` výraz může být reprezentován následujícím způsobem.

[!code-csharp[ExpressionExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L40-L43)]

Metoda `Evaluate` `Expression` instance je vyvolána k vyhodnocení daného výrazu `double` a vytvoření hodnoty. Metoda přebírá `Dictionary` argument, který obsahuje názvy proměnných (jako klíče položek) a hodnoty (jako hodnoty položek). Protože `Evaluate` je abstraktní metoda, neabstraktní třídy odvozené z `Expression` musí přepsat . `Evaluate`

Implementace `Constant`'s `Evaluate` jednoduše vrátí uloženou konstantu. Implementace `VariableReference`společnosti vyhledá název proměnné ve slovníku a vrátí výslednou hodnotu. Implementace `Operation`'s nejprve vyhodnotí levé a pravé operandy (rekurzivně vyvoláníjejich `Evaluate` metod) a poté provede danou aritmetické operace.

Následující program používá `Expression` třídy k `x * (y + 2)` vyhodnocení výrazu pro různé hodnoty `x` a `y`.

[!code-csharp[ExpressionUsage](~/samples/snippets/csharp/tour/classes-and-objects/Expressions.cs#L66-L89)]

### <a name="method-overloading"></a>Přetížení metody

*Přetížení* metody umožňuje více metod ve stejné třídě mít stejný název tak dlouho, dokud mají jedinečné podpisy. Při kompilaci vyvolání přetížené metody kompilátor používá *řešení přetížení* k určení konkrétní metody vyvolat. Řešení přetížení najde jednu metodu, která nejlépe odpovídá argumenty nebo hlásí chybu, pokud nelze nalézt jednu nejlepší shodu. Následující příklad ukazuje rozlišení přetížení ve skutečnosti. Komentář pro každé vyvolání `UsageExample` v metodě ukazuje, která metoda je vyvolána.

[!code-csharp[OverloadUsage](~/samples/snippets/csharp/tour/classes-and-objects/Overloading.cs#L3-L41)]

Jak ukazuje příklad, určitou metodu lze vždy vybrat explicitním převedením argumentů na přesné typy parametrů a/nebo explicitně zadávající argumenty typu.

## <a name="other-function-members"></a>Ostatní členové funkce

Členové, které obsahují spustitelný kód jsou souhrnně označovány jako *členy funkce* třídy. Předchozí část popisuje metody, které jsou primární typy členů funkce. Tato část popisuje další druhy členů funkce podporovaných C#: konstruktory, vlastnosti, indexery, události, operátory a finalizační metody.

Následující příklad ukazuje obecnou `MyList<T>`třídu s názvem , která implementuje početný seznam objektů. Třída obsahuje několik příkladů nejběžnějších druhů členů funkce.

> [!NOTE]
> Tento příklad `MyList` vytvoří třídu, která není stejná <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>jako standard .NET . Ilustruje koncepty potřebné pro toto turné, ale není náhradou za tuto třídu.

[!code-csharp[ListClass](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L4-L89)]

### <a name="constructors"></a>Konstruktory

C# podporuje instance a statické konstruktory. Konstruktor *instance* je člen, který implementuje akce potřebné k inicializaci instance třídy. *Statický konstruktor* je člen, který implementuje akce potřebné k inicializaci samotné třídy při prvním načtení.

Konstruktor je deklarován jako metoda bez návratového typu a se stejným názvem jako obsahující třída. Pokud deklarace konstruktoru obsahuje statický modifikátor, deklaruje statický konstruktor. V opačném případě deklaruje konstruktor instance.

Instance konstruktory mohou být přetížené a může mít volitelné parametry. Například třída `MyList<T>` deklaruje jeden konstruktor `int` instance s jedním volitelným parametrem. Instance konstruktory jsou vyvolány pomocí operátoru. `new` Následující příkazy `MyList<string>` přidělit dvě instance pomocí `MyList` konstruktoru třídy s a bez volitelné argument.

[!code-csharp[ListExample1](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L95-L96)]

Na rozdíl od jiných členů nejsou zděděny konstruktory instancí a třída nemá žádné instance konstruktory jiné než tyto konstruktory skutečně deklarované ve třídě. Pokud pro třídu není zadán žádný konstruktor instance, bude automaticky poskytnut prázdný bez parametrů.

### <a name="properties"></a>Vlastnosti

*Vlastnosti* jsou přirozeným rozšířením polí. Oba jsou pojmenovány členy s přidruženými typy a syntaxe pro přístup k polím a vlastnostem je stejná. Na rozdíl od polí však vlastnosti neoznačují umístění úložiště. Místo toho vlastnosti mají *přístupové objekty,* které určují příkazy, které mají být provedeny při čtení nebo zápisu jejich hodnoty.

Vlastnost je deklarována jako pole, s tím rozdílem, že deklarace končí get `{` `}` přistupující ho a/nebo set přistupující ho mezi oddělovači a místo konce středníkem. Vlastnost, která má přístupový objekt get a set přistupující objekt je *vlastnost pro čtení a zápis*, vlastnost, která má pouze get přistupující objekt je vlastnost jen pro *čtení*a vlastnost, která má pouze set přistupující objekt je vlastnost jen *pro zápis*.

Přístupový objekt get odpovídá metodě parameterless s návratovou hodnotou typu vlastnosti. S výjimkou jako cíl přiřazení, když je odkazováno vlastnost ve výrazu, get přistupující objekt vlastnosti je vyvolána k výpočtu hodnoty vlastnosti.

Přístupový objekt set odpovídá metodě s jedním parametrem s názvem value a bez návratového typu. Když je vlastnost odkazována jako cíl přiřazení nebo jako operand ++ nebo --, je vyvolán a argumentem, který poskytuje novou hodnotu.

Třída `MyList<T>` deklaruje `Count` `Capacity`dvě vlastnosti a , které jsou jen pro čtení a pro čtení, v uvedeném pořadí. Následující kód je příkladem použití těchto vlastností:

[!code-csharp[ListExample2](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L101-L104)]

Podobně jako pole a metody, C# podporuje vlastnosti instance a statické vlastnosti. Statické vlastnosti jsou deklarovány pomocí statického modifikátoru a vlastnosti instance jsou deklarovány bez něj.

Přistupující objekt (y) vlastnostmůže být virtuální. Pokud deklarace vlastnosti obsahuje `virtual`modifikátor , `abstract`nebo, `override` vztahuje se na přistupující objektvlastnosti.

### <a name="indexers"></a>Indexery

*Indexer* je člen, který umožňuje objekty, které mají být indexovány stejným způsobem jako pole. Indexer je deklarován jako vlastnost s `this` tím rozdílem, že za `[` názvem `]`člena následuje seznam parametrů napsaný mezi oddělovači a . Parametry jsou k dispozici v přístupovéobjekty indexeru. Podobně jako vlastnosti indexery mohou být jen pro čtení, jen pro čtení a jen pro zápis a přistupující objekty indexeru mohou být virtuální.

Třída `MyList<T>` deklaruje jeden indexer pro `int` čtení a zápis, který přebírá parametr. Indexer umožňuje indexovat `MyList<T>` instance s `int` hodnotami. Například:

[!code-csharp[ListExample3](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L109-L117)]

Indexery mohou být přetížené, což znamená, že třída může deklarovat více indexerů tak dlouho, dokud se liší počet nebo typy jejich parametrů.

### <a name="events"></a>Akce

*Událost* je člen, který umožňuje třídy nebo objektu poskytovat oznámení. Událost je deklarována jako pole s tím rozdílem, že deklarace obsahuje klíčové slovo události a typ musí být typ delegáta.

V rámci třídy, která deklaruje člen události, se událost chová stejně jako pole typu delegáta (za předpokladu, že událost není abstraktní a nedeklaruje přistupující objekty). Pole ukládá odkaz na delegáta, který představuje obslužné rutiny události, které byly přidány do události. Pokud nejsou k dispozici žádné obslužné rutiny událostí, pole je `null`.

Třída `MyList<T>` deklaruje jeden `Changed`člen události s názvem , což znamená, že do seznamu byla přidána nová položka. Changed Událost je vyvolána `OnChanged` virtuální metodou, která nejprve zkontroluje, zda je `null` událost (což znamená, že žádné obslužné rutiny jsou k dispozici). Pojem vyvolání události je přesně ekvivalentní vyvolání delegáta reprezentovaného událostí – proto neexistují žádné speciální jazykové konstrukce pro vyvolání událostí.

Klienti reagují na události prostřednictvím *obslužných rutin událostí*. Obslužné rutiny `+=` událostí jsou `-=` připojeny pomocí operátoru a odebrány pomocí operátoru. Následující příklad připojí obslužnou rutinu `Changed` události k události . `MyList<string>`

[!code-csharp[EventExample](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L132-L148)]

Pro pokročilé scénáře, kde je požadováno řízení základního úložiště události, deklarace události může explicitně poskytnout `add` a `remove` přistupující objekty, které jsou podobné `set` přistupujícího objektu vlastnosti.

### <a name="operators"></a>Operátory

*Operátor* je člen, který definuje význam použití určitého operátoru výrazu na instance třídy. Lze definovat tři druhy operátorů: unární operátory, binární operátory a operátory převodu. Všechny hospodářské subjekty `public` `static`musí být deklarovány jako a .

Třída `MyList<T>` deklaruje `operator ==` `operator !=`dva operátory a , a proto dává `MyList` nový význam výrazy, které používají tyto operátory instance. Konkrétně operátory definovat rovnost `MyList<T>` dvou instancí jako porovnání každé obsažené objekty pomocí jejich Equals metody. Následující příklad používá `==` operátor k `MyList<int>` porovnání dvou instancí.

[!code-csharp[OperatorExample](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L121-L129)]

První `Console.WriteLine` výstupy, `True` protože dva seznamy obsahují stejný počet objektů se stejnými hodnotami ve stejném pořadí. Pokud `MyList<T>` není `operator ==`definována `Console.WriteLine` , `False` první `a` `b` by `MyList<int>` výstup, protože a odkazovat na různé instance.

### <a name="finalizers"></a>Finalizační metody

*Finalizační metoda* je člen, který implementuje akce potřebné k dokončení instance třídy. Finalizační metody nemohou mít parametry, nemohou mít modifikátory usnadnění a nelze je explicitně vyvolat. Finalizační metoda pro instanci je vyvolána automaticky během uvolňování paměti.

Uvolňování paměti je povoleno široké šířky při rozhodování o tom, kdy shromažďovat objekty a spustit finalizační metody. Konkrétně načasování involací finalizační metody není deterministické a finalizační metody mohou být provedeny v libovolném vlákně. Z těchto a dalších důvodů by třídy měly implementovat finalizační metody pouze v případě, že nejsou proveditelná žádná jiná řešení.

Příkaz `using` poskytuje lepší přístup k zničení objektu.

> [!div class="step-by-step"]
> [Předchozí](statements.md)
> [další](arrays.md)
