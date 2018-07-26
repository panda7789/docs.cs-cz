---
title: Testování služeb ASP.NET Core a webové aplikace
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Testování služeb ASP.NET Core a webové aplikace
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: f7bd75ecdd85e49524ccdf67f3e59aa4be46bdce
ms.sourcegitcommit: 702d5ffc6e733b6c4ded85bf1c92e2293638ee9a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/04/2018
ms.locfileid: "37792410"
---
# <a name="testing-aspnet-core-services-and-web-apps"></a><span data-ttu-id="876a1-103">Testování služeb ASP.NET Core a webové aplikace</span><span class="sxs-lookup"><span data-stu-id="876a1-103">Testing ASP.NET Core services and web apps</span></span>

<span data-ttu-id="876a1-104">Kontrolery jsou klíčovou součást všem službám rozhraní API pro ASP.NET Core a ASP.NET MVC webové aplikace.</span><span class="sxs-lookup"><span data-stu-id="876a1-104">Controllers are a central part of any ASP.NET Core API service and ASP.NET MVC Web application.</span></span> <span data-ttu-id="876a1-105">V důsledku toho byste měli mít jistotu, které se chovají se tak, jak má pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="876a1-105">As such, you should have confidence they behave as intended for your application.</span></span> <span data-ttu-id="876a1-106">Automatizované testy vám můžou poskytnout tento spolehlivosti a dokáže detekovat chyby dřív, než dorazí produkčního prostředí.</span><span class="sxs-lookup"><span data-stu-id="876a1-106">Automated tests can provide you with this confidence and can detect errors before they reach production.</span></span>

<span data-ttu-id="876a1-107">Je potřeba otestovat, jak se chová podle platný nebo neplatný vstupy kontroler a testovací kontroler odpovědi na základě výsledku obchodní operace, které provádí.</span><span class="sxs-lookup"><span data-stu-id="876a1-107">You need to test how the controller behaves based on valid or invalid inputs, and test controller responses based on the result of the business operation it performs.</span></span> <span data-ttu-id="876a1-108">Nicméně byste měli mít tyto druhy testů mikroslužby:</span><span class="sxs-lookup"><span data-stu-id="876a1-108">However, you should have these types of tests your microservices:</span></span>

-   <span data-ttu-id="876a1-109">Testy jednotek.</span><span class="sxs-lookup"><span data-stu-id="876a1-109">Unit tests.</span></span> <span data-ttu-id="876a1-110">Tyto Ujistěte se, že jednotlivé komponenty aplikace fungovat podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="876a1-110">These ensure that individual components of the application work as expected.</span></span> <span data-ttu-id="876a1-111">Kontrolní výrazy otestování rozhraní API součásti.</span><span class="sxs-lookup"><span data-stu-id="876a1-111">Assertions test the component API.</span></span>

-   <span data-ttu-id="876a1-112">Integrační testy.</span><span class="sxs-lookup"><span data-stu-id="876a1-112">Integration tests.</span></span> <span data-ttu-id="876a1-113">Tyto Ujistěte se, že součást interakce fungovat podle očekávání proti externí artefakty, jako jsou databáze.</span><span class="sxs-lookup"><span data-stu-id="876a1-113">These ensure that component interactions work as expected against external artifacts like databases.</span></span> <span data-ttu-id="876a1-114">Kontrolní výrazy můžete otestovat rozhraní API součásti, uživatelského rozhraní nebo vedlejší efekty akce, jako je databáze vstupně-výstupních operací, protokolování, atd.</span><span class="sxs-lookup"><span data-stu-id="876a1-114">Assertions can test component API, UI, or the side effects of actions like database I/O, logging, etc.</span></span>

-   <span data-ttu-id="876a1-115">Funkční testy u jednotlivých mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="876a1-115">Functional tests for each microservice.</span></span> <span data-ttu-id="876a1-116">Tyto Ujistěte se, že aplikace funguje podle očekávání z pohledu uživatele.</span><span class="sxs-lookup"><span data-stu-id="876a1-116">These ensure that the application works as expected from the user’s perspective.</span></span>

