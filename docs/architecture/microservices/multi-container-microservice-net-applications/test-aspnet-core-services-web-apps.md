---
title: Testování služeb a webových aplikací ASP.NET Core
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Prozkoumejte architekturu pro testování ASP.NET Core služeb a webových aplikací v kontejnerech.
ms.date: 10/02/2018
ms.openlocfilehash: 0a741fca84f456d635e1790d6be1c72e70345a24
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296540"
---
# <a name="testing-aspnet-core-services-and-web-apps"></a><span data-ttu-id="4a433-103">Testování služeb a webových aplikací ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4a433-103">Testing ASP.NET Core services and web apps</span></span>

<span data-ttu-id="4a433-104">Řadiče jsou centrální součástí jakékoli ASP.NET Core služby API a webové aplikace ASP.NET MVC.</span><span class="sxs-lookup"><span data-stu-id="4a433-104">Controllers are a central part of any ASP.NET Core API service and ASP.NET MVC Web application.</span></span> <span data-ttu-id="4a433-105">V takovém případě byste měli mít jistotu, že se chovají jako zamýšlená pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="4a433-105">As such, you should have confidence they behave as intended for your application.</span></span> <span data-ttu-id="4a433-106">Automatizované testy vám můžou poskytnout tuto jistotu a můžou odhalit chyby dřív, než dosáhnou produkčního prostředí.</span><span class="sxs-lookup"><span data-stu-id="4a433-106">Automated tests can provide you with this confidence and can detect errors before they reach production.</span></span>

<span data-ttu-id="4a433-107">Je nutné otestovat, jak se kontroler chová na základě platných nebo neplatných vstupů, a odezvy testovacího kontroléru na základě výsledku obchodní operace, kterou provádí.</span><span class="sxs-lookup"><span data-stu-id="4a433-107">You need to test how the controller behaves based on valid or invalid inputs, and test controller responses based on the result of the business operation it performs.</span></span> <span data-ttu-id="4a433-108">Nicméně byste měli mít tyto typy testů pro vaše mikroslužby:</span><span class="sxs-lookup"><span data-stu-id="4a433-108">However, you should have these types of tests for your microservices:</span></span>

- <span data-ttu-id="4a433-109">Testování částí.</span><span class="sxs-lookup"><span data-stu-id="4a433-109">Unit tests.</span></span> <span data-ttu-id="4a433-110">Tím zajistíte, že jednotlivé komponenty aplikace fungují podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="4a433-110">These ensure that individual components of the application work as expected.</span></span> <span data-ttu-id="4a433-111">Kontrolní výrazy testují rozhraní API součásti.</span><span class="sxs-lookup"><span data-stu-id="4a433-111">Assertions test the component API.</span></span>

- <span data-ttu-id="4a433-112">Integrační testy.</span><span class="sxs-lookup"><span data-stu-id="4a433-112">Integration tests.</span></span> <span data-ttu-id="4a433-113">Tím zajistíte, aby interakce komponent fungovaly podle očekávání proti externím artefaktům, jako jsou databáze.</span><span class="sxs-lookup"><span data-stu-id="4a433-113">These ensure that component interactions work as expected against external artifacts like databases.</span></span> <span data-ttu-id="4a433-114">Kontrolní výrazy mohou testovat součásti rozhraní API komponenty, uživatelského rozhraní nebo vedlejší účinky akcí, jako je v/v databáze, protokolování atd.</span><span class="sxs-lookup"><span data-stu-id="4a433-114">Assertions can test component API, UI, or the side effects of actions like database I/O, logging, etc.</span></span>

- <span data-ttu-id="4a433-115">Funkční testy pro jednotlivé mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="4a433-115">Functional tests for each microservice.</span></span> <span data-ttu-id="4a433-116">Tím se zajistí, že aplikace bude v perspektivě uživatele fungovat podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="4a433-116">These ensure that the application works as expected from the user’s perspective.</span></span>

