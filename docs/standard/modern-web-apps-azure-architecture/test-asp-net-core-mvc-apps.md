---
title: ASP.NET Core MVC testování aplikace
description: Navrhování moderních webových aplikací pomocí ASP.NET Core a Azure | Test ASP.NET Core MVC aplikace
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 06d2b576e70afb904683ca1a182c6e061faabf79
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663830"
---
# <a name="test-aspnet-core-mvc-apps"></a><span data-ttu-id="81091-103">ASP.NET Core MVC testování aplikace</span><span class="sxs-lookup"><span data-stu-id="81091-103">Test ASP.NET Core MVC apps</span></span>

> <span data-ttu-id="81091-104">*"Pokud se vám testování produktu, pravděpodobně vaši zákazníci nebudou, jako je a otestovat ho, buď."*</span><span class="sxs-lookup"><span data-stu-id="81091-104">*"If you don't like unit testing your product, most likely your customers won't like to test it, either."*</span></span>
 > <span data-ttu-id="81091-105">\_-Anonymní-</span><span class="sxs-lookup"><span data-stu-id="81091-105">\_- Anonymous-</span></span>

<span data-ttu-id="81091-106">Software jakékoli složitosti, může selhat neočekávaným způsobem v reakci na změny.</span><span class="sxs-lookup"><span data-stu-id="81091-106">Software of any complexity can fail in unexpected ways in response to changes.</span></span> <span data-ttu-id="81091-107">Proto testování po provedení změn je potřeba u všech aplikací nejvíce triviální (nebo nejméně důležité).</span><span class="sxs-lookup"><span data-stu-id="81091-107">Thus, testing after making changes is required for all but the most trivial (or least critical) applications.</span></span> <span data-ttu-id="81091-108">Manuální testování je nejpomalejší, nejméně spolehlivé a nejdražší způsob testování softwaru.</span><span class="sxs-lookup"><span data-stu-id="81091-108">Manual testing is the slowest, least reliable, most expensive way to test software.</span></span> <span data-ttu-id="81091-109">Bohužel Pokud aplikace nejsou navržena jako možností intenzivního testování, může být k dispozici pouze prostředky.</span><span class="sxs-lookup"><span data-stu-id="81091-109">Unfortunately, if applications aren't designed to be testable, it can be the only means available.</span></span> <span data-ttu-id="81091-110">Aplikace vytvořené po architektonických principů nastíněny v [kapitoly 4](architectural-principles.md) by měl být jednotka možností intenzivního testování a aplikace ASP.NET Core podporují automatizované integraci a také funkční testování.</span><span class="sxs-lookup"><span data-stu-id="81091-110">Applications written following the architectural principles laid out in [chapter 4](architectural-principles.md) should be unit testable, and ASP.NET Core applications support automated integration and functional testing as well.</span></span>

## <a name="kinds-of-automated-tests"></a><span data-ttu-id="81091-111">Druhy automatizované testy</span><span class="sxs-lookup"><span data-stu-id="81091-111">Kinds of automated tests</span></span>

<span data-ttu-id="81091-112">Existují různé druhy automatizovaných testů pro softwarové aplikace.</span><span class="sxs-lookup"><span data-stu-id="81091-112">There are many kinds of automated tests for software applications.</span></span> <span data-ttu-id="81091-113">Nejjednodušší, nejnižší úrovni test je testování částí.</span><span class="sxs-lookup"><span data-stu-id="81091-113">The simplest, lowest level test is the unit test.</span></span> <span data-ttu-id="81091-114">Mírně vyšší úrovně jsou integrační testy a funkčních testů.</span><span class="sxs-lookup"><span data-stu-id="81091-114">At a slightly higher level there are integration tests and functional tests.</span></span> <span data-ttu-id="81091-115">Jiné druhy testů, jako jsou testy uživatelského rozhraní, zátěžové testy, zátěžové testy a orientačních testů jsou nad rámec tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="81091-115">Other kinds of tests, like UI tests, load tests, stress tests, and smoke tests, are beyond the scope of this document.</span></span>

### <a name="unit-tests"></a><span data-ttu-id="81091-116">Testování částí</span><span class="sxs-lookup"><span data-stu-id="81091-116">Unit tests</span></span>

<span data-ttu-id="81091-117">Test jednotky testů jedné části vaší aplikace logiky.</span><span class="sxs-lookup"><span data-stu-id="81091-117">A unit test tests a single part of your application's logic.</span></span> <span data-ttu-id="81091-118">Jeden je podrobnější popis uvedením některé z akcí, které není.</span><span class="sxs-lookup"><span data-stu-id="81091-118">One can further describe it by listing some of the things that it isn't.</span></span> <span data-ttu-id="81091-119">Testování částí nepodporuje testování, jak váš kód funguje bez závislostí nebo infrastruktury –, který je co integrační testy jsou určené pro.</span><span class="sxs-lookup"><span data-stu-id="81091-119">A unit test doesn't test how your code works with dependencies or infrastructure – that's what integration tests are for.</span></span> <span data-ttu-id="81091-120">Jednotkový test není testovací rozhraní, které váš kód psaní vycházelo – by měl předpokládat ho funguje nebo, pokud pro vás není oznámit chybu a kód alternativní řešení.</span><span class="sxs-lookup"><span data-stu-id="81091-120">A unit test doesn't test the framework your code is written on – you should assume it works or, if you find it doesn't, file a bug and code a workaround.</span></span> <span data-ttu-id="81091-121">Testování částí spouští kompletně v paměti a v procesu.</span><span class="sxs-lookup"><span data-stu-id="81091-121">A unit test runs completely in memory and in process.</span></span> <span data-ttu-id="81091-122">Nelze komunikovat pomocí systému souborů, sítě nebo v databázi.</span><span class="sxs-lookup"><span data-stu-id="81091-122">It doesn't communicate with the file system, the network, or a database.</span></span> <span data-ttu-id="81091-123">Testy jednotek by měl pouze testování kódu.</span><span class="sxs-lookup"><span data-stu-id="81091-123">Unit tests should only test your code.</span></span>

<span data-ttu-id="81091-124">Testy jednotek, tím, že fakt, že se test pouze jednu jednotku kódu, nemá žádné externí závislosti, by se měl spustit velmi rychle.</span><span class="sxs-lookup"><span data-stu-id="81091-124">Unit tests, by virtue of the fact that they test only a single unit of your code, with no external dependencies, should execute extremely quickly.</span></span> <span data-ttu-id="81091-125">Proto byste měli spustit testovací sady stovky testů jednotek za pár sekund.</span><span class="sxs-lookup"><span data-stu-id="81091-125">Thus, you should be able to run test suites of hundreds of unit tests in a few seconds.</span></span> <span data-ttu-id="81091-126">Spuštění je často, v ideálním případě před každou push do úložiště správy sdílené zdroje a jistě s každou automatické sestavení na vašem serveru sestavení.</span><span class="sxs-lookup"><span data-stu-id="81091-126">Run them frequently, ideally before every push to a shared source control repository, and certainly with every automated build on your build server.</span></span>

