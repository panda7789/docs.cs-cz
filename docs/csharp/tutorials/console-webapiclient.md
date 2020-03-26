---
title: Vytvoření klienta REST pomocí rozhraní .NET Core
description: Tento kurz vás naučí řadu funkcí v .NET Core a jazyk C#.
ms.date: 01/09/2020
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 0105db519f7accec6bf8bfbafdc6a67a444b1074
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249165"
---
# <a name="rest-client"></a>Klient REST

Tento kurz vás naučí řadu funkcí v .NET Core a jazyk C#. Dozvíte se:

* Základy rozhraní příkazového příkazu jádra .NET.
* Přehled funkcí jazyka C#.
* Správa závislostí pomocí NuGet
* HTTP komunikace
* Zpracování informací JSON
* Správa konfigurace pomocí atributů.

Vytvoříte aplikaci, která vydává požadavky HTTP do služby REST na GitHubu. Budete číst informace ve formátu JSON a převést, že paket JSON do C# objekty. Nakonec uvidíte, jak pracovat s objekty Jazyka C#.

V tomto kurzu je mnoho funkcí. Postavíme je jeden po druhém.

Pokud dáváte přednost sledování spolu s [konečnou ukázkou](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) pro toto téma, můžete si ji stáhnout. Pokyny ke stažení naleznete v [tématu Ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Požadavky

Budete muset nastavit počítač pro spuštění jádra .NET. Pokyny k instalaci naleznete na stránce [Ke stažení jádra .NET.](https://dotnet.microsoft.com/download) Tuto aplikaci můžete spustit ve Windows, Linuxu, macOS nebo v kontejneru Dockeru.
Budete muset nainstalovat svůj oblíbený editor kódu. Níže uvedené popisy používají [Visual Studio Code](https://code.visualstudio.com/), což je open source editor napříč platformami. Nicméně, můžete použít bez ohledu na nástroje, které jsou pohodlné s.

## <a name="create-the-application"></a>Vytvoření aplikace

Prvním krokem je vytvoření nové aplikace. Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci. Ať je to aktuální adresář. V okně konzoly zadejte následující příkaz:

```dotnetcli
dotnet new console --name WebApiClient
```

Tím se vytvoří počáteční soubory pro základní aplikaci "Hello World". Název projektu je "WebApiClient". Vzhledem k tomu, že se jedná o nový projekt, žádná ze závislostí není na místě. První spuštění stáhne rozhraní .NET Core framework, nainstaluje vývojový certifikát a spustí správce balíčků NuGet a obnoví chybějící závislosti.

Než začnete provádět změny, zadejte `dotnet run` na příkazovém řádku příkaz[(viz poznámka)](#dotnet-restore-note)a spusťte aplikaci. `dotnet run`automaticky `dotnet restore` provádí, pokud ve vašem prostředí chybí závislosti. Také provádí, `dotnet build` pokud je potřeba znovu sestavit aplikaci.
Po počátečním nastavení budete muset `dotnet restore` spustit `dotnet build` nebo pouze tehdy, když to dává smysl pro váš projekt.

## <a name="adding-new-dependencies"></a>Přidání nových závislostí

Jedním z klíčových cílů návrhu pro .NET Core je minimalizovat velikost instalace .NET. Pokud aplikace potřebuje další knihovny pro některé z jeho funkcí, přidáte\*tyto závislosti do souboru projektu C# ( .csproj). Pro náš příklad budete muset přidat `System.Runtime.Serialization.Json` balíček, takže vaše aplikace může zpracovávat odpovědi JSON.

Budete potřebovat balíček `System.Runtime.Serialization.Json` pro tuto aplikaci. Přidejte jej do projektu spuštěním následujícího příkazu [rozhraní PŘÍKAZU .NET:](../../core/tools/dotnet-add-package.md)

```dotnetcli
dotnet add package System.Text.Json
```

## <a name="making-web-requests"></a>Vytváření webových požadavků

Nyní můžete začít načítat data z webu. V této aplikaci budete číst informace z [GitHub API](https://developer.github.com/v3/). Přečtěme si informace o projektech pod zastřešujícím programem [.NET Foundation.](https://www.dotnetfoundation.org/) Začnete tím, že žádost github api načíst informace o projektech. Koncový bod, který budete <https://api.github.com/orgs/dotnet/repos>používat, je: . Chcete načíst všechny informace o těchto projektech, takže budete používat požadavek HTTP GET.
Váš prohlížeč také používá požadavky HTTP GET, takže můžete tuto adresu URL vložit do prohlížeče a zjistit, jaké informace budete dostávat a zpracovávat.

Třídu <xref:System.Net.Http.HttpClient> používáte k výrobě webových požadavků. Stejně jako všechna moderní <xref:System.Net.Http.HttpClient> rozhraní API .NET podporuje pouze asynchronní metody pro dlouhotrvající rozhraní API.
Začněte tím, že asynchronní metodu. Budete vyplnit implementaci při vytváření funkce aplikace. Začněte otevřením souboru `program.cs` v adresáři projektu `Program` a přidáním následující metody do třídy:

```csharp
private static async Task ProcessRepositories()
{
}
```

Budete muset přidat direktivu `using` v `Main` horní části metody tak, aby <xref:System.Threading.Tasks.Task> kompilátor Jazyka C# rozpozná typ:

```csharp
using System.Threading.Tasks;
```

Pokud vytvoříte projekt v tomto okamžiku, zobrazí se upozornění generované pro tuto metodu, protože neobsahuje žádné `await` operátory a bude spuštěnsynchronně. Prozatím to ignorujte; při vyplňování `await` metody přidáte operátory.

Dále přejmenujte obor názvů `namespace` definovaný v příkazu z jeho výchozí ho `ConsoleApp` `WebAPIClient`na . Později definujeme `repo` třídu v tomto oboru názvů.

Dále aktualizujte `Main` metodu pro volání této metody. Metoda `ProcessRepositories` vrátí úkol a neměli byste ukončit program před dokončením této úlohy. Proto je nutné změnit `Main`podpis . Přidejte `async` modifikátor a změňte návratový typ na `Task`. Potom v těle metody přidejte volání `ProcessRepositories`. Přidejte `await` klíčové slovo do volání této metody:

```csharp
static async Task Main(string[] args)
{
    await ProcessRepositories();
}
```

Nyní máte program, který nedělá nic, ale dělá to asynchronně. Pojďme to zlepšit.

Nejprve potřebujete objekt, který je schopen načíst data z webu; můžete použít <xref:System.Net.Http.HttpClient> k tomu, že. Tento objekt zpracovává požadavek a odpovědi. Vytvořte instanci tohoto typu ve `Program` třídě uvnitř *Program.cs* souboru.

```csharp
namespace WebAPIClient
{
    class Program
    {
        private static readonly HttpClient client = new HttpClient();

        static async Task Main(string[] args)
        {
            //...
        }
    }
}
```

Vraťme se k `ProcessRepositories` metodě a vyplňte její první verzi:

```csharp
private static async Task ProcessRepositories()
{
    client.DefaultRequestHeaders.Accept.Clear();
    client.DefaultRequestHeaders.Accept.Add(
        new MediaTypeWithQualityHeaderValue("application/vnd.github.v3+json"));
    client.DefaultRequestHeaders.Add("User-Agent", ".NET Foundation Repository Reporter");

    var stringTask = client.GetStringAsync("https://api.github.com/orgs/dotnet/repos");

    var msg = await stringTask;
    Console.Write(msg);
}
```

Budete také muset přidat dvě `using` nové direktivy v horní části souboru pro tento kompilovat:

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

Tato první verze vytvoří webový požadavek na čtení seznamu všech úložišť v rámci organizace dotnet foundation. (GitHub ID pro .NET Foundation je 'dotnet'). Prvních několik řádků nastavit <xref:System.Net.Http.HttpClient> pro tento požadavek. Nejprve je nakonfigurován tak, aby přijímal odpovědi GitHub JSON.
Tento formát je jednoduše JSON. Další řádek přidá hlavičku uživatelského agenta ke všem požadavkům z tohoto objektu. Tyto dvě hlavičky jsou kontrolovány kódem serveru GitHub a jsou nezbytné k načtení informací z GitHubu.

Po konfiguraci <xref:System.Net.Http.HttpClient>aplikace provedete webový požadavek a načtete odpověď. V této první verzi <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> použijete metodu pohodlí. Tato metoda pohodlí spustí úlohu, která vytvoří webový požadavek a potom, když se požadavek vrátí, přečte datový proud odpovědi a extrahuje obsah z datového proudu. Tělo odpovědi je vrácena <xref:System.String>jako . Řetězec je k dispozici po dokončení úlohy.

Poslední dva řádky této metody čekají na tuto úlohu a vytisknout odpověď na konzolu.
Vytvořte aplikaci a spusťte ji. Upozornění sestavení je nyní pryč, protože `ProcessRepositories` `await` nyní obsahuje operátor. Zobrazí se dlouhé zobrazení textu ve formátu JSON.

## <a name="processing-the-json-result"></a>Zpracování výsledku JSON

V tomto okamžiku jste napsali kód pro načtení odpovědi z webového serveru a zobrazení textu, který je obsažen v této odpovědi. Dále převeďte odpověď JSON na objekty Jazyka C#.

Třída <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> serializuje objekty do JSON a reserializuje JSON do objektů. Začněte definováním třídy `repo` představující objekt JSON vrácený z rozhraní API GitHub:

```csharp
using System;

namespace WebAPIClient
{
    public class Repository
    {
        public string name { get; set; }
    }
}
```

Vložte výše uvedený kód do nového souboru s názvem 'repo.cs'. Tato verze třídy představuje nejjednodušší cestu ke zpracování dat JSON. Název třídy a název člena odpovídají názvům použitým v paketu JSON namísto následujících konvencí jazyka C#. Opravíte to tím, že později poskytnete některé atributy konfigurace. Tato třída ukazuje další důležitou funkci serializace json a deserializace: Ne všechna pole v paketu JSON jsou součástí této třídy.
Serializátor JSON bude ignorovat informace, které nejsou zahrnuty v typu třídy, který se používá.
Tato funkce usnadňuje vytváření typů, které pracují pouze s podmnožinou polí v paketu JSON.

Teď, když jste vytvořili typ, pojďme ho rekonstruovat.

Dále použijete serializátor k převodu JSON na objekty Jazyka C#. Nahraďte <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> volání `ProcessRepositories` v metodě následujícími řádky:

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
```

Používáte nový obor názvů, takže ho budete muset přidat také v horní části souboru:

```csharp
using System.Text.Json;
```

Všimněte si, že <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> nyní <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>používáte místo . Serializátor používá datový proud namísto řetězce jako jeho zdroj. Vysvětlíme několik funkcí jazyka C#, které se používají ve druhém řádku předchozího fragmentu kódu. Prvním argumentem <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> je `await` výraz. (Další dva parametry jsou volitelné a jsou vynechány ve fragmentu kódu.) Await výrazy se mohou zobrazit téměř kdekoli ve vašem kódu, i když až do teď, jste je viděli pouze jako součást příkazu přiřazení. Metoda `Deserialize` je *obecná*, což znamená, že je nutné zadat argumenty typu pro jaký druh objektů by měl být vytvořen z textu JSON. V tomto příkladu reserializujete `List<Repository>`na , což je <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>jiný obecný objekt, . Třída `List<>` ukládá kolekci objektů. Argument typu deklaruje typ `List<>`objektů uložených v . Text JSON představuje kolekci objektů repo, takže `Repository`argument typu je .

S touhle sekcí jsi skoro skončil. Teď, když jste převedli JSON na objekty Jazyka C#, zobrazme název každého úložiště. Nahraďte řádky s přečtenými řádky:

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

s následujícími:

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

Zkompilujte a spusťte aplikaci. Vytiskne názvy úložišť, které jsou součástí .NET Foundation.

## <a name="controlling-serialization"></a>Řízení serializace

Než přidáte další funkce, pojďme `name` adresu vlastnost `[JsonPropertyName]` pomocí atributu. Proveďte následující změny v `name` deklaraci pole v repo.cs:

```csharp
[JsonPropertyName("name")]
public string Name { get; set; }
```

Chcete-li použít `[JsonPropertyName]` atribut, budete <xref:System.Text.Json.Serialization> muset přidat `using` obor názvů do směrnic:

```csharp
using System.Text.Json.Serialization;
```

Tato změna znamená, že je třeba změnit kód, který zapisuje název každého úložiště v program.cs:

```csharp
Console.WriteLine(repo.Name);
```

Proveďte, `dotnet run` abyste se ujistili, že máte správné mapování. Měli byste vidět stejný výstup jako předtím.

Před přidáním nových funkcí proveďte ještě jednu změnu. Metoda `ProcessRepositories` může provést asynchronní práci a vrátit kolekci úložišť. Vraťme z `List<Repository>` této metody a přesuňte kód, který `Main` zapisuje informace do metody.

Změňte podpis `ProcessRepositories` funkce a vraťte úkol, `Repository` jehož výsledkem je seznam objektů:

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

Potom vraťte úložiště po zpracování odpovědi JSON:

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
return repositories;
```

Kompilátor generuje `Task<T>` objekt pro návrat, protože jste tuto `async`metodu označili jako .
Potom pojďme upravit `Main` metodu tak, aby zachytí tyto výsledky a zapíše každý název úložiště do konzoly. Vaše `Main` metoda nyní vypadá takto:

```csharp
public static async Task Main(string[] args)
{
    var repositories = await ProcessRepositories();

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

## <a name="reading-more-information"></a>Čtení více informací

Dokončení tohoto zpracování zpracováním několik dalších vlastností v paketu JSON, který se odesílá z rozhraní API GitHub. Nebudete chtít uchopit všechno, ale přidání několika vlastností bude demonstrovat několik dalších funkcí jazyka C#.

Začněme přidáním několika dalších jednoduchých typů do definice třídy. `Repository` Přidejte tyto vlastnosti do této třídy:

```csharp
[JsonPropertyName("description")]
public string Description { get; set; }

[JsonPropertyName("html_url")]
public Uri GitHubHomeUrl { get; set; }

[JsonPropertyName("homepage")]
public Uri Homepage { get; set; }

[JsonPropertyName("watchers")]
public int Watchers { get; set; }
```

Tyto vlastnosti mají předdefinované převody z typu řetězce (což je co obsahují pakety JSON) na cílový typ. Typ <xref:System.Uri> může být pro vás nový. Představuje identifikátor URI nebo v tomto případě adresu URL. V případě `Uri` a `int` typy, pokud paket JSON obsahuje data, která nepřevádí na cílový typ, akce serializace vyvolá výjimku.

Po přidání těchto aktualizací aktualizujte metodu `Main` tak, aby se tyto prvky zobrazily:

```csharp
foreach (var repo in repositories)
{
    Console.WriteLine(repo.Name);
    Console.WriteLine(repo.Description);
    Console.WriteLine(repo.GitHubHomeUrl);
    Console.WriteLine(repo.Homepage);
    Console.WriteLine(repo.Watchers);
    Console.WriteLine();
}
```

Jako poslední krok přidáme informace pro poslední operaci push. Tyto informace jsou formátovány tímto způsobem v odpovědi JSON:

```json
2016-02-08T21:27:00Z
```

Tento formát je v koordinovaném čase (UTC), <xref:System.DateTime> takže <xref:System.DateTime.Kind%2A> získáte <xref:System.DateTimeKind.Utc>hodnotu, jejíž vlastnost je . Pokud dáváte přednost datu reprezentovanému ve vašem časovém pásmu, budete muset napsat vlastní metodu převodu. Nejprve `public` definujte vlastnost, která bude obsahovat reprezentaci `Repository` UTC `LastPush` `readonly` data a času ve vaší třídě a vlastnost, která vrací datum převedené na místní čas:

```csharp
[JsonPropertyName("pushed_at")]
public DateTime LastPushUtc { get; set; }

public DateTime LastPush => LastPushUtc.ToLocalTime();
```

Projděme si nové konstrukce, které jsme právě definovali. Vlastnost `LastPush` je definována pomocí člena s `get` *výrazem pro* přistupujícího objektu. Neexistuje žádný `set` přistupující odkaz. Vynechání přistupujícího objektu `set` je způsob, jakým definujete vlastnost jen pro *čtení* v c#. (Ano, můžete vytvořit vlastnosti *pouze pro zápis* v c#, ale jejich hodnota je omezená.)

Nakonec přidejte ještě jeden výstupní příkaz do konzoly a jste připraveni vytvořit a spustit tuto aplikaci znovu:

```csharp
Console.WriteLine(repo.LastPush);
```

Vaše verze by nyní měla odpovídat [dokončené ukázce](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).

## <a name="conclusion"></a>Závěr

Tento kurz vám ukázal, jak vytvořit webové požadavky, analyzovat výsledek a zobrazit vlastnosti těchto výsledků. Také jste přidali nové balíčky jako závislosti v projektu. Viděli jste některé funkce jazyka C#, které podporují objektově orientované techniky.

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
