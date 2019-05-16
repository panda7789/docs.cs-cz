---
title: Testování služeb a webových aplikací ASP.NET Core
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Prozkoumejte architekturu pro účely testování služeb ASP.NET Core a webové aplikace v kontejnerech.
ms.date: 10/02/2018
ms.openlocfilehash: 0a741fca84f456d635e1790d6be1c72e70345a24
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644213"
---
# <a name="testing-aspnet-core-services-and-web-apps"></a><span data-ttu-id="dee6f-103">Testování služeb a webových aplikací ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="dee6f-103">Testing ASP.NET Core services and web apps</span></span>

<span data-ttu-id="dee6f-104">Kontrolery jsou klíčovou součást všem službám rozhraní API pro ASP.NET Core a ASP.NET MVC webové aplikace.</span><span class="sxs-lookup"><span data-stu-id="dee6f-104">Controllers are a central part of any ASP.NET Core API service and ASP.NET MVC Web application.</span></span> <span data-ttu-id="dee6f-105">V důsledku toho byste měli mít jistotu, které se chovají se tak, jak má pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="dee6f-105">As such, you should have confidence they behave as intended for your application.</span></span> <span data-ttu-id="dee6f-106">Automatizované testy vám můžou poskytnout tento spolehlivosti a dokáže detekovat chyby dřív, než dorazí produkčního prostředí.</span><span class="sxs-lookup"><span data-stu-id="dee6f-106">Automated tests can provide you with this confidence and can detect errors before they reach production.</span></span>

<span data-ttu-id="dee6f-107">Je potřeba otestovat, jak se chová podle platný nebo neplatný vstupy kontroler a testovací kontroler odpovědi na základě výsledku obchodní operace, které provádí.</span><span class="sxs-lookup"><span data-stu-id="dee6f-107">You need to test how the controller behaves based on valid or invalid inputs, and test controller responses based on the result of the business operation it performs.</span></span> <span data-ttu-id="dee6f-108">Nicméně byste měli mít tyto druhy testů pro mikroslužby:</span><span class="sxs-lookup"><span data-stu-id="dee6f-108">However, you should have these types of tests for your microservices:</span></span>

- <span data-ttu-id="dee6f-109">Testy jednotek.</span><span class="sxs-lookup"><span data-stu-id="dee6f-109">Unit tests.</span></span> <span data-ttu-id="dee6f-110">Tyto Ujistěte se, že jednotlivé komponenty aplikace fungovat podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="dee6f-110">These ensure that individual components of the application work as expected.</span></span> <span data-ttu-id="dee6f-111">Kontrolní výrazy otestování rozhraní API součásti.</span><span class="sxs-lookup"><span data-stu-id="dee6f-111">Assertions test the component API.</span></span>

- <span data-ttu-id="dee6f-112">Integrační testy.</span><span class="sxs-lookup"><span data-stu-id="dee6f-112">Integration tests.</span></span> <span data-ttu-id="dee6f-113">Tyto Ujistěte se, že součást interakce fungovat podle očekávání proti externí artefakty, jako jsou databáze.</span><span class="sxs-lookup"><span data-stu-id="dee6f-113">These ensure that component interactions work as expected against external artifacts like databases.</span></span> <span data-ttu-id="dee6f-114">Kontrolní výrazy můžete otestovat rozhraní API součásti, uživatelského rozhraní nebo vedlejší efekty akce, jako je databáze vstupně-výstupních operací, protokolování, atd.</span><span class="sxs-lookup"><span data-stu-id="dee6f-114">Assertions can test component API, UI, or the side effects of actions like database I/O, logging, etc.</span></span>

- <span data-ttu-id="dee6f-115">Funkční testy u jednotlivých mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="dee6f-115">Functional tests for each microservice.</span></span> <span data-ttu-id="dee6f-116">Tyto Ujistěte se, že aplikace funguje podle očekávání z pohledu uživatele.</span><span class="sxs-lookup"><span data-stu-id="dee6f-116">These ensure that the application works as expected from the user’s perspective.</span></span>