### <a name="integration-tests"></a><span data-ttu-id="81091-127">Integrační testy</span><span class="sxs-lookup"><span data-stu-id="81091-127">Integration tests</span></span>

<span data-ttu-id="81091-128">I když je vhodné k zapouzdření kódu, který komunikuje s infrastruktury, jako jsou databáze nebo souborové systémy, budete mít stále některé tento kód a budete pravděpodobně chtít otestovat.</span><span class="sxs-lookup"><span data-stu-id="81091-128">Although it's a good idea to encapsulate your code that interacts with infrastructure like databases and file systems, you will still have some of that code, and you will probably want to test it.</span></span> <span data-ttu-id="81091-129">Kromě toho byste měli ověřit, že váš kód vrstvy pracovat jako očekáváte, že když jsou zcela přeložit závislostí aplikace.</span><span class="sxs-lookup"><span data-stu-id="81091-129">Additionally, you should verify that your code's layers interact as you expect when your application's dependencies are fully resolved.</span></span> <span data-ttu-id="81091-130">To odpovídá testů integrace.</span><span class="sxs-lookup"><span data-stu-id="81091-130">This is the responsibility of integration tests.</span></span> <span data-ttu-id="81091-131">Integrační testy mají být pomalejší a obtížnější než testování částí, nastavit, protože jsou často závislé na vnější závislosti a infrastrukturou.</span><span class="sxs-lookup"><span data-stu-id="81091-131">Integration tests tend to be slower and more difficult to set up than unit tests, because they often depend on external dependencies and infrastructure.</span></span> <span data-ttu-id="81091-132">Proto byste se měli vyhnout testování věcí, které by mohly být testovány s testy jednotek v testech integrace.</span><span class="sxs-lookup"><span data-stu-id="81091-132">Thus, you should avoid testing things that could be tested with unit tests in integration tests.</span></span> <span data-ttu-id="81091-133">Pokud daný scénář můžete otestovat pomocí testování částí, měli byste otestovat pomocí testování částí.</span><span class="sxs-lookup"><span data-stu-id="81091-133">If you can test a given scenario with a unit test, you should test it with a unit test.</span></span> <span data-ttu-id="81091-134">Pokud není možné, zvažte použití o test integrace.</span><span class="sxs-lookup"><span data-stu-id="81091-134">If you can't, then consider using an integration test.</span></span>

<span data-ttu-id="81091-135">Integrační testy se mají často mnohem složitější nastavení a jejich vyřazování z provozu postupy než testování částí.</span><span class="sxs-lookup"><span data-stu-id="81091-135">Integration tests will often have more complex setup and teardown procedures than unit tests.</span></span> <span data-ttu-id="81091-136">Například o test integrace, který odkazuje na databázi aplikace skutečný potřebovat způsob, jak vrátit databázi do známého stavu před jednotlivých testovacích běhů.</span><span class="sxs-lookup"><span data-stu-id="81091-136">For example, an integration test that goes against an actual database will need a way to return the database to a known state before each test run.</span></span> <span data-ttu-id="81091-137">Jak se přidávají nové testy a schéma databáze produkční vyvíjí, tyto testovací skripty bodech zvětšit velikost a složitost.</span><span class="sxs-lookup"><span data-stu-id="81091-137">As new tests are added and the production database schema evolves, these test scripts will tend to grow in size and complexity.</span></span> <span data-ttu-id="81091-138">V mnoha velkých systémů je nepraktické spustit úplné sady testů integrace na vývojářské pracovní stanice před vrácením se změnami do správy sdílených zdrojů.</span><span class="sxs-lookup"><span data-stu-id="81091-138">In many large systems, it is impractical to run full suites of integration tests on developer workstations before checking in changes to shared source control.</span></span> <span data-ttu-id="81091-139">V těchto případech se může spustit testy integrace na serveru sestavení.</span><span class="sxs-lookup"><span data-stu-id="81091-139">In these cases, integration tests may be run on a build server.</span></span>

<span data-ttu-id="81091-140">Implementace třídy LocalFileImageService implementuje logiku pro načítání a vrátí počet bajtů soubor obrázku z konkrétní složky zadané id:</span><span class="sxs-lookup"><span data-stu-id="81091-140">The LocalFileImageService implementation class implements the logic for fetching and returning the bytes of an image file from a particular folder given an id:</span></span>

```csharp
public class LocalFileImageService : IImageService
{
    private readonly IHostingEnvironment _env;
    public LocalFileImageService(IHostingEnvironment env)
    {
        _env = env;
    }
    public byte[] GetImageBytesById(int id)
    {
        try
        {
            var contentRoot = _env.ContentRootPath + "//Pics";
            var path = Path.Combine(contentRoot, id + ".png");
            return File.ReadAllBytes(path);
        }
        catch (FileNotFoundException ex)
        {
            throw new CatalogImageMissingException(ex);
        }
    }
}
```

### <a name="functional-tests"></a><span data-ttu-id="81091-141">Funkční testy</span><span class="sxs-lookup"><span data-stu-id="81091-141">Functional tests</span></span>

<span data-ttu-id="81091-142">Integrační testy se zapisují z pohledu vývojáře, chcete-li ověřit, že některé součásti systému správně fungovat společně.</span><span class="sxs-lookup"><span data-stu-id="81091-142">Integration tests are written from the perspective of the developer, to verify that some components of the system work correctly together.</span></span> <span data-ttu-id="81091-143">Funkční testy se zapisují z pohledu uživatele a ověřte správnost podle svých požadavků na systém.</span><span class="sxs-lookup"><span data-stu-id="81091-143">Functional tests are written from the perspective of the user, and verify the correctness of the system based on its requirements.</span></span> <span data-ttu-id="81091-144">Následující úryvek nabízí užitečné přirovnání jak uvažovat o funkčních testů v porovnání s testy jednotek:</span><span class="sxs-lookup"><span data-stu-id="81091-144">The following excerpt offers a useful analogy for how to think about functional tests, compared to unit tests:</span></span>

