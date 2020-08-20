---
title: Vytvoření klienta REST pomocí .NET Core
description: V tomto kurzu se naučíte řadou funkcí v .NET Core a v jazyce C#.
ms.date: 01/09/2020
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 8db87440bb6e0995b1cc2c97b0d28995170ada8c
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656941"
---
# <a name="rest-client"></a>Klient REST

V tomto kurzu se naučíte řadou funkcí v .NET Core a v jazyce C#. Naučíte se:

* Základy .NET Core CLI.
* Přehled funkcí jazyka C#.
* Správa závislostí pomocí NuGet
* Komunikace HTTP
* Zpracování informací JSON
* Správa konfigurace s atributy.

Vytvoříte aplikaci, která vydává požadavky HTTP na službu REST na GitHubu. Přečtete si informace ve formátu JSON a převeďte tento paket JSON na objekty C#. Nakonec uvidíte, jak pracovat s objekty C#.

V tomto kurzu máte spoustu funkcí. Pojďme je sestavit jednou po jednom.

Pokud chcete postupovat spolu s [závěrečnou ukázkou](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) tohoto tématu, můžete si ho stáhnout. Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#view-and-download-samples).

## <a name="prerequisites"></a>Předpoklady

Budete muset nastavit počítač tak, aby běžel .NET Core. Pokyny k instalaci najdete na stránce [soubory ke stažení pro .NET Core](https://dotnet.microsoft.com/download) . Tuto aplikaci můžete spustit na Windows, Linux, macOS nebo v kontejneru Docker.
Budete muset nainstalovat svůj oblíbený editor kódu. Níže uvedené popisy používají [Visual Studio Code](https://code.visualstudio.com/), což je Open Source Editor pro různé platformy. Můžete ale použít jakékoli nástroje, se kterými máte v pohodlí.

## <a name="create-the-application"></a>Vytvoření aplikace

Prvním krokem je vytvoření nové aplikace. Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci. Zajistěte, aby byl aktuální adresář. V okně konzoly zadejte následující příkaz:

```dotnetcli
dotnet new console --name WebAPIClient
```

Tím se vytvoří počáteční soubory pro základní aplikaci "Hello World". Název projektu je "WebAPIClient". Vzhledem k tomu, že se jedná o nový projekt, není provedena žádná závislost. První spuštění stáhne rozhraní .NET Core Framework, nainstaluje certifikát pro vývoj a spustí Správce balíčků NuGet pro obnovení chybějících závislostí.

Než začnete provádět úpravy, zadejte `dotnet run` ([Viz poznámku](#dotnet-restore-note)) na příkazovém řádku a spusťte tak aplikaci. `dotnet run` provede automaticky `dotnet restore` v případě chybějících závislostí ve vašem prostředí. Provádí se také `dotnet build` v případě, že vaše aplikace musí být znovu sestavena.
Po počáteční instalaci budete muset spustit pouze `dotnet restore` nebo, `dotnet build` když to pro váš projekt dává smysl.

## <a name="adding-new-dependencies"></a>Přidávání nových závislostí

Jedním z klíčových cílů pro .NET Core je minimalizace velikosti instalace rozhraní .NET. Pokud aplikace potřebuje další knihovny pro některé z jejích funkcí, přidejte tyto závislosti do souboru projektu C# ( \* . csproj). V našem příkladu budete muset `System.Runtime.Serialization.Json` balíček přidat, aby mohla aplikace zpracovat odpovědi JSON.

`System.Runtime.Serialization.Json`Pro tuto aplikaci budete potřebovat balíček. Přidejte ho do projektu spuštěním následujícího příkazu [rozhraní .NET CLI](../../core/tools/dotnet-add-package.md) :

```dotnetcli
dotnet add package System.Text.Json
```

## <a name="making-web-requests"></a>Vytváření webových požadavků

Teď jste připraveni začít načítat data z webu. V této aplikaci si přečtete informace z [rozhraní API GitHubu](https://developer.github.com/v3/). Pojďme si přečíst informace o projektech v rámci [.NET Foundation](https://www.dotnetfoundation.org/) zastřešující. Začnete tím, že si vyžádáte rozhraní API GitHubu, abyste načetli informace o projektech. Koncový bod, který budete používat, je: <https://api.github.com/orgs/dotnet/repos> . Chcete načíst všechny informace o těchto projektech, abyste použili požadavek HTTP GET.
Váš prohlížeč používá také požadavky HTTP GET, takže můžete vložit tuto adresu URL do prohlížeče, abyste viděli informace, které budete dostávat a zpracovávat.

Třídu můžete použít <xref:System.Net.Http.HttpClient> k vytváření webových požadavků. Stejně jako všechna moderní rozhraní API .NET <xref:System.Net.Http.HttpClient> podporuje pouze asynchronní metody pro svá dlouhotrvající rozhraní API.
Začněte vytvořením asynchronní metody. Při sestavování funkčnosti aplikace naplníte implementaci. Začněte otevřením `program.cs` souboru v adresáři projektu a přidáním následující metody do `Program` třídy:

```csharp
private static async Task ProcessRepositories()
{
}
```

V horní části metody bude nutné přidat `using` direktivu `Main` , aby kompilátor jazyka C# rozpoznal <xref:System.Threading.Tasks.Task> Typ:

```csharp
using System.Threading.Tasks;
```

Pokud v tomto okamžiku sestavíte projekt, zobrazí se pro tuto metodu upozornění vygenerované, protože neobsahuje žádné `await` operátory a spustí se synchronně. Tuto chvíli ignorujte. operátory přidáte při `await` vyplňování metody.

Dále aktualizujte `Main` metodu pro volání `ProcessRepositories` metody. `ProcessRepositories`Metoda vrátí úlohu a neukončí program před dokončením této úlohy. Proto je nutné změnit signaturu `Main` . Přidejte `async` modifikátor a změňte návratový typ na `Task` . Pak v těle metody přidejte volání do `ProcessRepositories` . Přidejte `await` klíčové slovo do tohoto volání metody:

```csharp
static async Task Main(string[] args)
{
    await ProcessRepositories();
}
```

Nyní máte program, který nic nedělá, ale asynchronně ho provede. Pojďme to vylepšit.

Nejprve potřebujete objekt, který je schopný načíst data z webu. k tomu můžete použít <xref:System.Net.Http.HttpClient> . Tento objekt zpracovává požadavek a odpovědi. Vytvořte instanci jedné instance daného typu ve `Program` třídě uvnitř souboru *program.cs* .

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

Pojďme se zpátky k `ProcessRepositories` metodě a vyplnit první verzi IT:

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

V horní části souboru budete muset přidat také dvě nové `using` direktivy, aby se mohla kompilovat:

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

Tato první verze vytvoří webový požadavek na načtení seznamu všech úložišť v rámci organizace dotnet Foundation. (ID gitHubu pro .NET Foundation je "dotnet"). Prvních pár řádků, které jsou <xref:System.Net.Http.HttpClient> pro tento požadavek nastaveny. Nejdřív je nakonfigurovaný tak, aby přijímal odpovědi na adresu JSON pro GitHub.
Tento formát je jednoduše JSON. Další řádek přidá hlavičku uživatelského agenta do všech požadavků od tohoto objektu. Tato dvě záhlaví jsou kontrolována kódem serveru GitHub a jsou nutná k načtení informací z GitHubu.

Po dokončení konfigurace aplikace vytvoříte <xref:System.Net.Http.HttpClient> webový požadavek a načtete odpověď. V této první verzi použijete <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> metodu usnadnění. Tato pohodlná metoda spustí úlohu, která provede webový požadavek, a poté, co požadavek vrátí, načte datový proud odpovědi a extrahuje obsah z datového proudu. Tělo odpovědi je vráceno jako <xref:System.String> . Řetězec je k dispozici po dokončení úkolu.

Poslední dva řádky této metody čekají na daný úkol a pak vytiskněte odpověď do konzoly.
Sestavte aplikaci a spusťte ji. Upozornění na sestavení je nyní pryč, protože `ProcessRepositories` nyní obsahuje `await` operátor. Zobrazí se dlouhé zobrazení textu ve formátu JSON.

## <a name="processing-the-json-result"></a>Zpracování výsledku JSON

V tuto chvíli jste napsali kód, který načte odpověď z webového serveru, a zobrazí text obsažený v této odpovědi. Nyní převedeme tuto odpověď JSON na objekty jazyka C#.

<xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType>Třída serializace objektů do formátu JSON a deserializace JSON do objektů. Začněte tím, že definujete třídu, která představuje `repo` objekt JSON vrácený z rozhraní API GitHubu:

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

Výše uvedený kód vložte do nového souboru s názvem "úložiště. cs". Tato verze třídy představuje nejjednodušší cestu pro zpracování dat JSON. Název třídy a název členu odpovídají názvům použitým v paketu JSON namísto následujících konvencí jazyka C#. Opravte to tak, že později poskytnete nějaké konfigurační atributy. Tato třída ukazuje další důležitou funkci serializace a deserializace JSON: Ne všechna pole v paketu JSON jsou součástí této třídy.
Serializátor JSON bude ignorovat informace, které nejsou zahrnuté do používaného typu třídy.
Tato funkce usnadňuje vytváření typů, které pracují pouze s podmnožinou polí v paketu JSON.

Teď, když jste vytvořili typ, Pojďme ho deserializovat.

V dalším kroku použijete serializátor k převedení formátu JSON na objekty jazyka C#. Nahraďte volání <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> v `ProcessRepositories` metodě následujícími řádky:

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
```

Používáte nové obory názvů, takže ho budete muset přidat i na začátek souboru:

```csharp
using System.Collections.Generic;
using System.Text.Json;
```

Všimněte si, že nyní používáte <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> místo <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> . Serializátor používá jako svůj zdroj datový proud místo řetězce. Pojďme Vysvětleme několik funkcí jazyka C#, které jsou používány v druhém řádku předchozího fragmentu kódu. První argument pro <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> je `await` výraz. (Ostatní dva parametry jsou volitelné a jsou vynechány ve fragmentu kódu.) Výrazy await se můžou vyskytovat skoro kdekoli v kódu, a to i v případě, že jste je teď udělali jenom jako součást příkazu přiřazení. `Deserialize`Metoda je *Obecná*, což znamená, že je nutné zadat argumenty typu pro typ objektu, který by měl být VYTVOŘEN z textu JSON. V tomto příkladu provádíte deserializaci do `List<Repository>` , což je jiný obecný objekt, <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> . `List<>`Třída ukládá kolekci objektů. Argument typu deklaruje typ objektů uložených v `List<>` . Text JSON představuje kolekci objektů úložiště, takže je argument typu `Repository` .

V této části už skoro jste hotovi. Teď, když jste převedli JSON na objekty C#, pojďme zobrazit název každého úložiště. Nahraďte řádky, které se čtou:

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

s následujícím:

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

Zkompilujte a spusťte aplikaci. Vypíše názvy úložišť, která jsou součástí .NET Foundation.

## <a name="controlling-serialization"></a>Řízení serializace

Než přidáte více funkcí, pojďme tuto `name` vlastnost adresovat pomocí `[JsonPropertyName]` atributu. Proveďte následující změny v deklaraci `name` pole v repo.cs:

```csharp
[JsonPropertyName("name")]
public string Name { get; set; }
```

Chcete-li použít `[JsonPropertyName]` atribut, budete muset přidat <xref:System.Text.Json.Serialization> obor názvů do `using` direktiv:

```csharp
using System.Text.Json.Serialization;
```

Tato změna znamená, že potřebujete změnit kód, který zapisuje název každého úložiště v program.cs:

```csharp
Console.WriteLine(repo.Name);
```

Spusťte `dotnet run` , abyste se ujistili, že jsou mapování správná. Měl by se zobrazit stejný výstup jako předtím.

Pojďme ještě před přidáním nových funkcí udělat nějakou další změnu. `ProcessRepositories`Metoda může provádět asynchronní práci a vracet kolekci úložišť. Pojďme `List<Repository>` z této metody vracet a přesunete kód, který zapisuje informace do `Main` metody.

Změnou signatury `ProcessRepositories` vrátíte úkol, jehož výsledkem je seznam `Repository` objektů:

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

Pak jednoduše vraťte úložiště po zpracování odpovědi JSON:

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
return repositories;
```

Kompilátor vygeneruje `Task<T>` objekt pro návrat, protože jste označili tuto metodu jako `async` .
Pak Pojďme `Main` metodu upravit tak, aby zachytit tyto výsledky a zapsala všechny názvy úložišť do konzoly. Vaše `Main` Metoda teď vypadá takto:

```csharp
public static async Task Main(string[] args)
{
    var repositories = await ProcessRepositories();

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

## <a name="reading-more-information"></a>Přečtěte si další informace

Pojďme to dokončit zpracováním několika dalších vlastností v paketu JSON, které se odesílají z rozhraní API GitHubu. Nebudete chtít všechno přidat, ale přidáním několika vlastností se ukáže několik dalších funkcí jazyka C#.

Pojďme začít přidáním několika jednoduchých typů do `Repository` definice třídy. Přidejte tyto vlastnosti do této třídy:

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

Tyto vlastnosti mají předdefinované převody z typu řetězce (což je to, co pakety JSON obsahují) k cílovému typu. <xref:System.Uri>Typ může být pro vás nový. Představuje identifikátor URI, nebo v tomto případě adresu URL. V případě `Uri` typů a platí `int` , že pokud paket JSON obsahuje data, která nejsou převedena na cílový typ, akce serializace vyvolá výjimku.

Jakmile je přidáte, aktualizujte `Main` metodu tak, aby zobrazovala tyto prvky:

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

Jako poslední krok Pojďme přidat informace pro poslední operaci Push. Tyto informace jsou v odpovědi JSON formátované tímto způsobem:

```json
2016-02-08T21:27:00Z
```

Tento formát je koordinovaný světový čas (UTC), takže získáte <xref:System.DateTime> hodnotu, jejíž <xref:System.DateTime.Kind%2A> vlastnost je <xref:System.DateTimeKind.Utc> . Pokud upřednostňujete datum reprezentované ve vašem časovém pásmu, budete muset napsat vlastní metodu převodu. Nejprve definujte `public` vlastnost, která bude obsahovat reprezentaci UTC pro datum a čas ve vaší `Repository` třídě a `LastPush` `readonly` vlastnost, která vrátí datum převedené na místní čas:

```csharp
[JsonPropertyName("pushed_at")]
public DateTime LastPushUtc { get; set; }

public DateTime LastPush => LastPushUtc.ToLocalTime();
```

Pojďme přecházet na nové konstrukce, které jsme právě definovali. `LastPush`Vlastnost je definována pomocí *člena Expression-těle* pro `get` přistupující objekt. K dispozici není žádný `set` přistupující objekt. Vynechání `set` přístupového objektu je způsob, jakým definujete vlastnost *jen pro čtení* v jazyce C#. (Ano, v jazyce C# můžete vytvořit vlastnosti *jen pro zápis* , ale jejich hodnota je omezená.)

Nakonec přidejte do konzoly další příkaz Output a teď budete připraveni tuto aplikaci sestavit a spustit:

```csharp
Console.WriteLine(repo.LastPush);
```

Verze by měla nyní odpovídat [ukázce dokončeno](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).

## <a name="conclusion"></a>Závěr

V tomto kurzu jste si ukázali, jak vytvářet webové požadavky, analyzovat výsledek a zobrazovat vlastnosti těchto výsledků. Přidali jste také nové balíčky jako závislosti ve vašem projektu. Viděli jste některé z funkcí jazyka C#, které podporují objektově orientované techniky.

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
