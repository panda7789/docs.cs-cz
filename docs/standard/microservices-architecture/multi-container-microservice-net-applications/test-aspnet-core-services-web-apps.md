---
title: Testování služeb ASP.NET Core a webové aplikace
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Testování služeb ASP.NET Core a webové aplikace
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 2702a273ade0e58ba93d556cfd1ecc5531027f93
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47232856"
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

Jako jednotku můžete testovat vaše akce kontroleru, ujistěte se, že se že zaměříte jenom na jejich chování. Řadič testu jednotek se vyhnete věci jako filtry, směrování nebo vazby modelu. Protože zaměřují se na testování pouze jednou z věcí, testování jednotek je obecně k zápisu snadné a rychlé spuštění. Kvalitně napsané sady testů jednotek můžete často spustit bez spojená tak velká režie.

Testování částí se implementují podle testovacích architektur, jako jsou například xUnit.net, MSTest, Moq nebo NUnit. Pro ukázkovou aplikaci aplikaci eShopOnContainers používáme xUnit.

Při psaní testů jednotek pro kontroler Web API je vytvoření instance třídy controller přímo pomocí new – klíčové slovo v jazyce C\#tak, aby se tak rychle spustí test. Následující příklad ukazuje, jak na to, jestli používáte [xUnit](https://xunit.github.io/) jako rozhraní pro testování.

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

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a>Implementace integrace a funkční testy u jednotlivých mikroslužeb

Jak je uvedeno, integrační testy a funkční testy mají různé účely a cíle. Způsob, jak implementovat při testování kontrolery ASP.NET Core je ale podobný, takže v této části budeme soustředit na integrační testy.

Testování integrace zajistí, že součásti aplikace fungovat správně při sestavena. ASP.NET Core podporuje integrační testování s využitím rozhraní testování částí a integrované testovací webového hostitele, který slouží ke zpracování požadavků bez nároky na síť.

Na rozdíl od testování jednotek testy integrace často zahrnují starostí o infrastrukturu aplikace, jako je například databáze, systém souborů, síťové prostředky, nebo webové požadavky a odpovědi. Testy jednotek použít produkt fakes nebo napodobení objekty místo tyto problémy. Ale testy integrace slouží k potvrzení, že systém funguje podle očekávání u těchto systémů, tak pro testování integrace můžete použít produkt fakes ani napodobení objekty. Místo toho vložte infrastruktury, jako jsou databáze přístupu nebo služba volání z jiné služby.

Protože testy integrace využít větší segmentů kódu než testování částí a integrační testy závisí na prvky infrastruktury, jsou často na řádově pomalejší než testování částí. Proto je vhodné omezit počet testů integrace, zápis a spouštění.

ASP.NET Core zahrnuje integrované testovací webového hostitele, který slouží ke zpracování požadavků HTTP bez nároky na síť, což znamená, že můžete spustit tyto testy rychlejší při použití skutečné webového hostitele. Hostitel webového testu je k dispozici v komponentě NuGet jako Microsoft.AspNetCore.TestHost. Lze přidat do projektů testování integrace a používané aplikace do hostitele ASP.NET Core.

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

-   **Steve Smith. Testování kontrolerů** (ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](/aspnet/core/mvc/controllers/testing)

-   **Steve Smith. Testování integrace** (ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/test/integration-tests*](/aspnet/core/test/integration-tests)

-   **Testování jednotek v .NET Core pomocí příkazu dotnet test**
    [*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](../../../core/testing/unit-testing-with-dotnet-test.md)

-   **xUnit.net**. Oficiální web.
    [*https://xunit.github.io/*](https://xunit.github.io/)

-   **Základní informace o testování částí.**
    [*https://msdn.microsoft.com/library/hh694602.aspx*](https://msdn.microsoft.com/library/hh694602.aspx)

-   **Moq**. Úložiště GitHub.
    [*https://github.com/moq/moq*](https://github.com/moq/moq)

-   **NUnit**. Oficiální web.
    [*https://www.nunit.org/*](https://www.nunit.org/)

### <a name="implementing-service-tests-on-a-multi-container-application"></a>Implementace služby testů na vícekontejnerová aplikace 

Jak je uvedeno výše, při testování vícekontejnerových aplikací, všechny mikroslužby musí běžet v rámci clusteru hostitelů nebo kontejneru Docker. Služby – koncový testů, které zahrnují více operací zahrnující několik mikroslužby vyžadují, abyste nasadit a spustit celou aplikaci v hostitele Docker pomocí docker-compose up (nebo mechanismus srovnatelné, pokud používáte orchestrator). Po celou aplikaci a její služby běží, můžete provést integraci začátku do konce a funkčních testů.

Existuje několik přístupů, které můžete použít. V souboru docker-compose.yml, můžete použít k nasazení aplikace (nebo podobnosti, jako je docker-compose.ci.build.yml) na úrovni řešení můžete rozbalit vstupním bodem k použití [příkazu dotnet test](../../../core/tools/dotnet-test.md). Můžete také použít jiný soubor compose, který by na obrázku, který se zaměřujete na spuštění testů. S použitím jiný soubor compose pro integrační testy, které zahrnují mikroslužeb a databází v kontejnerech, abyste měli jistotu, že související data se vždy obnovit do původního stavu před spuštěním testů.

Jakmile psaní aplikace je spuštěná, můžete využít výhod zarážky a výjimek, pokud používáte Visual Studio. Nebo můžete spustit testy integrace automaticky v kanálu CI v DevOps služby Azure nebo jakémkoli jiném systému CI/CD, který podporuje kontejnery Dockeru.

>[!div class="step-by-step"]
[Předchozí](subscribe-events.md)
[další](../microservice-ddd-cqrs-patterns/index.md)