> <span data-ttu-id="81091-145">"V mnoha případech vývoj systému je připodobnit sestavování z domu.</span><span class="sxs-lookup"><span data-stu-id="81091-145">"Many times the development of a system is likened to the building of a house.</span></span> <span data-ttu-id="81091-146">Zatímco tato analogie není úplně správná, teď ho můžeme rozšířit pro účely vysvětlení rozdílu mezi částí a funkčních testů.</span><span class="sxs-lookup"><span data-stu-id="81091-146">While this analogy isn't quite correct, we can extend it for the purposes of understanding the difference between unit and functional tests.</span></span> <span data-ttu-id="81091-147">Testování jednotek je obdobou vytváření inspektoru konstrukce společnosti organizace.</span><span class="sxs-lookup"><span data-stu-id="81091-147">Unit testing is analogous to a building inspector visiting a house's construction site.</span></span> <span data-ttu-id="81091-148">Má se zaměřuje na různých interních systémů house základ vypracování, elektrický, domovních instalací a tak dále.</span><span class="sxs-lookup"><span data-stu-id="81091-148">He is focused on the various internal systems of the house, the foundation, framing, electrical, plumbing, and so on.</span></span> <span data-ttu-id="81091-149">Má zajišťuje (testů), součástí dům bude fungovat správně a bezpečně, to znamená, že splňují sestavování kódu.</span><span class="sxs-lookup"><span data-stu-id="81091-149">He ensures (tests) that the parts of the house will work correctly and safely, that is, meet the building code.</span></span> <span data-ttu-id="81091-150">Funkční testy v tomto scénáři jsou podobná na základě návštěvě tohoto webu stejné konstrukce.</span><span class="sxs-lookup"><span data-stu-id="81091-150">Functional tests in this scenario are analogous to the homeowner visiting this same construction site.</span></span> <span data-ttu-id="81091-151">Má se předpokládá, že se bude odpovídajícím způsobem chovat interních systémů, inspektor vytváření fungování jeho úlohy.</span><span class="sxs-lookup"><span data-stu-id="81091-151">He assumes that the internal systems will behave appropriately, that the building inspector is performing his task.</span></span> <span data-ttu-id="81091-152">Základě se zaměřuje na co je třeba to je toto porušuje.</span><span class="sxs-lookup"><span data-stu-id="81091-152">The homeowner is focused on what it will be like to live in this house.</span></span> <span data-ttu-id="81091-153">Problémem vzhledu dům, jsou různé místnosti pohodlné velikost, nemá dům podle potřeb vaší rodiny, jsou windows nevhodná situace pro zachycení sun ráno.</span><span class="sxs-lookup"><span data-stu-id="81091-153">He is concerned with how the house looks, are the various rooms a comfortable size, does the house fit the family's needs, are the windows in a good spot to catch the morning sun.</span></span> <span data-ttu-id="81091-154">Na dům provádí základě funkčních testů.</span><span class="sxs-lookup"><span data-stu-id="81091-154">The homeowner is performing functional tests on the house.</span></span> <span data-ttu-id="81091-155">Má pohledu uživatele.</span><span class="sxs-lookup"><span data-stu-id="81091-155">He has the user's perspective.</span></span> <span data-ttu-id="81091-156">Inspektor sestavení na dům provádí testy jednotek.</span><span class="sxs-lookup"><span data-stu-id="81091-156">The building inspector is performing unit tests on the house.</span></span> <span data-ttu-id="81091-157">Má Tvůrce perspektivy."</span><span class="sxs-lookup"><span data-stu-id="81091-157">He has the builder's perspective."</span></span>

<span data-ttu-id="81091-158">Zdroj: [Testování a funkční testy jednotek](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)</span><span class="sxs-lookup"><span data-stu-id="81091-158">Source: [Unit Testing versus Functional Tests](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)</span></span>

<span data-ttu-id="81091-159">Jsem rádi o tom, že "jako vývojáři služeb při selhání dvěma způsoby: jsme integrovali věc nesprávné nebo integrujeme špatného."</span><span class="sxs-lookup"><span data-stu-id="81091-159">I'm fond of saying "As developers, we fail in two ways: we build the thing wrong, or we build the wrong thing."</span></span> <span data-ttu-id="81091-160">Testování částí zajišťuje, že vytváříte věc, kterou vpravo; funkční testy – Ujistěte se, že vytváříte správné věci.</span><span class="sxs-lookup"><span data-stu-id="81091-160">Unit tests ensure you are building the thing right; functional tests ensure you are building the right thing.</span></span>

<span data-ttu-id="81091-161">Vzhledem k tomu, že funkční testy pracovat na úrovni systému, můžou vyžadovat jistou automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="81091-161">Since functional tests operate at the system level, they may require some degree of UI automation.</span></span> <span data-ttu-id="81091-162">Stejně jako integrační testy obvykle fungují s nějaký druh také infrastrukturu pro testování.</span><span class="sxs-lookup"><span data-stu-id="81091-162">Like integration tests, they usually work with some kind of test infrastructure as well.</span></span> <span data-ttu-id="81091-163">Díky tomu je pomalejší a křehký více než testy jednotky a integrace.</span><span class="sxs-lookup"><span data-stu-id="81091-163">This makes them slower and more brittle than unit and integration tests.</span></span> <span data-ttu-id="81091-164">Měli byste mít jenom tolik funkčních testů, jak potřebujete být jistí, systému se nechová podle očekávání uživatelů.</span><span class="sxs-lookup"><span data-stu-id="81091-164">You should have only as many functional tests as you need to be confident the system is behaving as users expect.</span></span>

### <a name="testing-pyramid"></a><span data-ttu-id="81091-165">Testování pyramidového diagramu</span><span class="sxs-lookup"><span data-stu-id="81091-165">Testing Pyramid</span></span>

<span data-ttu-id="81091-166">Martina Fowlera napsal o testování pyramidového diagramu, které příklad v obrázek 9-1.</span><span class="sxs-lookup"><span data-stu-id="81091-166">Martin Fowler wrote about the testing pyramid, an example of which is shown in Figure 9-1.</span></span>

![](./media/image9-1.png)

<span data-ttu-id="81091-167">Obrázek 9-1 testování pyramidového diagramu</span><span class="sxs-lookup"><span data-stu-id="81091-167">Figure 9-1 Testing Pyramid</span></span>

<span data-ttu-id="81091-168">Různé vrstvy pyramidy a jejich relativní velikosti představují různé druhy testů a kolik měli byste psát pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="81091-168">The different layers of the pyramid, and their relative sizes, represent different kinds of tests and how many you should write for your application.</span></span> <span data-ttu-id="81091-169">Jak je vidět, doporučujeme mít velký základ testování částí nepodporuje menší vrstvy testů integrace, dokonce i menší vrstvou funkčních testů.</span><span class="sxs-lookup"><span data-stu-id="81091-169">As you can see, the recommendation is to have a large base of unit tests, supported by a smaller layer of integration tests, with an even smaller layer of functional tests.</span></span> <span data-ttu-id="81091-170">Každá vrstva by měl v ideálním případě obsahovat pouze testy, které se nedá adekvátně v nižší vrstvě.</span><span class="sxs-lookup"><span data-stu-id="81091-170">Each layer should ideally only have tests in it that cannot be performed adequately at a lower layer.</span></span> <span data-ttu-id="81091-171">Testování pyramidového diagramu mít na paměti, když se pokoušíte rozhodnout, jaký druh testu, je nutné pro konkrétní scénář.</span><span class="sxs-lookup"><span data-stu-id="81091-171">Keep the testing pyramid in mind when you are trying to decide which kind of test you need for a particular scenario.</span></span>

