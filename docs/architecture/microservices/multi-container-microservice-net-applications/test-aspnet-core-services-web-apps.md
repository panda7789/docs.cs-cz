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
# <a name="testing-aspnet-core-services-and-web-apps"></a><span data-ttu-id="495ff-103">Testování služeb a webových aplikací ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="495ff-103">Testing ASP.NET Core services and web apps</span></span>

<span data-ttu-id="495ff-104">Řadiče jsou centrální součástí jakékoli služby ASP.NET Core API a ASP.NET webové aplikace MVC.</span><span class="sxs-lookup"><span data-stu-id="495ff-104">Controllers are a central part of any ASP.NET Core API service and ASP.NET MVC Web application.</span></span> <span data-ttu-id="495ff-105">Jako takové byste měli mít jistotu, že se chovají tak, jak je určeno pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="495ff-105">As such, you should have confidence they behave as intended for your application.</span></span> <span data-ttu-id="495ff-106">Automatizované testy vám mohou poskytnout tuto jistotu a mohou zjistit chyby dříve, než se dostanou do produkčního prostředí.</span><span class="sxs-lookup"><span data-stu-id="495ff-106">Automated tests can provide you with this confidence and can detect errors before they reach production.</span></span>

<span data-ttu-id="495ff-107">Je třeba otestovat, jak se ovladač chová na základě platných nebo neplatných vstupů a testovat odpovědi řadiče na základě výsledku obchodní operace, kterou provádí.</span><span class="sxs-lookup"><span data-stu-id="495ff-107">You need to test how the controller behaves based on valid or invalid inputs, and test controller responses based on the result of the business operation it performs.</span></span> <span data-ttu-id="495ff-108">Měli byste však mít tyto typy testů pro vaše mikroslužby:</span><span class="sxs-lookup"><span data-stu-id="495ff-108">However, you should have these types of tests for your microservices:</span></span>

- <span data-ttu-id="495ff-109">Jednotkové testy.</span><span class="sxs-lookup"><span data-stu-id="495ff-109">Unit tests.</span></span> <span data-ttu-id="495ff-110">Ty zajišťují, že jednotlivé součásti aplikace fungují podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="495ff-110">These ensure that individual components of the application work as expected.</span></span> <span data-ttu-id="495ff-111">Kontrolní výrazy testují rozhraní API komponenty.</span><span class="sxs-lookup"><span data-stu-id="495ff-111">Assertions test the component API.</span></span>

- <span data-ttu-id="495ff-112">Integrační testy.</span><span class="sxs-lookup"><span data-stu-id="495ff-112">Integration tests.</span></span> <span data-ttu-id="495ff-113">Ty zajišťují, že interakce komponent fungovat podle očekávání proti externí artefakty, jako jsou databáze.</span><span class="sxs-lookup"><span data-stu-id="495ff-113">These ensure that component interactions work as expected against external artifacts like databases.</span></span> <span data-ttu-id="495ff-114">Kontrolní výrazy můžete otestovat rozhraní API součásti, ui nebo vedlejší účinky akcí, jako je vstupně-v.o databáze, protokolování, atd.</span><span class="sxs-lookup"><span data-stu-id="495ff-114">Assertions can test component API, UI, or the side effects of actions like database I/O, logging, etc.</span></span>

- <span data-ttu-id="495ff-115">Funkční testy pro každou mikroslužbu.</span><span class="sxs-lookup"><span data-stu-id="495ff-115">Functional tests for each microservice.</span></span> <span data-ttu-id="495ff-116">Ty zajišťují, že aplikace funguje podle očekávání z pohledu uživatele.</span><span class="sxs-lookup"><span data-stu-id="495ff-116">These ensure that the application works as expected from the user's perspective.</span></span>

