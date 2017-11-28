---
title: "Asynchronní programování"
description: "Další informace o C# úroveň jazyka asynchronní programovací model poskytované .NET Core."
keywords: "Rozhraní .NET, .NET core"
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.openlocfilehash: dc9b45e21f15ad92304685a1aff6760f3406cee2
ms.sourcegitcommit: 43c656811dd38a66a6672084c65d10c0cbbf2015
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2017
---
# <a name="asynchronous-programming"></a>Asynchronní programování

Pokud máte všechny požadavky I/čítači (například požadavek na data v síti nebo přístup k databázi), budete chtít využívat asynchronní programování.  Můžete mít také kód vázané na procesor, například při provádění nákladné výpočtu, která je také funkční scénář pro psaní kódu asynchronní.

C# má úroveň jazyka asynchronní programovací model, který umožňuje snadno psaní kódu asynchronní bez nutnosti přehlednější zpětná volání nebo do knihovny, která podporuje asynchrony v souladu. Vyplývá z toho, která se označuje jako [založený na úlohách asynchronní vzor (TAP)](https://msdn.microsoft.com/library/hh873175.aspx).

## <a name="basic-overview-of-the-asynchronous-model"></a>Základní přehled asynchronní modelu

Základní programování asynchronních jsou `Task` a `Task<T>` objekty, které model asynchronní operace.  Jsou podporovány `async` a `await` klíčová slova.  Model je docela jednoduché ve většině případů: 

Pro kód I/čítači můžete `await` operace, která vrátí hodnotu `Task` nebo `Task<T>` uvnitř `async` metoda.

Pro kód vázané na procesor můžete `await` operace, který se spouští na vlákna na pozadí s `Task.Run` metoda.

`await` – Klíčové slovo je, kde se stane magic. Ovládací prvek bude vrácen volajícímu metody, která provádí `await`, a nakonec umožňuje uživatelského rozhraní jako odpovídající nebo elastické služby.

Existují jiné způsoby kódu asynchronní metodu než `async` a `await` uvedených v článku klepněte na uvedený výše, ale tento dokument se soustředí na úrovni jazykové konstrukty od tohoto okamžiku.

### <a name="io-bound-example-downloading-data-from-a-web-service"></a>Příklad I/čítači: stahování dat z webové služby

Budete muset stáhnout některá data z webové služby, při stisknutí tlačítka, ale nechcete, aby k blokování vlákna uživatelského rozhraní. Dosáhnete jednoduše takto:

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

A je to! Kód vyjadřoval záměr (asynchronně stahování některá data), aniž zabřednete v interakci s objekty úloh.

### <a name="cpu-bound-example-performing-a-calculation-for-a-game"></a>Příklad vázané na procesor: Provádění výpočtu pro hry

Řekněme, že píšete mobilní hru kde stisknutím tlačítka může způsobit poškození v mnoha nepřátel na obrazovce.  Provádění výpočtu poškození může být náročná, a to ve vlákně UI by proveďte hra, zobrazí se pozastavit, jak se provádí výpočet!

Nejlepší způsob, jak to se dá začít vlákna na pozadí, která zajišťuje pomocí pracovní `Task.Run`, a `await` její výsledek.  To vám umožní Uživatelském rozhraní působí smooth, jako práce.

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

A je to!  Tento kód ještě jednou vyjadřoval záměr události kliknutí na tlačítko, není třeba ručně Správa vlákna na pozadí a učiní tak způsobem neblokující.

### <a name="what-happens-under-the-covers"></a>Co se stane skrytě

Existuje mnoho přesunutí částí, kde jsou problémem asynchronní operace.  Pokud se chcete zjistit, co se děje pod zahrnuje z `Task` a `Task<T>`, najdete v článku věnovaném [asynchronní podrobný](../standard/async-in-depth.md) Další informace najdete v článku.

Na C# straně věcí, kompilátor transformuje na stavu počítače, která uchovává informace o takové věci, jako je spuštění kódu při `await` se dosáhlo maximálního a opětovné spuštění, až se dokončí úlohu na pozadí.

U teoreticky sklon, je to implementace [Promise Model asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises).

## <a name="key-pieces-to-understand"></a>Důležité pochopit

*   Asynchronní kódu je možné kódu I/čítači a vázané na procesor, ale jinak pro jednotlivé scénáře.
*   Asynchronní kód používá `Task<T>` a `Task`, které jsou konstrukce používané k modelu práci probíhá na pozadí.
* `async` – Klíčové slovo změní metoda do asynchronní metody, která umožňuje používat `await` – klíčové slovo v jeho obsahu.
*   Když `await` – klíčové slovo se použije, volání metody pozastaví a vypočítá řízení zpět do jeho volajícího, až do dokončení awaited úloh.
*   `await`dá se použít jenom uvnitř asynchronní metody.

