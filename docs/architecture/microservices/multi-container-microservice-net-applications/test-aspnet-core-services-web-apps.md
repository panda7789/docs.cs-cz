---
title: Testování služeb a webových aplikací ASP.NET Core
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Prozkoumejte architekturu pro testování ASP.NET Core služeb a webových aplikací v kontejnerech.
ms.date: 10/02/2018
ms.openlocfilehash: 324b71d830bca43be71e8847fe2dd1b8b1593556
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739470"
---
# <a name="testing-aspnet-core-services-and-web-apps"></a>Testování služeb a webových aplikací ASP.NET Core

Řadiče jsou centrální součástí jakékoli ASP.NET Core služby API a webové aplikace ASP.NET MVC. V takovém případě byste měli mít jistotu, že se chovají jako zamýšlená pro vaši aplikaci. Automatizované testy vám můžou poskytnout tuto jistotu a můžou odhalit chyby dřív, než dosáhnou produkčního prostředí.

Je nutné otestovat, jak se kontroler chová na základě platných nebo neplatných vstupů, a odezvy testovacího kontroléru na základě výsledku obchodní operace, kterou provádí. Nicméně byste měli mít tyto typy testů pro vaše mikroslužby:

- Testování částí. Tím zajistíte, že jednotlivé komponenty aplikace fungují podle očekávání. Kontrolní výrazy testují rozhraní API součásti.

- Integrační testy. Tím zajistíte, aby interakce komponent fungovaly podle očekávání proti externím artefaktům, jako jsou databáze. Kontrolní výrazy mohou testovat součásti rozhraní API komponenty, uživatelského rozhraní nebo vedlejší účinky akcí, jako je v/v databáze, protokolování atd.

- Funkční testy pro jednotlivé mikroslužby. Tím se zajistí, že aplikace bude v perspektivě uživatele fungovat podle očekávání.

- Testy služby. Tím se zajistí, že budou testovány kompletní případy použití služeb, včetně testování více služeb současně. Pro tento typ testování musíte nejprve připravit prostředí. V takovém případě to znamená spouštění služeb (například pomocí Docker – sestavení).

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a>Implementace testů jednotek pro ASP.NET Core webová rozhraní API

Testování částí zahrnuje testování součásti aplikace v izolaci od jejich infrastruktury a závislostí. V případě logiky testovacího kontroleru jednotek je testován pouze obsah jedné akce nebo metody, nikoli chování jeho závislostí nebo samotného rozhraní. Testy jednotek nezjišťují problémy v interakci mezi komponentami, což je účel testování integrací.

Při testování akcí kontroleru se ujistěte, že se zaměříte jenom na jejich chování. Test jednotek kontroleru se vyhne tomu, jako jsou filtry, směrování nebo vazby modelů (mapování dat požadavků na ViewModel nebo DTO). Vzhledem k tomu, že se soustředí na testování pouze jedné věci, testy jednotek jsou obecně jednoduché pro psaní a rychlé spuštění. Dobře zapsaná sada testů jednotek se může spouštět často bez nadměrné režie.

Testy jednotek jsou implementovány na základě testovacích rozhraní, jako jsou xUnit.net, MSTest, MOQ nebo NUnit. Pro ukázkovou aplikaci eShopOnContainers používáme xUnit.

Při psaní testu jednotek pro kontroler webového rozhraní API se vytvoří instance třídy Controller přímo pomocí klíčového slova New v jazyce C \#, aby se test spouštěl co nejrychleji. Následující příklad ukazuje, jak to provést při použití [xUnit](https://xunit.github.io/) jako testovacího rozhraní.

```csharp
[Fact]
public async Task Get_order_detail_success()
{
    //Arrange
    var fakeOrderId = "12";
    var fakeOrder = GetFakeOrder();

    //...

    //Act
    var orderController = new OrderController(
        _orderServiceMock.Object,
        _basketServiceMock.Object,
        _identityParserMock.Object);

    orderController.ControllerContext.HttpContext = _contextMock.Object;
    var actionResult = await orderController.Detail(fakeOrderId);

    //Assert
    var viewResult = Assert.IsType<ViewResult>(actionResult);
    Assert.IsAssignableFrom<Order>(viewResult.ViewData.Model);
}
```

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a>Implementace integračních a funkčních testů pro jednotlivé mikroslužby