- <span data-ttu-id="495ff-117">Servisní testy.</span><span class="sxs-lookup"><span data-stu-id="495ff-117">Service tests.</span></span> <span data-ttu-id="495ff-118">Ty zajišťují, že jsou testovány případy použití služby end-to-end, včetně testování více služeb současně.</span><span class="sxs-lookup"><span data-stu-id="495ff-118">These ensure that end-to-end service use cases, including testing multiple services at the same time, are tested.</span></span> <span data-ttu-id="495ff-119">Pro tento typ testování je třeba nejprve připravit prostředí.</span><span class="sxs-lookup"><span data-stu-id="495ff-119">For this type of testing, you need to prepare the environment first.</span></span> <span data-ttu-id="495ff-120">V tomto případě to znamená spuštění služeb (například pomocí docker-compose up).</span><span class="sxs-lookup"><span data-stu-id="495ff-120">In this case, it means starting the services (for example, by using docker-compose up).</span></span>

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a><span data-ttu-id="495ff-121">Implementace testů částí pro ASP.NET základní webová rozhraní API</span><span class="sxs-lookup"><span data-stu-id="495ff-121">Implementing unit tests for ASP.NET Core Web APIs</span></span>

<span data-ttu-id="495ff-122">Testování částí zahrnuje testování části aplikace v izolaci od její infrastruktury a závislostí.</span><span class="sxs-lookup"><span data-stu-id="495ff-122">Unit testing involves testing a part of an application in isolation from its infrastructure and dependencies.</span></span> <span data-ttu-id="495ff-123">Při testování logiky řadiče jednotky pouze obsah jedné akce nebo metody je testován, nikoli chování jeho závislostí nebo samotného rozhraní.</span><span class="sxs-lookup"><span data-stu-id="495ff-123">When you unit test controller logic, only the content of a single action or method is tested, not the behavior of its dependencies or of the framework itself.</span></span> <span data-ttu-id="495ff-124">Testování částí nezjišťuje problémy v interakci mezi součástmi – to je účel testování integrace.</span><span class="sxs-lookup"><span data-stu-id="495ff-124">Unit tests do not detect issues in the interaction between components—that is the purpose of integration testing.</span></span>

<span data-ttu-id="495ff-125">Při testování částí akce ovladače, ujistěte se, že se zaměříte pouze na jejich chování.</span><span class="sxs-lookup"><span data-stu-id="495ff-125">As you unit test your controller actions, make sure you focus only on their behavior.</span></span> <span data-ttu-id="495ff-126">Testování jednotky řadiče se vyhýbá věcem, jako jsou filtry, směrování nebo vazba modelu (mapování dat požadavku na ViewModel nebo DTO).</span><span class="sxs-lookup"><span data-stu-id="495ff-126">A controller unit test avoids things like filters, routing, or model binding (the mapping of request data to a ViewModel or DTO).</span></span> <span data-ttu-id="495ff-127">Vzhledem k tomu, že se zaměřují na testování pouze jednu věc, testování částí jsou obecně jednoduché psát a rychle spustit.</span><span class="sxs-lookup"><span data-stu-id="495ff-127">Because they focus on testing just one thing, unit tests are generally simple to write and quick to run.</span></span> <span data-ttu-id="495ff-128">Dobře napsaná sada testů částí lze spustit často bez velké režie.</span><span class="sxs-lookup"><span data-stu-id="495ff-128">A well-written set of unit tests can be run frequently without much overhead.</span></span>

<span data-ttu-id="495ff-129">Testování částí jsou implementovány na základě testovacích architektur, jako je xUnit.net, MSTest, Moq nebo NUnit.</span><span class="sxs-lookup"><span data-stu-id="495ff-129">Unit tests are implemented based on test frameworks like xUnit.net, MSTest, Moq, or NUnit.</span></span> <span data-ttu-id="495ff-130">Pro ukázkovou aplikaci eShopOnContainers používáme xUnit.</span><span class="sxs-lookup"><span data-stu-id="495ff-130">For the eShopOnContainers sample application, we are using xUnit.</span></span>

<span data-ttu-id="495ff-131">Při psaní testování částí pro řadič webového rozhraní API, konstanci třídy\#řadiče přímo pomocí nové klíčové slovo v C , tak, aby test bude spuštěn co nejrychleji.</span><span class="sxs-lookup"><span data-stu-id="495ff-131">When you write a unit test for a Web API controller, you instantiate the controller class directly using the new keyword in C\#, so that the test will run as fast as possible.</span></span> <span data-ttu-id="495ff-132">Následující příklad ukazuje, jak to provést při použití [xUnit](https://xunit.github.io/) jako rozhraní Test.</span><span class="sxs-lookup"><span data-stu-id="495ff-132">The following example shows how to do this when using [xUnit](https://xunit.github.io/) as the Test framework.</span></span>

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

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a><span data-ttu-id="495ff-133">Implementace integračních a funkčních testů pro každou mikroslužbu</span><span class="sxs-lookup"><span data-stu-id="495ff-133">Implementing integration and functional tests for each microservice</span></span>