## <a name="recognize-cpu-bound-and-io-bound-work"></a>Rozpoznat vázané na procesor a I/čítači práce

První dva příklady Tento průvodce vám ukázal, jak můžete použít `async` a `await` pro pracovní I/čítači a vázané na procesor.  Jeho klíč, který je možné určit úlohy, je potřeba udělat I/čítači nebo vázané na procesor, protože může výrazně ovlivnit výkon kódu a může potenciálně vést k zneužití určité vytvoří.

Zde jsou dva otázek, na které je třeba požádat před psaní jakéhokoli kódu:

1. Bude kód "čekat" něco, třeba dat z databáze?

    Pokud je vaše odpověď "Ano", pak je práce **I/čítači**.

2. Bude kód provádět velmi náročná výpočet?

    Pokud jste odpověděli "Ano", pak je práce **vázané na procesor**.
    
Pokud je pracovní máte **I/čítači**, použijte `async` a `await` *bez* `Task.Run`.  Můžete *neměli* použít Task Parallel Library.  Důvodem je uvedené v [asynchronní v článku hloubka](../standard/async-in-depth.md).

Pokud je pracovní máte **vázané na procesor** a kterých vám nejvíc záleží kratší reakční doby, použijte `async` a `await` ale spawn práce vypnout na jiné vlákno *s* `Task.Run`.  Pokud je vhodná pro concurrency a paralelismus práce, měli byste také zvážit použití Task Parallel Library.

Kromě toho by měla vždycky měření provádění kódu.  Například sami zjistíte v situaci, kdy není nákladná práci vázané na procesor dostatečně porovnání s nároky na kontext přepínačů při více vláken.  Všechny možnosti je jeho kompromis a měli byste vybrat správný kompromis pro vaši situaci.

## <a name="more-examples"></a>Další příklady

Následující příklady ukazují různé způsoby, můžete napsat kód asynchronní v jazyce C#.  Jejich zahrnují několik různých scénářů, které můžete narazit na.

### <a name="extracting-data-from-a-network"></a>Extrakce dat ze sítě

Tento fragment kódu HTML z www.dotnetfoundation.org a udává počet, kolikrát řetězec ".NET" dochází v kódu HTML.  ASP.NET MVC používá k definování webové metody řadiče, který provádí tato úloha vrácení číslo.

> [!NOTE]
> Pokud máte v úmyslu provádět analýzy v produkčním kódu HTML, nepoužívejte regulární výrazy. Místo toho použijte knihovnu analýzy.

```csharp
private readonly HttpClient _httpClient = new HttpClient();

[HttpGet]
[Route("DotNetCount")]
public async Task<int> GetDotNetCountAsync()
{
    // Suspends GetDotNetCountAsync() to allow the caller (the web server)
    // to accept another request, rather than blocking on this one.
    var html = await _httpClient.DownloadStringAsync("http://dotnetfoundation.org");

    return Regex.Matches(html, @"\.NET").Count;
}
```

Zde je stejný scénář napsané pro univerzální aplikace pro Windows, který provádí stejnou úlohu při stisknutí tlačítka:

```csharp
private readonly HttpClient _httpClient = new HttpClient();

private async void SeeTheDotNets_Click(object sender, RoutedEventArgs e)
{
    // Capture the task handle here so we can await the background task later.
    var getDotNetFoundationHtmlTask = _httpClient.GetStringAsync("http://www.dotnetfoundation.org");

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
    NetworkProgressBar.Visbility = Visibility.Collapsed;
}
```

### <a name="waiting-for-multiple-tasks-to-complete"></a>Čekání na dokončení více úloh

Sami zjistíte v situaci, kdy potřebujete souběžně načtení dat na více místech.  `Task` Rozhraní API obsahuje dvě metody, `Task.WhenAll` a `Task.WhenAny` které umožňují napsat asynchronní kód, který provádí neblokující čekání na více úloh na pozadí.

Tento příklad ukazuje, jak může získat `User` data pro sadu `userId`s.

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

Zde je další způsob, jak to trochu více stručně zapsat pomocí LINQ:

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
Přestože je méně kódu, vezměte v potaz při kombinování LINQ asynchronní kódem.  Protože LINQ používá odložené provedení (lazy), asynchronní volání nedojde k ní okamžitě nebudou `foreach()` cykly, pokud vynutíte generovaného pořadí k iteraci pomocí volání `.ToList()` nebo `.ToArray()`.

