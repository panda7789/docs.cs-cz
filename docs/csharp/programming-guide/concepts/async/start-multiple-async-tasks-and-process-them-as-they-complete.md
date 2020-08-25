---
title: Zpracování asynchronních úloh po dokončení
description: Tento příklad ukazuje, jak použít Task. WhenAny v jazyce C# ke spuštění více úkolů a zpracování jejich výsledků při jejich dokončení, místo jejich zpracování v pořadí.
ms.date: 08/19/2020
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
ms.openlocfilehash: c2fe66e865a2c88f4cae50b816f9326614fcbb89
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812026"
---
# <a name="process-asynchronous-tasks-as-they-complete-c"></a>Zpracování asynchronních úloh po dokončení (C#)

Pomocí nástroje <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> můžete spustit více úloh současně a zpracovat je jeden po jednom, protože jsou dokončeny, a nikoli jejich zpracování v pořadí, ve kterém jsou spuštěny.

Následující příklad používá dotaz k vytvoření kolekce úkolů. Každý úkol stáhne obsah zadaného webu. V každé iteraci smyčky while očekává volání metody <xref:System.Threading.Tasks.Task.WhenAny%2A> vrácení úlohy v kolekci úkolů, které dokončí stahování jako první. Tato úloha je odebrána z kolekce a zpracována. Smyčka se opakuje, dokud kolekce neobsahuje žádné další úlohy.

## <a name="create-example-application"></a>Vytvořit ukázkovou aplikaci

