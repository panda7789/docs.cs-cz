---
title: "Vytvoření klienta REST pomocí .NET Core"
description: "V tomto kurzu se dozvíte, jaké celou řadu funkcí v .NET Core a jazyka C#."
keywords: "Rozhraní .NET, .NET core"
author: BillWagner
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 6b0f3acc3a6dbed4f44497d92d3c518ee5a5d2a7
ms.sourcegitcommit: dd6ea7f0e581ac84e0a90d9b23c463fcf1ec3ce7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2018
---
# <a name="rest-client"></a>Klienta REST

## <a name="introduction"></a>Úvod
V tomto kurzu se dozvíte, jaké celou řadu funkcí v .NET Core a jazyka C#. Naučíte:
*   Základy .NET Core rozhraní příkazového řádku (CLI).
*   Přehled funkcí jazyka C#.
*   Správa závislostí s NuGet
*   Komunikace HTTP
*   Informace o zpracování JSON
*   Správa konfigurací s atributy. 

Budete sestavit aplikaci, která vydává požadavků HTTP pro službu REST na Githubu. Budete přečtěte si informace ve formátu JSON a převést paketu JSON na objekty C#. Nakonec uvidíte, jak pracovat s objekty jazyka C#.

V tomto kurzu je celá řada funkcí. Umožňuje vytvořit, je po jednom.

