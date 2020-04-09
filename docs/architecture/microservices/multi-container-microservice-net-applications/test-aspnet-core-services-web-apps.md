---
title: Testování služeb a webových aplikací ASP.NET Core
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Prozkoumejte architekturu pro testování ASP.NET základních služeb a webových aplikací v kontejnerech.
ms.date: 01/30/2020
ms.openlocfilehash: f66d6184d913405c9372904f8072dda1dbfbe6ac
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988229"
---
# <a name="testing-aspnet-core-services-and-web-apps"></a>Testování služeb a webových aplikací ASP.NET Core

Řadiče jsou centrální součástí jakékoli služby ASP.NET Core API a ASP.NET webové aplikace MVC. Jako takové byste měli mít jistotu, že se chovají tak, jak je určeno pro vaši aplikaci. Automatizované testy vám mohou poskytnout tuto jistotu a mohou zjistit chyby dříve, než se dostanou do produkčního prostředí.

Je třeba otestovat, jak se ovladač chová na základě platných nebo neplatných vstupů a testovat odpovědi řadiče na základě výsledku obchodní operace, kterou provádí. Měli byste však mít tyto typy testů pro vaše mikroslužby:

- Jednotkové testy. Ty zajišťují, že jednotlivé součásti aplikace fungují podle očekávání. Kontrolní výrazy testují rozhraní API komponenty.

- Integrační testy. Ty zajišťují, že interakce komponent fungovat podle očekávání proti externí artefakty, jako jsou databáze. Kontrolní výrazy můžete otestovat rozhraní API součásti, ui nebo vedlejší účinky akcí, jako je vstupně-v.o databáze, protokolování, atd.

- Funkční testy pro každou mikroslužbu. Ty zajišťují, že aplikace funguje podle očekávání z pohledu uživatele.

- Servisní testy. Ty zajišťují, že jsou testovány případy použití služby end-to-end, včetně testování více služeb současně. Pro tento typ testování je třeba nejprve připravit prostředí. V tomto případě to znamená spuštění služeb (například pomocí docker-compose up).

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a>Implementace testů částí pro ASP.NET základní webová rozhraní API

Testování částí zahrnuje testování části aplikace v izolaci od její infrastruktury a závislostí. Při testování logiky řadiče jednotky pouze obsah jedné akce nebo metody je testován, nikoli chování jeho závislostí nebo samotného rozhraní. Testování částí nezjišťuje problémy v interakci mezi součástmi – to je účel testování integrace.

Při testování částí akce ovladače, ujistěte se, že se zaměříte pouze na jejich chování. Testování jednotky řadiče se vyhýbá věcem, jako jsou filtry, směrování nebo vazba modelu (mapování dat požadavku na ViewModel nebo DTO). Vzhledem k tomu, že se zaměřují na testování pouze jednu věc, testování částí jsou obecně jednoduché psát a rychle spustit. Dobře napsaná sada testů částí lze spustit často bez velké režie.

Testování částí jsou implementovány na základě testovacích architektur, jako je xUnit.net, MSTest, Moq nebo NUnit. Pro ukázkovou aplikaci eShopOnContainers používáme xUnit.

Při psaní testování částí pro řadič webového rozhraní API, konstanci třídy\#řadiče přímo pomocí nové klíčové slovo v C , tak, aby test bude spuštěn co nejrychleji. Následující příklad ukazuje, jak to provést při použití [xUnit](https://xunit.github.io/) jako rozhraní Test.

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

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a>Implementace integračních a funkčních testů pro každou mikroslužbu

Jak již bylo uvedeno, integrační testy a funkční testy mají různé účely a cíle. Způsob implementace obou při testování ASP.NET řadiče Core je však podobný, takže v této části se soustředíme na integrační testy.

Testování integrace zajišťuje, že součásti aplikace fungují správně při sestavení. ASP.NET Core podporuje testování integrace pomocí rozhraní testování částí a integrovaného testovacího webového hostitele, který lze použít ke zpracování požadavků bez zatížení sítě.

Na rozdíl od testování částí testy integrace často zahrnují problémy infrastruktury aplikací, jako je například databáze, systém souborů, síťové prostředky nebo webové požadavky a odpovědi. Testy částí používají falešné nebo falešné objekty místo těchto obav. Ale účelem integračních testů je potvrdit, že systém funguje podle očekávání s těmito systémy, takže pro testování integrace nepoužíváte padělky nebo falešné objekty. Místo toho zahrnete infrastrukturu, jako je přístup k databázi nebo vyvolání služby z jiných služeb.

Vzhledem k tomu, že integrační testy vykonávají větší segmenty kódu než testy částí a protože integrační testy spoléhají na prvky infrastruktury, mají tendenci být řádově pomalejší než testy částí. Proto je vhodné omezit, kolik integračních testů napíšete a spustíte.

ASP.NET Core obsahuje vestavěný testovací webový hostitel, který lze použít ke zpracování požadavků HTTP bez zatížení sítě, což znamená, že tyto testy můžete spustit rychleji než při použití skutečného webového hostitele. Testovací webový hostitel (TestServer) je k dispozici v součásti NuGet jako Microsoft.AspNetCore.TestHost. Lze jej přidat do projektů testů integrace a použít k hostování ASP.NET základních aplikací.

Jak můžete vidět v následujícím kódu, při vytváření testů integrace pro ASP.NET řadiče Core, můžete vytvořit instanci řadiče prostřednictvím testovacího hostitele. To je srovnatelné s požadavkem HTTP, ale běží rychleji.

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