## <a name="important-info-and-advice"></a>Důležité informace a Rady, jak

I když je relativně jednoduché asynchronní programování, nejsou některé podrobnosti k mějte na paměti, která může zabránit neočekávanému chování.

*  `async`**metody musí mít** `await` **– klíčové slovo v jejich textu nebo nikdy předá!**

To je důležité pamatovat.  Pokud `await` není použit v textu `async` metoda, C# kompilátoru bude generovat upozornění, ale kód bude zkompilování a spuštění, jako kdyby šlo o normální metody.  Všimněte si, že také bude velmi neefektivní, jako by být splníte stav stavového stroje generované kompilátor jazyka C# pro asynchronní metody, nic.

*   **Měli byste přidat "Asynchronní" jako přípona názvů každých asynchronní metoda, kterou píšete.**

Toto je názvů v rozhraní .NET sloužící k další snadno odlišení synchronní a asynchronní metody. Všimněte si, že některé metody, které nejsou výslovně volány váš kód (například obslužné rutiny událostí nebo metody kontroleru webového) není nemusí nezbytně vztahovat. Protože tyto nejsou ve vašem kódu explicitně volané, probíhá explicitní o jejich názvy není jako důležité.

*   `async void`**musí být použit pouze pro obslužné rutiny událostí.**

`async void`je jediný způsob, jak povolit obslužné rutiny událostí asynchronní pracovat, protože události nemají návratové typy (proto nelze provést použití `Task` a `Task<T>`). Jakékoliv jiné použití `async void` nedodrží klepněte na modelu a může být náročné, pokud chcete použít, například:

  *   Výjimky vzniklé v `async void` metoda nemůže být zachycena mimo tuto metodu.
  *   `async void`metody jsou velmi obtížné otestovat.
  *   `async void`metody může způsobit chybný vedlejší účinky, pokud má volající není očekáván mají být asynchronní.

*   **Pečlivě běhounu při použití asynchronní lambdas v LINQ – výrazy**

Výrazy lambda v technologii LINQ použít odložené provedení, může stát, že kód význam provádění v době, kdy neočekáváte jej do. Zavedení blokování do této úlohy můžete snadno následek zablokování, pokud není správně zapsaná. Kromě toho vnoření asynchronní kódu jako to provést také ho obtížnější důvod o provádění kódu. Async a LINQ jsou efektivní, ale má být použit společně jako pečlivě a jasně nejblíže.

*   **Napsat kód, který čeká úlohy způsobem neblokující**

Blokování aktuální vlákno jako prostředek k čekání na dokončení úlohy může způsobit zablokování a blokovaný kontextu vláken a může vyžadovat mnohem složitější zpracování chyb. Následující tabulka obsahuje pokyny k řešení problémů s čekání úlohy způsobem neblokující:

| Použijte... | Místo to... | Pokud chtějí tomu |
| --- | --- | --- |
| `await` | `Task.Wait`nebo`Task.Result` | Načítání výsledek úlohy na pozadí |
| `await Task.WhenAny` | `Task.WaitAny` | Čekání na dokončení žádné úlohy |
| `await Task.WhenAll` | `Task.WaitAll` | Čekání na dokončení všech úloh |
| `await Task.Delay` | `Thread.Sleep` | Čekání na v časovém intervalu |

*   **Napsat méně stavový kód**

Nemáte závisí na stavu globální objekty nebo provádění určitých metody. Místo toho závisí pouze na vrácených hodnotách metod. Proč?

  *   Kód bude jednodušší důvod o.
  *   Kód bude jednodušší k testování.
  *   Kombinování asynchronní a synchronní kód je mnohem jednodušší.
  *   Obvykle se vyhnout zcela časování.
  *   V závislosti na vrácených hodnotách i koordinující asynchronní kódu.
  *   (Bonusové) funguje dobře skutečně s vkládání závislostí.

Doporučené cílem je dosáhnout úplné nebo téměř úplné [referenční průhlednost](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) ve vašem kódu. Díky tomu bude výsledkem codebase velmi předvídatelný, možností intenzivního testování a udržovatelný.

## <a name="other-resources"></a>Další zdroje

* [Asynchronní podrobný](../standard/async-in-depth.md) poskytuje další informace o fungování úlohy.
* Lucian Wischik [šesti důležité tipy pro asynchronní](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) jsou vynikající prostředků pro asynchronní programování