Pokud dáváte přednost použijte spolu s [konečný vzorek](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-webapiclient) pro toto téma, můžete ho stáhnout. Pokyny ke stažení najdete v tématu [ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Požadavky
Budete muset nastavit svůj počítač ke spuštění .NET core. Pokyny k instalaci najdete na [.NET Core](https://www.microsoft.com/net/core) stránky. Tuto aplikaci můžete spustit v systému Windows, Linux, systému macOS nebo v kontejner Docker. Budete muset nainstalovat editor vaše oblíbené kódu. Popisy níže použijte [Visual Studio Code](https://code.visualstudio.com/), který je typu open source pro různé platformy editor. Můžete však použít, ať nástroje umíte pracovat s.
## <a name="create-the-application"></a>Vytvoření aplikace
Prvním krokem je vytvoření nové aplikace. Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci. Nastavit aktuální adresář. Zadejte příkaz `dotnet new console` na příkazovém řádku. Tím se vytvoří počáteční soubory pro základní aplikace "Hello World".

Než začnete, provádění změn, přejděte přes kroky a spusťte tak jednoduchou aplikaci Hello World. Po vytvoření aplikace, zadejte `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) na příkazovém řádku. Tento příkaz spustí proces obnovení balíčku NuGet. NuGet je Správce balíčků .NET. Tento příkaz stáhne všechny chybějící závislosti pro váš projekt. Toto je nový projekt, žádné závislosti na místě, se tak během prvního spuštění stáhnou rozhraní .NET Core. Po provedení tohoto kroku počáteční se jenom musíte spustit `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) při přidání nové závislé balíčky nebo aktualizace verze všechny svoje závislosti.  

Po obnovení balíčků, můžete spustit `dotnet build`. To provede modul sestavení a vytvoří vaší aplikace. Nakonec spuštěním `dotnet run` spusťte aplikaci.

## <a name="adding-new-dependencies"></a>Přidání nové závislosti
Jedním z hlavních cílů aplikace .NET Core je minimální velikost instalace rozhraní .NET framework. Rozhraní .NET Core obsahuje pouze běžných prvků úplné rozhraní .NET Framework. Pokud aplikace potřebuje další knihovny pro některé jeho funkce, přidejte tyto závislosti do projektu C# (\*.csproj) souboru. Pro náš příklad, budete muset přidat `System.Runtime.Serialization.Json` balíčku, vaše aplikace může zpracovat odpovědi JSON.

Otevřete váš `csproj` souboru projektu. První řádek souboru by měla vypadat jako:

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

Přidejte následující okamžitě po tomto řádku: 

```xml
   <ItemGroup>
      <PackageReference Include="System.Runtime.Serialization.Json" Version="4.3.0" />
   </ItemGroup> 
```
Většinu kódu editory poskytne dokončení pro různé verze tyto knihovny. Obvykle budete chtít použít nejnovější verzi balíčku, která přidáte. Je však potřeba se ujistit, že verze všech balíčků odpovídá, a aby splňovaly verzi rozhraní .NET Core.

Po provedení těchto změn, byste měli spustit `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) znovu, aby balíček nainstalován ve vašem systému.

## <a name="making-web-requests"></a>Provádění webových požadavků
Teď jste připravení zahájit načítání dat z webu. V této aplikaci, budete pro čtení informací z [Githubu API](https://developer.github.com/v3/). Umožňuje načíst informace o projekty v části [.NET Foundation](http://www.dotnetfoundation.org/) zastřešující. Ukázku zahájíte tím, že žádost na rozhraní API Githubu k načtení informací o projektech. Koncový bod, které budete používat: [https://api.github.com/orgs/dotnet/repos](https://api.github.com/orgs/dotnet/repos). Chcete načíst všechny informace o těchto projekty, takže budete používat požadavek HTTP GET.
Váš prohlížeč používá také HTTP GET požadavků a vložit, adresu URL do prohlížeče jaké informace můžete budete být přijímání a zpracování.

Můžete použít <xref:System.Net.Http.HttpClient> třída k vytvoření webových požadavků. Všechny moderní API technologie .NET, například <xref:System.Net.Http.HttpClient> podporuje pouze asynchronní metody pro jeho dlouho běžící rozhraní API.
Spustit tím, že asynchronní metody. Při sestavování funkce aplikace, budete implementace vyplnit. Začněte otevřením `program.cs` soubor v adresáři projektu a přidání metodu `Program` třídy:

```csharp
private static async Task ProcessRepositories()
{
    
}
```

Budete muset přidat `using` příkaz v horní části vaší `Main` metoda tak, aby rozpozná kompilátor jazyka C# <xref:System.Threading.Tasks.Task> typu:

```csharp
using System.Threading.Tasks;
```

Pokud nyní vytvoříte projekt, protože neobsahuje žádné získáte upozornění generovaná pro tato metoda `await` operátory a spustí synchronně. Ignorovat, teď; přidáte `await` operátory jako můžete vyplnit metodu.

V dalším kroku přejmenovat definovaný v oboru názvů `namespace` příkaz z výchozí hodnoty `ConsoleApp` k `WebAPIClient`. Budeme později definovat `repo` třídy v tomto oboru názvů.

Potom aktualizujte `Main` metoda mohli volat tuto metodu. `ProcessRepositories` Metoda vrátí úlohu, a neměly by se ukončovat program, než dokončení této úlohy. Proto je nutné použít `Wait` metoda blokovat a počkejte na dokončení úlohy:

```csharp
public static void Main(string[] args)
{
    ProcessRepositories().Wait();
}
```

Nyní máte program, který nic neprovádí, ale dělá asynchronně. Umožňuje zvýšit.

Je třeba nejprve objekt, který je schopen načíst data z webu; můžete použít <xref:System.Net.Http.HttpClient> to provést. Tento objekt zpracovává žádosti a odpovědi. Vytvořit jednu instanci daného typu v `Program` – třída v souboru Program.cs.

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

 Přejděte zpět do `ProcessRepositories` metoda a vyplňte v první verzi:

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

Budete muset přidat také dva nové kompilace pomocí příkazů v horní části souboru pro tento:

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

Tato první verze vytvoří žádost webové číst seznam všech úložiště v rámci organizace foundation dotnet. (ID Githubu .NET Foundation je 'dotnet.). Nastavit několik prvních řádků <xref:System.Net.Http.HttpClient> pro tento požadavek. Nejprve je nakonfigurován tak, aby přijímal odpovědi JSON Githubu.
Tento formát je jednoduše JSON. Na další řádek přidá hlavičku uživatelského agenta na všechny požadavky z tohoto objektu. Tyto dvě hlavičky se ověří pomocí kódu serveru Githubu a jsou nezbytné k načtení informací z Githubu.

Po dokončení konfigurace <xref:System.Net.Http.HttpClient>, provedete webové žádosti a načíst odpověď. V této verzi první použijete <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> metoda pohodlí. Tato metoda pohodlí spustí úlohu, která provede webový požadavek, a pak po dokončení žádosti, čtení datového proudu odpovědi a extrahuje obsah z datového proudu. Text odpovědi se vrátí jako <xref:System.String>. Řetězec je k dispozici po dokončení úlohy. 

Poslední dva řádky této metody await této úlohy a poté vytiskněte odpověď na konzole.
Sestavte aplikaci a spusťte ho. Upozornění sestavení je pryč nyní, protože `ProcessRepositories` nyní neobsahuje `await` operátor. Uvidíte, že se že jedná o dlouho zobrazení JSON formátovaného textu.   

## <a name="processing-the-json-result"></a>Zpracování výsledku JSON

V tomto okamžiku jste zapisují kód načíst odpověď z webového serveru, a zobrazit text, který je obsažený v této odpovědi. Dále umožňuje převést tuto odpověď JSON na objekty C#.

Serializátor JSON převede JSON data na objekty C#. První úlohou je definice typu třídy jazyka C# obsahuje informace, které můžete použít z této odpovědi. Vytvořme tomto pomalu, takže začněte s jednoduché C# typu, který obsahuje název úložiště:

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

Uveďte ve výše uvedeném kódu v nový soubor s názvem 'repo.cs'. Tato verze třídy představuje nejjednodušší cestu ke zpracování dat JSON. Název třídy a člen název odpovídat názvů používaných v paketu JSON, místo následující konvence C#. Budete to opravíme tím, že poskytuje některé konfigurační atributy později. Tato třída představuje další důležité funkcí JSON serializace a deserializace: Ne všechna pole v paketu JSON jsou součástí této třídy.
Serializátor JSON bude ignorovat informace, které nejsou součástí typu třídy, který je používán.
Tato funkce usnadňuje vytvoření typů, které pracují se jenom podmnožinu pole v paketu JSON.

Teď, když jste vytvořili typ, můžeme deserializaci. Budete muset vytvořit <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> objektu. Tento objekt musíte znát typ CLR očekávala paketu JSON načte. Paket z Githubu obsahuje posloupnost úložiště, takže `List<repo>` není správného typu. Přidejte následující řádek na vaše `ProcessRepositories` metoda:

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<repo>));
```

Používáte dva nové obory názvů, takže budete muset přidat ty také:

```csharp
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
```

V dalším kroku použijete serializátor JSON převést na objekty C#. Nahraďte volání <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> ve vaší `ProcessRepositories` metoda s následující dva řádky:

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = serializer.ReadObject(await streamTask) as List<repo>;
```

Všimněte si, že teď používáte <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> místo <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>. Serializátor používá jako zdroj datového proudu místo řetězec. Pojďme vysvětlují několik funkcí jazyka C#, které jsou používány ve druhém řádku výše. Argument <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> je `await` výrazu. Await výrazy může vyskytovat téměř kdekoli v kódu, i když až zatím Seznámili jste se pouze jejich v rámci příkazu přiřazení.

Za druhé `as` operátor převede z typu čas kompilace `object` k `List<repo>`. Prohlášení o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> deklaruje, že vrací objekt typu <xref:System.Object?displayProperty=nameWithType>. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)>Vrátí typ, který jste zadali, když se vám ho (`List<repo>` v tomto kurzu). Pokud převod neproběhne úspěšně, `as` vyhodnocen jako operátor `null`, místo došlo k výjimce.

Téměř jste hotovi s v této části. Teď, když jste převést JSON na objekty C#, můžeme zobrazí název každé úložiště. Nahraďte řádky, které čtou:

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

pomocí následující:

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

Zkompilování a spuštění aplikace. Vytiskne názvy úložiště, které jsou součástí služby .NET Foundation.

## <a name="controlling-serialization"></a>Řízení serializace

Než přidáte další funkce, budeme adres `repo` zadejte a nastavit jej konvencemi více standardní C#. Můžete to udělat pomocí zadávání poznámek k `repo` zadejte s *atributy* které řídí, jak funguje serializátor JSON. V případě použijete tyto atributy definovat mapování mezi názvy klíčů JSON a C# třídy a člen názvy. Jsou dva atributy používané `DataContract` atribut a `DataMember` atribut. Podle konvence všechny třídy atributů končit příponou `Attribute`. Však není potřeba použít tuto příponu, když použijete atribut. 

`DataContract` a `DataMember` atributy jsou různé knihovny, takže budete muset přidat této knihovny do souboru projektu C# jako závislost. Přidejte následující řádek na `<ItemGroup>` části souboru projektu:

```xml
<PackageReference Include="System.Runtime.Serialization.Primitives" Version="4.3.0" />
```

Po uložení souboru spouštět `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) pro načtení tohoto balíčku.