<span data-ttu-id="495ff-134">Jak již bylo uvedeno, integrační testy a funkční testy mají různé účely a cíle.</span><span class="sxs-lookup"><span data-stu-id="495ff-134">As noted, integration tests and functional tests have different purposes and goals.</span></span> <span data-ttu-id="495ff-135">Způsob implementace obou při testování ASP.NET řadiče Core je však podobný, takže v této části se soustředíme na integrační testy.</span><span class="sxs-lookup"><span data-stu-id="495ff-135">However, the way you implement both when testing ASP.NET Core controllers is similar, so in this section we concentrate on integration tests.</span></span>

<span data-ttu-id="495ff-136">Testování integrace zajišťuje, že součásti aplikace fungují správně při sestavení.</span><span class="sxs-lookup"><span data-stu-id="495ff-136">Integration testing ensures that an application's components function correctly when assembled.</span></span> <span data-ttu-id="495ff-137">ASP.NET Core podporuje testování integrace pomocí rozhraní testování částí a integrovaného testovacího webového hostitele, který lze použít ke zpracování požadavků bez zatížení sítě.</span><span class="sxs-lookup"><span data-stu-id="495ff-137">ASP.NET Core supports integration testing using unit test frameworks and a built-in test web host that can be used to handle requests without network overhead.</span></span>

<span data-ttu-id="495ff-138">Na rozdíl od testování částí testy integrace často zahrnují problémy infrastruktury aplikací, jako je například databáze, systém souborů, síťové prostředky nebo webové požadavky a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="495ff-138">Unlike unit testing, integration tests frequently involve application infrastructure concerns, such as a database, file system, network resources, or web requests and responses.</span></span> <span data-ttu-id="495ff-139">Testy částí používají falešné nebo falešné objekty místo těchto obav.</span><span class="sxs-lookup"><span data-stu-id="495ff-139">Unit tests use fakes or mock objects in place of these concerns.</span></span> <span data-ttu-id="495ff-140">Ale účelem integračních testů je potvrdit, že systém funguje podle očekávání s těmito systémy, takže pro testování integrace nepoužíváte padělky nebo falešné objekty.</span><span class="sxs-lookup"><span data-stu-id="495ff-140">But the purpose of integration tests is to confirm that the system works as expected with these systems, so for integration testing you do not use fakes or mock objects.</span></span> <span data-ttu-id="495ff-141">Místo toho zahrnete infrastrukturu, jako je přístup k databázi nebo vyvolání služby z jiných služeb.</span><span class="sxs-lookup"><span data-stu-id="495ff-141">Instead, you include the infrastructure, like database access or service invocation from other services.</span></span>

<span data-ttu-id="495ff-142">Vzhledem k tomu, že integrační testy vykonávají větší segmenty kódu než testy částí a protože integrační testy spoléhají na prvky infrastruktury, mají tendenci být řádově pomalejší než testy částí.</span><span class="sxs-lookup"><span data-stu-id="495ff-142">Because integration tests exercise larger segments of code than unit tests, and because integration tests rely on infrastructure elements, they tend to be orders of magnitude slower than unit tests.</span></span> <span data-ttu-id="495ff-143">Proto je vhodné omezit, kolik integračních testů napíšete a spustíte.</span><span class="sxs-lookup"><span data-stu-id="495ff-143">Thus, it is a good idea to limit how many integration tests you write and run.</span></span>

<span data-ttu-id="495ff-144">ASP.NET Core obsahuje vestavěný testovací webový hostitel, který lze použít ke zpracování požadavků HTTP bez zatížení sítě, což znamená, že tyto testy můžete spustit rychleji než při použití skutečného webového hostitele.</span><span class="sxs-lookup"><span data-stu-id="495ff-144">ASP.NET Core includes a built-in test web host that can be used to handle HTTP requests without network overhead, meaning that you can run those tests faster than when using a real web host.</span></span> <span data-ttu-id="495ff-145">Testovací webový hostitel (TestServer) je k dispozici v součásti NuGet jako Microsoft.AspNetCore.TestHost.</span><span class="sxs-lookup"><span data-stu-id="495ff-145">The test web host (TestServer) is available in a NuGet component as Microsoft.AspNetCore.TestHost.</span></span> <span data-ttu-id="495ff-146">Lze jej přidat do projektů testů integrace a použít k hostování ASP.NET základních aplikací.</span><span class="sxs-lookup"><span data-stu-id="495ff-146">It can be added to integration test projects and used to host ASP.NET Core applications.</span></span>

