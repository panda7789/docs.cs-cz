---
title: 'Asynchronní programování - C #'
description: Další informace o asynchronním programovacím modelu na úrovni jazyka C# poskytovaného rozhraním .NET Core.
author: cartermp
ms.date: 06/20/2016
ms.technology: csharp-async
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.openlocfilehash: 38d7c856e9a536db9ef26349175ad440a49f5fe2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713952"
---
# <a name="asynchronous-programming"></a>Asynchronní programování

Pokud máte nějaké potřeby vázané na vstupně-výstupní jednotky (například vyžádání dat ze sítě nebo přístup k databázi), budete chtít využít asynchronní programování.  Můžete mít také kód vázaný na procesor, jako je například provádění nákladného výpočtu, což je také dobrý scénář pro psaní asynchronního kódu.

C# má asynchronní programovací model na úrovni jazyka, který umožňuje snadné psaní asynchronního kódu bez nutnosti žonglovat s zpětná volání nebo v souladu s knihovnou, která podporuje asynchronii. Z vyplývá, co je známé jako [task-based asynchronní vzor (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).

## <a name="basic-overview-of-the-asynchronous-model"></a>Základní přehled asynchronního modelu

Jádrem asynchronního `Task` programování `Task<T>` je a objekty, které modelují asynchronní operace.  Jsou podporovány `async` a `await` klíčová slova.  Model je ve většině případů poměrně jednoduchý:

Pro vstupně-výstupní kód, `await` operace, která `Task` `Task<T>` vrátí nebo `async` uvnitř metody.

Pro kód vázaný na `await` procesor, operace, která je `Task.Run` spuštěna na podprocesu na pozadí s metodou.

Klíčové `await` slovo je místo, kde se stane kouzlo. Poskytuje řízení volajícímu metody, která `await`provedla a nakonec umožňuje uživatelské rozhraní reagovat nebo služby být elastické.

Existují i jiné způsoby, `async` jak `await` přistupovat k asynchronnímu kódu než a je uvedeno v článku TAP propojeném výše, ale tento dokument se od tohoto okamžiku zaměří na konstrukce na úrovni jazyka.

### <a name="io-bound-example-downloading-data-from-a-web-service"></a>Příklad stahování dat z webové služby

Možná budete muset stáhnout některá data z webové služby při stisknutí tlačítka, ale nechcete blokovat vlákno uživatelského rozhraní. To může být provedeno jednoduše takto:

```csharp
private readonly HttpClient _httpClient = new HttpClient();

downloadButton.Clicked += async (o, e) =>
{
    // This line will yield control to the UI as the request
    // from the web service is happening.
    //
    // The UI thread is now free to perform other work.
    var stringData = await _httpClient.GetStringAsync(URL);
    DoSomethingWithData(stringData);
};
```

A to je vše! Kód vyjadřuje záměr (stahování některých dat asynchronně) bez zabředne do interakce s task objekty.

### <a name="cpu-bound-example-performing-a-calculation-for-a-game"></a>Příklad vázaný na procesor: Provedení výpočtu pro hru

Řekněme, že píšete mobilní hru, kde stisknutí tlačítka může způsobit poškození mnoha nepřátelům na obrazovce.  Provedení výpočtu poškození může být nákladné a dělat to na vlákně uživatelského rozhraní by se hra zdála být pozastavena při výpočtu!

Nejlepší způsob, jak to zvládnout, je spustit vlákno `Task.Run`na `await` pozadí, které provádí práci pomocí aplikace a jeho výsledek.  To umožní, aby se uI cítilo hladce, když se práce provádí.

```csharp
private DamageResult CalculateDamageDone()
{
    // Code omitted:
    //
    // Does an expensive calculation and returns
    // the result of that calculation.
}

calculateButton.Clicked += async (o, e) =>
{
    // This line will yield control to the UI while CalculateDamageDone()
    // performs its work.  The UI thread is free to perform other work.
    var damageResult = await Task.Run(() => CalculateDamageDone());
    DisplayDamage(damageResult);
};
```

