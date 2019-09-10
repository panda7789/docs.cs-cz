---
title: Vytvoření klienta REST pomocí .NET Core
description: V tomto kurzu se naučíte řadou funkcí v .NET Core a v C# jazyce.
ms.date: 03/06/2017
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 001a9cbaae1cdb57b6451bc42ce326864f8dcf7b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850975"
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

Prvním krokem je vytvoření nové aplikace. Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci. Zajistěte, aby byl aktuální adresář. Zadejte příkaz `dotnet new console` na příkazovém řádku. Tím se vytvoří počáteční soubory pro základní aplikaci "Hello World". Vzhledem k tomu, že se jedná o nový projekt, není zavedena žádná závislost, takže první spuštění stáhne rozhraní .NET Core Framework, nainstaluje certifikát pro vývoj a spustí Správce balíčků NuGet pro obnovení chybějících závislostí.

Než začnete provádět úpravy, zadejte `dotnet run` ([Viz poznámku](#dotnet-restore-note)) na příkazovém řádku a spusťte tak aplikaci. `dotnet run`provede `dotnet restore` automaticky v případě chybějících závislostí ve vašem prostředí. Provádí `dotnet build` se také v případě, že vaše aplikace musí být znovu sestavena.
Po počáteční instalaci budete muset spustit `dotnet restore` pouze nebo `dotnet build` , když to pro váš projekt dává smysl.

## <a name="adding-new-dependencies"></a>Přidávání nových závislostí

Jedním z klíčových cílů pro .NET Core je minimalizace velikosti instalace rozhraní .NET. Pokud aplikace potřebuje pro některé z jejích funkcí další knihovny, přidejte tyto závislosti do souboru C# projektu (\*. csproj). V našem příkladu budete muset přidat `System.Runtime.Serialization.Json` balíček, aby aplikace mohla zpracovávat odpovědi JSON.

Otevřete soubor `csproj` projektu. První řádek souboru by měl vypadat takto:

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

Hned za tento řádek přidejte následující:

```xml
   <ItemGroup>
      <PackageReference Include="System.Runtime.Serialization.Json" Version="4.3.0" />
   </ItemGroup>
```

Většina editorů kódu bude poskytovat dokončování pro různé verze těchto knihoven. Obvykle budete chtít použít nejnovější verzi balíčku, který přidáte. Je však důležité se ujistit, že verze všech balíčků odpovídají a že také odpovídají verzi rozhraní .NET Core Application Framework.

Po provedení těchto změn proveďte `dotnet restore` příkaz ([Viz poznámku](#dotnet-restore-note)), aby se balíček nainstaloval do vašeho systému.

## <a name="making-web-requests"></a>Vytváření webových požadavků

Teď jste připraveni začít načítat data z webu. V této aplikaci si přečtete informace z [rozhraní API GitHubu](https://developer.github.com/v3/). Pojďme si přečíst informace o projektech v rámci [.NET Foundation](https://www.dotnetfoundation.org/) zastřešující. Začnete tím, že si vyžádáte rozhraní API GitHubu, abyste načetli informace o projektech. Koncový bod, který budete používat, <https://api.github.com/orgs/dotnet/repos>je:. Chcete načíst všechny informace o těchto projektech, abyste použili požadavek HTTP GET.
Váš prohlížeč používá také požadavky HTTP GET, takže můžete vložit tuto adresu URL do prohlížeče, abyste viděli informace, které budete dostávat a zpracovávat.

<xref:System.Net.Http.HttpClient> Třídu můžete použít k vytváření webových požadavků. Stejně jako všechna moderní rozhraní API <xref:System.Net.Http.HttpClient> .NET podporuje pouze asynchronní metody pro svá dlouhotrvající rozhraní API.
Začněte vytvořením asynchronní metody. Při sestavování funkčnosti aplikace naplníte implementaci. Začněte otevřením `program.cs` souboru v adresáři projektu a přidáním následující metody `Program` do třídy:

```csharp
private static async Task ProcessRepositories()
{
}
```

Je nutné přidat `using` příkaz na začátek `Main` metody C# <xref:System.Threading.Tasks.Task> , aby kompilátor rozpoznal typ:

```csharp
using System.Threading.Tasks;
```

Pokud v tomto okamžiku sestavíte projekt, zobrazí se pro tuto metodu upozornění vygenerované, protože neobsahuje žádné `await` operátory a spustí se synchronně. Tuto chvíli ignorujte. operátory přidáte `await` při vyplňování metody.

Dále přejmenujte obor názvů definovaný v `namespace` příkazu z jeho výchozí hodnoty `ConsoleApp` na `WebAPIClient`. Později v tomto oboru názvů `repo` definujeme třídu.

Dále aktualizujte `Main` metodu pro volání této metody. `ProcessRepositories` Metoda vrátí úlohu a neukončí program před dokončením této úlohy. Proto je nutné použít `Wait` metodu k blokování a čekání na dokončení úlohy:

```csharp
static void Main(string[] args)
{
    ProcessRepositories().Wait();
}
```

Nyní máte program, který nic nedělá, ale asynchronně ho provede. Pojďme to vylepšit.

Nejprve potřebujete objekt, který je schopný načíst data z webu. <xref:System.Net.Http.HttpClient> k tomu můžete použít. Tento objekt zpracovává požadavek a odpovědi. Vytvořte instanci jedné instance daného typu ve `Program` třídě uvnitř souboru program.cs.

```csharp
namespace WebAPIClient
{
    class Program
    {
        private static readonly HttpClient client = new HttpClient();

        static void Main(string[] args)
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

V horní části souboru budete muset přidat také dvě nové příkazy using, aby se mohla kompilovat:

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

Tato první verze vytvoří webový požadavek na načtení seznamu všech úložišť v rámci organizace dotnet Foundation. (ID gitHubu pro .NET Foundation je "dotnet"). Prvních pár řádků, které jsou <xref:System.Net.Http.HttpClient> pro tento požadavek nastaveny. Nejdřív je nakonfigurovaný tak, aby přijímal odpovědi na adresu JSON pro GitHub.
Tento formát je jednoduše JSON. Další řádek přidá hlavičku uživatelského agenta do všech požadavků od tohoto objektu. Tato dvě záhlaví jsou kontrolována kódem serveru GitHub a jsou nutná k načtení informací z GitHubu.

Po dokončení konfigurace <xref:System.Net.Http.HttpClient>aplikace vytvoříte webový požadavek a načtete odpověď. V této první verzi použijete <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> metodu usnadnění. Tato pohodlná metoda spustí úlohu, která provede webový požadavek, a poté, co požadavek vrátí, načte datový proud odpovědi a extrahuje obsah z datového proudu. Tělo odpovědi je vráceno jako <xref:System.String>. Řetězec je k dispozici po dokončení úkolu.

Poslední dva řádky této metody čekají na daný úkol a pak vytiskněte odpověď do konzoly.
Sestavte aplikaci a spusťte ji. Upozornění na sestavení je nyní pryč, protože `ProcessRepositories` nyní `await` obsahuje operátor. Zobrazí se dlouhé zobrazení textu ve formátu JSON.

## <a name="processing-the-json-result"></a>Zpracování výsledku JSON

V tuto chvíli jste napsali kód, který načte odpověď z webového serveru, a zobrazí text obsažený v této odpovědi. Nyní převedeme tuto odpověď JSON na C# objekty.

Serializátor JSON převede data JSON na C# objekty. Prvním úkolem je definovat typ C# třídy, který bude obsahovat informace, které z této odpovědi použijete. Pojďme to sestavit pomalu, takže začněte jednoduchým C# typem, který obsahuje název úložiště:

```csharp
using System;

namespace WebAPIClient
{
    public class repo
    {
        public string name;
    }
}
```

Výše uvedený kód vložte do nového souboru s názvem "úložiště. cs". Tato verze třídy představuje nejjednodušší cestu pro zpracování dat JSON. Název třídy a název členu odpovídají názvům použitým v paketu JSON namísto následujících C# konvencí. Opravte to tak, že později poskytnete nějaké konfigurační atributy. Tato třída ukazuje další důležitou funkci serializace a deserializace JSON: Ne všechna pole v paketu JSON jsou součástí této třídy.
Serializátor JSON bude ignorovat informace, které nejsou zahrnuté do používaného typu třídy.
Tato funkce usnadňuje vytváření typů, které pracují pouze s podmnožinou polí v paketu JSON.

Teď, když jste vytvořili typ, Pojďme ho deserializovat. Budete muset vytvořit <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> objekt. Tento objekt musí znát typ CLR očekávaný pro načtený paket JSON. Paket z GitHubu obsahuje sekvenci úložišť, takže `List<repo>` je to správný typ. Do `ProcessRepositories` metody přidejte následující řádek:

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<repo>));
```

Používáte dva nové obory názvů, takže je budete muset přidat také:

```csharp
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
```

V dalším kroku použijete serializátor k převedení JSON na C# objekty. Nahraďte volání <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> `ProcessRepositories` v metodě následujícími dvěma řádky:

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = serializer.ReadObject(await streamTask) as List<repo>;
```

Všimněte si, že nyní používáte <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>místo. Serializátor používá jako svůj zdroj datový proud místo řetězce. Pojďme vysvětlit několik funkcí C# jazyka, které se používají ve druhém řádku výše. Argumentem <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> `await` výrazu je výraz. Výrazy await se můžou vyskytovat skoro kdekoli v kódu, a to i v případě, že jste je teď udělali jenom jako součást příkazu přiřazení.

Následně se `as` operátor převede z `object` typu doby kompilace na `List<repo>`.
Deklarace <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> deklaruje, že vrací objekt typu <xref:System.Object?displayProperty=nameWithType>. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)>Vrátí typ, který jste zadali při jeho sestavení (`List<repo>` v tomto kurzu). Pokud převod není úspěšný, `as` operátor vyhodnotí `null`, namísto vyvolání výjimky.

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

Než přidáte více funkcí, pojďme tento `repo` typ adresovat a postupovat podle standardních C# konvencí. Provedete to tak, že použijete anotaci `repo` typu s *atributy* , které řídí způsob fungování serializátoru JSON. V takovém případě použijete tyto atributy k definování mapování mezi názvy klíčů JSON a názvy C# tříd a členů. Používají <xref:System.Runtime.Serialization.DataContractAttribute> se dva atributy a <xref:System.Runtime.Serialization.DataMemberAttribute> . Podle konvence všechny třídy atributů končí v příponě `Attribute`. Tuto příponu však nemusíte používat při použití atributu.

Atributy <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> jsou v jiné knihovně, takže je nutné přidat tuto knihovnu do souboru C# projektu jako závislost. Přidejte následující řádek do `<ItemGroup>` části souboru projektu:

```xml
<PackageReference Include="System.Runtime.Serialization.Primitives" Version="4.3.0" />
```

Po uložení souboru spusťte `dotnet restore` příkaz ([Viz poznámku](#dotnet-restore-note)) pro načtení tohoto balíčku.

Pak otevřete `repo.cs` soubor. Pojďme změnit název tak, aby používal velká písmena jazyka Pascal, a plně hláskovat název `Repository` Pořád chceme mapovat uzly úložiště JSON na tento typ, takže budete muset přidat <xref:System.Runtime.Serialization.DataContractAttribute> atribut do deklarace třídy. Nastavíte `Name` vlastnost atributu na název uzlů JSON, které jsou namapovány na tento typ:

```csharp
[DataContract(Name="repo")]
public class Repository
```

Je členem <xref:System.Runtime.Serialization> oboru názvů, takže budete muset přidat příslušný `using` příkaz na začátek souboru: <xref:System.Runtime.Serialization.DataContractAttribute>

```csharp
using System.Runtime.Serialization;
```

Změnili jste název `repo` třídy na `Repository`, takže budete muset v program.cs udělat stejnou změnu názvu (některé editory můžou podporovat Refaktoring přejmenování, který tuto změnu provede automaticky:).

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<Repository>));

// ...

var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
```

Nyní provedeme stejnou změnu s `name` polem <xref:System.Runtime.Serialization.DataMemberAttribute> pomocí třídy. Proveďte následující změny v deklaraci `name` pole v repo.cs:

```csharp
[DataMember(Name="name")]
public string Name;
```

Tato změna znamená, že potřebujete změnit kód, který zapisuje název každého úložiště v program.cs:

```csharp
Console.WriteLine(repo.Name);
```

Po následování a `dotnet run` se ujistěte, že jsou mapování správná. `dotnet build` Měl by se zobrazit stejný výstup jako předtím. Než my zpracujeme další vlastnosti z webového serveru, Pojďme udělat ještě jednu změnu `Repository` třídy. `Name` Člen je veřejně přístupný pole. To není dobrý postup orientovaný na objekt, takže ho můžeme změnit na vlastnost. Pro naše účely nepotřebujeme, aby při získávání nebo nastavování vlastnosti běžel žádný konkrétní kód, ale změna na vlastnost usnadňuje přidávání těchto změn později, aniž by došlo k `Repository` porušení kódu, který používá třídu.

Odeberte definici pole a nahraďte ji pomocí [automaticky implementované vlastnosti](../programming-guide/classes-and-structs/auto-implemented-properties.md):

```csharp
public string Name { get; set; }
```

Kompilátor generuje tělo `get` a přistupující objekty a `set` také soukromé pole pro uložení názvu. Je podobný následujícímu kódu, který jste mohli zadat ručně:

```csharp
public string Name
{
    get { return this._name; }
    set { this._name = value; }
}
private string _name;
```

Pojďme ještě před přidáním nových funkcí udělat nějakou další změnu. `ProcessRepositories` Metoda může provádět asynchronní práci a vracet kolekci úložišť. Pojďme `List<Repository>` z této metody vracet a přesunete kód, který zapisuje informace `Main` do metody.

Změnou signatury `ProcessRepositories` vrátíte úkol, jehož výsledkem je `Repository` seznam objektů:

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

Pak jednoduše vraťte úložiště po zpracování odpovědi JSON:

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

Kompilátor vygeneruje `Task<T>` objekt pro návrat, protože jste označili tuto metodu jako `async`.
Pak Pojďme `Main` metodu upravit tak, aby zachytit tyto výsledky a zapsala všechny názvy úložišť do konzoly. Vaše `Main` metoda teď vypadá takto:

```csharp
public static void Main(string[] args)
{
    var repositories = ProcessRepositories().Result;

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

Přístup k `Result` vlastnosti bloků úkolu, dokud se úloha nedokončí. Normálně byste měli preferovat `await` dokončení úlohy, jako `ProcessRepositories` v metodě, ale `Main` které nejsou v metodě povoleny.

## <a name="reading-more-information"></a>Přečtěte si další informace

Pojďme to dokončit zpracováním několika dalších vlastností v paketu JSON, které se odesílají z rozhraní API GitHubu. Nebudete chtít všechno přidat, ale přidáním několika vlastností se ukáže několik dalších funkcí tohoto C# jazyka.

Pojďme začít přidáním několika jednoduchých typů do `Repository` definice třídy. Přidejte tyto vlastnosti do této třídy:

```csharp
[DataMember(Name="description")]
public string Description { get; set; }

[DataMember(Name="html_url")]
public Uri GitHubHomeUrl { get; set; }

[DataMember(Name="homepage")]
public Uri Homepage { get; set; }

[DataMember(Name="watchers")]
public int Watchers { get; set; }
```

Tyto vlastnosti mají předdefinované převody z typu řetězce (což je to, co pakety JSON obsahují) k cílovému typu. <xref:System.Uri> Typ může být pro vás nový. Představuje identifikátor URI, nebo v tomto případě adresu URL. V případě `Uri` typů a `int` platí, že pokud paket JSON obsahuje data, která nejsou převedena na cílový typ, akce serializace vyvolá výjimku.

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

Tento formát nedodržuje žádné standardní formáty .NET <xref:System.DateTime> . Z tohoto důvodu budete muset napsat vlastní metodu převodu. Pravděpodobně nebudete chtít, aby Nezpracovaný řetězec byl vystaven uživatelům `Repository` třídy. Atributy mohou také určovat. Nejprve definujte `private` vlastnost, která bude obsahovat řetězcové vyjádření data a času ve vaší `Repository` třídě:

```csharp
[DataMember(Name="pushed_at")]
private string JsonDate { get; set; }
```

<xref:System.Runtime.Serialization.DataMemberAttribute> Atribut informuje serializátor, který by měl být zpracován, i když se nejedná o veřejný člen. Dále musíte napsat veřejnou vlastnost jen pro čtení, která převede řetězec na platný <xref:System.DateTime> objekt a vrátí to: <xref:System.DateTime>

```csharp
[IgnoreDataMember]
public DateTime LastPush
{
    get
    {
        return DateTime.ParseExact(JsonDate, "yyyy-MM-ddTHH:mm:ssZ", CultureInfo.InvariantCulture);
    }
}
```

Pojďme přejít na výše uvedené nové konstrukce. `IgnoreDataMember` Atribut instruuje serializátor, že tento typ by neměl být čten nebo napsán z libovolného objektu JSON. Tato vlastnost obsahuje pouze `get` přistupující objekt. K dispozici `set` není žádný přistupující objekt. To je způsob, jak definovat vlastnost *jen pro čtení* v C#. (Ano, můžete vytvořit vlastnosti *pouze pro zápis* v C#, ale jejich hodnota je omezená.) Metoda analyzuje řetězec a <xref:System.DateTime> vytvoří objekt pomocí poskytnutého formátu data a `DateTime` přidá další `CultureInfo` metadata do objektu pomocí objektu. <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> Pokud operace analýzy není úspěšná, přistupující objekt vlastnosti vyvolá výjimku.

Chcete- <xref:System.Globalization.CultureInfo.InvariantCulture>li použít, budete muset <xref:System.Globalization> přidat obor názvů do `using` příkazů v `repo.cs`:

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
