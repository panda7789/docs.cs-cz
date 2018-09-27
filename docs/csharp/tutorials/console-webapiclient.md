---
title: Vytvoření klienta REST s využitím .NET Core
description: V tomto kurzu se naučíte mnoho funkcí v jazyce C# a .NET Core.
ms.date: 03/06/2017
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 13466b717d0676c2db5edf4c98a4ead3e673b96c
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2018
ms.locfileid: "47397917"
---
# <a name="rest-client"></a>Klient REST

## <a name="introduction"></a>Úvod
V tomto kurzu se naučíte mnoho funkcí v jazyce C# a .NET Core. Získáte informace:
*   Základní informace o .NET Core rozhraní příkazového řádku (CLI).
*   Přehled funkcí jazyka C#.
*   Správa závislostí nuget
*   Komunikace protokolu HTTP
*   Informace o zpracování JSON
*   Správa konfigurace s atributy. 

Vytvoříte aplikaci, která vydává požadavků HTTP pro službu REST na Githubu. Budete číst informace ve formátu JSON a převést paketu JSON na objekty jazyka C#. Nakonec uvidíte, jak pracovat s objekty jazyka C#.

Existuje mnoho funkcí v tomto kurzu. Vytvořme je jeden po druhém.

Pokud chcete postupovat podle [konečný vzorek](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) pro toto téma, můžete ji stáhnout. Pokyny ke stažení najdete v tématu [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Požadavky
Budete muset nastavit počítač pro spuštění .NET core. Můžete najít pokyny k instalaci na [.NET Core](https://www.microsoft.com/net/core) stránky. Tuto aplikaci můžete spustit na Windows, Linux, macOS nebo v kontejneru Dockeru. Bude potřeba nainstalovat váš oblíbený editor kódu. Popisy níže použití [Visual Studio Code](https://code.visualstudio.com/), což je open source pro různé platformy editoru. Ale můžete použít jakýkoli nástroje jste obeznámeni.
## <a name="create-the-application"></a>Vytvoření aplikace
Prvním krokem je vytvoření nové aplikace. Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci. Ujistěte se, že do aktuálního adresáře. Zadejte příkaz `dotnet new console` příkazového řádku. Tím se vytvoří počáteční soubory pro základní aplikace "Hello World".

Než začnete, úpravy, Podívejme se kroky ke spuštění jednoduché aplikace Hello World. Po vytvoření aplikace, zadejte `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) na příkazovém řádku. Tento příkaz spustí proces obnovení balíčku NuGet. Správce balíčků NuGet je Správce balíčků .NET. Tento příkaz načte všechny chybějící závislosti pro váš projekt. Toto je nový projekt, závislosti nejsou v místě, tak při prvním spuštění se stáhnout .NET Core framework. Po provedení tohoto kroku počáteční je pouze potřeba spustit `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) při přidání nové závislé balíčky nebo aktualizace verze závislosti.  

Po obnovení balíčků, spustíte `dotnet build`. To spustí modul sestavení a vytvoří vaší aplikace. Nakonec spuštěním `dotnet run` ke spuštění aplikace.

## <a name="adding-new-dependencies"></a>Přidání nové závislosti
Jedním z hlavních cílů pro .NET Core je minimální velikost instalace rozhraní .NET. Pokud aplikace potřebuje další knihovny pro některé z jejích funkcí, přidejte tyto závislosti do projektu C# (\*.csproj) souboru. V našem příkladu bude potřeba přidat `System.Runtime.Serialization.Json` balíček, vaše aplikace dokáže zpracovat odpověďmi ve formátu JSON.

Otevřete váš `csproj` souboru projektu. První řádek souboru by měl vypadat jako:

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

Přidejte následující ihned po tomto řádku: 

```xml
   <ItemGroup>
      <PackageReference Include="System.Runtime.Serialization.Json" Version="4.3.0" />
   </ItemGroup> 
```
Většina editory kódu bude poskytovat dokončování pro různé verze knihoven. Obvykle budete chtít používat nejnovější verzi balíčku, který přidáte. Je důležité, abyste měli jistotu, že odpovídají verze všechny balíčky a aby splňovaly verzi rozhraní framework aplikace .NET Core.

Po provedení těchto změn, měli byste spustit `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) znovu tak, aby se balíček nainstaluje do systému.

## <a name="making-web-requests"></a>Vytváření webových požadavků
Teď jste připravení začít, načítání dat z webu. V této aplikaci, nemusíte se věnovat čtení informací z [rozhraní API Githubu](https://developer.github.com/v3/). Načteme informace o projektech v rámci [.NET Foundation](http://www.dotnetfoundation.org/) zastřešující. Začnete tím, že požadavek na rozhraní API Githubu k načtení informací o projektech. Koncový bod, který budete používat: [ https://api.github.com/orgs/dotnet/repos ](https://api.github.com/orgs/dotnet/repos). Budete chtít získat všechny informace o těchto projektů, takže budete používat požadavek HTTP GET.
Váš prohlížeč také používá HTTP GET požadavky, takže vložíte je, že adresy URL do prohlížeče informací vám bude přijímat a zpracování.

Můžete použít <xref:System.Net.Http.HttpClient> třídy k vytvoření webových požadavků. Všechny moderní rozhraní .NET API, jako jsou <xref:System.Net.Http.HttpClient> podporuje pouze asynchronní metody pro jeho dlouho běžící rozhraní API.
Začněte tím, že asynchronní metody. Implementace budete vyplňte během vytváření funkce aplikace. Začněte otevřením `program.cs` souborů v adresáři projektu a přidáním následující metodu do `Program` třídy:

```csharp
private static async Task ProcessRepositories()
{
    
}
```

Budete muset přidat `using` příkazu v horní části vaší `Main` metoda tak, aby kompilátor jazyka C# rozpozná <xref:System.Threading.Tasks.Task> typu:

```csharp
using System.Threading.Tasks;
```

V tomto okamžiku sestavení projektu získáte upozornění vygenerované pro tuto metodu, protože neobsahuje žádný `await` operátory a spustí se synchronně. Ignorovat, který teď; přidáte `await` operátory při vyplňte metodu.

V dalším kroku přejmenujte obor názvů definovaný v `namespace` příkaz z výchozí hodnoty `ConsoleApp` k `WebAPIClient`. Budeme dále definovat `repo` třídy v tomto oboru názvů.

Dále, aktualizujte `Main` metoda k volání této metody. `ProcessRepositories` Metoda vrátí úkol a by neměl ukončete program před dokončením tohoto úkolu. Proto je nutné použít `Wait` metoda blokovat a počkejte na dokončení úlohy:

```csharp
static void Main(string[] args)
{
    ProcessRepositories().Wait();
}
```

Teď máte program, který nemá žádný účinek, ale nemá asynchronně. Ho můžeme vylepšit.

Nejdřív je potřeba objekt, který je schopen načíst data z webu; můžete použít <xref:System.Net.Http.HttpClient> to udělat. Tento objekt zpracovává žádosti a odpovědi. Vytvořte instanci jedné instance daného typu v `Program` třída v souboru Program.cs.

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

 Vraťme se k `ProcessRepositories` metoda a vyplňte první verzi:

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

Musíte také přidejte dva nové příkazy using v horní části souboru pro tuto kompilace:

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

Tato první verze díky webový požadavek na čtení seznamu všechna úložiště v rámci organizace foundation dotnet. (ID Githubu pro .NET Foundation je "dotnet"). Nastavit několik prvních řádků <xref:System.Net.Http.HttpClient> pro tento požadavek. Nejprve je nakonfigurován tak, aby přijímal odpověďmi ve formátu JSON Githubu.
Tento formát je jednoduše JSON. Další řádek přidá hlavičku uživatelského agenta na všechny požadavky z tohoto objektu. Tyto dvě záhlaví jsou kontrolovány v kódu serveru Githubu a jsou nezbytné k načtení informací z Githubu.

Po dokončení konfigurace <xref:System.Net.Http.HttpClient>, provedete webové žádosti a načíst odpovědi. V této první verzi, můžete použít <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> metoda pohodlí. Tato metoda pohodlí spustí úlohu, která provádí na webový požadavek, a potom po návratu požadavek načte datový proud odpovědí a extrahuje obsah z datového proudu. Text odpovědi se vrátí jako <xref:System.String>. Řetězec je k dispozici po dokončení úlohy. 

Poslední dva řádky této metody await tento úkol a pak vytiskněte odpovědi do konzoly.
Sestavení aplikace a spustíme ji. Upozornění sestavení je pryč nyní, protože `ProcessRepositories` teď obsahují `await` operátor. Uvidíte, že se že jedná o dlouho zobrazení JSON formátovaného textu.   

## <a name="processing-the-json-result"></a>Zpracování výsledku JSON

V tomto okamžiku jste napsali kód k načtení odpověď z webového serveru a zobrazení text, který je obsažen v této odpovědi. V dalším kroku můžeme převést tuto odpověď JSON na objekty jazyka C#.

Serializátor JSON převádí JSON data na objekty jazyka C#. První úloha je definice typu třídy C# obsahuje informace, které můžete použít z této odpovědi. Vytvořme tomto pomalu, takže začínat jednoduchý typ jazyka C#, který obsahuje název úložiště:

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

Výše uvedený kód umístěte do nového souboru s názvem "repo.cs". Tato verze třídy představuje nejjednodušší způsob zpracování dat JSON. Název třídy a název člena shodovat s názvy používanými v paketu JSON, namísto následující převody C#. Opravíte to tím, že poskytuje některé atributy konfigurace později. Tato třída ukazuje další důležitou funkcí JSON serializace a deserializace: všechna pole v paketu JSON jsou součástí této třídy.
Serializátor JSON bude ignorovat informace, které není součástí typu třídy se používají.
Tato funkce usnadňuje vytváření typů, které pracují s pouze podmnožinu polí v paketu JSON.

Teď, když jste vytvořili typ, Pojďme deserializovat. Budete muset vytvořit <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> objektu. Tento objekt musíte znát očekávaný typ CLR pro paket JSON ho načte. Paket z Githubu obsahuje posloupnost úložiště, takže `List<repo>` je nesprávného typu. Přidejte následující řádek, který vaše `ProcessRepositories` metody:

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<repo>));
```

Používáte dva nové obory názvů, takže budete muset přidat ty také:

```csharp
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
```

V dalším kroku použijete serializátoru, který můžete převést JSON na objekty jazyka C#. Nahraďte volání <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> ve vašich `ProcessRepositories` metoda s následujícími dvěma řádky:

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = serializer.ReadObject(await streamTask) as List<repo>;
```

Všimněte si, že teď používáte <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> místo <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>. Serializátoru, který používá jako zdroj datového proudu namísto řetězce. Pojďme vysvětlují několik funkcí jazyka C#, která se používají v druhý řádek výše. Argument <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> je `await` výrazu. Operátor await výrazy se mohou objevit skoro kdekoli v kódu, i když až doteď jste viděli pouze jejich jako součást příkazu přiřazení.

Za druhé `as` operátor převede typ času kompilace `object` k `List<repo>`. Deklarace <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> deklaruje, že vrátí objekt typu <xref:System.Object?displayProperty=nameWithType>. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> Vrátí typ, který jste zadali při jeho vytvořený (`List<repo>` v tomto kurzu). Pokud převod selže, `as` vyhodnotí jako operátor `null`, namísto vyvolání výjimky.

Téměř dokončení této části. Teď, když jste převést JSON na objekty jazyka C#, Pojďme zobrazovaný název každého úložiště. Nahraďte řádky, které čtou:

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

následující:

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

Kompilace a spuštění aplikace. Vytiskne názvy úložišť, které jsou součástí .NET Foundation.

## <a name="controlling-serialization"></a>Řízení serializace

Předtím, než přidáte další funkce, Pojďme adres `repo` typ a nastavte ji více standard jazyka C# pro vytváření. Provedete to anotací `repo` typ s *atributy* , které řídí, jak funguje serializátor JSON. Ve vašem případě použijete tyto atributy definovat mapování mezi názvy klíčů JSON a C# názvy tříd a členů. Jsou dva atributy použité `DataContract` atribut a `DataMember` atribut. Podle konvence, všechny třídy atributu končit příponou `Attribute`. Ale není potřeba použít tuto příponu při použití atributu. 

`DataContract` a `DataMember` atributy jsou v jiné knihovny, takže budete muset přidat tuto knihovnu do souboru projektu C# jako závislost. Přidejte následující řádek, který `<ItemGroup>` část souboru projektu:

```xml
<PackageReference Include="System.Runtime.Serialization.Primitives" Version="4.3.0" />
```

Až soubor uložíte, spusťte `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) pro načtení tohoto balíčku.