- <span data-ttu-id="dee6f-117">Ověřuje se služba.</span><span class="sxs-lookup"><span data-stu-id="dee6f-117">Service tests.</span></span> <span data-ttu-id="dee6f-118">Tyto Ujistěte se, že jsou testovány případy použití konec konec služby, včetně testování víc služeb ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="dee6f-118">These ensure that end-to-end service use cases, including testing multiple services at the same time, are tested.</span></span> <span data-ttu-id="dee6f-119">Pro tento typ testování musíte nejprve připravit prostředí.</span><span class="sxs-lookup"><span data-stu-id="dee6f-119">For this type of testing, you need to prepare the environment first.</span></span> <span data-ttu-id="dee6f-120">V tomto případě znamená spouštění služeb (například pomocí docker-compose up).</span><span class="sxs-lookup"><span data-stu-id="dee6f-120">In this case, it means starting the services (for example, by using docker-compose up).</span></span>

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a><span data-ttu-id="dee6f-121">Implementace testů částí pro rozhraní Web API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="dee6f-121">Implementing unit tests for ASP.NET Core Web APIs</span></span>

<span data-ttu-id="dee6f-122">Testování částí zahrnuje testování částí aplikace v izolaci od jeho infrastrukturu a závislosti.</span><span class="sxs-lookup"><span data-stu-id="dee6f-122">Unit testing involves testing a part of an application in isolation from its infrastructure and dependencies.</span></span> <span data-ttu-id="dee6f-123">Při testování částí je logice kontroleru, jenom obsah jedné akce nebo metoda je testována, není chování z jejich závislých nebo samotného rozhraní.</span><span class="sxs-lookup"><span data-stu-id="dee6f-123">When you unit test controller logic, only the content of a single action or method is tested, not the behavior of its dependencies or of the framework itself.</span></span> <span data-ttu-id="dee6f-124">Testy jednotek Nezjišťovat problémy v interakci mezi komponentami –, který je cílem testování integrace.</span><span class="sxs-lookup"><span data-stu-id="dee6f-124">Unit tests do not detect issues in the interaction between components—that is the purpose of integration testing.</span></span>

<span data-ttu-id="dee6f-125">Jako jednotku můžete testovat vaše akce kontroleru, ujistěte se, že se že zaměříte jenom na jejich chování.</span><span class="sxs-lookup"><span data-stu-id="dee6f-125">As you unit test your controller actions, make sure you focus only on their behavior.</span></span> <span data-ttu-id="dee6f-126">Řadič testu jednotek se vyhnete věci jako filtry, směrování nebo vazby modelu (mapování dat požadavku ViewModel nebo objekt DTO).</span><span class="sxs-lookup"><span data-stu-id="dee6f-126">A controller unit test avoids things like filters, routing, or model binding (the mapping of request data to a ViewModel or DTO).</span></span> <span data-ttu-id="dee6f-127">Protože zaměřují se na testování pouze jednou z věcí, testování jednotek je obecně k zápisu snadné a rychlé spuštění.</span><span class="sxs-lookup"><span data-stu-id="dee6f-127">Because they focus on testing just one thing, unit tests are generally simple to write and quick to run.</span></span> <span data-ttu-id="dee6f-128">Kvalitně napsané sady testů jednotek můžete často spustit bez spojená tak velká režie.</span><span class="sxs-lookup"><span data-stu-id="dee6f-128">A well-written set of unit tests can be run frequently without much overhead.</span></span>

