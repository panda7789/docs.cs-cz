---
title: Mikroslužeb hostované v Docker - C#
description: Naučte se vytvořit základní služby, které běží v kontejnerech Docker asp.net
ms.date: 06/08/2017
ms.assetid: 87e93838-a363-4813-b859-7356023d98ed
ms.openlocfilehash: b043b0109bcf8a67867d2c73a5ab22e43a4963cf
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208357"
---
# <a name="microservices-hosted-in-docker"></a>Mikroslužeb hostované v Docker

V tomto kurzu podrobnosti o úlohách, které jsou nezbytné pro vytváření a nasazení ASP.NET Core mikroslužbu v kontejner Docker. V průběhu tohoto kurzu se dozvíte:

* Jak vygenerovat aplikace ASP.NET Core.
* Postup vytvoření prostředí pro vývoj Docker.
* Jak vytvořit bitovou kopii Docker na základě existující bitové kopie.
* Postup nasazení služby do kontejner Docker.

Cestou se dozvíte se taky, některé funkce jazyka C#:

* Postup převedení objektů jazyka C# do datové části JSON.
* Jak sestavit neměnné datové objekty přenosu.
* Postupy pro zpracování příchozích požadavků HTTP a vygenerování odpovědi HTTP.
* Jak pracovat s typy hodnot s povolenou hodnotou Null.

