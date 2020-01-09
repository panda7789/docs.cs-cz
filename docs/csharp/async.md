---
title: Asynchronní programování –C#
description: Seznamte se C# s asynchronním programovacím modelem na úrovni jazyka, který poskytuje .NET Core.
author: cartermp
ms.date: 06/20/2016
ms.technology: csharp-async
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.openlocfilehash: 38d7c856e9a536db9ef26349175ad440a49f5fe2
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713952"
---
# <a name="asynchronous-programming"></a>Asynchronní programování

Pokud máte nějaké požadavky na vstupně-výstupní operace (například vyžádání dat ze sítě nebo přístup k databázi), budete chtít využít asynchronní programování.  Můžete mít také kód vázaný na procesor, jako je například provádění nákladného výpočtu, což je také dobrý scénář pro psaní asynchronního kódu.

C#má model asynchronního programování na úrovni jazyka, který umožňuje snadno psát asynchronní kód bez nutnosti juggle zpětná volání nebo odpovídat knihovně, která podporuje asynchronii. Postupuje podle toho, co se říká [asynchronní vzor založený na úlohách (klepněte)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).

## <a name="basic-overview-of-the-asynchronous-model"></a>Základní přehled asynchronního modelu

Základem asynchronního programování jsou objekty `Task` a `Task<T>`, které modelují asynchronní operace.  Jsou podporovány `async` a `await` klíčová slova.  Model je ve většině případů velmi jednoduchý:

Pro vstupně-výstupní kód s vazbou `await` operace, která vrací `Task` nebo `Task<T>` uvnitř metody `async`.

V případě kódu vázaného na procesor `await` operace, která je spuštěna ve vlákně na pozadí s metodou `Task.Run`.

Klíčovým slovem `await` je místo, kde se Magic stane. Poskytuje řízení volajícímu metody, která provedla `await`, a nakonec umožňuje, aby uživatelské rozhraní mohlo reagovat nebo služba měla být Elasticka.

Existují i jiné způsoby, jak přistupovat k asynchronnímu kódu než `async` a `await` popsaný v článku výše, který je uvedený výše. Tento dokument se ale bude soustředit na konstrukty na úrovni jazyka od tohoto okamžiku předem.

### <a name="io-bound-example-downloading-data-from-a-web-service"></a>I/O-vázaný příklad: stahování dat z webové služby

Může být nutné stáhnout některá data z webové služby, když je stisknuto tlačítko, ale nechcete zablokovat vlákno uživatelského rozhraní. Můžete to provést jednoduše takto:

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

A je to hotovo. Kód vyjadřuje záměr (asynchronně stahovat data), aniž by bylo nutné zabřednete v interakci s objekty Task.

### <a name="cpu-bound-example-performing-a-calculation-for-a-game"></a>Příklad vázaný na procesor: provádění výpočtu hry

Řekněme, že píšete mobilní hru, kde stisknutí tlačítka může způsobit poškození mnoha Enemies na obrazovce.  Provádění výpočtu škod může být nákladné a jeho provedení na vlákně UI by vedlo k tomu, že se hra po provedení výpočtu zastaví.

Nejlepším způsobem, jak to zpracovat, je spustit vlákno na pozadí, které funguje pomocí `Task.Run`a `await` jeho výsledek.  Tím umožníte, aby uživatelské rozhraní bylo hladké, protože práce se provádí.

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

A je to!  Tento kód čistě vyjadřuje záměr události kliknutí na tlačítko, nevyžaduje ruční správu vlákna na pozadí a je tak neblokujícím způsobem.

### <a name="what-happens-under-the-covers"></a>Co se stane v rámci pokrývání

Existuje velký počet přesunů, ve kterých jsou jednotlivé asynchronní operace obavy.  Pokud jste zajímái o tom, co se děje, na základě pokrývání `Task` a `Task<T>`, další informace najdete [v](../standard/async-in-depth.md) podrobném článku.

Na C# straně sebe Kompilátor transformuje váš kód do stavového počítače, který uchovává informace o tom, jako je například vrácení spuštění, když je dosaženo `await` a pokračuje v provádění po dokončení úlohy na pozadí.