<span data-ttu-id="dee6f-129">Testování částí se implementují podle testovacích architektur, jako jsou například xUnit.net, MSTest, Moq nebo NUnit.</span><span class="sxs-lookup"><span data-stu-id="dee6f-129">Unit tests are implemented based on test frameworks like xUnit.net, MSTest, Moq, or NUnit.</span></span> <span data-ttu-id="dee6f-130">Pro ukázkovou aplikaci aplikaci eShopOnContainers používáme xUnit.</span><span class="sxs-lookup"><span data-stu-id="dee6f-130">For the eShopOnContainers sample application, we are using xUnit.</span></span>

<span data-ttu-id="dee6f-131">Při psaní testů jednotek pro kontroler Web API je vytvoření instance třídy controller přímo pomocí new – klíčové slovo v jazyce C\#tak, aby se tak rychle spustí test.</span><span class="sxs-lookup"><span data-stu-id="dee6f-131">When you write a unit test for a Web API controller, you instantiate the controller class directly using the new keyword in C\#, so that the test will run as fast as possible.</span></span> <span data-ttu-id="dee6f-132">Následující příklad ukazuje, jak na to, jestli používáte [xUnit](https://xunit.github.io/) jako rozhraní pro testování.</span><span class="sxs-lookup"><span data-stu-id="dee6f-132">The following example shows how to do this when using [xUnit](https://xunit.github.io/) as the Test framework.</span></span>

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

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a><span data-ttu-id="dee6f-133">Implementace integrace a funkční testy u jednotlivých mikroslužeb</span><span class="sxs-lookup"><span data-stu-id="dee6f-133">Implementing integration and functional tests for each microservice</span></span>

<span data-ttu-id="dee6f-134">Jak je uvedeno, integrační testy a funkční testy mají různé účely a cíle.</span><span class="sxs-lookup"><span data-stu-id="dee6f-134">As noted, integration tests and functional tests have different purposes and goals.</span></span> <span data-ttu-id="dee6f-135">Způsob, jak implementovat při testování kontrolery ASP.NET Core je ale podobný, takže v této části budeme soustředit na integrační testy.</span><span class="sxs-lookup"><span data-stu-id="dee6f-135">However, the way you implement both when testing ASP.NET Core controllers is similar, so in this section we concentrate on integration tests.</span></span>

<span data-ttu-id="dee6f-136">Testování integrace zajistí, že součásti aplikace fungovat správně při sestavena.</span><span class="sxs-lookup"><span data-stu-id="dee6f-136">Integration testing ensures that an application's components function correctly when assembled.</span></span> <span data-ttu-id="dee6f-137">ASP.NET Core podporuje integrační testování s využitím rozhraní testování částí a integrované testovací webového hostitele, který slouží ke zpracování požadavků bez nároky na síť.</span><span class="sxs-lookup"><span data-stu-id="dee6f-137">ASP.NET Core supports integration testing using unit test frameworks and a built-in test web host that can be used to handle requests without network overhead.</span></span>

<span data-ttu-id="dee6f-138">Na rozdíl od testování jednotek testy integrace často zahrnují starostí o infrastrukturu aplikace, jako je například databáze, systém souborů, síťové prostředky, nebo webové požadavky a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="dee6f-138">Unlike unit testing, integration tests frequently involve application infrastructure concerns, such as a database, file system, network resources, or web requests and responses.</span></span> <span data-ttu-id="dee6f-139">Testy jednotek použít produkt fakes nebo napodobení objekty místo tyto problémy.</span><span class="sxs-lookup"><span data-stu-id="dee6f-139">Unit tests use fakes or mock objects in place of these concerns.</span></span> <span data-ttu-id="dee6f-140">Ale testy integrace slouží k potvrzení, že systém funguje podle očekávání u těchto systémů, tak pro testování integrace můžete použít produkt fakes ani napodobení objekty.</span><span class="sxs-lookup"><span data-stu-id="dee6f-140">But the purpose of integration tests is to confirm that the system works as expected with these systems, so for integration testing you do not use fakes or mock objects.</span></span> <span data-ttu-id="dee6f-141">Místo toho vložte infrastruktury, jako jsou databáze přístupu nebo služba volání z jiné služby.</span><span class="sxs-lookup"><span data-stu-id="dee6f-141">Instead, you include the infrastructure, like database access or service invocation from other services.</span></span>