### <a name="what-to-test"></a><span data-ttu-id="81091-172">Co se má testovat</span><span class="sxs-lookup"><span data-stu-id="81091-172">What to test</span></span>

<span data-ttu-id="81091-173">Běžný problém pro vývojáře, kteří jsou Nezkušený s vytváření automatizovaných testů se chystá s co se má otestovat.</span><span class="sxs-lookup"><span data-stu-id="81091-173">A common problem for developers who are inexperienced with writing automated tests is coming up with what to test.</span></span> <span data-ttu-id="81091-174">Dobrým výchozím bodem je otestovat podmíněnou logiku.</span><span class="sxs-lookup"><span data-stu-id="81091-174">A good starting point is to test conditional logic.</span></span> <span data-ttu-id="81091-175">Kdekoli měl odpovídající metodu s chování, které mění podle údajů zadaných v podmíněném příkazu (if-else, přepnout, atd.), byste měli aktivován alespoň několik testy, které potvrdí správný chování za určitých podmínek.</span><span class="sxs-lookup"><span data-stu-id="81091-175">Anywhere you have a method with behavior that changes based on a conditional statement (if-else, switch, etc.), you should be able to come up at least a couple of tests that confirm the correct behavior for certain conditions.</span></span> <span data-ttu-id="81091-176">Pokud má váš kód chybové stavy, je vhodné k zápisu u minimálně jednoho testu pro "všechno nejlepší cestu" skrze kód (s žádné chyby) a alespoň jeden test pro "sad cesty" (s chybami nebo atypické výsledky) pro potvrzení, že vaše aplikace chová podle očekávání i v případě chyby.</span><span class="sxs-lookup"><span data-stu-id="81091-176">If your code has error conditions, it's good to write at least one test for the "happy path" through the code (with no errors), and at least one test for the "sad path" (with errors or atypical results) to confirm your application behaves as expected in the face of errors.</span></span> <span data-ttu-id="81091-177">A konečně pokuste se zaměřit na testování věcí, které může selhat, místo zaměření na metriky, jako je pokrytí kódu.</span><span class="sxs-lookup"><span data-stu-id="81091-177">Finally, try to focus on testing things that can fail, rather than focusing on metrics like code coverage.</span></span> <span data-ttu-id="81091-178">Další pokrytí kódu je obecně lepší než méně.</span><span class="sxs-lookup"><span data-stu-id="81091-178">More code coverage is better than less, generally.</span></span> <span data-ttu-id="81091-179">Zápis několik více testů velmi náročné a komplexní obchodní – metoda je však obvykle lepší využití času než psaní testů pro automatické vlastnosti pouze ke zlepšení metriky pro pokrytí kódu testu.</span><span class="sxs-lookup"><span data-stu-id="81091-179">However, writing a few more tests of a very complex and business-critical method is usually a better use of time than writing tests for auto-properties just to improve test code coverage metrics.</span></span>

## <a name="organizing-test-projects"></a><span data-ttu-id="81091-180">Uspořádání projektů testování</span><span class="sxs-lookup"><span data-stu-id="81091-180">Organizing test projects</span></span>

<span data-ttu-id="81091-181">Projekty testů lze uspořádat, ale funguje nejlépe za vás.</span><span class="sxs-lookup"><span data-stu-id="81091-181">Test projects can be organized however works best for you.</span></span> <span data-ttu-id="81091-182">Je vhodné oddělit testy podle typu (testování částí, test integrace) a co testují (podle projektu, oboru názvů).</span><span class="sxs-lookup"><span data-stu-id="81091-182">It's a good idea to separate tests by type (unit test, integration test) and by what they are testing (by project, by namespace).</span></span> <span data-ttu-id="81091-183">Ať už toto oddělení se skládá ze složky v rámci jednoho testovacího projektu, nebo více zkušebních projektů, je rozhodnutí o návrhu.</span><span class="sxs-lookup"><span data-stu-id="81091-183">Whether this separation consists of folders within a single test project, or multiple test projects, is a design decision.</span></span> <span data-ttu-id="81091-184">Nejjednodušší je jeden projekt, ale pro velké projekty s mnoho testů, nebo chcete-li snadněji spustit různé sady testů, můžete chtít mít několik různých testovacích projektů.</span><span class="sxs-lookup"><span data-stu-id="81091-184">One project is simplest, but for large projects with many tests, or in order to more easily run different sets of tests, you might want to have several different test projects.</span></span> <span data-ttu-id="81091-185">Mnoho týmů uspořádat projekty testů podle projektu, které testují, který pro aplikace s více než několik projektů může mít za následek velký počet projekty testů, zejména v případě, že se můžete stále rozdělit tyto podle druh testy jsou v každém projektu.</span><span class="sxs-lookup"><span data-stu-id="81091-185">Many teams organize test projects based on the project they are testing, which for applications with more than a few projects can result in a large number of test projects, especially if you still break these down according to what kind of tests are in each project.</span></span> <span data-ttu-id="81091-186">Přístup založený na ohrožení zabezpečení je, aby jeden projekt za druh testu na aplikaci, se složkami v testovacích projektů po označení projektu (a třída) testován.</span><span class="sxs-lookup"><span data-stu-id="81091-186">A compromise approach is to have one project per kind of test, per application, with folders inside the test projects to indicate the project (and class) being tested.</span></span>

<span data-ttu-id="81091-187">Běžným přístupem je uspořádat projekty aplikací v rámci složky "src" a projekty testů aplikace v rámci složky paralelní "testů".</span><span class="sxs-lookup"><span data-stu-id="81091-187">A common approach is to organize the application projects under a ‘src' folder, and the application's test projects under a parallel ‘tests' folder.</span></span> <span data-ttu-id="81091-188">Pokud najdete užitečné této organizace, můžete vytvořit odpovídající složky řešení v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="81091-188">You can create matching solution folders in Visual Studio, if you find this organization useful.</span></span>

![](./media/image9-2.png)

<span data-ttu-id="81091-189">Obrázek 9-2 Test organizace ve vašem řešení</span><span class="sxs-lookup"><span data-stu-id="81091-189">Figure 9-2 Test organization in your solution</span></span>

<span data-ttu-id="81091-190">Můžete použít testovací vámi preferované rozhraní.</span><span class="sxs-lookup"><span data-stu-id="81091-190">You can use whichever test framework you prefer.</span></span> <span data-ttu-id="81091-191">Rozhraní xUnit dobře funguje a co se všechny testy v ASP.NET Core a EF Core jsou napsané v.</span><span class="sxs-lookup"><span data-stu-id="81091-191">The xUnit framework works well and is what all of the ASP.NET Core and EF Core tests are written in.</span></span> <span data-ttu-id="81091-192">V sadě Visual Studio pomocí šablony je znázorněno v obrázek 9-3, nebo z rozhraní příkazového řádku pomocí nové xunit dotnet můžete přidat projekt testů xUnit.</span><span class="sxs-lookup"><span data-stu-id="81091-192">You can add an xUnit test project in Visual Studio using the template shown in Figure 9-3, or from the CLI using dotnet new xunit.</span></span>

