---
title: Stavební kameny programů v jazyce C# "
description: Přečtěte si o členech, výrazech a příkazech jazyka C#. Typy obsahují členy, které zapisujete. Tyto členy jsou sestaveny z příkazů a výrazů.
ms.date: 08/06/2020
ms.openlocfilehash: 142fe7b5a3424a8925638bfb4e4437392347f4c6
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2020
ms.locfileid: "88268137"
---
# <a name="program-building-blocks"></a>Stavební bloky programu

Typy popsané v předchozím článku jsou sestaveny pomocí těchto stavebních bloků: [***členy***](../programming-guide/classes-and-structs/members.md), [ ***výrazy***a ***příkazy***](../programming-guide/statements-expressions-operators/index.md).

## <a name="members"></a>Členové

Členové a `class` jsou buď ***statickými členy*** , nebo ***členy instance***. Statické členy patří ke třídám a členy instance patří do objektů (instance tříd).

Následující seznam obsahuje přehled druhů členů, které třída může obsahovat.

- **Konstanty**: konstantní hodnoty přidružené ke třídě
- **Pole**: proměnné, které jsou přidruženy ke třídě
- **Metody**: akce, které mohou být provedeny třídou
- **Vlastnosti**: akce spojené s čtením a zápisem s názvem vlastnosti třídy
- **Indexery**: akce přidružené k indexování instancí třídy, jako je pole
- **Události**: oznámení, která mohou být vygenerována třídou
- **Operátory**: převody a operátory výrazů podporované třídou
- **Konstruktory**: akce vyžadované pro inicializaci instancí třídy nebo samotné třídy
- **Finalizační metody**: akce provedené před trvalým zahozením instancí třídy
- **Typy**: vnořené typy deklarované třídou

## <a name="accessibility"></a>Přístupnost

Každý člen třídy má přidruženou přístupnost, která řídí oblasti textu programu, které mají přístup ke členu. Existuje šest možných forem usnadnění přístupu. Modifikátory přístupu jsou shrnuty níže.

- `public`: Přístup není omezený.
- `private`: Přístup je omezen na tuto třídu.
- `protected`: Přístup je omezen na tuto třídu nebo třídy odvozené z této třídy.
- `internal`: Přístup je omezen na aktuální sestavení ( `.exe` nebo `.dll` ).
- `protected internal`: Přístup je omezen na tuto třídu, třídy odvozené z této třídy nebo třídy v rámci stejného sestavení.
- `private protected`: Přístup je omezen na tuto třídu nebo třídy odvozené z tohoto typu v rámci stejného sestavení.

## <a name="fields"></a>Fields (Pole)

*Pole* je proměnná, která je přidružena ke třídě nebo s instancí třídy.

Pole deklarované pomocí statického modifikátoru definuje statické pole. Statické pole identifikuje právě jedno umístění úložiště. Bez ohledu na to, kolik instancí třídy je vytvořeno, je k dispozici pouze jedna kopie statického pole.

Pole deklarované bez statického modifikátoru definuje pole instance. Každá instance třídy obsahuje samostatnou kopii všech polí instance této třídy.

V následujícím příkladu má každá instance `Color` třídy samostatnou kopii `r` `g` `b` polí instance, a, ale existuje pouze jedna kopie `Black` `White` pole,, `Red` , `Green` a `Blue` statických polí:

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="ColorClassDefinition":::

Jak je znázorněno v předchozím příkladu, *pole jen pro čtení* mohou být deklarována s `readonly` modifikátorem. Přiřazení k poli jen pro čtení se může vyskytovat pouze v rámci deklarace pole nebo v konstruktoru ve stejné třídě.

## <a name="methods"></a>Metody

*Metoda* je člen, který implementuje výpočet nebo akci, kterou lze provést pomocí objektu nebo třídy. *Statické metody* jsou k dispozici prostřednictvím třídy. *Metody instance* jsou k dispozici prostřednictvím instancí třídy.

