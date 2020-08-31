---
title: Zrušení seznamu úkolů (C#)
description: Naučte se používat tokeny zrušení k signalizaci žádosti o zrušení seznamu úkolů.
ms.date: 08/19/2020
ms.topic: tutorial
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
ms.openlocfilehash: 30bef5d1a5082fbd3757377dbedb8f9b9d17e218
ms.sourcegitcommit: 2560a355c76b0a04cba0d34da870df9ad94ceca3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2020
ms.locfileid: "89053090"
---
# <a name="cancel-a-list-of-tasks-c"></a>Zrušení seznamu úkolů (C#)

Můžete zrušit asynchronní konzolovou aplikaci, pokud nechcete čekat na její dokončení. Podle následujícího příkladu v tomto tématu můžete přidat zrušení do aplikace, která stáhne obsah seznamu webů. Přiřazením <xref:System.Threading.CancellationTokenSource> instance ke každému úkolu můžete zrušit mnoho úloh. Pokud vyberete klávesu <kbd>ENTER</kbd> , zrušíte všechny úlohy, které ještě nebyly dokončeny.

Tento kurz zahrnuje:

> [!div class="checklist"]
>
> - Vytvoření konzolové aplikace .NET
> - Zápis asynchronní aplikace, která podporuje zrušení
> - Demonstrace zrušení signalizace

## <a name="prerequisites"></a>Požadavky

V tomto kurzu budete potřebovat následující:

- [.NET 5,0 nebo novější SDK](https://dotnet.microsoft.com/download/dotnet/5.0)
- Integrované vývojové prostředí (IDE)
  - [Doporučujeme Visual Studio, Visual Studio Code nebo Visual Studio pro Mac](https://visualstudio.microsoft.com)

### <a name="create-example-application"></a>Vytvořit ukázkovou aplikaci

Vytvořte novou konzolovou aplikaci .NET Core. Můžete ho vytvořit pomocí [`dotnet new console`](../../../../core/tools/dotnet-new.md#console) příkazu nebo ze sady [Visual Studio](/visualstudio/install/install-visual-studio). Otevřete soubor *program.cs* ve svém oblíbeném editoru kódu.

### <a name="replace-using-statements"></a>Nahradit příkazy using

Nahraďte existující příkazy using těmito deklaracemi:

```csharp
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Net.Http;
using System.Threading;
using System.Threading.Tasks;
```

## <a name="add-fields"></a>Přidat pole

Do `Program` definice třídy přidejte tato tři pole:

```csharp
static readonly CancellationTokenSource s_cts = new CancellationTokenSource();

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

<xref:System.Threading.CancellationTokenSource>Slouží k signalizaci požadovaného zrušení na <xref:System.Threading.CancellationToken> . `HttpClient`Zpřístupňuje možnost odesílat požadavky HTTP a přijímat odpovědi HTTP. `s_urlList`Obsahuje všechny adresy URL, které aplikace plánuje zpracovat.

## <a name="update-application-entry-point"></a>Aktualizovat vstupní bod aplikace

Hlavní vstupní bod do konzolové aplikace je `Main` metoda. Existující metodu nahraďte následujícím způsobem:

```csharp
static async Task Main()
{
    Console.WriteLine("Application started.");
    Console.WriteLine("Press the ENTER key to cancel...\n");

    Task cancelTask = Task.Run(() =>
    {
        while (Console.ReadKey().Key != ConsoleKey.Enter)
        {
            Console.WriteLine("Press the ENTER key to cancel...");
        }

        Console.WriteLine("\nENTER key pressed: cancelling downloads.\n");
        s_cts.Cancel();
    });

    Task sumPageSizesTask = SumPageSizesAsync();

    await Task.WhenAny(new[] { cancelTask, sumPageSizesTask });

    Console.WriteLine("Application ending.");
}
```

Aktualizovaná `Main` Metoda je nyní považována za [asynchronní hlavní](../../../whats-new/csharp-7-1.md#async-main), což umožňuje asynchronní vstupní bod do spustitelného souboru. Zapisuje do konzoly několik pokynů a pak deklaruje <xref:System.Threading.Tasks.Task> instanci nazvanou `cancelTask` , která načte tahy kláves konzoly. Při stisknutí klávesy <kbd>ENTER</kbd> se <xref:System.Threading.CancellationTokenSource.Cancel?displayProperty=nameWithType> provede volání. Tato akce zruší zrušení signálu. Dále `sumPageSizesTask` je proměnná přiřazena z `SumPageSizesAsync` metody. Oba úkoly jsou následně předány do <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])?displayProperty=nameWithType> , což bude pokračovat po dokončení kterékoli ze dvou úloh.

## <a name="create-the-asynchronous-sum-page-sizes-method"></a>Vytvořit metodu asynchronní velikosti stránek součtu

Pod `Main` metodu přidejte `SumPageSizesAsync` metodu:

```csharp
static async Task SumPageSizesAsync()
{
    var stopwatch = Stopwatch.StartNew();

    int total = 0;
    foreach (string url in s_urlList)
    {
        int contentLength = await ProcessUrlAsync(url, s_client, s_cts.Token);
        total += contentLength;
    }

    stopwatch.Stop();

    Console.WriteLine($"\nTotal bytes returned:  {total:#,#}");
    Console.WriteLine($"Elapsed time:          {stopwatch.Elapsed}\n");
}
```

Metoda začíná vytvořením instance a spuštěním <xref:System.Diagnostics.Stopwatch> . Pak projde každou adresu URL v `s_urlList` voláních a `ProcessUrlAsync` . Při každé iteraci se `s_cts.Token` předává do `ProcessUrlAsync` metody a kód vrátí <xref:System.Threading.Tasks.Task%601> , kde `TResult` je celé číslo:

```csharp
int total = 0;
foreach (string url in s_urlList)
{
    int contentLength = await ProcessUrlAsync(url, s_client, s_cts.Token);
    total += contentLength;
}
```

## <a name="add-process-method"></a>Přidat metodu procesu

Do metody přidejte následující `ProcessUrlAsync` metodu `SumPageSizesAsync` :

```csharp
static async Task<int> ProcessUrlAsync(string url, HttpClient client, CancellationToken token)
{
    HttpResponseMessage response = await client.GetAsync(url, token);
    byte[] content = await response.Content.ReadAsByteArrayAsync(token);
    Console.WriteLine($"{url,-60} {content.Length,10:#,#}");

    return content.Length;
}
```

Pro všechny zadané adresy URL metoda použije `client` poskytnutou instanci k získání odpovědi jako `byte[]` . <xref:System.Threading.CancellationToken>Instance je předána do <xref:System.Net.Http.HttpClient.GetAsync(System.String,System.Threading.CancellationToken)?displayProperty=nameWithType> metod a <xref:System.Net.Http.HttpContent.ReadAsByteArrayAsync(System.Threading.CancellationToken)?displayProperty=nameWithType> . `token`Slouží k registraci k požadovanému zrušení. Délka se vrátí po zápisu adresy URL a délky do konzoly.

### <a name="example-application-output"></a>Příklad výstupu aplikace

```console
Application started.
Press the ENTER key to cancel...

https://docs.microsoft.com                                       37,357
https://docs.microsoft.com/aspnet/core                           85,589
https://docs.microsoft.com/azure                                398,939
https://docs.microsoft.com/azure/devops                          73,663
https://docs.microsoft.com/dotnet                                67,452
https://docs.microsoft.com/dynamics365                           48,582
https://docs.microsoft.com/education                             22,924

ENTER key pressed: cancelling downloads.

Application ending.
```

## <a name="complete-example"></a>Kompletní příklad

Následující kód je úplný text souboru *program.cs* pro příklad.

:::code language="csharp" source="snippets/cancel-tasks/cancel-tasks/Program.cs":::

## <a name="see-also"></a>Viz také

- <xref:System.Threading.CancellationToken>
- <xref:System.Threading.CancellationTokenSource>
- [Asynchronní programování s modifikátorem Async a operátoru Await (C#)](index.md)

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Zrušení asynchronních úloh po určitém časovém intervalu (C#)](cancel-async-tasks-after-a-period-of-time.md)