Dále otevřete `repo.cs` souboru. Umožňuje změnit název Pascalcase a plně pravopisu jméno `Repository`. Chceme mapují JSON "úložiště" uzly k tomuto typu, takže budete muset přidat `DataContract` atribut deklarace třídy. Nastavíte `Name` vlastnost atributu název JSON uzly, které se mapují k tomuto typu:

```csharp
[DataContract(Name="repo")]
public class Repository
```

<xref:System.Runtime.Serialization.DataContractAttribute> Je členem skupiny <xref:System.Runtime.Serialization> obor názvů, takže budete muset přidat příslušné `using` příkazu v horní části souboru:

```csharp
using System.Runtime.Serialization;
```

Změnili jste název `repo` třídu `Repository`, takže budete muset vytvořit stejný název změnit v souboru Program.cs (Některé editory mohou podporovat refaktoring pro přejmenování, která bude tuto změnu provést automaticky:)

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<Repository>));

// ...

var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
```

V dalším kroku vytvoříme stejnou změnu s `name` pole, a to pomocí <xref:System.Runtime.Serialization.DataMemberAttribute> třídy. Proveďte následující změny k deklaraci `name` repo.cs pole:

```csharp
[DataMember(Name="name")]
public string Name;
```

Tato změna znamená, že budete muset změnit kód, který zapíše název každého úložiště v souboru program.cs:

```csharp
Console.WriteLine(repo.Name);
```

Proveďte `dotnet build` následovaný `dotnet run` k Ujistěte se, že máte mapování správné. Měli byste vidět stejný výstup jako před. Předtím, než zpracujeme více vlastností z webového serveru, vytvoříme jednu další změnu `Repository` třídy. `Name` Člen je veřejně dostupná pole. Není vhodné objektově orientované, můžeme ho změnit na vlastnost. Pro naše účely nepotřebujeme žádné konkrétní spuštění kódu při načtení nebo nastavení vlastnosti, ale změna vlastnosti usnadňuje později přidat tyto změny bez narušení veškerý kód, který se používá `Repository` třídy.

Odebrat definici pole a nahraďte ho hodnotou [automaticky implementované vlastnosti](../programming-guide/classes-and-structs/auto-implemented-properties.md):

```csharp
public string Name { get; set; }
```

Kompilátor generuje text `get` a `set` přístupové objekty, stejně jako soukromé pole pro uložení názvu. By měl vypadat přibližně následující kód, který můžete ručně zadat:

```csharp
public string Name 
{ 
    get { return this._name; }
    set { this._name = value; }
}
private string _name;
```

Vytvoříme jednu další změnu před přidáním nových funkcí. `ProcessRepositories` Metoda umí asynchronní práce a vrátí kolekci úložišť. Vraťme `List<Repository>` z této metody a přesuňte kód, který zapisuje informace do `Main` metody.

Změna podpisu `ProcessRepositories` vrátit úlohu, jehož výsledkem je seznam z `Repository` objekty:

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

Pak se jenom vrátit úložiště po zpracování odpověď JSON:

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

Kompilátor vygeneruje `Task<T>` objektu pro vrácení, protože jste označili jako tato metoda `async`.
Potom Pojďme upravit `Main` metoda tak se zaznamená ty výsledky a název každého úložiště zapisuje do konzoly. Vaše `Main` metoda nyní vypadá takto:

```csharp
public static void Main(string[] args)
{
    var repositories = ProcessRepositories().Result;

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

Přístup k `Result` vlastnost úlohy blokuje, dokud není úloha dokončena. Za normálních okolností si přejete `await` úlohy, jako v `ProcessRepositories` metody, ale to není povoleno v `Main` metody.

## <a name="reading-more-information"></a>Další informace pro čtení

Pojďme to dokončete tak, že zpracování několik dalších vlastností v JSON paket načte odeslaný z rozhraní API Githubu. Si nebudete chtít získejte všechno, ale přidává několik vlastností vám předvede několik více funkcí jazyka C#.

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

Tyto vlastnosti mají integrovanou převody z typu řetězec (což je, co obsahují pakety JSON) do cílového typu. <xref:System.Uri> Typ může být pro vás nová. Představuje identifikátor URI, nebo v tomto případě adresy URL. V případě třídy `Uri` a `int` typy, pokud je paket JSON obsahuje data, která nejde převést na cílový typ., Serializační akce vyvolá výjimku.

Jakmile přidáte tyto aktualizace `Main` metodu pro zobrazení těchto prvků:

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
V posledním kroku Pojďme přidat informace o poslední operaci push. Tyto informace je ve formátu tímto způsobem v odpovědi JSON:

```json
2016-02-08T21:27:00Z
```

Tento formát nedodržuje některé standardní .NET <xref:System.DateTime> formátů. Proto musíte napsat vlastní převod metodu. Nejspíš taky budete nechcete nezpracovaného řetězce vystavené pro uživatele `Repository` třídy. Ovládací prvek, který také může pomoct atributy. Nejprve definujte `private` vlastnost, která bude obsahovat řetězcovou reprezentaci data času ve vaší `Repository` třídy:

```csharp
[DataMember(Name="pushed_at")]
private string JsonDate { get; set; }
```

`DataMember` Atribut informuje serializátoru, který je, že to má být zpracován, i když není veřejný člen. Dále je třeba napsat veřejnou vlastnost jen pro čtení, která převede řetězec na platnou <xref:System.DateTime> objekt a vrátí ji <xref:System.DateTime>:

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

Probereme si nové konstruktory výše. `IgnoreDataMember` Atribut nastaví serializátor, že tento typ by neměly být ke čtení nebo zapisovat z libovolného objektu JSON. Tato vlastnost obsahuje pouze `get` přistupujícího objektu. Neexistuje žádná `set` přistupujícího objektu. To je, jak definovat *jen pro čtení* vlastností v jazyce C#. (Ano, můžete vytvořit *jen pro zápis* vlastností v jazyce C#, ale jejich hodnota je omezený.) <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> Metoda analyzuje řetězec a vytvoří <xref:System.DateTime> pomocí formátu zadané datum a přidá další metadata, aby `DateTime` pomocí `CultureInfo` objektu. Přistupující objekt vlastnosti vyvolá výjimku, pokud se nezdaří operace analýzy.

Použití <xref:System.Globalization.CultureInfo.InvariantCulture>, budete muset přidat <xref:System.Globalization> obor názvů, aby `using` příkazů v `repo.cs`:

```csharp
using System.Globalization;
```

Nakonec přidejte jednu výstupní více příkazu v konzole, a budete připraveni k sestavení a znovu spusťte tuto aplikaci:

```csharp
Console.WriteLine(repo.LastPush);
```

Vaše verze by měla odpovídat nyní [dokončení ukázkové](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).
 
## <a name="conclusion"></a>Závěr

Tento kurz vám ukázal vytvoření webových požadavků, výsledek analyzovat a zobrazovat vlastnosti těchto výsledků. Jste také přidali nové balíčky jako závislosti ve vašem projektu. Jste viděli některé z funkcí jazyka C# podporující objektově orientované techniky.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