- <span data-ttu-id="4a433-117">Testy služby.</span><span class="sxs-lookup"><span data-stu-id="4a433-117">Service tests.</span></span> <span data-ttu-id="4a433-118">Tím se zajistí, že budou testovány kompletní případy použití služeb, včetně testování více služeb současně.</span><span class="sxs-lookup"><span data-stu-id="4a433-118">These ensure that end-to-end service use cases, including testing multiple services at the same time, are tested.</span></span> <span data-ttu-id="4a433-119">Pro tento typ testování musíte nejprve připravit prostředí.</span><span class="sxs-lookup"><span data-stu-id="4a433-119">For this type of testing, you need to prepare the environment first.</span></span> <span data-ttu-id="4a433-120">V takovém případě to znamená spouštění služeb (například pomocí Docker – sestavení).</span><span class="sxs-lookup"><span data-stu-id="4a433-120">In this case, it means starting the services (for example, by using docker-compose up).</span></span>

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a><span data-ttu-id="4a433-121">Implementace testů jednotek pro ASP.NET Core webová rozhraní API</span><span class="sxs-lookup"><span data-stu-id="4a433-121">Implementing unit tests for ASP.NET Core Web APIs</span></span>

<span data-ttu-id="4a433-122">Testování částí zahrnuje testování součásti aplikace v izolaci od jejich infrastruktury a závislostí.</span><span class="sxs-lookup"><span data-stu-id="4a433-122">Unit testing involves testing a part of an application in isolation from its infrastructure and dependencies.</span></span> <span data-ttu-id="4a433-123">V případě logiky testovacího kontroleru jednotek je testován pouze obsah jedné akce nebo metody, nikoli chování jeho závislostí nebo samotného rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4a433-123">When you unit test controller logic, only the content of a single action or method is tested, not the behavior of its dependencies or of the framework itself.</span></span> <span data-ttu-id="4a433-124">Testy jednotek nezjišťují problémy v interakci mezi komponentami, což je účel testování integrací.</span><span class="sxs-lookup"><span data-stu-id="4a433-124">Unit tests do not detect issues in the interaction between components—that is the purpose of integration testing.</span></span>

<span data-ttu-id="4a433-125">Při testování akcí kontroleru se ujistěte, že se zaměříte jenom na jejich chování.</span><span class="sxs-lookup"><span data-stu-id="4a433-125">As you unit test your controller actions, make sure you focus only on their behavior.</span></span> <span data-ttu-id="4a433-126">Test jednotek kontroleru se vyhne tomu, jako jsou filtry, směrování nebo vazby modelů (mapování dat požadavků na ViewModel nebo DTO).</span><span class="sxs-lookup"><span data-stu-id="4a433-126">A controller unit test avoids things like filters, routing, or model binding (the mapping of request data to a ViewModel or DTO).</span></span> <span data-ttu-id="4a433-127">Vzhledem k tomu, že se soustředí na testování pouze jedné věci, testy jednotek jsou obecně jednoduché pro psaní a rychlé spuštění.</span><span class="sxs-lookup"><span data-stu-id="4a433-127">Because they focus on testing just one thing, unit tests are generally simple to write and quick to run.</span></span> <span data-ttu-id="4a433-128">Dobře zapsaná sada testů jednotek se může spouštět často bez nadměrné režie.</span><span class="sxs-lookup"><span data-stu-id="4a433-128">A well-written set of unit tests can be run frequently without much overhead.</span></span>

<span data-ttu-id="4a433-129">Testy jednotek jsou implementovány na základě testovacích rozhraní, jako jsou xUnit.net, MSTest, MOQ nebo NUnit.</span><span class="sxs-lookup"><span data-stu-id="4a433-129">Unit tests are implemented based on test frameworks like xUnit.net, MSTest, Moq, or NUnit.</span></span> <span data-ttu-id="4a433-130">Pro ukázkovou aplikaci eShopOnContainers používáme xUnit.</span><span class="sxs-lookup"><span data-stu-id="4a433-130">For the eShopOnContainers sample application, we are using xUnit.</span></span>

<span data-ttu-id="4a433-131">Při psaní testu jednotek pro kontroler webového rozhraní API se vytvoří instance třídy Controller přímo pomocí klíčového slova New v jazyce C\#, aby se test spouštěl co nejrychleji.</span><span class="sxs-lookup"><span data-stu-id="4a433-131">When you write a unit test for a Web API controller, you instantiate the controller class directly using the new keyword in C\#, so that the test will run as fast as possible.</span></span> <span data-ttu-id="4a433-132">Následující příklad ukazuje, jak to provést při použití [xUnit](https://xunit.github.io/) jako testovacího rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4a433-132">The following example shows how to do this when using [xUnit](https://xunit.github.io/) as the Test framework.</span></span>

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

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a><span data-ttu-id="4a433-133">Implementace integračních a funkčních testů pro jednotlivé mikroslužby</span><span class="sxs-lookup"><span data-stu-id="4a433-133">Implementing integration and functional tests for each microservice</span></span>

