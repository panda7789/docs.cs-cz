---
title: Metody – průvodce C#
description: Přehled metod, parametrů metody a vrácených hodnot metody
ms.technology: csharp-fundamentals
ms.date: 05/21/2018
ms.assetid: 577a8527-1081-4b36-9b9e-0685b6553c6e
ms.openlocfilehash: f44c83408e884d76eef5e2b5abbca511fbae2a1f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399446"
---
# <a name="methods"></a>Metody

Metoda je blok kódu, který obsahuje řadu příkazů. Program způsobí, že příkazy, které mají být provedeny voláním metody a zadáním všechny argumenty požadované metody. V C# každá provedená instrukce se provádí v kontextu metody. Metoda `Main` je vstupníbod pro každou aplikaci Jazyka C# a je volána za běhu common jazyka (CLR) při spuštění programu.

> [!NOTE]
> Toto téma popisuje pojmenované metody. Informace o anonymních funkcích naleznete [v tématu Anonymní funkce](programming-guide/statements-expressions-operators/anonymous-functions.md).

<a name="signatures"></a>

## <a name="method-signatures"></a>Podpisy metod

Metody jsou deklarovány v `class` nebo `struct` zadáním:

- Volitelná úroveň přístupu, například `public` nebo `private`. Výchozí formát je `private`.
- Volitelné modifikátory, například `abstract` nebo `sealed`.
- Vrácená hodnota `void` nebo pokud metoda nemá žádné.
- Název metody.
- Všechny parametry metody. Parametry metody jsou uzavřeny v závorce a jsou odděleny čárkami. Prázdné závorky označují, že metoda nevyžaduje žádné parametry.

Tyto části dohromady tvoří podpis metody.

> [!NOTE]
> Návratový typ metody není součástí podpisu metody pro účely přetížení metody. Je však součástí podpisu metody při určování kompatibility mezi delegátem a metodou, na kterou odkazuje.

Následující příklad definuje třídu `Motorcycle` s názvem, která obsahuje pět metod:

[!code-csharp[csSnippets.Methods#40](../../samples/snippets/csharp/concepts/methods/methods40.cs#40)]

Všimněte `Motorcycle` si, že třída `Drive`obsahuje přetížené metody . Dvě metody mají stejný název, ale musí být odlišeny podle jejich typů parametrů.

<a name="invocation"></a>

## <a name="method-invocation"></a>Vyvolání metody

Metody mohou být *instance* nebo *statické*. Vyvolání metody instance vyžaduje vytvoření instance objektu a volání metody na tomto objektu; instance metoda pracuje na této instanci a její data. Vyvoláte statickou metodu odkazem na název typu, ke kterému metoda patří; statické metody nepracují s daty instancí. Pokus o volání statické metody prostřednictvím instance objektu generuje chybu kompilátoru.

Volání metody je jako přístup k poli. Za název objektu (pokud voláte metodu instance) nebo za `static` název typu (pokud voláte metodu) přidejte tečku, název metody a závorky. Argumenty jsou uvedeny v závorce a jsou odděleny čárkami.

Definice metody určuje názvy a typy všech požadovaných parametrů. Když volající vyvolá metodu, poskytuje konkrétní hodnoty, nazývané argumenty, pro každý parametr. Argumenty musí být kompatibilní s typem parametru, ale název argumentu, pokud je použit v volajícím kódu, nemusí být stejný jako parametr pojmenovaná v metodě. V následujícím příkladu `Square` metoda obsahuje jeden `int` parametr typu s názvem *i*. První volání metody `Square` předá metodu `int` proměnnou typu s názvem *num*; druhá, číselná konstanta; a třetí, výraz.

[!code-csharp[csSnippets.Methods#74](../../samples/snippets/csharp/concepts/methods/params74.cs#74)]

Nejběžnější forma vyvolání metody používá poziční argumenty; poskytuje argumenty ve stejném pořadí jako parametry metody. Metody třídy `Motorcycle` proto lze volat jako v následujícím příkladu. Volání `Drive` metody, například obsahuje dva argumenty, které odpovídají dva parametry v syntaxi metody. První se stane hodnotou parametru, `miles` druhá `speed` hodnota parametru.

[!code-csharp[csSnippets.Methods#41](../../samples/snippets/csharp/concepts/methods/methods40.cs#41)]

Při vyvolání metody můžete také použít *pojmenované argumenty* namísto pozičních argumentů. Při použití pojmenovaných argumentů zadáte název parametru následovaný dvojtečkou (":") a argument. Argumenty metody se mohou zobrazit v libovolném pořadí, pokud jsou přítomny všechny požadované argumenty. Následující příklad používá pojmenované argumenty `TestMotorcycle.Drive` k vyvolání metody. V tomto příkladu jsou pojmenované argumenty předány v opačném pořadí ze seznamu parametrů metody.

[!code-csharp[csSnippets.Methods#45](../../samples/snippets/csharp/concepts/methods/named1.cs#45)]

Metodu můžete vyvolat pomocí pozičních argumentů i pojmenovaných argumentů. Poziční argument však nemůže následovat pojmenovaný argument. Následující příklad vyvolá `TestMotorcycle.Drive` metodu z předchozího příkladu pomocí jednoho pozičního argumentu a jednoho pojmenovaného argumentu.

[!code-csharp[csSnippets.Methods#46](../../samples/snippets/csharp/concepts/methods/named2.cs#46)]

<a name="inherited"></a>

## <a name="inherited-and-overridden-methods"></a>Zděděné a přepsané metody

Kromě členů, které jsou explicitně definovány v typu, typ dědí členy definované v jeho základní třídy. Vzhledem k tomu, že všechny typy v <xref:System.Object> systému spravovaného typu dědí <xref:System.Object.GetType>přímo <xref:System.Object.ToString>nebo nepřímo z třídy, všechny typy dědí jeho členy, například <xref:System.Object.Equals(System.Object)>, , a . Následující příklad definuje `Person` třídu, konkretizovat `Person` dva `Person.Equals` objekty a volá metodu k určení, zda jsou tyto dva objekty stejné. Metoda `Equals` však není definována `Person` ve třídě; je zděděn z <xref:System.Object>.

[!code-csharp[csSnippets.Methods#104](../../samples/snippets/csharp/concepts/methods/inherited1.cs#104)]

Typy můžete přepsat zděděné `override` členy pomocí klíčového slova a poskytování implementace pro přepsané metody. Podpis metody musí být stejný jako u přepsané metody. Následující příklad je jako předchozí, s tím <xref:System.Object.Equals(System.Object)> rozdílem, že přepíše metodu. (Také přepíše <xref:System.Object.GetHashCode> metodu, protože tyto dvě metody jsou určeny k zajištění konzistentních výsledků.)

[!code-csharp[csSnippets.Methods#105](../../samples/snippets/csharp/concepts/methods/overridden1.cs#105)]

<a name="passing"></a>

## <a name="passing-parameters"></a>Předávání parametrů

Typy v c# jsou buď *typy hodnot* nebo *typy odkazů*. Seznam předdefinovaných typů hodnot naleznete v tématu [Typy a proměnné](./tour-of-csharp/types-and-variables.md). Ve výchozím nastavení jsou metody podle hodnoty předány typy hodnot i typy odkazů.

<a name="byval"></a>

### <a name="passing-parameters-by-value"></a>Předávání parametrů podle hodnoty

Pokud je typ hodnoty předán metodě podle hodnoty, je metodě předána kopie objektu namísto samotného objektu. Proto změny objektu v volané metody nemají žádný vliv na původní objekt při ovládacíprvek vrátí volajícímu.

Následující příklad předá typ hodnoty metodě podle hodnoty a volaná metoda se pokusí změnit hodnotu typu hodnoty. Definuje proměnnou typu `int`, což je typ hodnoty, inicializuje jeho hodnotu na 20 a předá ji metodě s názvem, `ModifyValue` která změní hodnotu proměnné na 30. Když však metoda vrátí, hodnota proměnné zůstane nezměněna.

[!code-csharp[csSnippets.Methods#10](../../samples/snippets/csharp/concepts/methods/byvalue10.cs#10)]

Pokud je objekt typu odkazu předán metodě hodnotou, je odkaz na objekt předán hodnotou. To znamená, že metoda neobdrží samotný objekt, ale argument, který označuje umístění objektu. Pokud změníte člen objektu pomocí tohoto odkazu, změna se projeví v objektu při ovládacíprvek vrátí do volající metody. Nahrazení objektu předané metodě však nemá žádný vliv na původní objekt při návratu ovládacího prvku volajícímu.

Následující příklad definuje třídu (což je typ `SampleRefType`odkazu) s názvem . Konkretipouje `SampleRefType` objekt, přiřadí 44 k `value` jeho `ModifyObject` pole a předá objekt metodě. Tento příklad dělá v podstatě totéž jako v předchozím příkladu -- předá argument podle hodnoty metodě. Ale protože se používá typ odkazu, výsledek je jiný. Změna, která je `ModifyObject` provedena `obj.value` v poli `value` také změní `rt`pole argumentu , v metodě `Main` 33, jak ukazuje výstup z příkladu.

[!code-csharp[csSnippets.Methods#42](../../samples/snippets/csharp/concepts/methods/byvalue42.cs#42)]

<a name="byref"></a>

### <a name="passing-parameters-by-reference"></a>Předávání parametrů odkazem

Parametr předáte odkazem, pokud chcete změnit hodnotu argumentu v metodě a chcete tuto změnu reflektovat, když se ovládací prvek vrátí do volající metody. Chcete-li předat parametr odkazem, použijte klíčové slovo [`ref`](language-reference/keywords/ref.md) nebo. [`out`](language-reference/keywords/out-parameter-modifier.md) Můžete také předat hodnotu odkazem, abyste se vyhnuli [`in`](language-reference/keywords/in-parameter-modifier.md) kopírování, ale stále zabraňte změnám pomocí klíčového slova.

Následující příklad je shodný s předchozím, s výjimkou hodnoty `ModifyValue` je předán odkazem na metodu. Při změně hodnoty parametru v `ModifyValue` metodě se změna hodnoty projeví při vrácení ovládacího prvku volajícímu.

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/byref106.cs#106)]

Společný vzor, který používá ref parametry zahrnuje zaměňování hodnoty proměnných. Předáte dvě proměnné metodě odkazem a metoda zamění jejich obsah. Následující příklad zamění celé hodnoty.

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/swap107.cs#107)]

Předání parametru typu odkazu umožňuje změnit hodnotu samotného odkazu, nikoli hodnotu jednotlivých prvků nebo polí.

<a name="paramarray"></a>

### <a name="parameter-arrays"></a>Pole parametrů

V některých případě požadavek, který zadáte přesný počet argumentů pro vaši metodu je omezující. Pomocí klíčového `params` slova k označení, že parametr je pole parametrů, povolíte, aby byla metoda volána s proměnným počtem argumentů. Parametr označený klíčovým `params` slovem musí být typ pole a musí se jednat o poslední parametr v seznamu parametrů metody.

Volající pak můžete vyvolat metodu v jedním ze tří způsobů:

- Předáním pole příslušného typu, který obsahuje požadovaný počet prvků.
- Předáním seznamu jednotlivých argumentů odpovídajícího typu odděleným čárkami do metody.
- Tím, že poskytuje argument pole parametrů.

Následující příklad definuje metodu `GetVowels` s názvem, která vrací všechny samohlásky z pole parametrů. Metoda `Main` ilustruje všechny tři způsoby vyvolání metody. Volající nejsou povinni zadat žádné argumenty pro `params` parametry, které obsahují modifikátor. V takovém případě je `null`parametr .

[!code-csharp[csSnippets.Methods#75](~/samples/snippets/csharp/concepts/methods/params75.cs#75)]

<a name="optional"></a>

## <a name="optional-parameters-and-arguments"></a>Volitelné parametry a argumenty

Definice metody může určit, že její parametry jsou povinné nebo že jsou volitelné. Ve výchozím nastavení jsou požadovány parametry. Volitelné parametry jsou určeny zahrnutím výchozí hodnoty parametru do definice metody. Při volání metody, pokud žádný argument je zadán pro volitelný parametr, výchozí hodnota se použije místo.

Výchozí hodnota parametru musí být přiřazena jedním z následujících druhů výrazů:

- Konstanta, například literál řetězec nebo číslo.
- Výraz formuláře `new ValType()`, kde `ValType` je typ hodnoty. Všimněte si, že to vyvolá implicitní konstruktor implicitní parametrless typu hodnoty, který není skutečným členem typu.
- Výraz formuláře `default(ValType)`, kde `ValType` je typ hodnoty.

Pokud metoda obsahuje požadované i volitelné parametry, jsou volitelné parametry definovány na konci seznamu parametrů, po všech požadovaných parametrech.

Následující příklad definuje metodu `ExampleMethod`, která má jeden povinný a dva volitelné parametry.

[!code-csharp[csSnippets.Methods#21](../../samples/snippets/csharp/concepts/methods/optional1.cs#21)]

Pokud je vyvolána metoda s více volitelnými argumenty pomocí pozičních argumentů, volající musí zadat argument pro všechny volitelné parametry od prvního do posledního, pro který je zadán argument. V případě `ExampleMethod` metody, například pokud volající poskytuje argument pro `description` parametr, musí také zadat `optionalInt` jeden pro parametr. `opt.ExampleMethod(2, 2, "Addition of 2 and 2");`je volání platné metody; `opt.ExampleMethod(2, , "Addition of 2 and 0");` generuje chybu kompilátoru "Argument missing".

Pokud je metoda volána pomocí pojmenovaných argumentů nebo kombinace pozičních a pojmenovaných argumentů, volající může vynechat všechny argumenty, které následují za posledním pozičním argumentem ve volání metody.

Následující příklad volá `ExampleMethod` metodu třikrát.  První dvě volání metody používají poziční argumenty. První vyneche oba volitelné argumenty, zatímco druhý vynese poslední argument. Třetí metoda volání poskytuje poziční argument pro požadovaný parametr, ale používá `description` pojmenovaný argument k `optionalInt` dodání hodnoty parametru při vynechání argumentu.

[!code-csharp[csSnippets.Methods#22](../../samples/snippets/csharp/concepts/methods/optional1.cs#22)]

Použití volitelných parametrů ovlivňuje *rozlišení přetížení*nebo způsob, jakým kompilátor Jazyka C# určuje, které konkrétní přetížení by mělo být vyvoláno voláním metody, následujícím způsobem:

- Metoda, indexer nebo konstruktor je kandidátem pro spuštění, pokud je každý z jeho parametrů volitelný nebo odpovídá podle názvu nebo pozice jednomu argumentu v příkazu volání a tento argument lze převést na typ parametru.
- Pokud je nalezen více než jeden kandidát, pravidla řešení přetížení pro upřednostňované převody se použijí na argumenty, které jsou explicitně zadány. Vynechané argumenty pro volitelné parametry jsou ignorovány.
- Pokud jsou dva kandidáti považováni za stejně dobré, upřednostňuje se kandidát, který nemá volitelné parametry, pro které byly argumenty ve výzvě vynechány. To je důsledkem obecné preference v řešení přetížení pro kandidáty, kteří mají méně parametrů.

<a name="return"></a>

## <a name="return-values"></a>Vrácené hodnoty

Metody můžete vrátit hodnotu volajícímu. Pokud návratový typ (typ uvedený před názvem `void`metody) není , metoda `return` může vrátit hodnotu pomocí klíčového slova. Příkaz s `return` klíčovým slovem následovaný proměnnou, konstantou nebo výrazem, který odpovídá návratovému typu, vrátí tuto hodnotu volajícímu metody. Metody s nevoid návratový typ jsou `return` nutné použít klíčové slovo vrátit hodnotu. Klíčové `return` slovo také zastaví provádění metody.

Pokud je `void`návratový `return` typ , příkaz bez hodnoty je stále užitečné zastavit provádění metody. Bez `return` klíčového slova se metoda zastaví při dosažení konce bloku kódu.

Například tyto dvě metody `return` používají klíčové slovo k vrácení celá čísla:

[!code-csharp[csSnippets.Methods#44](../../samples/snippets/csharp/concepts/methods/return44.cs#44)]

Chcete-li použít hodnotu vrácenou z metody, může metoda volání použít metodu, která se nazývá kdekoli, že by stačila hodnota stejného typu. Návratovou hodnotu můžete také přiřadit proměnné. Například následující dva příklady kódu dosáhnout stejného cíle:

[!code-csharp[csSnippets.Methods#45](../../samples/snippets/csharp/concepts/methods/return44.cs#45)]

[!code-csharp[csSnippets.Methods#46](../../samples/snippets/csharp/concepts/methods/return44.cs#46)]

Použití místní proměnné, v `result`tomto případě , k uložení hodnoty je volitelné. Může pomoci čitelnost kódu nebo může být nezbytné, pokud potřebujete uložit původní hodnotu argumentu pro celý rozsah metody.

V některých případě chcete, aby vaše metoda vrátit více než jednu hodnotu. Počínaje C# 7.0, můžete to provést snadno pomocí *řazené kolekce členů typy* a *n-tice literals*. Typ n-tice definuje datové typy prvků řazené kolekce členů. N-tice literály poskytují skutečné hodnoty vrácené řazené kolekce členů. V následujícím příkladu definuje typ řazené kolekce členů, `(string, string, string, int)` který je vrácen `GetPersonalInfo` metodou. Výraz `(per.FirstName, per.MiddleName, per.LastName, per.Age)` je doslovný řazené kolekce členů; metoda vrátí první, střední a příjmení, spolu s věkem objektu. `PersonInfo`

```csharp
public (string, string, string, int) GetPersonalInfo(string id)
{
    PersonInfo per = PersonInfo.RetrieveInfoById(id);
    return (per.FirstName, per.MiddleName, per.LastName, per.Age);
}
```

Volající pak může využívat vrácenou řazenou n-tice s kódem, jako je následující:

```csharp
var person = GetPersonalInfo("111111111")
Console.WriteLine("{person.Item1} {person.Item3}: age = {person.Item4}");
```

Názvy lze také přiřadit k prvky řazené kolekce členů v definici typu řazené kolekce členů. Následující příklad ukazuje alternativní verzi `GetPersonalInfo` metody, která používá pojmenované prvky:

```csharp
public (string FName, string MName, string LName, int Age) GetPersonalInfo(string id)
{
    PersonInfo per = PersonInfo.RetrieveInfoById(id);
    return (per.FirstName, per.MiddleName, per.LastName, per.Age);
}
```

Předchozí volání `GetPersonInfo` metody pak lze upravit takto:

```csharp
var person = GetPersonalInfo("111111111");
Console.WriteLine("{person.FName} {person.LName}: age = {person.Age}");
```

Pokud je metoda předána pole jako argument a upravuje hodnotu jednotlivých prvků, není nutné pro metodu vrátit pole, i když můžete zvolit tak pro dobrý styl nebo funkční tok hodnot.  Důvodem je, že C# předá všechny typy odkazů podle hodnoty a hodnota odkazu pole je ukazatel na pole. V následujícím příkladu jsou změny `values` obsahu pole, které `DoubleValues` jsou provedeny v metodě, pozorovatelné libovolným kódem, který má odkaz na pole.

[!code-csharp[csSnippets.Methods#101](../../samples/snippets/csharp/concepts/methods/returnarray1.cs#101)]

<a name="extension"></a>

## <a name="extension-methods"></a>Metody rozšíření

Obvykle existují dva způsoby, jak přidat metodu k existujícímu typu:

- Upravte zdrojový kód pro tento typ. To samozřejmě nelze provést, pokud nevlastníte zdrojový kód typu. A to se stane narušující změnou, pokud přidáte také všechna soukromá datová pole pro podporu metody.
- Definujte novou metodu v odvozené třídě. Metoda nelze přidat tímto způsobem pomocí dědičnosti pro jiné typy, jako jsou například struktury a výčty. Nelze jej použít ani k "přidání" metody do zapečetěné třídy.

Rozšiřující metody umožňují "přidat" metodu k existujícímu typu bez změny samotného typu nebo implementace nové metody v zděděném typu. Metoda rozšíření také nemusí být umístěna ve stejném sestavení jako typ, který rozšiřuje. Volání metody rozšíření, jako by byl definovaný člen typu.

Další informace naleznete v [tématu Metody rozšíření](programming-guide/classes-and-structs/extension-methods.md).

<a name="async"></a>

## <a name="async-methods"></a>Asynchronní metody

Pomocí funkce async můžete vyvolat asynchronní metody bez použití explicitních zpětných volání nebo ručnírozdělení kódu mezi více metod nebo výrazy lambda.

Pokud označíte metodu s [asynchronním](language-reference/keywords/async.md) modifikátorem, můžete použít operátor [await](language-reference/operators/await.md) v metodě. Když ovládací prvek `await` dosáhne výrazv asynchronní metodě, ovládací prvek se vrátí volajícímu, pokud `await` není dokončena očekávaná úloha, a průběh metody s klíčovým slovem je pozastaven, dokud nebude dokončena očekávaná úloha. Po dokončení úlohy může spuštění pokračovat v metodě.

> [!NOTE]
> Asynchronní metoda se vrátí volajícímu, když buď narazí na první očekávaný objekt, který ještě není dokončen, nebo se dostane na konec asynchronní metody, podle toho, co nastane dříve.

Asynchronní metoda může mít <xref:System.Threading.Tasks.Task%601>návratový typ , <xref:System.Threading.Tasks.Task>, nebo `void`. Návratový `void` typ se používá především k definování `void` obslužných rutin událostí, kde je vyžadován návratový typ. Asynchronní metoda, `void` která vrátí nelze čekat a volající metody vrácení void nemůže zachytit výjimky, které metoda vyvolá. Počínaje C# 7.0, asynchronní metoda může mít [libovolný návratový typ podobný úkolu](./whats-new/csharp-7.md#generalized-async-return-types).

V následujícím příkladu je asynchronní metoda, `DelayAsync` která má return prohlášení, které vrací celé číslo. Protože se jedná o asynchronní metodu, musí `Task<int>`mít deklarace metody návratový typ . Vzhledem k `Task<int>`tomu, že `await` návratový `DoSomethingAsync` typ je , vyhodnocení výrazu v vytváří celé číslo, jak ukazuje následující `int result = await delayTask` příkaz.

[!code-csharp[csSnippets.Methods#102](../../samples/snippets/csharp/concepts/methods/async1.cs#102)]

Asynchronní metoda nemůže deklarovat žádné parametry [in](language-reference/keywords/in-parameter-modifier.md), [ref](language-reference/keywords/ref.md)nebo [out,](language-reference/keywords/out-parameter-modifier.md) ale může volat metody, které mají takové parametry.

 Další informace o asynchronních metodách naleznete [v tématech Asynchronní programování s asynchronními a awaity](async.md), [Tok řízení v asynchronních programech](programming-guide/concepts/async/control-flow-in-async-programs.md)a [Asynchronní návratové typy](programming-guide/concepts/async/async-return-types.md).

<a name="expr"></a>

## <a name="expression-bodied-members"></a>Členové tvoření výrazy

Je běžné mít definice metod, které jednoduše vrátit okamžitě s výsledkem výrazu nebo které mají jeden příkaz jako tělo metody.  Existuje zástupce syntaxe pro definování `=>`těchto metod pomocí :

```csharp
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);
public void Print() => Console.WriteLine(First + " " + Last);
// Works with operators, properties, and indexers too.
public static Complex operator +(Complex a, Complex b) => a.Add(b);
public string Name => First + " " + Last;
public Customer this[long id] => store.LookupCustomer(id);
```

Pokud metoda `void` vrátí nebo je asynchronní metoda, tělo metody musí být výraz příkazu (stejné jako u lambdas).  Pro vlastnosti a indexery musí být jen pro `get` čtení a nepoužíváte klíčové slovo přistupujícího objektu.

<a name="iterators"></a>

## <a name="iterators"></a>Iterátory

Iterátor provádí vlastní iteraci přes kolekci, jako je například seznam nebo pole. Iterátor používá yield [return](language-reference/keywords/yield.md) prohlášení vrátit každý prvek jeden po druhém. Po `yield return` dosažení příkazu je zapamatováno aktuální umístění, aby volající mohl požádat o další prvek v sekvenci.

Návratový typ iterátoru může <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601>být <xref:System.Collections.IEnumerator>, <xref:System.Collections.Generic.IEnumerator%601>, , nebo .

Další informace naleznete v tématu [Iterators](programming-guide/concepts/iterators.md).

## <a name="see-also"></a>Viz také

- [Modifikátory přístupu](language-reference/keywords/access-modifiers.md)
- [Statické třídy a jejich členové](programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [Dědičnost](programming-guide/classes-and-structs/inheritance.md)
- [Abstraktní a uzavřené třídy a jejich členové](programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [params](language-reference/keywords/params.md)
- [ven](language-reference/keywords/out-parameter-modifier.md)
- [ref](language-reference/keywords/ref.md)
- [In](language-reference/keywords/in-parameter-modifier.md)
- [Předávání parametrů](programming-guide/classes-and-structs/passing-parameters.md)
