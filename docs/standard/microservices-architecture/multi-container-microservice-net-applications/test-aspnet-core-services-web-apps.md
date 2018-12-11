---
title: Testování služeb ASP.NET Core a webové aplikace
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Prozkoumejte architekturu pro účely testování služeb ASP.NET Core a webové aplikace v kontejnerech.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: 67989dc9651745ce0bd9ee9bbcbde1af0b7bc452
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148025"
---
# <a name="testing-aspnet-core-services-and-web-apps"></a>Testování služeb ASP.NET Core a webové aplikace

Kontrolery jsou klíčovou součást všem službám rozhraní API pro ASP.NET Core a ASP.NET MVC webové aplikace. V důsledku toho byste měli mít jistotu, které se chovají se tak, jak má pro vaši aplikaci. Automatizované testy vám můžou poskytnout tento spolehlivosti a dokáže detekovat chyby dřív, než dorazí produkčního prostředí.

Je potřeba otestovat, jak se chová podle platný nebo neplatný vstupy kontroler a testovací kontroler odpovědi na základě výsledku obchodní operace, které provádí. Nicméně byste měli mít tyto druhy testů pro mikroslužby:

-   Testy jednotek. Tyto Ujistěte se, že jednotlivé komponenty aplikace fungovat podle očekávání. Kontrolní výrazy otestování rozhraní API součásti.

-   Integrační testy. Tyto Ujistěte se, že součást interakce fungovat podle očekávání proti externí artefakty, jako jsou databáze. Kontrolní výrazy můžete otestovat rozhraní API součásti, uživatelského rozhraní nebo vedlejší efekty akce, jako je databáze vstupně-výstupních operací, protokolování, atd.

-   Funkční testy u jednotlivých mikroslužeb. Tyto Ujistěte se, že aplikace funguje podle očekávání z pohledu uživatele.

-   Ověřuje se služba. Tyto Ujistěte se, že jsou testovány případy použití konec konec služby, včetně testování víc služeb ve stejnou dobu. Pro tento typ testování musíte nejprve připravit prostředí. V tomto případě znamená spouštění služeb (například pomocí docker-compose up).

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a>Implementace testů částí pro rozhraní Web API ASP.NET Core

Testování částí zahrnuje testování částí aplikace v izolaci od jeho infrastrukturu a závislosti. Při testování částí je logice kontroleru, jenom obsah jedné akce nebo metoda je testována, není chování z jejich závislých nebo samotného rozhraní. Testy jednotek Nezjišťovat problémy v interakci mezi komponentami –, který je cílem testování integrace.

Jako jednotku můžete testovat vaše akce kontroleru, ujistěte se, že se že zaměříte jenom na jejich chování. Řadič testu jednotek se vyhnete věci jako filtry, směrování nebo vazby modelu (mapování dat požadavku ViewModel nebo objekt DTO). Protože zaměřují se na testování pouze jednou z věcí, testování jednotek je obecně k zápisu snadné a rychlé spuštění. Kvalitně napsané sady testů jednotek můžete často spustit bez spojená tak velká režie.

Testování částí se implementují podle testovacích architektur, jako jsou například xUnit.net, MSTest, Moq nebo NUnit. Pro ukázkovou aplikaci aplikaci eShopOnContainers používáme xUnit.

Při psaní testů jednotek pro kontroler Web API je vytvoření instance třídy controller přímo pomocí new – klíčové slovo v jazyce C\#tak, aby se tak rychle spustí test. Následující příklad ukazuje, jak na to, jestli používáte [xUnit](https://xunit.github.io/) jako rozhraní pro testování.

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

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a>Implementace integrace a funkční testy u jednotlivých mikroslužeb

Jak je uvedeno, integrační testy a funkční testy mají různé účely a cíle. Způsob, jak implementovat při testování kontrolery ASP.NET Core je ale podobný, takže v této části budeme soustředit na integrační testy.

Testování integrace zajistí, že součásti aplikace fungovat správně při sestavena. ASP.NET Core podporuje integrační testování s využitím rozhraní testování částí a integrované testovací webového hostitele, který slouží ke zpracování požadavků bez nároky na síť.

Na rozdíl od testování jednotek testy integrace často zahrnují starostí o infrastrukturu aplikace, jako je například databáze, systém souborů, síťové prostředky, nebo webové požadavky a odpovědi. Testy jednotek použít produkt fakes nebo napodobení objekty místo tyto problémy. Ale testy integrace slouží k potvrzení, že systém funguje podle očekávání u těchto systémů, tak pro testování integrace můžete použít produkt fakes ani napodobení objekty. Místo toho vložte infrastruktury, jako jsou databáze přístupu nebo služba volání z jiné služby.

Protože testy integrace využít větší segmentů kódu než testování částí a integrační testy závisí na prvky infrastruktury, jsou často na řádově pomalejší než testování částí. Proto je vhodné omezit počet testů integrace, zápis a spouštění.

ASP.NET Core zahrnuje integrované testovací webového hostitele, který slouží ke zpracování požadavků HTTP bez nároky na síť, což znamená, že můžete spustit tyto testy rychlejší při použití skutečné webového hostitele. Hostitel webového testu (TestServer) je k dispozici v komponentě NuGet jako Microsoft.AspNetCore.TestHost. Lze přidat do projektů testování integrace a používané aplikace do hostitele ASP.NET Core.

Jak je vidět v následujícím kódu, při vytváření testů integrace pro ASP.NET Core řadiče, vytvoříte instanci řadiče přes hostitele testu. Toto je srovnatelná se požadavek HTTP, ale běží rychleji.

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