<span data-ttu-id="dee6f-142">Protože testy integrace využít větší segmentů kódu než testování částí a integrační testy závisí na prvky infrastruktury, jsou často na řádově pomalejší než testování částí.</span><span class="sxs-lookup"><span data-stu-id="dee6f-142">Because integration tests exercise larger segments of code than unit tests, and because integration tests rely on infrastructure elements, they tend to be orders of magnitude slower than unit tests.</span></span> <span data-ttu-id="dee6f-143">Proto je vhodné omezit počet testů integrace, zápis a spouštění.</span><span class="sxs-lookup"><span data-stu-id="dee6f-143">Thus, it is a good idea to limit how many integration tests you write and run.</span></span>

<span data-ttu-id="dee6f-144">ASP.NET Core zahrnuje integrované testovací webového hostitele, který slouží ke zpracování požadavků HTTP bez nároky na síť, což znamená, že můžete spustit tyto testy rychlejší při použití skutečné webového hostitele.</span><span class="sxs-lookup"><span data-stu-id="dee6f-144">ASP.NET Core includes a built-in test web host that can be used to handle HTTP requests without network overhead, meaning that you can run those tests faster when using a real web host.</span></span> <span data-ttu-id="dee6f-145">Hostitel webového testu (TestServer) je k dispozici v komponentě NuGet jako Microsoft.AspNetCore.TestHost.</span><span class="sxs-lookup"><span data-stu-id="dee6f-145">The test web host (TestServer) is available in a NuGet component as Microsoft.AspNetCore.TestHost.</span></span> <span data-ttu-id="dee6f-146">Lze přidat do projektů testování integrace a používané aplikace do hostitele ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="dee6f-146">It can be added to integration test projects and used to host ASP.NET Core applications.</span></span>

<span data-ttu-id="dee6f-147">Jak je vidět v následujícím kódu, při vytváření testů integrace pro ASP.NET Core řadiče, vytvoříte instanci řadiče přes hostitele testu.</span><span class="sxs-lookup"><span data-stu-id="dee6f-147">As you can see in the following code, when you create integration tests for ASP.NET Core controllers, you instantiate the controllers through the test host.</span></span> <span data-ttu-id="dee6f-148">Toto je srovnatelná se požadavek HTTP, ale běží rychleji.</span><span class="sxs-lookup"><span data-stu-id="dee6f-148">This is comparable to an HTTP request, but it runs faster.</span></span>

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

#### <a name="additional-resources"></a><span data-ttu-id="dee6f-149">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="dee6f-149">Additional resources</span></span>