<span data-ttu-id="4a433-134">Jak je uvedeno, testy integrace a funkční testy mají různé účely a cíle.</span><span class="sxs-lookup"><span data-stu-id="4a433-134">As noted, integration tests and functional tests have different purposes and goals.</span></span> <span data-ttu-id="4a433-135">Nicméně způsob implementace při testování ASP.NET Corech řadičů je podobný, takže v této části se zaměřujeme na integrační testy.</span><span class="sxs-lookup"><span data-stu-id="4a433-135">However, the way you implement both when testing ASP.NET Core controllers is similar, so in this section we concentrate on integration tests.</span></span>

<span data-ttu-id="4a433-136">Při testování integrace je zajištěno, že komponenty aplikace budou při sestavování fungovat správně.</span><span class="sxs-lookup"><span data-stu-id="4a433-136">Integration testing ensures that an application's components function correctly when assembled.</span></span> <span data-ttu-id="4a433-137">ASP.NET Core podporuje testování integrace pomocí rozhraní pro testování částí a integrovaného testovacího webového hostitele, který lze použít pro zpracování požadavků bez režie sítě.</span><span class="sxs-lookup"><span data-stu-id="4a433-137">ASP.NET Core supports integration testing using unit test frameworks and a built-in test web host that can be used to handle requests without network overhead.</span></span>

<span data-ttu-id="4a433-138">Na rozdíl od testování částí zahrnuje testy pro integraci často aspekty infrastruktury aplikace, jako je databáze, systém souborů, síťové prostředky nebo webové požadavky a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="4a433-138">Unlike unit testing, integration tests frequently involve application infrastructure concerns, such as a database, file system, network resources, or web requests and responses.</span></span> <span data-ttu-id="4a433-139">Testování částí místo těchto otázek používají napodobeniny nebo napodobné objekty.</span><span class="sxs-lookup"><span data-stu-id="4a433-139">Unit tests use fakes or mock objects in place of these concerns.</span></span> <span data-ttu-id="4a433-140">Ale účelem integračních testů je potvrdit, že systém pracuje podle očekávání u těchto systémů, takže pro účely integrace při integraci nepoužíváte napodobeniny nebo objekty s přípravou.</span><span class="sxs-lookup"><span data-stu-id="4a433-140">But the purpose of integration tests is to confirm that the system works as expected with these systems, so for integration testing you do not use fakes or mock objects.</span></span> <span data-ttu-id="4a433-141">Místo toho zahrnete infrastrukturu, jako je přístup k databázi nebo vyvolání služby z jiných služeb.</span><span class="sxs-lookup"><span data-stu-id="4a433-141">Instead, you include the infrastructure, like database access or service invocation from other services.</span></span>

<span data-ttu-id="4a433-142">Vzhledem k tomu, že integrační testy vykonávají větší segmenty kódu než testy jednotek a protože integrační testy spoléhají na prvky infrastruktury, mají za následek, že se jedná o objednávky pomaleji než testy jednotek.</span><span class="sxs-lookup"><span data-stu-id="4a433-142">Because integration tests exercise larger segments of code than unit tests, and because integration tests rely on infrastructure elements, they tend to be orders of magnitude slower than unit tests.</span></span> <span data-ttu-id="4a433-143">Proto je vhodné omezit počet testů integrace, které zapisujete a spouštíte.</span><span class="sxs-lookup"><span data-stu-id="4a433-143">Thus, it is a good idea to limit how many integration tests you write and run.</span></span>

<span data-ttu-id="4a433-144">ASP.NET Core obsahuje vestavěný testovací webový hostitel, který se dá použít ke zpracování požadavků HTTP bez režie sítě, což znamená, že tyto testy můžete spustit rychleji při použití reálného webového hostitele.</span><span class="sxs-lookup"><span data-stu-id="4a433-144">ASP.NET Core includes a built-in test web host that can be used to handle HTTP requests without network overhead, meaning that you can run those tests faster when using a real web host.</span></span> <span data-ttu-id="4a433-145">Testovací webový hostitel (TestServer) je k dispozici v komponentě NuGet jako Microsoft. AspNetCore. TestHost.</span><span class="sxs-lookup"><span data-stu-id="4a433-145">The test web host (TestServer) is available in a NuGet component as Microsoft.AspNetCore.TestHost.</span></span> <span data-ttu-id="4a433-146">Lze ji přidat do projektů Integration Tests a použít k hostování ASP.NET Corech aplikací.</span><span class="sxs-lookup"><span data-stu-id="4a433-146">It can be added to integration test projects and used to host ASP.NET Core applications.</span></span>