A to je vše!  Tento kód čistě vyjadřuje záměr události kliknutí na tlačítko, nevyžaduje ruční správu vlákna na pozadí a činí tak neblokujícím způsobem.

### <a name="what-happens-under-the-covers"></a>Co se děje pod kryty

Je tu spousta pohyblivých kusů, pokud jde o asynchronní operace.  Pokud jste zvědaví, co se děje `Task` pod `Task<T>`kryty a , pokladna [Async in-hloubkový](../standard/async-in-depth.md) článek pro více informací.

Na straně C# věcí kompilátor transformuje váš kód do stavu počítače, který `await` udržuje informace o věcech, jako je získávání spuštění při dosažení a obnovení provádění po dokončení úlohy na pozadí.

Pro teoreticky nakloněné, toto je implementace [Promise Model asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises).

## <a name="key-pieces-to-understand"></a>Klíčové kousky k pochopení

* Asynchronní kód lze použít pro vstupně-výstupní a procesorvázaný kód, ale odlišně pro každý scénář.
* Asynchronní `Task<T>` kód `Task`používá a , které jsou konstrukce používané k modelování práce se provádí na pozadí.
* Klíčové `async` slovo změní metodu na asynchronní metodu, která vám umožní použít `await` klíčové slovo v jeho těle.
* Při `await` použití klíčového slova pozastaví volající metodu a vrátí ovládací prvek zpět volajícímu, dokud nebude dokončena očekávaná úloha.
* `await`lze použít pouze uvnitř asynchronní metody.

## <a name="recognize-cpu-bound-and-io-bound-work"></a>Rozpoznat práci vázanou na procesor a vstupně-výstupní svázané práce

První dva příklady této příručky ukázaly, jak můžete použít `async` a `await` pro práci vázanou na vstupně-výstupní a procesorovou.  Je to klíč, který můžete identifikovat, když úloha, kterou potřebujete udělat, je I/O-vázaná nebo vázaný na procesor, protože může výrazně ovlivnit výkon kódu a může potenciálně vést ke zneužití určitých konstrukcí.

Zde jsou dvě otázky, které byste se měli zeptat, než napíšete nějaký kód:

1. Bude váš kód "čekání" na něco, jako jsou data z databáze?

    Pokud je vaše odpověď "ano", pak je vaše práce **i/ O-vázána**.

2. Bude váš kód provádět velmi nákladné výpočty?

    Pokud jste odpověděli "ano", pak je vaše práce **vázána na procesor**.

Pokud je práce, kterou **máte, vázána na vstupně-výstupní ,** použijte `async` `await` a *bez* `Task.Run`.  *Neměli* byste používat paralelní knihovnu úloh.  Důvod je popsán v [článku Async in Depth](../standard/async-in-depth.md).

Pokud je práce, kterou **máte, vázána na** `async` procesor `await` a záleží vám na odezvě, použijte a ale zplodíte práci na jiném vlákně *s* `Task.Run`.  Pokud je práce vhodná pro souběžnost a paralelismus, měli byste také zvážit použití [paralelní knihovny úloh](../standard/parallel-programming/task-parallel-library-tpl.md).

Kromě toho byste měli vždy měřit provádění kódu.  Například můžete najít sami sebe v situaci, kdy vaše práce vázaná na procesor není dostatečně nákladné ve srovnání s režií přepnutí kontextu při multithreading.  Každá volba má svůj kompromis, a měli byste si vybrat správný kompromis pro vaši situaci.

## <a name="more-examples"></a>Další příklady

Následující příklady ukazují různé způsoby, jak můžete psát asynchronní kód v C#.  Pokrývají několik různých scénářů, na které se můžete sejít.

### <a name="extracting-data-from-a-network"></a>Extrahování dat ze sítě

