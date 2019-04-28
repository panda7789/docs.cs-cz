---
title: Metody – Průvodce v C#
description: Přehled metody, metoda parametry a návratové hodnoty metod
author: rpetrusha
ms.author: ronpet
ms.date: 05/21/2018
ms.assetid: 577a8527-1081-4b36-9b9e-0685b6553c6e
ms.openlocfilehash: 54657fb8ed4c0935c7c21fad333c7a62b42aec2e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61688264"
---
# <a name="methods"></a>Metody

Metoda je blok kódu, který obsahuje řadu příkazů. Program způsobí, že příkazů ke spuštění volání metody a zadáním argumentů požadovanou metodu. V jazyce C# se provádí každých provedené instrukce v rámci metody. `Main` Metoda je vstupní bod pro každou aplikaci C# a je volána modulem common language runtime (CLR), když se program spustí.

> [!NOTE]
> Toto téma popisuje pojmenované metody. Informace o anonymní funkce, najdete v části [anonymní funkce](programming-guide/statements-expressions-operators/anonymous-functions.md).

Toto téma obsahuje následující oddíly:

- [Podpisy metod](#signatures)
- [Volání metody](#invocation)
- [Zděděné a přepsané metody](#inherited)
- [Předávání parametrů](#passing)
  - [Předávání parametrů podle hodnoty](#byval)
  - [Předávání parametrů odkazem.](#byref)
  - [Pole parametrů](#paramarray)
- [Volitelné parametry a argumenty](#optional)
- [Návratové hodnoty](#return)
- [Rozšiřující metody](#extension)
- [Asynchronní metody](#async)
- [Členové tvoření výrazy](#expr)
- [Iterátory](#iterators)

<a name="signatures"></a>

## <a name="method-signatures"></a>Podpisy metod

Metody jsou deklarovány v `class` nebo `struct` zadáním:

- Volitelný přístup na úrovni, jako například `public` nebo `private`. Výchozí hodnota je `private`.
- Volitelné modifikátory jako `abstract` nebo `sealed`.
- Návratová hodnota nebo `void` Pokud metoda nemá žádný.
- Název metody.
- Všechny parametry metody. Parametry metody jsou uzavřeny v závorkách a odděleny čárkami. Prázdných kulatých závorek znamenat, že metoda nevyžaduje žádné parametry.

Tyto části společně tvoří podpisu metody.

> [!NOTE]
> Návratový typ metody není součástí podpis metody pro účely přetížení metody. Je však součást podpisu metody při určování kompatibility mezi delegáta a, který odkazuje na metodu.

Následující příklad definuje třídu s názvem `Motorcycle` , která obsahuje pět metod:

[!code-csharp[csSnippets.Methods#40](../../samples/snippets/csharp/concepts/methods/methods40.cs#40)]

Všimněte si, `Motorcycle` třída zahrnuje přetěžované metody, `Drive`. Dvě metody se stejným názvem, ale musí být rozlišené pomocí jejich typy parametrů.

<a name="invocation"></a>

## <a name="method-invocation"></a>Volání metody

Metody mohou být buď *instance* nebo *statické*. Volání metody instance vyžaduje vytvoření instance objektu a volat metodu na objektu. Metoda instance pracuje na tuto instanci a jeho data. Volání statické metody pomocí odkazu na název typu, do kterého metoda patří; statické metody se nevztahují na instance data. Pokus o volání statické metody instancí objektu generuje chybu kompilátoru.

Volání metody je například přístup k poli. Po názvu objektu (Pokud voláte metodu instance) nebo název typu (při volání `static` metoda), přidejte tečku, názvu metody a závorky. Argumenty jsou uvedeny v závorkách a odděleny čárkami.

Definice metody určuje názvy a typy všech parametrů, které jsou požadovány. Když volající vyvolá metodu, poskytne konkrétní hodnoty, nazývaných argumenty pro každý parametr. Argumenty musí být kompatibilní s typem parametru, ale název argumentu, pokud se používá ve volajícím kódu, nemusí být stejné jako parametr s názvem definovaný v metodě. V následujícím příkladu `Square` metoda obsahuje jeden parametr typu `int` s názvem *můžu*. První metoda volání předá `Square` metody a proměnné typu `int` s názvem *num*; druhý, číselnou konstantu; a třetí, výraz.

[!code-csharp[csSnippets.Methods#74](../../samples/snippets/csharp/concepts/methods/params74.cs#74)]

Nejběžnější forma volání metody použít poziční argumenty; poskytne argumenty ve stejném pořadí jako parametry metod. Metody `Motorcycle` třídy proto lze volat jako v následujícím příkladu. Volání `Drive` metody, například obsahuje dva argumenty, které odpovídají na dva parametry syntaxe metody. První změní hodnotu `miles` parametr, druhá hodnota `speed` parametru.

[!code-csharp[csSnippets.Methods#41](../../samples/snippets/csharp/concepts/methods/methods40.cs#41)]

Můžete také použít *pojmenované argumenty* místo poziční argumenty při volání metody. Při použití pojmenované argumenty, zadejte název parametru, za nímž následuje dvojtečka (":") a argument. Argumenty metody se může zobrazit v libovolném pořadí, dokud nejsou všechny povinné argumenty. Následující příklad používá pojmenované argumenty k vyvolání `TestMotorcycle.Drive` metody. V tomto příkladu jsou pojmenované argumenty předány v opačném pořadí ze seznamu parametrů metody.

[!code-csharp[csSnippets.Methods#45](../../samples/snippets/csharp/concepts/methods/named1.cs#45)]

Můžete vyvolat metodu pomocí obou poziční argumenty a pojmenované argumenty. Ale poziční argument nemůže následovat za pojmenovaným argumentem. Následující příklad popisuje vyvolání `TestMotorcycle.Drive` metoda z předchozího příkladu pomocí jednoho poziční argument a jeden pojmenovaný argument.

[!code-csharp[csSnippets.Methods#46](../../samples/snippets/csharp/concepts/methods/named2.cs#46)]

<a name="inherited"></a>

## <a name="inherited-and-overridden-methods"></a>Zděděné a přepsané metody

Kromě členy, které jsou explicitně definovány v rámci typu Typ dědí členy definované v její základní třídy. Protože všechny typy v systému spravovaný typ dědí přímo nebo nepřímo <xref:System.Object> třídu, všechny typy dědit její členy jako <xref:System.Object.Equals(System.Object)>, <xref:System.Object.GetType>, a <xref:System.Object.ToString>. Následující příklad definuje `Person` třídy, vytvoří dvě `Person` objektů a volá `Person.Equals` metodou ke zjištění, zda dva objekty rovnají. `Equals` Metody, ale není definovaný v `Person` třída; je zděděno od <xref:System.Object>.

[!code-csharp[csSnippets.Methods#104](../../samples/snippets/csharp/concepts/methods/inherited1.cs#104)]

Typy lze přepsat pomocí zděděných členů `override` – klíčové slovo a zajistit pomocí implementace přepsané metody. Podpis metody musí být stejné jako u přepsané metody. Následující příklad je podobný předchozímu, s tím rozdílem, že přepíše <xref:System.Object.Equals(System.Object)> metody. (Přepíše také <xref:System.Object.GetHashCode> metody, protože tyto dvě metody jsou určená k zajištění konzistentní výsledky.)

[!code-csharp[csSnippets.Methods#105](../../samples/snippets/csharp/concepts/methods/overridden1.cs#105)]

<a name="passing"></a>

## <a name="passing-parameters"></a>Předávání parametrů

Typy v jazyce C# jsou buď *typů hodnot* nebo *referenční typy*. Seznam typů předdefinovaných hodnot najdete v tématu [typy a proměnné](./tour-of-csharp/types-and-variables.md). Ve výchozím nastavení typy hodnot a odkazové typy jsou předávány na metodu hodnotou.

<a name="byval"></a>

### <a name="passing-parameters-by-value"></a>Předávání parametrů podle hodnoty

Pokud typ hodnoty je předán do metody podle hodnoty, kopii objektu namísto objektu samotného je předán metodě. Proto změny objektu volané metody nemají žádný vliv na původní objekt, když ovládací prvek vrátí volajícímu.

Následující příklad předává typu hodnoty metodě podle hodnoty a volané metody se pokusí změnit hodnotu typu hodnoty. Definuje proměnnou typu `int`, které je typ hodnoty, inicializuje jeho hodnotu na 20 a předává je na metodu s názvem `ModifyValue` , která se změní hodnota proměnné na 30. Když metoda vrátí, ale hodnota proměnné zůstane beze změny.

[!code-csharp[csSnippets.Methods#10](../../samples/snippets/csharp/concepts/methods/byvalue10.cs#10)]

Pokud objekt typu odkazu je předán do metody podle hodnoty, odkaz na objekt je předán podle hodnoty. To znamená metoda obdrží, nikoli samotného objektu, ale argument, který označuje umístění objektu. Pokud změníte členem objektu pomocí tohoto odkazu, změna se projeví v objektu při vrácení ovládacího prvku k volání metody. Ale nahradit objekt předaný metodě nemá žádný vliv na původní objekt při ovládací prvek vrátí volajícímu.

Následující příklad definuje třídu (což je odkazový typ) s názvem `SampleRefType`. Vytvoření instance `SampleRefType` objektu, přiřadí 44 k jeho `value` pole a předá objekt, který má `ModifyObject` metoda. V tomto příkladu provede v podstatě totéž, jako předchozí příklad – předá argumentu podle hodnoty metody. Ale protože odkazový typ se používá, výsledek se liší. Úpravy, které se provádí v `ModifyObject` k `obj.value` pole také změny `value` pole argumentu `rt`v `Main` metoda 33, jak výstup z příkladu ukazuje.

[!code-csharp[csSnippets.Methods#42](../../samples/snippets/csharp/concepts/methods/byvalue42.cs#42)]

<a name="byref"></a>

### <a name="passing-parameters-by-reference"></a>Předávání parametrů odkazem.

Předávání parametru podle odkazu, pokud chcete změňte hodnotu argumentu v metodě a chcete, aby odrážela tuto změnu, když ovládací prvek vrátí volajícímu metody. Parametr předávání pomocí odkazu, použijte [ `ref` ](language-reference/keywords/ref.md) nebo [ `out` ](language-reference/keywords/out-parameter-modifier.md) – klíčové slovo. Můžete také předat hodnotu s odkazem na vyhnout kopírování, ale stále zabránit změny pomocí [ `in` ](language-reference/keywords/in-parameter-modifier.md) – klíčové slovo.

Následující příklad je stejný jako předchozímu, s tím rozdílem, hodnota je předán odkazem na `ModifyValue` metody. Při změně hodnoty parametru v `ModifyValue` metoda změnu v hodnotě se projeví, když ovládací prvek vrátí volajícímu.

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/byref106.cs#106)]

Běžným vzorem, který používá parametry ref zahrnuje prohození hodnoty proměnných. Dvě proměnné, které předáte metodě odkazem a metodu Zamění jejich obsah. Následující příklad zaměňuje celočíselné hodnoty.

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/swap107.cs#107)]

Předávání parametrů typu odkazu můžete změnit hodnotu referenční samotné, nikoli hodnotu jeho jednotlivé prvky nebo pole.

<a name="paramarray"></a>

### <a name="parameter-arrays"></a>Pole parametrů

V některých případech je omezující požadavek zadat přesný počet argumentů pro metodu. S použitím `params` – klíčové slovo k označení, že je parametr pole parametrů, povolíte metodu volat s proměnným počtem argumentů. Parametr označené `params` – klíčové slovo musí být typu pole a musí být posledním parametrem v seznamu parametrů metody.

Volající lze poté vyvolat metodu v jednom ze tří způsobů:

- Předáním pole příslušného typu, který obsahuje požadovaný počet prvků.
- Předáním čárkou oddělený seznam jednotlivé argumenty příslušného typu metody.
- Tak, že neposkytnete argument pole parametrů.

Následující příklad definuje metodu s názvem `DoStringOperation` , který provádí operace řetězců určené její první parametr `StringOperation` člena výčtu. Řetězce, na kterých je k provedení této operace jsou určené pole parametrů. `Main` Metoda ukazuje všechny tři způsoby volání metody. Všimněte si, že metoda označené `params` – klíčové slovo musí být připravena ke zpracování případu, ve kterém není zadaný žádný argument pro parametr pole, tak, aby její hodnota je `null`.

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/byref108.cs#108)]

<a name="optional"></a>

## <a name="optional-parameters-and-arguments"></a>Volitelné parametry a argumenty

Definice metody můžete určit, že její parametry jsou povinné a že jsou volitelné. Ve výchozím nastavení parametry jsou povinné. Volitelné parametry jsou určeny včetně výchozí hodnota parametru v definici metody. Při volání metody pro volitelný parametr není zadaný žádný argument, je použita výchozí hodnota.

Výchozí hodnota parametru musí mít přiřazenou pomocí jedné z následující typy výrazů:

- Toto je konstanta, třeba řetězec nebo číslo.
- Výraz ve tvaru `new ValType`, kde `ValType` je typ hodnoty. Všimněte si, že tím se vyvolá typ hodnoty implicitní konstruktor bez parametrů, která není skutečný člen daného typu.
- Výraz ve tvaru `default(ValType)`, kde `ValType` je typ hodnoty.

Pokud metoda obsahuje povinných a volitelných parametrů, volitelné parametry jsou definované na konci seznamu parametrů, až poté, co všechny požadované parametry.

Následující příklad definuje metodu, `ExampleMethod`, který má vyžadující jeden a dva volitelné parametry.

[!code-csharp[csSnippets.Methods#21](../../samples/snippets/csharp/concepts/methods/optional1.cs#21)]

Pokud metoda s více volitelných argumentů je vyvolán pomocí poziční argumenty, volající musí zadat argument pro všechny volitelné parametry z první z nich pro poslední, pro který je zadán argument. V případě třídy `ExampleMethod` metody, například, pokud volající poskytuje argument `description` parametr, je nutné také jednu třídu dodat pro `optionalInt` parametru. `opt.ExampleMethod(2, 2, "Addition of 2 and 2");` je platná metoda volání; `opt.ExampleMethod(2, , "Addition of 2 and 0");` generuje "chybí Argument." chybu kompilátoru.

Pokud je metoda volána pomocí pojmenovaných argumentů nebo ke kombinaci komponent poziční a pojmenované argumenty, volající vynechat žádné argumenty, které následují poslední poziční argument ve volání metody.

Následující příklad volá `ExampleMethod` metoda třikrát.  První dvě metody volání využívat poziční argumenty. První vynechá oba volitelné argumenty, zatímco druhý vynechá posledním argumentem. Třetí volání metody poskytuje poziční argument pro parametr povinný, ale používá pojmenovaný argument zadat hodnotu, která `description` parametr při vynechání `optionalInt` argument.

[!code-csharp[csSnippets.Methods#22](../../samples/snippets/csharp/concepts/methods/optional1.cs#22)]

Má vliv na použití volitelných parametrů *rozlišení přetěžování*, nebo způsob, ve kterém kompilátor jazyka C# určuje, které konkrétní přetížení má vyvolat volání metody, následujícím způsobem:

- Metoda, indexer nebo konstruktor je kandidátem pro spuštění, pokud každý ze svých parametrů je nepovinný nebo odpovídá podle názvu nebo podle pozice jediný argument ve volání příkazu, a že argument lze převést na typ parametru.
- Pokud je nalezen více než jeden Release candidate, pravidla rozlišení přetížení pro upřednostňované převody se aplikují na argumenty, které jsou explicitně zadány. Vynechaný argumenty pro volitelné parametry jsou ignorovány.
- Pokud dvě kandidáty jsou považovány za stejnou měrou bezproblémový, předvoleb přejde na Release candidate, který nemá žádné volitelné parametry, které byly vynechány argumenty ve volání. Toto je důsledkem obecné předvoleb v rozlišení přetížení pro kandidáty, které mají méně parametrů.

<a name="return"></a>

## <a name="return-values"></a>Vrácené hodnoty

Metody může vrátit hodnotu volajícímu. Pokud je návratový typ (typ uveden před název metody) `void`, metoda může vrátit hodnotu pomocí `return` – klíčové slovo. Příkaz s `return` – klíčové slovo následované proměnná, konstanta nebo výraz, který odpovídá návratový typ, vrátí tuto hodnotu volajícímu metody. Metody s jiný než void vrací typ jsou nutné k použití `return` – klíčové slovo vrátit hodnotu. `return` – Klíčové slovo také zastaví provádění metody.

Pokud je návratový typ `void`, `return` příkaz bez hodnoty je stále užitečná pro zastavení provádění metody. Bez `return` – klíčové slovo, metoda se zastaví provádění dosáhne konce bloku kódu.

Například tyto dvě metody použít `return` – klíčové slovo do vrací celá čísla:

[!code-csharp[csSnippets.Methods#44](../../samples/snippets/csharp/concepts/methods/return44.cs#44)]

Na používání hodnoty vrátil z metody, můžete použít volání metody volání metody samotný kdekoli, že by stačit hodnotu stejného typu. Můžete také přiřadit návratovou hodnotu proměnné. Například následující dva příklady provedení stejného cíle:

[!code-csharp[csSnippets.Methods#45](../../samples/snippets/csharp/concepts/methods/return44.cs#45)]

[!code-csharp[csSnippets.Methods#46](../../samples/snippets/csharp/concepts/methods/return44.cs#46)]

Použití místní proměnné, v tomto případě `result`pro ukládání hodnota je volitelná. To může pomoci čitelnost kódu nebo může být nezbytné, pokud je potřeba uložit původní hodnoty argumentu pro celý rozsah metody.

V některých případech budete chtít vaše metoda vrátit více než jednu hodnotu. Od verze C# 7.0, můžete tuto operaci provést snadno pomocí *typy řazené kolekce členů* a *literálech řazené kolekce členů*. Typ řazené kolekce členů definuje datové typy elementů řazené kolekce členů. Literálech řazené kolekce členů zadejte skutečné hodnoty vrácené řazené kolekce členů. V následujícím příkladu `(string, string, string, int)` definuje typ řazené kolekce členů, který je vrácený `GetPersonalInfo` metody. Výraz `(per.FirstName, per.MiddleName, per.LastName, per.Age)` řazené kolekce členů je literál; metoda vrátí název první a poslední spolu s věk, nástroje `PersonInfo` objektu.

```csharp
public (string, string, string, int) GetPersonalInfo(string id)
{
    PersonInfo per = PersonInfo.RetrieveInfoById(id);
    return (per.FirstName, per.MiddleName, per.LastName, per.Age);
}
```

Volající je pak mohou využívat vrácené řazené kolekce členů s kódem, jako je následující:

```csharp
var person = GetPersonalInfo("111111111")
Console.WriteLine("{person.Item1} {person.Item3}: age = {person.Item4}");
```

Lze také přiřadit názvy elementů řazené kolekce členů v definici typu řazené kolekce členů. Následující příklad ukazuje alternativní verze `GetPersonalInfo` metodu, která se používá s názvem prvky:

```csharp
public (string FName, string MName, string LName, int Age) GetPersonalInfo(string id)
{
    PersonInfo per = PersonInfo.RetrieveInfoById(id);
    return (per.FirstName, per.MiddleName, per.LastName, per.Age);
}
```

Předchozí volání `GetPersonInfo` metoda pak lze upravit následujícím způsobem:

```csharp
var person = GetPersonalInfo("111111111");
Console.WriteLine("{person.FName} {person.LName}: age = {person.Age}");
```

Pokud metoda pole je předán jako argument a změní hodnotu jednotlivých prvků, není nutné pro metodu vrátit pole, i když můžete k tomu dobrý styl nebo funkční toku hodnot.  Je to proto, že C# projde všechny typy odkazů podle hodnoty a odkazu na pole má hodnotu ukazatele na pole. V následujícím příkladu se změní na obsah `values` pole, které probíhají v `DoubleValues` metody jsou pozorovat podle veškerý kód, který obsahuje odkaz na pole.

[!code-csharp[csSnippets.Methods#101](../../samples/snippets/csharp/concepts/methods/returnarray1.cs#101)]

<a name="extension"></a>

## <a name="extension-methods"></a>Rozšiřující metody

Obvykle existují dva způsoby, jak přidat metodu k existujícímu typu:

- Upravte zdrojový kód tohoto typu. Nemůže to provedete, samozřejmě, pokud nejste vlastníkem tohoto typu zdrojového kódu. A to se stane rozbíjející změny, pokud je také přidat všechny privátní datová pole pro podporu metodu.
- Definujte novou metodu v odvozené třídě. Metodu nelze přidat tímto způsobem použití dědičnosti pro ostatní typy, jako je například struktury a výčty. Ani jej lze "Přidání" metodu pro zapečetěnou třídu.

Metody rozšíření umožňují "přidávat" metody do existujícího typu bez změny samotného typu nebo implementaci nová metoda ve zděděném typu. Metoda rozšíření také nemusí nacházet ve stejném sestavení, typ, který rozšiřuje. Rozšiřující metody volání, jako by šlo definovaný člen typu.

Další informace najdete v tématu [rozšiřující metody](programming-guide/classes-and-structs/extension-methods.md).

<a name="async"></a>

## <a name="async-methods"></a>Asynchronní metody

Při použití asynchronní funkce, se dají vyvolat asynchronní metody bez použití explicitní zpětná volání nebo Ruční rozdělení kódu mezi více metodách a výrazech lambda.

Pokud určíte metodu s [asynchronní](language-reference/keywords/async.md) modifikátor, můžete použít [await](language-reference/keywords/await.md) operátor v metodě. Když ovládací prvek dosáhne `await` výrazu v asynchronní metodě, ovládací prvek vrátí volajícímu, pokud není dokončen očekávaný úkol a průběh v metodě s `await` – klíčové slovo je pozastaveno, dokud nebude dokončen očekávaný úkol. Po dokončení úlohy se provádění může pokračovat v metodě.

> [!NOTE]
> Asynchronní metoda vrátí řízení volajícímu, když nalezne první očekávaný objekt, který ještě není dokončeno nebo získá konec asynchronní metody podle toho, co nastane dříve.

Asynchronní metoda může mít návratový typ <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, nebo `void`. `void` Typ vrácení se používá především k definování obslužných rutin událostí, kde `void` je požadován návratový typ. Asynchronní metody vracející `void` nemůže být očekávána a volající metody vracející typ void nemůže zachytit výjimky, které metoda vyvolá. Od verze C# 7.0, asynchronní metoda může mít [jakýkoli návratový typ takový](./whats-new/csharp-7.md#generalized-async-return-types).

V následujícím příkladu `DelayAsync` je asynchronní metoda, která má návratový příkaz, který vrátí celé číslo. Protože se jedná o asynchronní metodu, jeho deklarace metody musí mít typ vrácené hodnoty `Task<int>`. Vzhledem k tomu, že je návratový typ `Task<int>`, vyhodnocení `await` výrazu v `DoSomethingAsync` vytváří celého čísla, následujícím způsobem `int result = await delayTask` příkaz ukazuje.

[!code-csharp[csSnippets.Methods#102](../../samples/snippets/csharp/concepts/methods/async1.cs#102)]

Asynchronní metoda nemůže deklarovat všechny [v](language-reference/keywords/in-parameter-modifier.md), [ref](language-reference/keywords/ref.md), nebo [si](language-reference/keywords/out-parameter-modifier.md) parametry, ale může volat metody, které mají tyto parametry.

 Další informace o metodách async naleznete v tématu [Asynchronous Programming with Async and Await](async.md), [tok řízení v asynchronních programech](programming-guide/concepts/async/control-flow-in-async-programs.md), a [Async Return Types](programming-guide/concepts/async/async-return-types.md).

<a name="expr"></a>

## <a name="expression-bodied-members"></a>Členové tvoření výrazy

Je běžné mít definice metod, které jednoduše okamžitě vrátí výsledek výrazu nebo, které mají jeden příkaz jako tělo metody.  Existuje místní syntaxe pro definování těchto metod pomocí `=>`:

```csharp
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);
public void Print() => Console.WriteLine(First + " " + Last);
// Works with operators, properties, and indexers too.
public static Complex operator +(Complex a, Complex b) => a.Add(b);
public string Name => First + " " + Last;
public Customer this[long id] => store.LookupCustomer(id);
```

Pokud metoda vrátí `void` nebo je asynchronní metody, výrazu příkazu (stejně jako výrazy lambda) musí být tělo metody.  Pro vlastnostmi a indexery, musí být jen pro čtení a je velmi riskantní používat `get` – klíčové slovo přistupujícího objektu.

<a name="iterators"></a>

## <a name="iterators"></a>Iterátory

Iterátor provádí vlastní iterace nad kolekcí, jako je například seznam nebo pole. Iterátor používá [yield return](language-reference/keywords/yield.md) příkaz vrátit vždy jeden prvek v čase. Když `yield return` je dosažen příkaz aktuální umístění se uloží, tak, aby volající mohl požadovat další prvek v sekvenci.

Návratový typ iterátor může být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, nebo <xref:System.Collections.Generic.IEnumerator%601>.

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