Metody mohou mít seznam *parametrů*, které reprezentují hodnoty nebo odkazy na proměnné předané metodě. Metody mají *návratový typ*, který určuje typ počítané hodnoty a vrácený metodou. Návratový typ metody je `void` , pokud nevrací hodnotu.

Podobně jako typy mohou metody mít také sadu parametrů typu, pro které argumenty typu musí být zadány při volání metody. Na rozdíl od typů lze argumenty typu často odvodit z argumentů volání metody a nemusí být explicitně předány.

*Signatura* metody musí být jedinečná ve třídě, ve které je metoda deklarovaná. Signatura metody se skládá z názvu metody, počtu parametrů typu a počtu, modifikátorů a typů jeho parametrů. Signatura metody neobsahuje návratový typ.

Je-li tělo metody jeden výraz, lze metodu definovat pomocí formátu kompaktního výrazu, jak je znázorněno v následujícím příkladu:

```csharp
public override ToString() => "This is an object";
```

### <a name="parameters"></a>Parametry

Parametry slouží k předání hodnot nebo odkazů na proměnné metody. Parametry metody získají jejich skutečné hodnoty z *argumentů* , které jsou zadány při volání metody. Existují čtyři typy parametrů: parametry hodnoty, parametry odkazu, výstupní parametry a pole parametrů.

*Parametr hodnoty* se používá pro předávání vstupních argumentů. Parametr hodnoty odpovídá místní proměnné, která vrací počáteční hodnotu z argumentu předaného pro parametr. Úpravy parametru hodnoty neovlivňují argument, který byl předán parametru.

Parametry hodnoty mohou být volitelné, zadáním výchozí hodnoty, aby bylo možné vynechat odpovídající argumenty.

*Parametr reference* se používá pro předávání argumentů odkazem. Argument předaný parametru reference musí být proměnná s určitou hodnotou. Během provádění metody představuje parametr reference stejné umístění úložiště jako proměnná argumentu. Parametr reference je deklarován s `ref` modifikátorem. Následující příklad ukazuje použití `ref` parametrů.

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="RefExample":::

*Výstupní parametr* se používá pro předávání argumentů odkazem. Je podobná referenčnímu parametru, s tím rozdílem, že nevyžaduje explicitně přiřadit hodnotu k argumentu, který je k dispozici volajícímu. Výstupní parametr je deklarován s `out` modifikátorem. Následující příklad ukazuje použití `out` parametrů pomocí syntaxe představené v jazyce C# 7.

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="OutExample":::

*Pole parametrů* povoluje proměnný počet argumentů, které mají být předány metodě. Pole parametrů je deklarováno s `params` modifikátorem. Pouze poslední parametr metody může být pole parametrů a typ pole parametrů musí být jednorozměrné pole. `Write`Metody a `WriteLine` <xref:System.Console?displayProperty=nameWithType> třídy jsou osvědčenými příklady použití pole parametrů. Jsou deklarovány následujícím způsobem.

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="ConsoleExtract":::

V rámci metody, která používá pole parametrů, se pole parametru chová stejně jako regulární parametr typu pole. Při vyvolání metody s parametrem pole je však možné předat buď jeden argument typu pole parametru, nebo libovolný počet argumentů typu prvku pole parametrů. V druhém případě je instance pole automaticky vytvořena a inicializována s danými argumenty. Tento příklad

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="UseParamsArgs":::

je ekvivalentem zápisu následujícího.

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="CompilerParams":::

### <a name="method-body-and-local-variables"></a>Tělo metody a místní proměnné

Tělo metody Určuje příkazy, které mají být provedeny při volání metody.

Tělo metody může deklarovat proměnné, které jsou specifické pro vyvolání metody. Tyto proměnné se nazývají *místní proměnné*. Místní deklarace proměnné Určuje název typu, název proměnné a pravděpodobně počáteční hodnotu. Následující příklad deklaruje místní proměnnou `i` s počáteční hodnotou nula a místní proměnnou `j` bez počáteční hodnoty.

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="SquaresClass":::

