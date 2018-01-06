---
title: "Mikroslužeb hostované v Docker - C#"
description: "Naučte se vytvořit základní služby, které běží v kontejnerech Docker asp.net"
keywords: "Rozhraní .NET, rozhraní .NET core, Docker, C#, ASP.NET, Mikroslužbu"
author: BillWagner
ms.author: wiwagn
ms.date: 02/03/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: csharp
ms.assetid: 87e93838-a363-4813-b859-7356023d98ed
ms.openlocfilehash: d399cdce81350356b71e21d879a4f5b5079f98d8
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2018
---
# <a name="microservices-hosted-in-docker"></a>Mikroslužeb hostované v Docker

V tomto kurzu podrobnosti o úlohách, které jsou nezbytné pro vytváření a nasazení ASP.NET Core mikroslužbu v kontejner Docker. V průběhu tohoto kurzu se dozvíte:

* Jak vygenerovat aplikace ASP.NET Core pomocí Yeoman
* Postup vytvoření prostředí pro vývoj Docker
* Jak vytvořit bitovou kopii Docker na základě existující bitové kopie.
* Postup nasazení služby do kontejner Docker.

Cestou se dozvíte se taky, některé funkce jazyka C#:

* Postup převedení objektů jazyka C# do datové části JSON.
* Jak vytvořit objekty neměnné přenosu dat
* Postupy pro zpracování příchozích požadavků HTTP a vygenerování odpovědi HTTP
* Jak pracovat s typy hodnot s povolenou hodnotou Null

