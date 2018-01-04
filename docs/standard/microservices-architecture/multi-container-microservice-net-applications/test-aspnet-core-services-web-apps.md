---
title: "Testování služeb ASP.NET Core a webové aplikace"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Testování služeb ASP.NET Core a webové aplikace"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b2e9bdb08d4b1607dfea34babbe7fd14627decff
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="testing-aspnet-core-services-and-web-apps"></a>Testování služeb ASP.NET Core a webové aplikace

Řadiče jsou centrální součástí všechny služby rozhraní API ASP.NET Core a ASP.NET MVC webové aplikace. Jako takový měli byste mít přitom jistotu, že chovají se jako určený pro vaši aplikaci. Automatizované testy vám může poskytnout tento spolehlivosti a chyby může zjistit, než dosáhnou produkční.

Budete muset testování chování podle platný nebo neplatný vstupy kontroleru a testování řadiče odpovědí na základě výsledku operace firmy, které provádí. Tyto typy testů, ale musí mít vaše mikroslužeb:

-   Testování částí. Tyto Ujistěte se, že jednotlivé součásti aplikace fungovat podle očekávání. Kontrolní výrazy otestovat rozhraní API součásti.

-   Integrace testy. Tyto Ujistěte se, že interakce komponenty fungují podle očekávání proti externí artefaktů, jako jsou databáze. Kontrolní výrazy můžete otestovat součást rozhraní API, uživatelského rozhraní nebo vedlejší účinky akcí jako vstupně-výstupní operace databáze protokolování atd.

-   Funkčních testů pro každý mikroslužby. Tyto Ujistěte se, že aplikace funguje podle očekávání z pohledu uživatele.

-   Služba testy. Tyto Ujistěte se, že případy použití služby začátku do konce, včetně testování víc služeb ve stejnou dobu, jsou testovány. Pro tento typ testování musíte nejdřív připravit prostředí. V takovém případě znamená spouštění služeb (například pomocí docker tvoří nahoru).

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a>Implementuje testy částí pro rozhraní API webové jádro ASP.NET

Testování částí zahrnuje testování součástí aplikace izolovaně od jeho infrastruktury a závislosti. Když jste jednotkové testování řadiče logiku, obsah jenom jednu akci nebo metoda je testován, není chování jeho závislé součásti nebo rozhraní samotného. Testování částí Nezjišťovat problémy v interakci mezi součástmi – to znamená účelem integrace testování.

Jako jednotku můžete otestovat vaše akce kontroleru, ujistěte se, že byste se zaměřit pouze na jejich chování. Testování částí řadiče zabraňuje věcmi, jako jsou filtry, směrování nebo vazby modelu. Protože se zaměřuje na testování právě jednou z věcí, testy jednotek jsou obecně jednoduché k zápisu a rychlé spuštění. Kvalitně sadu testů jednotek se může spouštět často bez mnoho zásahů.

Testování částí se implementují podle testovací architektury, jako je xUnit.net Mstestu, Moq nebo NUnit. Pro ukázkovou aplikaci eShopOnContainers používáme XUnit.

Když píšete testů jednotek pro kontroler Web API, můžete vytvořit instanci třídy controller přímo pomocí new – klíčové slovo v jazyce C\#tak, aby se test spustí co nejrychleji. Následující příklad ukazuje, jak postupovat při použití [XUnit](https://xunit.github.io/) jako Test framework.

```csharp
[Fact]
public void Add_new_Order_raises_new_event()
{
    // Arrange
    var street = " FakeStreet ";
    var city = "FakeCity";
    // Other variables omitted for brevity ...
    // Act
    var fakeOrder = new Order(new Address(street, city, state, country, zipcode),
        cardTypeId, cardNumber,
        cardSecurityNumber, cardHolderName,
        cardExpiration);
    // Assert
    Assert.Equal(fakeOrder.DomainEvents.Count, expectedResult);
}
```

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a>Implementace integrace a funkčních testů pro každý mikroslužbu

Jak jsme uvedli, integrace testy a funkčních testů mají různé účely a cíle. Způsob, jakým implementujete i při testování řadiče ASP.NET Core je však podobný, takže v této části jsme soustředit se jenom na integraci testy.

Testování integrace zajistí, že součásti aplikace fungovat správně při sestaví. Integrace podporuje ASP.NET Core testování pomocí systémů testování částí a integrované testovací webového hostitele, který lze použít ke zpracování požadavků bez nároky na síť.