![](./media/image9-3.png)

<span data-ttu-id="81091-193">Obrázek 9-3 v sadě Visual Studio přidejte projekt testů xUnit</span><span class="sxs-lookup"><span data-stu-id="81091-193">Figure 9-3 Add an xUnit Test Project in Visual Studio</span></span>

### <a name="test-naming"></a><span data-ttu-id="81091-194">Názvy testů</span><span class="sxs-lookup"><span data-stu-id="81091-194">Test naming</span></span>

<span data-ttu-id="81091-195">Byste měli pojmenovat testů v konzistentní podobě s názvy, které označují, co dělá každého testu.</span><span class="sxs-lookup"><span data-stu-id="81091-195">You should name your tests in a consistent fashion, with names that indicate what each test does.</span></span> <span data-ttu-id="81091-196">Jedním z přístupů, které měl skvělý o úspěšných nasazeních je název testovací třídy podle třídy a metody, které testují.</span><span class="sxs-lookup"><span data-stu-id="81091-196">One approach I've had great success with is to name test classes according to the class and method they are testing.</span></span> <span data-ttu-id="81091-197">Výsledkem je mnoho tříd malý test, ale umožní bylo velmi jasné, co je zodpovědný za každý test.</span><span class="sxs-lookup"><span data-stu-id="81091-197">This results in many small test classes, but it makes it extremely clear what each test is responsible for.</span></span> <span data-ttu-id="81091-198">Pomocí názvu třídy testů nastavení k identifikaci třídy a metody, které má být testována název testovací metody slouží k určení chování testován.</span><span class="sxs-lookup"><span data-stu-id="81091-198">With the test class name set up to identify the class and method to be tested, the test method name can be used to specify the behavior being tested.</span></span> <span data-ttu-id="81091-199">Ty by měly zahrnovat očekávané chování a žádné vstupy nebo předpokladů, které by měl vést k tomuto chování.</span><span class="sxs-lookup"><span data-stu-id="81091-199">This should include the expected behavior and any inputs or assumptions that should yield this behavior.</span></span> <span data-ttu-id="81091-200">Některé příklady názvů testů:</span><span class="sxs-lookup"><span data-stu-id="81091-200">Some example test names:</span></span>

- `CatalogControllerGetImage.CallsImageServiceWithId`

- `CatalogControllerGetImage.LogsWarningGivenImageMissingException`

- `CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess`

- `CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException`

<span data-ttu-id="81091-201">Variace tohoto přístupu končí názvem testovací třídy "By" a mírně změní čas:</span><span class="sxs-lookup"><span data-stu-id="81091-201">A variation of this approach ends each test class name with "Should" and modifies the tense slightly:</span></span>

- <span data-ttu-id="81091-202">`CatalogControllerGetImage`**By měl**`.`**volání**`ImageServiceWithId`</span><span class="sxs-lookup"><span data-stu-id="81091-202">`CatalogControllerGetImage`**Should**`.`**Call**`ImageServiceWithId`</span></span>

- <span data-ttu-id="81091-203">`CatalogControllerGetImage`**By měl**`.`**protokolu**`WarningGivenImageMissingException`</span><span class="sxs-lookup"><span data-stu-id="81091-203">`CatalogControllerGetImage`**Should**`.`**Log**`WarningGivenImageMissingException`</span></span>

<span data-ttu-id="81091-204">Některé týmy najít druhý způsob pojmenování jasnější, ale o něco víc verbose.</span><span class="sxs-lookup"><span data-stu-id="81091-204">Some teams find the second naming approach clearer, though slightly more verbose.</span></span> <span data-ttu-id="81091-205">V každém případě zkuste použít zásady vytváření názvů, který poskytuje podrobné informace o chování testu tak, aby když dojde k selhání jednoho nebo více testů, je zřejmý z jejich názvy, jaké případy, které selhaly.</span><span class="sxs-lookup"><span data-stu-id="81091-205">In any case, try to use a naming convention that provides insight into test behavior, so that when one or more tests fail, it's obvious from their names what cases have failed.</span></span> <span data-ttu-id="81091-206">Vyhněte se pojmenování můžete testy představu o možných, jako je například ControllerTests.Test1, jako ty nabízejí žádnou hodnotu, když se zobrazí ve výsledcích testu.</span><span class="sxs-lookup"><span data-stu-id="81091-206">Avoid naming you tests vaguely, such as ControllerTests.Test1, as these offer no value when you see them in test results.</span></span>

<span data-ttu-id="81091-207">Pokud budete postupovat podle zásady vytváření názvů jako ten výše, který vytvoří mnoho tříd malý test, je vhodné uspořádat ještě více testů pomocí složky a obory názvů.</span><span class="sxs-lookup"><span data-stu-id="81091-207">If you follow a naming convention like the one above that produces many small test classes, it's a good idea to further organize your tests using folders and namespaces.</span></span> <span data-ttu-id="81091-208">Jedním z přístupů k uspořádání testů podle složky, které obsahuje několik testovacích projektů je vidět na obrázku 9-4.</span><span class="sxs-lookup"><span data-stu-id="81091-208">Figure 9-4 shows one approach to organizing tests by folder within several test projects.</span></span>

![](./media/image9-4.png)

<span data-ttu-id="81091-209">**Obrázek 9-4.**</span><span class="sxs-lookup"><span data-stu-id="81091-209">**Figure 9-4.**</span></span> <span data-ttu-id="81091-210">Uspořádání testovacích tříd ve složce založené na třídě testován.</span><span class="sxs-lookup"><span data-stu-id="81091-210">Organizing test classes by folder based on class being tested.</span></span>

<span data-ttu-id="81091-211">Samozřejmě pokud třída konkrétní aplikace má mnoho metod testování (a tedy mnoho testovací třídy), může mít smysl ve složce odpovídající – třída aplikace umístit.</span><span class="sxs-lookup"><span data-stu-id="81091-211">Of course, if a particular application class has many methods being tested (and thus many test classes), it may make sense to place these in a folder corresponding to the application class.</span></span> <span data-ttu-id="81091-212">Toto uspořádání se nijak neliší od jak můžete organizovat soubory do složek, které jinde.</span><span class="sxs-lookup"><span data-stu-id="81091-212">This organization is no different than how you might organize files into folders elsewhere.</span></span> <span data-ttu-id="81091-213">Pokud máte více než tři nebo čtyři související soubory ve složce obsahující mnoho souborů, je často užitečné k přesunutí do své vlastní podsložce.</span><span class="sxs-lookup"><span data-stu-id="81091-213">If you have more than three or four related files in a folder containing many other files, it's often helpful to move them into their own subfolder.</span></span>

## <a name="unit-testing-aspnet-core-apps"></a><span data-ttu-id="81091-214">Aplikace ASP.NET Core pro testování částí</span><span class="sxs-lookup"><span data-stu-id="81091-214">Unit testing ASP.NET Core apps</span></span>