Jazyk C# vyžaduje, aby místní proměnná byla *jednoznačně přiřazena* , aby bylo možné získat její hodnotu. Například pokud deklarace předchozího `i` neobsahovala počáteční hodnotu, kompilátor by nahlásil chybu pro pozdější použití, protože by nemuseli `i` `i` být jednoznačně přiřazeni v těchto bodech v programu.

Metoda může použít `return` příkazy pro vrácení řízení volajícímu. V metodách, které vracejí `void` , `return` příkazy nemůžou zadat výraz. V metodě, která vrací typ non-void, `return` musí příkazy zahrnovat výraz, který vypočítá vrácenou hodnotu.

### <a name="static-and-instance-methods"></a>Statické a instanční metody

Metoda deklarovaná s `static` modifikátorem je *statická metoda*. Statická metoda nefunguje na konkrétní instanci a může přímo přistupovat ke statickým členům.

Metoda deklarovaná bez `static` modifikátoru je *Metoda instance*. Metoda instance pracuje na konkrétní instanci a může přistupovat ke statickým i instancím členů. Instance, na které byla vyvolána metoda instance, může být explicitně k dispozici jako `this` . V případě, že se odkazuje na statickou metodu, se jedná o chybu `this` .

Následující `Entity` Třída má členy statických i instancí.

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="EntityClass":::

Každá `Entity` instance obsahuje sériové číslo (a předpokládá se, že některé další informace nejsou zde uvedeny). `Entity`Konstruktor (který je jako metoda instance) Inicializuje novou instanci s dalším dostupným sériovým číslem. Vzhledem k tomu, že je konstruktor členem instance, je povolen přístup k `_serialNo` poli instance i k `s_nextSerialNo` statickému poli.

`GetNextSerialNo` `SetNextSerialNo` Statické metody a můžou přistupovat ke `s_nextSerialNo` statickému poli, ale při přímém přístupu k poli instance by to byla chyba `_serialNo` .

Následující příklad ukazuje použití `Entity` třídy.

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="UsingEntity":::

`SetNextSerialNo` `GetNextSerialNo` Statické metody a jsou vyvolány ve třídě, zatímco `GetSerialNo` Metoda instance je vyvolána na instancích třídy.

### <a name="virtual-override-and-abstract-methods"></a>Virtuální, přepisování a abstraktní metody

Pokud deklarace metody instance obsahuje `virtual` modifikátor, metoda je označována jako *virtuální metoda*. Pokud není k dispozici žádný modifikátor Virtual, metoda je označována jako *nevirtuální metoda*.

Když je vyvolána virtuální metoda, je *typ běhu* instance, pro kterou probíhá vyvolání, určuje vlastní implementaci metody, která má být vyvolána. V nevirtuálním volání metody je *Typ doby kompilace* instance určujícím faktorem.

Virtuální metoda může být *přepsána* v odvozené třídě. Pokud deklarace metody instance obsahuje modifikátor přepsání, metoda přepíše zděděnou virtuální metodu se stejnou signaturou. AA deklarace virtuální metody zavádí novou metodu. Deklarace metody přepsání specializuje existující zděděnou virtuální metodu tím, že poskytuje novou implementaci této metody.

*Abstraktní metoda* je virtuální metoda bez implementace. Abstraktní metoda je deklarována s `abstract` modifikátorem a je povolena pouze v abstraktní třídě. Abstraktní metoda musí být přepsána v každé neabstraktní odvozené třídě.

Následující příklad deklaruje abstraktní třídu, `Expression` , která představuje uzel stromu výrazu, a tři odvozené třídy,, `Constant` `VariableReference` , a `Operation` , které implementují uzly stromu výrazu pro konstanty, odkazy na proměnné a aritmetické operace. (Tento příklad je podobný jako, ale nesouvisí s typy stromu výrazů).

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="WorkingWithExpressions":::

K modelování aritmetických výrazů lze použít předchozí čtyři třídy. Například pomocí instancí těchto tříd `x + 3` může být výraz reprezentován následujícím způsobem.

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="UseExpressions":::