Pro teoreticky-skloněnou je to implementace [modelu asynchronii pro příslib](https://en.wikipedia.org/wiki/Futures_and_promises).

## <a name="key-pieces-to-understand"></a>Klíčové kousky, které je potřeba pochopit

* Asynchronní kód lze použít pro vstupně-výstupní operace i pro kód vázaný na procesor, ale pro každý scénář odlišně.
* Asynchronní kód používá `Task<T>` a `Task`, které jsou konstrukce používané k modelování práce prováděné na pozadí.
* Klíčové slovo `async` přepíná metodu do asynchronní metody, která umožňuje použití klíčového slova `await` v těle.
* Při použití klíčového slova `await` pozastaví volající metodu a vrátí řízení volajícímu, dokud není dokončen očekávaný úkol.
* `await` lze použít pouze v asynchronní metodě.

## <a name="recognize-cpu-bound-and-io-bound-work"></a>Rozpoznání práce vázané na procesor a vstupně-výstupní operace

První dva příklady této příručky ukázaly, jak můžete použít `async` a `await` pro vstupně-výstupní operace a práci vázanou na procesor.  Je klíč, který můžete identifikovat, když je potřeba udělat úlohu, která je vázaná na vstupně-výstupní operace, nebo na základě procesoru, protože může významně ovlivnit výkon kódu a může potenciálně vést k omylům s některými konstrukcemi.

Tady jsou dvě otázky, které byste měli před psaním kódu zeptat:

1. Bude váš kód "čekání" na něco, například data z databáze?

    Pokud je vaše odpověď "Ano", vaše práce je **vázána na vstup/výstup**.

2. Bude váš kód provádět velmi nákladný výpočet?

    Pokud jste odpověděli na Ano, vaše práce bude **vázaná na procesor**.

Pokud je práce, kterou jste **vázáni na vstup/výstup**, používejte `async` a `await` *bez* `Task.Run`.  *Neměli byste* používat Task Parallel Library.  Důvod tohoto důvodu je popsaný v [článku o Dehloubce Async](../standard/async-in-depth.md).

Pokud je práce **vázaná na procesor** a Vy zajímáte odezvu, použijte `async` a `await`, ale pracujte na jiném vlákně *s* `Task.Run`.  Pokud je práce vhodná pro souběžnost a paralelismu, měli byste také zvážit použití [Task Parallel Library](../standard/parallel-programming/task-parallel-library-tpl.md).

Kromě toho byste měli vždy změřit provádění kódu.  Například se můžete setkat v situaci, kdy práce vázaná na procesor není ve srovnání s režií kontextových přepínačů v případě multithreadingu dostatečně nákladná.  Každá volba má své kompromisy a měli byste si vybrat správné kompromisy pro vaši situaci.

## <a name="more-examples"></a>Další příklady

Následující příklady ukazují různé způsoby, jak můžete napsat asynchronní kód v C#.  Pokrývají několik různých scénářů, které se mohou nacházet v rámci.

### <a name="extracting-data-from-a-network"></a>Extrakce dat ze sítě

Tento fragment kódu stáhne kód HTML z domovské stránky na pozici [www.dotnetfoundation.org](https://www.dotnetfoundation.org) a spočítá počet výskytů řetězce ".NET" v HTML.  Pomocí ASP.NET MVC definuje metodu webového kontroléru, která provádí tuto úlohu, a vrátí číslo.

> [!NOTE]
> Pokud plánujete provádění analýzy HTML v produkčním kódu, nepoužívejte regulární výrazy. Místo toho použijte analýzu knihovny.

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

Tady je stejný scénář, který je napsán pro univerzální aplikaci pro Windows, která při stisknutí tlačítka provede stejnou úlohu:

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

### <a name="waiting-for-multiple-tasks-to-complete"></a>Čeká se na dokončení více úloh.

Můžete se setkat v situaci, kdy potřebujete současně načíst více dat.  Rozhraní `Task` API obsahuje dvě metody, `Task.WhenAll` a `Task.WhenAny`, které umožňují napsat asynchronní kód, který provádí neblokující čekání na více úloh na pozadí.

Tento příklad ukazuje, jak můžete `User` data pro sadu `userId`s.

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

Tady je další způsob, jak tento trochu napsat mnohem více, pomocí LINQ:

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

I když je to méně kódu, při kombinování LINQ s asynchronním kódem je potřeba dbát.  Vzhledem k tomu, že LINQ používá odložené (opožděné) provádění, asynchronní volání nebudou provedena ihned stejně jako v `foreach()` smyčce, pokud nevynutíte vygenerovanou sekvenci iterací voláním `.ToList()` nebo `.ToArray()`.

## <a name="important-info-and-advice"></a>Důležité informace a Rady

I když je asynchronní programování relativně jednoduché, je třeba mít na paměti několik detailů, které mohou zabránit neočekávanému chování.

* `async` **metody musí mít** **v těle klíčové slovo `await`, jinak nebudou nikdy vracet!**

To je důležité mít na paměti.  Pokud se `await` nepoužívá v těle metody `async`, C# kompilátor vygeneruje upozornění, ale kód se zkompiluje a spustí, jako kdyby šlo o běžnou metodu.  Všimněte si, že by to bylo také neuvěřitelně neefektivní, protože Stavový počítač generovaný C# kompilátorem pro asynchronní metodu nebude provádět žádné akce.

* **Jako příponu každého názvu asynchronní metody, kterou píšete, byste měli přidat "Async".**

Toto je konvence, která se používá v rozhraní .NET pro snadnější odlišení synchronních a asynchronních metod. Všimněte si, že některé metody, které nejsou explicitně volány vaším kódem (například obslužné rutiny událostí nebo metody webového kontroleru), nemusí nutně platit. Vzhledem k tomu, že nejsou explicitně volány vaším kódem, explicitní informace o jejich pojmenování nejsou důležité.

* `async void` **by měla být použita pouze pro obslužné rutiny událostí.**

`async void` je jediným způsobem, jak povolit fungování asynchronních obslužných rutin událostí, protože události nemají návratové typy (proto nemohou používat `Task` a `Task<T>`). Jakékoli jiné použití `async void` nedodržuje model klepnutí a může být náročné na použití, například:

* Výjimky vyvolané v metodě `async void` nejde zachytit mimo tuto metodu.
* metody `async void` jsou velmi obtížné testovat.
* `async void` metody mohou způsobit špatné vedlejší účinky, pokud volající neočekává, že budou Async.

* **Při použití asynchronních výrazů lambda ve výrazech LINQ pečlivě běhouny**

Výrazy lambda v jazyce LINQ používají odložené provádění, což znamená, že kód může být spuštěn v okamžiku, kdy ho neočekáváte. Zavedení blokujících úloh do této operace může snadno vést k zablokování, pokud není správně napsáno. Kromě toho vnořování asynchronního kódu, jako je, může také ztížit důvod spuštění kódu. Asynchronní a LINQ jsou výkonné, ale měly by být používány společně co nejdříve a jasně.

* **Napsat kód, který čeká na úlohy bez blokování**

Blokování aktuálního vlákna jako prostředku pro čekání na dokončení úlohy může způsobit zablokování a blokované kontextová vlákna a může vyžadovat podstatně složitější zpracování chyb. V následující tabulce najdete pokyny, jak se zabývat čekáním na úlohy neblokujícím způsobem:

| Postup... | Místo... | Kdy to chcete udělat |
| --- | --- | --- |
| `await` | `Task.Wait` Nebo `Task.Result` | Načítání výsledku úlohy na pozadí |
| `await Task.WhenAny` | `Task.WaitAny` | Čeká se na dokončení všech úloh. |
| `await Task.WhenAll` | `Task.WaitAll` | Čeká se na dokončení všech úloh. |
| `await Task.Delay` | `Thread.Sleep` | Čekání na časový úsek |

* **Zápis méně stavového kódu**

Nezávisí na stavu globálních objektů nebo provádění určitých metod. Místo toho závisí pouze na vrácených hodnotách metod. Proč?

* Kód bude z důvodu snazší.
* Testování kódu bude snazší.
* Kombinování asynchronního a synchronního kódu je mnohem jednodušší.
* Konflikty časování se obvykle můžou vyvarovat zcela.
* V závislosti na vrácených hodnotách je jednodušší koordinovat asynchronní kód.
* (Bonus) funguje ve skutečnosti i při vkládání závislostí.

Doporučeným cílem je dosáhnout úplné nebo téměř úplné [referenční transparentnosti](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) ve vašem kódu. Výsledkem je mimořádně předvídatelný, testovatelné a udržovatelný základ kódu.

## <a name="other-resources"></a>Další zdroje

* [Async-Depth](../standard/async-in-depth.md) poskytuje další informace o práci s úkoly.
* [Asynchronní programování s modifikátorem Async aC#operátoru Await ()](./programming-guide/concepts/async/index.md)
* [Šest důležitých tipů pro Lucian Wischik pro Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) je vynikajícím prostředkem pro asynchronní programování.
