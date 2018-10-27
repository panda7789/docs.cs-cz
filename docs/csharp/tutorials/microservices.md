---
title: Mikroslužby hostované v Dockeru –C#
description: Zjistěte, jak vytvořit základní služby, které běží v kontejnerech Dockeru technologie asp.net
ms.date: 06/08/2017
ms.assetid: 87e93838-a363-4813-b859-7356023d98ed
ms.openlocfilehash: b1f7159a222ab4d68715844e9997ca922676bc80
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2018
ms.locfileid: "49454483"
---
# <a name="microservices-hosted-in-docker"></a>Mikroslužby hostované v Dockeru

Tento kurz podrobně popisuje úlohy plánování pro sestavování a nasazování mikroslužeb ASP.NET Core v kontejneru Dockeru. V průběhu tohoto kurzu se dozvíte:

* Jak vygenerovat aplikaci ASP.NET Core.
* Jak vytvořit vývojové prostředí Dockeru.
* Postup pro sestavení image Dockeru na základě existující image.
* Postup nasazení služby do kontejneru Dockeru.

Na cestě, uvidíte také některé C# funkcí jazyka:

* Jak převést C# objekty do datové části JSON.
* Postup pro sestavení neměnné datové objekty přenosu.
* Jak ke zpracování příchozích požadavků HTTP a generovat odpověď HTTP.
* Jak pracovat s typy s možnou hodnotou Null.