`Evaluate`Metoda `Expression` instance je vyvolána pro vyhodnocení daného výrazu a vytvoření `double` hodnoty. Metoda přebírá `Dictionary` argument, který obsahuje názvy proměnných (jako klíče záznamů) a hodnoty (jako hodnoty položek). Protože `Evaluate` je abstraktní metoda, neabstraktní třídy odvozené z musí být `Expression` přepsány `Evaluate` .

`Constant`Implementace `Evaluate` jednoduše vrátí uloženou konstantu. `VariableReference`Implementace objektu vyhledá název proměnné ve slovníku a vrátí výslednou hodnotu. `Operation`Implementace nejprve vyhodnotí levý a pravý operand (rekurzivním voláním `Evaluate` metod) a poté provede danou aritmetickou operaci.

Následující program používá `Expression` třídy pro vyhodnocení výrazu `x * (y + 2)` pro různé hodnoty `x` a `y` .

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="UsingExpressions":::

### <a name="method-overloading"></a>Přetížení metody

*Přetížení* metody umožňuje, aby více metod ve stejné třídě měl stejný název, pokud mají jedinečné podpisy. Při kompilování volání přetížené metody kompilátor používá *řešení přetížení* k určení konkrétní metody, která má být vyvolána. Řešení přetížení najde jednu metodu, která nejlépe odpovídá argumentům. Pokud nemůžete najít žádnou nejlepší shodu, nahlásí se chyba. Následující příklad ukazuje rozlišení přetížení v platnosti. Komentář pro každé vyvolání v `UsageExample` metodě ukazuje, která metoda je vyvolána.

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="Overloading":::

Jak je znázorněno v příkladu, konkrétní metodu lze vždy vybrat explicitním přetypováním argumentů na přesné typy parametrů a argumenty typu.

## <a name="other-function-members"></a>Další členové funkcí

Členy, které obsahují spustitelný kód, jsou souhrnně označovány jako *Členové funkce* třídy. Předchozí část popisuje metody, které jsou primárními typy členů funkce. Tato část popisuje další druhy členů funkce podporované jazykem C#: konstruktory, vlastnosti, indexery, události, operátory a finalizační metody.

Následující příklad ukazuje obecnou třídu s názvem `MyList<T>` , která implementuje zvětšený seznam objektů. Třída obsahuje několik příkladů nejběžnějších druhů členů funkce.

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="ListExample":::

### <a name="constructors"></a>Konstruktory

Jazyk C# podporuje konstruktory instancí i statických konstruktorů. *Konstruktor instance* je člen, který implementuje akce vyžadované pro inicializaci instance třídy. *Statický konstruktor* je člen, který implementuje akce vyžadované k inicializaci samotné třídy při prvním načtení.

Konstruktor je deklarovaný jako metoda bez návratového typu a stejný název jako obsahující třída. Pokud deklarace konstruktoru obsahuje `static` modifikátor, deklaruje statický konstruktor. V opačném případě deklaruje konstruktor instance.

Konstruktory instancí můžou být přetížené a můžou mít volitelné parametry. Například `MyList<T>` Třída deklaruje jeden konstruktor instance s jedním volitelným `int` parametrem. Konstruktory instancí jsou vyvolány pomocí `new` operátoru. Následující příkazy přidělují dvě `MyList<string>` instance pomocí konstruktoru `MyList` třídy s nepovinným argumentem a bez něj.

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="CreateLists":::

Na rozdíl od jiných členů nejsou konstruktory instancí děděny. Třída nemá žádné konstruktory instancí jiné než konstruktory, které jsou ve skutečnosti deklarovány ve třídě. Pokud pro třídu není zadán konstruktor instance, bude automaticky zadáno prázdné číslo bez parametrů.

### <a name="properties"></a>Vlastnosti

*Vlastnosti* jsou přirozené rozšíření polí. Oba se nazývají členové s přidruženými typy a syntaxe pro přístup k polím a vlastnostem je stejná. Na rozdíl od polí ale vlastnosti neoznačují umístění úložiště. Místo toho mají vlastnosti *přistupující objekty* , které určují příkazy, které byly provedeny, když jsou jejich hodnoty čteny nebo zapsány.