Jak je uvedeno, testy integrace a funkční testy mají různé účely a cíle. Nicméně způsob implementace při testování ASP.NET Corech řadičů je podobný, takže v této části se zaměřujeme na integrační testy.

Při testování integrace je zajištěno, že komponenty aplikace budou při sestavování fungovat správně. ASP.NET Core podporuje testování integrace pomocí rozhraní pro testování částí a integrovaného testovacího webového hostitele, který lze použít pro zpracování požadavků bez režie sítě.

Na rozdíl od testování částí zahrnuje testy pro integraci často aspekty infrastruktury aplikace, jako je databáze, systém souborů, síťové prostředky nebo webové požadavky a odpovědi. Testování částí místo těchto otázek používají napodobeniny nebo napodobné objekty. Ale účelem integračních testů je potvrdit, že systém pracuje podle očekávání u těchto systémů, takže pro účely integrace při integraci nepoužíváte napodobeniny nebo objekty s přípravou. Místo toho zahrnete infrastrukturu, jako je přístup k databázi nebo vyvolání služby z jiných služeb.

Vzhledem k tomu, že integrační testy vykonávají větší segmenty kódu než testy jednotek a protože integrační testy spoléhají na prvky infrastruktury, mají za následek, že se jedná o objednávky pomaleji než testy jednotek. Proto je vhodné omezit počet testů integrace, které zapisujete a spouštíte.

ASP.NET Core obsahuje vestavěný testovací webový hostitel, který se dá použít ke zpracování požadavků HTTP bez režie sítě, což znamená, že tyto testy můžete spustit rychleji při použití reálného webového hostitele. Testovací webový hostitel (TestServer) je k dispozici v komponentě NuGet jako Microsoft. AspNetCore. TestHost. Lze ji přidat do projektů Integration Tests a použít k hostování ASP.NET Corech aplikací.

Jak vidíte v následujícím kódu, při vytváření integračních testů pro ASP.NET Core řadiče, vytváříte instance řadičů přes testovacího hostitele. To je srovnatelné s požadavkem HTTP, ale běží rychleji.

```csharp
public class PrimeWebDefaultRequestShould
{
    private readonly TestServer _server;
    private readonly HttpClient _client;

    public PrimeWebDefaultRequestShould()
    {
        // Arrange
        _server = new TestServer(new WebHostBuilder()
           .UseStartup<Startup>());
           _client = _server.CreateClient();
    }

    [Fact]
    public async Task ReturnHelloWorld()
    {
        // Act
        var response = await _client.GetAsync("/");
        response.EnsureSuccessStatusCode();
        var responseString = await response.Content.ReadAsStringAsync();
        // Assert
        Assert.Equal("Hello World!", responseString);
    }
}
```

#### <a name="additional-resources"></a>Další zdroje

