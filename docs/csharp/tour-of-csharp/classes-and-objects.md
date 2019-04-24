---
title: Třídy a objekty v C# – připravuje C# jazyka
description: Teprve se C#? Přečtěte si tento přehled tříd, objektů a dědičnost
ms.date: 08/10/2016
ms.assetid: 63a89bde-0f05-4bc4-b0cd-4f693854f0cd
ms.openlocfilehash: 36def74888f67dfa216cea7c093d80724e452c7b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59976401"
---
# <a name="classes-and-objects"></a>Třídy a objekty

*Třídy* jsou nejdůležitější z C#na typy. Třída je datová struktura, která kombinuje stavů (pole) a akcí (metody a další funkce členů) v jediné jednotce. Třída obsahuje definici pro dynamicky vytvořené *instance* třídy, označované také jako *objekty*. Třídy podpory *dědičnosti* a *polymorfismus*, mechanismy kterým *odvozené třídy* můžete rozšířit a specialize *základních tříd*.

Nové třídy jsou vytvořené pomocí deklarace tříd. Deklarace třídy začíná hlavičku, která určuje atributy a modifikátory třídy, název třídy, základní třídy (Pokud je zadaný) a rozhraní implementované třídy. Záhlaví je následována tělo třídy, které se skládá ze seznamu deklarací členů napsané mezi oddělovači `{` a `}`.

Následuje deklaraci jednoduchou třídu pojmenovanou `Point`:

[!code-csharp[PointClass](~/samples/snippets/csharp/tour/classes-and-objects/Point.cs#L3-L11)]

Jsou vytvořeny pomocí instance třídy `new` operátor, který přiděluje paměť pro novou instanci, vyvolá konstruktor k inicializaci instance a vrátí odkaz na instanci. Následující příkazy vytvořit dva objekty bod a uložit odkazy na tyto objekty do dvou proměnných:

[!code-csharp[PointExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L9-L10)]

Paměti obsazena objekt je automaticky uvolněn, když objekt už není dostupný. To není nezbytné ani možné explicitně uvolnit objekty v jazyce C#.

## <a name="members"></a>Členové

Členy třídy jsou statické členy nebo členy instance. Statické členy patří do třídy a členy instance patřit k objektům (instance třídy).

Následující body nabízí přehled o druhy členů, které mohou obsahovat třídu.

* Konstanty
  - Konstantní hodnoty, které jsou přidružené k třídě
* Pole
  - Proměnné třídy
* Metody
  - Výpočtů a akcí, které lze provést pomocí třídy
* Vlastnosti
  - Akce přidružené k čtení a zápis s názvem vlastnosti třídy
* Indexery
  - Akce přidružené k indexování instancí třídy jako pole
* Události
  - Oznámení, která mohou být generovány třídy
* Operátory
  - Převody a podporovaných třídou operátory výrazů
* Konstruktory
  - Akce potřebné k inicializaci instance třídy nebo vlastní třídy
* Finalizační metody
  - Akce k provedení před instancí třídy budou trvale odstraněny
* Typy
  - Vnořené typy deklarované pomocí třídy

## <a name="accessibility"></a>Usnadnění

Každý člen třídy má přidružené usnadnění přístupu, který řídí oblasti textem programu, které budou mít přístup k členu. Existuje šest možných formy usnadnění přístupu. Ty jsou shrnuté dole.

* `public`
  - Přístup mimo jiné
* `protected`
  - Přístup pouze pro tuto třídu nebo třídy odvozené z této třídy
* `internal`
  - Přístup pouze pro aktuální sestavení (.exe, .dll, atd.)
* `protected internal`
  - Přístup omezen na obsahující třídy, třídy odvozené od třídy obsahující nebo tříd v rámci stejného sestavení
* `private`
  - Přístup pouze pro tuto třídu
* `private protected`
  - Přístup omezen na obsahující třídu nebo třídy odvozené z nadřazeného typu v rámci stejného sestavení

## <a name="type-parameters"></a>Parametry typu

Definice třídy může určit sadu parametrů typu podle názvu třídy s ostré závorky uzavírající seznam názvy parametrů typů. Parametry typu pak lze v těle deklarace třídy definují členy třídy. V následujícím příkladu, parametry typu `Pair` jsou `TFirst` a `TSecond`:

[!code-csharp[Pair](~/samples/snippets/csharp/tour/classes-and-objects/Pair.cs#L3-L7)]

Typ třídy, který je deklarován mít parametry typu se nazývá *typu obecné třídy*. Typy struktury, rozhraní a delegátů mohou být obecný.
Při použití obecné třídy musí být uvedeny argumentů typu pro jednotlivé parametry typu:

[!code-csharp[PairExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L15-L17)]

Obecný typ s argumenty typů, které jsou k dispozici, jako je třeba `Pair<int,string>` výše, je volána *konstruovaný typ.*.

## <a name="base-classes"></a>Základní třídy

Deklarace třídy může určovat základní třídu pomocí následujících parametrů názvem a typem třídy pomocí dvojtečku a název základní třídy. Vynechání specifikace základní třídy je stejný jako odvozený od typu `object`. V následujícím příkladu základní třída `Point3D` je `Point`a základní třídu `Point` je `object`:

[!code-csharp[Point3DClass](~/samples/snippets/csharp/tour/classes-and-objects/Point.cs#L3-L20)]

Třída dědí členy své základní třídy. Dědičnost znamená, že třídy implicitně obsahuje všechny členy své základní třídy, s výjimkou instance a statické konstruktory a finalizační metody základní třídy. Odvozené třídy můžete přidat nové členy pro ty, které se dědí, ale nemůže odstranit definici zděděného člena. V předchozím příkladu `Point3D` dědí `x` a `y` pole z `Point`a každý `Point3D` instance obsahuje tři pole `x`, `y`, a `z`.

Implicitní převod existuje z typu třídy pro některé typy jejího základní třídy. Proměnné typu třídy. proto odkazovat instance této třídy nebo instance všechny odvozené třídy. Například dány předchozí deklarace třídy, proměnné typu `Point` odkazovat buď `Point` nebo `Point3D`:

[!code-csharp[Point3DExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L22-L23)]

## <a name="fields"></a>Pole

A *pole* je proměnná, která souvisí s třídou nebo s instancí třídy.

Pole deklarované pomocí statických modifikátor definuje statické pole. Statické pole identifikuje přesně jednoho umístění úložiště. Bez ohledu na to, kolik instancí třídy jsou vytvořeny je někdy pouze jednu kopii tohoto statické pole.

Pole deklarované bez statickém modifikátoru definuje pole instance. Každá instance třídy obsahuje kopii všechna pole instancí této třídy.

V následujícím příkladu, každá instance `Color` třída má samostatnou kopii `r`, `g`, a `b` instance pole, ale existuje pouze jedna kopie `Black`, `White`, `Red`, `Green`, a `Blue` statická pole:

[!code-csharp[ColorClass](~/samples/snippets/csharp/tour/classes-and-objects/Color.cs#L3-L17)]

Jak je znázorněno v předchozím příkladu *pole jen pro čtení* mohou být deklarovány s `readonly` modifikátor. Přiřazení `readonly` pole se můžou vyskytnout jenom jako součást deklarace pole nebo v konstruktoru ve stejné třídě.

## <a name="methods"></a>Metody

A *metoda* je člen, který implementuje výpočtu nebo akce, která může provádět k objektu nebo třídě. *Statické metody* jsou přístupné prostřednictvím třídy. *Instance metody* jsou přístupné prostřednictvím instance třídy.

Metody mohou mít seznam *parametry*, které představují hodnoty nebo odkazy na proměnné předaný metodě a *návratový typ*, která určuje typ hodnoty vypočítané a vrácen touto metodou. Návratový typ metody je `void` Pokud nevrací hodnotu.

Podobně jako typy metody mají také sadu parametrů typu, pro které musí být zadán argumenty typu při volání metody. Na rozdíl od typů argumenty typu často jde odvodit z argumentů volání metody a nemusí být explicitně uvedena.

*Podpis* metody musí být jedinečný ve třídě, ve kterém je deklarována metodu. Podpis metody se skládá z názvu metody, počet parametrů typu a číslo, modifikátory a typy ze svých parametrů. Podpis metody neobsahuje návratovým typem.

### <a name="parameters"></a>Parametry

Parametry se používají k předávání hodnot nebo proměnné odkazy na metody. Parametry metody získávají skutečné hodnoty z *argumenty* , které jsou určeny při vyvolání metody. Existují čtyři druhy parametry: hodnoty, parametry, parametry odkazů, výstupní parametry a pole parametrů.

A *parametr hodnoty* slouží k předání vstupních argumentů. Hodnota parametru odpovídá místní proměnná, která se získá z argumentu, který byl předán parametr počáteční hodnoty. Úpravy parametru hodnoty nemají vliv na argument, který byl předán parametr.

Parametry s hodnotou může být volitelný, a zadat výchozí hodnotu tak, aby odpovídající argumenty lze vynechat.

A *odkazovat na parametr* slouží k předávání argumentů podle odkazu. Argument předaný pro referenční parametr musí být proměnná s určitou hodnotou a při provádění metody referenční parametr představuje stejné úložiště jako argument proměnné. Parametr odkazu je deklarována s `ref` modifikátor. Následující příklad ukazuje použití `ref` parametry.

[!code-csharp[swapExample](~/samples/snippets/csharp/tour/classes-and-objects/RefExample.cs#L3-L18)]

*Výstupní parametr* slouží k předávání argumentů podle odkazu. Je podobný parametr odkazu, s tím rozdílem, že se nevyžaduje, aby explicitně přiřadit hodnotu argumentu zadaný volajícího. Výstupní parametr je deklarována s `out` modifikátor. Následující příklad ukazuje použití `out` parametry s využitím syntaxe zavedený C# 7.

[!code-csharp[OutExample](~/samples/snippets/csharp/tour/classes-and-objects/OutExample.cs#L3-L17)]

A *pole parametrů* povoluje proměnlivý počet argumentů, které mají být předána metodě. Pole parametrů je deklarována s `params` modifikátor. Poslední parametr metody může být pole parametrů a typ pole parametrů musí být typu jednorozměrné pole. Zápis a WriteLine metod <xref:System.Console?displayProperty=nameWithType> třídy jsou dobrým příkladem použití pole parametrů. Jsou deklarovány následujícím způsobem.

[!code-csharp[ConsoleExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L78-L83)]

Pole parametrů se v rámci metody, která používá pole parametrů, chová stejně jako regulární parametr typu pole. Ve volání metody s polem parametrů, je možné předat buď jeden argument typu pole parametru nebo libovolný počet argumentů typu prvku pole parametrů. V druhém případě pole instance je automaticky vytvořen a inicializován pomocí dané argumenty. V tomto příkladu

[!code-csharp[StringFormat](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L55-L55)]

je ekvivalentní zápisu následující.

[!code-csharp[StringFormat2](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L30-L35)]

### <a name="method-body-and-local-variables"></a>Tělo metody a lokální proměnné

Tělo metody určuje příkazy ke spuštění při vyvolání metody.

Tělo metody můžete deklarovat proměnné, které jsou specifické pro vyvolání metody. Tyto proměnné jsou volány *lokální proměnné*. Místní deklarace proměnné Určuje název typu, název proměnné a případně na počáteční hodnotu. Následující příklad deklaruje místní proměnnou `i` s počáteční hodnotou nula a místní proměnnou `j` s žádná počáteční hodnota.

[!code-csharp[Squares](~/samples/snippets/csharp/tour/classes-and-objects/Squares.cs#L3-L17)]

C# vyžaduje místní proměnnou *jednoznačně přiřazena* před její hodnotu lze získat. Například pokud deklarace předchozí `i` počáteční hodnotu neobsahuje, kompilátor by oznámit chybu pro následné použití `i` protože `i` nemusí být jednoznačně přiřazena v těchto bodech v programu.

Můžete použít metodu `return` příkazy vrátí řízení volajícímu. Do metody vracející `void`, `return` příkazy nemohou zadat výraz. Do metody vracející typ jiný než void `return` příkazů musí obsahovat výraz, který vypočítá návratovou hodnotu.

### <a name="static-and-instance-methods"></a>Statické a instance metody

Metody deklarované pomocí statických modifikátoru je *statickou metodu*. Statická metoda nefunguje na konkrétní instanci a pouze přímý přístup k statické členy.

Metody deklarované bez je statický modifikátor *metodu instance*. Metodu instance funguje na konkrétní instanci, můžete přístup ke statické a členy instance. Instance, ve kterém byla vyvolána metoda instance je explicitně přístupná jako `this`. Jedná se o chybu k odkazování na `this` uvnitř statické metody.

Následující `Entity` má statické třídy a členy instance.

[!code-csharp[Entity](~/samples/snippets/csharp/tour/classes-and-objects/Entity.cs#L16-L36)]

Každý `Entity` instance obsahuje sériové číslo (a pravděpodobně některé další informace, které tady není ukázaný). `Entity` Konstruktoru (což je jako metoda instance) inicializuje novou instanci s další dostupné sériové číslo. Protože konstruktor je členem instance, je povoleno přístup i `serialNo` pole instance a `nextSerialNo` statické pole.

`GetNextSerialNo` a `SetNextSerialNo` statické metody se dostanete `nextSerialNo` statické pole, ale bude k chybě pro ně umožňuje přímý přístup k `serialNo` pole instance.

Následující příklad ukazuje použití třídy Entity.

[!code-csharp[EntityExample](~/samples/snippets/csharp/tour/classes-and-objects/Entity.cs#L3-L15)]

Všimněte si, že `SetNextSerialNo` a `GetNextSerialNo` statické metody jsou vyvolány ve třídě, kdežto `GetSerialNo` metodu instance se vyvolá u instance třídy.

### <a name="virtual-override-and-abstract-methods"></a>Virtual, override a abstraktní metody

Při deklaraci instance metody obsahuje `virtual` modifikátor, metoda se říká, že *virtuální metoda*. Pokud je k dispozici žádné virtuální modifikátor, metoda se říká, že *nevirtuální metoda*.

Při vyvolání virtuální metody, *run-time typu* instance, pro který přebírá tento vyvolání místo určuje implementaci skutečné metoda k vyvolání. Ve volání nevirtuální metody *typu v době kompilace* instance je určujícím faktorem.

Virtuální metoda může být *přepsat* v odvozené třídě. Při deklaraci instanci metody zahrnuje modifikátor override, přepíše metodu zděděnou virtuální metodu se stejným podpisem. Vzhledem k tomu virtuální metoda deklarace zavádí nové metody, specializuje deklaraci metody přepsání existující zděděnou virtuální metodu tím, že poskytuje novou implementaci této metody.

*Abstraktní metoda* virtuální metoda bez implementace. Abstraktní metoda je deklarována s modifikátorem abstract a smí obsahovat pouze ve třídě, která je také deklarovaná jako abstraktní. Abstraktní metody musí být přepsána v každé třídě odvozené neabstraktní.

Následující příklad deklaruje abstraktní třídu, `Expression`, který představuje uzel stromu výrazu a tři odvozené třídy, `Constant`, `VariableReference`, a `Operation`, které implementují uzly stromu výrazů konstant, proměnných Reference a aritmetické operace. (To je podobné, ale ne by se zaměňovat s typy stromu výrazů).

[!code-csharp[ExpressionClass](~/samples/snippets/csharp/tour/classes-and-objects/Expressions.cs#L3-L61)]

Předchozí čtyři třídy lze použít k modelování aritmetických výrazech. Například použití instance těchto tříd, výraz `x + 3` můžou být vyjádřeny následujícím způsobem.

[!code-csharp[ExpressionExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L40-L43)]

`Evaluate` Metodu `Expression` instance se vyvolá, aby vyhodnotit tento výraz a vytvářet `double` hodnotu. Tato metoda přebírá `Dictionary` argument, který obsahuje názvy proměnných (jako klíče položky) a hodnoty (jako hodnoty položek). Protože `Evaluate` je abstraktní metody, jako neabstraktní třídy odvozené od `Expression` musí přepsat `Evaluate`.

A `Constant`vaší implementace `Evaluate` jednoduše vrací uložené – konstanta. A `VariableReference`vaší implementace vyhledá název proměnné ve slovníku a vrátí výslednou hodnotu. `Operation`Na provádění nejprve vyhodnotí jako operandy vlevo a vpravo (vyvoláním rekurzivně jejich `Evaluate` metody) a potom provede daný aritmetické operace.

Následující program používá `Expression` třídy pro vyhodnocení výrazu `x * (y + 2)` pro různé hodnoty `x` a `y`.

[!code-csharp[ExpressionUsage](~/samples/snippets/csharp/tour/classes-and-objects/Expressions.cs#L66-L89)]

### <a name="method-overloading"></a>Přetěžování metody

Metoda *přetížení* povoluje více metod ve stejné třídě, aby mají stejný název tak dlouho, dokud mají jedinečný podpis. Při kompilaci vyvolání přetěžované metody, kterou kompilátor používá *rozlišení přetěžování* určit konkrétní metodu chce volat. Řešení přetížení vyhledá jednu metodu, nejlépe odpovídá argumenty nebo hlásí chybu, pokud lze najít žádné jediné nejlepší shodu. Následující příklad ukazuje přetížení v platnosti. Komentář pro každé vyvolání v `UsageExample` metoda ukazuje, jakou metodu ve skutečnosti je vyvolána.

[!code-csharp[OverloadUsage](~/samples/snippets/csharp/tour/classes-and-objects/Overloading.cs#L3-L41)]

Jak je znázorněno v příkladu, konkrétní metody lze vybrat vždy explicitně použití argumentů na typy parametrů přesný nebo explicitně zadávání argumentů typu.

## <a name="other-function-members"></a>Ostatní členové – funkce

Členy, které obsahují spustitelného kódu jsou souhrnně označovány jako *funkce členy* třídy. Předchozí část popisuje metody, které jsou primární druh členy funkce. Tato část popisuje jiné druhy členů funkce nepodporuje C#: konstruktory, vlastnosti, indexery, události, operátory a finalizační metody.

Následující příklad zobrazuje obecný třídu s názvem `MyList<T>`, který implementuje growable seznam objektů. Třída obsahuje několik příkladů nejběžnější druhy členů funkce.

> [!NOTE]
> Tento příklad vytvoří `MyList` třídy, který není stejný jako .NET standard <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>. Ukazuje koncepty jsou potřeba u této ukázky, ale není to náhrada pro danou třídu.

[!code-csharp[ListClass](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L4-L89)]

### <a name="constructors"></a>Konstruktory

C# podporuje instance a statické konstruktory. *Konstruktor instance* je člen, který implementuje akce potřebné k inicializaci instance třídy. A *statický konstruktor* je člen, který implementuje akce potřebné k inicializaci třídy samotný při prvním načtení.

Konstruktor je deklarován jako metoda bez návratového typu a stejný název jako třídu obsahující. Pokud deklarace konstruktoru obsahuje statický modifikátor, deklaruje statický konstruktor. V opačném případě deklaruje konstruktor instance.

Konstruktory instancí můžou být přetížené a může obsahovat volitelné parametry. Například `MyList<T>` třída deklaruje dva konstruktory instancí, jednu s žádné parametry a ten, který přebírá `int` parametru. Konstruktory instancí jsou vyvolány pomocí `new` operátor. Následující příkazy přidělit dvě `MyList<string>` instance pomocí konstruktoru `MyList` třídy a nemusíte nepovinný argument.

[!code-csharp[ListExample1](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L95-L96)]

Na rozdíl od jiných členů nejsou zděděné konstruktory instancí a třída nemá žádné konstruktory instance než tyto skutečně deklarovaná ve třídě. Pokud žádný konstruktor instance není zadána pro třídu, pak prázdná bez parametrů je automaticky zadáno.

### <a name="properties"></a>Vlastnosti

*Vlastnosti* jsou přirozené rozšíření polí. Jsou pojmenované členy s přidružené typy a syntaxe pro přístup k vlastnosti a pole je stejná. Na rozdíl od pole, ale vlastnosti nejsou označení umístění úložiště. Místo toho mají vlastnosti *přistupující objekty* , které určují příkazy ke se spustí při jejich hodnoty jsou číst nebo zapisovat.

Vlastnost je deklarován jako pole, s tím rozdílem, že deklarace končí přistupující objekt get a/nebo přístupový objekt set napsané mezi oddělovači `{` a `}` místo končí středníkem. Vlastnost, která má přistupující objekt get a přístupového objektu set je *čtení a zápis vlastnosti*, je vlastnost, která má pouze přístupový objekt get *vlastnost jen pro čtení*, a vlastnost, která má pouze přístupový objekt set je *vlastnost jen pro zápis*.

Přístupový objekt get odpovídající konstruktor bez parametrů metody s návratovou hodnotou typu vlastnosti. S výjimkou jako cílem přiřazení, když vlastnost se odkazuje ve výrazu, přístupový objekt get vlastnosti je vyvolána k výpočtu hodnoty vlastnosti.

Přístupový objekt set odpovídající metodu s jedním parametrem s názvem hodnotu a bez návratového typu. Když je jako cíl přiřazení nebo jako operand odkazuje vlastnost ++ a--, přístupový objekt set je volána s argumentem, který obsahuje novou hodnotu.

`MyList<T>` Třída deklaruje dvě vlastnosti `Count` a `Capacity`, které jsou v uvedeném pořadí jen pro čtení a čtení i zápis. Následuje příklad použití těchto vlastností:

[!code-csharp[ListExample2](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L101-L104)]

Podobně jako k polím a metodám, C# podporuje vlastnosti instance a statické vlastnosti. Statické vlastnosti jsou deklarovány s modifikátorem statické a vlastnosti instance jsou deklarovány bez něj.

Accessor(s) vlastnost může být virtuální. Pokud obsahuje deklaraci vlastnosti `virtual`, `abstract`, nebo `override` modifikátor, se vztahuje na accessor(s) vlastnost.

### <a name="indexers"></a>Indexery

*Indexer* je člen, který umožňuje objekty, které mají být indexovány v stejným způsobem jako pole. Indexer je deklarován jako vlastnost, s tím rozdílem, že název člena je to za nímž následuje seznam parametrů napsané mezi oddělovači `[` a `]`. Parametry jsou k dispozici v accessor(s) indexeru. Podobně jako u vlastnosti, indexery mohou být pro čtení i zápis, jen pro čtení a jen pro zápis a accessor(s) indexer může být virtuální.

`MyList<T>` Třída deklaruje jednu indexeru pro čtení i zápis, která přebírá `int` parametru. Indexer umožňuje index `MyList<T>` instance s `int` hodnoty. Příklad:

[!code-csharp[ListExample3](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L109-L117)]

Indexery mohou být přetíženy, což znamená, že třídy lze deklarovat několik indexerů jako číslo nebo typů jejich parametrů se liší.

### <a name="events"></a>Události

*Události* je člen, který umožňuje třídu nebo objektu pro sdělení. Událost je deklarován jako pole, s tím rozdílem, že event – klíčové slovo obsahuje prohlášení a typ musí být typu delegáta.

V rámci třídy, které deklaruje člen události události se chová stejně jako pole s typem delegáta (za předpokladu, události není abstraktní a nedeklaruje přistupující objekty). Toto pole obsahuje odkaz na delegáta, který představuje obslužné rutiny událostí, které byly přidány k této události. Pokud jsou k dispozici žádné obslužné rutiny událostí, je pole `null`.

`MyList<T>` Třída deklaruje člen jedna událost s názvem `Changed`, což znamená, že se do seznamu přidá nová položka. Vyvolá událost změněné `OnChanged` virtuální metody, které nejprve zkontroluje, zda je událost `null` (to znamená, že jsou k dispozici žádné obslužné rutiny). Pojem vyvolání události je přesně ekvivalentní k vyvolání delegáta představované událostí – to znamená, nejsou žádné zvláštní jazykovým konstrukcím pro vyvolání události.

Klienti reagovat na události prostřednictvím *obslužné rutiny událostí*. Obslužné rutiny událostí se připojují pomocí `+=` operátor a odebrané pomocí `-=` operátor. Následující příklad připojí obslužnou rutinu události pro `Changed` události `MyList<string>`.

[!code-csharp[EventExample](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L132-L148)]

Pro pokročilé scénáře, kde je žádoucí ovládací prvek pro použité úložiště událostí, můžete explicitně uvést deklaraci události `add` a `remove` přístupové objekty, které jsou poněkud podobně jako `set` přistupujícího objektu vlastnosti.

### <a name="operators"></a>Operátory

*Operátor* je člen, který definuje význam použití operátoru konkrétní výraz do instance třídy. Je možné definovat tři typy operátorů: unární operátory, binární operátory a operátory převodu. Všechny operátory musí být deklarována jako `public` a `static`.

`MyList<T>` Třída deklaruje dva operátory `operator ==` a `operator !=`a proto poskytuje nový význam pro výrazy, které se vztahují na tyto operátory `MyList` instancí. Konkrétně definovat operátory rovnosti dvou `MyList<T>` instance vyjádřený jako porovnání všech obsažených objektů pomocí jejich metod Equals. V následujícím příkladu `==` operátor pro porovnání dvou `MyList<int>` instancí.

[!code-csharp[OperatorExample](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L121-L129)]

První `Console.WriteLine` výstupy `True` vzhledem k tomu, že oba seznamy obsahují stejný počet objektů se stejnými hodnotami ve stejném pořadí. Měl `MyList<T>` není definována `operator ==`, první `Console.WriteLine` by mít výstup `False` protože `a` a `b` odkaz na jiný `MyList<int>` instancí.

### <a name="finalizers"></a>Finalizační metody

A *finalizační metodu* je člen, který implementuje akce potřebné k dokončení instance třídy. Finalizační metody nemohou mít parametry nemohou mít modifikátory a nemůže být volány explicitně. Finalizační metoda instance je automaticky vyvolána při uvolnění.

Uvolňování paměti je povolená široké šířky při rozhodování, kdy se mají shromáždit objekty a spuštění finalizační metody. Konkrétně není deterministický. časování volání finalizační metody a finalizační metody mohou být provedeny v libovolném vlákně. Pro tyto a další důvody třídy by měly implementovat finalizační metody pouze v případě, že žádná jiná řešení jsou vhodná.

`using` Příkaz poskytuje lepší přístup ke zničení objektu.

> [!div class="step-by-step"]
> [Předchozí](statements.md)
> [další](structs.md)