Vlastnost je deklarována jako pole s tím rozdílem, že deklarace končí pomocí přístupového objektu Get nebo pomocí přístupového objektu sady zapsaný mezi oddělovači `{` a `}` místo konci středníku. Vlastnost, která má přistupující objekt get i přístupový objekt set, je *vlastnost pro čtení i zápis*, vlastnost, která má pouze přistupující objekt get, je *vlastnost jen pro čtení*a vlastnost, která má pouze přístupový objekt set, je *vlastnost pouze pro zápis*.

Přístupový objekt get odpovídá metodě bez parametrů s návratovou hodnotou typu vlastnosti. Přístupový objekt set odpovídá metodě s jedním parametrem s názvem Value a bez návratového typu. Přistupující objekt get vypočítá hodnotu vlastnosti. Přístupový objekt set poskytuje novou hodnotu pro vlastnost. Když je vlastnost cílem přiřazení, nebo operandem `++` nebo `--` , je vyvolána přistupující objekt set. V jiných případech, kde je odkazováno na vlastnost, je vyvolána přistupující objekt get.

 Když se na vlastnost odkazuje jako na cíl přiřazení nebo jako operand + + nebo--, přistupující objekt set je vyvolán s argumentem, který poskytuje novou hodnotu.

`MyList<T>`Třída deklaruje dvě vlastnosti, `Count` `Capacity` které jsou jen pro čtení a pro čtení i zápis, v uvedeném pořadí. Následující kód je příkladem použití těchto vlastností:

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="AccessProperties":::

Podobně jako pole a metody podporuje C# vlastnosti instance i statické vlastnosti. Statické vlastnosti jsou deklarovány se statickým modifikátorem a vlastnosti instance jsou deklarovány bez ní.

Přístupové objekty vlastnosti mohou být virtuální. Pokud deklarace vlastnosti obsahuje `virtual` `abstract` modifikátor, nebo, vztahuje se `override` na přístupový objekt (y) vlastnosti.

### <a name="indexers"></a>Indexery

*Indexer* je člen, který umožňuje, aby objekty byly indexovány stejným způsobem jako pole. Indexer je deklarován jako vlastnost s tím rozdílem, že název člena je `this` následován seznamem parametrů napsaným mezi oddělovači `[` a `]` . Parametry jsou k dispozici v přistupujícím objektu indexeru. Podobně jako u vlastností mohou být indexery pro čtení i zápis, jen pro čtení a přístup k nástroji indexeru, které mohou být virtuální.

`MyList<T>`Třída deklaruje jeden indexer pro čtení a zápis, který přebírá `int` parametr. Indexer umožňuje indexovat `MyList<T>` instance s `int` hodnotami. Příklad:

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="ListAccess":::

Indexery mohou být přetíženy. Třída může deklarovat více indexerů za předpokladu, že počet nebo typy jejich parametrů se liší.

### <a name="events"></a>Události

*Událost* je člen, který umožňuje třídě nebo objektu poskytovat oznámení. Událost je deklarována jako pole s tím rozdílem, že deklarace zahrnuje `event` klíčové slovo a typ musí být delegovaný typ.

V rámci třídy, která deklaruje člena události, se událost chová stejně jako pole typu delegáta (za předpokladu, že událost není abstraktní a nedeklaruje přistupující objekty). Pole ukládá odkaz na delegáta, který představuje obslužné rutiny událostí, které byly přidány do události. Pokud nejsou k dispozici žádné obslužné rutiny událostí, pole je `null` .

`MyList<T>`Třída deklaruje jeden člen události s názvem `Changed` , který indikuje, že do seznamu byla přidána nová položka. Změněná událost je vyvolána `OnChanged` virtuální metodou, která nejprve kontroluje, zda je událost `null` (to znamená, že nejsou přítomny žádné obslužné rutiny). Pojem vyvolání události je přesně shodný s voláním delegáta, reprezentovaného událostí. Pro vyvolání událostí nejsou k dispozici žádné speciální jazykové konstrukce.