- **Steve Smith. Testovací kontroléry** (ASP.NET Core) \
    [https://docs.microsoft.com/aspnet/core/mvc/controllers/testing](/aspnet/core/mvc/controllers/testing)

- **Steve Smith. Testování integrace** (ASP.NET Core) \
    [https://docs.microsoft.com/aspnet/core/test/integration-tests](/aspnet/core/test/integration-tests)

- **Testování částí v .NET Core pomocí příkazu dotnet test** \
    [https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test](../../../core/testing/unit-testing-with-dotnet-test.md)

- **xUnit.NET**. Oficiální lokalita. \
    <https://xunit.github.io/>

- **Základy testování částí.** \
    [https://docs.microsoft.com/visualstudio/test/unit-test-basics](/visualstudio/test/unit-test-basics)

- **MOQ**. Úložiště GitHub. \
    <https://github.com/moq/moq>

- **Nunit**. Oficiální lokalita. \
    <https://www.nunit.org/>

### <a name="implementing-service-tests-on-a-multi-container-application"></a>Implementace testů služby v aplikaci s více kontejnery

Jak bylo uvedeno dříve, při testování aplikací s více kontejnery musí být všechny mikroslužby spuštěny v hostiteli Docker nebo v clusteru kontejnerů. Komplexní testy služby, které zahrnují více operací, které zahrnují několik mikroslužeb, vyžadují nasazení a spuštění celé aplikace v hostiteli Docker spuštěním Docker – sestavení (nebo srovnatelného mechanismu, pokud používáte nástroj Orchestrator). Po spuštění celé aplikace a všech jejích služeb můžete provést ucelenou integraci a funkční testy.

K dispozici je několik přístupů, které můžete použít. V souboru Docker-Compose. yml, který používáte k nasazení aplikace na úrovni řešení, můžete rozšířit vstupní bod pro použití [testu dotnet](../../../core/tools/dotnet-test.md). Můžete také použít jiný soubor pro vytváření, který by spouštěl testy v imagi, na kterou cílíte. Pomocí jiného souboru pro testy integrace, který obsahuje vaše mikroslužby a databáze na kontejnerech, můžete zajistit, aby se související data při spuštění testů vždycky obnovila do původního stavu.

Jakmile je aplikace pro psaní v provozu, můžete využít zarážky a výjimky, pokud používáte sadu Visual Studio. Nebo můžete spustit testy integrace automaticky v kanálu CI v Azure DevOps Services nebo jakémkoli jiném systému CI/CD, který podporuje kontejnery Docker.

## <a name="testing-in-eshoponcontainers"></a>Testování v eShopOnContainers

Testy referenční aplikace (eShopOnContainers) se nedávno změnily a teď existují čtyři kategorie:

1. Testování **částí** , stejně jako staré staré testy jednotek, obsažené v poli **{mikroservice}. Projekty UnitTests**

2. **Testy funkčnosti nebo integrace mikroslužeb**s testovacími případy, které se týkají infrastruktury pro jednotlivé mikroslužby, ale izolované od ostatních a jsou součástí služby **{mikroslužba}. Projekty FunctionalTests**

3. **Funkce/integrační testy pro aplikace**, které se zaměřují na integraci mikroslužeb, s testovacími případy, které působí několik mikroslužeb. Tyto testy jsou umístěny v Project **Application. FunctionalTests**.

4. **Zátěžové testy**, které se zaměřují na doby odezvy pro jednotlivé mikroslužby. Tyto testy jsou umístěné v Project **LoadTest** a potřebují Visual Studio 2017 Enterprise Edition.

Test jednotek a integračních testů na mikroslužbu je obsažen v testovací složce v každé mikroslužbě a aplikaci. testy zatížení jsou obsaženy ve složce test ve složce řešení, jak je znázorněno na obrázku 6-25.

![Snímek obrazovky VS ukazující některé z testovacích projektů v řešení](./media/test-aspnet-core-services-web-apps/eshoponcontainers-test-folder-structure.png)

**Obrázek 6-25**. Struktura testovacích složek v eShopOnContainers

Testy funkcí a integrace mikroslužeb a aplikací jsou spouštěny ze sady Visual Studio pomocí rutiny regulárních testů, ale nejdřív je potřeba spustit požadované služby infrastruktury, a to pomocí sady souborů Docker pro sestavení, které jsou obsaženy ve složce test řešení. :

**Docker-Compose-test. yml**

```yml
version: '3.4'

services:
  redis.data:
    image: redis:alpine
  rabbitmq:
    image: rabbitmq:3-management-alpine
  sql.data:
    image: microsoft/mssql-server-linux:2017-latest
  nosql.data:
    image: mongo
```

**Docker-Compose-test. override. yml**

```yml
version: '3.4'

services:
  redis.data:
    ports:
      - "6379:6379"
  rabbitmq:
    ports:
      - "15672:15672"
      - "5672:5672"
  sql.data:
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
  nosql.data:
    ports:
      - "27017:27017"
```

Takže pokud chcete spustit testy funkčnosti nebo integrace, musíte nejdřív spustit tento příkaz ze složky test řešení:

```console
docker-compose -f docker-compose-test.yml -f docker-compose-test.override.yml up
```

Jak vidíte, tyto soubory Docker-skládání začínají pouze mikroslužby Redis, RabbitMQ, SQL Server a MongoDB.

### <a name="additional-resources"></a>Další zdroje

- **Testuje soubor Readme** v úložišti EShopOnContainers na GitHubu \
    <https://github.com/dotnet-architecture/eShopOnContainers/tree/dev/test>

- **Zátěžové testy souboru Readme** v úložišti EShopOnContainers na GitHubu \
    <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/test/ServicesTests/LoadTest/>

> [!div class="step-by-step"]
> [Předchozí](subscribe-events.md)
> [Další](background-tasks-with-ihostedservice.md)