-   <span data-ttu-id="876a1-117">Ověřuje se služba.</span><span class="sxs-lookup"><span data-stu-id="876a1-117">Service tests.</span></span> <span data-ttu-id="876a1-118">Tyto Ujistěte se, že jsou testovány případy použití konec konec služby, včetně testování víc služeb ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="876a1-118">These ensure that end-to-end service use cases, including testing multiple services at the same time, are tested.</span></span> <span data-ttu-id="876a1-119">Pro tento typ testování musíte nejprve připravit prostředí.</span><span class="sxs-lookup"><span data-stu-id="876a1-119">For this type of testing, you need to prepare the environment first.</span></span> <span data-ttu-id="876a1-120">V tomto případě znamená spouštění služeb (například pomocí docker-compose up).</span><span class="sxs-lookup"><span data-stu-id="876a1-120">In this case, it means starting the services (for example, by using docker-compose up).</span></span>

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a><span data-ttu-id="876a1-121">Implementace testů částí pro rozhraní Web API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="876a1-121">Implementing unit tests for ASP.NET Core Web APIs</span></span>

<span data-ttu-id="876a1-122">Testování částí zahrnuje testování částí aplikace v izolaci od jeho infrastrukturu a závislosti.</span><span class="sxs-lookup"><span data-stu-id="876a1-122">Unit testing involves testing a part of an application in isolation from its infrastructure and dependencies.</span></span> <span data-ttu-id="876a1-123">Při testování částí je logice kontroleru, jenom obsah jedné akce nebo metoda je testována, není chování z jejich závislých nebo samotného rozhraní.</span><span class="sxs-lookup"><span data-stu-id="876a1-123">When you unit test controller logic, only the content of a single action or method is tested, not the behavior of its dependencies or of the framework itself.</span></span> <span data-ttu-id="876a1-124">Testy jednotek Nezjišťovat problémy v interakci mezi komponentami –, který je cílem testování integrace.</span><span class="sxs-lookup"><span data-stu-id="876a1-124">Unit tests do not detect issues in the interaction between components—that is the purpose of integration testing.</span></span>

<span data-ttu-id="876a1-125">Jako jednotku můžete testovat vaše akce kontroleru, ujistěte se, že se že zaměříte jenom na jejich chování.</span><span class="sxs-lookup"><span data-stu-id="876a1-125">As you unit test your controller actions, make sure you focus only on their behavior.</span></span> <span data-ttu-id="876a1-126">Řadič testu jednotek se vyhnete věci jako filtry, směrování nebo vazby modelu.</span><span class="sxs-lookup"><span data-stu-id="876a1-126">A controller unit test avoids things like filters, routing, or model binding.</span></span> <span data-ttu-id="876a1-127">Protože zaměřují se na testování pouze jednou z věcí, testování jednotek je obecně k zápisu snadné a rychlé spuštění.</span><span class="sxs-lookup"><span data-stu-id="876a1-127">Because they focus on testing just one thing, unit tests are generally simple to write and quick to run.</span></span> <span data-ttu-id="876a1-128">Kvalitně napsané sady testů jednotek můžete často spustit bez spojená tak velká režie.</span><span class="sxs-lookup"><span data-stu-id="876a1-128">A well-written set of unit tests can be run frequently without much overhead.</span></span>

<span data-ttu-id="876a1-129">Testování částí se implementují podle testovacích architektur, jako jsou například xUnit.net, MSTest, Moq nebo NUnit.</span><span class="sxs-lookup"><span data-stu-id="876a1-129">Unit tests are implemented based on test frameworks like xUnit.net, MSTest, Moq, or NUnit.</span></span> <span data-ttu-id="876a1-130">Pro ukázkovou aplikaci aplikaci eShopOnContainers používáme XUnit.</span><span class="sxs-lookup"><span data-stu-id="876a1-130">For the eShopOnContainers sample application, we are using XUnit.</span></span>