Tento úryvek stáhne HTML z domovské stránky v [www.dotnetfoundation.org](https://www.dotnetfoundation.org) a spočítá, kolikrát se řetězec ".NET" vyskytuje v HTML.  Používá ASP.NET MVC k definování metody webového kontroléru, která provádí tento úkol a vrací číslo.

> [!NOTE]
> Pokud plánujete analýzu HTML v produkčním kódu, nepoužívejte regulární výrazy. Místo toho použijte knihovnu analýzy.

```csharp
private readonly HttpClient _httpClient = new HttpClient();

[HttpGet]
[Route("DotNetCount")]
public async Task<int> GetDotNetCountAsync()
{
    // Suspends GetDotNetCountAsync() to allow the caller (the web server)
    // to accept another request, rather than blocking on this one.
    var html = await _httpClient.GetStringAsync("https://dotnetfoundation.org");

    return Regex.Matches(html, @"\.NET").Count;
}
```

Tady je stejný scénář napsaný pro univerzální aplikaci pro Windows, která provádí stejnou úlohu při stisknutí tlačítka:

```csharp
private readonly HttpClient _httpClient = new HttpClient();

private async void SeeTheDotNets_Click(object sender, RoutedEventArgs e)
{
    // Capture the task handle here so we can await the background task later.
    var getDotNetFoundationHtmlTask = _httpClient.GetStringAsync("https://www.dotnetfoundation.org");

    // Any other work on the UI thread can be done here, such as enabling a Progress Bar.
    // This is important to do here, before the "await" call, so that the user
    // sees the progress bar before execution of this method is yielded.
    NetworkProgressBar.IsEnabled = true;
    NetworkProgressBar.Visibility = Visibility.Visible;

    // The await operator suspends SeeTheDotNets_Click, returning control to its caller.
    // This is what allows the app to be responsive and not block the UI thread.
    var html = await getDotNetFoundationHtmlTask;
    int count = Regex.Matches(html, @"\.NET").Count;

    DotNetCountLabel.Text = $"Number of .NETs on dotnetfoundation.org: {count}";

    NetworkProgressBar.IsEnabled = false;
    NetworkProgressBar.Visibility = Visibility.Collapsed;
}
```

### <a name="waiting-for-multiple-tasks-to-complete"></a>Čekání na dokončení více úkolů

Můžete se ocitnout v situaci, kdy je třeba načíst více kusů dat současně.  Rozhraní `Task` API obsahuje `Task.WhenAll` dvě `Task.WhenAny` metody, které umožňují psát asynchronní kód, který provádí neblokující čekání na více úloh na pozadí.

Tento příklad ukazuje, `User` jak můžete uchopit data pro sadu `userId`s.

```csharp
public async Task<User> GetUserAsync(int userId)
{
    // Code omitted:
    //
    // Given a user Id {userId}, retrieves a User object corresponding
    // to the entry in the database with {userId} as its Id.
}

public static async Task<IEnumerable<User>> GetUsersAsync(IEnumerable<int> userIds)
{
    var getUserTasks = new List<Task<User>>();

    foreach (int userId in userIds)
    {
        getUserTasks.Add(GetUserAsync(userId));
    }

    return await Task.WhenAll(getUserTasks);
}
```

Zde je další způsob, jak napsat to trochu stručněji, pomocí LINQ:

```csharp
public async Task<User> GetUserAsync(int userId)
{
    // Code omitted:
    //
    // Given a user Id {userId}, retrieves a User object corresponding
    // to the entry in the database with {userId} as its Id.
}

public static async Task<User[]> GetUsersAsync(IEnumerable<int> userIds)
{
    var getUserTasks = userIds.Select(id => GetUserAsync(id));
    return await Task.WhenAll(getUserTasks);
}
```

I když je méně kódu, dávejte pozor při míchání LINQ s asynchronním kódem.  Protože LINQ používá odložené (opožděné) spuštění, asynchronní volání `foreach()` nedojde okamžitě jako ve smyčce, pokud vynutíte generované sekvence iterovat s voláním `.ToList()` nebo `.ToArray()`.

## <a name="important-info-and-advice"></a>Důležité informace a rady

Přestože asynchronní programování je poměrně jednoduché, existují některé podrobnosti, které je třeba mít na paměti, které mohou zabránit neočekávanému chování.

* `async`**metody musí mít** `await` **klíčové slovo ve svém těle, nebo se nikdy výnos!**

To je důležité mít na paměti.  Pokud `await` není použit v těle `async` metody, kompilátor Jazyka C# vygeneruje upozornění, ale kód bude kompilovat a spouštět, jako by to byla normální metoda.  Všimněte si, že by to také neuvěřitelně neefektivní, jako stavový počítač generovaný kompilátorem Jazyka C# pro asynchronní metodu by nebylo dosaženo nic.

* **Měli byste přidat "Async" jako příponu každého názvu asynchronní metody, kterou napíšete.**

Toto je konvence používaná v rozhraní .NET pro snadněji rozlišovací synchronní a asynchronní metody. Všimněte si, že některé metody, které nejsou explicitně volány vaším kódem (například obslužné rutiny událostí nebo metody webového kontroleru) nemusí nutně platit. Vzhledem k tomu, že tyto nejsou explicitně volány vaším kódem, explicitní o jejich pojmenování není tak důležité.

* `async void`**by měl být použit pouze pro obslužné rutiny událostí.**

`async void`je jediný způsob, jak povolit zpracování obslužných rutin asynchronních událostí, `Task` `Task<T>`protože události nemají návratové typy (proto nelze použít a ). Jakékoli jiné `async void` použití modelu TAP neodpovídá modelu TAP a může být náročné na použití, například:

* Výjimky vyzdvižené v metodě `async void` nelze zachytit mimo tuto metodu.
* `async void`metody jsou velmi obtížné testovat.
* `async void`metody mohou způsobit špatné vedlejší účinky, pokud volající neočekává, že budou asynchronní.

* **Při použití asynchronních lambdů ve výrazech LINQ opatrně**

Lambda výrazy v LINQ použít odložené spuštění, což znamená, že kód může skončit provádění v době, kdy nejste očekávali, že. Zavedení blokování úloh do tohoto může snadno vést k zablokování, pokud není napsánsprávně. Navíc vnoření asynchronního kódu, jako je tento může také ztížit důvod o provádění kódu. Async a LINQ jsou silné, ale měly by být používány společně co nejpečlivěji a nejjasněji.

* **Napište kód, který čeká úkoly neblokujícím způsobem**

Blokování aktuální vlákno jako prostředek čekání na task k dokončení může mít za následek zablokování a blokované podprocesů kontextu a může vyžadovat výrazně složitější zpracování chyb. Následující tabulka obsahuje pokyny, jak se vypořádat s čekáním na úkoly neblokujícím způsobem:

| Postup... | Místo tohohle... | Když si to přejí |
| --- | --- | --- |
| `await` | `Task.Wait` nebo `Task.Result` | Načítání výsledku úlohy na pozadí |
| `await Task.WhenAny` | `Task.WaitAny` | Čekání na dokončení jakékoli úlohy |
| `await Task.WhenAll` | `Task.WaitAll` | Čekání na dokončení všech úkolů |
| `await Task.Delay` | `Thread.Sleep` | Čekání na určitou dobu |

* **Zápis méně stavového kódu**

Nezávisí na stavu globálních objektů nebo provádění určitých metod. Místo toho závisí pouze na vrácené hodnoty metod. Proč?

* Kód bude snazší důvod.
* Kód bude snazší testovat.
* Míchání asynchronního a synchronního kódu je mnohem jednodušší.
* Sporičné podmínky lze obvykle zcela vyhnout.
* V závislosti na návratové hodnoty umožňuje koordinaci asynchronní kód jednoduché.
* (Bonus) to funguje opravdu dobře s závislostí injekce.

Doporučeným cílem je dosáhnout úplné nebo téměř úplné [referenční průhlednosti](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) ve vašem kódu. To bude mít za následek velmi předvídatelné, testovatelné a udržovatelné codebase.

## <a name="other-resources"></a>Další prostředky

* [Asynchronní hloubka](../standard/async-in-depth.md) poskytuje další informace o tom, jak úkoly fungují.
* [Asynchronní programování s asynchronní a čekat (C#)](./programming-guide/concepts/async/index.md)
* Lucian Wischik šest [základních tipů pro Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) jsou skvělý zdroj pro asynchronní programování