<span data-ttu-id="81091-215">V dobře navržené aplikace ASP.NET Core bude se většina složitost a obchodní logiky zapouzdřeny v obchodní entity a širokou škálu služeb.</span><span class="sxs-lookup"><span data-stu-id="81091-215">In a well-designed ASP.NET Core application, most of the complexity and business logic will be encapsulated in business entities and a variety of services.</span></span> <span data-ttu-id="81091-216">Aplikace ASP.NET Core MVC, s řadiči, filtry, modely viewmodels a zobrazení, by měla vyžadovat velmi málo testování částí.</span><span class="sxs-lookup"><span data-stu-id="81091-216">The ASP.NET Core MVC app itself, with its controllers, filters, viewmodels, and views, should require very few unit tests.</span></span> <span data-ttu-id="81091-217">Většina funkcí danou akci leží mimo samotný metody akce.</span><span class="sxs-lookup"><span data-stu-id="81091-217">Much of the functionality of a given action lies outside the action method itself.</span></span> <span data-ttu-id="81091-218">Testování, zda směrování funguje správně, nebo zpracování globální chyb, není možné efektivně pomocí testování částí.</span><span class="sxs-lookup"><span data-stu-id="81091-218">Testing whether routing works correctly, or global error handling, cannot be done effectively with a unit test.</span></span> <span data-ttu-id="81091-219">Podobně všechny filtry, včetně ověření modelu a ověřování a autorizace filtry, nemůže být testován částí.</span><span class="sxs-lookup"><span data-stu-id="81091-219">Likewise, any filters, including model validation and authentication and authorization filters, cannot be unit tested.</span></span> <span data-ttu-id="81091-220">Bez těchto zdrojů chování by měl být triviálně malé, delegování hromadné svou práci do služby, které můžete testovat nezávisle na kontroler, který používá většina metod akce.</span><span class="sxs-lookup"><span data-stu-id="81091-220">Without these sources of behavior, most action methods should be trivially small, delegating the bulk of their work to services that can be tested independent of the controller that uses them.</span></span>

<span data-ttu-id="81091-221">V některých případech budete muset Refaktorovat kód v pořadí pro testování částí.</span><span class="sxs-lookup"><span data-stu-id="81091-221">Sometimes you'll need to refactor your code in order to unit test it.</span></span> <span data-ttu-id="81091-222">Často to zahrnuje identifikaci abstrakce a využitím vkládání závislostí pro přístup k odběru v kódu, který chcete otestovat, spíše než kódovat infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="81091-222">Frequently this involves identifying abstractions and using dependency injection to access the abstraction in the code you'd like to test, rather than coding directly against infrastructure.</span></span> <span data-ttu-id="81091-223">Zvažte například tuto metodu jednoduché akce pro zobrazení obrázků:</span><span class="sxs-lookup"><span data-stu-id="81091-223">For example, consider this simple action method for displaying images:</span></span>

```csharp
[HttpGet("[controller]/pic/{id}")]
public IActionResult GetImage(int id)
{
    var contentRoot = _env.ContentRootPath + "//Pics";
    var path = Path.Combine(contentRoot, id + ".png");
    Byte[] b = System.IO.File.ReadAllBytes(path);
    return File(b, "image/png");
}
```

<span data-ttu-id="81091-224">Testování tato metoda provádí složité s přímým přístupem je závislá na System.IO.File, kterou používá ke čtení ze systému souborů.</span><span class="sxs-lookup"><span data-stu-id="81091-224">Unit testing this method is made difficult by its direct dependency on System.IO.File, which it uses to read from the file system.</span></span> <span data-ttu-id="81091-225">Toto chování zajistit funguje podle očekávání, ale to skutečné souborech se o test integrace můžete otestovat.</span><span class="sxs-lookup"><span data-stu-id="81091-225">You can test this behavior to ensure it works as expected, but doing so with real files is an integration test.</span></span> <span data-ttu-id="81091-226">Je vhodné poznamenat, nejde jednotku testování této metody směrování – uvidíte, jak na to používat funkční testy za chvíli.</span><span class="sxs-lookup"><span data-stu-id="81091-226">It's worth noting you can't unit test this method's route – you'll see how to do this with a functional test shortly.</span></span>

<span data-ttu-id="81091-227">Pokud nelze přímo Jednotkový test chování systému souborů a nelze otestovat trasu, co má k testování?</span><span class="sxs-lookup"><span data-stu-id="81091-227">If you can't unit test the file system behavior directly, and you can't test the route, what is there to test?</span></span> <span data-ttu-id="81091-228">Po refaktoring provádět testování částí je to možné, může také zjistit některé testovací případy a chybějící chování, jako je zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="81091-228">Well, after refactoring to make unit testing possible, you may discover some test cases and missing behavior, such as error handling.</span></span> <span data-ttu-id="81091-229">Co metodu dělat, když nebyl nalezen soubor?</span><span class="sxs-lookup"><span data-stu-id="81091-229">What does the method do when a file isn't found?</span></span> <span data-ttu-id="81091-230">Co to dělat?</span><span class="sxs-lookup"><span data-stu-id="81091-230">What should it do?</span></span> <span data-ttu-id="81091-231">V tomto příkladu refaktorovaný metoda vypadá například takto:</span><span class="sxs-lookup"><span data-stu-id="81091-231">In this example, the refactored method looks like this:</span></span>

```csharp
[HttpGet("[controller]/pic/{id}")\]
public IActionResult GetImage(int id)
{
    byte[] imageBytes;
    try
    {
        imageBytes = _imageService.GetImageBytesById(id);
    }
    catch (CatalogImageMissingException ex)
    {
        _logger.LogWarning($"No image found for id: {id}");
        return NotFound();
    }
    return File(imageBytes, "image/png");
}
```

<span data-ttu-id="81091-232">\_Protokolovací nástroj a \_obě imageService jsou vloženy jako závislosti.</span><span class="sxs-lookup"><span data-stu-id="81091-232">The \_logger and \_imageService are both injected as dependencies.</span></span> <span data-ttu-id="81091-233">Nyní můžete otestovat, že je předán stejné id, který je předán metodě akce \_imageService, a že výsledný počet bajtů se vrátí jako součást FileResult.</span><span class="sxs-lookup"><span data-stu-id="81091-233">Now you can test that the same id that is passed to the action method is passed to the \_imageService, and that the resulting bytes are returned as part of the FileResult.</span></span> <span data-ttu-id="81091-234">Můžete také otestovat, protokolování chyb dochází podle očekávání, a, pokud chybí bitovou kopii, vrátí se výsledek NotFound za předpokladu, že toto je chování důležité aplikace (to znamená, jenom dočasné kód pro vývojáře, přidá k diagnostice problému).</span><span class="sxs-lookup"><span data-stu-id="81091-234">You can also test that error logging is happening as expected, and that a NotFound result is returned if the image is missing, assuming this is important application behavior (that is, not just temporary code the developer added to diagnose an issue).</span></span> <span data-ttu-id="81091-235">Logika skutečný soubor přesunul do samostatné implementace služby a je rozšířený vrátit výjimku specifické pro aplikaci pro případ chybí soubor.</span><span class="sxs-lookup"><span data-stu-id="81091-235">The actual file logic has moved into a separate implementation service, and has been augmented to return an application-specific exception for the case of a missing file.</span></span> <span data-ttu-id="81091-236">Tato implementace můžete otestovat nezávisle na sobě pomocí o test integrace.</span><span class="sxs-lookup"><span data-stu-id="81091-236">You can test this implementation independently, using an integration test.</span></span>