<span data-ttu-id="876a1-131">Při psaní testů jednotek pro kontroler Web API je vytvoření instance třídy controller přímo pomocí new – klíčové slovo v jazyce C\#tak, aby se tak rychle spustí test.</span><span class="sxs-lookup"><span data-stu-id="876a1-131">When you write a unit test for a Web API controller, you instantiate the controller class directly using the new keyword in C\#, so that the test will run as fast as possible.</span></span> <span data-ttu-id="876a1-132">Následující příklad ukazuje, jak na to, jestli používáte [XUnit](https://xunit.github.io/) jako rozhraní pro testování.</span><span class="sxs-lookup"><span data-stu-id="876a1-132">The following example shows how to do this when using [XUnit](https://xunit.github.io/) as the Test framework.</span></span>

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

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a><span data-ttu-id="876a1-133">Implementace integrace a funkční testy u jednotlivých mikroslužeb</span><span class="sxs-lookup"><span data-stu-id="876a1-133">Implementing integration and functional tests for each microservice</span></span>

<span data-ttu-id="876a1-134">Jak je uvedeno, integrační testy a funkční testy mají různé účely a cíle.</span><span class="sxs-lookup"><span data-stu-id="876a1-134">As noted, integration tests and functional tests have different purposes and goals.</span></span> <span data-ttu-id="876a1-135">Způsob, jak implementovat při testování kontrolery ASP.NET Core je ale podobný, takže v této části budeme soustředit na integrační testy.</span><span class="sxs-lookup"><span data-stu-id="876a1-135">However, the way you implement both when testing ASP.NET Core controllers is similar, so in this section we concentrate on integration tests.</span></span>

<span data-ttu-id="876a1-136">Testování integrace zajistí, že součásti aplikace fungovat správně při sestavena.</span><span class="sxs-lookup"><span data-stu-id="876a1-136">Integration testing ensures that an application's components function correctly when assembled.</span></span> <span data-ttu-id="876a1-137">ASP.NET Core podporuje integrační testování s využitím rozhraní testování částí a integrované testovací webového hostitele, který slouží ke zpracování požadavků bez nároky na síť.</span><span class="sxs-lookup"><span data-stu-id="876a1-137">ASP.NET Core supports integration testing using unit test frameworks and a built-in test web host that can be used to handle requests without network overhead.</span></span>

<span data-ttu-id="876a1-138">Na rozdíl od testování jednotek testy integrace často zahrnují starostí o infrastrukturu aplikace, jako je například databáze, systém souborů, síťové prostředky, nebo webové požadavky a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="876a1-138">Unlike unit testing, integration tests frequently involve application infrastructure concerns, such as a database, file system, network resources, or web requests and responses.</span></span> <span data-ttu-id="876a1-139">Testy jednotek použít produkt fakes nebo napodobení objekty místo tyto problémy.</span><span class="sxs-lookup"><span data-stu-id="876a1-139">Unit tests use fakes or mock objects in place of these concerns.</span></span> <span data-ttu-id="876a1-140">Ale testy integrace slouží k potvrzení, že systém funguje podle očekávání u těchto systémů, tak pro testování integrace můžete použít produkt fakes ani napodobení objekty.</span><span class="sxs-lookup"><span data-stu-id="876a1-140">But the purpose of integration tests is to confirm that the system works as expected with these systems, so for integration testing you do not use fakes or mock objects.</span></span> <span data-ttu-id="876a1-141">Místo toho vložte infrastruktury, jako jsou databáze přístupu nebo služba volání z jiné služby.</span><span class="sxs-lookup"><span data-stu-id="876a1-141">Instead, you include the infrastructure, like database access or service invocation from other services.</span></span>

<span data-ttu-id="876a1-142">Protože testy integrace využít větší segmentů kódu než testování částí a integrační testy závisí na prvky infrastruktury, jsou často na řádově pomalejší než testování částí.</span><span class="sxs-lookup"><span data-stu-id="876a1-142">Because integration tests exercise larger segments of code than unit tests, and because integration tests rely on infrastructure elements, they tend to be orders of magnitude slower than unit tests.</span></span> <span data-ttu-id="876a1-143">Proto je vhodné omezit počet testů integrace, zápis a spouštění.</span><span class="sxs-lookup"><span data-stu-id="876a1-143">Thus, it is a good idea to limit how many integration tests you write and run.</span></span>