Můžete [zobrazení nebo stažení ukázkové aplikace](https://github.com/dotnet/samples/tree/master/csharp/getting-started/WeatherMicroservice) pro toto téma. Pokyny ke stažení najdete v tématu [ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="why-docker"></a>Proč Docker?

Docker usnadňuje vytvoření bitové kopie standardní počítačů pro hostování vaší služby v datovém centru, nebo veřejný cloud. Docker umožňuje konfiguraci bitové kopie a replikaci podle potřeby škálování k instalaci vaší aplikace.

Všechny kód v tomto kurzu bude fungovat v jakémkoli prostředí .NET Core.
Další úlohy pro instalaci Docker budou fungovat v aplikaci ASP.NET Core. 

## <a name="prerequisites"></a>Požadavky

Budete potřebovat k nastavení vašeho počítače ke spuštění .NET Core. Pokyny k instalaci najdete na [.NET Core](https://www.microsoft.com/net/core) stránky.
Tuto aplikaci můžete spustit v systému Windows, Linux, systému macOS nebo v kontejner Docker.
Budete muset nainstalovat editor vaše oblíbené kódu. Popisy níže použijte [Visual Studio Code](https://code.visualstudio.com/) který je typu open source pro různé platformy editor. Můžete však použít, ať nástroje umíte pracovat s.

Také budete potřebovat k instalaci modulu Docker. Najdete v článku [Docker instalační stránka](http://www.docker.com/products/docker) pokyny pro vaši platformu.
Docker lze nainstalovat v mnoha Linuxových distribucích, systému macOS nebo systému Windows. Tato stránka výše uvedené obsahuje oddíly pro každou instalaci k dispozici.

## <a name="create-the-application"></a>Vytvoření aplikace

Teď, když jste nainstalovali všechny nástroje, vytvořte novou aplikaci ASP.NET Core. To lze provést, vytvořte nový adresář s názvem "WeatherMicroservice" a spusťte následující příkaz v tomto adresáři ve své oblíbené prostředí:

```console
dotnet new web
```

`dotnet` Příkaz spustí nástroje potřebné pro .NET – vývoj. Každý příkaz spouští jiný příkaz.

`dotnet new` Příkaz se používá k vytvoření .net základní projekty.

Pro tento mikroslužby chceme nejjednodušším, nejvíce jednoduché webové aplikace to možné, takže jsme použili šabloně "ASP.NET Core prázdný" zadáním jeho krátký název `web`.

Šablona pro vás vytvoří čtyři soubory:

* Soubor Startup.cs. Tato položka obsahuje základ aplikace.
* Soubor Program.cs. Tato položka obsahuje vstupní bod aplikace.
* Soubor WeatherMicroservice.csproj. Toto je soubor sestavení pro aplikaci.
* Soubor Properties/launchSettings.json. Tato položka obsahuje ladění nastavení, které používají integrovaného vývojového prostředí.

Nyní můžete spustit aplikace vygeneruje šablony:

```console
dotnet run
```

Tento příkaz obnoví nejprve závislosti požadované aplikace se sestaví a potom ho sestavte aplikaci.

Výchozí konfigurace naslouchá `http://localhost:5000`. Otevřete prohlížeč, přejděte na této stránce a najdete v části "Hello World!" Zpráva.

Když jste hotovi, můžete vypnout aplikaci stisknutím <kbd>Ctrl</kbd>+<kbd>C</kbd>.

### <a name="anatomy-of-an-aspnet-core-application"></a>Anatomie aplikace ASP.NET Core

Teď, když jste sestavili aplikaci, podíváme, jak je implementována tato funkce. Existují dva generované soubory, které jsou v tomto okamžiku zajímavé: WeatherMicroservice.csproj a Startup.cs. 

Souboru .csproj obsahuje informace o projektu.
Jsou dva uzly, které jsou nejvíce zajímavé `<TargetFramework>` a `<PackageReference>`.

`<TargetFramework>` Uzlu Určuje verzi rozhraní .NET, který se spustí tuto aplikaci.

Každý `<PackageReference>` uzlu se používá k určení balíčku, který je potřebný pro tuto aplikaci.

Aplikace je implementovaná v souboru Startup.cs. Tento soubor obsahuje třídu pro spuštění.

Tyto dvě metody jsou volány ASP.NET základní infrastruktury pro konfiguraci a spuštění aplikace. `ConfigureServices` Metoda popisuje služby, které jsou nutné pro tuto aplikaci. Kterou sestavujete štíhlého mikroslužbu, takže není nutné nakonfigurovat všechny závislosti. `Configure` Metoda konfiguruje obslužných rutin pro příchozí požadavky HTTP. Šablona generuje jednoduchá obslužná rutina, která reaguje na každou žádost s text "Hello, World!".

## <a name="build-a-microservice"></a>Sestavení mikroslužbu

Službu se chystáte vytvořit získávat zprávy o počasí odkudkoli po celém světě. V případě produkční aplikace by volání některé služby k načtení dat počasí. Pro naše ukázka budete se vygeneruje náhodné předpověď počasí. 

Existuje několik úloh, které budete muset provést kvůli implementaci naši službu náhodných počasí:

* Analyzovat příchozí požadavek na čtení zeměpisné šířky a délky.
* Generovat některé náhodná data prognózy.
* Převeďte náhodných dat prognózy z jazyka C# objektů JSON paketů.
* Nastavte hlavičku odpovědi k označení, že vaše služba odesílá zpět JSON.
* Zápis do odpovědi.

Další části vás provede procesem každý z těchto kroků.

### <a name="parsing-the-query-string"></a>Analýza řetězec dotazu

Brzy analýzou řetězce dotazu. Služba bude přijímat 'lat' a 'dlouhý' argumenty na řetězec dotazu v tomto formuláři:

```
http://localhost:5000/?lat=-35.55&long=-12.35
```

Všechny změny je třeba, aby se definován jako argument výraz lambda `app.Run` v třídě spuštění.

Argument na výrazu lambda je `HttpContext` pro požadavek. Jedna z vlastností je `Request` objektu. `Request` Objekt má `Query` vlastnost, která obsahuje slovník ze všech hodnot v řetězci dotazu pro daný požadavek. Pokud chcete najít hodnoty zeměpisné šířky a délky je první přidání:

[!code-csharp[ReadQueryString](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ReadQueryString "read variables from the query string")]

`Query` Hodnoty slovníku jsou `StringValue` typu. Tento typ může obsahovat kolekci řetězců. Každá hodnota služby počasí je jeden řetězec. Proto je volání `FirstOrDefault()` ve výše uvedeném kódu. 

Dále musíte převést řetězce na hodnoty Double. Je metoda, které budete používat pro řetězec převést na dvojitou `double.TryParse()`:

```csharp
bool TryParse(string s, out double result);
```

Tato metoda využívá C# výstupní parametry k označení, pokud lze vstupní řetězec převést na dvojitou hodnotu. Pokud řetězec představují znázornění platná pro datový typ double, vrátí metoda hodnotu true a `result` argument obsahuje hodnotu. Pokud řetězec nepředstavuje platný datový typ double, vrátí metoda hodnotu false.

Můžete přizpůsobit toto rozhraní API s použitím *metoda rozšíření* , který vrací *s možnou hodnotou Null dvojitou*. A *typ s možnou hodnotou Null hodnoty* je typ, který reprezentuje typ některé hodnoty a můžete také obsahovat chybějící nebo hodnota null. Typ s možnou hodnotou null je reprezentována připojením `?` znak na deklaraci typu. 

Rozšiřující metody jsou metody, které jsou definovány jako statické metody, ale přidáním `this` modifikátor na prvním parametrem nelze volat, jako kdyby jsou členy této třídy. Rozšiřující metody, může být definována pouze statické třídy. Zde je definice třídy obsahující rozšiřující metodu pro analýzu:

[!code-csharp[TryParseExtension](../../../samples/csharp/getting-started/WeatherMicroservice/Extensions.cs#TryParseExtension "try parse to a nullable")]

Před voláním metody rozšíření, změňte výchozí jazykové verze aktuálního:

[!code-csharp[SetCulture](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#SetCulture "set current culture to invariant")]

Tím se zajistí, že vaše aplikace analyzuje stejná čísla na libovolném serveru, bez ohledu na jeho výchozí jazykovou verzi.

Teď můžete použít metodu rozšíření převést na typ dvojitý argumenty řetězce dotazu:

[!code-csharp[UseTryParse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#UseTryParse "Use the try parse extension method")]

Snadno otestovat kód pro analýzu, aktualizujte odpověď na hodnoty argumenty, které zahrnují:

[!code-csharp[WriteResponse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#WriteResponse "Write the output response")]

V tomto okamžiku můžete spustit webové aplikace a zda analýzy kódu funguje. Přidání hodnoty do webové žádosti v prohlížeči a měli byste vidět aktualizované výsledky.

### <a name="build-a-random-weather-forecast"></a>Sestavení náhodných předpovědi počasí

Svůj další úkol je sestavení náhodných předpověď počasí. Začneme kontejner dat, který obsahuje hodnoty, které je vhodnější pro předpověď počasí:

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

V dalším kroku sestavení konstruktor, který náhodně nastaví tyto hodnoty. Tento konstruktor používá hodnoty pro zeměpisnou šířku a zeměpisnou délku na počáteční hodnoty `Random` generátoru čísel. To znamená, že předpovědi pro stejné umístění je stejný. Pokud změníte argumenty pro zeměpisnou šířku a délku, získáte různých prognózy (protože začínat různých počáteční hodnoty).

[!code-csharp[WeatherReportConstructor](../../../samples/csharp/getting-started/WeatherMicroservice/WeatherReport.cs#WeatherReportConstructor "Weather Report Constructor")]

Nyní můžete generovat prognózy 5 dní v odpovědi metodu:

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

Kód poslední úlohy na serveru je převést `WeatherReport` seznamu do dokumentu JSON a odesílání, která zpět do klienta. Začněme vytvořením dokumentu JSON. Serializátor Newtonsoft JSON přidáte do seznamu závislosti. Můžete to udělat pomocí následujících `dotnet` příkaz:

```console
dotnet add package Newtonsoft.Json
```

Pak můžete použít `JsonConvert` třída pro psaní objekt na řetězec:

[!code-csharp[ConvertToJson](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ConvertToJSON "Convert objects to JSON")]

Výše uvedený kód převede objekt prognózy (seznam `WeatherForecast` objekty) do dokumentu JSON. Po způsob konstrukce odpovědi dokument, typ obsahu, který nastavíte na `application/json`a zápis řetězec.

Aplikace se teď spustí a vrátí náhodné prognózy.

## <a name="build-a-docker-image"></a>Vytvořit bitovou kopii Docker

Naše poslední je spuštění aplikace v nástroji Docker. Vytvoříme kontejner Docker, který spouští Docker obrázku, který představuje naší aplikace.

A ***Docker Image*** je soubor, který definuje prostředí pro spuštění aplikace.

A ***kontejner Docker*** představuje spuštěné instance Docker bitové kopie.

Obdobně, si můžete představit *Docker Image* jako *třída*a *kontejner Docker* jako objekt nebo instance této třídy.  

Následující soubor Docker bude sloužit pro naše účely:

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

Vraťme se přes jeho obsah.

První řádek určuje zdrojové bitové kopie, použít pro vytvoření aplikace:

```
FROM microsoft/dotnet:2.1-sdk AS build
```

Docker umožňuje nakonfigurovat bitové kopie počítače na základě šablony zdroje. Znamená, že nemáte k zadání všech parametrů počítač při spuštění, stačí zadat všechny změny. Změny tady bude zahrnovat naší aplikace.

V této ukázce, použijeme `2.1-sdk` verzi `dotnet` bitové kopie. Toto je nejjednodušší způsob, jak vytvořit funkční Docker prostředí. Tento image obsahuje na .NET Core runtime a .NET Core SDK.
Který usnadňuje začít a sestavení, ale vytvoření bitové kopie větší, proto použijeme tuto bitovou kopii pro vytváření aplikace a jinou bitovou kopii ji spustit.

Další řádky instalační program a sestavit aplikaci:

```
WORKDIR /app

# Copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# Copy everything else and build
COPY . ./
RUN dotnet publish -c Release -o out
```

To se zkopírovat soubor projektu z aktuálního adresáře na virtuální počítač Docker a obnovit všechny balíčky. Pomocí rozhraní příkazového řádku dotnet znamená, že Docker image musí obsahovat .NET Core SDK. Potom získá zbývající aplikace zkopírovali a `dotnet
publish` příkaz vytvoří a balíčky aplikace.

Nakonec jsme vytvořit bitovou kopii druhý Docker, který spouští aplikaci:

```
# Build runtime image
FROM microsoft/dotnet:2.1-aspnetcore-runtime
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "WeatherMicroservice.dll"]
```

Používá tuto bitovou kopii `2.1-aspnetcore-runtime` verzi `dotnet` bitovou kopii, kterou obsahuje všechno potřebné ke spouštění aplikací ASP.NET Core, ale nezahrnuje .NET Core SDK. To znamená, že tento obrázek nelze použít k vytváření aplikací .NET Core, ale také umožňuje finální image menší.

Aby byla zajištěna, jsme zkopírujte integrované aplikace z první bitové kopie na druhou.

`ENTRYPOINT` Příkaz informuje Docker jaké příkazu spustí službu.

## <a name="building-and-running-the-image-in-a-container"></a>Vytváření a spouštění bitovou kopii v kontejneru

Umožňuje vytvořit bitovou kopii a spustit službu uvnitř kontejner Docker. Nechcete, aby všechny soubory z vašeho místního adresáře zkopírován do bitové kopie. Místo toho budete vytvoříte aplikaci v kontejneru. Vytvoříte `.dockerignore` souboru k zadání adresáře, které nejsou zkopírovány do bitové kopie. Nechcete, aby všechny prostředky sestavení zkopírovali. Zadejte sestavení a publikování adresářů v `.dockerignore` souboru:

```
bin/*
obj/*
out/*
```

Sestavování pomocí bitové kopie `docker build` příkaz. Spusťte následující příkaz z adresáře, která obsahuje váš kód.

```console
docker build -t weather-microservice .
```

Tento příkaz vytvoří bitovou kopii kontejneru na základě všech informací v váš soubor Docker. `-t` Argument poskytuje značka nebo název pro tuto bitovou kopii kontejneru. V příkazovém řádku výše, je použít pro kontejner Docker značky `weather-microservice`. Po dokončení tohoto příkazu máte připraven ke spuštění služby nový kontejner. 

Spusťte následující příkaz spusťte kontejner a spusťte služby:

```console
docker run -d -p 80:80 --name hello-docker weather-microservice
```

`-d` Možnost znamená, že spusťte kontejner odpojený od aktuální terminálu. To znamená, že neuvidíte výstupu příkazu v terminálu. `-p` Možnost označuje mapování portů mezi službou a hostitele. Zde říká, že port 80 na kontejneru mají předávat všechny příchozí požadavek na portu 80. Pomocí 80 odpovídá portu, které vaše služba naslouchá na, což je výchozí port pro výrobní aplikace. `--name` Argument názvy vaší spuštěné kontejneru. Je vhodné názvem, který můžete použít pro práci s tohoto kontejneru.

Můžete zjistit, zda bitovou kopii je spuštěn kontrolou příkaz:

```console
docker ps
```

Pokud vaše kontejneru běží, uvidíte řádek, který uvádí v spuštěných procesů. (To může být pouze.)

Otevřením prohlížeče a přejdete na místního hostitele a určující zeměpisnou šířku a délku můžete otestovat služby:

```
http://localhost/?lat=35.5&long=40.75
```

## <a name="attaching-to-a-running-container"></a>Připojení ke spuštěné kontejneru

Chcete-li v příkazovém okně služby, by mohli zobrazit diagnostické informace vytisknout pro každý požadavek. Tyto informace nevidíte, pokud je v odpojeném režimu vašeho kontejneru. Docker připojit příkaz umožňuje připojit ke kontejneru spuštěné, aby mohli zobrazit informace o protokolu.  Tento příkaz spusťte z příkazového okna:

```console
docker attach --sig-proxy=false hello-docker
```

`--sig-proxy=false` Argument znamená, že <kbd>Ctrl</kbd>+<kbd>C</kbd> příkazy get neodešle do procesu kontejneru, ale spíš Zastavit `docker attach` příkaz. Konečný argument je daný název kontejneru v `docker run` příkaz. 

> [!NOTE]
> Můžete taky Docker přiřazeno ID kontejneru odkazovat na žádné kontejneru. Pokud jste nezadali název vašeho kontejneru v `docker run` je nutné použít ID kontejneru.

Otevřete prohlížeč a přejděte do služby. Uvidíte diagnostické zprávy v systému windows příkaz z připojených spuštěné kontejneru.

Stiskněte klávesu <kbd>Ctrl</kbd>+<kbd>C</kbd> zastavit proces připojení.

Po dokončení práce s vaší kontejneru, můžete ho zastavit:

```console
docker stop hello-docker
```

Kontejner a bitové kopie je stále k dispozici pro restartování.  Pokud chcete odebrat kontejner z počítače, můžete pomocí následujícího příkazu:

```console
docker rm hello-docker
```

Pokud chcete odebrat nepoužité bitové kopie z počítače, můžete pomocí následujícího příkazu:

```console
docker rmi weather-microservice
```

## <a name="conclusion"></a>Závěr 

V tomto kurzu vytvořené mikroslužbu ASP.NET Core a přidat několik jednoduchých funkce.

Vytvořené Docker kontejneru bitovou kopii pro tuto službu a byl spuštěn kontejneru na váš počítač. Připojit ke službě okno terminálu a viděli diagnostické zprávy z vaší služby.

Přitom jste viděli několik funkcí jazyka C# v akci.