Klienti reagují na události prostřednictvím *obslužných rutin událostí*. Obslužné rutiny událostí jsou připojeny pomocí `+=` operátoru a odebrány pomocí `-=` operátoru. Následující příklad připojí obslužnou rutinu události k `Changed` události `MyList<string>` .

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="RespondToEvents":::

Pro pokročilé scénáře, kde je požadováno řízení základního úložiště události, může deklarace události explicitně poskytnout `add` a `remove` přistupující objekty, které jsou podobné `set` přístupovému objektu vlastnosti.

### <a name="operators"></a>Operátory

*Operátor* je člen, který definuje význam použití konkrétního operátoru výrazu na instance třídy. Lze definovat tři typy operátorů: unární operátory, binární operátory a operátory převodu. Všechny operátory musí být deklarovány jako `public` a `static` .

`MyList<T>`Třída deklaruje dva operátory `operator ==` a `operator !=` . Tyto přepsané operátory poskytují nový význam pro výrazy, které tyto operátory aplikují na `MyList` instance. Konkrétně operátory definují rovnost dvou `MyList<T>` instancí jako porovnávání každého z obsažených objektů pomocí jejich `Equals` metod. Následující příklad používá `==` operátor k porovnání dvou `MyList<int>` instancí.

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="ListAddition":::

První `Console.WriteLine` výstupy, `True` protože dva seznamy obsahují stejný počet objektů se stejnými hodnotami ve stejném pořadí. `MyList<T>`Nebyl definován `operator ==` , první `Console.WriteLine` by měl výstup, `False` protože `a` a odkazují na `b` různé `MyList<int>` instance.

### <a name="finalizers"></a>Finalizační metody

*Finalizační metoda* je člen, který implementuje akce vyžadované k finalizaci instance třídy. Pro uvolnění nespravovaných prostředků je obvykle potřeba finalizační metoda. Finalizační metody nemohou mít parametry, nemohou mít modifikátory dostupnosti a nelze je volat explicitně. Finalizační metoda pro instanci je vyvolána automaticky během uvolňování paměti. Další podrobnosti najdete v článku o [finalizační metody](../programming-guide/classes-and-structs/destructors.md).

Uvolňování paměti je povolená rozsáhlá Zeměpisná šířka při rozhodování o shromažďování objektů a spouštění finalizační metody. Konkrétně časování volání finalizační metody není deterministické a finalizační metody mohou být provedeny v jakémkoli vlákně. Z těchto a dalších důvodů by třídy měly implementovat finalizační metody pouze v případě, že žádná jiná řešení nejsou proveditelná.

`using`Příkaz poskytuje lepší přístup k zničení objektu.

## <a name="expressions"></a>Výrazy

*Výrazy* jsou vytvořené z *operandů* a *operátorů*. Operátory výrazu označují, které operace se mají použít u operandů. Příklady operátorů zahrnují `+` , `-` ,, a `*` `/` `new` . Příklady operandů zahrnují literály, pole, místní proměnné a výrazy.

Pokud výraz obsahuje více operátorů, jejich *priorita* určuje pořadí, ve kterém jsou jednotlivé operátory vyhodnocovány. Například výraz `x + y * z` je vyhodnocen jako, `x + (y * z)` protože `*` operátor má vyšší prioritu než `+` operátor.

Když dojde k operandu mezi dvěma operátory se stejnou prioritou, *asociativita* operátor řídí pořadí, ve kterém jsou operace prováděny:

* S výjimkou operátorů přiřazení a slučování s hodnotou null jsou všechny binární operátory *asociativní*, což znamená, že operace jsou prováděny zleva doprava. Například `x + y + z` je vyhodnocen jako `(x + y) + z` .
* Operátory přiřazení, sloučení hodnoty null `??` a `??=` operátory a podmíněný operátor `?:` jsou *asociativní zprava*, což znamená, že operace jsou prováděny zprava doleva. Například `x = y = z` je vyhodnocen jako `x = (y = z)` .