<span data-ttu-id="876a1-144">ASP.NET Core zahrnuje integrované testovací webového hostitele, který slouží ke zpracování požadavků HTTP bez nároky na síť, což znamená, že můžete spustit tyto testy rychlejší při použití skutečné webového hostitele.</span><span class="sxs-lookup"><span data-stu-id="876a1-144">ASP.NET Core includes a built-in test web host that can be used to handle HTTP requests without network overhead, meaning that you can run those tests faster when using a real web host.</span></span> <span data-ttu-id="876a1-145">Hostitel webového testu je k dispozici v komponentě NuGet jako Microsoft.AspNetCore.TestHost.</span><span class="sxs-lookup"><span data-stu-id="876a1-145">The test web host is available in a NuGet component as Microsoft.AspNetCore.TestHost.</span></span> <span data-ttu-id="876a1-146">Lze přidat do projektů testování integrace a používané aplikace do hostitele ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="876a1-146">It can be added to integration test projects and used to host ASP.NET Core applications.</span></span>

<span data-ttu-id="876a1-147">Jak je vidět v následujícím kódu, při vytváření testů integrace pro ASP.NET Core řadiče, vytvoříte instanci řadiče přes hostitele testu.</span><span class="sxs-lookup"><span data-stu-id="876a1-147">As you can see in the following code, when you create integration tests for ASP.NET Core controllers, you instantiate the controllers through the test host.</span></span> <span data-ttu-id="876a1-148">Toto je srovnatelná se požadavek HTTP, ale běží rychleji.</span><span class="sxs-lookup"><span data-stu-id="876a1-148">This is comparable to an HTTP request, but it runs faster.</span></span>

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

#### <a name="additional-resources"></a><span data-ttu-id="876a1-149">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="876a1-149">Additional resources</span></span>

-   <span data-ttu-id="876a1-150">**Steve Smith. Testování kontrolerů** (ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](/aspnet/core/mvc/controllers/testing)</span><span class="sxs-lookup"><span data-stu-id="876a1-150">**Steve Smith. Testing controllers** (ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](/aspnet/core/mvc/controllers/testing)</span></span>

-   <span data-ttu-id="876a1-151">**Steve Smith. Testování integrace** (ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/test/integration-tests*](/aspnet/core/test/integration-tests)</span><span class="sxs-lookup"><span data-stu-id="876a1-151">**Steve Smith. Integration testing** (ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/test/integration-tests*](/aspnet/core/test/integration-tests)</span></span>

-   <span data-ttu-id="876a1-152">**Testování jednotek v .NET Core pomocí příkazu dotnet test**
    [*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](../../../core/testing/unit-testing-with-dotnet-test.md)</span><span class="sxs-lookup"><span data-stu-id="876a1-152">**Unit testing in .NET Core using dotnet test**
[*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](../../../core/testing/unit-testing-with-dotnet-test.md)</span></span>

