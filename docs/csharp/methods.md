---
title: Metody – Průvodce C#
description: Přehled metod, metoda parametry a návratové hodnoty – metoda
author: rpetrusha
ms.author: ronpet
ms.date: 10/26/2016
ms.assetid: 577a8527-1081-4b36-9b9e-0685b6553c6e
ms.openlocfilehash: 6a99ccc0157b044eb1a9ed7189de94ca69225d1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="methods"></a>Metody #

Metoda je blok kódu, který obsahuje řadu příkazů. Program způsobí, že příkazy provádět volání metody a zadání argumentů požadovaná metoda. V jazyce C# každé spuštění instrukce se provádí v kontextu metody. `Main` Metoda je vstupní bod pro každou aplikaci C# a je volána metodou common language runtime (CLR) při spuštění programu.

> [!NOTE]
> Toto téma popisuje pojmenované metody. Informace o anonymní funkce najdete v tématu [anonymní funkce](programming-guide/statements-expressions-operators/anonymous-functions.md).

Toto téma obsahuje následující oddíly:

- [Podpisy – metoda](#signatures)
- [Volání metody](#invocation)
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
## <a name="method-signatures"></a>Podpisy – metoda ##

Metody, které jsou deklarované v `class` nebo `struct` zadáním:

- Volitelný přístup úrovně, jako například `public` nebo `private`. Výchozí hodnota je `private`.
- Volitelné modifikátory jako `abstract` nebo `sealed`.
- Návratovou hodnotu, nebo `void` Pokud metoda má none.
- Název metody.
- Všechny parametry metody. Parametry metody jsou uzavřené v závorkách a jsou odděleny čárkami. Závorky, jinak znamenat, že metoda nevyžaduje žádné parametry.

Tyto části společně tvoří podpis metody.

> [!NOTE]
> Návratový typ metody není součástí podpis metody pro účely přetěžování metody. Je však součástí podpis metody při určování kompatibilitu mezi delegáta a metodu, která odkazuje na.

Následující příklad definuje třídu s názvem `Motorcycle` obsahující pět metody:

[!code-csharp[csSnippets.Methods#40](../../samples/snippets/csharp/concepts/methods/methods40.cs#40)]

Všimněte si, že `Motorcycle` třída zahrnuje přetížené metody, `Drive`. Dvě metody se stejným názvem, ale musí být rozlišené pomocí jejich typy parametrů.

<a name="invocation"></a>
## <a name="method-invocation"></a>Volání metody ##

Metody může být buď *instance* nebo *statické*. Vyvolání metody instance vyžaduje, abyste vytvoří instanci objektu a volat metodu u tohoto objektu. Metoda instance funguje na tuto instanci a jeho data. Vyvolání statickou metodu pod položkou Název typu, do které patří metodu; statické metody pracovat se nevztahují na instance data. Probíhá pokus o volání statickou metodu pomocí instance objektu generuje chybu kompilátoru.

Volání metody je jako přístup k poli. Po názvu objektu (pokud jsou volání metody instance) nebo název typu (při volání `static` metoda), přidejte období, název metody, a kulaté závorky. Argumenty jsou uvedeny v závorkách a jsou odděleny čárkami.

Definice metoda určuje názvy a typy parametrů, které jsou požadovány. Když volající vyvolá metodu, poskytuje konkrétní hodnoty, nazývaných argumenty pro jednotlivé parametry. Argumenty, které musí být kompatibilní s typem parametru, ale název argument, pokud používá v volání kódu, nemusí být stejný jako parametr s názvem definované v metodě. V následujícím příkladu `Square` metoda obsahuje jeden parametr typu `int` s názvem *i*. První metodu volat průchodů `Square` metoda a proměnná typu `int` s názvem *num*; druhý, číselnou konstantu; a třetí, výrazu.

[!code-csharp[csSnippets.Methods#74](../../samples/snippets/csharp/concepts/methods/params74.cs#74)]

Nejběžnější volání metody státní poziční argumenty; poskytne argumenty ve stejném pořadí jako parametry metody. Metody `Motorcycle` třída proto nelze volat jako v následujícím příkladu. Volání `Drive` metoda, například obsahuje dva argumenty, které odpovídají dva parametry v syntaxi metody. První se změní na hodnotu `miles` parametr, druhá hodnota `speed` parametr.

[!code-csharp[csSnippets.Methods#41](../../samples/snippets/csharp/concepts/methods/methods40.cs#41)]

Můžete také použít *s názvem argumenty* místo poziční argumenty při vyvolání metody. Při použití s názvem argumenty, je třeba zadat název parametru následovaným dvojtečkou (":") a argumentem. Argumenty pro metodu může vyskytovat v libovolném pořadí, tak dlouho, dokud nejsou všechny požadované argumenty. Následující příklad používá pojmenované argumenty pro vyvolání `TestMotorcycle.Drive` metoda. V tomto příkladu jsou pojmenované argumenty z seznam parametrů metody předán v opačném pořadí.

[!code-csharp[csSnippets.Methods#45](../../samples/snippets/csharp/concepts/methods/named1.cs#45)]

Můžete vyvolat metodu pomocí obou argumentů umístění a pojmenované argumenty. Poziční argument však nelze sledovat pojmenovaný argument. Následující příklad popisuje vyvolání `TestMotorcycle.Drive` metoda z předchozího příkladu pomocí poziční jeden argument a jednu s názvem argument.

[!code-csharp[csSnippets.Methods#46](../../samples/snippets/csharp/concepts/methods/named2.cs#46)]

 <a name="inherited"></a>
 ##<a name="inherited-and-overridden-methods"></a>Zděděné a přepsané metody ##

Kromě členů, které jsou explicitně definované v typu zdědí typu členy definované v jeho základních tříd. Vzhledem k tomu, že všechny typy v systému spravovaný typ dědí přímo nebo nepřímo <xref:System.Object> třída, všechny typy dědit jejích členů, například <xref:System.Object.Equals(System.Object)>, <xref:System.Object.GetType>, a <xref:System.Object.ToString>. V následujícím příkladu definuje `Person` třídy, vytvoří dvě instance `Person` objekty a volá `Person.Equals` metoda k určení, zda jsou oba objekty stejné. `Equals` Metoda, však není definován v `Person` třídy; je zděděn z <xref:System.Object>.

[!code-csharp[csSnippets.Methods#104](../../samples/snippets/csharp/concepts/methods/inherited1.cs#104)]

Typy můžete přepsat zděděné členy pomocí `override` – klíčové slovo a poskytuje implementaci pro metodu přepsané. Podpis metody musí být stejný jako přepsané metody. Následující příklad je stejný, jako je předchozí s tím rozdílem, že přepíše <xref:System.Object.Equals(System.Object)> metoda. (Potlačí také <xref:System.Object.GetHashCode> metoda, protože tyto dvě metody jsou určeny k poskytování konzistentních výsledků.)

[!code-csharp[csSnippets.Methods#105](../../samples/snippets/csharp/concepts/methods/overridden1.cs#105)]

<a name="passing"></a>
## <a name="passing-parameters"></a>Předávání parametrů ##

Typy v jazyku C# jsou buď *typů hodnot* nebo *odkazové typy*. Seznam typů předdefinovaných hodnot najdete v tématu [typy a proměnné](./tour-of-csharp/types-and-variables.md). Ve výchozím nastavení typy hodnot a odkazové typy jsou předaný metodě hodnotou.

<a name="byval"></a>
### <a name="passing-parameters-by-value"></a>Předávání parametrů podle hodnoty ###

Když metoda předána typ hodnoty podle hodnoty, je kopii objektu místo samotného objektu předaný metodě. Změny objektu volané metody tedy mít žádný vliv na původní objekt při řízení vrátí volajícímu.

Následující příklad předá typ hodnoty metodu podle hodnoty a zavolat metodu pokusí změnit hodnotu typ hodnoty. Definuje proměnné typu `int`, což je typ hodnoty, inicializuje jeho hodnotu na 20 a předává je pro metodu s názvem `ModifyValue` , se změní hodnota proměnné na 30. Když metoda vrátí, ale hodnota proměnné zůstane beze změny.

[!code-csharp[csSnippets.Methods#10](../../samples/snippets/csharp/concepts/methods/byvalue10.cs#10)]

Když metoda předána objekt typu odkaz podle hodnoty, je předaná hodnota odkaz na objekt. To znamená metoda obdrží není samotného objektu, ale argument, který určuje umístění objektu. Pokud změníte členem objektu pomocí tohoto odkazu, změny se v objektu, když se vrátí ovládací prvek volání metody. Však nahradit objekt předaný metodě nemá žádný vliv na původní objekt při řízení vrátí volajícímu.

Následující příklad definuje třídu (která je typu odkazu) s názvem `SampleRefType`. Vytvoření instance `SampleRefType` objektu, přiřadí 44 k jeho `value` pole a předá objekt, který má `ModifyObject` metoda. Tento příklad nemá v podstatě má stejnou funkci jako předchozí příklad – předá argumentu podle hodnoty metodu. Ale protože odkaz na typ se používá, výsledek se liší. Změna, která se provádí v `ModifyObject` k `obj.value` poli také změní `value` pole argumentu, `rt`v `Main` metodu 33, jako výstup ukazuje příklad.

[!code-csharp[csSnippets.Methods#42](../../samples/snippets/csharp/concepts/methods/byvalue42.cs#42)]

<a name="byref"></a>
### <a name="passing-parameters-by-reference"></a>Předávání parametrů odkazem ###

Předání parametru odkazu, pokud chcete změnit hodnotu argumentu v metodě a chcete refect tato změna při volání metody vrátí ovládací prvek. Chcete-li předat parametr odkazu, použijte [ `ref` ](language-reference/keywords/ref.md) nebo [ `out` ](language-reference/keywords/out-parameter-modifier.md) – klíčové slovo. Můžete také předat hodnotu odkazem vyhnout kopírování, ale stále zabránit úpravy pomocí [ `in` ](language-reference/keywords/in-parameter-modifier.md) – klíčové slovo.

Následující příklad je stejný jako předchozí, s výjimkou toho, je předaná hodnota odkaz na `ModifyValue` metoda. Pokud je hodnota parametru pozměněn v `ModifyValue` metoda změnu hodnoty se projeví po návratu řízení volajícímu.

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/byref106.cs#106)]

Běžný vzor, který používá parametry ref zahrnuje odkládací hodnoty proměnných. Dvě proměnné, které předáte metodě odkazem a metoda prohození jejich obsah. Následující příklad prohození celočíselné hodnoty.

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/swap107.cs#107)]

Předávání parametrů typu odkazu můžete změnit hodnotu odkaz sám sebe, nikoli hodnotu jeho jednotlivé elementy nebo pole.

<a name="paramarray"></a>
### <a name="parameter-arrays"></a>Pole parametrů ###

V některých případech je požadavek je zadat přesně počet argumentů pro metodu omezující. Pomocí `params` – klíčové slovo označíte, že je parametr pole parametrů, povolte metodu k volání s proměnlivým počtem argumentů. Parametr označené `params` – klíčové slovo musí být typu pole a musí být poslední parametr v seznamu parametrů metody.

Volající pak můžete vyvolat metodu jedním ze tří způsobů:

- Předáním pole příslušného typu, který obsahuje požadovaný počet elementů.
- Pomocí metody předání čárkami oddělený seznam jednotlivých argumentů příslušného typu.
- Poskytnutím není argumentu pole parametrů.

V následujícím příkladu definuje metodu s názvem `DoStringOperation` který provede operaci řetězec určeného její první parametr `StringOperation` – člen výčtu. Pole parametrů jsou definovány řetězce, na kterých je k provedení operace. `Main` Metoda znázorňuje všechny tři způsoby vyvolání metody. Všimněte si, že metoda označené `params` – klíčové slovo musí být schopen zpracovávat tento případ, ve kterém je žádný argument zadaný pro parametr pole, tak, aby jeho hodnota může být `null`.

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/byref108.cs#108)]

<a name="optional"></a>
## <a name="optional-parameters-and-arguments"></a>Volitelné parametry a argumenty ##

Definice metody můžete určit, že jeho parametry jsou povinné a že jsou volitelné. Ve výchozím nastavení jsou vyžadovány parametry. Volitelné parametry jsou určené v definici metoda včetně výchozí hodnoty parametru. Při volání metody pro volitelný parametr nebude zadán žádný argument, bude místo něj použita výchozí hodnota.

Výchozí hodnoty parametru musí být přiřadit pomocí jedné z následujících druhy výrazů:

- Toto je konstanta, například řetězcového literálu nebo číslo.
- Výraz, který formulář `new ValType`, kde `ValType` je typ hodnoty. Všimněte si, že tím se spustí tento typ hodnoty implicitní výchozí konstruktor, který není skutečné člen daného typu.
- Výraz, který formulář `default(ValType)`, kde `ValType` je typ hodnoty.

Obsahuje-li metodu povinných a volitelných parametrů, volitelné parametry jsou definovány na konci seznamu parametrů po všechny požadované parametry.

V následujícím příkladu definuje metodu, `ExampleMethod`, který má jeden požadované a volitelné dva parametry.

[!code-csharp[csSnippets.Methods#21](../../samples/snippets/csharp/concepts/methods/optional1.cs#21)]

Pokud je metoda s více volitelné argumenty je vyvolána pomocí poziční argumenty, volající musíte zadat argument pro všechny volitelné parametry z první z nich pro naposledy, pro který je zadán argument. U `ExampleMethod` metoda, například, pokud má volající poskytuje argument pro `description` parametru, je třeba zadat také jeden pro `optionalInt` parametr. `opt.ExampleMethod(2, 2, "Addition of 2 and 2");` je neplatná metoda volání; `opt.ExampleMethod(2, , "Addition of 2 and 0);` generuje "Argument chybějící" Chyba kompilátoru.

Pokud je volána metoda pomocí pojmenované argumenty nebo jejich kombinaci poziční a pojmenované argumenty, volající vynechat všechny argumenty, které následují poslední poziční argument při volání metody.

Následující příklad volání `ExampleMethod` metoda třikrát.  Volání první dvě metody používají poziční argumenty. První vynechá obou volitelné argumenty, zatímco druhý vynechá poslední argument. Třetí volání metody, které poskytuje poziční argument pro požadovaný parametr, ale používá pojmenovaný argument zadat hodnotu, která `description` parametr při vynechání `optionalInt` argument.

[!code-csharp[csSnippets.Methods#22](../../samples/snippets/csharp/concepts/methods/optional1.cs#22)]

Použití volitelné parametry ovlivňuje *řešení přetížení*, nebo způsobem, ve kterém kompilátor jazyka C# určuje, které konkrétní přetížení by měla být volána metoda volání, následujícím způsobem:

- Metoda, indexer nebo konstruktor je kandidátem na spuštění, pokud všechny její parametry je volitelný nebo odpovídá podle názvu nebo podle pozici, na jeden argument příkazu volání a který argument lze převést na typ parametru.
- Pokud je nalezen více než jeden candidate, přetížení řešení pro upřednostňované převody pravidla argumenty, které jsou explicitně určena. Vynechání argumenty pro volitelné parametry jsou ignorovány.
- Pokud dva kandidáty jsou považovány za být stejně dobrý, předvoleb přejde na candidate, který nemá volitelné parametry, pro které byly vynechány argumenty ve volání. Toto je důsledkem Obecné předvolby rozlišení přetížení pro kandidáty, které mají méně parametry.

 <a name="return"></a>
 ## <a name="return-values"></a>Vrácené hodnoty ##

Metody můžete vrátit hodnotu volajícímu. Návratový typ (typ uvedené před název metody) není-li `void`, metoda může vrátit hodnotu pomocí `return` – klíčové slovo. Příkaz s `return` – klíčové slovo, za nímž následuje proměnná, konstanta nebo výraz, který odpovídá návratový typ, vrátí tuto hodnotu Metoda volajícího. Metody s není void vrací typ jsou nutné k použití `return` – klíčové slovo bude vrácena hodnota. `return` – Klíčové slovo také zastaví provádění metody.

Pokud je návratový typ `void`, `return` je stále užitečné zastavit provádění metody příkaz bez hodnoty. Bez `return` – klíčové slovo, metoda skončí při ukončení bloku kódu.

Například použít tyto dvě metody `return` – klíčové slovo vrátit celá čísla:

[!code-csharp[csSnippets.Methods#44](../../samples/snippets/csharp/concepts/methods/return44.cs#44)]

Pokud chcete použít hodnotu, vrátí metoda, můžete použít metodu volání volání metody samotné kdekoli hodnota stejného typu by být dostatečná. Můžete také přiřadit návratovou hodnotu proměnné. Například následující příklady kódu dvě dosažení stejné cíle:

[!code-csharp[csSnippets.Methods#45](../../samples/snippets/csharp/concepts/methods/return44.cs#45)]

[!code-csharp[csSnippets.Methods#46](../../samples/snippets/csharp/concepts/methods/return44.cs#46)]

Použití místní proměnné, v takovém případě `result`, ukládat hodnota je volitelná. Dobře čitelnost kódu, nebo může být nutné, pokud je třeba uložit původní hodnota argumentu pro celý rozsah metodu.

V některých případech budete chtít metodu vrátit více než jednu hodnotu. Od verze 7.0 C#, můžete k tomu snadno pomocí *řazené kolekce členů typy* a *řazené kolekce členů literály*. Typ řazené kolekce členů definuje datové typy elementů řazené kolekce členů. Literály řazené kolekce členů zadejte skutečné hodnoty vrácené řazené kolekce členů. V následujícím příkladu `(string, string, string, int)` definuje typ řazené kolekce členů, která je vrácena `GetPersonalInfo` metoda. Výraz `(per.FirstName, per.MiddleName, per.LastName, per.Age)` je literál; název první a poslední společně s stáří, vrátí metoda z řazenou kolekci členů `PersonInfo` objektu.

```csharp
public (string, string, string, int) GetPersonalInfo(string id)
{
    PersonInfo per = PersonInfo.RetrieveInfoById(id);
    if (per != null)
       return (per.FirstName, per.MiddleName, per.LastName, per.Age);
    else
       return null;
}
```

Volající pak spotřebovat vrácený řazené kolekce členů s kódem takto:

```csharp
var person = GetPersonalInfo("111111111")
if (person != null)
   Console.WriteLine("{person.Item1} {person.Item3}: age = {person.Item4}");
```

Názvy můžete také přiřazený k elementům řazené kolekce členů v definici typu řazené kolekce členů. Následující příklad ukazuje alternativní verze `GetPersonalInfo` metoda, která používá s názvem prvky:

```csharp
public (string FName, string MName, string LName, int Age) GetPersonalInfo(string id)
{
    PersonInfo per = PersonInfo.RetrieveInfoById(id);
    if (per != null)
       return (per.FirstName, per.MiddleName, per.LastName, per.Age);
    else
       return null;
}
```

Předchozí volání `GetPersonInfo` metoda pak lze upravit takto:

```csharp
var person = GetPersonalInfo("111111111");
if (person != null)
   Console.WriteLine("{person.FName} {person.LName}: age = {person.Age}");
```

Pokud metoda pole je předat jako argument a upraví hodnoty jednotlivých prvků, není nutné pro metodu vrátit pole, i když můžete tak učinit pro dobrý styl nebo funkční toku hodnot.  Je to proto C# předá všechny odkazové typy podle hodnoty a odkaz na pole hodnotu má ukazatel na pole. V následujícím příkladu se změní na obsah `values` pole, které jsou vytvářeny v `DoubleValues` metoda jsou lze zobrazit pomocí kód, který obsahuje odkaz na pole.

[!code-csharp[csSnippets.Methods#101](../../samples/snippets/csharp/concepts/methods/returnarray1.cs#101)]

 <a name="exten"></a>
 ## <a name="extension-methods"></a>Metody rozšíření ##

Normálně existují dva způsoby, jak přidat metodu do stávající typ:

- Zdrojový kód pro tento typ změňte. Nelze to uděláte, samozřejmě, pokud nejste vlastníkem tohoto typu zdrojového kódu. A to se stane narušující změně, pokud přidáte také všechna pole privátní dat podporuje metodu.
- Definujte nové metody v odvozené třídě. Metodu nelze přidat tímto způsobem použití dědičnosti pro jiné typy, jako je například struktury a výčty. Ani jej lze "Přidat" metodu zapečetěné třídy.

Rozšiřující metody umožňují "Přidat" metodu existující typ bez úpravy vlastní typ nebo implementace nová metoda v zděděné typu. Metody rozšíření také nemá být umístěné ve stejném sestavení jako typ, který rozšiřuje ji. Metody rozšíření volání, jako by šlo definované člena typu.

Další informace najdete v tématu [rozšiřující metody](programming-guide/classes-and-structs/extension-methods.md).

<a name="async"></a>
## <a name="async-methods"></a>Asynchronní metody ##

Pomocí funkce asynchronní můžete vyvolat asynchronních metod bez použití explicitní zpětná volání nebo Ruční rozdělení kódu mezi více metod nebo výrazy lambda.

Pokud označíte metodu s [asynchronní](language-reference/keywords/async.md) modifikátor, můžete použít [await](language-reference/keywords/await.md) operátor v metodě. Při řízení dosáhnou `await` výrazu v asynchronní metody řízení vrátí volající Pokud awaited úloha není dokončena a pokroku v metodě s `await` – klíčové slovo je pozastaveno, dokud se nedokončí awaited úloh. Po dokončení úlohy provádění může pokračovat v metodě.

> [!NOTE]
> Asynchronní metody vrátí volající, pokud zjistí první awaited objekt, který ještě není dokončena nebo získá na konec asynchronní metody, cokoliv nastane dříve.

Asynchronní metody může mít návratový typ <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, nebo `void`. `void` Vrátí typ se používá hlavně k definování obslužné rutiny událostí, kde `void` návratový typ je požadovaná. Asynchronní metody, která vrací `void` nemůže být očekáváno, a volající metody vrácení void nelze catch výjimky, které vyvolá metoda. C# 7.0, po vydání, bude usnadňují toto omezení umožňující použití asynchronní metody [vrátit jakýkoli typ úlohy jako](https://github.com/ljw1004/roslyn/blob/features/async-return/docs/specs/feature%20-%20arbitrary%20async%20returns.md).

V následujícím příkladu `DelayAsync` je asynchronní metody, který má návratový příkaz, který vrátí celé číslo. Protože je asynchronní metody, jeho metoda deklarace musí mít návratový typ `Task<int>`. Vzhledem k tomu, že je návratový typ `Task<int>`, vyhodnocení `await` výrazu v `DoSomethingAsync` vytváří celé jako následující `int result = await delayTask` ukazuje příkaz.

[!code-csharp[csSnippets.Methods#102](../../samples/snippets/csharp/concepts/methods/async1.cs#102)]

Asynchronní metody nelze deklarovat všechny [v](language-reference/keywords/in-parameter-modifier.md), [ref](language-reference/keywords/ref.md), nebo [out](language-reference/keywords/out-parameter-modifier.md) parametry, ale můžete volat metody, které mají tyto parametry.

 Další informace o asynchronní metody najdete v tématu [asynchronní programování s Async a Await](async.md), [řízení toku v asynchronních programech](programming-guide/concepts/async/control-flow-in-async-programs.md), a [asynchronní vrátit typy](programming-guide/concepts/async/async-return-types.md).

<a name="expr"></a>
## <a name="expression-bodied-members"></a>Výraz vozidlo členy ##

Je běžné metoda definicemi, jednoduše okamžitě vrátí s výsledkem výrazu nebo které mají jediný příkaz jako text metody.  Je syntaxe zástupce pro definování těchto metod, pomocí `=>`:

```csharp
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);
public void Print() => Console.WriteLine(First + " " + Last);
// Works with operators, properties, and indexers too.
public static Complex operator +(Complex a, Complex b) => a.Add(b);
public string Name => First + " " + Last;
public Customer this[long id] => store.LookupCustomer(id);
```

Pokud metoda vrátí `void` nebo asynchronní metody, obsah metody musí být výraz – příkaz (stejné jako u lambdas).  Pro vlastnostmi a indexery, musí být jen pro čtení a nepoužívejte `get` – klíčové slovo přistupujícího objektu.

<a name="iterators"></a>
## <a name="iterators"></a>Iterátory ##

Iterátor provede vlastní iterace nad kolekcí, jako je například seznam nebo pole. Iterátor používá [yield vrátit](language-reference/keywords/yield.md) příkaz vrátit každý element, jeden v čase. Když `yield return` příkaz je dosaženo, aktuální umístění je uloží, takže volající může požádat o další prvek v pořadí.

Návratový typ iterovat může být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, nebo <xref:System.Collections.Generic.IEnumerator%601>.

Další informace najdete v tématu [iterátory](programming-guide/concepts/iterators.md).

## <a name="see-also"></a>Viz také ##

[Modifikátory přístupu](language-reference/keywords/access-modifiers.md)   
[Statické třídy a jejich členové](programming-guide/classes-and-structs/static-classes-and-static-class-members.md)   
[dědičnost](programming-guide/classes-and-structs/inheritance.md)   
[Abstraktní a uzavřené třídy a jejich členové](programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)   
[Parametry](language-reference/keywords/params.md)   
[na více systémů](language-reference/keywords/out-parameter-modifier.md)   
[REF](language-reference/keywords/ref.md)   
[V](language-reference/keywords/in-parameter-modifier.md)   
[Předávání parametrů](programming-guide/classes-and-structs/passing-parameters.md)