Na rozdíl od testování částí integrace testy často zahrnují aspekty infrastruktury aplikace, jako je například databáze, systém souborů, síťové prostředky, nebo webové požadavky a odpovědi. Testování částí použijte fakes nebo model objektů místo tyto problémy. Ale účelem testů integrace je potvrďte, že systém funguje podle očekávání se tyto systémy, tak pro testování integrace nemáte použít fakes nebo model objektů. Místo toho můžete zahrnout infrastruktury, jako je databáze přístupu nebo služba volání z jiné služby.

Protože integrace testy prověření větší segmenty kódu než testy jednotek a protože integrace testy využívají prvky infrastruktury, že jsou obvykle pořadí podle velikosti pomalejší než testování částí. Proto je vhodné omezit kolik integrace testy zápisu a spustit.

ASP.NET Core zahrnuje integrovanou test webové hostitele, který lze použít pro zpracování požadavků HTTP bez nároky na síť, což znamená, že můžete spustit tyto testy rychlejší při použití skutečné webového hostitele. Test webového hostitele je k dispozici v komponentě NuGet jako Microsoft.AspNetCore.TestHost. Jej lze přidat do projektů testování integrace a použít k hostiteli ASP.NET Core aplikace.

Jak můžete vidět v následujícím kódu, při vytváření integrace testy pro ASP.NET Core řadiče, vytvoří instanci řadiče prostřednictvím testovacího hostitele. Toto je porovnatelný z hlediska na požadavek HTTP, ale běží rychleji.

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

-   **Steve Smith. Testování řadiče** (ASP.NET Core) [ *https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](https://docs.microsoft.com/aspnet/core/mvc/controllers/testing)

-   **Steve Smith. Testování integrace** (ASP.NET Core) [ *https://docs.microsoft.com/aspnet/core/testing/integration-testing*](https://docs.microsoft.com/aspnet/core/testing/integration-testing)

-   **Testování v .NET Core pomocí dotnet testů částí**
    [*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test)

-   **xUnit.net**. Oficiální web.
    [*https://xunit.github.IO/*](https://xunit.github.io/)

-   **Testování částí. ** 
     [ *https://msdn.microsoft.com/en-us/library/hh694602.aspx*](https://msdn.microsoft.com/en-us/library/hh694602.aspx)

-   **Moq**. Úložiště GitHub.
    [*https://github.com/moq/moq*](https://github.com/moq/moq)

-   **NUnit**. Oficiální web.
    [*https://www.nunit.org/*](https://www.nunit.org/)

### <a name="implementing-service-tests-on-a-multi-container-application"></a>Implementace služby testy na aplikace s více kontejnerů 

Jak jsme uvedli dříve, při testování aplikace s více kontejner, musíte používat v rámci clusteru hostitele nebo kontejner Docker všechny mikroslužeb. Testy začátku do konce služby, které zahrnují více operací zahrnujících několik mikroslužeb musíte nasadit a spustit celou aplikaci na hostiteli Docker spuštěním docker-tvoří nahoru (nebo srovnatelný mechanismus, pokud používáte produktu orchestrator). Po celou aplikaci a všechny její služby běží, můžete provést integraci začátku do konce a funkčních testů.

Existuje několik přístupů, které můžete použít. V soubor docker-compose.yml, který můžete použít k nasazení aplikace (nebo podobné těm, které jsou, jako je docker compose.ci.build.yml), na úrovni řešení můžete rozšířit vstupní bod používat [dotnet testovací](https://docs.microsoft.com/dotnet/core/tools/dotnet-test). Můžete taky jiné vytvářené soubor, který by spouštění testů do bitové kopie, které se zaměříte. Pomocí jiného souboru vytvářené pro integraci testy, které zahrnuje mikroslužeb a databáze na kontejnery měli jistotu, že související data se vždy vynuluje do původního stavu před spuštěním testů.

Jakmile vytvářené aplikace spuštěná, můžete využít výhod zarážky a výjimky, pokud používáte Visual Studio. Nebo můžete spustit testy integrace automaticky v kanálu vaší konfigurace v sadě Visual Studio Team Services nebo všechny ostatní systémy CI/CD, který podporuje Docker kontejnery.

>[!div class="step-by-step"]
[Předchozí] (přihlášení k odběru events.md) [Další] (.. /microservice-ddd-cqrs-Patterns/index.MD)