Vytvořte novou konzolovou aplikaci .NET Core. Můžete ho vytvořit pomocí příkazu [dotnet New Console](../../../../core/tools/dotnet-new.md#console) nebo ze sady [Visual Studio](/visualstudio/install/install-visual-studio). Otevřete soubor *program.cs* ve svém oblíbeném editoru kódu.

### <a name="replace-using-statements"></a>Nahradit příkazy using

Nahraďte existující příkazy using těmito deklaracemi:

```csharp
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Linq;
using System.Net.Http;
using System.Threading.Tasks;
```

## <a name="add-fields"></a>Přidat pole

V `Program` definici třídy přidejte následující dvě pole:

```csharp
static readonly HttpClient s_client = new HttpClient
{
    MaxResponseContentBufferSize = 1_000_000
};

static readonly IEnumerable<string> s_urlList = new string[]
{
    "https://docs.microsoft.com",
    "https://docs.microsoft.com/aspnet/core",
    "https://docs.microsoft.com/azure",
    "https://docs.microsoft.com/azure/devops",
    "https://docs.microsoft.com/dotnet",
    "https://docs.microsoft.com/dynamics365",
    "https://docs.microsoft.com/education",
    "https://docs.microsoft.com/enterprise-mobility-security",
    "https://docs.microsoft.com/gaming",
    "https://docs.microsoft.com/graph",
    "https://docs.microsoft.com/microsoft-365",
    "https://docs.microsoft.com/office",
    "https://docs.microsoft.com/powershell",
    "https://docs.microsoft.com/sql",
    "https://docs.microsoft.com/surface",
    "https://docs.microsoft.com/system-center",
    "https://docs.microsoft.com/visualstudio",
    "https://docs.microsoft.com/windows",
    "https://docs.microsoft.com/xamarin"
};
```

`HttpClient`Zpřístupňuje možnost odesílat požadavky HTTP a přijímat odpovědi HTTP. `s_urlList`Obsahuje všechny adresy URL, které aplikace plánuje zpracovat.

## <a name="update-application-entry-point"></a>Aktualizovat vstupní bod aplikace

Hlavní vstupní bod do konzolové aplikace je `Main` metoda. Existující metodu nahraďte následujícím způsobem:

```csharp
static Task Main() => SumPageSizesAsync();
```

Aktualizovaná `Main` Metoda je nyní považována za [asynchronní hlavní](../../../whats-new/csharp-7-1.md#async-main), což umožňuje asynchronní vstupní bod do spustitelného souboru. Vyjadřuje volání `SumPageSizesAsync` .

## <a name="create-the-asynchronous-sum-page-sizes-method"></a>Vytvořit metodu asynchronní velikosti stránek součtu

Pod `Main` metodu přidejte `SumPageSizesAsync` metodu:

```csharp
static async Task SumPageSizesAsync()
{
    var stopwatch = Stopwatch.StartNew();

    IEnumerable<Task<int>> downloadTasksQuery =
        from url in s_urlList
        select ProcessUrlAsync(url, s_client);

    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();

    int total = 0;
    while (downloadTasks.Any())
    {
        Task<int> finishedTask = await Task.WhenAny(downloadTasks);
        downloadTasks.Remove(finishedTask);
        total += await finishedTask;
    }

    stopwatch.Stop();

    Console.WriteLine($"\nTotal bytes returned:  {total:#,#}");
    Console.WriteLine($"Elapsed time:          {stopwatch.Elapsed}\n");
}
```

Metoda začíná vytvořením instance a spuštěním <xref:System.Diagnostics.Stopwatch> . Pak obsahuje dotaz, který při spuštění vytvoří kolekci úkolů. Každé volání do `ProcessUrlAsync` v následujícím kódu vrátí <xref:System.Threading.Tasks.Task%601> , kde `TResult` je celé číslo:

```csharp
IEnumerable<Task<int>> downloadTasksQuery =
    from url in s_urlList
    select ProcessUrlAsync(url, s_client);
```

Z důvodu [odloženého spuštění](../linq/deferred-execution-example.md) s LINQ se zavoláte <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> na spuštění jednotlivých úloh.

```csharp
List<Task<int>> downloadTasks = downloadTasksQuery.ToList();
```

`while`Smyčka provádí následující kroky pro každý úkol v kolekci:

1. Očekává volání `WhenAny` k identifikaci prvního úkolu v kolekci, která dokončila stažení.

    ```csharp
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);
    ```

1. Odebere úlohu z kolekce.

    ```csharp
    downloadTasks.Remove(firstFinishedTask);
    ```

1. Čeká `finishedTask` , který je vrácen voláním metody `ProcessUrlAsync` . `finishedTask`Proměnná je <xref:System.Threading.Tasks.Task%601> , kde `TResult` je celé číslo. Úkol je již dokončen, ale očekáváte, že bude načtena délka staženého webu, jak ukazuje následující příklad. Pokud dojde k chybě úlohy, `await` vyvolá první podřízenou výjimku uloženou v objektu `AggregateException` , na rozdíl od čtení <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> vlastnosti, která by vyvolala `AggregateException` .

    ```csharp
    total += await finishedTask;
    ```

## <a name="add-process-method"></a>Přidat metodu procesu

Do metody přidejte následující `ProcessUrlAsync` metodu `SumPageSizesAsync` :

```csharp
static async Task<int> ProcessUrlAsync(string url, HttpClient client)
{
    byte[] content = await client.GetByteArrayAsync(url);
    Console.WriteLine($"{url,-60} {content.Length,10:#,#}");

    return content.Length;
}
```

Pro všechny zadané adresy URL metoda použije `client` poskytnutou instanci k získání odpovědi jako `byte[]` . Délka se vrátí po zápisu adresy URL a délky do konzoly.

Spusťte program několikrát, abyste ověřili, že stažené délky se vždy nezobrazí ve stejném pořadí.

> [!CAUTION]
> Můžete použít `WhenAny` ve smyčce, jak je popsáno v příkladu, pro řešení problémů, které zahrnují malý počet úkolů. Další přístupy jsou ale efektivnější, pokud máte velký počet úkolů, které je potřeba zpracovat. Další informace a příklady najdete v tématu [zpracování úloh po dokončení](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete).

## <a name="complete-example"></a>Kompletní příklad

Následující kód je úplný text souboru *program.cs* pro příklad.

:::code language="csharp" source="snippets/multiple-tasks/Program.cs":::

## <a name="see-also"></a>Viz také

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [Asynchronní programování s modifikátorem Async a operátoru Await (C#)](index.md)