- **Steva Smithe. Testovací řadiče** (ASP.NET Core) \
    [https://docs.microsoft.com/aspnet/core/mvc/controllers/testing](/aspnet/core/mvc/controllers/testing)

- **Steva Smithe. Testování integrace** (ASP.NET jádro) \
    [https://docs.microsoft.com/aspnet/core/test/integration-tests](/aspnet/core/test/integration-tests)

- **Testování částí v rozhraní .NET Core pomocí dotnetového testu** \
    [https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test](../../../core/testing/unit-testing-with-dotnet-test.md)

- **xUnit.net**. Oficiální stránky. \
    <https://xunit.github.io/>

- **Základy testu částí.** \
    [https://docs.microsoft.com/visualstudio/test/unit-test-basics](/visualstudio/test/unit-test-basics)

- **Moq**. úložiště GitHub. \
    <https://github.com/moq/moq>

- **NUnit**. Oficiální stránky. \
    <https://www.nunit.org/>

### <a name="implementing-service-tests-on-a-multi-container-application"></a>Implementace servisních testů v aplikaci s více kontejnery

Jak již bylo uvedeno dříve, při testování aplikací s více kontejnery, všechny mikroslužby musí být spuštěnv rámci clusteru hostitele Dockeru nebo kontejneru. End-to-end testy služeb, které zahrnují více operací zahrnujících několik mikroslužeb vyžadují nasazení a spuštění celé aplikace v hostiteli Dockeru spuštěním docker-compose up (nebo srovnatelný mechanismus, pokud používáte orchestrator). Jakmile je spuštěna celá aplikace a všechny její služby, můžete provést komplexní integrační a funkční testy.

Existuje několik přístupů, které můžete použít. V souboru docker-compose.yml, který používáte k nasazení aplikace na úrovni řešení, můžete rozbalit vstupní bod a použít [test dotnet](../../../core/tools/dotnet-test.md). Můžete také použít jiný soubor compose, který by spustit testy v obrázku, který cílí. Pomocí jiného souboru compose pro integrační testy, které zahrnuje vaše mikroslužeb a databází na kontejnery, můžete se ujistit, že související data je vždy obnovit původní stav před spuštěním testů.

Jakmile je aplikace pro komponovat spuštěna, můžete využít zarážky a výjimky, pokud používáte Visual Studio. Nebo můžete spustit testy integrace automaticky v kanálu CI ve službě Azure DevOps Services nebo v jakémkoli jiném systému CI/CD, který podporuje kontejnery Dockeru.

## <a name="testing-in-eshoponcontainers"></a>Testování v eShopOnContainers

Testy referenční aplikace (eShopOnContainers) byly nedávno restrukturalizovány a nyní existují čtyři kategorie:

1. **Testy částí,** jen obyčejné staré pravidelné testy částí, obsažené v **{MicroserviceName}. Projekty UnitTests**

2. **Mikroslužby funkční/integrační testy**, s testovacích případů zahrnující infrastrukturu pro každou mikroslužbu, ale izolované od ostatních a jsou obsaženy v **{MicroserviceName}. FunctionalTests** projekty.

3. **Testy funkčnosti/integrace aplikace**, které se zaměřují na integraci mikroslužeb, s testovacích případů, které vyvíjejí několik mikroslužeb. Tyto testy jsou umístěny v projektu **Application.FunctionalTests**.

Testování jednotky a integrace na mikroslužbu jsou obsaženy v testovací složce v každé mikroslužbě a aplikace zatížení testy jsou obsaženy pod testovací složky ve složce řešení, jak je znázorněno na obrázku 6-25.

![Snímek obrazovky v VS s upozorněním na některé testovací projekty v řešení.](./media/test-aspnet-core-services-web-apps/eshoponcontainers-test-folder-structure.png)

**Obrázek 6-25**. Testování struktury složek v kontejnerech eShopOnContainers

Mikroslužby a testy funkce/integrace aplikací jsou spuštěny z visual studia pomocí pravidelné testy runner, ale nejprve je třeba spustit požadované služby infrastruktury pomocí sady docker-compose souborů obsažených ve složce test řešení:

**docker-compose-test.yml**

```yml
version: '3.4'

services:
  redis.data:
    image: redis:alpine
  rabbitmq:
    image: rabbitmq:3-management-alpine
  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest
  nosqldata:
    image: mongo
```

**docker-compose-test.override.yml**

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
  sqldata:
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
  nosqldata:
    ports:
      - "27017:27017"
```

Chcete-li spustit testy funkčnosti/integrace, musíte nejprve spustit tento příkaz ze složky testu řešení:

```console
docker-compose -f docker-compose-test.yml -f docker-compose-test.override.yml up
```

Jak můžete vidět, tyto soubory docker-compose pouze spustit Redis, RabbitMQ, SQL Server a MongoDB mikroslužeb.

### <a name="additional-resources"></a>Další zdroje

- **Testuje soubor README** na úložišti eShopOnContainers na GitHubu \
    <https://github.com/dotnet-architecture/eShopOnContainers/tree/dev/test>

- **Načtení testů souborreadme** na eShopOnContainers repo na GitHub \
    <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/test/ServicesTests/LoadTest/>

> [!div class="step-by-step"]
> [Předchozí](subscribe-events.md)
> [další](background-tasks-with-ihostedservice.md)