<span data-ttu-id="495ff-147">Jak můžete vidět v následujícím kódu, při vytváření testů integrace pro ASP.NET řadiče Core, můžete vytvořit instanci řadiče prostřednictvím testovacího hostitele.</span><span class="sxs-lookup"><span data-stu-id="495ff-147">As you can see in the following code, when you create integration tests for ASP.NET Core controllers, you instantiate the controllers through the test host.</span></span> <span data-ttu-id="495ff-148">To je srovnatelné s požadavkem HTTP, ale běží rychleji.</span><span class="sxs-lookup"><span data-stu-id="495ff-148">This is comparable to an HTTP request, but it runs faster.</span></span>

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

#### <a name="additional-resources"></a><span data-ttu-id="495ff-149">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="495ff-149">Additional resources</span></span>

- <span data-ttu-id="495ff-150">**Steva Smithe. Testovací řadiče** (ASP.NET Core) </span><span class="sxs-lookup"><span data-stu-id="495ff-150">**Steve Smith. Testing controllers** (ASP.NET Core) </span></span>\
    [https://docs.microsoft.com/aspnet/core/mvc/controllers/testing](/aspnet/core/mvc/controllers/testing)

- <span data-ttu-id="495ff-151">**Steva Smithe. Testování integrace** (ASP.NET jádro) </span><span class="sxs-lookup"><span data-stu-id="495ff-151">**Steve Smith. Integration testing** (ASP.NET Core) </span></span>\
    [https://docs.microsoft.com/aspnet/core/test/integration-tests](/aspnet/core/test/integration-tests)

- <span data-ttu-id="495ff-152">**Testování částí v rozhraní .NET Core pomocí dotnetového testu** </span><span class="sxs-lookup"><span data-stu-id="495ff-152">**Unit testing in .NET Core using dotnet test** </span></span>\
    [https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test](../../../core/testing/unit-testing-with-dotnet-test.md)

- <span data-ttu-id="495ff-153">**xUnit.net**.</span><span class="sxs-lookup"><span data-stu-id="495ff-153">**xUnit.net**.</span></span> <span data-ttu-id="495ff-154">Oficiální stránky.</span><span class="sxs-lookup"><span data-stu-id="495ff-154">Official site.</span></span> \
    <https://xunit.github.io/>

- <span data-ttu-id="495ff-155">**Základy testu částí.**</span><span class="sxs-lookup"><span data-stu-id="495ff-155">**Unit Test Basics.**</span></span> \
    [https://docs.microsoft.com/visualstudio/test/unit-test-basics](/visualstudio/test/unit-test-basics)

- <span data-ttu-id="495ff-156">**Moq**.</span><span class="sxs-lookup"><span data-stu-id="495ff-156">**Moq**.</span></span> <span data-ttu-id="495ff-157">úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="495ff-157">GitHub repo.</span></span> \
    <https://github.com/moq/moq>

- <span data-ttu-id="495ff-158">**NUnit**.</span><span class="sxs-lookup"><span data-stu-id="495ff-158">**NUnit**.</span></span> <span data-ttu-id="495ff-159">Oficiální stránky.</span><span class="sxs-lookup"><span data-stu-id="495ff-159">Official site.</span></span> \
    <https://www.nunit.org/>

### <a name="implementing-service-tests-on-a-multi-container-application"></a><span data-ttu-id="495ff-160">Implementace servisních testů v aplikaci s více kontejnery</span><span class="sxs-lookup"><span data-stu-id="495ff-160">Implementing service tests on a multi-container application</span></span>

<span data-ttu-id="495ff-161">Jak již bylo uvedeno dříve, při testování aplikací s více kontejnery, všechny mikroslužby musí být spuštěnv rámci clusteru hostitele Dockeru nebo kontejneru.</span><span class="sxs-lookup"><span data-stu-id="495ff-161">As noted earlier, when you test multi-container applications, all the microservices need to be running within the Docker host or container cluster.</span></span> <span data-ttu-id="495ff-162">End-to-end testy služeb, které zahrnují více operací zahrnujících několik mikroslužeb vyžadují nasazení a spuštění celé aplikace v hostiteli Dockeru spuštěním docker-compose up (nebo srovnatelný mechanismus, pokud používáte orchestrator).</span><span class="sxs-lookup"><span data-stu-id="495ff-162">End-to-end service tests that include multiple operations involving several microservices require you to deploy and start the whole application in the Docker host by running docker-compose up (or a comparable mechanism if you are using an orchestrator).</span></span> <span data-ttu-id="495ff-163">Jakmile je spuštěna celá aplikace a všechny její služby, můžete provést komplexní integrační a funkční testy.</span><span class="sxs-lookup"><span data-stu-id="495ff-163">Once the whole application and all its services is running, you can execute end-to-end integration and functional tests.</span></span>

<span data-ttu-id="495ff-164">Existuje několik přístupů, které můžete použít.</span><span class="sxs-lookup"><span data-stu-id="495ff-164">There are a few approaches you can use.</span></span> <span data-ttu-id="495ff-165">V souboru docker-compose.yml, který používáte k nasazení aplikace na úrovni řešení, můžete rozbalit vstupní bod a použít [test dotnet](../../../core/tools/dotnet-test.md).</span><span class="sxs-lookup"><span data-stu-id="495ff-165">In the docker-compose.yml file that you use to deploy the application at the solution level you can expand the entry point to use [dotnet test](../../../core/tools/dotnet-test.md).</span></span> <span data-ttu-id="495ff-166">Můžete také použít jiný soubor compose, který by spustit testy v obrázku, který cílí.</span><span class="sxs-lookup"><span data-stu-id="495ff-166">You can also use another compose file that would run your tests in the image you are targeting.</span></span> <span data-ttu-id="495ff-167">Pomocí jiného souboru compose pro integrační testy, které zahrnuje vaše mikroslužeb a databází na kontejnery, můžete se ujistit, že související data je vždy obnovit původní stav před spuštěním testů.</span><span class="sxs-lookup"><span data-stu-id="495ff-167">By using another compose file for integration tests that includes your microservices and databases on containers, you can make sure that the related data is always reset to its original state before running the tests.</span></span>

<span data-ttu-id="495ff-168">Jakmile je aplikace pro komponovat spuštěna, můžete využít zarážky a výjimky, pokud používáte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="495ff-168">Once the compose application is up and running, you can take advantage of breakpoints and exceptions if you are running Visual Studio.</span></span> <span data-ttu-id="495ff-169">Nebo můžete spustit testy integrace automaticky v kanálu CI ve službě Azure DevOps Services nebo v jakémkoli jiném systému CI/CD, který podporuje kontejnery Dockeru.</span><span class="sxs-lookup"><span data-stu-id="495ff-169">Or you can run the integration tests automatically in your CI pipeline in Azure DevOps Services or any other CI/CD system that supports Docker containers.</span></span>

## <a name="testing-in-eshoponcontainers"></a><span data-ttu-id="495ff-170">Testování v eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="495ff-170">Testing in eShopOnContainers</span></span>

<span data-ttu-id="495ff-171">Testy referenční aplikace (eShopOnContainers) byly nedávno restrukturalizovány a nyní existují čtyři kategorie:</span><span class="sxs-lookup"><span data-stu-id="495ff-171">The reference application (eShopOnContainers) tests were recently restructured and now there are four categories:</span></span>

1. <span data-ttu-id="495ff-172">**Testy částí,** jen obyčejné staré pravidelné testy částí, obsažené v **{MicroserviceName}. Projekty UnitTests**</span><span class="sxs-lookup"><span data-stu-id="495ff-172">**Unit** tests, just plain old regular unit tests, contained in the **{MicroserviceName}.UnitTests** projects</span></span>

2. <span data-ttu-id="495ff-173">**Mikroslužby funkční/integrační testy**, s testovacích případů zahrnující infrastrukturu pro každou mikroslužbu, ale izolované od ostatních a jsou obsaženy v **{MicroserviceName}. FunctionalTests** projekty.</span><span class="sxs-lookup"><span data-stu-id="495ff-173">**Microservice functional/integration tests**, with test cases involving the infrastructure for each microservice but isolated from the others and are contained in the **{MicroserviceName}.FunctionalTests** projects.</span></span>

3. <span data-ttu-id="495ff-174">**Testy funkčnosti/integrace aplikace**, které se zaměřují na integraci mikroslužeb, s testovacích případů, které vyvíjejí několik mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="495ff-174">**Application functional/integration tests**, which focus on microservices integration, with test cases that exert several microservices.</span></span> <span data-ttu-id="495ff-175">Tyto testy jsou umístěny v projektu **Application.FunctionalTests**.</span><span class="sxs-lookup"><span data-stu-id="495ff-175">These tests are located in project **Application.FunctionalTests**.</span></span>

<span data-ttu-id="495ff-176">Testování jednotky a integrace na mikroslužbu jsou obsaženy v testovací složce v každé mikroslužbě a aplikace zatížení testy jsou obsaženy pod testovací složky ve složce řešení, jak je znázorněno na obrázku 6-25.</span><span class="sxs-lookup"><span data-stu-id="495ff-176">Unit and integration test per microservice are contained in a test folder in each microservice and Application a Load tests are contained under the test folder in the solution folder, as shown in Figure 6-25.</span></span>

![Snímek obrazovky v VS s upozorněním na některé testovací projekty v řešení.](./media/test-aspnet-core-services-web-apps/eshoponcontainers-test-folder-structure.png)

<span data-ttu-id="495ff-178">**Obrázek 6-25**.</span><span class="sxs-lookup"><span data-stu-id="495ff-178">**Figure 6-25**.</span></span> <span data-ttu-id="495ff-179">Testování struktury složek v kontejnerech eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="495ff-179">Test folder structure in eShopOnContainers</span></span>

<span data-ttu-id="495ff-180">Mikroslužby a testy funkce/integrace aplikací jsou spuštěny z visual studia pomocí pravidelné testy runner, ale nejprve je třeba spustit požadované služby infrastruktury pomocí sady docker-compose souborů obsažených ve složce test řešení:</span><span class="sxs-lookup"><span data-stu-id="495ff-180">Microservice and Application functional/integration tests are run from Visual Studio, using the regular tests runner, but first you need to start the required infrastructure services, by means of a set of docker-compose files contained in the solution test folder:</span></span>

<span data-ttu-id="495ff-181">**docker-compose-test.yml**</span><span class="sxs-lookup"><span data-stu-id="495ff-181">**docker-compose-test.yml**</span></span>

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

<span data-ttu-id="495ff-182">**docker-compose-test.override.yml**</span><span class="sxs-lookup"><span data-stu-id="495ff-182">**docker-compose-test.override.yml**</span></span>

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

<span data-ttu-id="495ff-183">Chcete-li spustit testy funkčnosti/integrace, musíte nejprve spustit tento příkaz ze složky testu řešení:</span><span class="sxs-lookup"><span data-stu-id="495ff-183">So, to run the functional/integration tests you must first run this command, from the solution test folder:</span></span>

```console
docker-compose -f docker-compose-test.yml -f docker-compose-test.override.yml up
```

<span data-ttu-id="495ff-184">Jak můžete vidět, tyto soubory docker-compose pouze spustit Redis, RabbitMQ, SQL Server a MongoDB mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="495ff-184">As you can see, these docker-compose files only start the Redis, RabbitMQ, SQL Server and MongoDB microservices.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="495ff-185">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="495ff-185">Additional resources</span></span>

- <span data-ttu-id="495ff-186">**Testuje soubor README** na úložišti eShopOnContainers na GitHubu </span><span class="sxs-lookup"><span data-stu-id="495ff-186">**Tests README file** on the eShopOnContainers repo on GitHub </span></span>\
    <https://github.com/dotnet-architecture/eShopOnContainers/tree/dev/test>

- <span data-ttu-id="495ff-187">**Načtení testů souborreadme** na eShopOnContainers repo na GitHub </span><span class="sxs-lookup"><span data-stu-id="495ff-187">**Load tests README file** on the eShopOnContainers repo on GitHub </span></span>\
    <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/test/ServicesTests/LoadTest/>

> [!div class="step-by-step"]
> <span data-ttu-id="495ff-188">[Předchozí](subscribe-events.md)
> [další](background-tasks-with-ihostedservice.md)</span><span class="sxs-lookup"><span data-stu-id="495ff-188">[Previous](subscribe-events.md)
[Next](background-tasks-with-ihostedservice.md)</span></span>
