---
title: 'Asynchronní programování – C #'
description: Přečtěte si o asynchronním programovacím modelu C#, který poskytuje .NET Core, na úrovni jazyka C#.
author: cartermp
ms.date: 05/20/2020
ms.technology: csharp-async
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.openlocfilehash: b5643dd7eddefebc9cbf922ff5cce75d72dee4dd
ms.sourcegitcommit: 4ad2f8920251f3744240c3b42a443ffbe0a46577
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/08/2020
ms.locfileid: "86100896"
---
# <a name="asynchronous-programming"></a>Asynchronní programování

Pokud máte nějaké požadavky na vstupně-výstupní operace (například vyžádání dat ze sítě, přístup k databázi nebo čtení a zápis do systému souborů), budete chtít využít asynchronní programování. Můžete mít také kód vázaný na procesor, jako je například provádění nákladného výpočtu, což je také dobrý scénář pro psaní asynchronního kódu.

Jazyk C# má model asynchronního programování na úrovni jazyka, který umožňuje snadné psaní asynchronního kódu bez nutnosti juggle zpětná volání nebo odpovídat knihovně, která podporuje asynchronii. Postupuje podle toho, co se říká [asynchronní vzor založený na úlohách (klepněte)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).

## <a name="overview-of-the-asynchronous-model"></a>Přehled asynchronního modelu

Základem asynchronního programování jsou `Task` `Task<T>` objekty a, které modelují asynchronní operace. Jsou podporovány pomocí `async` `await` klíčových slov a. Model je ve většině případů velmi jednoduchý:

- Pro kód vázaný na vstupně-výstupní operace očekáváte operaci, která vrací `Task` nebo `Task<T>` uvnitř `async` metody.
- Pro kód vázaný na procesor očekáváte operaci, která je spuštěna ve vlákně na pozadí s <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> metodou.

`await`Klíčové slovo je místo, kde dojde k Magic. Poskytuje řízení volajícímu metody, kterou provedl `await` , a nakonec umožňuje, aby uživatelské rozhraní mohlo reagovat nebo služba měla být Elasticka. I když [existují způsoby](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) přístupu k asynchronnímu kódu, který je jiný než `async` a `await` , Tento článek se zaměřuje na konstrukce na úrovni jazyka.

### <a name="io-bound-example-download-data-from-a-web-service"></a>Vstup/výstup – příklad vazby: stažení dat z webové služby

Může být nutné stáhnout některá data z webové služby, když je stisknuto tlačítko, ale nechcete zablokovat vlákno uživatelského rozhraní. Můžete to provést takto:

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

Kód vyjadřuje záměr (asynchronní stahování dat) bez nutnosti zabřednete v interakci s `Task` objekty.

### <a name="cpu-bound-example-perform-a-calculation-for-a-game"></a>Příklad vázaný na procesor: provedení výpočtu pro hru

Řekněme, že píšete mobilní hru, kde stisknutí tlačítka může způsobit poškození mnoha Enemies na obrazovce. Provádění výpočtu škod může být nákladné a jeho provedení na vlákně UI by vedlo k tomu, že se hra po provedení výpočtu zastaví.

