---
title: Třídy a objekty v C# -A prohlídku C# jazyka
description: Začínáte C#? Přečtěte si tento přehled tříd, objektů a dědičnosti.
ms.date: 02/27/2020
ms.assetid: 63a89bde-0f05-4bc4-b0cd-4f693854f0cd
ms.openlocfilehash: c178e11b5667905f75538555c8a309e2fdb4a9ef
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159179"
---
# <a name="classes-and-objects"></a>Třídy a objekty

*Třídy* jsou základem C#typů. Třída je datová struktura, která kombinuje stav (pole) a akce (metody a další členy funkce) v jedné jednotce. Třída poskytuje definici pro dynamicky vytvořené *instance* třídy, označované také jako *objekty*. Třídy podporují *Dědičnost* a *polymorfismus*, mechanismy, kterými mohou *odvozené třídy* roztáhnout a specializovat *základní třídy*.

Nové třídy jsou vytvářeny pomocí deklarací třídy. Deklarace třídy začíná hlavičkou, která určuje atributy a modifikátory třídy, název třídy, základní třídu (Pokud je daná) a rozhraní implementovaná třídou. Pod hlavičkou následuje tělo třídy, které se skládá ze seznamu deklarací členů napsaných mezi oddělovači `{` a `}`.

Následující kód ukazuje deklaraci jednoduché třídy s názvem `Point`:

[!code-csharp[PointClass](~/samples/snippets/csharp/tour/classes-and-objects/Point.cs#L3-L11)]

Instance tříd jsou vytvořeny pomocí operátoru `new`, který přiděluje paměť pro novou instanci, vyvolá konstruktor pro inicializaci instance a vrátí odkaz na instanci. Následující příkazy vytvoří dva objekty Point a ukládají odkazy na tyto objekty ve dvou proměnných:

[!code-csharp[PointExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L9-L10)]

Paměť obsazená objektem je automaticky uvolněna v případě, že objekt již není dostupný. Není ani možné explicitně zrušit přidělení objektů v C#.

## <a name="members"></a>Členové

Členy třídy jsou buď statické členy, nebo členy instance. Statické členy patří ke třídám a členy instance patří do objektů (instance tříd).

Následující seznam obsahuje přehled druhů členů, které třída může obsahovat.

- Konstanty
  - Konstantní hodnoty přidružené ke třídě
- Fields (Pole)
  - Proměnné třídy
- Metody
  - Výpočty a akce, které mohou být provedeny třídou
- Vlastnosti
  - Akce spojené s čtením a zápisem s názvem vlastnosti třídy
- Indexery
  - Akce přidružené k indexování instancí třídy, jako je pole
- Události
  - Oznámení, která mohou být vygenerována třídou
- Operátory
  - Převody a operátory výrazů podporované třídou
- Konstruktory
  - Akce vyžadované pro inicializaci instancí třídy nebo samotné třídy
- Finalizační metody
  - Akce, které se mají provést před tím, než se instance třídy trvale zahodí
- Typy
  - Vnořené typy deklarované třídou

## <a name="accessibility"></a>Přístupnost

Každý člen třídy má přidruženou přístupnost, která řídí oblasti textu programu, které mají přístup ke členu. Existuje šest možných forem usnadnění přístupu. Modifikátory přístupu jsou shrnuty níže.

- `public`
  - Přístup není omezen.
- `protected`
  - Přístup je omezen na tuto třídu nebo třídy odvozené z této třídy.
- `internal`
  - Přístup je omezen na aktuální sestavení (. exe,. dll atd.).
- `protected internal`
  - Přístup je omezen na obsahující třídu, třídy odvozené z obsahující třídy nebo třídy v rámci stejného sestavení.
- `private`
  - Přístup je omezen na tuto třídu.
- `private protected`
  - Přístup je omezen na obsahující třídu nebo třídy odvozené z nadřazeného typu v rámci stejného sestavení.

## <a name="type-parameters"></a>Parametry typu

Definice třídy může určovat sadu parametrů typu za názvem třídy a lomenými závorkami ohraničující seznam názvů parametrů typu. Parametry typu lze potom použít v těle deklarací třídy k definování členů třídy. V následujícím příkladu jsou parametry typu `Pair` `TFirst` a `TSecond`:

[!code-csharp[Pair](~/samples/snippets/csharp/tour/classes-and-objects/Pair.cs#L3-L7)]

Typ třídy, která je deklarována pro přijetí parametrů typu, se nazývá *typ obecné třídy*. Typy struktury, rozhraní a delegátů můžou být také obecné.
Při použití obecné třídy je nutné zadat argumenty typu pro každý z parametrů typu:

[!code-csharp[PairExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L15-L17)]

Obecný typ s poskytnutými argumenty typu, například `Pair<int,string>` výše, se označuje jako *konstruovaný typ*.

## <a name="base-classes"></a>Základní třídy

Deklarace třídy může specifikovat základní třídu za názvem třídy a parametry typu s dvojtečkou a názvem základní třídy. Vynechání specifikace základní třídy je stejné jako odvození z typu `object`. V následujícím příkladu je základní třída `Point3D` `Point`a základní třída `Point` je `object`:

[!code-csharp[Point3DClass](~/samples/snippets/csharp/tour/classes-and-objects/Point.cs#L3-L20)]

Třída dědí členy své základní třídy. Dědičnost znamená, že třída implicitně obsahuje všechny členy své základní třídy, s výjimkou instancí a statických konstruktorů a finalizační metody základní třídy. Odvozená třída může přidat nové členy do těch členů, které dědí, ale nemůže odebrat definici zděděného člena. V předchozím příkladu `Point3D` dědí pole `x` a `y` ze `Point`a každá `Point3D` instance obsahuje tři pole, `x`, `y`a `z`.

Implicitní převod existuje z typu třídy na libovolný z jeho základních typů třídy. Proměnná typu třídy může odkazovat na instanci této třídy nebo instance jakékoli odvozené třídy. Například s ohledem na předchozí deklarace třídy může proměnná typu `Point` odkazovat buď na `Point`, nebo na `Point3D`:

[!code-csharp[Point3DExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L22-L23)]

## <a name="fields"></a>Fields (Pole)

*Pole* je proměnná, která je přidružena ke třídě nebo s instancí třídy.

Pole deklarované pomocí statického modifikátoru definuje statické pole. Statické pole identifikuje právě jedno umístění úložiště. Bez ohledu na to, kolik instancí třídy je vytvořeno, je k dispozici pouze jedna kopie statického pole.

Pole deklarované bez statického modifikátoru definuje pole instance. Každá instance třídy obsahuje samostatnou kopii všech polí instance této třídy.

V následujícím příkladu má každá instance třídy `Color` samostatnou kopii polí `r`, `g`a `b` instance, ale existuje pouze jedna kopie `Black`, `White`, `Red`, `Green`a `Blue` statických polí:

[!code-csharp[ColorClass](~/samples/snippets/csharp/tour/classes-and-objects/Color.cs#L3-L17)]

Jak je znázorněno v předchozím příkladu, *pole jen pro čtení* lze deklarovat pomocí modifikátoru `readonly`. Přiřazení k poli `readonly` se může vyskytovat pouze v rámci deklarace pole nebo v konstruktoru ve stejné třídě.

## <a name="methods"></a>Metody

*Metoda* je člen, který implementuje výpočet nebo akci, kterou lze provést pomocí objektu nebo třídy. *Statické metody* jsou k dispozici prostřednictvím třídy. *Metody instance* jsou k dispozici prostřednictvím instancí třídy.

Metody mohou mít seznam *parametrů*, které reprezentují hodnoty nebo odkazy na proměnné předané metodě a *návratový typ*, který určuje typ počítané hodnoty a vrácený metodou. Návratový typ metody je `void`, pokud nevrací hodnotu.

Podobně jako typy mohou metody mít také sadu parametrů typu, pro které argumenty typu musí být zadány při volání metody. Na rozdíl od typů lze argumenty typu často odvodit z argumentů volání metody a nemusí být explicitně předány.

*Signatura* metody musí být jedinečná ve třídě, ve které je metoda deklarovaná. Signatura metody se skládá z názvu metody, počtu parametrů typu a počtu, modifikátorů a typů jeho parametrů. Signatura metody neobsahuje návratový typ.

### <a name="parameters"></a>Parametry

Parametry slouží k předání hodnot nebo odkazů na proměnné metody. Parametry metody získají jejich skutečné hodnoty z *argumentů* , které jsou zadány při volání metody. Existují čtyři typy parametrů: parametry hodnoty, parametry odkazu, výstupní parametry a pole parametrů.

*Parametr hodnoty* se používá pro předávání vstupních argumentů. Parametr hodnoty odpovídá místní proměnné, která vrací počáteční hodnotu z argumentu předaného pro parametr. Úpravy parametru hodnoty neovlivňují argument, který byl předán parametru.

Parametry hodnoty mohou být volitelné, zadáním výchozí hodnoty, aby bylo možné vynechat odpovídající argumenty.

*Parametr reference* se používá pro předávání argumentů odkazem. Argument předaný parametru reference musí být proměnná s určitou hodnotou a během provádění metody představuje parametr reference stejné umístění úložiště jako proměnná argumentu. Parametr reference je deklarován pomocí modifikátoru `ref`. Následující příklad ukazuje použití parametrů `ref`.

[!code-csharp[swapExample](~/samples/snippets/csharp/tour/classes-and-objects/RefExample.cs#L3-L18)]

*Výstupní parametr* se používá pro předávání argumentů odkazem. Je podobná referenčnímu parametru, s tím rozdílem, že nevyžaduje explicitně přiřadit hodnotu k argumentu, který je k dispozici volajícímu. Výstupní parametr je deklarován pomocí modifikátoru `out`. Následující příklad ukazuje použití parametrů `out` pomocí syntaxe představené v C# 7.

[!code-csharp[OutExample](~/samples/snippets/csharp/tour/classes-and-objects/OutExample.cs#L3-L17)]

*Pole parametrů* povoluje proměnný počet argumentů, které mají být předány metodě. Pole parametrů je deklarováno s modifikátorem `params`. Pouze poslední parametr metody může být pole parametrů a typ pole parametrů musí být jednorozměrné pole. Metody Write a WriteLine třídy <xref:System.Console?displayProperty=nameWithType> jsou vhodnými příklady použití pole parametrů. Jsou deklarovány následujícím způsobem.

[!code-csharp[ConsoleExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L78-L83)]

V rámci metody, která používá pole parametrů, se pole parametru chová stejně jako regulární parametr typu pole. Při vyvolání metody s parametrem pole je však možné předat buď jeden argument typu pole parametru, nebo libovolný počet argumentů typu prvku pole parametrů. V druhém případě je instance pole automaticky vytvořena a inicializována s danými argumenty. Příklad:

[!code-csharp[StringFormat](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L55-L55)]

je ekvivalentem zápisu následujícího.

[!code-csharp[StringFormat2](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L30-L35)]

### <a name="method-body-and-local-variables"></a>Tělo metody a místní proměnné

Tělo metody Určuje příkazy, které mají být provedeny při volání metody.

Tělo metody může deklarovat proměnné, které jsou specifické pro vyvolání metody. Tyto proměnné se nazývají *místní proměnné*. Místní deklarace proměnné Určuje název typu, název proměnné a pravděpodobně počáteční hodnotu. Následující příklad deklaruje místní proměnnou `i` s počáteční hodnotou 0 a místní proměnnou `j` bez počáteční hodnoty.

[!code-csharp[Squares](~/samples/snippets/csharp/tour/classes-and-objects/Squares.cs#L3-L17)]

C#aby bylo možné získat hodnotu, musí být místní proměnná *jednoznačně přiřazena* . Například pokud deklarace předchozí `i` neobsahovala počáteční hodnotu, kompilátor by nahlásil chybu pro následné použití `i`, protože `i` nemusely být jednoznačně přiřazeny v těchto bodech v programu.

Metoda může použít příkazy `return` pro vrácení řízení volajícímu. V metodě, která vrací `void`, `return` příkazy nemůžou specifikovat výraz. V metodě vracející typ, který není void, `return` příkazy musí zahrnovat výraz, který vypočítá vrácenou hodnotu.

### <a name="static-and-instance-methods"></a>Statické a instanční metody

Metoda deklarovaná pomocí statického modifikátoru je *statická metoda*. Statická metoda nefunguje na konkrétní instanci a může přímo přistupovat ke statickým členům.

Metoda deklarovaná bez statického modifikátoru je *Metoda instance*. Metoda instance pracuje na konkrétní instanci a může přistupovat ke statickým i instancím členů. Instance, na které byla vyvolána metoda instance, může být explicitně k dispozici jako `this`. Odkaz na `this` ve statické metodě je chyba.

Následující třída `Entity` má statické i členy instance.

[!code-csharp[Entity](~/samples/snippets/csharp/tour/classes-and-objects/Entity.cs#L16-L36)]

Každá instance `Entity` obsahuje sériové číslo (a předpokládá se, že některé další informace nejsou zde uvedeny). Konstruktor `Entity` (který je jako metoda instance) Inicializuje novou instanci s dalším dostupným sériovým číslem. Vzhledem k tomu, že je konstruktor členem instance, je povolen přístup k poli `serialNo` instance i k `nextSerialNo` statickému poli.

Statické metody `GetNextSerialNo` a `SetNextSerialNo` mají přístup k poli `nextSerialNo` static, ale při přímém přístupu k poli instance `serialNo` by došlo k chybě.

Následující příklad ukazuje použití třídy entity.

[!code-csharp[EntityExample](~/samples/snippets/csharp/tour/classes-and-objects/Entity.cs#L3-L15)]

Statické metody `SetNextSerialNo` a `GetNextSerialNo` jsou vyvolány na třídě, zatímco metoda instance `GetSerialNo` je vyvolána na instancích třídy.

### <a name="virtual-override-and-abstract-methods"></a>Virtuální, přepisování a abstraktní metody

Pokud deklarace metody instance obsahuje modifikátor `virtual`, metoda je označována jako *virtuální metoda*. Pokud není k dispozici žádný modifikátor Virtual, metoda je označována jako *nevirtuální metoda*.

Když je vyvolána virtuální metoda, je *typ běhu* instance, pro kterou probíhá vyvolání, určuje vlastní implementaci metody, která má být vyvolána. V nevirtuálním volání metody je *Typ doby kompilace* instance určujícím faktorem.

Virtuální metoda může být *přepsána* v odvozené třídě. Pokud deklarace metody instance obsahuje modifikátor přepsání, metoda přepíše zděděnou virtuální metodu se stejnou signaturou. Zatímco deklarace virtuální metody zavádí novou metodu, deklarace metody přepsání specializuje existující zděděnou virtuální metodu tím, že poskytuje novou implementaci této metody.

*Abstraktní metoda* je virtuální metoda bez implementace. Abstraktní metoda je deklarována s modifikátorem abstract a je povolena pouze ve třídě, která je také deklarována jako abstraktní. Abstraktní metoda musí být přepsána v každé neabstraktní odvozené třídě.

Následující příklad deklaruje abstraktní třídu, `Expression`, která představuje uzel stromu výrazu, a tři odvozené třídy, `Constant`, `VariableReference`a `Operation`, které implementují uzly stromu výrazů pro konstanty, odkazy na proměnné a aritmetické operace. (Tento příklad je podobný, ale nelze je zaměňovat s typy stromu výrazů).

[!code-csharp[ExpressionClass](~/samples/snippets/csharp/tour/classes-and-objects/Expressions.cs#L3-L61)]

K modelování aritmetických výrazů lze použít předchozí čtyři třídy. Například použití instancí těchto tříd může být výraz `x + 3` reprezentován následujícím způsobem.

[!code-csharp[ExpressionExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L40-L43)]

Metoda `Evaluate` instance `Expression` je vyvolána pro vyhodnocení daného výrazu a vytvoření `double` hodnoty. Metoda přebírá `Dictionary` argument, který obsahuje názvy proměnných (jako klíče položek) a hodnoty (jako hodnoty položek). Vzhledem k tomu, že `Evaluate` je abstraktní metoda, neabstraktní třídy odvozené od `Expression` musí přepsat `Evaluate`.

Implementace `Evaluate` `Constant`jednoduše vrátí uloženou konstantu. Implementace `VariableReference`vyhledá název proměnné ve slovníku a vrátí výslednou hodnotu. Implementace `Operation`nejprve vyhodnotí levý a pravý operand (rekurzivním voláním metod `Evaluate`) a poté provede danou aritmetickou operaci.

Následující program používá třídy `Expression` k vyhodnocení výrazu `x * (y + 2)` pro jiné hodnoty `x` a `y`.

[!code-csharp[ExpressionUsage](~/samples/snippets/csharp/tour/classes-and-objects/Expressions.cs#L66-L89)]

### <a name="method-overloading"></a>Přetížení metody

*Přetížení* metody umožňuje, aby více metod ve stejné třídě měl stejný název, pokud mají jedinečné podpisy. Při kompilování volání přetížené metody kompilátor používá *řešení přetížení* k určení konkrétní metody, která má být vyvolána. Řešení přetížení najde jednu metodu, která nejlépe odpovídá argumentům, nebo hlásí chybu, pokud nelze najít žádnou nejlepší shodu. Následující příklad ukazuje rozlišení přetížení v platnosti. Komentář pro každé vyvolání v metodě `UsageExample` ukazuje, která metoda je vyvolána.

[!code-csharp[OverloadUsage](~/samples/snippets/csharp/tour/classes-and-objects/Overloading.cs#L3-L41)]

Jak je znázorněno v příkladu, konkrétní metodu lze vždy vybrat explicitním přetypováním argumentů na přesné typy parametrů a/nebo explicitním zadáním argumentů typu.

## <a name="other-function-members"></a>Další členové funkcí

Členy, které obsahují spustitelný kód, jsou souhrnně označovány jako *Členové funkce* třídy. Předchozí část popisuje metody, které jsou primárními typy členů funkce. Tato část popisuje další typy členů funkce, které C#podporuje: konstruktory, vlastnosti, indexery, události, operátory a finalizační metody.

Následující příklad ukazuje obecnou třídu s názvem `MyList<T>`, která implementuje zvětšený seznam objektů. Třída obsahuje několik příkladů nejběžnějších druhů členů funkce.

> [!NOTE]
> Tento příklad vytvoří třídu `MyList`, která není stejná jako <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.NET Standard. Ilustruje koncepty potřebné pro tuto prohlídku, ale není náhradou za tuto třídu.

[!code-csharp[ListClass](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L4-L89)]

### <a name="constructors"></a>Konstruktory

C#podporuje jak instance, tak statické konstruktory. *Konstruktor instance* je člen, který implementuje akce vyžadované pro inicializaci instance třídy. *Statický konstruktor* je člen, který implementuje akce vyžadované k inicializaci samotné třídy při prvním načtení.

Konstruktor je deklarovaný jako metoda bez návratového typu a stejný název jako obsahující třída. Pokud deklarace konstruktoru obsahuje statický modifikátor, deklaruje statický konstruktor. V opačném případě deklaruje konstruktor instance.

Konstruktory instancí můžou být přetížené a můžou mít volitelné parametry. Například třída `MyList<T>` deklaruje jeden konstruktor instance s jedním volitelným `int` parametrem. Konstruktory instancí jsou vyvolány pomocí operátoru `new`. Následující příkazy přidělují dvě `MyList<string>` instance pomocí konstruktoru `MyList` třídy s a bez volitelného argumentu.

[!code-csharp[ListExample1](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L95-L96)]

Na rozdíl od jiných členů konstruktory instancí nejsou děděny a třída nemá žádné konstruktory instancí, než tyto konstruktory jsou ve skutečnosti deklarovány ve třídě. Pokud pro třídu není zadán konstruktor instance, bude automaticky zadáno prázdné číslo bez parametrů.

### <a name="properties"></a>Vlastnosti

*Vlastnosti* jsou přirozené rozšíření polí. Oba se nazývají členové s přidruženými typy a syntaxe pro přístup k polím a vlastnostem je stejná. Na rozdíl od polí ale vlastnosti neoznačují umístění úložiště. Místo toho mají vlastnosti *přistupující objekty* , které určují příkazy, které mají být provedeny, když jsou jejich hodnoty čteny nebo zapsány.

Vlastnost je deklarována jako pole s tím rozdílem, že deklarace končí pomocí přístupového objektu Get nebo pomocí přístupového objektu sady zapsaného mezi oddělovači `{` a `}` namísto ukončení středníku. Vlastnost, která má přistupující objekt get i přístupový objekt set, je *vlastnost pro čtení i zápis*, vlastnost, která má pouze přistupující objekt get, je *vlastnost jen pro čtení*a vlastnost, která má pouze přístupový objekt set, je *vlastnost pouze pro zápis*.

Přístupový objekt get odpovídá metodě bez parametrů s návratovou hodnotou typu vlastnosti. S výjimkou cíle přiřazení, při odkazování na vlastnost ve výrazu, je vyvolána přístupová metoda get vlastnosti pro výpočet hodnoty vlastnosti.

Přístupový objekt set odpovídá metodě s jedním parametrem s názvem Value a bez návratového typu. Když se na vlastnost odkazuje jako na cíl přiřazení nebo jako operand + + nebo--, přistupující objekt set je vyvolán s argumentem, který poskytuje novou hodnotu.

Třída `MyList<T>` deklaruje dvě vlastnosti, `Count` a `Capacity`, které jsou jen pro čtení a pro čtení i zápis, v uvedeném pořadí. Následující kód je příkladem použití těchto vlastností:

[!code-csharp[ListExample2](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L101-L104)]

Podobně jako pole a metody C# podporuje vlastnosti instance i statické vlastnosti. Statické vlastnosti jsou deklarovány se statickým modifikátorem a vlastnosti instance jsou deklarovány bez ní.

Přístupové objekty vlastnosti mohou být virtuální. Pokud deklarace vlastnosti obsahuje modifikátor `virtual`, `abstract`nebo `override`, vztahuje se na přistupující objekty vlastnosti.

### <a name="indexers"></a>Indexery

*Indexer* je člen, který umožňuje, aby objekty byly indexovány stejným způsobem jako pole. Indexer je deklarován jako vlastnost s tím rozdílem, že název členu je `this` následovaný seznamem parametrů napsaným mezi oddělovači `[` a `]`. Parametry jsou k dispozici v přistupujícím objektu indexeru. Podobně jako u vlastností mohou být indexery pro čtení i zápis, jen pro čtení a přístup k nástroji indexeru, které mohou být virtuální.

Třída `MyList<T>` deklaruje jeden indexer pro čtení a zápis, který přebírá parametr `int`. Indexer umožňuje indexovat `MyList<T>` instancí s použitím hodnot `int`. Příklad:

[!code-csharp[ListExample3](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L109-L117)]

Indexery mohou být přetíženy, což znamená, že třída může deklarovat více indexerů za předpokladu, že počet nebo typy jejich parametrů se liší.

### <a name="events"></a>Události

*Událost* je člen, který umožňuje třídě nebo objektu poskytovat oznámení. Událost je deklarována jako pole s tím rozdílem, že deklarace zahrnuje klíčové slovo události a typ musí být delegát typu.

V rámci třídy, která deklaruje člena události, se událost chová stejně jako pole typu delegáta (za předpokladu, že událost není abstraktní a nedeklaruje přistupující objekty). Pole ukládá odkaz na delegáta, který představuje obslužné rutiny událostí, které byly přidány do události. Pokud nejsou k dispozici žádné obslužné rutiny událostí, pole je `null`.

Třída `MyList<T>` deklaruje jednoho člena události s názvem `Changed`, který označuje, že do seznamu byla přidána nová položka. Změněná událost je vyvolána `OnChanged` virtuální metodou, která nejprve kontroluje, zda je událost `null` (což znamená, že nejsou přítomny žádné obslužné rutiny). Pojem vyvolání události je přesně shodný s voláním delegáta reprezentovaného událostí, takže neexistují žádné speciální jazykové konstrukce pro vyvolání událostí.

Klienti reagují na události prostřednictvím *obslužných rutin událostí*. Obslužné rutiny události jsou připojeny pomocí operátoru `+=` a odebraly se pomocí operátoru `-=`. Následující příklad připojí obslužnou rutinu události k události `Changed` `MyList<string>`.

[!code-csharp[EventExample](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L132-L148)]

Pro pokročilé scénáře, kde je požadováno řízení základního úložiště události, může deklarace události explicitně poskytnout `add` a přístupové objekty `remove`, které jsou podobné přístupovému objektu `set` vlastnosti.

### <a name="operators"></a>Operátory

*Operátor* je člen, který definuje význam použití konkrétního operátoru výrazu na instance třídy. Lze definovat tři typy operátorů: unární operátory, binární operátory a operátory převodu. Všechny operátory musí být deklarovány jako `public` a `static`.

Třída `MyList<T>` deklaruje dva operátory, `operator ==` a `operator !=`, a díky tomu má nový význam pro výrazy, které tyto operátory aplikují na instance `MyList`. Konkrétně operátory definují rovnost dvou instancí `MyList<T>` jako porovnávání každého z obsažených objektů pomocí jejich stejných metod. Následující příklad používá operátor `==` k porovnání dvou instancí `MyList<int>`.

[!code-csharp[OperatorExample](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L121-L129)]

První `Console.WriteLine` výstupy `True`, protože dva seznamy obsahují stejný počet objektů se stejnými hodnotami ve stejném pořadí. `MyList<T>` není definován `operator ==`, první `Console.WriteLine` by měla výstup `False`, protože `a` a `b` odkazují na různé instance `MyList<int>`.

### <a name="finalizers"></a>Finalizační metody

*Finalizační metoda* je člen, který implementuje akce vyžadované k finalizaci instance třídy. Finalizační metody nemohou mít parametry, nemohou mít modifikátory dostupnosti a nelze je volat explicitně. Finalizační metoda pro instanci je vyvolána automaticky během uvolňování paměti.

Uvolňování paměti je povolená rozsáhlá Zeměpisná šířka při rozhodování o shromažďování objektů a spouštění finalizační metody. Konkrétně časování volání finalizační metody není deterministické a finalizační metody mohou být provedeny v jakémkoli vlákně. Z těchto a dalších důvodů by třídy měly implementovat finalizační metody pouze v případě, že žádná jiná řešení nejsou proveditelná.

Příkaz `using` poskytuje lepší přístup k zničení objektu.

> [!div class="step-by-step"]
> [Předchozí](statements.md)
> [Další](arrays.md)