- <span data-ttu-id="dee6f-150">**Steve Smith. Testování kontrolerů** (ASP.NET Core) \\</span><span class="sxs-lookup"><span data-stu-id="dee6f-150">**Steve Smith. Testing controllers** (ASP.NET Core) \\</span></span>
    [https://docs.microsoft.com/aspnet/core/mvc/controllers/testing](/aspnet/core/mvc/controllers/testing)

- <span data-ttu-id="dee6f-151">**Steve Smith. Testování integrace** (ASP.NET Core) \\</span><span class="sxs-lookup"><span data-stu-id="dee6f-151">**Steve Smith. Integration testing** (ASP.NET Core) \\</span></span>
    [https://docs.microsoft.com/aspnet/core/test/integration-tests](/aspnet/core/test/integration-tests)

- <span data-ttu-id="dee6f-152">**Testování jednotek v .NET Core pomocí příkazu dotnet test** \\</span><span class="sxs-lookup"><span data-stu-id="dee6f-152">**Unit testing in .NET Core using dotnet test** \\</span></span>
    [https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test](../../../core/testing/unit-testing-with-dotnet-test.md)

- <span data-ttu-id="dee6f-153">**xUnit.net**.</span><span class="sxs-lookup"><span data-stu-id="dee6f-153">**xUnit.net**.</span></span> <span data-ttu-id="dee6f-154">Oficiální web.</span><span class="sxs-lookup"><span data-stu-id="dee6f-154">Official site.</span></span> \
    <https://xunit.github.io/>

- <span data-ttu-id="dee6f-155">**Základní informace o testování částí.**</span><span class="sxs-lookup"><span data-stu-id="dee6f-155">**Unit Test Basics.**</span></span> \
    [https://docs.microsoft.com/visualstudio/test/unit-test-basics](/visualstudio/test/unit-test-basics)

- <span data-ttu-id="dee6f-156">**Moq**.</span><span class="sxs-lookup"><span data-stu-id="dee6f-156">**Moq**.</span></span> <span data-ttu-id="dee6f-157">Úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="dee6f-157">GitHub repo.</span></span> \
    <https://github.com/moq/moq>

- <span data-ttu-id="dee6f-158">**NUnit**.</span><span class="sxs-lookup"><span data-stu-id="dee6f-158">**NUnit**.</span></span> <span data-ttu-id="dee6f-159">Oficiální web.</span><span class="sxs-lookup"><span data-stu-id="dee6f-159">Official site.</span></span> \
    <https://www.nunit.org/>

### <a name="implementing-service-tests-on-a-multi-container-application"></a><span data-ttu-id="dee6f-160">Implementace služby testů na vícekontejnerová aplikace</span><span class="sxs-lookup"><span data-stu-id="dee6f-160">Implementing service tests on a multi-container application</span></span>

<span data-ttu-id="dee6f-161">Jak je uvedeno výše, při testování vícekontejnerových aplikací, všechny mikroslužby musí běžet v rámci clusteru hostitelů nebo kontejneru Docker.</span><span class="sxs-lookup"><span data-stu-id="dee6f-161">As noted earlier, when you test multi-container applications, all the microservices need to be running within the Docker host or container cluster.</span></span> <span data-ttu-id="dee6f-162">Služby – koncový testů, které zahrnují více operací zahrnující několik mikroslužby vyžadují, abyste nasadit a spustit celou aplikaci v hostitele Docker pomocí docker-compose up (nebo mechanismus srovnatelné, pokud používáte orchestrator).</span><span class="sxs-lookup"><span data-stu-id="dee6f-162">End-to-end service tests that include multiple operations involving several microservices require you to deploy and start the whole application in the Docker host by running docker-compose up (or a comparable mechanism if you are using an orchestrator).</span></span> <span data-ttu-id="dee6f-163">Po celou aplikaci a její služby běží, můžete provést integraci začátku do konce a funkčních testů.</span><span class="sxs-lookup"><span data-stu-id="dee6f-163">Once the whole application and all its services is running, you can execute end-to-end integration and functional tests.</span></span>

<span data-ttu-id="dee6f-164">Existuje několik přístupů, které můžete použít.</span><span class="sxs-lookup"><span data-stu-id="dee6f-164">There are a few approaches you can use.</span></span> <span data-ttu-id="dee6f-165">V souboru docker-compose.yml, který použijete k nasazení aplikace na úrovni řešení můžete rozbalit vstupním bodem k použití [příkazu dotnet test](../../../core/tools/dotnet-test.md).</span><span class="sxs-lookup"><span data-stu-id="dee6f-165">In the docker-compose.yml file that you use to deploy the application at the solution level you can expand the entry point to use [dotnet test](../../../core/tools/dotnet-test.md).</span></span> <span data-ttu-id="dee6f-166">Můžete také použít jiný soubor compose, který by na obrázku, který se zaměřujete na spuštění testů.</span><span class="sxs-lookup"><span data-stu-id="dee6f-166">You can also use another compose file that would run your tests in the image you are targeting.</span></span> <span data-ttu-id="dee6f-167">S použitím jiný soubor compose pro integrační testy, které zahrnují mikroslužeb a databází v kontejnerech, abyste měli jistotu, že související data se vždy obnovit do původního stavu před spuštěním testů.</span><span class="sxs-lookup"><span data-stu-id="dee6f-167">By using another compose file for integration tests that includes your microservices and databases on containers, you can make sure that the related data is always reset to its original state before running the tests.</span></span>

<span data-ttu-id="dee6f-168">Jakmile psaní aplikace je spuštěná, můžete využít výhod zarážky a výjimek, pokud používáte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dee6f-168">Once the compose application is up and running, you can take advantage of breakpoints and exceptions if you are running Visual Studio.</span></span> <span data-ttu-id="dee6f-169">Nebo můžete spustit testy integrace automaticky v kanálu CI v DevOps služby Azure nebo jakémkoli jiném systému CI/CD, který podporuje kontejnery Dockeru.</span><span class="sxs-lookup"><span data-stu-id="dee6f-169">Or you can run the integration tests automatically in your CI pipeline in Azure DevOps Services or any other CI/CD system that supports Docker containers.</span></span>

## <a name="testing-in-eshoponcontainers"></a><span data-ttu-id="dee6f-170">Testování v aplikaci eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="dee6f-170">Testing in eShopOnContainers</span></span>

<span data-ttu-id="dee6f-171">Testy odkaz na aplikaci (aplikaci eShopOnContainers) byly nedávno změnili a nyní existují čtyři kategorie:</span><span class="sxs-lookup"><span data-stu-id="dee6f-171">The reference application (eShopOnContainers) tests were recently restructured and now there are four categories:</span></span>

1. <span data-ttu-id="dee6f-172">**Jednotka** testy, jenom prostý staré regulární jednotkové testy, součástí **{MicroserviceName}. UnitTests** projekty</span><span class="sxs-lookup"><span data-stu-id="dee6f-172">**Unit** tests, just plain old regular unit tests, contained in the **{MicroserviceName}.UnitTests** projects</span></span>

2. <span data-ttu-id="dee6f-173">**Mikroslužby funkční a integrační testy**, s testovacími případy, které zahrnují infrastrukturu u jednotlivých mikroslužeb ale izolované od ostatních a jsou obsaženy v **{MicroserviceName}. FunctionalTests** projekty.</span><span class="sxs-lookup"><span data-stu-id="dee6f-173">**Microservice functional/integration tests**, with test cases involving the infrastructure for each microservice but isolated from the others and are contained in the **{MicroserviceName}.FunctionalTests** projects.</span></span>

3. <span data-ttu-id="dee6f-174">**Testy funkčnosti/integrace aplikace**, které se zaměřují na mikroslužby integrace s testovacími případy, které získat několika mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="dee6f-174">**Application functional/integration tests**, that focus on microservices integration, with test cases that exert several microservices.</span></span> <span data-ttu-id="dee6f-175">Tyto testy se nacházejí v projektu **Application.FunctionalTests**.</span><span class="sxs-lookup"><span data-stu-id="dee6f-175">These tests are located in project **Application.FunctionalTests**.</span></span>

4. <span data-ttu-id="dee6f-176">**Zátěžové testy**, které se zaměřují na dobu odezvy u jednotlivých mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="dee6f-176">**Load tests**, that focus on response times for each microservice.</span></span> <span data-ttu-id="dee6f-177">Tyto testy se nacházejí v projektu **LoadTest** a potřebujete Visual Studio 2017 Enterprise Edition.</span><span class="sxs-lookup"><span data-stu-id="dee6f-177">These tests are located in project **LoadTest** and need Visual Studio 2017 Enterprise Edition.</span></span>

<span data-ttu-id="dee6f-178">Test jednotky a integrace jednotlivých mikroslužbách jsou obsaženy v testovací složku v jednotlivých mikroslužeb a aplikace, které zátěžové testy jsou obsaženy ve složce testu ve složce řešení, jak je znázorněno v obrázek 6 – 25.</span><span class="sxs-lookup"><span data-stu-id="dee6f-178">Unit and integration test per microservice are contained in a test folder in each microservice and Application a Load tests are contained under the test folder in the solution folder, as shown in Figure 6-25.</span></span>

![Struktura testů v aplikaci eShopOnContainers: Každá služba má složka "test", která zahrnuje částí a funkčních testů.](./media/image42.png)

<span data-ttu-id="dee6f-181">**Obrázek 6 – 25**.</span><span class="sxs-lookup"><span data-stu-id="dee6f-181">**Figure 6-25**.</span></span> <span data-ttu-id="dee6f-182">Struktura složek testu v aplikaci eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="dee6f-182">Test folder structure in eShopOnContainers</span></span>

<span data-ttu-id="dee6f-183">Mikroslužby a testy funkčnosti/integrace aplikace se spouštějí ze sady Visual Studio pomocí runneru pravidelné testy, ale nejdřív je potřeba spustit požadované infrastruktury služby, prostřednictvím sady docker-compose soubory obsažené v řešení testovat složky :</span><span class="sxs-lookup"><span data-stu-id="dee6f-183">Microservice and Application functional/integration tests are run from Visual Studio, using the regular tests runner, but first you need to start the required infrastructure services, by means of a set of docker-compose files contained in the solution test folder:</span></span>

<span data-ttu-id="dee6f-184">**docker-compose-test.yml**</span><span class="sxs-lookup"><span data-stu-id="dee6f-184">**docker-compose-test.yml**</span></span>

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

<span data-ttu-id="dee6f-185">**docker-compose-test.override.yml**</span><span class="sxs-lookup"><span data-stu-id="dee6f-185">**docker-compose-test.override.yml**</span></span>

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

<span data-ttu-id="dee6f-186">Tedy ke spuštění testů integrace funkcí a je třeba nejprve spustit tento příkaz ze složky řešení testu:</span><span class="sxs-lookup"><span data-stu-id="dee6f-186">So, to run the functional/integration tests you must first run this command, from the solution test folder:</span></span>

``` console
docker-compose -f docker-compose-test.yml -f docker-compose-test.override.yml up
```

<span data-ttu-id="dee6f-187">Jak je vidět, tyto docker-compose soubory pouze start mikroslužeb Redis, RabbitMQ, SQL Server a MongoDB.</span><span class="sxs-lookup"><span data-stu-id="dee6f-187">As you can see, these docker-compose files only start the Redis, RabbitMQ, SQL Server and MongoDB microservices.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="dee6f-188">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="dee6f-188">Additional resources</span></span>

- <span data-ttu-id="dee6f-189">**Soubor README testy** v aplikaci eShopOnContainers úložišti na Githubu \\</span><span class="sxs-lookup"><span data-stu-id="dee6f-189">**Tests README file** on the eShopOnContainers repo on GitHub \\</span></span>
    <https://github.com/dotnet-architecture/eShopOnContainers/tree/dev/test>

- <span data-ttu-id="dee6f-190">**Soubor README testy zatížení** v aplikaci eShopOnContainers úložišti na Githubu \\</span><span class="sxs-lookup"><span data-stu-id="dee6f-190">**Load tests README file** on the eShopOnContainers repo on GitHub \\</span></span>
    <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/test/ServicesTests/LoadTest/>

> [!div class="step-by-step"]
> <span data-ttu-id="dee6f-191">[Předchozí](subscribe-events.md)
> [další](background-tasks-with-ihostedservice.md)</span><span class="sxs-lookup"><span data-stu-id="dee6f-191">[Previous](subscribe-events.md)
[Next](background-tasks-with-ihostedservice.md)</span></span>
