---
title: Asynchronní programování –C#
description: Další informace o jazyce C# úrovni jazyka asynchronní programovací model poskytované .NET Core.
author: cartermp
ms.date: 06/20/2016
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.custom: seodec18
ms.openlocfilehash: a36f4a6f01c4e11429fda3a3022b4092e98db6cf
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212206"
---
# <a name="asynchronous-programming"></a>Asynchronní programování

Pokud máte jakékoli vstupně-výstupní požadavky (například požadavek na data ze sítě nebo přístup k databázi), budete chtít využívat asynchronní programování.  Můžete mít také vázané na procesor kódu, jako je například provádění nákladné výpočtu, která je také vhodné scénář pro psaní asynchronního kódu.

C# má úroveň jazyka asynchronní programovací model, který umožňuje snadno psaní asynchronního kódu bez nutnosti přehlednější zpětná volání nebo do knihovny, která podporuje asynchronii v souladu. Vyplývá, která se označuje jako [úkolově orientovanou asynchronní vzor (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).

## <a name="basic-overview-of-the-asynchronous-model"></a>Základní přehled asynchronní Model

Základem asynchronního programování je `Task` a `Task<T>` objekty, které model asynchronních operací.  Jsou podporovány `async` a `await` klíčová slova.  Model je ve většině případů poměrně jednoduchý:

Pro vstupně-výstupní kód můžete `await` operace, která vrátí `Task` nebo `Task<T>` uvnitř `async` metoda.

Pro kód vázané na procesor je `await` operace, která je spuštěna ve vlákně na pozadí s `Task.Run` metody.

`await` – Klíčové slovo je, kde se to všechno děje. Ovládací prvek bude vrácen volajícímu metody, která provádí `await`, a nakonec umožňuje být interaktivní uživatelské rozhraní nebo službu pružný.

Existují jiné způsoby, jak přístup asynchronní kód než `async` a `await` uvedených v článku TAP propojené výše, ale tento dokument se zaměřuje na úrovni jazyka konstrukce od této chvíle dál.

### <a name="io-bound-example-downloading-data-from-a-web-service"></a>Vstupně-výstupní příklad: Stahování dat z webové služby

Budete muset stáhnout data z webové služby při stisknutí tlačítka, ale nechcete, aby k blokování vlákna uživatelského rozhraní. To lze provést jednoduše takto:

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

A to je všechno! Kód vyjadřují záměr (stahuje se některá data asynchronně) bez získání energií v práci s objekty úloh.

### <a name="cpu-bound-example-performing-a-calculation-for-a-game"></a>Příklad vázané na procesor: Výpočty pro hru

Dejme tomu, že píšete mobilní hru, ve kterém stisknutím tlačítka může způsobit poškození na mnoho nepřátel na obrazovce.  Výpočty poškození může být nákladné a dělat na vlákně UI by vytvořit hru zobrazí pozastavit, jak se provádí výpočet!

Nejlepší způsob, jak se o to postarají je spuštění vlákna na pozadí, který provádí práci pomocí `Task.Run`, a `await` jeho výsledek.  To vám umožní uživatelského rozhraní pocit smooth, jak se provádí práci.

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

A to je všechno!  Tento kód čistě vyjadřují záměr kliknutím na tlačítko na událost, nevyžaduje ruční správu vlákna na pozadí a dělá to tak neblokující.

### <a name="what-happens-under-the-covers"></a>Co se stane, že na pozadí

Je hodně přesouvání položek, kde se týká asynchronních operací.  Pokud vás to zajímá o co se děje na pozadí `Task` a `Task<T>`, rezervace [asynchronní podrobné](../standard/async-in-depth.md) najdete další informace.

V C# straně věcí, kompilátor transformuje na stavový počítač, který uchovává informace o věci, jako je vracení provádění kódu při `await` je dosaženo a obnovení provádění po dokončení úlohy na pozadí.