<span data-ttu-id="81091-237">Ve většině případů budete chtít použít obslužné rutiny globálních výjimek ve vašich kontrolerech, by tak měly být minimální množství logiku v nich a pravděpodobně není vhodné testování částí.</span><span class="sxs-lookup"><span data-stu-id="81091-237">In most cases, you’ll want to use global exception handlers in your controllers, so the amount of logic in them should be minimal and probably not worth unit testing.</span></span> <span data-ttu-id="81091-238">Byste měli dělat většina testování používat funkční testy akce kontroleru a `TestServer` třídy je popsáno níže.</span><span class="sxs-lookup"><span data-stu-id="81091-238">You should do most of your testing of controller actions using functional tests and the `TestServer` class described below.</span></span>

## <a name="integration-testing-aspnet-core-apps"></a><span data-ttu-id="81091-239">Aplikace ASP.NET Core pro testování integrace</span><span class="sxs-lookup"><span data-stu-id="81091-239">Integration testing ASP.NET Core apps</span></span>

<span data-ttu-id="81091-240">Většinu testů integrace do svých aplikací ASP.NET Core by měl testování služeb a jiné implementace typy definované v projektu infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="81091-240">Most of the integration tests in your ASP.NET Core apps should be testing services and other implementation types defined in your Infrastructure project.</span></span> <span data-ttu-id="81091-241">Funkční testy, které spustit pro vaše aplikace spuštěná v hostiteli testů je nejlepší způsob, jak otestovat, že váš projekt ASP.NET Core MVC nepracuje správně.</span><span class="sxs-lookup"><span data-stu-id="81091-241">The best way to test that your ASP.NET Core MVC project is behaving correctly is with functional tests that run against your app running in a test host.</span></span> <span data-ttu-id="81091-242">Příklad o test integrace třídy datového přístupu se zobrazí v části Testování integrace dříve v této kapitole.</span><span class="sxs-lookup"><span data-stu-id="81091-242">An example of an integration test of a data access class is shown in the Integration Testing section earlier in this chapter.</span></span>

## <a name="functional-testing-aspnet-core-apps"></a><span data-ttu-id="81091-243">Funkční testování aplikací ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="81091-243">Functional testing ASP.NET Core apps</span></span>

<span data-ttu-id="81091-244">Pro aplikace ASP.NET Core `TestServer` třída provede funkční testy poměrně snadné k zápisu.</span><span class="sxs-lookup"><span data-stu-id="81091-244">For ASP.NET Core applications, the `TestServer` class makes functional tests fairly easy to write.</span></span> <span data-ttu-id="81091-245">Nakonfigurujete `TestServer` pomocí `WebHostBuilder` přímo (běžným způsobem pro vaše aplikace), nebo se `WebApplicationFactory` typ (k dispozici od verze 2.1).</span><span class="sxs-lookup"><span data-stu-id="81091-245">You configure a `TestServer` using a `WebHostBuilder` directly (as you normally do for your application), or with the `WebApplicationFactory` type (available since version 2.1).</span></span> <span data-ttu-id="81091-246">Doporučujeme co nejpřesněji souhlasit s hostitelem vašeho testu na produkční hostitele tak, že testy budou vykonávat chování podobné co aplikace provádět v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="81091-246">You should try to match your test host to your production host as closely as possible, so your tests will exercise behavior similar to what the app will do in production.</span></span> <span data-ttu-id="81091-247">`WebApplicationFactory` Třída je užitečné pro konfiguraci objekt TestServer ContentRoot, který používá ASP.NET Core najít jako zobrazení statických prostředků.</span><span class="sxs-lookup"><span data-stu-id="81091-247">The `WebApplicationFactory` class is helpful for configuring the TestServer's ContentRoot, which is used by ASP.NET Core to locate static resource like Views.</span></span>

<span data-ttu-id="81091-248">Vytvoříte jednoduchou funkční testy tak, že vytvoříte testovací třídě, která implementuje IClassFixture\<WebApplicationFactory\<TEntry >> kde TEntry je třída při spuštění vaší webové aplikace.</span><span class="sxs-lookup"><span data-stu-id="81091-248">You can create simple functional tests by creating a test class that implements IClassFixture\<WebApplicationFactory\<TEntry>> where TEntry is your web application's Startup class.</span></span> <span data-ttu-id="81091-249">S tímto na místě můžete vytvořit testovací přípravek klienta pomocí metody CreateClient factory pro:</span><span class="sxs-lookup"><span data-stu-id="81091-249">With this in place, your test fixture can create a client using the factory's CreateClient method:</span></span>

```cs
public class BasicWebTests : IClassFixture<WebApplicationFactory<Startup>>
{
    protected readonly HttpClient _client;

    public BaseWebTest(WebApplicationFactory<Startup> factory)
    {
        _client = factory.CreateClient();
    }

    // write tests that use _client
}
```

<span data-ttu-id="81091-250">Často, bude potřeba provést další konfiguraci vašeho webu, před spuštěním každého testu, jako je například konfigurace aplikace pro použití v paměti úložiště dat a pak synchronizace replik indexů aplikace s daty testu.</span><span class="sxs-lookup"><span data-stu-id="81091-250">Frequently, you'll want to perform some additional configuration of your site before each test runs, such as configuring the application to use an in memory data store and then seeding the application with test data.</span></span> <span data-ttu-id="81091-251">Proto byste měli vytvořit vlastní podtřídy WebApplicationFactory\<TEntry > a přepsat její ConfigureWebHost metodu.</span><span class="sxs-lookup"><span data-stu-id="81091-251">To do this, you should create your own subclass of WebApplicationFactory\<TEntry> and override its ConfigureWebHost method.</span></span> <span data-ttu-id="81091-252">Následující příklad je z projektu FunctionalTests eShopOnWeb a slouží jako součást testy na hlavní webové aplikace.</span><span class="sxs-lookup"><span data-stu-id="81091-252">The example below is from the eShopOnWeb FunctionalTests project and is used as part of the tests on the main web application.</span></span>