Priority a asociativita lze ovládat pomocí závorek. Například `x + y * z` první vynásobí `y` `z` a poté přidá výsledek do `x` , ale `(x + y) * z` nejprve přidá `x` a `y` a pak vynásobí výsledek hodnotou `z` .

Většina operátorů může být [*přetížená*](../language-reference/operators/operator-overloading.md). Přetížení operátoru umožňuje zadat uživatelsky definované implementace operátorů pro operace, u nichž jeden nebo oba operandy jsou uživatelsky definovaný typ třídy nebo struktury.

Jazyk C# poskytuje řadu operátorů pro provádění [aritmetických](../language-reference/operators/arithmetic-operators.md)operací, [logických](../language-reference/operators/boolean-logical-operators.md), [bitových a posunutí](../language-reference/operators/bitwise-and-shift-operators.md) a porovnávání [rovnosti](../language-reference/operators/equality-operators.md) a [pořadí](../language-reference/operators/comparison-operators.md) .

Úplný seznam operátorů jazyka C# seřazených podle priority úrovně naleznete v tématu [operátory jazyka c#](../language-reference/operators/index.md).

## <a name="statements"></a>Příkazy

Akce programu jsou vyjádřeny pomocí *příkazů*. Jazyk C# podporuje několik různých druhů příkazů, jejichž počet je definován z podmínek vložených příkazů.

- *Blok* povoluje zápis více příkazů v kontextech, kde je povolen jediný příkaz. Blok obsahuje seznam příkazů zapsaných mezi oddělovači `{` a `}` .
- *Příkazy deklarace* slouží k deklaraci lokálních proměnných a konstant.
- *Příkazy výrazů* se používají k vyhodnocení výrazů. Výrazy, které lze použít jako příkazy, zahrnují vyvolání metod, přidělení objektů pomocí `new` operátoru, přiřazení pomocí `=` a operátory přiřazení, zvýšení a snížení pomocí operátorů a `++` `--` a `await` výrazů.
- *Příkazy výběru* se používají k výběru jednoho z několika možných příkazů pro spuštění na základě hodnoty nějakého výrazu. Tato skupina obsahuje `if` příkazy a `switch` .
- *Příkazy iterace* se používají ke opakovanému provedení vloženého příkazu. Tato skupina obsahuje `while` příkazy, `do` , `for` a `foreach` .
- *Příkazy skoku* slouží k přenosu ovládacího prvku. Tato skupina obsahuje `break` příkazy, `continue` , `goto` , `throw` , `return` a `yield` .
- `try`Příkaz... slouží `catch` k zachycení výjimek, ke kterým dojde během provádění bloku, a `try` příkaz... `finally` slouží k určení konečného kódu, který je vždy spuštěn, bez ohledu na to, zda došlo k výjimce nebo nikoli.
- `checked`Příkazy a `unchecked` slouží k řízení kontextu kontroly přetečení pro aritmetické operace a převody integrálního typu.
- `lock`Příkaz slouží k získání zámku vzájemného vyloučení pro daný objekt, spuštění příkazu a uvolnění zámku.
- `using`Příkaz slouží k získání prostředku, spuštění příkazu a následnému uvolnění tohoto prostředku.

Následující seznam uvádí typy příkazů, které lze použít:

* Místní deklarace proměnné
* Deklarace místní konstanty
* Příkaz výrazu.
* `if` vydá.
* `switch` vydá.
* `while` vydá.
* `do` vydá.
* `for` vydá.
* `foreach` vydá.
* `break` vydá.
* `continue` vydá.
* `goto` vydá.
* `return` vydá.
* `yield` vydá.
* `throw` příkazy a `try` příkazy.
* `checked``unchecked`příkazy a.
* `lock` vydá.
* `using` vydá.

>[!div class="step-by-step"]
>[Předchozí](types.md) 
> [Další](features.md)
