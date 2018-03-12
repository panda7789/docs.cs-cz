---
title: "Třídy a objekty v jazyce C# – přehled používání jazyka C#"
description: "Nové jazyka C#? Přečtěte si tento přehled tříd, objekty a dědičnost"
keywords: "Rozhraní .NET, csharp, třídu, instance, objekt, dědičnosti, polymorfismus"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 63a89bde-0f05-4bc4-b0cd-4f693854f0cd
ms.openlocfilehash: 97559a6e7b24f4a61b49dd4f050747a6d0ccbda0
ms.sourcegitcommit: d95a91d685565f4d95c8773b558752864a6a3d7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2018
---
# <a name="classes-and-objects"></a>Třídy a objekty

*Třídy* jsou nejvíce základní typy C# na. Třída je datová struktura, která spojuje stavu (pole) a akce (metody a členy jiné funkce) v jediné jednotky. Třída obsahuje definici pro dynamicky vytvořený *instance* třídy, také známé jako *objekty*. Třídy podpory *dědičnosti* a *polymorfismus*, mechanismy které *odvozených třídách* můžete rozšířit a specialize *základní třídy*.

Nové třídy jsou vytvořeny pomocí deklarace tříd. Deklarace třídy začíná hlavičku, která určuje, atributy a třídy modifikátory, název třídy základní třídy (je-li zadána) a rozhraní implementované v třídě. Záhlaví následuje tělo třídy, které se skládá z seznam deklarace členů zapsána mezi oddělovače `{` a `}`.

Toto je prohlášení o jednoduché třídy s názvem `Point`:

[!code-csharp[PointClass](../../../samples/snippets/csharp/tour/classes-and-objects/Point.cs#L3-L11)]

Instance třídy jsou vytvořené pomocí `new` operátor, který se přidělí paměť pro novou instanci, volá konstruktor k inicializaci instance a vrátí odkaz na instanci. Následující příkazy vytvořte dva objekty bodu a ukládání odkazů na tyto objekty ve dvou proměnných:

[!code-csharp[PointExample](../../../samples/snippets/csharp/tour/classes-and-objects/Program.cs#L9-L10)]

Paměti obsazené objektem je automaticky uvolní, pokud je objekt už nebude dostupný. Je nutné ani možné explicitně navrácení objekty v jazyce C#.

## <a name="members"></a>Členové

Členy třídy jsou statické členy nebo členů instance. Statické členy patřit do třídy a instance členy patří k objektům (instance třídy).

Následující část obsahuje přehled různých druhů členů, které může obsahovat třídu.

* Konstanty
    - Konstantní hodnoty, které jsou přidružené k třídě
* Pole
    - Proměnné třídy
* Metody
    - Výpočty a akce, které lze provést pomocí třídy
* Vlastnosti
    - Akce přidružené k čtení a zápis s názvem vlastnosti třídy
* Indexery
    - Akce přidružené k indexování instancí třídy jako pole
* Události
    - Oznámení, která může být generována třídy
* Operátory
    - Převody a operátory výraz nepodporuje třídy
* Konstruktory
    - Akce potřebné k chybě při inicializaci instance třídy nebo vlastní třídy
* Finalizační metody
    - Akce, které je třeba provést před instancí třídy jsou trvale zahozeny.
* Typy
    - Vnořené typy deklarovaná třídy

## <a name="accessibility"></a>Usnadnění

Každý člen třídy má přidružené usnadnění přístupu, který řídí oblasti program textu, která mají mít přístup k členovi. Nejsou k dispozici pět možné formy usnadnění. Tyto jsou shrnuté níž.

* `public`
    - Přístup není omezené.
* `protected`
    - Přístup k omezené na této třídě nebo třídy odvozené z této třídy
* `internal`
    - Přístup omezený na aktuální sestavení (.exe, .dll atd.)
* `protected internal`
    - Přístup omezené na obsahující třídu nebo třídy odvozené od obsahující – třída
* `private`
    - Přístup k omezené na tato třída
* `private protected`
    - Přístup obsahující třídy a třídy nesmí být odvozen od typu obsahující v rámci stejného sestavení

## <a name="type-parameters"></a>Parametry typu

Definice třídy může určit sadu parametrů typu podle názvu třídy s lomené závorky uzavření do seznamu názvy parametrů typu. Parametry typu pak lze v těle deklarace tříd členy třídy definovat. V následujícím příkladu, parametry typu `Pair` jsou `TFirst` a `TSecond`:

[!code-csharp[Pair](../../../samples/snippets/csharp/tour/classes-and-objects/Pair.cs#L3-L7)]

Typ třídy, který je deklarovaný typ parametry nazývá *typu obecné třídy*. Typy struktura, rozhraní a delegáta může být také obecné.
Pokud se použije obecná třída, musí být uvedeny argumenty typu pro jednotlivé parametry typu:

[!code-csharp[PairExample](../../../samples/snippets/csharp/tour/classes-and-objects/Program.cs#L15-L17)]

Obecného typu s argumenty typu, jako je třeba zadat `Pair<int,string>` vyšších verzích se nazývá *sestavený typu*.

## <a name="base-classes"></a>Základní třídy

Deklarace třídy mohou zadejte základní třídu třída název a typ parametry s dvojtečkou a název základní třídy. Vynechání specifikaci základní třída je stejný jako odvozování z typu `object`. V následujícím příkladu, základní třídu `Point3D` je `Point`a základní třídu `Point` je `object`:

[!code-csharp[Point3DClass](../../../samples/snippets/csharp/tour/classes-and-objects/Point.cs#L3-L20)]

Třídy dědí členy základní třídy. Dědičnost znamená, že třídu implicitně obsahuje všechny členy její základní třída, s výjimkou instance a statických konstruktorů a finalizační metody třídy base. Odvozené třídy můžete přidat nové členy ty, které dědí, ale nemůže odstranit definici zděděného členu. V předchozím příkladu `Point3D` dědí `x` a `y` pole z `Point`a každou `Point3D` instance obsahuje tři pole `x`, `y`, a `z`.

Implicitní převod existuje z typu třídy pro všechny typy jejich základní třídy. Proto můžete proměnné typu třídy odkazovat instance této třídy nebo instance všechny odvozené třídy. Například uděleno předchozí deklarace tříd proměnné typu `Point` může odkazovat buď `Point` nebo `Point3D`:

[!code-csharp[Point3DExample](../../../samples/snippets/csharp/tour/classes-and-objects/Program.cs#L22-L23)]

## <a name="fields"></a>Pole

A *pole* je proměnná, která souvisí s třídy nebo instance třídy.

Pole deklarovat s statický modifikátor definuje statické pole. Statické pole identifikuje přesně jedno umístění úložiště. Bez ohledu na to, kolik instancí třídy vytváří je někdy pouze jedné kopie statické pole.

Pole deklarované bez statický modifikátor definuje poli instance. Každá instance třídy obsahuje kopii pole instance této třídy.

V následujícím příkladu, každá instance `Color` třída má samostatnou kopii `r`, `g`, a `b` instance pole, ale existuje pouze jedna kopie `Black`, `White`, `Red`, `Green`, a `Blue` statických polí:

[!code-csharp[ColorClass](../../../samples/snippets/csharp/tour/classes-and-objects/Color.cs#L3-L17)]

Jak je uvedeno v předchozím příkladu *pole jen pro čtení* může deklarovat s `readonly` modifikátor. Přiřazení `readonly` pole lze použít pouze v jako součást deklaraci pole nebo v konstruktoru ve stejné třídě.

## <a name="methods"></a>Metody

A *metoda* je člen, který implementuje výpočtu nebo akce, které lze provést pomocí objektu nebo třídy. *Statické metody* jsou přístupné prostřednictvím třídy. *Instance metody* jsou přístupné prostřednictvím instancí třídy.

Metody může mít seznam *parametry*, které představují hodnoty nebo odkazy na proměnné předaný metodě a *návratový typ*, která určuje typ hodnoty počítaný a vrácený metodou. Návratový typ metoda `void` Pokud nevrací hodnotu.

Podobně jako typy metody také obsahovat sadu parametrů typu, pro které argumenty typu se musí zadat při volání metody. Na rozdíl od typů argumenty typu lze odvodit často z argumentů volání metody a nemusí být explicitně uvedena.

*Podpis* metody musí být jedinečný v třídě, ve kterém je deklarovaná metodu. Podpis metody se skládá z název metody, počet parametrů typu a počtu, modifikátory a typy její parametry. Podpis metody nezahrnuje návratový typ.

### <a name="parameters"></a>Parametry

Parametry se používají k předávání hodnot nebo proměnné odkazy na metody. Parametry metody získat své skutečné hodnoty z *argumenty* které zadávají při vyvolání metody. Existují čtyři typy parametrů: hodnoty parametrů, odkaz na parametry, výstupní parametry a pole parametrů.

A *hodnota parametru* slouží k předávání vstupní argumenty. Hodnota parametru odpovídá místní proměnné, která se získá z argument, který byl předán pro parametr počáteční hodnoty. Úpravy na hodnotu parametr nemají vliv argument, který byl předán pro parametr. 

Parametry s hodnotou může být volitelné, zadáním výchozí hodnotu tak, aby odpovídající argumenty lze vynechat.

A *odkazovat parametr* se používá pro předání argumentů odkazem. Argument předaná pro parametr odkazu musí být proměnná s určitou hodnotu a během provádění metody parametr odkazu představuje stejné umístění úložiště jako proměnnou argument. Parametr odkazu je deklarovaný s `ref` modifikátor. Následující příklad ukazuje použití `ref` parametry.

[!code-csharp[swapExample](../../../samples/snippets/csharp/tour/classes-and-objects/RefExample.cs#L3-L18)]

*Výstupní parametr* se používá pro předání argumentů odkazem. Podobně jako parametr odkaz je s tím rozdílem, že není třeba explicitně přiřadit hodnotu na zadaný volající argument. Výstupní parametr je deklarovaný s `out` modifikátor. Následující příklad ukazuje použití `out` parametry s využitím syntaxe byla zavedená v C# 7.

[!code-csharp[OutExample](../../../samples/snippets/csharp/tour/classes-and-objects/OutExample.cs#L3-L17)]

A *parametr pole* umožňuje proměnný počet argumentů mají být předány metodu. Pole parametrů je deklarovaný s `params` modifikátor. Pouze poslední parametr metody může být pole parametrů a typ pole parametrů musí být typu jednorozměrná pole. Metody zápisu a WriteLine <xref:System.Console?displayProperty=nameWithType> třídy jsou dobrými příklady použití pole parametrů. Jsou deklarovány následujícím způsobem.

[!code-csharp[ConsoleExample](../../../samples/snippets/csharp/tour/classes-and-objects/Program.cs#L78-L83)]

V rámci metody, která používá pole parametrů pole parametrů se chová stejně jako regulární parametr pole typu. V k vyvolání metody se pole parametrů, je možné předat buď jeden argument parametr pole typu nebo libovolný počet argumentů typu element pole parametrů. V takovém případě je instance pole automaticky vytvořen a inicializován s danou argumenty. Tento příklad

[!code-csharp[StringFormat](../../../samples/snippets/csharp/tour/classes-and-objects/Program.cs#L55-L55)]

je ekvivalentní zápis následující.

[!code-csharp[StringFormat2](../../../samples/snippets/csharp/tour/classes-and-objects/Program.cs#L30-L35)]

### <a name="method-body-and-local-variables"></a>Metoda textu a lokální proměnné

Metoda textu určuje příkazy provést při vyvolání metody.

Metoda text můžou deklarovat proměnné, které jsou specifické pro volání metody. Tyto proměnné se nazývají *místní proměnné*. Místní deklarace proměnné Určuje název typu, název proměnné a pravděpodobně má počáteční hodnotu. Následující příklad uvádí, místní proměnné `i` má počáteční hodnotu nula a místní proměnné `j` bez počáteční hodnoty.

[!code-csharp[Squares](../../../samples/snippets/csharp/tour/classes-and-objects/Squares.cs#L3-L17)]

C# vyžaduje místní proměnné být *výborný přiřazené* před jeho hodnotu lze získat. Například pokud deklaraci předchozí `i` neobsahuje počáteční hodnotu, kompilátor zasílat zprávy o chybě pro následné použití `i` protože `i` nebude přiřazen výborný v těchto bodech v programu.

Můžete použít metodu `return` příkazy vrátit kontrolu jeho volajícího. V metodě vrácení `void`, `return` příkazy nelze zadat výraz. V metodě vrácení není void `return` příkazy musí obsahovat výraz, který vypočítá návratovou hodnotu.

### <a name="static-and-instance-methods"></a>Statické a instance metody

Je metoda deklarovat s statický modifikátor *statickou metodu*. Statickou metodu nefunguje na konkrétní instanci a můžete pouze přímý přístup k statické členy.

Metoda deklarované bez je statický modifikátor *metodu instance*. Metodu instance funguje na konkrétní instanci, můžete přístup jak statické a instance členy. Instance, na kterém byl vyvolán metodu instance explicitně přístupná jako `this`. Jedná se o chybu, který bude odkazovat na `this` v statickou metodu.

Následující `Entity` třída má statické a instanci členy.

[!code-csharp[Entity](../../../samples/snippets/csharp/tour/classes-and-objects/Entity.cs#L16-L36)]

Každý `Entity` instance obsahuje sériové číslo (a pravděpodobně z důvodu některé další informace, které není tady zobrazené). `Entity` – Konstruktor (což je jako metodu instance) inicializuje novou instanci s další dostupné sériové číslo. Protože konstruktoru instanci členu, ho povolený přístup i `serialNo` poli instance a `nextSerialNo` statické pole.

`GetNextSerialNo` a `SetNextSerialNo` přístup statických metod `nextSerialNo` statické pole, ale bude k chybě pro ně přímý přístup `serialNo` pole instance.

Následující příklad ukazuje použití třídy Entity.

[!code-csharp[EntityExample](../../../samples/snippets/csharp/tour/classes-and-objects/Entity.cs#L3-L15)]

Všimněte si, že `SetNextSerialNo` a `GetNextSerialNo` statické metody jsou vyvolány na třídu, zatímco `GetSerialNo` instance metoda je volána, instance této třídy.

### <a name="virtual-override-and-abstract-methods"></a>Virtuální, přepsání a abstraktní metody

Když metoda deklaraci instance obsahuje `virtual` modifikátor, metodu se říká, že *virtuální metoda*. Pokud je k dispozici žádná virtuální modifikátor, metoda se říká, že *nevirtuální metoda*.

Pokud virtuální metoda je volána, *běhového typu* instance, které tento volání trvá místní určuje implementace skutečné metoda k vyvolání. V metodě nevirtuální vyvolání *kompilaci typu* instance je určujícím faktorem.

Virtuální metoda může být *přepsat* v odvozené třídě. Pokud deklarace metoda instance zahrnuje modifikátor přepsání, přepíše metodu zděděnou virtuální metodu se stejným podpisem. Zatímco deklaraci virtuální metoda představuje nový způsob, deklarace přepsání metody tím, že poskytuje nové implementace této metody se specializuje existující zděděnou virtuální metodu.

*Abstraktní metody* je virtuální metoda s žádnou implementaci. Abstraktní metodu je deklarovaný s modifikátorem abstraktní a smí obsahovat pouze třídu, která je také deklarována jako abstraktní. Abstraktní metodu musí být přepsána nastaveními v každé Odvozené neabstraktní třídy.

Následující příklad deklaruje abstraktní třídu, `Expression`, který představuje uzel stromu výraz a tři odvozených tříd, `Constant`, `VariableReference`, a `Operation`, které implementují uzly stromu výraz pro konstanty, proměnné odkazy a aritmetické operace. (To je podobná, ale ne k termín nelze zaměňovat s typy výrazů stromu).

[!code-csharp[ExpressionClass](../../../samples/snippets/csharp/tour/classes-and-objects/Expressions.cs#L3-L61)]

Lze použít předchozí čtyři třídy pro modelování aritmetických výrazech. Například pomocí instancemi těchto tříd výraz `x + 3` může být reprezentován následujícím způsobem.

[!code-csharp[ExpressionExample](../../../samples/snippets/csharp/tour/classes-and-objects/Program.cs#L40-L43)]

`Evaluate` Metodu `Expression` instance je vyvolána k vyhodnocování daného výrazu a vytvořit `double` hodnotu. Tato metoda přebírá `Dictionary` argument, který obsahuje názvy proměnných (jako klíče položek) a hodnoty (jako hodnoty položek). Protože `Evaluate` je abstraktní metodu neabstraktní třídy odvozené od `Expression` musí přepsat `Evaluate`.

A `Constant`na implementaci `Evaluate` jednoduše vrátí uložené konstanta. A `VariableReference`je implementace vyhledává názvu proměnné ve slovníku a vrátí výslednou hodnotu. `Operation`Na implementaci nejprve vyhodnotí operandy vlevo a vpravo (vyvoláním rekurzivně jejich `Evaluate` metody) a potom provede daný aritmetické operace.

Tento program používá `Expression` třídy při vyhodnocování výrazu `x * (y + 2)` pro různé hodnoty `x` a `y`.

[!code-csharp[ExpressionUsage](../../../samples/snippets/csharp/tour/classes-and-objects/Expressions.cs#L66-L89)]

### <a name="method-overloading"></a>Přetěžování metody

Metoda *přetížení* umožňuje několika metod ve stejné třídě do mají stejný název, dokud mají jedinečné podpisy. Při kompilování k vyvolání přetížené metody, kompilátor použije *rozlišení přetěžování* určit konkrétní metody vyvolání. Řešení přetížení vyhledá jednu metodu, nejlépe odpovídá argumenty nebo nahlásí chybu, pokud lze nalézt žádné jeden nejlepší shodu. Následující příklad ukazuje rozlišení přetížení v platnosti. Komentář pro každé vyvolání v `Main` metoda ukazuje, jakou metodu je ve skutečnosti vyvolat.

[!code-csharp[OverloadUsage](../../../samples/snippets/csharp/tour/classes-and-objects/Overloading.cs#L3-L41)]

Jak ukazuje příklad, konkrétní metody lze vybrat vždy explicitně přetypování argumenty, které mají typy přesný parametrů nebo explicitně zadávání argumenty typu.

## <a name="other-function-members"></a>Jiní členové – funkce

Členové, které obsahují spustitelného kódu, které se souhrnně označují jako *funkce členy* třídy. Předchozí část popisuje postupy, které se primární druh funkce členy. Tato část popisuje typy členů funkce podporované v jazyce C#: konstruktory, vlastnosti, indexery, události, operátory a finalizační metody.

Následující příklad zobrazuje obecný třídu s názvem seznamu<T>, který implementuje growable seznam objektů. Třída obsahuje několik příkladů nejběžnější druhy funkce členů.

[!code-csharp[ListClass](../../../samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L4-L89)]

### <a name="constructors"></a>Konstruktory

C# podporuje instance a statických konstruktorů. *Konstruktoru instance* je člen, který implementuje akce potřebné k inicializaci instance třídy. A *statického konstruktoru* je člen, který implementuje akce potřebné k inicializaci třídy samotné při prvním načtení.

Konstruktor je deklarován jako metodu s žádný návratový typ a stejný název jako obsahující třídy. Pokud deklaraci konstruktor obsahuje statický modifikátor, deklaruje statického konstruktoru. Jinak deklaruje konstruktoru instance.

Konstruktory instancí mohou být přetíženy a můžou mít volitelné parametry. Například `List<T>` třída deklaruje dva konstruktory instancí, s žádné parametry a ten, který přebírá `int` parametr. Konstruktory instancí jsou vyvolány pomocí `new` operátor. Následující příkazy přidělit dvě `List<string>` instance pomocí konstruktoru `List` třídy a bez nepovinný argument.

[!code-csharp[ListExample1](../../../samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L95-L96)]

Na rozdíl od jiných členů nejsou zděděné konstruktory instancí a třída nemá žádné instance konstruktory než ty ve skutečnosti deklarované v třídě. Pokud je zadaný žádný konstruktor instance pro třídu, pak prázdnou bez parametrů je automaticky zadáno.

### <a name="properties"></a>Vlastnosti

*Vlastnosti* jsou přirozené rozšíření polí. Obě jsou pojmenované členy s přidružené typy a syntaxe pro přístup k pole a vlastnosti je stejný. Na rozdíl od pole, ale vlastnosti není označují umístění úložiště. Místo toho vlastnosti mají *přístupové objekty* , zadejte příkazy, které budou spuštěny při jejich hodnoty jsou číst nebo zapisovat.

Vlastnost je deklarován jako pole, s tím rozdílem, že deklaraci končí přistupující objekt get nebo přistupující objekt set zapsána mezi oddělovače `{` a `}` místo končící na středníkem. Je vlastnost, která má přistupující objekt get a přistupující objekt set *pro čtení a zápis vlastnost*, je vlastnost, která má pouze přistupující *vlastnost určenou jen pro čtení*, a vlastnost, která má pouze přistupujícím objektem set *vlastnost jen pro zápis*.

Přistupující objekt get odpovídá bez parametrů metody s hodnotou návratový typ vlastnosti. S výjimkou jako cíl přiřazení, při odkazování na vlastnost ve výrazu, přistupující objekt get vlastnosti je vyvolána k výpočtu hodnoty vlastnosti.

Přistupující objekt set odpovídá pomocí jediného parametru s názvem hodnota a žádný návratový typ metody. Když se vlastnost odkazuje jako cílem přiřazení nebo jako operand ++ a--, přistupující objekt set volána s argumentem, který poskytuje novou hodnotu.

`List<T>` Třída deklaruje dvě vlastnosti, počtu a kapacity, které jsou jen pro čtení a pro čtení a zápis, v uvedeném pořadí. Následuje příklad použití těchto vlastností.

[!code-csharp[ListExample2](../../../samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L101-L104)]

Podobně jako u pole a metody, C# podporuje vlastnosti instance i statické vlastnosti. Statické vlastnosti, které jsou deklarovány s statický modifikátor a vlastnosti instance jsou deklarované bez ní.

Accessor(s) vlastnosti může být virtuální. Pokud deklarace vlastnosti zahrnuje `virtual`, `abstract`, nebo `override` modifikátor, se vztahuje na accessor(s) vlastnosti.

### <a name="indexers"></a>Indexery

*Indexer* je člen, který umožňuje objekty indexovaných stejným způsobem jako pole. Indexer je deklarován jako vlastnost s tím rozdílem, že název člena je to následovaný seznamem parametr zapsána mezi oddělovače `[` a `]`. Parametry jsou k dispozici v accessor(s) indexeru. Podobně jako u vlastnosti, indexery může být pro čtení a zápis, jen pro čtení a jen pro zápis, a accessor(s) indexer může být virtuální.

`List` Třída deklaruje jednu indexeru pro čtení a zápis, který přebírá `int` parametr. Indexer umožňuje indexu `List` instance s `int` hodnoty. Příklad:

[!code-csharp[ListExample3](../../../samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L109-L117)]

Indexery mohou být přetíženy, což znamená, že třídu můžou deklarovat několik indexerů tak dlouho, dokud číslo nebo typy jejich parametrů se liší.

### <a name="events"></a>Události

*Událostí* je člen, který umožňuje třídu nebo objekt, který chcete poskytnout oznámení. Událost je deklarován jako pole s tím rozdílem, že deklarace obsahuje event – klíčové slovo a typ musí být typu delegáta.

V rámci třídy, který deklaruje člen události události se chová stejně jako pole typu delegáta (za předpokladu událost není abstraktní a nedeklaruje přístupových objektů). Pole ukládá odkaz na delegáta, který představuje obslužné rutiny událostí, které byly přidány k události. Pokud nejsou žádné obslužné rutiny událostí, je pole `null`.

`List<T>` Třída deklaruje jednu událost člena s názvem `Changed`, což naznačuje, že byl přidán do seznamu novou položku. Změněno událost vyvolána pomocí `OnChanged` virtuální metoda, která první zkontroluje, zda je událost `null` (což znamená, že jsou k dispozici žádné obslužné rutiny). Znalost problematicky vyvolání události přesněji odpovídá k vyvolání delegáta reprezentována událost – proto nejsou žádné zvláštní jazykové konstrukty pro vyvolávání událostí.

Klienti reagování na události prostřednictvím *obslužné rutiny událostí*. Obslužné rutiny událostí jsou připojené pomocí `+=` operátor a odebrané pomocí `-=` operátor. Následující příklad připojí obslužnou rutinu události a `Changed` události `List<string>`.

[!code-csharp[EventExample](../../../samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L132-L148)]

Pro pokročilé scénáře, kde je žádoucí ovládací prvek základní úložiště události, může být explicitně deklaraci události `add` a `remove` přístupové objekty, které jsou částečně podobá `set` přistupujícího objektu vlastnosti.

### <a name="operators"></a>Operátory

*Operátor* je člen, který určuje význam použití operátoru konkrétní výraz do instance třídy. Je možné definovat tři druhy operátory: unární operátory, binární operátory a operátory převodu. Všechny operátory musí být deklarována jako `public` a `static`.

`List<T>` Třída deklaruje dva operátory `operator ==` a `operator !=`a proto nabízí nové význam výrazy, které se vztahují tyto operátory `List` instance. Konkrétně definování operátory rovnosti dvou `List<T>` instance jako porovnávání všechny obsažené objekty pomocí své metody rovná se. Následující příklad používá `==` operátor k porovnání dvou `List<int>` instance.

[!code-csharp[OperatorExample](../../../samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L121-L129)]

První `Console.WriteLine` výstupy `True` vzhledem k tomu, že dva seznamy obsahovat stejný počet objektů se stejnými hodnotami ve stejném pořadí. Měl `List<T>` není definována `operator ==`, první `Console.WriteLine` by být výstupu `False` protože `a` a `b` odkaz na jiný `List<int>` instance.

### <a name="finalizers"></a>Finalizační metody

A *finalizační metodu* je člen, který implementuje akcí požadovaných pro dokončení instance třídy. Finalizační metody nemohou mít parametry, nemohou mít modifikátory dostupnosti a nemůže být explicitně volána. Finalizační metodu pro instance je vyvolána automaticky během uvolňování paměti.

Uvolňování paměti je povoleno široké zeměpisnou šířku při rozhodování, kdy se mají shromažďovat objekty a spustit finalizační metody. Konkrétně načasování finalizační metodu volání není deterministický a finalizační metody mohou být spouštěny žádné přístup z více vláken. Pro tyto a z jiných důvodů by měla třídy implementovat finalizační metody jenom v případě, že jsou vhodná žádná jiná řešení.

`using` Příkaz poskytuje lepší přístup k odstranění objektu.

>[!div class="step-by-step"]
[Předchozí](statements.md)
[další](structs.md)