```cs
using Microsoft.AspNetCore.Hosting;
using Microsoft.AspNetCore.Mvc.Testing;
using Microsoft.EntityFrameworkCore;
using Microsoft.eShopWeb.Infrastructure.Data;
using Microsoft.eShopWeb.Infrastructure.Identity;
using Microsoft.eShopWeb.Web;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Logging;
using System;

namespace Microsoft.eShopWeb.FunctionalTests.Web.Controllers
{
    public class CustomWebApplicationFactory<TStartup>
    : WebApplicationFactory<Startup>
    {
        protected override void ConfigureWebHost(IWebHostBuilder builder)
        {
            builder.ConfigureServices(services =>
            {
                // Create a new service provider.
                var serviceProvider = new ServiceCollection()
                    .AddEntityFrameworkInMemoryDatabase()
                    .BuildServiceProvider();

                // Add a database context (ApplicationDbContext) using an in-memory 
                // database for testing.
                services.AddDbContext<CatalogContext>(options =>
                {
                    options.UseInMemoryDatabase("InMemoryDbForTesting");
                    options.UseInternalServiceProvider(serviceProvider);
                });

                services.AddDbContext<AppIdentityDbContext>(options =>
                {
                    options.UseInMemoryDatabase("Identity");
                    options.UseInternalServiceProvider(serviceProvider);
                });

                // Build the service provider.
                var sp = services.BuildServiceProvider();

                // Create a scope to obtain a reference to the database
                // context (ApplicationDbContext).
                using (var scope = sp.CreateScope())
                {
                    var scopedServices = scope.ServiceProvider;
                    var db = scopedServices.GetRequiredService<CatalogContext>();
                    var loggerFactory = scopedServices.GetRequiredService<ILoggerFactory>();

                    var logger = scopedServices
                        .GetRequiredService<ILogger<CustomWebApplicationFactory<TStartup>>>();

                    // Ensure the database is created.
                    db.Database.EnsureCreated();

                    try
                    {
                        // Seed the database with test data.
                        CatalogContextSeed.SeedAsync(db, loggerFactory).Wait();
                    }
                    catch (Exception ex)
                    {
                        logger.LogError(ex, $"An error occurred seeding the " +
                            "database with test messages. Error: {ex.Message}");
                    }
                }
            });
        }
    }
}
```

<span data-ttu-id="81091-253">Testy můžete využít tuto vlastní WebApplicationFactory tak, že použijete k vytvoření klienta a pak zasílání požadavků na aplikaci pomocí instance tohoto klienta.</span><span class="sxs-lookup"><span data-stu-id="81091-253">Tests can make use of this custom WebApplicationFactory by using it to create a client and then making requests to the application using this client instance.</span></span> <span data-ttu-id="81091-254">Aplikace bude mít nasazený data, která slouží jako část testu kontrolní výrazy.</span><span class="sxs-lookup"><span data-stu-id="81091-254">The application will have data seeded that can be used as part of the test's assertions.</span></span> <span data-ttu-id="81091-255">Následující test ověří, zda domovskou stránku aplikace eShopOnWeb načte správně a obsahuje seznam produktů, která byla přidána k aplikaci jako součást počáteční hodnoty data.</span><span class="sxs-lookup"><span data-stu-id="81091-255">The following test verifies that the home page of the eShopOnWeb application loads correctly and includes a product listing that was added to the application as part of the seed data.</span></span>

```cs
using Microsoft.eShopWeb.FunctionalTests.Web.Controllers;
using Microsoft.eShopWeb.Web;
using System.Net.Http;
using System.Threading.Tasks;
using Xunit;

namespace Microsoft.eShopWeb.FunctionalTests.WebRazorPages
{
    public class HomePageOnGet : IClassFixture<CustomWebApplicationFactory<Startup>>
    {
        public HomePageOnGet(CustomWebApplicationFactory<Startup> factory)
        {
            Client = factory.CreateClient();
        }

        public HttpClient Client { get; }

        [Fact]
        public async Task ReturnsHomePageWithProductListing()
        {
            // Arrange & Act
            var response = await Client.GetAsync("/");
            response.EnsureSuccessStatusCode();
            var stringResponse = await response.Content.ReadAsStringAsync();

            // Assert
            Assert.Contains(".NET Bot Black Sweatshirt", stringResponse);
        }
    }
}
```

<span data-ttu-id="81091-256">Tato funkční testování vykonává úplné ASP.NET Core MVC / zásobníku aplikace Razor Pages, včetně middleware, filtry, vazače, atd., které mohou být na místě.</span><span class="sxs-lookup"><span data-stu-id="81091-256">This functional test exercises the full ASP.NET Core MVC / Razor Pages application stack, including all middleware, filters, binders, etc. that may be in place.</span></span> <span data-ttu-id="81091-257">Ověřuje, že danou trasou ("/") vrátí stavový kód úspěchu očekávané a výstupu protokolu HTML.</span><span class="sxs-lookup"><span data-stu-id="81091-257">It verifies that a given route ("/") returns the expected success status code and HTML output.</span></span> <span data-ttu-id="81091-258">Provádí se bez nastavování skutečné webový server a proto zabraňuje velkou část brittleness, který používá skutečné webového serveru pro účely testování můžete vyzkoušet (například problémy s nastavením brány firewall).</span><span class="sxs-lookup"><span data-stu-id="81091-258">It does so without setting up a real web server, and so avoids much of the brittleness that using a real web server for testing can experience (for example, problems with firewall settings).</span></span> <span data-ttu-id="81091-259">Funkční testy, které spustily TestServer jsou obvykle nižší než integraci a testy jednotek, ale jsou mnohem rychleji než testy, které se spustí v síti k serveru webového testu.</span><span class="sxs-lookup"><span data-stu-id="81091-259">Functional tests that run against TestServer are usually slower than integration and unit tests, but are much faster than tests that would run over the network to a test web server.</span></span> <span data-ttu-id="81091-260">Abyste používali funkční testy k zajištění, že zásobník front-endu vaší aplikace funguje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="81091-260">You should use functional tests to ensure your application's front-end stack is working as expected.</span></span> <span data-ttu-id="81091-261">Tyto testy jsou zvláště užitečné při najít duplicity ve vašich kontrolerech nebo stránky a adresy duplicity přidáním filtrů.</span><span class="sxs-lookup"><span data-stu-id="81091-261">These tests are especially useful when you find duplication in your controllers or pages and you address the duplication by adding filters.</span></span> <span data-ttu-id="81091-262">V ideálním případě by tento refaktoring nedojde ke změně chování aplikace a sadu funkční testy se ověří, že jde o tento případ.</span><span class="sxs-lookup"><span data-stu-id="81091-262">Ideally, this refactoring won't change the behavior of the application, and a suite of functional tests will verify this is the case.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="81091-263">[Předchozí](work-with-data-in-asp-net-core-apps.md)
>[další](development-process-for-azure.md)</span><span class="sxs-lookup"><span data-stu-id="81091-263">[Previous](work-with-data-in-asp-net-core-apps.md)
[Next](development-process-for-azure.md)</span></span>