Dále otevřete `repo.cs` souboru. Umožňuje změnit název Pascalcase a plně pravopisu název `Repository`. Chceme mapování JSON, úložiště, uzly na tento typ, takže budete muset přidat `DataContract` atribut deklaraci třídy. Budete nastavíte `Name` vlastnost na název JSON uzlů, které jsou mapovány na tento typ atributu:

```csharp
[DataContract(Name="repo")]
public class Repository
```

<xref:System.Runtime.Serialization.DataContractAttribute> Je členem skupiny <xref:System.Runtime.Serialization> obor názvů, takže budete muset přidat odpovídající `using` příkaz v horní části souboru:

```csharp
using System.Runtime.Serialization;
```

Změnit název `repo` třídy k `Repository`, takže budete potřebovat, aby se stejným názvem změnit v souboru Program.cs (Některé editory můžou podporovat přejmenování refaktoring, která bude tuto změnu provést automaticky:)

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<Repository>));

// ...

var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
```

V dalším kroku provedeme stejné změny s `name` pole pomocí <xref:System.Runtime.Serialization.DataMemberAttribute> – třída. Proveďte následující změny k prohlášení o `name` pole repo.cs:

```csharp
[DataMember(Name="name")]
public string Name;
```

Tato změna znamená, že budete muset změnit kód, který zapisuje do souboru program.cs název každé úložiště:

```csharp
Console.WriteLine(repo.Name);
```

Proveďte `dotnet build` následuje `dotnet run` a ujistěte se, máte k dispozici mapování správný. Měli byste vidět stejný výstup jako před. Před jsme zpracovat další vlastnosti z webového serveru, můžeme provést jeden další změny pro `Repository` třídy. `Name` Člen je veřejně dostupná pole. Není vhodné objektově orientované, takže můžeme ho změnit na vlastnost. Pro naše účely jsme nepotřebují žádné konkrétní spuštění kódu při získání nebo nastavení vlastnosti, ale změna na vlastnost usnadňuje přidat tyto změny později, aniž by vás kód, který používá `Repository` třídy.

Odebrat definici pole a nahraďte ho [automaticky implementované vlastnosti](../programming-guide/classes-and-structs/auto-implemented-properties.md):

```csharp
public string Name { get; set; }
```

Kompilátor generuje text `get` a `set` přístupové objekty a také soukromé pole k uložení názvu. Je podobná následující kód, který můžete ručně zadat:

```csharp
public string Name 
{ 
    get { return this._name; }
    set { this._name = value; }
}
private string _name;
```

Umožňuje provést jeden další změnu před přidáním nové funkce. `ProcessRepositories` Metoda můžete práci asynchronní a vracet kolekci úložišť. Umožňuje vrátit `List<Repository>` z této metody a přesuňte kód, který zapisuje informace do `Main` metoda.

Změnit podpis `ProcessRepositories` vrátit úlohy, jejichž výsledkem je seznam z `Repository` objekty:

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

Pak se právě vraťte úložiště po zpracování odpovědi JSON:

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

Kompilátor vygeneruje `Task<T>` objekt pro návrat, protože jste označili jako tuto metodu `async`.
Potom Pojďme upravit `Main` metoda tak to zaznamená ty výsledků a zapíše každý název úložiště do konzoly. Vaše `Main` metoda nyní vypadat třeba takto:

```csharp
public static void Main(string[] args)
{
    var repositories = ProcessRepositories().Result;

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

Přístup k `Result` vlastnosti úlohy blokuje až po dokončení úlohy. Za normálních okolností raději `await` dokončení této úlohy, jako v `ProcessRepositories` metoda, ale není povolen v `Main` metoda.

## <a name="reading-more-information"></a>Další informace pro čtení

Umožňuje to dokončit zpracováním několik dalších vlastností v paketu JSON, která se odešlou z rozhraní API Githubu. Nebudete chtít získat všechno, ale přidání několik vlastností ukážeme pár více funkcí jazyka C#.

Začněme přidáním další pár jednoduchých typů k `Repository` definici třídy. Přidejte tyto vlastnosti třídy:

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

Tyto vlastnosti mají integrované převody z typu řetězec (což je co obsahovat pakety JSON) na typ cíle. <xref:System.Uri> Typ může být pro vás nový. Reprezentuje identifikátor URI, nebo v tomto případě adresy URL. U `Uri` a `int` typy, pokud paketu JSON obsahuje data, která není převést na typ cíle, akce serializace vyvolá výjimku.

Jakmile přidáte tyto aktualizace `Main` metodu pro zobrazení tyto prvky:

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
V posledním kroku Pojďme přidat informace o poslední operace push. Tyto informace formátována tímto způsobem v odpovědi JSON:

```json
2016-02-08T21:27:00Z
```

Tento formát není postupovat podle některého z standardní .NET <xref:System.DateTime> formáty. Z tohoto důvodu budete muset napíše metoda, vlastní převod. Nezpracovaný řetězec vystavené uživatelům taky pravděpodobně nebudete chtít `Repository` třídy. Atributy může pomoct to také ovládací prvek. Nejprve definovat `private` vlastnost, která bude obsahovat řetězcovou reprezentaci času ve vaší `Repository` třídy:

```csharp
[DataMember(Name="pushed_at")]
private string JsonDate { get; set; }
```

`DataMember` Atribut informuje serializátor, měla by to být zpracována, i když není členem veřejné. Potom budete muset napsat veřejné vlastnosti jen pro čtení, která převede řetězec na platnou <xref:System.DateTime> objektu a vrátí který <xref:System.DateTime>:

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

Vraťme se přes nové konstrukce výše. `IgnoreDataMember` Atribut nastaví serializátor, že tento typ by neměly být pro čtení nebo zapisovat z libovolného objektu JSON. Tato vlastnost obsahuje pouze `get` přistupujícího objektu. Neexistuje žádné `set` přistupujícího objektu. To je, jak definovat *jen pro čtení* vlastnost v jazyce C#. (Ano, můžete vytvořit *jen pro zápis* vlastnosti v C#, ale jeho hodnota je omezená.) <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> Metoda analyzuje řetězec a vytvoří <xref:System.DateTime> objektu formátu zadané datum a přidá další metadata, aby `DateTime` pomocí `CultureInfo` objektu. Pokud se nezdaří operace analýzy, přistupující objekt vlastnosti vyvolá výjimku.

Použít <xref:System.Globalization.CultureInfo.InvariantCulture>, budete muset přidat <xref:System.Globalization> názvů `using` příkazy v `repo.cs`:

```csharp
using System.Globalization;
```

Nakonec přidejte jednu výstupní více příkaz v konzole a jste připraveni k sestavení a spuštění této aplikace znovu:

```csharp
Console.WriteLine(repo.LastPush);
```

Teď má shodovat s vaší verzí [dokončení ukázkové](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-webapiclient).
 
## <a name="conclusion"></a>Závěr

Tento kurz vám ukázal jak webové požadavky, analyzovat výsledek a zobrazit vlastnosti výsledků. Jste také přidali nové balíčky jako závislé položky ve vašem projektu. Seznámili jste některé z funkcí jazyka C#, které podporují objektově orientované techniky.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