<span data-ttu-id="4a433-147">Jak vidíte v následujícím kódu, při vytváření integračních testů pro ASP.NET Core řadiče, vytváříte instance řadičů přes testovacího hostitele.</span><span class="sxs-lookup"><span data-stu-id="4a433-147">As you can see in the following code, when you create integration tests for ASP.NET Core controllers, you instantiate the controllers through the test host.</span></span> <span data-ttu-id="4a433-148">To je srovnatelné s požadavkem HTTP, ale běží rychleji.</span><span class="sxs-lookup"><span data-stu-id="4a433-148">This is comparable to an HTTP request, but it runs faster.</span></span>

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

#### <a name="additional-resources"></a><span data-ttu-id="4a433-149">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="4a433-149">Additional resources</span></span>

- <span data-ttu-id="4a433-150">**Steve Smith. Testovací kontroléry** (ASP.NET Core) </span><span class="sxs-lookup"><span data-stu-id="4a433-150">**Steve Smith. Testing controllers** (ASP.NET Core) </span></span>\
    [https://docs.microsoft.com/aspnet/core/mvc/controllers/testing](/aspnet/core/mvc/controllers/testing)

- <span data-ttu-id="4a433-151">**Steve Smith. Testování** integrace (ASP.NET Core) </span><span class="sxs-lookup"><span data-stu-id="4a433-151">**Steve Smith. Integration testing** (ASP.NET Core) </span></span>\
    [https://docs.microsoft.com/aspnet/core/test/integration-tests](/aspnet/core/test/integration-tests)

- <span data-ttu-id="4a433-152">**Testování částí v .NET Core pomocí testu dotnet** </span><span class="sxs-lookup"><span data-stu-id="4a433-152">**Unit testing in .NET Core using dotnet test** </span></span>\
    [https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test](../../../core/testing/unit-testing-with-dotnet-test.md)

- <span data-ttu-id="4a433-153">**xUnit.net**.</span><span class="sxs-lookup"><span data-stu-id="4a433-153">**xUnit.net**.</span></span> <span data-ttu-id="4a433-154">Oficiální lokalita.</span><span class="sxs-lookup"><span data-stu-id="4a433-154">Official site.</span></span> \
    <https://xunit.github.io/>

- <span data-ttu-id="4a433-155">**Základy testování částí.**</span><span class="sxs-lookup"><span data-stu-id="4a433-155">**Unit Test Basics.**</span></span> \
    [https://docs.microsoft.com/visualstudio/test/unit-test-basics](/visualstudio/test/unit-test-basics)

- <span data-ttu-id="4a433-156">**MOQ**.</span><span class="sxs-lookup"><span data-stu-id="4a433-156">**Moq**.</span></span> <span data-ttu-id="4a433-157">Úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="4a433-157">GitHub repo.</span></span> \
    <https://github.com/moq/moq>

- <span data-ttu-id="4a433-158">**Nunit**.</span><span class="sxs-lookup"><span data-stu-id="4a433-158">**NUnit**.</span></span> <span data-ttu-id="4a433-159">Oficiální lokalita.</span><span class="sxs-lookup"><span data-stu-id="4a433-159">Official site.</span></span> \
    <https://www.nunit.org/>

### <a name="implementing-service-tests-on-a-multi-container-application"></a><span data-ttu-id="4a433-160">Implementace testů služby v aplikaci s více kontejnery</span><span class="sxs-lookup"><span data-stu-id="4a433-160">Implementing service tests on a multi-container application</span></span>

<span data-ttu-id="4a433-161">Jak bylo uvedeno dříve, při testování aplikací s více kontejnery musí být všechny mikroslužby spuštěny v hostiteli Docker nebo v clusteru kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="4a433-161">As noted earlier, when you test multi-container applications, all the microservices need to be running within the Docker host or container cluster.</span></span> <span data-ttu-id="4a433-162">Komplexní testy služby, které zahrnují více operací, které zahrnují několik mikroslužeb, vyžadují nasazení a spuštění celé aplikace v hostiteli Docker spuštěním Docker – sestavení (nebo srovnatelného mechanismu, pokud používáte nástroj Orchestrator).</span><span class="sxs-lookup"><span data-stu-id="4a433-162">End-to-end service tests that include multiple operations involving several microservices require you to deploy and start the whole application in the Docker host by running docker-compose up (or a comparable mechanism if you are using an orchestrator).</span></span> <span data-ttu-id="4a433-163">Po spuštění celé aplikace a všech jejích služeb můžete provést ucelenou integraci a funkční testy.</span><span class="sxs-lookup"><span data-stu-id="4a433-163">Once the whole application and all its services is running, you can execute end-to-end integration and functional tests.</span></span>

<span data-ttu-id="4a433-164">K dispozici je několik přístupů, které můžete použít.</span><span class="sxs-lookup"><span data-stu-id="4a433-164">There are a few approaches you can use.</span></span> <span data-ttu-id="4a433-165">V souboru Docker-Compose. yml, který používáte k nasazení aplikace na úrovni řešení, můžete rozšířit vstupní bod pro použití [testu dotnet](../../../core/tools/dotnet-test.md).</span><span class="sxs-lookup"><span data-stu-id="4a433-165">In the docker-compose.yml file that you use to deploy the application at the solution level you can expand the entry point to use [dotnet test](../../../core/tools/dotnet-test.md).</span></span> <span data-ttu-id="4a433-166">Můžete také použít jiný soubor pro vytváření, který by spouštěl testy v imagi, na kterou cílíte.</span><span class="sxs-lookup"><span data-stu-id="4a433-166">You can also use another compose file that would run your tests in the image you are targeting.</span></span> <span data-ttu-id="4a433-167">Pomocí jiného souboru pro testy integrace, který obsahuje vaše mikroslužby a databáze na kontejnerech, můžete zajistit, aby se související data při spuštění testů vždycky obnovila do původního stavu.</span><span class="sxs-lookup"><span data-stu-id="4a433-167">By using another compose file for integration tests that includes your microservices and databases on containers, you can make sure that the related data is always reset to its original state before running the tests.</span></span>

<span data-ttu-id="4a433-168">Jakmile je aplikace pro psaní v provozu, můžete využít zarážky a výjimky, pokud používáte sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4a433-168">Once the compose application is up and running, you can take advantage of breakpoints and exceptions if you are running Visual Studio.</span></span> <span data-ttu-id="4a433-169">Nebo můžete spustit testy integrace automaticky v kanálu CI v Azure DevOps Services nebo jakémkoli jiném systému CI/CD, který podporuje kontejnery Docker.</span><span class="sxs-lookup"><span data-stu-id="4a433-169">Or you can run the integration tests automatically in your CI pipeline in Azure DevOps Services or any other CI/CD system that supports Docker containers.</span></span>

## <a name="testing-in-eshoponcontainers"></a><span data-ttu-id="4a433-170">Testování v eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="4a433-170">Testing in eShopOnContainers</span></span>

<span data-ttu-id="4a433-171">Testy referenční aplikace (eShopOnContainers) se nedávno změnily a teď existují čtyři kategorie:</span><span class="sxs-lookup"><span data-stu-id="4a433-171">The reference application (eShopOnContainers) tests were recently restructured and now there are four categories:</span></span>

1. <span data-ttu-id="4a433-172">Testování **částí** , stejně jako staré staré testy jednotek, obsažené v poli **{mikroservice}. Projekty UnitTests**</span><span class="sxs-lookup"><span data-stu-id="4a433-172">**Unit** tests, just plain old regular unit tests, contained in the **{MicroserviceName}.UnitTests** projects</span></span>

2. <span data-ttu-id="4a433-173">**Testy funkčnosti nebo integrace mikroslužeb**s testovacími případy, které se týkají infrastruktury pro jednotlivé mikroslužby, ale izolované od ostatních a jsou součástí služby **{mikroslužba}. Projekty FunctionalTests**</span><span class="sxs-lookup"><span data-stu-id="4a433-173">**Microservice functional/integration tests**, with test cases involving the infrastructure for each microservice but isolated from the others and are contained in the **{MicroserviceName}.FunctionalTests** projects.</span></span>

3. <span data-ttu-id="4a433-174">**Funkce/integrační testy pro aplikace**, které se zaměřují na integraci mikroslužeb, s testovacími případy, které působí několik mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="4a433-174">**Application functional/integration tests**, that focus on microservices integration, with test cases that exert several microservices.</span></span> <span data-ttu-id="4a433-175">Tyto testy jsou umístěny v Project **Application. FunctionalTests**.</span><span class="sxs-lookup"><span data-stu-id="4a433-175">These tests are located in project **Application.FunctionalTests**.</span></span>

4. <span data-ttu-id="4a433-176">**Zátěžové testy**, které se zaměřují na doby odezvy pro jednotlivé mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="4a433-176">**Load tests**, that focus on response times for each microservice.</span></span> <span data-ttu-id="4a433-177">Tyto testy jsou umístěné v Project **LoadTest** a potřebují Visual Studio 2017 Enterprise Edition.</span><span class="sxs-lookup"><span data-stu-id="4a433-177">These tests are located in project **LoadTest** and need Visual Studio 2017 Enterprise Edition.</span></span>

<span data-ttu-id="4a433-178">Test jednotek a integračních testů na mikroslužbu je obsažen v testovací složce v každé mikroslužbě a aplikaci. testy zatížení jsou obsaženy ve složce test ve složce řešení, jak je znázorněno na obrázku 6-25.</span><span class="sxs-lookup"><span data-stu-id="4a433-178">Unit and integration test per microservice are contained in a test folder in each microservice and Application a Load tests are contained under the test folder in the solution folder, as shown in Figure 6-25.</span></span>

![Struktura testů v eShopOnContainers: Každá služba má "testovací" složku, která obsahuje jednotky a funkční testy.](./media/image42.png)

<span data-ttu-id="4a433-181">**Obrázek 6-25**.</span><span class="sxs-lookup"><span data-stu-id="4a433-181">**Figure 6-25**.</span></span> <span data-ttu-id="4a433-182">Struktura testovacích složek v eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="4a433-182">Test folder structure in eShopOnContainers</span></span>

<span data-ttu-id="4a433-183">Testy funkcí a integrace mikroslužeb a aplikací jsou spouštěny ze sady Visual Studio pomocí rutiny regulárních testů, ale nejdřív je potřeba spustit požadované služby infrastruktury, a to pomocí sady souborů Docker pro sestavení, které jsou obsaženy ve složce test řešení. :</span><span class="sxs-lookup"><span data-stu-id="4a433-183">Microservice and Application functional/integration tests are run from Visual Studio, using the regular tests runner, but first you need to start the required infrastructure services, by means of a set of docker-compose files contained in the solution test folder:</span></span>

<span data-ttu-id="4a433-184">**docker-compose-test.yml**</span><span class="sxs-lookup"><span data-stu-id="4a433-184">**docker-compose-test.yml**</span></span>

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

<span data-ttu-id="4a433-185">**docker-compose-test.override.yml**</span><span class="sxs-lookup"><span data-stu-id="4a433-185">**docker-compose-test.override.yml**</span></span>

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

<span data-ttu-id="4a433-186">Takže pokud chcete spustit testy funkčnosti nebo integrace, musíte nejdřív spustit tento příkaz ze složky test řešení:</span><span class="sxs-lookup"><span data-stu-id="4a433-186">So, to run the functional/integration tests you must first run this command, from the solution test folder:</span></span>

``` console
docker-compose -f docker-compose-test.yml -f docker-compose-test.override.yml up
```

<span data-ttu-id="4a433-187">Jak vidíte, tyto soubory Docker-skládání začínají pouze mikroslužby Redis, RabbitMQ, SQL Server a MongoDB.</span><span class="sxs-lookup"><span data-stu-id="4a433-187">As you can see, these docker-compose files only start the Redis, RabbitMQ, SQL Server and MongoDB microservices.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="4a433-188">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="4a433-188">Additional resources</span></span>

- <span data-ttu-id="4a433-189">**Testuje soubor Readme** v úložišti EShopOnContainers na GitHubu </span><span class="sxs-lookup"><span data-stu-id="4a433-189">**Tests README file** on the eShopOnContainers repo on GitHub </span></span>\
    <https://github.com/dotnet-architecture/eShopOnContainers/tree/dev/test>

- <span data-ttu-id="4a433-190">**Zátěžové testy souboru Readme** v úložišti EShopOnContainers na GitHubu </span><span class="sxs-lookup"><span data-stu-id="4a433-190">**Load tests README file** on the eShopOnContainers repo on GitHub </span></span>\
    <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/test/ServicesTests/LoadTest/>

> [!div class="step-by-step"]
> <span data-ttu-id="4a433-191">[Předchozí](subscribe-events.md)Další
> [](background-tasks-with-ihostedservice.md)</span><span class="sxs-lookup"><span data-stu-id="4a433-191">[Previous](subscribe-events.md)
[Next](background-tasks-with-ihostedservice.md)</span></span>