Můžete [zobrazení nebo stažení ukázkové aplikace](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/WeatherMicroservice) pro toto téma. Pokyny ke stažení najdete v tématu [ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

### <a name="why-docker"></a>Proč Docker?

Docker usnadňuje vytvoření bitové kopie standardní počítačů pro hostování vaší služby v datovém centru, nebo veřejný cloud. Docker umožňuje konfiguraci bitové kopie a replikaci podle potřeby škálování k instalaci vaší aplikace.

Všechny kód v tomto kurzu bude fungovat v jakémkoli prostředí .NET Core.
Další úlohy pro instalaci Docker budou fungovat v aplikaci ASP.NET Core. 

## <a name="prerequisites"></a>Požadavky
Budete potřebovat k nastavení vašeho počítače ke spuštění .NET core. Pokyny k instalaci najdete na [.NET Core](https://www.microsoft.com/net/core) stránky.
Tuto aplikaci můžete spustit v systému Windows, Ubuntu Linux, systému macOS nebo v kontejner Docker. Budete muset nainstalovat editor vaše oblíbené kódu. Popisy níže použijte [Visual Studio Code](https://code.visualstudio.com/) který je typu open source pro různé platformy editor. Můžete však použít, ať nástroje umíte pracovat s.

Také budete potřebovat k instalaci modulu Docker. Najdete v článku [Docker instalační stránka](http://www.docker.com/products/docker) pokyny pro vaši platformu.
Docker lze nainstalovat v mnoha Linuxových distribucích, systému macOS nebo systému Windows. Tato stránka výše uvedené obsahuje oddíly pro každou instalaci k dispozici.

Většina součástí k instalaci, provádí správce balíčků. Pokud máte Správce balíčků na node.js `npm` nainstalované, můžete tento krok přeskočit. V opačném případě nainstalovat nejnovější NodeJs z [nodejs.org](https://nodejs.org) který nainstaluje Správce balíčku npm. 

V tomto okamžiku musíte nainstalovat několik nástrojů příkazového řádku, které podporují ASP.NET core vývoj. Šablony příkazového řádku pomocí Yeoman, Grunt, Bower a Gulp. Pokud máte je nainstalován, které je vhodný, v opačném případě zadejte následující do své oblíbené prostředí:

`npm install -g yo bower grunt-cli gulp`

`-g` Možnost znamená, že je globální instalace, a tyto nástroje jsou k dispozici celý systém. (Místní instalace rozsahy balíčku, který má jeden projekt). Jakmile tyto základní nástroje jste nainstalovali, musíte nainstalovat generátory yeoman ASP.NET šablony:

`npm install -g generator-aspnet`

## <a name="create-the-application"></a>Vytvoření aplikace

Teď, když jste nainstalovali všechny nástroje, vytvořte novou aplikaci ASP.NET Core. Pokud chcete používat generátor příkazového řádku, spusťte následující příkaz yeoman ve své oblíbené prostředí:

`yo aspnet`

Tento příkaz zobrazí výzva k výběru jaký typ aplikace, kterou chcete vytvořit. Pro tento mikroslužbu má možné nejjednodušším, nejvíce jednoduché webové aplikace, tak vyberte 'Prázdné webové aplikace'. Šablona zobrazí výzvu k zadání názvu. Vyberte 'WeatherMicroservice'. 

Šablona pro vás vytvoří osm soubory:

* .Gitignore přizpůsobené pro aplikace ASP.NET Core.
* Soubor Startup.cs. Tato položka obsahuje základ aplikace.
* Soubor Program.cs. Tato položka obsahuje vstupní bod aplikace.
* Soubor WeatherMicroservice.csproj. Toto je soubor sestavení pro aplikaci.
* Soubor Docker. Tento skript vytvoří bitovou kopii Docker pro aplikaci.
* README.md. Tato položka obsahuje odkazy na další zdroje ASP.NET Core.
* Soubor web.config. Tato položka obsahuje informace o základní konfiguraci.
* Soubor runtimeconfig.template.json. Tato položka obsahuje ladění nastavení, které používají integrovaného vývojového prostředí.

Nyní můžete spustit aplikace vygeneruje šablony. Pomocí řady nástroje z příkazového řádku, které bylo dokončeno. `dotnet` Příkaz spustí nástroje potřebné pro .NET – vývoj. Každý příkaz spouští jiný příkaz

Prvním krokem je obnovit všechny závislosti:

```console
dotnet restore
```

Obnovení DotNet používá Správce balíčků NuGet k instalaci nezbytných balíčků do adresáře aplikace. Rovněž vygeneruje soubor project.json.lock. Tento soubor obsahuje informace o každý balíček, který se odkazuje. Po obnovení všechny závislosti, sestavte aplikaci:

```console
dotnet build
```
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

A Jakmile vytvoříte aplikaci, můžete ji spustit z příkazového řádku:

```console
dotnet run
```

Výchozí konfigurace naslouchá na http://localhost: 5000. Otevřete prohlížeč, přejděte na této stránce a najdete v části "Hello World!" Zpráva.

### <a name="anatomy-of-an-aspnet-core-application"></a>Anatomie aplikace ASP.NET Core

Teď, když jste sestavili aplikaci, podíváme, jak je implementována tato funkce. Existují dva generované soubory, které jsou v tomto okamžiku zajímavé: project.json a Startup.cs. 

Project.JSON obsahuje informace o projektu. Dva uzly, se kterými budete často pracovat jsou 'závislosti' a 'architektury'. Uzel závislosti zobrazí seznam všech balíčků, které jsou potřebné pro tuto aplikaci.
V tuto chvíli Toto je malé uzlu, kteří potřebují jenom balíčky, které spustí webový server.

Uzlu 'architektury' Určuje verze a konfigurace rozhraní .NET Framework, který se spustí tuto aplikaci.

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

### <a name="parsing-the-query-string"></a>Analýza řetězec dotazu.

Brzy analýzou řetězce dotazu. Služba bude přijímat 'lat' a 'dlouhý' argumenty na řetězec dotazu v tomto formuláři:

`http://localhost:5000/?lat=-35.55&long=-12.35`  

Všechny změny je třeba, aby se definován jako argument výraz lambda `app.Run` v třídě spuštění.

Argument na výrazu lambda je `HttpContext` pro požadavek. Jedna z vlastností je `Request` objektu. `Request` Objekt má `Query` vlastnost, která obsahuje slovník ze všech hodnot v řetězci dotazu pro daný požadavek. Pokud chcete najít hodnoty zeměpisné šířky a délky je první přidání:

[!code-csharp[ReadQueryString](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ReadQueryString "read variables from the query string")]

Hodnoty slovníku dotazu jsou `StringValue` typu. Tento typ může obsahovat kolekci řetězců. Každá hodnota služby počasí je jeden řetězec. Proto je volání `FirstOrDefault()` ve výše uvedeném kódu. 

Dále musíte převést řetězce na hodnoty Double. Je metoda, které budete používat pro řetězec převést na dvojitou `double.TryParse()`:

```csharp
bool TryParse(string s, out double result);
```

Tato metoda využívá C# výstupní parametry k označení, pokud lze vstupní řetězec převést na dvojitou hodnotu. Pokud řetězec představují znázornění platná pro datový typ double, vrátí metoda hodnotu true a `result` argument obsahuje hodnotu. Pokud řetězec nepředstavuje platný datový typ double, vrátí metoda hodnotu false.

Můžete přizpůsobit toto rozhraní API s použitím *metoda rozšíření* , který vrací *s možnou hodnotou Null dvojitou*. A *typ s možnou hodnotou Null hodnoty* je typ, který reprezentuje typ některé hodnoty a můžete také obsahovat chybějící nebo hodnota null. Typ s možnou hodnotou null je reprezentována připojením `?` znak na deklaraci typu. 

Rozšiřující metody jsou metody, které jsou definovány jako statické metody, ale přidáním `this` modifikátor na prvním parametrem nelze volat, jako kdyby jsou členy této třídy. Rozšiřující metody, může být definována pouze statické třídy. Zde je definice třídy obsahující rozšiřující metodu pro analýzu:

[!code-csharp[TryParseExtension](../../../samples/csharp/getting-started/WeatherMicroservice/Extensions.cs#TryParseExtension "try parse to a nullable")]

`default(double?)` Výraz vrátí výchozí hodnota `double?` typu. Tato výchozí hodnota je hodnota null (nebo chybějící).

Tato metoda rozšíření můžete převést na typ dvojitý argumenty řetězce dotazu:

[!code-csharp[UseTryParse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#UseTryParse "Use the try parse extension method")]

Snadno otestovat kód pro analýzu, aktualizujte odpověď na hodnoty argumenty, které zahrnují:

[!code-csharp[WriteResponse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#WriteResponse "Write the output response")]

V tomto okamžiku můžete spustit webové aplikace a zda analýzy kódu funguje. Přidání hodnoty do webové žádosti v prohlížeči a měli byste vidět aktualizované výsledky.

### <a name="build-a-random-weather-forecast"></a>Sestavení náhodných předpovědi počasí

Svůj další úkol je sestavení náhodných předpověď počasí. Začneme kontejner dat, který obsahuje hodnoty, které je vhodnější pro předpověď počasí:

```csharp
public class WeatherReport
{
    private static readonly string[] PossibleConditions = new string[]
    {
        "Sunny",
        "Mostly Sunny",
        "Partly Sunny",
        "Partly Cloudy",
        "Mostly Cloudy",
        "Rain"
    };

    public int HiTemperature { get; }
    public int LoTemperature { get; }
    public int AverageWindSpeed { get; }
    public string Conditions { get; }
}
```

V dalším kroku sestavení konstruktor, který náhodně nastaví tyto hodnoty. Tento konstruktor používá hodnoty zeměpisné šířky a délky k generátor náhodných čísel. To znamená, že předpovědi pro stejné umístění je stejný. Pokud změníte argumenty pro zeměpisnou šířku a délku, získáte různých prognózy (protože se začíná s jinou počáteční hodnoty.)

[!code-csharp[WeatherReportConstructor](../../../samples/csharp/getting-started/WeatherMicroservice/WeatherReport.cs#WeatherReportConstructor "Weather Report Constructor")]

Nyní můžete generovat prognózy 5 dní v odpovědi metodu:

[!code-csharp[GenerateRandomReport](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#GenerateRandomReport "Generate a random weather report")]

### <a name="build-the-json-response"></a>Vytvořte odpověď JSON.

Kód poslední úlohy na serveru je převést na JSON paket WeatherReport pole a odesílat to zpět do klienta. Začněme vytvořením paketu JSON. Serializátor JSON NewtonSoft přidáte do seznamu závislosti. Můžete to, že pomocí `dotnet` rozhraní příkazového řádku:

```
dotnet add package Newtonsoft.Json
```

Pak můžete použít `JsonConvert` třída pro psaní objekt na řetězec:

[!code-csharp[ConvertToJson](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ConvertToJSON "Convert objects to JSON")]

Výše uvedený kód převede objekt prognózy (seznam `WeatherForecast` objekty) do formátu JSON paketu. Po způsob konstrukce paket odpovědi, nastavíte typ obsahu na `application/json`a zápis řetězec.

Aplikace se teď spustí a vrátí náhodné prognózy.

## <a name="build-a-docker-image"></a>Vytvořit bitovou kopii Docker

Naše poslední je spuštění aplikace v nástroji Docker. Vytvoříme kontejner Docker, který spouští Docker obrázku, který představuje naší aplikace.

A ***Docker Image*** je soubor, který definuje prostředí pro spuštění aplikace.

A ***kontejner Docker*** představuje spuštěné instance Docker bitové kopie.

Obdobně, si můžete představit *Docker Image* jako *třída*a *kontejner Docker* jako objekt nebo instance této třídy.  

Soubor Docker vytvořených šablonou ASP.NET bude sloužit pro naše účely. Vraťme se přes jeho obsah.

První řádek určuje zdrojové bitové kopie:

```
FROM microsoft/dotnet:1.1-sdk-msbuild
```

Docker umožňuje nakonfigurovat bitové kopie počítače na základě šablony zdroje. Znamená, že nemáte k zadání všech parametrů počítač při spuštění, stačí zadat všechny změny. Změny tady bude zahrnovat naší aplikace.

V této ukázce první použijeme `1.1-sdk-msbuild` verze bitové kopie dotnet. Toto je nejjednodušší způsob, jak vytvořit funkční Docker prostředí. Tento image zahrnovat na dotnet core runtime a dotnet SDK. Který usnadňuje začít a sestavení, ale vytvoření bitové kopie větší.

Následujících pět řádků instalační program a sestavit aplikaci:

```
WORKDIR /app

# copy csproj and restore as distinct layers

COPY WeatherMicroservice.csproj .
RUN dotnet restore 

# copy and build everything else

COPY . .

# RUN dotnet restore
RUN dotnet publish -c Release -o out
```

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

To se zkopírovat soubor projektu z aktuálního adresáře na virtuální počítač Docker a obnovit všechny balíčky. Pomocí rozhraní příkazového řádku dotnet znamená, že Docker image musí obsahovat .NET Core SDK. Poté se zkopírují zbytek vaší aplikace a dotnet publikování příkaz sestavení a balíčky aplikace.

Poslední řádek souboru spustí aplikaci:

```
ENTRYPOINT ["dotnet", "out/WeatherMicroservice.dll", "--server.urls", "http://0.0.0.0:5000"]
```

Tento port nakonfigurovaný odkazuje `--server.urls` argument `dotnet` na posledním řádku soubor Docker. `ENTRYPOINT` Příkaz informuje Docker jaké příkaz a možnosti příkazového řádku spusťte službu. 

## <a name="building-and-running-the-image-in-a-container"></a>Vytváření a spouštění bitovou kopii v kontejneru.

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
docker run -d -p 80:5000 --name hello-docker weather-microservice
```

`-d` Možnost znamená, že spusťte kontejner odpojený od aktuální terminálu. To znamená, že neuvidíte výstupu příkazu v terminálu. `-p` Možnost označuje mapování portů mezi službou a hostitele. Zde říká, že port 5000 na kontejneru mají předávat všechny příchozí požadavek na portu 80. Pomocí 5000 odpovídá vaší služby z argumentů příkazového řádku zadaný v výše soubor Docker naslouchá na portu. `--name` Argument názvy vaší spuštěné kontejneru. Je vhodné názvem, který můžete použít pro práci s tohoto kontejneru. 

Můžete zjistit, zda bitovou kopii je spuštěn kontrolou příkaz:

```console
docker ps
```

Pokud vaše kontejneru běží, uvidíte řádek, který uvádí v spuštěných procesů. (To může být pouze).

Otevřením prohlížeče a přejdete na místního hostitele a určující zeměpisnou šířku a délku můžete otestovat služby:

```
http://localhost/?lat=35.5&long=40.75
```

## <a name="attaching-to-a-running-container"></a>Připojení ke spuštěné kontejneru

Chcete-li v příkazovém okně vaší adresářové, by mohli zobrazit diagnostické informace vytisknout pro každý požadavek. Tyto informace nevidíte, pokud je v odpojeném režimu vašeho kontejneru. Docker připojit příkaz umožňuje připojit ke kontejneru spuštěné, aby mohli zobrazit informace o protokolu.  Tento příkaz spusťte z příkazového okna:

```console
docker attach --sig-proxy=false hello-docker
```

`--sig-proxy=false` Argument znamená, že `Ctrl-C` příkazy get neodešle do procesu kontejneru, ale spíš Zastavit `docker attach` příkaz. Konečný argument je daný název kontejneru v `docker run` příkaz. 

> [!NOTE]
> Můžete taky Docker přiřazeno ID kontejneru odkazovat na žádné kontejneru. Pokud jste nezadali název vašeho kontejneru v `docker run` musíte použít id kontejneru.

Otevřete prohlížeč a přejděte do služby. Uvidíte diagnostické zprávy v systému windows příkaz z připojených spuštěné kontejneru.

Stiskněte klávesu `Ctrl-C` zastavit proces připojení.

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