Pro teoreticky sklon, toto je implementace [Promise modelu asynchronii](https://en.wikipedia.org/wiki/Futures_and_promises).

## <a name="key-pieces-to-understand"></a>Důležité porozumět

* Asynchronní kód můžete použít pro vstupně-výstupní a vázané na procesor kódu, ale jinak pro jednotlivé scénáře.
* Používá asynchronní kód `Task<T>` a `Task`, které jsou objektů, které používá model práce na pozadí.
* `async` – Klíčové slovo změní metodu na asynchronní metodu, která umožňuje používat `await` – klíčové slovo v těle.
* Když `await` – klíčové slovo se použijí, volání metody pozastaví a vrací řízení volajícímu zpět, dokud není dokončen očekávaný úkol.
* `await` jde použít jenom v asynchronní metodě.

## <a name="recognize-cpu-bound-and-io-bound-work"></a>Rozpoznat vázané na procesor a vstupně-výstupní práce

První dva příklady Tento průvodce vám ukázal, jak můžete `async` a `await` pro vstupně-výstupní a vázané na procesor práce.  Jeho klíč, který vám usnadní zjišťování se úlohy, je třeba provést je vstupně-výstupní nebo vázané na procesor, protože může výrazně ovlivnit výkon kódu a může potenciálně vést k zneužití určité vytvoří.

Tady jsou dva otázek, na které je třeba požádat předtím, než začnete psát kód:

1. Bude kód "čekat" něco, jako jsou data z databáze?

    Pokud vaše odpověď je "Ano", pak je práce **vstupně-výstupní**.

2. Bude kód provádět velmi náročné výpočty?

    Pokud jste odpověděli "Ano", pak je práce **vázané na procesor**.

Pokud je pracovní máte **vstupně-výstupní**, použijte `async` a `await` *bez* `Task.Run`.  Můžete *by neměla* použít Task Parallel Library.  Důvodem je popsaný v [asynchronní v článku hloubky](../standard/async-in-depth.md).

Pokud je pracovní máte **vázané na procesor** a péči o rychlosti odezvy, použijte `async` a `await` ale nejde vytvořit podřízený práce vypnout v jiném vlákně *s* `Task.Run`.  Pokud práce je vhodný pro souběžnost a paralelismu, měli byste také zvážit použití [Task Parallel Library](../standard/parallel-programming/task-parallel-library-tpl.md).

Kromě toho by měla vždy měření provádění kódu.  Například může být pro vás sami v situaci, kdy není nákladné práce vázané na procesor dostatečně ve srovnání s režií přepnutí kontextu při multithreadingu.  Každý volbou jeho kompromis, a měli byste vybrat správné kompromis pro vaše konkrétní potřeby.

## <a name="more-examples"></a>Další příklady

Následující příklady znázorňují různé způsoby, které můžete psát asynchronní kód v jazyce C#.  Několik různých scénářů, které můžete narazit na pokrývají.

### <a name="extracting-data-from-a-network"></a>Extrahování dat ze sítě

Tento fragment kódu HTML z domovské stránky na soubory ke stažení [www.dotnetfoundation.org](https://www.dotnetfoundation.org) a počet, kolikrát řetězec ".NET" vyvolá se v kódu HTML.  ASP.NET MVC používá k definování webové metody kontroleru, která tuto úlohu, vrací číslo.

> [!NOTE]
> Pokud máte v úmyslu provádět analýza v produkčním kódu HTML, nepoužívejte regulární výrazy. Místo toho použijte knihovnu analýzy.

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

Zde je stejný scénář napsané pro univerzální aplikace pro Windows, který provádí stejnou úlohu, když se stiskne tlačítko:

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
    // This is what allows the app to be responsive and not hang on the UI thread.
    var html = await getDotNetFoundationHtmlTask;
    int count = Regex.Matches(html, @"\.NET").Count;

    DotNetCountLabel.Text = $"Number of .NETs on dotnetfoundation.org: {count}";

    NetworkProgressBar.IsEnabled = false;
    NetworkProgressBar.Visibility = Visibility.Collapsed;
}
```

### <a name="waiting-for-multiple-tasks-to-complete"></a>Čekání na dokončení více úloh

Může být pro vás sami v situaci, kde je potřeba načíst data na více místech současně.  `Task` Rozhraní API obsahuje dvě metody `Task.WhenAll` a `Task.WhenAny` který umožňuje psát asynchronní kód, který provádí čekání bez blokování na víc úloh na pozadí.

Tento příklad ukazuje, jak může vzít `User` data pro sadu `userId`s.

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

Tady je další způsob, jak to trochu více stručně zapsat pomocí jazyka LINQ:

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

I když je tolik kódu, aby se postaral při kombinování LINQ s asynchronní kód.  Vzhledem k tomu LINQ používá odložené provedení (opožděné), asynchronní volání se neprovede okamžitě stejně jako `foreach()` smyčky není-li vynutit generovaného sekvenčního k iteraci pomocí volání `.ToList()` nebo `.ToArray()`.

## <a name="important-info-and-advice"></a>Důležité informace a Rady

Přestože je poměrně přímočarý asynchronní programování, existují některé podrobnosti potřeba mít na paměti, což může zabránit neočekávanému chování.

* `async` **metody musí mít** `await` **– klíčové slovo v jejich obsahu nebo se nikdy yield!**

To je důležité si pamatovat.  Pokud `await` není použit v těle `async` metoda, C# kompilátor bude generovat upozornění, ale bude kód zkompilovat a spustit jako by šlo normální metody.  Pamatujte, že to by také být velmi neefektivní, jako by být provádění stavového stroje generovaný kompilátorem jazyka C# pro asynchronní metody, cokoli.

* **Jako přípona názvu každý asynchronní metoda, který napíšete, měli byste přidat "Async".**

Toto je konvence v rozhraní .NET pro snadněji rozlišit synchronní a asynchronní metody. Všimněte si, že některé metody, které nejsou explicitně volána ve vašem kódu (například obslužné rutiny událostí nebo metody kontroleru webového) není nemusí nezbytně vztahovat. Protože tyto nejsou volány explicitně pomocí kódu, se explicitní o jejich pojmenování není důležité.

* `async void` **by měla sloužit pouze pro obslužné rutiny událostí.**

`async void` je jediný způsob, jak povolit asynchronní obslužné rutiny pracovat, protože události nemají návratové typy (tedy nemůže provádět využívání `Task` a `Task<T>`). Jakékoli další použití `async void` nedodržuje vzoru TAP a může být náročné, pokud chcete použít, jako například:

* Výjimky vyvolané `async void` metoda nemůže být zachycena mimo tuto metodu.
* `async void` metody jsou velmi obtížné testování.
* `async void` metod může způsobit špatné vedlejší účinky, pokud volající není očekáván je asynchronní.

* **Pečlivě běhounu při použití asynchronní výrazy lambda v LINQ – výrazy**

Výrazy lambda v jazyce LINQ pomocí odloženého provedení, můžou být nakonec význam kódu v době, kdy, jestliže neočekáváte na provádění. Po zavedení služby blokování úloh do tohoto může snadno způsobit zablokování Pokud nezapíše se správně. Kromě toho vnoření asynchronní kód tímto způsobem můžete také to ztížit argumentovat o provádění kódu. Asynchronní a LINQ jsou velmi výkonné, ale má být použit společně jako pečlivě a co je to možné.

* **Napsat kód, který čeká na úkoly způsobem neblokující**

Blokuje aktuální vlákno jako prostředek k čekání na dokončení úkolu může způsobit zablokování a konflikty blokované kontextu vlákna a můžou vyžadovat, aby výrazně složitějších zpracování chyb. Následující tabulka obsahuje pokyny k řešení problémů s čekání na neblokující způsobem úkolů:

| Použijte tento... | Místo to... | Když chce udělat |
| --- | --- | --- |
| `await` | `Task.Wait` Nebo `Task.Result` | Načítání výsledků úlohy na pozadí |
| `await Task.WhenAny` | `Task.WaitAny` | Čekání na dokončení úkolu |
| `await Task.WhenAll` | `Task.WaitAll` | Čekání na dokončení všech úloh |
| `await Task.Delay` | `Thread.Sleep` | Čekání na časový úsek |

* **Zápis méně stavový kód**

Nejsou závislé na stavu globálních objektů nebo provádění některých metod. Místo toho záviset pouze na návratové hodnoty metod. Proč?

  * Kód bude jednodušší argumentovat o.
  * Kód bude snazší testování.
  * Kombinace asynchronní a synchronní kód je mnohem jednodušší.
  * Ke konfliktům časování obvykle vyhnout úplně.
  * V závislosti na návratové hodnoty zjednodušuje koordinační asynchronní kód.
  * (Bonusové) je velice dobře funguje pro vkládání závislostí.

Doporučené cílem je dosáhnout úplné nebo téměř úplnou [referenční transparentnosti](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) ve vašem kódu. To způsobí velmi předvídatelné, možností intenzivního testování a udržovatelný kód.

## <a name="other-resources"></a>Další zdroje

* [Asynchronní podrobné](../standard/async-in-depth.md) poskytuje další informace o tom, jak pracují úkoly.
* [Asynchronní programování pomocí modifikátoru async a operátoru await (C#)](./programming-guide/concepts/async/index.md)
* Lucian Wischik [šest důležité tipy pro asynchronní](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) jsou vynikající prostředku pro asynchronní programování