Nejlepším způsobem, jak to zpracovat, je spustit vlákno na pozadí, které funguje pomocí `Task.Run` a očekávat jeho výsledek pomocí `await` . Díky tomu může uživatelské rozhraní cítit plynulé fungování práce.

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
    // performs its work. The UI thread is free to perform other work.
    var damageResult = await Task.Run(() => CalculateDamageDone());
    DisplayDamage(damageResult);
};
```

Tento kód čistě vyjadřuje záměr události kliknutí na tlačítko, nevyžaduje ruční správu vlákna na pozadí a je tak neblokujícím způsobem.

### <a name="what-happens-under-the-covers"></a>Co se stane v rámci pokrývání

Existuje mnoho pohybujících se částí, ve kterých se jedná o asynchronní operace. Pokud jste zajímái o tom, co se děje `Task` `Task<T>` , a další informace najdete [v](../standard/async-in-depth.md) podrobném článku.

Na straně jazyka C# kompilátor transformuje váš kód do stavového počítače, který uchovává informace o tom, jako je například vracení provádění při `await` dosažení a obnovení spuštění po dokončení úlohy na pozadí.

Pro teoreticky-skloněnou je to implementace [modelu asynchronii pro příslib](https://en.wikipedia.org/wiki/Futures_and_promises).

## <a name="key-pieces-to-understand"></a>Klíčové kousky, které je potřeba pochopit

* Asynchronní kód lze použít pro vstupně-výstupní operace i pro kód vázaný na procesor, ale pro každý scénář odlišně.
* Asynchronní kód používá `Task<T>` a `Task` , které jsou konstrukce používané k modelování práce prováděné na pozadí.
* `async`Klíčové slovo převede metodu do asynchronní metody, která umožňuje použití `await` klíčového slova v těle.
* Při `await` použití klíčového slova pozastaví volající metodu a vrátí řízení volajícímu, dokud není dokončen očekávaný úkol.
* `await`dá se použít jenom uvnitř asynchronní metody.

## <a name="recognize-cpu-bound-and-io-bound-work"></a>Rozpoznání práce vázané na procesor a vstupně-výstupní operace

První dva příklady této příručky ukázaly, jak můžete použít `async` a `await` pro vstupně-výstupní operace a práci vázané na procesor. Je klíč, který můžete identifikovat, když je potřeba udělat úlohu, která je vázaná na vstupně-výstupní operace, nebo na základě procesoru, protože může významně ovlivnit výkon kódu a může potenciálně vést k omylům s některými konstrukcemi.

Tady jsou dvě otázky, které byste měli před psaním kódu zeptat:

1. Bude váš kód "čekání" na něco, například data z databáze?

   Pokud je vaše odpověď "Ano", vaše práce je **vázána na vstup/výstup**.

1. Bude váš kód provádět nákladný výpočet?

   Pokud jste odpověděli na Ano, vaše práce bude **vázaná na procesor**.

Pokud je práce, kterou jste **vázáni na vstup/výstup**, použijte `async` a `await` *bez* `Task.Run` . *Neměli byste* používat Task Parallel Library. Důvod je popsaný v části Async v rámci [hloubky](../standard/async-in-depth.md).

Pokud je práce **vázaná na procesor** a Vy se zajímáte o odezvu, použijte `async` a `await` , ale zapněte práci na jiném vlákně *with* `Task.Run` . Pokud je práce vhodná pro souběžnost a paralelismu, zvažte také použití [paralelní knihovny Task](../standard/parallel-programming/task-parallel-library-tpl.md).

Kromě toho byste měli vždy změřit provádění kódu. Například se můžete setkat v situaci, kdy práce vázaná na procesor není ve srovnání s režií kontextových přepínačů v případě multithreadingu dostatečně nákladná. Každá volba má své kompromisy a měli byste si vybrat správné kompromisy pro vaši situaci.

## <a name="more-examples"></a>Další příklady

Následující příklady ukazují různé způsoby, jak lze v jazyce C# napsat asynchronní kód. Pokrývají několik různých scénářů, které se mohou nacházet v rámci.

### <a name="extract-data-from-a-network"></a>Extrakce dat ze sítě

Tento fragment kódu stáhne kód HTML z domovské stránky <https://dotnetfoundation.org> a spočítá počet výskytů řetězce ".NET" v HTML. Používá ASP.NET k definování metody kontroleru webového rozhraní API, která provádí tuto úlohu a vrací číslo.

> [!NOTE]
> Pokud plánujete provádění analýzy HTML v produkčním kódu, nepoužívejte regulární výrazy. Místo toho použijte analýzu knihovny.

```csharp
private readonly HttpClient _httpClient = new HttpClient();