Je možné [zobrazení nebo stažení ukázkové aplikace](https://github.com/dotnet/samples/tree/master/csharp/getting-started/WeatherMicroservice) pro toto téma. Pokyny ke stažení najdete v tématu [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="why-docker"></a>Proč Docker?

Docker usnadňuje vytváření imagí standardní počítač pro hostování vašich služeb v datovém centru nebo veřejného cloudu. Docker umožňuje nakonfigurujte image a replikaci podle potřeby škálování instalaci vaší aplikace.

Veškerý kód v tomto kurzu bude fungovat v jakémkoli prostředí .NET Core.
Další úkoly pro instalaci Dockeru bude fungovat pro aplikace ASP.NET Core. 

## <a name="prerequisites"></a>Požadavky

Budete potřebovat k nastavení vašeho počítače ke spuštění .NET Core. Můžete najít pokyny k instalaci na [.NET Core](https://www.microsoft.com/net/core) stránky.
Tuto aplikaci můžete spustit na Windows, Linux, macOS nebo v kontejneru Dockeru.
Bude potřeba nainstalovat váš oblíbený editor kódu. Popisy níže použití [Visual Studio Code](https://code.visualstudio.com/) což je open source pro různé platformy editoru. Ale můžete použít jakýkoli nástroje jste obeznámeni.

Musíte také nainstalovat modul Docker. Zobrazit [stránky instalace Dockeru](https://docs.docker.com/install/overview/) pokyny pro vaši platformu.
Docker je možné nainstalovat v mnoha distribucí systému Linux, macOS a Windows. Na stránce výše uvedenými obsahuje oddíly pro každý z dostupné instalace.

## <a name="create-the-application"></a>Vytvoření aplikace

Teď, když si nainstalujete všechny nástroje, vytvořte novou aplikaci ASP.NET Core v adresáři s názvem "WeatherMicroservice" spuštěním následujícího příkazu v oblíbeném prostředí:

```console
dotnet new web -o WeatherMicroservice
```

`dotnet` Příkaz spustí nástroje potřebné pro vývoj na platformě .NET. Každý příkaz spouští k jinému příkazu.

`dotnet new` Příkaz slouží k vytvoření.Net Core projekty.

`-o WeatherMicroservice` Za parametr `dotnet new` příkaz slouží k zadejte umístění pro vytvoření aplikace ASP.NET Core.

Pro mikroslužby, chceme nejjednodušší a největší jednoduché webové aplikace je to možné, takže jsme použili "ASP.NET Core prázdnou" šablonu tak, že zadáte jeho krátký název `web`.

Šablona pro vás vytvoří čtyři soubory:

* Souboru Startup.cs. Tato položka obsahuje základ aplikace.
* Soubor Program.cs. Tato položka obsahuje vstupní bod aplikace.
* WeatherMicroservice.csproj souboru. Toto je soubor sestavení pro aplikaci.
* Properties/launchSettings.json souboru. Tato položka obsahuje ladění nastavení, které používají integrovaného vývojového prostředí.

Nyní můžete spustit aplikaci vygenerovanou šablonu:

```console
dotnet run
```

Tento příkaz obnoví nejprve závislosti, které vyžaduje k sestavení aplikace a potom ho sestavte aplikaci.

Výchozí konfigurace naslouchá `http://localhost:5000`. Otevřete prohlížeč, přejděte na tuto stránku a naleznete v tématu "Hello World!" zpráva.

Jakmile budete hotovi, můžete vypnout aplikaci stisknutím klávesy <kbd>Ctrl</kbd>+<kbd>C</kbd>.

### <a name="anatomy-of-an-aspnet-core-application"></a>Anatomie aplikace ASP.NET Core

Teď, když jste vytvořili aplikaci, Podívejme se na tom, jak je implementována tato funkce. Existují dva soubory, které jsou v tuto chvíli zvlášť zajímavý: WeatherMicroservice.csproj a Startup.cs. 

Soubor .csproj obsahuje informace o projektu.
Jsou dva uzly, které jsou nejzajímavější `<TargetFramework>` a `<PackageReference>`.

`<TargetFramework>` Uzlu Určuje verzi rozhraní .NET, který se spustí tuto aplikaci.

Každý `<PackageReference>` uzlu se používá k určení balíčku, který je nezbytný pro tuto aplikaci.

Aplikace je implementováno v souboru Startup.cs. Tento soubor obsahuje třídu pro spuštění.

Tyto dvě metody jsou volány ASP.NET Core infrastrukturu pro konfiguraci a spuštění aplikace. `ConfigureServices` Metody jsou popsány služby, které jsou potřebné pro tuto aplikaci. Vytváříte Štíhlá mikroslužeb, takže není nutné nakonfigurovat všechny závislosti. `Configure` Metoda nakonfiguruje obslužné rutiny pro příchozí požadavky HTTP. Tato šablona vygeneruje jednoduchou obslužnou rutinu, která bude reagovat na každou žádost s textem "Hello World!".

## <a name="build-a-microservice"></a>Vytvářet mikroslužby

Služba se chystáte vytvořit doručí doručování předpovědí počasí odkudkoli na světě. V produkční aplikace by volání některé služby se načíst data o počasí. Naše ukázka vygenerujeme náhodné předpověď počasí. 

Existuje mnoho úloh, které budete muset provést, abyste mohli implementovat naše služby náhodné weather:

* Parsovat příchozí požadavek na čtení zeměpisné šířky a délky.
* Generovat náhodná data prognózy.
* Převést tento náhodných dat prognózy z C# objekty do formátu JSON paketů.
* Nastavte hlavičku odpovědi k označení, že vaše služba odešle zpět JSON.
* Zápis odpovědi.

Následující části vás provede jednotlivé kroky.

### <a name="parsing-the-query-string"></a>Analýza řetězce dotazu

Zobrazí za přibližně analýzou řetězce dotazu. Služba bude přijímat "lat" a "dlouhý" argumenty řetězce dotazu v tomto formuláři:

```
http://localhost:5000/?lat=-35.55&long=-12.35
```

Všechny změny, je třeba, aby se ve výrazu lambda, který je definován jako argument `app.Run` ve své třídě spuštění.

Argument výrazu lambda je `HttpContext` pro daný požadavek. Jedna z jeho vlastností je `Request` objektu. `Request` Má objekt `Query` vlastnost, která obsahuje slovník ze všech hodnot v řetězci dotazu požadavku. Pokud chcete najít hodnoty zeměpisné šířky a délky je prvního přidání:

[!code-csharp[ReadQueryString](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ReadQueryString "read variables from the query string")]

`Query` Hodnoty slovníku jsou `StringValue` typu. Tento typ mohou obsahovat kolekce řetězců. Pro vaši službu počasí každá hodnota je jeden řetězec. To je důvod, proč je volání `FirstOrDefault()` ve výše uvedeném kódu. 

Dále je třeba převést řetězce čísly typu Double. Metoda použijete tak řetězec převést na typ double je `double.TryParse()`:

```csharp
bool TryParse(string s, out double result);
```

Tato metoda využívá C# výstupní parametry k označení, pokud je možné vstupní řetězec převést na hodnotu double. Pokud řetězec představuje platný reprezentaci pro typ double, metoda vrátí hodnotu true a `result` argument obsahuje hodnotu. Pokud řetězec nepředstavuje platný typ double, vrátí metoda hodnotu false.

Můžete upravit toto rozhraní API s použitím *– metoda rozšíření* , která vrací *s možnou hodnotou Null double*. A *typ s možnou hodnotou Null* je typ, který představuje typ některé hodnoty a může také obsahovat chybějící nebo hodnota null. Typ připouštějící hodnotu Null, je reprezentována přidáním `?` znakem k deklaraci typu. 

Rozšiřující metody jsou metody, které jsou definovány jako statické metody, ale tak, že přidáte `this` modifikátor první parametr, lze volat, jakoby jsou členy této třídy. Metody rozšíření lze definovat pouze ve statické třídy. Tady je definice třídy obsahující metodu rozšíření pro analýzu:

[!code-csharp[TryParseExtension](../../../samples/csharp/getting-started/WeatherMicroservice/Extensions.cs#TryParseExtension "try parse to a nullable")]

Před voláním metody rozšíření, změňte na invariantní aktuální jazykové verze:

[!code-csharp[SetCulture](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#SetCulture "set current culture to invariant")]

Tím se zajistí, že vaše aplikace analyzuje stejná čísla na libovolném serveru, bez ohledu na jeho výchozí jazykovou verzi.

Teď můžete použít metodu rozšíření můžete převést na typ double argumenty řetězce dotazu:

[!code-csharp[UseTryParse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#UseTryParse "Use the try parse extension method")]

Chcete-li snadno testujte analýzy kódu, aktualizujte odpovědi zahrnout hodnoty argumentů:

[!code-csharp[WriteResponse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#WriteResponse "Write the output response")]

V tomto okamžiku můžete spustit webové aplikace a zda je analýza kódu funguje. Přidejte hodnoty webové žádosti v prohlížeči a měli byste vidět aktualizované výsledky.

### <a name="build-a-random-weather-forecast"></a>Vytvářet náhodné předpovědí počasí

Dalším úkolem je vytvářet náhodné předpověď počasí. Začněme datový kontejner, který obsahuje hodnoty, které je vhodné pro předpověď počasí:

```csharp
public class WeatherReport
{
    private static readonly string[] PossibleConditions =
    {
        "Sunny",
        "Mostly Sunny",
        "Partly Sunny",
        "Partly Cloudy",
        "Mostly Cloudy",
        "Rain"
    };

    public int HighTemperatureFahrenheit { get; }
    public int LowTemperatureFahrenheit { get; }
    public int AverageWindSpeedMph { get; }
    public string Condition { get; }
}
```

V dalším kroku sestavení konstruktor, který náhodně nastaví tyto hodnoty. Tento konstruktor používá hodnoty pro zeměpisnou šířku a zeměpisnou délku na počáteční hodnotu `Random` generátor čísel. To znamená, že předpovědi na stejném umístění je stejný. Pokud změníte argumenty pro zeměpisnou šířku a zeměpisnou délku, získáte různých předpovědi (protože začínat různé základní hodnota).

[!code-csharp[WeatherReportConstructor](../../../samples/csharp/getting-started/WeatherMicroservice/WeatherReport.cs#WeatherReportConstructor "Weather Report Constructor")]

Teď můžete vygenerovat 5 dní předpovědi ve své metodě odpovědi:

```csharp
if (latitude.HasValue && longitude.HasValue)
{
    var forecast = new List<WeatherReport>();
    for (var days = 1; days <= 5; days++)
    {
        forecast.Add(new WeatherReport(latitude.Value, longitude.Value, days));
    }
}
```

### <a name="build-the-json-response"></a>Sestavení odpověď JSON

Konečný kód úkol na serveru je převést `WeatherReport` seznamu do dokumentu JSON a odešlete zpět do klienta. Začněme vytvořením dokumentu JSON. Serializátor Newtonsoft JSON přidáte na seznam závislostí. Můžete to udělat pomocí následujících `dotnet` příkaz:

```console
dotnet add package Newtonsoft.Json
```

Potom můžete použít `JsonConvert` třídu pro zápis na objekt na řetězec:

[!code-csharp[ConvertToJson](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ConvertToJSON "Convert objects to JSON")]

Výše uvedený kód převede objekt prognózy (seznam `WeatherForecast` objekty) do dokumentu JSON. Poté, co jste vytvořen odpověď dokumentu, nastavte typ obsahu `application/json`a zápisu řetězce.

Aplikace se teď spustí a vrátí náhodné prognózy.

## <a name="build-a-docker-image"></a>Sestavíte image Dockeru

Naše poslední úkol je ke spuštění aplikace v Dockeru. Vytvoříme kontejner Dockeru, na kterém běží image Dockeru, který představuje naši aplikaci.

A ***Image Dockeru*** je soubor, který definuje prostředí pro spuštění aplikace.

A ***kontejneru Dockeru*** představuje běžící instance Image Dockeru.

Obdobně, si můžete představit *Image Dockeru* jako *třídy*a *kontejneru Dockeru* jako objekt nebo instance této třídy.  

Následující soubor Dockerfile bude sloužit pro naše účely:

```
FROM microsoft/dotnet:2.1-sdk AS build
WORKDIR /app

# Copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# Copy everything else and build
COPY . ./
RUN dotnet publish -c Release -o out

# Build runtime image
FROM microsoft/dotnet:2.1-aspnetcore-runtime
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "WeatherMicroservice.dll"]
```

Probereme si jeho obsah.

První řádek určuje zdroj obrázku použita k sestavení aplikace:

```
FROM microsoft/dotnet:2.1-sdk AS build
```

Docker umožňuje nakonfigurovat image počítače, na základě zdroje šablony. To znamená, není nutné zadat všechny parametry počítače při spuštění, stačí zadat všechny změny. Změny zde bude zahrnovat naši aplikaci.

V této ukázce použijeme `2.1-sdk` verzi `dotnet` bitové kopie. Toto je nejjednodušší způsob, jak vytvořit pracovní prostředí Dockeru. Tato image obsahuje modul runtime .NET Core a .NET Core SDK.
Zjednodušuje tím chcete začít pracovat a sestavení, ale vytvořit větší obrázek, takže použijeme tuto image pro vytváření aplikací a jiný obrázek k jeho spuštění.

Další řádky nastavení a sestavit aplikaci:

```
WORKDIR /app

# Copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# Copy everything else and build
COPY . ./
RUN dotnet publish -c Release -o out
```

To zkopíruje soubor projektu z aktuálního adresáře na virtuální počítač Docker a obnovte všechny balíčky. Pomocí rozhraní příkazového řádku dotnet znamená, že image Dockeru musí obsahovat sadu .NET Core SDK. Potom se zkopíruje zbývající části aplikace a `dotnet
publish` příkaz sestaví a zabalí aplikaci.

Nakonec vytvoříme druhý image Dockeru, na kterém běží aplikace:

```
# Build runtime image
FROM microsoft/dotnet:2.1-aspnetcore-runtime
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "WeatherMicroservice.dll"]
```

Tuto image používá `2.1-aspnetcore-runtime` verzi `dotnet` image, která obsahuje vše potřebné ke spouštění aplikací ASP.NET Core, ale nezahrnuje .NET Core SDK. To znamená, že tento obrázek nelze použít k sestavování aplikací .NET Core, ale také umožní konečném obrazu menší.

Chcete-li tuto práci, jsme zkopírujte sestavené aplikace z první image na druhou.

`ENTRYPOINT` Příkaz informuje Docker, jaké příkazu spustí službu.

## <a name="building-and-running-the-image-in-a-container"></a>Vytváření a spouštění image v kontejneru

Pojďme vytvořit bitovou kopii a spuštění služby uvnitř kontejneru Docker. Nechcete, aby všechny soubory z místního adresáře zkopírován do bitové kopie. Místo toho budete vytvářet aplikace v kontejneru. Vytvoříte `.dockerignore` souboru k zadání adresáře, které nejsou zkopírovány do bitové kopie. Nechcete některou prostředků sestavení zkopírovat. Zadejte sestavení a publikování adresáře `.dockerignore` souboru:

```
bin/*
obj/*
out/*
```

Sestavení image pomocí `docker build` příkazu. Spusťte následující příkaz z adresáře, který obsahuje váš kód.

```console
docker build -t weather-microservice .
```

Tento příkaz sestaví image kontejneru, na základě informací o ve vašem souboru Dockerfile. `-t` Argument obsahuje značku nebo název pro tuto bitovou kopii kontejneru. Na příkazovém řádku výše, značky použité pro kontejner Dockeru se `weather-microservice`. Po dokončení tohoto příkazu máte kontejner připraven ke spuštění nové služby. 

Spusťte následující příkaz pro spuštění kontejneru a spuštění služby:

```console
docker run -d -p 80:80 --name hello-docker weather-microservice
```

`-d` Možnost znamená, že ke spuštění kontejneru odpojena od aktuální terminálu. To znamená, že neuvidíte výstupu příkazu v terminálu. `-p` Možnost označuje mapování portů mezi službou a hostitele. Tady říká, že jakékoli příchozí žádosti na portu 80 se mají předávat na port 80 v kontejneru. Pomocí 80 odpovídá portu, které vaše služba naslouchá na, což je výchozí port pro aplikace v produkčním prostředí. `--name` Argument názvy spuštěný kontejner. Je vhodné název, který můžete použít pro práci s tohoto kontejneru.

Můžete zobrazit, zda obrázek běží tak, že zkontrolujete příkazu:

```console
docker ps
```

Pokud je váš kontejner spuštěný, zobrazí se vám řádek, který obsahuje spuštěné procesy. (Může být jenom jeden.)

Otevřete prohlížeč a přejděte na místního hostitele a určující zeměpisnou šířku a délku můžete otestovat vaši službu:

```
http://localhost/?lat=35.5&long=40.75
```

## <a name="attaching-to-a-running-container"></a>Připojení ke spuštěnému kontejneru

Při spuštění služby v příkazovém okně zobrazí diagnostické informace, které jsou zobrazeny pro každý požadavek. Tyto informace nevidíte, když je váš kontejner spuštěný v režimu odpojení. Příkaz připojit Dockeru umožňuje připojení k spuštěný kontejner, kde můžete zobrazit informace protokolu.  Spuštěním tohoto příkazu z příkazového okna:

```console
docker attach --sig-proxy=false hello-docker
```

`--sig-proxy=false` Argument znamená, že <kbd>Ctrl</kbd>+<kbd>C</kbd> příkazy získat neodesílají se do kontejneru procesu, ale spíše Zastavit `docker attach` příkazu. Konečný argument je daný název kontejneru v `docker run` příkazu. 

> [!NOTE]
> Přiřazené ID kontejneru Dockeru můžete použít také k odkazování na kterýkoli kontejner. Pokud jste nezadali název kontejneru v `docker run` je nutné použít ID kontejneru.

Otevřete prohlížeč a přejděte k vaší službě. Zobrazí se vám diagnostické zprávy v okně příkazového řádku z připojených spuštěný kontejner.

Stisknutím klávesy <kbd>Ctrl</kbd>+<kbd>C</kbd> zastavte sledovací proces připojení.

Po dokončení práce s kontejneru, můžete ho zastavit:

```console
docker stop hello-docker
```

Kontejner a image je stále k dispozici pro restartování.  Pokud chcete odebrat kontejner ze svého počítače, použijte tento příkaz:

```console
docker rm hello-docker
```

Pokud chcete odebrat z počítače nepoužívané Image, použijte tento příkaz:

```console
docker rmi weather-microservice
```

## <a name="conclusion"></a>Závěr 

V tomto kurzu založená mikroslužbách ASP.NET Core a přidá několik jednoduchých funkcí.

Sestavili image kontejneru pro tuto službu Docker a spuštění kontejneru na vašem počítači. Okno terminálu připojen ke službě a viděli diagnostické zprávy z vaší služby.

Na cestě jste viděli některé funkce služby C# jazyk v akci.