-   **Steve Smith. Testování kontrolerů** (ASP.NET Core) <br/>
    [*https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](https://docs.microsoft.com/aspnet/core/mvc/controllers/testing)

-   **Steve Smith. Testování integrace** (ASP.NET Core) <br/>
    [*https://docs.microsoft.com/aspnet/core/test/integration-tests*](https://docs.microsoft.com/aspnet/core/test/integration-tests)

-   **Testování jednotek v .NET Core pomocí příkazu dotnet test** <br/>
    [*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test)

-   **xUnit.net**. Oficiální web. <br/>
    [*https://xunit.github.io/*](https://xunit.github.io/)

-   **Základní informace o testování částí.** <br/>
    [*https://msdn.microsoft.com/library/hh694602.aspx*](https://msdn.microsoft.com/library/hh694602.aspx)

-   **Moq**. Úložiště GitHub. <br/>
    [*https://github.com/moq/moq*](https://github.com/moq/moq)

-   **NUnit**. Oficiální web. <br/>
    [*https://www.nunit.org/*](https://www.nunit.org/)

### <a name="implementing-service-tests-on-a-multi-container-application"></a>Implementace služby testů na vícekontejnerová aplikace 

Jak je uvedeno výše, při testování vícekontejnerových aplikací, všechny mikroslužby musí běžet v rámci clusteru hostitelů nebo kontejneru Docker. Služby – koncový testů, které zahrnují více operací zahrnující několik mikroslužby vyžadují, abyste nasadit a spustit celou aplikaci v hostitele Docker pomocí docker-compose up (nebo mechanismus srovnatelné, pokud používáte orchestrator). Po celou aplikaci a její služby běží, můžete provést integraci začátku do konce a funkčních testů.

Existuje několik přístupů, které můžete použít. V souboru docker-compose.yml, který použijete k nasazení aplikace na úrovni řešení můžete rozbalit vstupním bodem k použití [příkazu dotnet test](https://docs.microsoft.com/dotnet/articles/core/tools/dotnet-test). Můžete také použít jiný soubor compose, který by na obrázku, který se zaměřujete na spuštění testů. S použitím jiný soubor compose pro integrační testy, které zahrnují mikroslužeb a databází v kontejnerech, abyste měli jistotu, že související data se vždy obnovit do původního stavu před spuštěním testů.

Jakmile psaní aplikace je spuštěná, můžete využít výhod zarážky a výjimek, pokud používáte Visual Studio. Nebo můžete spustit testy integrace automaticky v kanálu CI v DevOps služby Azure nebo jakémkoli jiném systému CI/CD, který podporuje kontejnery Dockeru.

## <a name="testing-in-eshoponcontainers"></a>Testování v aplikaci eShopOnContainers

Testy odkaz na aplikaci (aplikaci eShopOnContainers) byly nedávno změnili a nyní existují čtyři kategorie:

1.  **Jednotka** testy, jenom prostý staré regulární jednotkové testy, součástí **{MicroserviceName}. UnitTests** projekty

2.  **Mikroslužby funkční a integrační testy**, s testovacími případy zahrnující infrastruktura u jednotlivých mikroslužeb ale izolované od ostatních a jsou obsaženy v **{MicroserviceName}. FunctionalTests** projekty.

3.  **Testy funkčnosti/integrace aplikace**, které se zaměřují na mikroslužby integrace s testovacími případy, které získat několika mikroslužeb. Tyto testy se nacházejí v projektu **Application.FunctionalTests**.

4.  **Zátěžové testy**, které se zaměřují na dobu odezvy u jednotlivých mikroslužeb. Tyto testy se nacházejí v projektu **LoadTest** a potřebujete Visual Studio 2017 Enterprise Edition.

Test jednotky a integrace jednotlivých mikroslužbách jsou obsaženy v testovací složku v jednotlivých mikroslužeb a aplikace, které zátěžové testy jsou obsaženy v rámci foldel testu ve složce řešení, jak je znázorněno v obrázek 6 – 25.

![Struktura testů v aplikaci eShopOnContainers: Každá služba má složka "test", která zahrnuje částí a funkčních testů. Ve složce řešení "test" jsou široký funkční testy aplikace a zátěžového testu.](./media/image42.png)

**Obrázek 6 – 25**. Struktura složek testu v aplikaci eShopOnContainers

Mikroslužby a testy funkčnosti/integrace aplikace se spouštějí ze sady Visual Studio pomocí runneru pravidelné testy, ale nejdřív je potřeba spustit požadované infrastruktury služby, prostřednictvím sady docker-compose soubory obsažené v řešení testovat složky :

**docker compose test.yml**

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

**docker compose test.override.yml**

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

Tedy ke spuštění testů integrace funkcí a je třeba nejprve spustit tento příkaz ze složky řešení testu:

``` console
docker-compose -f docker-compose-test.yml -f docker-compose-test.override.yml up
```

Jak je vidět, tyto docker-compose soubory pouze start mikroslužeb Redis, RabitMQ, SQL Server a MongoDB.

### <a name="additionl-resources"></a>Additionl prostředky

-   **Soubor README testy** v aplikaci eShopOnContainers úložišti na Githubu <br/>
    [*https://github.com/dotnet-architecture/eShopOnContainers/tree/dev/test*](https://github.com/dotnet-architecture/eShopOnContainers/tree/dev/test)

-   **Soubor README testy zatížení** v aplikaci eShopOnContainers úložišti na Githubu <br/>
    [*https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/test/ServicesTests/LoadTest/*](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/test/ServicesTests/LoadTest/)

>[!div class="step-by-step"]
>[Předchozí](subscribe-events.md)
>[další](background-tasks-with-ihostedservice.md)