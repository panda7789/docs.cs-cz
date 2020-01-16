---
title: Vytvoření klienta REST pomocí .NET Core
description: V tomto kurzu se naučíte řadou funkcí v .NET Core a v C# jazyce.
ms.date: 01/09/2020
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 9478966598a9aaa1e9f592b72afce8f878a38abf
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964411"
---
# <a name="rest-client"></a>Klient REST

## <a name="introduction"></a>Úvod

V tomto kurzu se naučíte řadou funkcí v .NET Core a v C# jazyce. Naučíte se:

* Základní informace o rozhraní příkazového řádku (CLI) .NET Core
* Přehled funkcí C# jazyka.
* Správa závislostí pomocí NuGet
* Komunikace HTTP
* Zpracování informací JSON
* Správa konfigurace s atributy.

Vytvoříte aplikaci, která vydává požadavky HTTP na službu REST na GitHubu. Přečtete si informace ve formátu JSON a převeďte tento paket JSON na C# objekty. Nakonec uvidíte, jak pracovat s C# objekty.

V tomto kurzu máte spoustu funkcí. Pojďme je sestavit jednou po jednom.

Pokud chcete postupovat spolu s [závěrečnou ukázkou](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) tohoto tématu, můžete si ho stáhnout. Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Požadavky

Budete muset nastavit počítač tak, aby běžel .NET Core. Pokyny k instalaci najdete na stránce [soubory ke stažení pro .NET Core](https://dotnet.microsoft.com/download) . Tuto aplikaci můžete spustit na Windows, Linux, macOS nebo v kontejneru Docker.
Budete muset nainstalovat svůj oblíbený editor kódu. Níže uvedené popisy používají [Visual Studio Code](https://code.visualstudio.com/), což je Open Source Editor pro různé platformy. Můžete ale použít jakékoli nástroje, se kterými máte v pohodlí.

## <a name="create-the-application"></a>Vytvoření aplikace

Prvním krokem je vytvoření nové aplikace. Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci. Zajistěte, aby byl aktuální adresář. V okně konzoly zadejte následující příkaz:

```dotnetcli
dotnet new console --name WebApiClient
```

Tím se vytvoří počáteční soubory pro základní aplikaci "Hello World". Název projektu je "WebApiClient". Vzhledem k tomu, že se jedná o nový projekt, není zavedena žádná závislost, takže první spuštění stáhne rozhraní .NET Core Framework, nainstaluje certifikát pro vývoj a spustí Správce balíčků NuGet pro obnovení chybějících závislostí.

Než začnete provádět úpravy, zadejte `dotnet run` ([Viz poznámku](#dotnet-restore-note)) na příkazovém řádku a spusťte tak aplikaci. `dotnet run` automaticky provádí `dotnet restore` v případě chybějících závislostí ve vašem prostředí. Také provádí `dotnet build`, pokud vaše aplikace musí být znovu sestavena.
Po počáteční instalaci budete muset spustit pouze `dotnet restore` nebo `dotnet build`, pokud to pro váš projekt dává smysl.

## <a name="adding-new-dependencies"></a>Přidávání nových závislostí

Jedním z klíčových cílů pro .NET Core je minimalizace velikosti instalace rozhraní .NET. Pokud aplikace potřebuje pro některé z jejích funkcí další knihovny, přidejte tyto závislosti do souboru C# projektu (\*. csproj). V našem příkladu budete muset přidat balíček `System.Runtime.Serialization.Json`, aby mohla aplikace zpracovat odpovědi JSON.

Pro tuto aplikaci budete potřebovat balíček `System.Runtime.Serialization.Json`. Přidejte ho do projektu spuštěním následujícího příkazu [rozhraní .NET CLI](../../core/tools/dotnet-add-package.md) :

```console
dotnet add package System.Text.Json
```

## <a name="making-web-requests"></a>Vytváření webových požadavků

Teď jste připraveni začít načítat data z webu. V této aplikaci si přečtete informace z [rozhraní API GitHubu](https://developer.github.com/v3/). Pojďme si přečíst informace o projektech v rámci [.NET Foundation](https://www.dotnetfoundation.org/) zastřešující. Začnete tím, že si vyžádáte rozhraní API GitHubu, abyste načetli informace o projektech. Koncový bod, který budete používat, je: <https://api.github.com/orgs/dotnet/repos>. Chcete načíst všechny informace o těchto projektech, abyste použili požadavek HTTP GET.
Váš prohlížeč používá také požadavky HTTP GET, takže můžete vložit tuto adresu URL do prohlížeče, abyste viděli informace, které budete dostávat a zpracovávat.

Třídu <xref:System.Net.Http.HttpClient> použijte k vytváření webových požadavků. Stejně jako všechna moderní rozhraní API .NET <xref:System.Net.Http.HttpClient> podporuje pouze asynchronní metody pro svá dlouhotrvající rozhraní API.
Začněte vytvořením asynchronní metody. Při sestavování funkčnosti aplikace naplníte implementaci. Začněte tím, že otevřete soubor `program.cs` v adresáři projektu a přidáte následující metodu do `Program` třídy:

```csharp
private static async Task ProcessRepositories()
{
}
```

V horní části metody `Main` budete muset přidat příkaz `using`, aby C# kompilátor rozpoznal typ <xref:System.Threading.Tasks.Task>:

```csharp
using System.Threading.Tasks;
```

Pokud v tomto okamžiku sestavíte projekt, zobrazí se pro tuto metodu upozornění vygenerované, protože neobsahuje žádné operátory `await` a spustí se synchronně. Tuto chvíli ignorujte. přidáte `await` operátory při vyplňování metody.

Dále přejmenujte obor názvů definovaný v příkazu `namespace` z jeho výchozího `ConsoleApp` na `WebAPIClient`. Později v tomto oboru názvů definujeme třídu `repo`.

Dále aktualizujte metodu `Main` pro volání této metody. Metoda `ProcessRepositories` vrátí úlohu a neukončí program před dokončením této úlohy. Proto je nutné změnit signaturu `Main`. Přidejte modifikátor `async` a změňte návratový typ na `Task`. Pak v těle metody přidejte volání `ProcessRepositories`. Přidejte klíčové slovo `await` při volání této metody:

```csharp
static Task Main(string[] args)
{
    await ProcessRepositories();
}
```

Nyní máte program, který nic nedělá, ale asynchronně ho provede. Pojďme to vylepšit.

Nejprve potřebujete objekt, který je schopný načíst data z webu. k tomu můžete použít <xref:System.Net.Http.HttpClient>. Tento objekt zpracovává požadavek a odpovědi. Vytvořte instanci jedné instance daného typu ve třídě `Program` v souboru Program.cs.

```csharp
namespace WebAPIClient
{
    class Program
    {
        private static readonly HttpClient client = new HttpClient();

        static Task Main(string[] args)
        {
            //...
        }
    }
}
```

Pojďme se zpátky do metody `ProcessRepositories` a vyplnit první verzi IT:

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

V horní části souboru budete muset přidat také dvě nové příkazy using, aby se mohla kompilovat:

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

Tato první verze vytvoří webový požadavek na načtení seznamu všech úložišť v rámci organizace dotnet Foundation. (ID gitHubu pro .NET Foundation je "dotnet"). První pár řádků nastavil <xref:System.Net.Http.HttpClient> pro tuto žádost. Nejdřív je nakonfigurovaný tak, aby přijímal odpovědi na adresu JSON pro GitHub.
Tento formát je jednoduše JSON. Další řádek přidá hlavičku uživatelského agenta do všech požadavků od tohoto objektu. Tato dvě záhlaví jsou kontrolována kódem serveru GitHub a jsou nutná k načtení informací z GitHubu.

Po dokončení konfigurace <xref:System.Net.Http.HttpClient>vytvoříte webový požadavek a načtete odpověď. V této první verzi použijete metodu <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> pohodlí. Tato pohodlná metoda spustí úlohu, která provede webový požadavek, a poté, co požadavek vrátí, načte datový proud odpovědi a extrahuje obsah z datového proudu. Tělo odpovědi je vráceno jako <xref:System.String>. Řetězec je k dispozici po dokončení úkolu.

Poslední dva řádky této metody čekají na daný úkol a pak vytiskněte odpověď do konzoly.
Sestavte aplikaci a spusťte ji. Upozornění na sestavení je teď pryč, protože `ProcessRepositories` nyní obsahuje operátor `await`. Zobrazí se dlouhé zobrazení textu ve formátu JSON.

## <a name="processing-the-json-result"></a>Zpracování výsledku JSON

V tuto chvíli jste napsali kód, který načte odpověď z webového serveru, a zobrazí text obsažený v této odpovědi. Nyní převedeme tuto odpověď JSON na C# objekty.

Třída <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> serializace objektů do formátu JSON a deserializace JSON do objektů. Začněte definováním třídy představující `repo` objekt JSON vrácený z rozhraní API GitHubu:

```csharp
using System;

namespace WebAPIClient
{
    public class Repository
    {
        public string name { get; set; };
    }
}
```

Výše uvedený kód vložte do nového souboru s názvem "úložiště. cs". Tato verze třídy představuje nejjednodušší cestu pro zpracování dat JSON. Název třídy a název členu odpovídají názvům použitým v paketu JSON namísto následujících C# konvencí. Opravte to tak, že později poskytnete nějaké konfigurační atributy. Tato třída ukazuje další důležitou funkci serializace a deserializace JSON: Ne všechna pole v paketu JSON jsou součástí této třídy.
Serializátor JSON bude ignorovat informace, které nejsou zahrnuté do používaného typu třídy.
Tato funkce usnadňuje vytváření typů, které pracují pouze s podmnožinou polí v paketu JSON.

Teď, když jste vytvořili typ, Pojďme ho deserializovat. 

V dalším kroku použijete serializátor k převedení JSON na C# objekty. Nahraďte volání <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> v metodě `ProcessRepositories` následující tři řádky:

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
return repositories;
```

Používáte nový obor názvů, takže ho budete muset přidat i na začátek souboru:

```csharp
using System.Text.Json;
```

Všimněte si, že teď místo <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>používáte <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)>. Serializátor používá jako svůj zdroj datový proud místo řetězce. Pojďme Vysvětleme několik funkcí C# jazyka, které se používají v druhém řádku předchozího fragmentu kódu. Prvním argumentem, který je <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType>, je výraz `await`. (Ostatní dva parametry jsou volitelné a jsou vynechány ve fragmentu kódu.) Výrazy await se můžou vyskytovat skoro kdekoli v kódu, a to i v případě, že jste je teď udělali jenom jako součást příkazu přiřazení. Metoda `Deserialize` je *Obecná*, což znamená, že je nutné zadat argumenty typu pro typ objektu, který by měl být vytvořen z textu JSON. V tomto příkladu provádíte deserializaci do `List<Repository>`, což je jiný obecný objekt, <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>. Třída `List<>` ukládá kolekci objektů. Argument typu deklaruje typ objektů uložených v `List<>`. Text JSON představuje kolekci objektů úložiště, takže je argument typu `Repository`.

V této části už skoro jste hotovi. Teď, když jste převedli JSON C# na objekty, pojďme zobrazit název každého úložiště. Nahraďte řádky, které se čtou:

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

Než přidáte další funkce, předejte adresu `name` vlastnosti pomocí atributu `[JsonPropertyName]`. Proveďte následující změny v deklaraci pole `name` v repo.cs:

```csharp
[JsonPropertyName("name")]
public string Name { get; set; }
```

Tato změna znamená, že potřebujete změnit kód, který zapisuje název každého úložiště v program.cs:

```csharp
Console.WriteLine(repo.Name);
```

Spusťte `dotnet run`, abyste se ujistili, že jsou mapování správná. Měl by se zobrazit stejný výstup jako předtím.

Pojďme ještě před přidáním nových funkcí udělat nějakou další změnu. Metoda `ProcessRepositories` může provádět asynchronní práci a vracet kolekci úložišť. Pojďme z této metody vracet `List<Repository>` a přesunete kód, který zapisuje informace do metody `Main`.

Změňte podpis `ProcessRepositories` a vraťte úkol, jehož výsledkem je seznam objektů `Repository`:

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

Pak jednoduše vraťte úložiště po zpracování odpovědi JSON:

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

Kompilátor vygeneruje objekt `Task<T>` pro návrat, protože jste tuto metodu označili jako `async`.
Pak upravíte metodu `Main` tak, aby zachytit tyto výsledky a zapsala jednotlivé názvy úložišť do konzoly. Vaše metoda `Main` nyní vypadá takto:

```csharp
public static Task Main(string[] args)
{
    var repositories = await ProcessRepositories();

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

## <a name="reading-more-information"></a>Přečtěte si další informace

Pojďme to dokončit zpracováním několika dalších vlastností v paketu JSON, které se odesílají z rozhraní API GitHubu. Nebudete chtít všechno přidat, ale přidáním několika vlastností se ukáže několik dalších funkcí tohoto C# jazyka.

Pojďme začít přidáním několika jednoduchých typů do definice `Repository` třídy. Přidejte tyto vlastnosti do této třídy:

```csharp
[JsonPropertyName(Name="description")]
public string Description { get; set; }

[JsonPropertyName(Name="html_url")]
public Uri GitHubHomeUrl { get; set; }

[JsonPropertyName(Name="homepage")]
public Uri Homepage { get; set; }

[JsonPropertyName(Name="watchers")]
public int Watchers { get; set; }
```

Tyto vlastnosti mají předdefinované převody z typu řetězce (což je to, co pakety JSON obsahují) k cílovému typu. Typ <xref:System.Uri> může být pro vás nový. Představuje identifikátor URI, nebo v tomto případě adresu URL. V případě `Uri` a `int`ch typů platí, že pokud paket JSON obsahuje data, která nejsou převedena na cílový typ, akce serializace vyvolá výjimku.

Jakmile je přidáte, aktualizujte metodu `Main`, aby zobrazovala tyto prvky:

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

Tento formát nedodržuje žádné standardní <xref:System.DateTime> formáty .NET. Z tohoto důvodu budete muset napsat vlastní metodu převodu. Pravděpodobně nebudete chtít, aby Nezpracovaný řetězec byl vystaven uživatelům třídy `Repository`. Atributy mohou také určovat. Nejprve definujte vlastnost `public`, která bude obsahovat řetězcové vyjádření data a času ve vaší třídě `Repository` a vlastnost `LastPush` `readonly`, která vrací formátovaný řetězec, který představuje vrácené datum:

```csharp
[JsonPropertyName(Name="pushed_at")]
public string JsonDate { get; set; }

public DateTime LastPush =>
    DateTime.ParseExact(JsonDate, "yyyy-MM-ddTHH:mm:ssZ", CultureInfo.InvariantCulture);
```

Pojďme přecházet na nové konstrukce, které jsme právě definovali. Vlastnost `LastPush` je definována pomocí *člena Expression-těle* pro přistupující objekt `get`. Neexistuje žádný přistupující objekt `set`. Vynechání přístupového objektu `set` je způsob, jakým definujete vlastnost C# *jen pro čtení* v. (Ano, můžete vytvořit vlastnosti *pouze pro zápis* v C#, ale jejich hodnota je omezená.) Metoda <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> analyzuje řetězec a vytvoří objekt <xref:System.DateTime> pomocí poskytnutého formátu data a přidá další metadata do `DateTime` pomocí objektu `CultureInfo`. Pokud operace analýzy není úspěšná, přistupující objekt vlastnosti vyvolá výjimku.

Chcete-li použít <xref:System.Globalization.CultureInfo.InvariantCulture>, bude nutné přidat <xref:System.Globalization> oboru názvů do příkazů `using` v `repo.cs`:

```csharp
using System.Globalization;
```

Nakonec přidejte do konzoly další příkaz Output a teď budete připraveni tuto aplikaci sestavit a spustit:

```csharp
Console.WriteLine(repo.LastPush);
```

Verze by měla nyní odpovídat [ukázce dokončeno](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).

## <a name="conclusion"></a>Závěr

V tomto kurzu jste si ukázali, jak vytvářet webové požadavky, analyzovat výsledek a zobrazovat vlastnosti těchto výsledků. Přidali jste také nové balíčky jako závislosti ve vašem projektu. Seznámili jste se s některými funkcemi C# jazyka, který podporuje objektově orientované techniky.

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
