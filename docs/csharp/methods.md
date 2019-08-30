---
title: Metody – C# Průvodce
description: Přehled metod, parametrů metod a návratových hodnot metody
author: rpetrusha
ms.author: ronpet
ms.date: 05/21/2018
ms.assetid: 577a8527-1081-4b36-9b9e-0685b6553c6e
ms.openlocfilehash: b95818e06d37b0e98bf55428ff97dd476f92fac7
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168516"
---
# <a name="methods"></a>Metody

Metoda je blok kódu, který obsahuje řadu příkazů. Program způsobí, že budou příkazy provedeny voláním metody a zadáním požadovaných argumentů metody. V C#je každá spuštěná instrukce provedena v kontextu metody. Metoda je vstupním bodem pro každou C# aplikaci a je volána modulem CLR (Common Language Runtime) při spuštění programu. `Main`

> [!NOTE]
> Toto téma popisuje pojmenované metody. Informace o anonymních funkcích naleznete v tématu [Anonymous Functions](programming-guide/statements-expressions-operators/anonymous-functions.md).

Toto téma obsahuje následující oddíly:

- [Signatury metod](#signatures)
- [Vyvolání metody](#invocation)
- [Zděděné a přepsané metody](#inherited)
- [Předávání parametrů](#passing)
  - [Předávání parametrů podle hodnoty](#byval)
  - [Předávání parametrů odkazem](#byref)
  - [Pole parametrů](#paramarray)
- [Volitelné parametry a argumenty](#optional)
- [Návratové hodnoty](#return)
- [Metody rozšíření](#extension)
- [Asynchronní metody](#async)
- [Členové tvoření výrazy](#expr)
- [Iterátory](#iterators)

<a name="signatures"></a>

## <a name="method-signatures"></a>Signatury metod

Metody jsou deklarovány v `class` nebo `struct` zadáním:

- Volitelná úroveň přístupu, například `public` nebo. `private` Výchozí hodnota je `private`.
- Volitelné modifikátory, například `abstract` nebo `sealed`.
- Návratová hodnota, nebo `void` Pokud metoda nemá žádný.
- Název metody.
- Jakékoli parametry metody. Parametry metody jsou uzavřeny v závorkách a jsou odděleny čárkami. Prázdné kulaté závorky označují, že metoda nepožaduje žádné parametry.

Tyto části dohromady tvoří signaturu metody.

> [!NOTE]
> Návratový typ metody není součástí signatury metody pro účely přetěžování metody. Je však součástí signatury metody při určování kompatibility mezi delegátem a metodou, na kterou odkazuje.

Následující příklad definuje třídu s názvem `Motorcycle` , která obsahuje pět metod:

[!code-csharp[csSnippets.Methods#40](../../samples/snippets/csharp/concepts/methods/methods40.cs#40)]

Všimněte si, `Motorcycle` že třída obsahuje přetíženou `Drive`metodu. Dvě metody mají stejný název, ale musí být odlišeny jejich typy parametrů.

<a name="invocation"></a>

## <a name="method-invocation"></a>Vyvolání metody

Metody mohou být buď *instance* , nebo *statické*. Vyvolání metody instance vyžaduje vytvoření instance objektu a volání metody v tomto objektu. Metoda instance pracuje s touto instancí a jejími daty. Vyvoláte statickou metodu odkazem na název typu, ke kterému patří metoda; statické metody nepracují s daty instance. Pokus o volání statické metody prostřednictvím instance objektu vygeneruje chybu kompilátoru.

Volání metody je například přístup k poli. Za název objektu (Pokud voláte metodu instance) nebo název typu (Pokud voláte `static` metodu), přidejte tečku, název metody a závorky. Argumenty jsou uvedeny v závorkách a jsou odděleny čárkami.

Definice metody určuje názvy a typy parametrů, které jsou požadovány. Když volající vyvolá metodu, poskytne konkrétní hodnoty nazvané argumenty pro každý parametr. Argumenty musí být kompatibilní s typem parametru, ale název argumentu, pokud je jeden použit v volajícím kódu, nemusí být stejný jako parametr s názvem definovaným v metodě. V následujícím příkladu `Square` metoda zahrnuje jeden parametr typu `int` s názvem *i*. První volání metody předá `Square` metodu proměnné typu `int` s názvem *NUM*; Second, číselnou konstantou a třetí výrazem.

[!code-csharp[csSnippets.Methods#74](../../samples/snippets/csharp/concepts/methods/params74.cs#74)]

Nejběžnější forma volání metody použila Poziční argumenty; dodává argumenty ve stejném pořadí jako parametry metody. Metody `Motorcycle` třídy lze proto volat jako v následujícím příkladu. Volání `Drive` metody, například obsahuje dva argumenty, které odpovídají dvěma parametrům v syntaxi metody. První se zobrazí jako hodnota `miles` parametru, druhá hodnota `speed` parametru.

[!code-csharp[csSnippets.Methods#41](../../samples/snippets/csharp/concepts/methods/methods40.cs#41)]

Při vyvolání metody lze také použít *pojmenované argumenty* namísto pozičních argumentů. Při použití pojmenovaných argumentů zadáte název parametru následovaný dvojtečkou (":") a argumentem. Argumenty metody mohou být zobrazeny v libovolném pořadí, pokud jsou k dispozici všechny požadované argumenty. Následující příklad používá pojmenované argumenty pro vyvolání `TestMotorcycle.Drive` metody. V tomto příkladu jsou pojmenované argumenty předány v opačném pořadí ze seznamu parametrů metody.

[!code-csharp[csSnippets.Methods#45](../../samples/snippets/csharp/concepts/methods/named1.cs#45)]

Metodu lze vyvolat pomocí pozičních argumentů i pojmenovaných argumentů. Poziční argument však nemůže následovat za pojmenovaným argumentem. Následující příklad vyvolá `TestMotorcycle.Drive` metodu z předchozího příkladu pomocí jednoho pozičního argumentu a jednoho pojmenovaného argumentu.

[!code-csharp[csSnippets.Methods#46](../../samples/snippets/csharp/concepts/methods/named2.cs#46)]

<a name="inherited"></a>

## <a name="inherited-and-overridden-methods"></a>Zděděné a přepsané metody

Kromě členů, které jsou explicitně definovány v typu, dědí typ členy definované v jeho základních třídách. Vzhledem k <xref:System.Object> tomu, že všechny typy v systému spravovaného typu dědí přímo nebo nepřímo z třídy, všechny typy dědí své členy <xref:System.Object.Equals(System.Object)>, <xref:System.Object.GetType>například, <xref:System.Object.ToString>a. Následující příklad definuje `Person` třídu, vytvoří instanci dvou `Person` `Person.Equals` objektů a zavolá metodu pro určení, zda jsou dva objekty stejné. Metoda však není definována `Person` ve třídě. je zděděna z <xref:System.Object>. `Equals`

[!code-csharp[csSnippets.Methods#104](../../samples/snippets/csharp/concepts/methods/inherited1.cs#104)]

Typy mohou přepsat zděděné členy pomocí `override` klíčového slova a poskytnutím implementace pro potlačenou metodu. Signatura metody musí být stejná jako u přepsané metody. Následující příklad je podobný předchozímu, s tím rozdílem, že Přepisuje <xref:System.Object.Equals(System.Object)> metodu. (Také přepisuje <xref:System.Object.GetHashCode> metodu, protože tyto dvě metody jsou určeny k zajištění konzistentních výsledků.)

[!code-csharp[csSnippets.Methods#105](../../samples/snippets/csharp/concepts/methods/overridden1.cs#105)]

<a name="passing"></a>

## <a name="passing-parameters"></a>Předávání parametrů

Typy v C# jsou buď *typy hodnot* nebo typy *odkazů*. Seznam předdefinovaných hodnotových typů naleznete v tématu [typy a proměnné](./tour-of-csharp/types-and-variables.md). Ve výchozím nastavení jsou typy hodnot a odkazové typy předány metodě podle hodnoty.

<a name="byval"></a>

### <a name="passing-parameters-by-value"></a>Předávání parametrů podle hodnoty

Když je typ hodnoty předán metodě podle hodnoty, kopie objektu namísto samotného objektu je předána metodě. Proto změny objektu v volané metodě nemají žádný vliv na původní objekt, když se ovládací prvek vrátí volajícímu.

Následující příklad předává typ hodnoty metodě podle hodnoty a volaná metoda se pokusí změnit hodnotu typu hodnoty. Definuje proměnnou typu `int`, což je hodnotový typ, inicializuje hodnotu na 20 a předá ji metodě s názvem `ModifyValue` , která změní hodnotu proměnné na 30. Když se metoda vrátí, hodnota proměnné ale zůstane beze změny.

[!code-csharp[csSnippets.Methods#10](../../samples/snippets/csharp/concepts/methods/byvalue10.cs#10)]

Když je objekt typu odkazu předán metodě podle hodnoty, odkaz na objekt je předán podle hodnoty. To znamená, že metoda nepřijímá samotný objekt, ale argument, který označuje umístění objektu. Pokud změníte člena objektu pomocí tohoto odkazu, změna se projeví v objektu, když se ovládací prvek vrátí volající metodě. Nahrazení objektu předaného metodě ale nemá žádný vliv na původní objekt, když se ovládací prvek vrátí volajícímu.

Následující příklad definuje třídu (což je odkazový typ) s názvem `SampleRefType`. Vytvoří instanci `SampleRefType` objektu, přiřadí 44 k příslušnému `value` poli a `ModifyObject` předá objekt metodě. V tomto příkladu je totéž jako v předchozím příkladu – předává argument podle hodnoty metodě. Protože je však použit typ odkazu, výsledek je jiný. Změny `ModifyObject` provedené v `value` politaké`rt` změní`Main` pole argumentu v metodě na 33, jak ukazuje výstup z příkladu. `obj.value`

[!code-csharp[csSnippets.Methods#42](../../samples/snippets/csharp/concepts/methods/byvalue42.cs#42)]

<a name="byref"></a>

### <a name="passing-parameters-by-reference"></a>Předávání parametrů odkazem

Parametr předáte odkazem, pokud chcete změnit hodnotu argumentu v metodě a chcete tuto změnu odrážet, když se ovládací prvek vrátí volající metodě. Chcete-li předat parametr odkazem, použijte [`ref`](language-reference/keywords/ref.md) klíčové slovo or. [`out`](language-reference/keywords/out-parameter-modifier.md) Můžete také předat hodnotu odkazem, aby nedocházelo ke kopírování, ale stále nebránili úpravám pomocí [`in`](language-reference/keywords/in-parameter-modifier.md) klíčového slova.

Následující příklad je stejný jako předchozí, s výjimkou, že hodnota je předána odkazem na `ModifyValue` metodu. Když je v `ModifyValue` metodě upravena hodnota parametru, změna hodnoty se projeví, když se ovládací prvek vrátí volajícímu.

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/byref106.cs#106)]

Společný vzor, který používá parametry ref, zahrnuje Záměna hodnot proměnných. Pomocí odkazu předáte do metody dvě proměnné a metoda zamění jejich obsah. Následující příklad odměňuje celočíselné hodnoty.

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/swap107.cs#107)]

Předání parametru referenčního typu umožňuje změnit hodnotu samotného odkazu, nikoli hodnotu jeho jednotlivých prvků nebo polí.

<a name="paramarray"></a>

### <a name="parameter-arrays"></a>Pole parametrů

V některých případech je požadavek, který určíte přesný počet argumentů pro metodu, omezující. Pomocí `params` klíčového slova k označení, že parametr je pole parametrů, umožníte volání metody s proměnným počtem argumentů. Parametr označený `params` klíčovým slovem musí být typu pole a musí být posledním parametrem v seznamu parametrů metody.

Volající pak může metodu vyvolat jedním ze tří způsobů:

- Předáním pole vhodného typu, který obsahuje požadovaný počet prvků.
- Předáním čárkami odděleného seznamu jednotlivých argumentů příslušného typu metodě.
- Neposkytnutím argumentu pro pole parametrů.

Následující příklad definuje metodu s názvem `GetVowels` , která vrátí všechny samohlásky z pole parametrů. `Main` Metoda znázorňuje všechny tři způsoby volání metody. Volající nejsou vyžadováni k zadání argumentů pro parametry, které obsahují `params` modifikátor. V takovém případě je `null`parametr.

[!code-csharp[csSnippets.Methods#75](~/samples/snippets/csharp/concepts/methods/params75.cs#75)]

<a name="optional"></a>

## <a name="optional-parameters-and-arguments"></a>Volitelné parametry a argumenty

Definice metody může určovat, že jeho parametry jsou povinné nebo jsou nepovinné. Ve výchozím nastavení jsou vyžadovány parametry. Volitelné parametry jsou určeny zahrnutím výchozí hodnoty parametru v definici metody. Pokud je metoda volána, pokud není zadán žádný argument pro volitelný parametr, je místo toho použita výchozí hodnota.

Výchozí hodnota parametru musí být přiřazena jedním z následujících typů výrazů:

- Konstanta, jako je například řetězcový literál nebo číslo.
- Výraz formuláře `new ValType`, kde `ValType` je hodnotový typ. Všimněte si, že tato hodnota vyvolá implicitní konstruktor bez parametrů, který není skutečným členem tohoto typu.
- Výraz formuláře `default(ValType)`, kde `ValType` je hodnotový typ.

Pokud metoda zahrnuje vyžadované i volitelné parametry, jsou nepovinné parametry definovány na konci seznamu parametrů po všech požadovaných parametrech.

Následující příklad definuje metodu `ExampleMethod`, která má jeden požadovaný a dva volitelné parametry.

[!code-csharp[csSnippets.Methods#21](../../samples/snippets/csharp/concepts/methods/optional1.cs#21)]

Pokud je metoda s více volitelnými argumenty vyvolána pomocí pozičních argumentů, volající musí zadat argument pro všechny volitelné parametry od prvního do posledního, pro který je zadán argument. V případě `ExampleMethod` metody, například pokud volající zadá argument `description` pro parametr, musí `optionalInt` také dodat jednu pro parametr. `opt.ExampleMethod(2, 2, "Addition of 2 and 2");`je platné volání metody; `opt.ExampleMethod(2, , "Addition of 2 and 0");` vygeneruje chybu kompilátoru "chybí argument".

Pokud je metoda volána pomocí pojmenovaných argumentů nebo kombinace pozičních a pojmenovaných argumentů, volající může vynechat všechny argumenty, které následují jako poslední poziční argument ve volání metody.

Následující příklad volá `ExampleMethod` metodu třikrát.  První dvě volání metody používají Poziční argumenty. První vynechá jak nepovinné argumenty, zatímco druhá vynechává poslední argument. Třetí metoda volá poziční argument pro požadovaný parametr, ale používá pojmenovaný argument k zadání hodnoty `description` parametru při vynechání `optionalInt` argumentu.

[!code-csharp[csSnippets.Methods#22](../../samples/snippets/csharp/concepts/methods/optional1.cs#22)]

Použití volitelných parametrů má vliv na *rozlišení přetěžování*nebo způsob, jakým C# kompilátor určuje, které konkrétní přetížení by mělo být vyvoláno voláním metody, následovně:

- Metoda, indexer nebo konstruktor je kandidátem na provedení, pokud jsou jednotlivé parametry buď volitelné, nebo odpovídají, podle názvu nebo podle pozice, k jednomu argumentu v příkazu volání a tento argument lze převést na typ parametru.
- Pokud je nalezen více než jeden kandidát, budou pravidla rozlišení přetížení pro preferované převody použita na argumenty, které jsou explicitně určeny. Vynechané argumenty pro volitelné parametry jsou ignorovány.
- Pokud jsou dva kandidáty odůvodněné stejně dobré, preference směřuje k kandidátovi, který nemá nepovinné parametry pro to, které argumenty byly ve volání vynechány. Jedná se o důsledek Obecné předvolby v řešení přetížení pro kandidáty, které mají méně parametrů.

<a name="return"></a>

## <a name="return-values"></a>Vrácené hodnoty

Metody mohou vracet hodnotu volajícímu. Pokud návratový typ (typ uvedený před názvem metody) `void`není, metoda může vracet hodnotu `return` pomocí klíčového slova. Příkaz s `return` klíčovým slovem následovaným proměnnou, konstantou nebo výrazem, který odpovídá typu vrácené hodnoty, vrátí tuto hodnotu volajícímu metody. Metody s návratovým typem, který není typu void, jsou vyžadovány k použití `return` klíčového slova k vrácení hodnoty. `return` Klíčové slovo také zastaví provádění metody.

Pokud je `void`návratový typ `return` , příkaz bez hodnoty je stále užitečný k zastavení provádění metody. `return` Bez klíčového slova, Metoda zastaví provádění, když dosáhne konce bloku kódu.

Například tyto dvě metody používají `return` klíčové slovo k vrácení celých čísel:

[!code-csharp[csSnippets.Methods#44](../../samples/snippets/csharp/concepts/methods/return44.cs#44)]

Chcete-li použít hodnotu vrácenou metodou, volající metoda může použít samotné volání metody kdekoli kdekoliv, kde bude stačit hodnota stejného typu. Vrácenou hodnotu můžete také přiřadit proměnné. Například následující dva příklady kódu mají stejný cíl:

[!code-csharp[csSnippets.Methods#45](../../samples/snippets/csharp/concepts/methods/return44.cs#45)]

[!code-csharp[csSnippets.Methods#46](../../samples/snippets/csharp/concepts/methods/return44.cs#46)]

Použití místní proměnné v tomto případě `result`pro uložení hodnoty je volitelné. Může to usnadnit čitelnost kódu nebo může být nutné, pokud potřebujete uložit původní hodnotu argumentu pro celý rozsah metody.

V některých případech budete chtít, aby metoda vracela více než jednu hodnotu. Počínaje C# 7,0 můžete to provést snadno pomocí *typů řazené kolekce členů* a *literálů řazené kolekce členů*. Typ řazené kolekce členů definuje datové typy elementů řazené kolekce členů. Literály řazené kolekce členů poskytují skutečné hodnoty vrácených řazené kolekce členů. V následujícím příkladu `(string, string, string, int)` definuje typ řazené kolekce členů, který je vrácen `GetPersonalInfo` metodou. Výraz `(per.FirstName, per.MiddleName, per.LastName, per.Age)` je literál řazené kolekce členů; metoda vrátí první, střední a poslední název spolu s stářím `PersonInfo` objektu.

```csharp
public (string, string, string, int) GetPersonalInfo(string id)
{
    PersonInfo per = PersonInfo.RetrieveInfoById(id);
    return (per.FirstName, per.MiddleName, per.LastName, per.Age);
}
```

Volající pak může využít vrácenou řazenou kolekci členů s kódem podobným následujícímu:

```csharp
var person = GetPersonalInfo("111111111")
Console.WriteLine("{person.Item1} {person.Item3}: age = {person.Item4}");
```

Názvy lze také přiřadit prvkům řazené kolekce členů v definici typu řazené kolekce členů. Následující příklad ukazuje alternativní verzi `GetPersonalInfo` metody, která používá pojmenované prvky:

```csharp
public (string FName, string MName, string LName, int Age) GetPersonalInfo(string id)
{
    PersonInfo per = PersonInfo.RetrieveInfoById(id);
    return (per.FirstName, per.MiddleName, per.LastName, per.Age);
}
```

Předchozí volání `GetPersonInfo` metody lze upravit následujícím způsobem:

```csharp
var person = GetPersonalInfo("111111111");
Console.WriteLine("{person.FName} {person.LName}: age = {person.Age}");
```

Pokud je metoda předána poli jako argument a upravuje hodnotu jednotlivých prvků, není nutné, aby metoda vracela pole, i když se můžete rozhodnout pro dobrý styl nebo funkční tok hodnot.  Důvodem je, C# že předává všechny typy odkazů podle hodnoty a hodnota odkazu na pole je ukazatel na pole. V následujícím příkladu jsou změny obsahu `values` pole, které je provedeno `DoubleValues` v metodě, pozorovatelný jakýmkoli kódem, který má odkaz na pole.

[!code-csharp[csSnippets.Methods#101](../../samples/snippets/csharp/concepts/methods/returnarray1.cs#101)]

<a name="extension"></a>

## <a name="extension-methods"></a>Metody rozšíření

Obvykle existují dva způsoby, jak přidat metodu do existujícího typu:

- Upravte zdrojový kód pro daný typ. Nemůžete to provést, Pokud nevlastníte zdrojový kód typu. A tato změna se změní i v případě, že přidáte jakákoli soukromá datová pole, která by podporovala metodu.
- Definujte novou metodu v odvozené třídě. Metodu nelze přidat tímto způsobem pomocí dědičnosti pro jiné typy, jako jsou například struktury a výčty. Ani jej nelze použít pro přidání metody do zapečetěné třídy.

Metody rozšíření umožňují přidat metodu do existujícího typu bez změny samotného typu nebo implementací nové metody ve zděděném typu. Metoda rozšíření také nemusí být umístěna ve stejném sestavení jako typ, který rozšiřuje. Zavoláte metodu rozšíření, jako by šlo o definovaného člena typu.

Další informace naleznete v tématu [metody rozšíření](programming-guide/classes-and-structs/extension-methods.md).

<a name="async"></a>

## <a name="async-methods"></a>Asynchronní metody

Pomocí asynchronní funkce můžete vyvolat asynchronní metody bez použití explicitních zpětných volání nebo ruční rozdělení kódu napříč více metodami nebo lambda výrazy.

Pokud označíte metodu pomocí modifikátoru [Async](language-reference/keywords/async.md) , můžete použít operátor [await](language-reference/operators/await.md) v metodě. Když ovládací prvek dosáhne `await` výrazu v asynchronní metodě, ovládací prvek se vrátí volajícímu, pokud se očekávaný úkol nedokončil a průběh metody `await` s klíčovým slovem je pozastaven až do dokončení očekávané úlohy. Po dokončení úlohy může provádění pokračovat v metodě.

> [!NOTE]
> Asynchronní metoda se vrátí volajícímu, když dojde k prvnímu očekávanému objektu, který ještě nebyl dokončen, nebo získá na konec asynchronní metody, podle toho, co nastane dříve.

Asynchronní metoda může mít návratový typ <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>nebo `void`. Návratový typ se používá primárně k definování obslužných rutin událostí, `void` kde je požadován návratový typ. `void` Asynchronní metoda, která se `void` vrátí, nemůže být očekávána a volající metody vracející typ void nemůže zachytit výjimky, které metoda vyvolá. Počínaje C# 7,0 může asynchronní metoda mít [jakýkoli návratový typ podobný tomuto úkolu](./whats-new/csharp-7.md#generalized-async-return-types).

V následujícím příkladu `DelayAsync` je asynchronní metoda, která má návratový příkaz, který vrací celé číslo. Vzhledem k tomu, že se jedná o asynchronní metodu, její deklarace metody musí mít `Task<int>`návratový typ. Vzhledem k tomu, že `Task<int>`návratový typ je, vyhodnocení `await` výrazu v `DoSomethingAsync` vytvoří celé číslo, jak ukazuje následující `int result = await delayTask` příkaz.

[!code-csharp[csSnippets.Methods#102](../../samples/snippets/csharp/concepts/methods/async1.cs#102)]

Asynchronní metoda nemůže deklarovat jakýkoli parametr [in](language-reference/keywords/in-parameter-modifier.md), [ref](language-reference/keywords/ref.md)nebo [out](language-reference/keywords/out-parameter-modifier.md) , ale může volat metody, které mají tyto parametry.

 Další informace o asynchronních metodách naleznete v tématu [asynchronní programování s Async a await](async.md), [řízení toku v asynchronních programech](programming-guide/concepts/async/control-flow-in-async-programs.md)a [Asynchronní návratové typy](programming-guide/concepts/async/async-return-types.md).

<a name="expr"></a>

## <a name="expression-bodied-members"></a>Členové tvoření výrazy

Je běžné mít definice metod, které se jednoduše vrátí s výsledkem výrazu nebo které mají jediný příkaz jako tělo metody.  Pro definování takových metod je k dispozici zástupce syntaxe `=>`pomocí příkazu:

```csharp
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);
public void Print() => Console.WriteLine(First + " " + Last);
// Works with operators, properties, and indexers too.
public static Complex operator +(Complex a, Complex b) => a.Add(b);
public string Name => First + " " + Last;
public Customer this[long id] => store.LookupCustomer(id);
```

Pokud metoda vrátí `void` nebo je asynchronní metodou, tělo metody musí být výraz příkazu (totéž jako u výrazů lambda).  U vlastností a indexerů musí být jen pro čtení a nepoužívejte klíčové slovo přistupující k `get` objektu.

<a name="iterators"></a>

## <a name="iterators"></a>Iterátory

Iterátor provádí vlastní iteraci v kolekci, jako je například seznam nebo pole. Iterátor používá příkaz [yield return](language-reference/keywords/yield.md) k vrácení každého elementu v jednom okamžiku. Při dosažení `yield return` příkazu je aktuální umístění zapamatovatelné, aby volající mohl požádat o další prvek v sekvenci.

Návratový typ <xref:System.Collections.IEnumerable>iterátoru může být, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>nebo <xref:System.Collections.Generic.IEnumerator%601>.

Další informace najdete v tématu [iterátory](programming-guide/concepts/iterators.md).

## <a name="see-also"></a>Viz také:

- [Modifikátory přístupu](language-reference/keywords/access-modifiers.md)
- [Statické třídy a jejich členové](programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [Dědičnost](programming-guide/classes-and-structs/inheritance.md)
- [Abstraktní a uzavřené třídy a jejich členové](programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [params](language-reference/keywords/params.md)
- [out](language-reference/keywords/out-parameter-modifier.md)
- [ref](language-reference/keywords/ref.md)
- [in](language-reference/keywords/in-parameter-modifier.md)
- [Předávání parametrů](programming-guide/classes-and-structs/passing-parameters.md)