-   <span data-ttu-id="876a1-153">**xUnit.net**.</span><span class="sxs-lookup"><span data-stu-id="876a1-153">**xUnit.net**.</span></span> <span data-ttu-id="876a1-154">Oficiální web.</span><span class="sxs-lookup"><span data-stu-id="876a1-154">Official site.</span></span>
    [*https://xunit.github.io/*](https://xunit.github.io/)

-   <span data-ttu-id="876a1-155">**Základní informace o testování částí.**
    [*https://msdn.microsoft.com/library/hh694602.aspx*](https://msdn.microsoft.com/library/hh694602.aspx)</span><span class="sxs-lookup"><span data-stu-id="876a1-155">**Unit Test Basics.**
[*https://msdn.microsoft.com/library/hh694602.aspx*](https://msdn.microsoft.com/library/hh694602.aspx)</span></span>

-   <span data-ttu-id="876a1-156">**Moq**.</span><span class="sxs-lookup"><span data-stu-id="876a1-156">**Moq**.</span></span> <span data-ttu-id="876a1-157">Úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="876a1-157">GitHub repo.</span></span>
    [*https://github.com/moq/moq*](https://github.com/moq/moq)

-   <span data-ttu-id="876a1-158">**NUnit**.</span><span class="sxs-lookup"><span data-stu-id="876a1-158">**NUnit**.</span></span> <span data-ttu-id="876a1-159">Oficiální web.</span><span class="sxs-lookup"><span data-stu-id="876a1-159">Official site.</span></span>
    [*https://www.nunit.org/*](https://www.nunit.org/)

### <a name="implementing-service-tests-on-a-multi-container-application"></a><span data-ttu-id="876a1-160">Implementace služby testů na vícekontejnerová aplikace</span><span class="sxs-lookup"><span data-stu-id="876a1-160">Implementing service tests on a multi-container application</span></span> 

<span data-ttu-id="876a1-161">Jak je uvedeno výše, při testování vícekontejnerových aplikací, všechny mikroslužby musí běžet v rámci clusteru hostitelů nebo kontejneru Docker.</span><span class="sxs-lookup"><span data-stu-id="876a1-161">As noted earlier, when you test multi-container applications, all the microservices need to be running within the Docker host or container cluster.</span></span> <span data-ttu-id="876a1-162">Služby – koncový testů, které zahrnují více operací zahrnující několik mikroslužby vyžadují, abyste nasadit a spustit celou aplikaci v hostitele Docker pomocí docker-compose up (nebo mechanismus srovnatelné, pokud používáte orchestrator).</span><span class="sxs-lookup"><span data-stu-id="876a1-162">End-to-end service tests that include multiple operations involving several microservices require you to deploy and start the whole application in the Docker host by running docker-compose up (or a comparable mechanism if you are using an orchestrator).</span></span> <span data-ttu-id="876a1-163">Po celou aplikaci a její služby běží, můžete provést integraci začátku do konce a funkčních testů.</span><span class="sxs-lookup"><span data-stu-id="876a1-163">Once the whole application and all its services is running, you can execute end-to-end integration and functional tests.</span></span>

<span data-ttu-id="876a1-164">Existuje několik přístupů, které můžete použít.</span><span class="sxs-lookup"><span data-stu-id="876a1-164">There are a few approaches you can use.</span></span> <span data-ttu-id="876a1-165">V souboru docker-compose.yml, můžete použít k nasazení aplikace (nebo podobnosti, jako je docker-compose.ci.build.yml) na úrovni řešení můžete rozbalit vstupním bodem k použití [příkazu dotnet test](../../../core/tools/dotnet-test.md).</span><span class="sxs-lookup"><span data-stu-id="876a1-165">In the docker-compose.yml file that you use to deploy the application (or similar ones, like docker-compose.ci.build.yml), at the solution level you can expand the entry point to use [dotnet test](../../../core/tools/dotnet-test.md).</span></span> <span data-ttu-id="876a1-166">Můžete také použít jiný soubor compose, který by na obrázku, který se zaměřujete na spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="876a1-166">You can also use another compose file that would run your tests in the image you are targeting.</span></span> <span data-ttu-id="876a1-167">S použitím jiný soubor compose pro integrační testy, které zahrnují mikroslužeb a databází v kontejnerech, abyste měli jistotu, že související data se vždy obnovit do původního stavu před spuštěním testů.</span><span class="sxs-lookup"><span data-stu-id="876a1-167">By using another compose file for integration tests that includes your microservices and databases on containers, you can make sure that the related data is always reset to its original state before running the tests.</span></span>

<span data-ttu-id="876a1-168">Jakmile psaní aplikace je spuštěná, můžete využít výhod zarážky a výjimek, pokud používáte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="876a1-168">Once the compose application is up and running, you can take advantage of breakpoints and exceptions if you are running Visual Studio.</span></span> <span data-ttu-id="876a1-169">Nebo můžete spustit testy integrace automaticky v kanálu CI v aplikaci Visual Studio Team Services nebo jakémkoli jiném systému CI/CD, který podporuje kontejnery Dockeru.</span><span class="sxs-lookup"><span data-stu-id="876a1-169">Or you can run the integration tests automatically in your CI pipeline in Visual Studio Team Services or any other CI/CD system that supports Docker containers.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="876a1-170">[Předchozí](subscribe-events.md)
[další](../microservice-ddd-cqrs-patterns/index.md)</span><span class="sxs-lookup"><span data-stu-id="876a1-170">[Previous](subscribe-events.md)
[Next](../microservice-ddd-cqrs-patterns/index.md)</span></span>