[HttpGet, Route("DotNetCount")]
public async Task<int> GetDotNetCount()
{
    // Suspends GetDotNetCount() to allow the caller (the web server)
    // to accept another request, rather than blocking on this one.
    var html = await _httpClient.GetStringAsync("https://dotnetfoundation.org");

    return Regex.Matches(html, @"\.NET").Count;
}
```

Tady je stejný scénář, který je napsán pro univerzální aplikaci pro Windows, která při stisknutí tlačítka provede stejnou úlohu:

```csharp
private readonly HttpClient _httpClient = new HttpClient();

private async void OnSeeTheDotNetsButtonClick(object sender, RoutedEventArgs e)
{
    // Capture the task handle here so we can await the background task later.
    var getDotNetFoundationHtmlTask = _httpClient.GetStringAsync("https://dotnetfoundation.org");

    // Any other work on the UI thread can be done here, such as enabling a Progress Bar.
    // This is important to do here, before the "await" call, so that the user
    // sees the progress bar before execution of this method is yielded.
    NetworkProgressBar.IsEnabled = true;
    NetworkProgressBar.Visibility = Visibility.Visible;

    // The await operator suspends OnSeeTheDotNetsButtonClick(), returning control to its caller.
    // This is what allows the app to be responsive and not block the UI thread.
    var html = await getDotNetFoundationHtmlTask;
    int count = Regex.Matches(html, @"\.NET").Count;

    DotNetCountLabel.Text = $"Number of .NETs on dotnetfoundation.org: {count}";

    NetworkProgressBar.IsEnabled = false;
    NetworkProgressBar.Visibility = Visibility.Collapsed;
}
```

### <a name="wait-for-multiple-tasks-to-complete"></a>Počkejte na dokončení více úloh.

Můžete se setkat v situaci, kdy potřebujete současně načíst více dat. `Task`Rozhraní API obsahuje dvě metody <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> , které umožňují napsat asynchronní kód, který provádí neblokující čekání na více úloh na pozadí.

Tento příklad ukazuje, jak můžete vyjímat `User` data pro sadu `userId` s.

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

Tady je další způsob, jak tento příklad napsat stručně pomocí LINQ:

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

I když je to méně kódu, při kombinování LINQ s asynchronním kódem je potřeba dbát. Vzhledem k tomu, že LINQ používá odložené (opožděné) provádění, asynchronní volání nebudou provedena ihned stejně jako ve `foreach` smyčce, pokud vynutíte vygenerování sekvence pro iteraci voláním `.ToList()` nebo `.ToArray()` .

## <a name="important-info-and-advice"></a>Důležité informace a Rady

V případě asynchronního programování jsou k dispozici nějaké podrobnosti, které vám pomůžou zabránit neočekávanému chování.

* `async`**metody musí mít** `await` **klíčové slovo ve svém těle, nebo nikdy nebude vracet!**

  To je důležité mít na paměti. Pokud `await` se v těle metody nepoužívá `async` , kompilátor C# vygeneruje upozornění, ale kód se zkompiluje a spustí, jako kdyby šlo o běžnou metodu. To je neuvěřitelně neefektivní, protože Stavový počítač generovaný kompilátorem jazyka C# pro asynchronní metodu neprovádí žádné výsledky.

* **Jako příponu každého názvu asynchronní metody, kterou píšete, byste měli přidat "Async".**

Toto je konvence, která se používá v rozhraní .NET k jednoduššímu odlišení synchronních a asynchronních metod. Některé metody, které nejsou explicitně volány vaším kódem (například obslužné rutiny událostí nebo metody webového kontroleru), nemusí nutně platit. Vzhledem k tomu, že nejsou explicitně volány vaším kódem, je explicitní informace o jejich pojmenování nevýznamná.

* `async void`**by mělo být použito pouze pro obslužné rutiny událostí.**

`async void`je jediným způsobem, jak povolit fungování asynchronních obslužných rutin událostí, protože události nemají návratové typy (proto nemohou použít `Task` a `Task<T>` ). Jakékoli jiné použití se `async void` neřídí modelem klepnutí a může být náročné na použití, například:

* Výjimky vyvolané v `async void` metodě nejde zachytit mimo tuto metodu.
* `async void`metody jsou obtížné testovat.
* `async void`metody mohou způsobit špatné vedlejší účinky, pokud volající neočekává, že budou Async.

* **Při použití asynchronních výrazů lambda ve výrazech LINQ pečlivě běhouny**

Výrazy lambda v jazyce LINQ používají odložené provádění, což znamená, že kód může být spuštěn v okamžiku, kdy ho neočekáváte. Zavedení blokujících úloh do této operace může snadno vést k zablokování, pokud není správně napsáno. Kromě toho vnořování asynchronního kódu, jako je, může také ztížit důvod spuštění kódu. Asynchronní a LINQ jsou výkonné, ale měly by být používány společně co nejdříve a jasně.

* **Napsat kód, který čeká na úlohy bez blokování**

Blokování aktuálního vlákna jako prostředku pro čekání `Task` na dokončení může způsobit zablokování a blokované kontextová vlákna a může vyžadovat složitější zpracování chyb. V následující tabulce najdete pokyny, jak se zabývat čekáním na úlohy neblokujícím způsobem:

| Postup...          | Místo...           | Kdy to chcete udělat...                 |
|----------------------|------------------------------|--------------------------------------------|
| `await`              | `Task.Wait` nebo `Task.Result` | Načítání výsledku úlohy na pozadí |
| `await Task.WhenAny` | `Task.WaitAny`               | Čeká se na dokončení všech úloh.           |
| `await Task.WhenAll` | `Task.WaitAll`               | Čeká se na dokončení všech úloh.          |
| `await Task.Delay`   | `Thread.Sleep`               | Čekání na časový úsek               |

* **Zvažte použití** `ValueTask` **Pokud je to možné**

Vrácení `Task` objektu z asynchronních metod může způsobit kritické body výkonu v určitých cestách. `Task`je odkazový typ, takže jeho použití znamená přidělení objektu. V případech, kdy metoda deklarovaná s `async` modifikátorem vrací výsledek uložený v mezipaměti nebo se dokončí synchronně, se další přidělení můžou stát značnými náklady v částech kritického výkonu v kódu. Pokud dojde k přidělení v těsných smyčkách, může to být nákladné. Další informace naleznete v tématu [generalizované asynchronní návratové typy](whats-new/csharp-7.md#generalized-async-return-types).

* **Zvažte použití**`ConfigureAwait(false)`

Běžnou otázkou je, "kdy mám použít <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> metodu?". Metoda umožňuje `Task` instanci nakonfigurovat svůj operátor await. To je důležitý aspekt a jeho nesprávné nastavení by mohlo mít dopad na výkon a dokonce i zablokování. Další informace o najdete v `ConfigureAwait` tématu [ConfigureAwait – Nejčastější dotazy](https://devblogs.microsoft.com/dotnet/configureawait-faq).

* **Zápis méně stavového kódu**

Nezávisí na stavu globálních objektů nebo provádění určitých metod. Místo toho závisí pouze na vrácených hodnotách metod. Proč?

* Kód bude z důvodu snazší.
* Testování kódu bude snazší.
* Kombinování asynchronního a synchronního kódu je mnohem jednodušší.
* Konflikty časování se obvykle můžou vyvarovat zcela.
* V závislosti na vrácených hodnotách je jednodušší koordinovat asynchronní kód.
* (Bonus) funguje ve skutečnosti i při vkládání závislostí.

Doporučeným cílem je dosáhnout úplné nebo téměř úplné [referenční transparentnosti](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) ve vašem kódu. Výsledkem je mimořádně předvídatelný, testovatelné a udržovatelný základ kódu.

## <a name="other-resources"></a>Další prostředky

* [Async-Depth](../standard/async-in-depth.md) poskytuje další informace o práci s úkoly.
* [Asynchronní programování s modifikátorem Async a operátoru Await (C#)](./programming-guide/concepts/async/index.md)
* [Šest důležitých tipů pro Lucian Wischik pro Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) je vynikajícím prostředkem pro asynchronní programování.
