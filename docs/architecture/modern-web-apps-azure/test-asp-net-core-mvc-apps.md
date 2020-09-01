---
title: Test ASP.NET Core aplikací MVC
description: Architekt moderních webových aplikací pomocí ASP.NET Core a Azure | Test ASP.NET Core aplikací MVC
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: 947a3bc7da0949781ae89ed74a87edb2637daf73
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89126512"
---
# <a name="test-aspnet-core-mvc-apps"></a><span data-ttu-id="98e6b-103">Test ASP.NET Core aplikací MVC</span><span class="sxs-lookup"><span data-stu-id="98e6b-103">Test ASP.NET Core MVC apps</span></span>

> <span data-ttu-id="98e6b-104">*"Pokud si nejste spokojeni s testováním částí vašeho produktu, pravděpodobně ho vaši zákazníci nechtějí testovat, buď."*</span><span class="sxs-lookup"><span data-stu-id="98e6b-104">*"If you don't like unit testing your product, most likely your customers won't like to test it, either."*</span></span>
 > <span data-ttu-id="98e6b-105">\_Anonymous</span><span class="sxs-lookup"><span data-stu-id="98e6b-105">\_- Anonymous-</span></span>

<span data-ttu-id="98e6b-106">Software jakékoli složitosti může při reakci na změny selhat neočekávaným způsobem.</span><span class="sxs-lookup"><span data-stu-id="98e6b-106">Software of any complexity can fail in unexpected ways in response to changes.</span></span> <span data-ttu-id="98e6b-107">Proto se testování po provedení změn vyžaduje pro všechny, ale nejvíce triviální (nebo nejméně kritické) aplikace.</span><span class="sxs-lookup"><span data-stu-id="98e6b-107">Thus, testing after making changes is required for all but the most trivial (or least critical) applications.</span></span> <span data-ttu-id="98e6b-108">Manuální testování je nejpomalejší, nejméně spolehlivý a nejnákladný způsob testování softwaru.</span><span class="sxs-lookup"><span data-stu-id="98e6b-108">Manual testing is the slowest, least reliable, most expensive way to test software.</span></span> <span data-ttu-id="98e6b-109">Pokud aplikace není navržena tak, aby se testovatelné, může to být pouze to, co je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="98e6b-109">Unfortunately, if applications aren't designed to be testable, it can be the only means available.</span></span> <span data-ttu-id="98e6b-110">Aplikace napsané pro sledování principů architektury stanovených v [kapitole 4](architectural-principles.md) by měly být jednotky testovatelné.</span><span class="sxs-lookup"><span data-stu-id="98e6b-110">Applications written to follow the architectural principles laid out in [chapter 4](architectural-principles.md) should be unit testable.</span></span> <span data-ttu-id="98e6b-111">ASP.NET Core aplikace podporují automatizovanou integraci a funkční testování.</span><span class="sxs-lookup"><span data-stu-id="98e6b-111">ASP.NET Core applications support automated integration and functional testing.</span></span>

## <a name="kinds-of-automated-tests"></a><span data-ttu-id="98e6b-112">Druhy automatizovaných testů</span><span class="sxs-lookup"><span data-stu-id="98e6b-112">Kinds of automated tests</span></span>

<span data-ttu-id="98e6b-113">Existuje mnoho druhů automatizovaných testů pro softwarové aplikace.</span><span class="sxs-lookup"><span data-stu-id="98e6b-113">There are many kinds of automated tests for software applications.</span></span> <span data-ttu-id="98e6b-114">Nejjednodušším, nejnižším testem úrovně je test jednotky.</span><span class="sxs-lookup"><span data-stu-id="98e6b-114">The simplest, lowest level test is the unit test.</span></span> <span data-ttu-id="98e6b-115">Na poněkud vyšší úrovni jsou integrační testy a funkční testy.</span><span class="sxs-lookup"><span data-stu-id="98e6b-115">At a slightly higher level, there are integration tests and functional tests.</span></span> <span data-ttu-id="98e6b-116">Jiné druhy testů, jako jsou například testy uživatelského rozhraní, zátěžové testy, zátěžové testy a testy kouře, jsou nad rámec tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="98e6b-116">Other kinds of tests, such as UI tests, load tests, stress tests, and smoke tests, are beyond the scope of this document.</span></span>

### <a name="unit-tests"></a><span data-ttu-id="98e6b-117">Testování částí</span><span class="sxs-lookup"><span data-stu-id="98e6b-117">Unit tests</span></span>

<span data-ttu-id="98e6b-118">Test jednotek testuje jednu část logiky vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="98e6b-118">A unit test tests a single part of your application's logic.</span></span> <span data-ttu-id="98e6b-119">Jednu z nich může popsána uvedením některých věcí, které nejsou.</span><span class="sxs-lookup"><span data-stu-id="98e6b-119">One can further describe it by listing some of the things that it isn't.</span></span> <span data-ttu-id="98e6b-120">Test jednotek netestuje, jak váš kód funguje se závislostmi nebo infrastrukturou – to je to, pro které jsou k disviset testy.</span><span class="sxs-lookup"><span data-stu-id="98e6b-120">A unit test doesn't test how your code works with dependencies or infrastructure – that's what integration tests are for.</span></span> <span data-ttu-id="98e6b-121">Test jednotek netestuje rozhraní, ve kterém je váš kód napsán – měli byste předpokládat, že funguje, nebo pokud ho nenajdete, poznamenejte si chybu a kód a požádejte ho.</span><span class="sxs-lookup"><span data-stu-id="98e6b-121">A unit test doesn't test the framework your code is written on – you should assume it works or, if you find it doesn't, file a bug and code a workaround.</span></span> <span data-ttu-id="98e6b-122">Test jednotek běží zcela v paměti a zpracovává se.</span><span class="sxs-lookup"><span data-stu-id="98e6b-122">A unit test runs completely in memory and in process.</span></span> <span data-ttu-id="98e6b-123">Nekomunikuje se systémem souborů, sítí nebo databází.</span><span class="sxs-lookup"><span data-stu-id="98e6b-123">It doesn't communicate with the file system, the network, or a database.</span></span> <span data-ttu-id="98e6b-124">Testy jednotek by měly testovat pouze váš kód.</span><span class="sxs-lookup"><span data-stu-id="98e6b-124">Unit tests should only test your code.</span></span>

<span data-ttu-id="98e6b-125">Testování částí, na základě skutečnosti, že testuje pouze jednu jednotku vašeho kódu bez externích závislostí, by mělo být prováděno velmi rychle.</span><span class="sxs-lookup"><span data-stu-id="98e6b-125">Unit tests, by virtue of the fact that they test only a single unit of your code, with no external dependencies, should execute extremely quickly.</span></span> <span data-ttu-id="98e6b-126">Proto byste měli být schopni spustit testovací sady stovek jednotek testů za několik sekund.</span><span class="sxs-lookup"><span data-stu-id="98e6b-126">Thus, you should be able to run test suites of hundreds of unit tests in a few seconds.</span></span> <span data-ttu-id="98e6b-127">Spouštějte je často, ideálně před každým vložením do sdíleného úložiště správy zdrojového kódu a jistě u každého automatizovaného sestavení na serveru sestavení.</span><span class="sxs-lookup"><span data-stu-id="98e6b-127">Run them frequently, ideally before every push to a shared source control repository, and certainly with every automated build on your build server.</span></span>

### <a name="integration-tests"></a><span data-ttu-id="98e6b-128">Integrační testy</span><span class="sxs-lookup"><span data-stu-id="98e6b-128">Integration tests</span></span>

<span data-ttu-id="98e6b-129">I když je vhodné zapouzdřit kód, který komunikuje s infrastrukturou, jako jsou databáze a systémy souborů, budete mít i nějaký kód a budete ho pravděpodobně chtít otestovat.</span><span class="sxs-lookup"><span data-stu-id="98e6b-129">Although it's a good idea to encapsulate your code that interacts with infrastructure like databases and file systems, you will still have some of that code, and you will probably want to test it.</span></span> <span data-ttu-id="98e6b-130">Kromě toho byste měli ověřit, že vrstvy kódu pracují podle očekávání, když jsou závislosti vaší aplikace zcela vyřešeny.</span><span class="sxs-lookup"><span data-stu-id="98e6b-130">Additionally, you should verify that your code's layers interact as you expect when your application's dependencies are fully resolved.</span></span> <span data-ttu-id="98e6b-131">Jedná se o zodpovědnost za integrační testy.</span><span class="sxs-lookup"><span data-stu-id="98e6b-131">This is the responsibility of integration tests.</span></span> <span data-ttu-id="98e6b-132">Testy integrace mají za následek pomalejší a obtížnější nastavení než testování částí, protože jsou často závislé na externích závislostech a infrastruktuře.</span><span class="sxs-lookup"><span data-stu-id="98e6b-132">Integration tests tend to be slower and more difficult to set up than unit tests, because they often depend on external dependencies and infrastructure.</span></span> <span data-ttu-id="98e6b-133">Proto byste se měli vyhnout testování věcí, které by mohly být testovány pomocí testů jednotek v rámci integračních testů.</span><span class="sxs-lookup"><span data-stu-id="98e6b-133">Thus, you should avoid testing things that could be tested with unit tests in integration tests.</span></span> <span data-ttu-id="98e6b-134">Pokud otestujete daný scénář s testováním částí, měli byste ho otestovat pomocí testu jednotek.</span><span class="sxs-lookup"><span data-stu-id="98e6b-134">If you can test a given scenario with a unit test, you should test it with a unit test.</span></span> <span data-ttu-id="98e6b-135">Pokud nemůžete, zvažte použití integračního testu.</span><span class="sxs-lookup"><span data-stu-id="98e6b-135">If you can't, then consider using an integration test.</span></span>

<span data-ttu-id="98e6b-136">Integrační testy často mají složitější nastavení a rozboru postupy než testy jednotek.</span><span class="sxs-lookup"><span data-stu-id="98e6b-136">Integration tests will often have more complex setup and teardown procedures than unit tests.</span></span> <span data-ttu-id="98e6b-137">Například test integrace, který se dostane ke skutečné databázi, bude potřebovat způsob, jak vrátit databázi do známého stavu před každým spuštěním testu.</span><span class="sxs-lookup"><span data-stu-id="98e6b-137">For example, an integration test that goes against an actual database will need a way to return the database to a known state before each test run.</span></span> <span data-ttu-id="98e6b-138">Při přidání nových testů a vývoje produkčního schématu databáze budou tyto testovací skripty v úmyslu růst velikosti a složitosti.</span><span class="sxs-lookup"><span data-stu-id="98e6b-138">As new tests are added and the production database schema evolves, these test scripts will tend to grow in size and complexity.</span></span> <span data-ttu-id="98e6b-139">V mnoha velkých systémech je nepraktické spouštět úplné sady integračních testů na pracovních stanicích pro vývojáře před vrácením změn do správy sdíleného zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="98e6b-139">In many large systems, it is impractical to run full suites of integration tests on developer workstations before checking in changes to shared source control.</span></span> <span data-ttu-id="98e6b-140">V těchto případech mohou být integrační testy spuštěny na serveru sestavení.</span><span class="sxs-lookup"><span data-stu-id="98e6b-140">In these cases, integration tests may be run on a build server.</span></span>

### <a name="functional-tests"></a><span data-ttu-id="98e6b-141">Funkční testy</span><span class="sxs-lookup"><span data-stu-id="98e6b-141">Functional tests</span></span>

<span data-ttu-id="98e6b-142">Integrační testy se napíší z perspektivy vývojářů, aby bylo možné ověřit, že některé součásti systému fungují správně společně.</span><span class="sxs-lookup"><span data-stu-id="98e6b-142">Integration tests are written from the perspective of the developer, to verify that some components of the system work correctly together.</span></span> <span data-ttu-id="98e6b-143">Funkční testy se zapisují z perspektivy uživatele a ověřují správnost systému na základě jeho požadavků.</span><span class="sxs-lookup"><span data-stu-id="98e6b-143">Functional tests are written from the perspective of the user, and verify the correctness of the system based on its requirements.</span></span> <span data-ttu-id="98e6b-144">Následující úryvek nabízí užitečný analogový způsob, jak si představit o funkčních testech v porovnání s testováním částí:</span><span class="sxs-lookup"><span data-stu-id="98e6b-144">The following excerpt offers a useful analogy for how to think about functional tests, compared to unit tests:</span></span>

> <span data-ttu-id="98e6b-145">"" Hodně vývoje systému likened do budování domu.</span><span class="sxs-lookup"><span data-stu-id="98e6b-145">"Many times the development of a system is likened to the building of a house.</span></span> <span data-ttu-id="98e6b-146">I když tato analogová možnost není poměrně správná, můžeme ji pro účely porozumění rozdílu mezi jednotkou a funkčními testy roztáhnout.</span><span class="sxs-lookup"><span data-stu-id="98e6b-146">While this analogy isn't quite correct, we can extend it for the purposes of understanding the difference between unit and functional tests.</span></span> <span data-ttu-id="98e6b-147">Testování částí je obdobné jako inspektor stavby, který se navštíví na staveništi.</span><span class="sxs-lookup"><span data-stu-id="98e6b-147">Unit testing is analogous to a building inspector visiting a house's construction site.</span></span> <span data-ttu-id="98e6b-148">Zaměřuje se na různé interní systémy domu, základů, rámců, elektroinstalace, instalací a tak dále.</span><span class="sxs-lookup"><span data-stu-id="98e6b-148">He is focused on the various internal systems of the house, the foundation, framing, electrical, plumbing, and so on.</span></span> <span data-ttu-id="98e6b-149">Zajišťuje (testuje), že části domu budou fungovat správně a bezpečně, to znamená, že budou splňovat stavební kód.</span><span class="sxs-lookup"><span data-stu-id="98e6b-149">He ensures (tests) that the parts of the house will work correctly and safely, that is, meet the building code.</span></span> <span data-ttu-id="98e6b-150">Funkční testy v tomto scénáři jsou obdobou domácnosti návštěvě tohoto téhož staveništového webu.</span><span class="sxs-lookup"><span data-stu-id="98e6b-150">Functional tests in this scenario are analogous to the homeowner visiting this same construction site.</span></span> <span data-ttu-id="98e6b-151">Předpokládá, že se interní systémy budou chovat patřičně, takže inspektor budovy provádí jeho úlohu.</span><span class="sxs-lookup"><span data-stu-id="98e6b-151">He assumes that the internal systems will behave appropriately, that the building inspector is performing his task.</span></span> <span data-ttu-id="98e6b-152">Domácnosti se zaměřuje na to, co bude v této domácnosti v provozu.</span><span class="sxs-lookup"><span data-stu-id="98e6b-152">The homeowner is focused on what it will be like to live in this house.</span></span> <span data-ttu-id="98e6b-153">Záleží na tom, jak se na pracovišti nachází, na různých místnostech a na tom, kde se v rodině hodí, jsou Windows na dobrém místě pro zachycení ráno.</span><span class="sxs-lookup"><span data-stu-id="98e6b-153">He is concerned with how the house looks, are the various rooms a comfortable size, does the house fit the family's needs, are the windows in a good spot to catch the morning sun.</span></span> <span data-ttu-id="98e6b-154">Domácnosti provádí funkční testy na domu.</span><span class="sxs-lookup"><span data-stu-id="98e6b-154">The homeowner is performing functional tests on the house.</span></span> <span data-ttu-id="98e6b-155">Má perspektivu uživatele.</span><span class="sxs-lookup"><span data-stu-id="98e6b-155">He has the user's perspective.</span></span> <span data-ttu-id="98e6b-156">Inspektor budovy provádí testování částí na pracovišti.</span><span class="sxs-lookup"><span data-stu-id="98e6b-156">The building inspector is performing unit tests on the house.</span></span> <span data-ttu-id="98e6b-157">Má perspektivu tvůrce. "</span><span class="sxs-lookup"><span data-stu-id="98e6b-157">He has the builder's perspective."</span></span>

<span data-ttu-id="98e6b-158">Zdroj: [testování částí versus funkční testy](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)</span><span class="sxs-lookup"><span data-stu-id="98e6b-158">Source: [Unit Testing versus Functional Tests](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)</span></span>

<span data-ttu-id="98e6b-159">Fond jsem se říkám vývojářům, že nedošlo k chybě dvěma způsoby: nepovedlo se nám sestavit chybu, nebo jsme vytvořili špatné věci. "</span><span class="sxs-lookup"><span data-stu-id="98e6b-159">I'm fond of saying "As developers, we fail in two ways: we build the thing wrong, or we build the wrong thing."</span></span> <span data-ttu-id="98e6b-160">Testování částí vám zajistí, že vytváříte přímo věc. funkční testy zajistí, že vytváříte správnou věc.</span><span class="sxs-lookup"><span data-stu-id="98e6b-160">Unit tests ensure you are building the thing right; functional tests ensure you are building the right thing.</span></span>

<span data-ttu-id="98e6b-161">Vzhledem k tomu, že funkční testy fungují na úrovni systému, mohou vyžadovat určitý stupeň automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="98e6b-161">Since functional tests operate at the system level, they may require some degree of UI automation.</span></span> <span data-ttu-id="98e6b-162">Stejně jako integrační testy obvykle pracují s určitým druhem testovací infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="98e6b-162">Like integration tests, they usually work with some kind of test infrastructure as well.</span></span> <span data-ttu-id="98e6b-163">Díky tomu jsou pomalejší a větší poměrně křehký než testy jednotek a integrace.</span><span class="sxs-lookup"><span data-stu-id="98e6b-163">This makes them slower and more brittle than unit and integration tests.</span></span> <span data-ttu-id="98e6b-164">Měli byste mít jenom tolik funkčních testů, protože potřebujete mít jistotu, že se systém chová, jako uživatelé očekávají.</span><span class="sxs-lookup"><span data-stu-id="98e6b-164">You should have only as many functional tests as you need to be confident the system is behaving as users expect.</span></span>

### <a name="testing-pyramid"></a><span data-ttu-id="98e6b-165">Testovací jehlan</span><span class="sxs-lookup"><span data-stu-id="98e6b-165">Testing Pyramid</span></span>

<span data-ttu-id="98e6b-166">Martin Fowlera zapsaný k testovacímu pyramidu, který je příkladem zobrazeného na obrázku 9-1.</span><span class="sxs-lookup"><span data-stu-id="98e6b-166">Martin Fowler wrote about the testing pyramid, an example of which is shown in Figure 9-1.</span></span>

![Testovací jehlan](./media/image9-1.png)

<span data-ttu-id="98e6b-168">**Obrázek 9-1**.</span><span class="sxs-lookup"><span data-stu-id="98e6b-168">**Figure 9-1**.</span></span> <span data-ttu-id="98e6b-169">Testovací jehlan</span><span class="sxs-lookup"><span data-stu-id="98e6b-169">Testing Pyramid</span></span>

<span data-ttu-id="98e6b-170">Různé vrstvy pyramidy a jejich relativní velikosti, reprezentují různé druhy testů a počet, kolik byste měli pro svou aplikaci psát.</span><span class="sxs-lookup"><span data-stu-id="98e6b-170">The different layers of the pyramid, and their relative sizes, represent different kinds of tests and how many you should write for your application.</span></span> <span data-ttu-id="98e6b-171">Jak vidíte, doporučuje se mít velký základ testování částí, který je podporován menší vrstvou integračních testů, s ještě menší vrstvou funkčních testů.</span><span class="sxs-lookup"><span data-stu-id="98e6b-171">As you can see, the recommendation is to have a large base of unit tests, supported by a smaller layer of integration tests, with an even smaller layer of functional tests.</span></span> <span data-ttu-id="98e6b-172">Každá vrstva by v ideálním případě měla mít pouze testy, které nemohou být provedeny přiměřeně na nižší vrstvě.</span><span class="sxs-lookup"><span data-stu-id="98e6b-172">Each layer should ideally only have tests in it that cannot be performed adequately at a lower layer.</span></span> <span data-ttu-id="98e6b-173">Mějte na paměti, že při pokusu o určení toho, jaký typ testu potřebujete pro konkrétní scénář, mějte na paměti jehlany s testováním.</span><span class="sxs-lookup"><span data-stu-id="98e6b-173">Keep the testing pyramid in mind when you are trying to decide which kind of test you need for a particular scenario.</span></span>

### <a name="what-to-test"></a><span data-ttu-id="98e6b-174">Co testovat</span><span class="sxs-lookup"><span data-stu-id="98e6b-174">What to test</span></span>

<span data-ttu-id="98e6b-175">Běžný problém pro vývojáře, kteří mají zkušenosti s psaním automatizovaných testů, se blíží k testování.</span><span class="sxs-lookup"><span data-stu-id="98e6b-175">A common problem for developers who are inexperienced with writing automated tests is coming up with what to test.</span></span> <span data-ttu-id="98e6b-176">Dobrým výchozím bodem je testování podmíněné logiky.</span><span class="sxs-lookup"><span data-stu-id="98e6b-176">A good starting point is to test conditional logic.</span></span> <span data-ttu-id="98e6b-177">Kdekoli máte metodu s chováním, které se mění v závislosti na podmíněném příkazu (Pokud-else, přepínač a tak dále), měli byste být schopni se připojit alespoň k několika testům, které pro určité podmínky potvrzují správné chování.</span><span class="sxs-lookup"><span data-stu-id="98e6b-177">Anywhere you have a method with behavior that changes based on a conditional statement (if-else, switch, and so on), you should be able to come up with at least a couple of tests that confirm the correct behavior for certain conditions.</span></span> <span data-ttu-id="98e6b-178">Pokud má váš kód chybové podmínky, je vhodné napsat alespoň jeden test pro "příjemné" cestu prostřednictvím kódu (bez chyb) a alespoň jeden test pro "cestu JSD" (s chybami nebo netypickými výsledky) k potvrzení, že se aplikace chová jako očekávaná na výskytu chyb.</span><span class="sxs-lookup"><span data-stu-id="98e6b-178">If your code has error conditions, it's good to write at least one test for the "happy path" through the code (with no errors), and at least one test for the "sad path" (with errors or atypical results) to confirm your application behaves as expected in the face of errors.</span></span> <span data-ttu-id="98e6b-179">Nakonec se snažte soustředit na testování věcí, které mohou selhat, a nemusíte se zaměřit na metriky, jako je pokrytí kódu.</span><span class="sxs-lookup"><span data-stu-id="98e6b-179">Finally, try to focus on testing things that can fail, rather than focusing on metrics like code coverage.</span></span> <span data-ttu-id="98e6b-180">Větší pokrytí kódu je lepší než méně, obecně.</span><span class="sxs-lookup"><span data-stu-id="98e6b-180">More code coverage is better than less, generally.</span></span> <span data-ttu-id="98e6b-181">Nicméně psaní několika dalších testů složitých a podnikových metod je obvykle vhodnější než při psaní testů pro automatické vlastnosti, a to jenom pro zlepšení metrik pokrytí testovacího kódu.</span><span class="sxs-lookup"><span data-stu-id="98e6b-181">However, writing a few more tests of a complex and business-critical method is usually a better use of time than writing tests for auto-properties just to improve test code coverage metrics.</span></span>

## <a name="organizing-test-projects"></a><span data-ttu-id="98e6b-182">Uspořádání projektů testů</span><span class="sxs-lookup"><span data-stu-id="98e6b-182">Organizing test projects</span></span>

<span data-ttu-id="98e6b-183">Projekty testů mohou být uspořádány, ale budou pro vás nejlépe fungovat.</span><span class="sxs-lookup"><span data-stu-id="98e6b-183">Test projects can be organized however works best for you.</span></span> <span data-ttu-id="98e6b-184">Je vhodné oddělit testy podle typu (testování částí, test integrace) a podle toho, co jsou testovány (podle projektu, podle oboru názvů).</span><span class="sxs-lookup"><span data-stu-id="98e6b-184">It's a good idea to separate tests by type (unit test, integration test) and by what they are testing (by project, by namespace).</span></span> <span data-ttu-id="98e6b-185">Bez ohledu na to, zda se toto oddělení skládá ze složek v rámci jednoho testovacího projektu nebo více testovacích projektů, je rozhodnutí o návrhu.</span><span class="sxs-lookup"><span data-stu-id="98e6b-185">Whether this separation consists of folders within a single test project, or multiple test projects, is a design decision.</span></span> <span data-ttu-id="98e6b-186">Jeden projekt je nejjednodušší, ale pro velké projekty s mnoha testy nebo pro snazší spouštění různých sad testů může být vhodné mít několik různých testovacích projektů.</span><span class="sxs-lookup"><span data-stu-id="98e6b-186">One project is simplest, but for large projects with many tests, or in order to more easily run different sets of tests, you might want to have several different test projects.</span></span> <span data-ttu-id="98e6b-187">Mnoho týmů organizuje projekty testů na základě projektu, který testuje, což pro aplikace s více než několika projekty může vést k velkému počtu testovacích projektů, zejména v případě, že je stále rozdělíte podle toho, jaké typy testů jsou v jednotlivých projektech.</span><span class="sxs-lookup"><span data-stu-id="98e6b-187">Many teams organize test projects based on the project they are testing, which for applications with more than a few projects can result in a large number of test projects, especially if you still break these down according to what kind of tests are in each project.</span></span> <span data-ttu-id="98e6b-188">Přístup k ohrožení je mít jeden projekt na typ testu, na aplikaci a složky uvnitř testovacích projektů k označení projektu (a třídy), který je testován.</span><span class="sxs-lookup"><span data-stu-id="98e6b-188">A compromise approach is to have one project per kind of test, per application, with folders inside the test projects to indicate the project (and class) being tested.</span></span>

<span data-ttu-id="98e6b-189">Běžným přístupem je uspořádání projektů aplikace do složky src a testovacích projektů aplikace v rámci paralelní "testy".</span><span class="sxs-lookup"><span data-stu-id="98e6b-189">A common approach is to organize the application projects under a 'src' folder, and the application's test projects under a parallel 'tests' folder.</span></span> <span data-ttu-id="98e6b-190">Můžete vytvořit vyhovující složky řešení v aplikaci Visual Studio, pokud najdete tuto organizaci jako užitečnou.</span><span class="sxs-lookup"><span data-stu-id="98e6b-190">You can create matching solution folders in Visual Studio, if you find this organization useful.</span></span>

![Testování organizace ve vašem řešení](./media/image9-2.png)

<span data-ttu-id="98e6b-192">**Obrázek 9-2**.</span><span class="sxs-lookup"><span data-stu-id="98e6b-192">**Figure 9-2**.</span></span> <span data-ttu-id="98e6b-193">Testování organizace ve vašem řešení</span><span class="sxs-lookup"><span data-stu-id="98e6b-193">Test organization in your solution</span></span>

<span data-ttu-id="98e6b-194">Můžete použít jakékoli testovací rozhraní, které dáváte přednost.</span><span class="sxs-lookup"><span data-stu-id="98e6b-194">You can use whichever test framework you prefer.</span></span> <span data-ttu-id="98e6b-195">XUnit Framework dobře funguje a je to, co všechny ASP.NET Core a EF Core testy jsou napsány v.</span><span class="sxs-lookup"><span data-stu-id="98e6b-195">The xUnit framework works well and is what all of the ASP.NET Core and EF Core tests are written in.</span></span> <span data-ttu-id="98e6b-196">Projekt testů xUnit můžete přidat do sady Visual Studio pomocí šablony zobrazené na obrázku 9-3 nebo z CLI pomocí `dotnet new xunit` .</span><span class="sxs-lookup"><span data-stu-id="98e6b-196">You can add an xUnit test project in Visual Studio using the template shown in Figure 9-3, or from the CLI using `dotnet new xunit`.</span></span>

![Přidání projektu testů xUnit do sady Visual Studio](./media/image9-3.png)

<span data-ttu-id="98e6b-198">**Obrázek 9-3**.</span><span class="sxs-lookup"><span data-stu-id="98e6b-198">**Figure 9-3**.</span></span> <span data-ttu-id="98e6b-199">Přidání projektu testů xUnit do sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="98e6b-199">Add an xUnit Test Project in Visual Studio</span></span>

### <a name="test-naming"></a><span data-ttu-id="98e6b-200">Pojmenování testů</span><span class="sxs-lookup"><span data-stu-id="98e6b-200">Test naming</span></span>

<span data-ttu-id="98e6b-201">Pojmenujte své testy konzistentním způsobem s názvy, které určují, co každý test dělá.</span><span class="sxs-lookup"><span data-stu-id="98e6b-201">Name your tests in a consistent fashion, with names that indicate what each test does.</span></span> <span data-ttu-id="98e6b-202">Jedním z přístupů, které mám skvělou úspěšnost, je pojmenovat třídy testu podle třídy a metody, které testuje.</span><span class="sxs-lookup"><span data-stu-id="98e6b-202">One approach I've had great success with is to name test classes according to the class and method they are testing.</span></span> <span data-ttu-id="98e6b-203">Výsledkem je mnoho malých testovacích tříd, ale je velmi jasné, co každý test zodpovídá za.</span><span class="sxs-lookup"><span data-stu-id="98e6b-203">This results in many small test classes, but it makes it extremely clear what each test is responsible for.</span></span> <span data-ttu-id="98e6b-204">S názvem třídy testu nastaveným k identifikaci třídy a metody, která má být testována, lze název testovací metody použít k určení testovaného chování.</span><span class="sxs-lookup"><span data-stu-id="98e6b-204">With the test class name set up to identify the class and method to be tested, the test method name can be used to specify the behavior being tested.</span></span> <span data-ttu-id="98e6b-205">To by mělo zahrnovat očekávané chování a všechny vstupy nebo předpoklady, které by měly toto chování vracet.</span><span class="sxs-lookup"><span data-stu-id="98e6b-205">This should include the expected behavior and any inputs or assumptions that should yield this behavior.</span></span> <span data-ttu-id="98e6b-206">Příklady názvů testů:</span><span class="sxs-lookup"><span data-stu-id="98e6b-206">Some example test names:</span></span>

- `CatalogControllerGetImage.CallsImageServiceWithId`

- `CatalogControllerGetImage.LogsWarningGivenImageMissingException`

- `CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess`

- `CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException`

<span data-ttu-id="98e6b-207">Variace tohoto přístupu končí každý název třídy testu pomocí "by" měl "a vhodné mírně mění:</span><span class="sxs-lookup"><span data-stu-id="98e6b-207">A variation of this approach ends each test class name with "Should" and modifies the tense slightly:</span></span>

- <span data-ttu-id="98e6b-208">`CatalogControllerGetImage`**Měl by** `.` **Volání**`ImageServiceWithId`</span><span class="sxs-lookup"><span data-stu-id="98e6b-208">`CatalogControllerGetImage`**Should**`.`**Call**`ImageServiceWithId`</span></span>

- <span data-ttu-id="98e6b-209">`CatalogControllerGetImage`**Měl by** `.` **Protokol**`WarningGivenImageMissingException`</span><span class="sxs-lookup"><span data-stu-id="98e6b-209">`CatalogControllerGetImage`**Should**`.`**Log**`WarningGivenImageMissingException`</span></span>

<span data-ttu-id="98e6b-210">Někteří týmy hledají druhý jasný přístup k pojmenování, i když mírně podrobnější.</span><span class="sxs-lookup"><span data-stu-id="98e6b-210">Some teams find the second naming approach clearer, though slightly more verbose.</span></span> <span data-ttu-id="98e6b-211">V každém případě se pokuste použít konvenci pojmenování, která poskytuje přehled o chování testu, aby při selhání jednoho nebo více testů bylo zřejmé, že se nezdařily jejich názvy.</span><span class="sxs-lookup"><span data-stu-id="98e6b-211">In any case, try to use a naming convention that provides insight into test behavior, so that when one or more tests fail, it's obvious from their names what cases have failed.</span></span> <span data-ttu-id="98e6b-212">Vyhněte se pojmenovávání testů Vaguely, jako je například ControllerTests. test1, protože při jejich zobrazení ve výsledcích testů nejsou k dispozici žádná hodnota.</span><span class="sxs-lookup"><span data-stu-id="98e6b-212">Avoid naming your tests vaguely, such as ControllerTests.Test1, as these offer no value when you see them in test results.</span></span>

<span data-ttu-id="98e6b-213">Pokud budete postupovat podle konvence pojmenování, jako je ta výše, která vytváří mnoho malých testovacích tříd, je vhodné lépe uspořádat testy pomocí složek a oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="98e6b-213">If you follow a naming convention like the one above that produces many small test classes, it's a good idea to further organize your tests using folders and namespaces.</span></span> <span data-ttu-id="98e6b-214">Obrázek 9-4 ukazuje jeden z přístupů k organizování testů podle složky v rámci několika testovacích projektů.</span><span class="sxs-lookup"><span data-stu-id="98e6b-214">Figure 9-4 shows one approach to organizing tests by folder within several test projects.</span></span>

![Uspořádání tříd testu podle složky na základě testované třídy](./media/image9-4.png)

<span data-ttu-id="98e6b-216">**Obrázek 9-4.**</span><span class="sxs-lookup"><span data-stu-id="98e6b-216">**Figure 9-4.**</span></span> <span data-ttu-id="98e6b-217">Uspořádání tříd testu podle složky na základě testované třídy.</span><span class="sxs-lookup"><span data-stu-id="98e6b-217">Organizing test classes by folder based on class being tested.</span></span>

<span data-ttu-id="98e6b-218">Pokud má určitá třída aplikace testovat mnoho metod (a tedy mnoho testovacích tříd), může to mít smysl umístit je do složky, která odpovídá třídě aplikace.</span><span class="sxs-lookup"><span data-stu-id="98e6b-218">If a particular application class has many methods being tested (and thus many test classes), it may make sense to place these in a folder corresponding to the application class.</span></span> <span data-ttu-id="98e6b-219">Tato organizace se neliší od způsobu, jakým můžete soubory uspořádat do složek jinde.</span><span class="sxs-lookup"><span data-stu-id="98e6b-219">This organization is no different than how you might organize files into folders elsewhere.</span></span> <span data-ttu-id="98e6b-220">Pokud máte ve složce obsahující mnoho dalších souborů více než tři nebo čtyři související soubory, je často vhodné je přesunout do své vlastní podsložky.</span><span class="sxs-lookup"><span data-stu-id="98e6b-220">If you have more than three or four related files in a folder containing many other files, it's often helpful to move them into their own subfolder.</span></span>

## <a name="unit-testing-aspnet-core-apps"></a><span data-ttu-id="98e6b-221">Testování částí ASP.NET Core aplikací</span><span class="sxs-lookup"><span data-stu-id="98e6b-221">Unit testing ASP.NET Core apps</span></span>

<span data-ttu-id="98e6b-222">V dobře navržené aplikaci ASP.NET Core bude většina složitosti a obchodní logiky zapouzdřená v obchodních entitách a v různých službách.</span><span class="sxs-lookup"><span data-stu-id="98e6b-222">In a well-designed ASP.NET Core application, most of the complexity and business logic will be encapsulated in business entities and a variety of services.</span></span> <span data-ttu-id="98e6b-223">Aplikace ASP.NET Core MVC samotná, s jejími kontroléry, filtry, ViewModels a zobrazeními, by měla vyžadovat hodně testů jednotek.</span><span class="sxs-lookup"><span data-stu-id="98e6b-223">The ASP.NET Core MVC app itself, with its controllers, filters, viewmodels, and views, should require very few unit tests.</span></span> <span data-ttu-id="98e6b-224">Většina funkcí dané akce leží mimo metodu Action sám.</span><span class="sxs-lookup"><span data-stu-id="98e6b-224">Much of the functionality of a given action lies outside the action method itself.</span></span> <span data-ttu-id="98e6b-225">Testování, zda směrování funguje správně, nebo globální zpracování chyb, nelze provést efektivně pomocí testu jednotek.</span><span class="sxs-lookup"><span data-stu-id="98e6b-225">Testing whether routing works correctly, or global error handling, cannot be done effectively with a unit test.</span></span> <span data-ttu-id="98e6b-226">Podobně platí, že jakékoli filtry, včetně ověřování modelu a ověřování a ověřovacích filtrů, nejde testovat pomocí testu, který cílí na metodu akce kontroleru.</span><span class="sxs-lookup"><span data-stu-id="98e6b-226">Likewise, any filters, including model validation and authentication and authorization filters, cannot be unit tested with a test targeting a controller's action method.</span></span> <span data-ttu-id="98e6b-227">Bez těchto zdrojů chování by většina metod akcí měla být triviální, a to bez ohledu na to, jestli je jejich práce na služby, která se dá testovat nezávisle na řadiči, který je používá.</span><span class="sxs-lookup"><span data-stu-id="98e6b-227">Without these sources of behavior, most action methods should be trivially small, delegating the bulk of their work to services that can be tested independent of the controller that uses them.</span></span>

<span data-ttu-id="98e6b-228">Někdy budete muset kód Refaktorovat za účelem testování částí.</span><span class="sxs-lookup"><span data-stu-id="98e6b-228">Sometimes you'll need to refactor your code in order to unit test it.</span></span> <span data-ttu-id="98e6b-229">To často zahrnuje identifikaci abstrakcí a použití injektáže závislosti pro přístup k abstrakci v kódu, který chcete testovat, spíše než kódování přímo proti infrastruktuře.</span><span class="sxs-lookup"><span data-stu-id="98e6b-229">Frequently this involves identifying abstractions and using dependency injection to access the abstraction in the code you'd like to test, rather than coding directly against infrastructure.</span></span> <span data-ttu-id="98e6b-230">Zvažte například tuto jednoduchou metodu akce pro zobrazení obrázků:</span><span class="sxs-lookup"><span data-stu-id="98e6b-230">For example, consider this simple action method for displaying images:</span></span>

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

<span data-ttu-id="98e6b-231">Testování částí: Tato metoda je obtížná při přímé závislosti na `System.IO.File` , kterou používá ke čtení ze systému souborů.</span><span class="sxs-lookup"><span data-stu-id="98e6b-231">Unit testing this method is made difficult by its direct dependency on `System.IO.File`, which it uses to read from the file system.</span></span> <span data-ttu-id="98e6b-232">Toto chování můžete otestovat, abyste zajistili, že funguje podle očekávání, ale v reálném souboru je test integrace.</span><span class="sxs-lookup"><span data-stu-id="98e6b-232">You can test this behavior to ensure it works as expected, but doing so with real files is an integration test.</span></span> <span data-ttu-id="98e6b-233">Vybereme na vědomí, že nemůžete testovat tuto trasu této metody – v krátké době se vám ukáže, jak to udělat s funkčním testem.</span><span class="sxs-lookup"><span data-stu-id="98e6b-233">It's worth noting you can't unit test this method's route – you'll see how to do this with a functional test shortly.</span></span>

<span data-ttu-id="98e6b-234">Pokud nemůžete testovat chování systému souborů přímo a nemůžete testovat trasu, co je pro test k dispozici?</span><span class="sxs-lookup"><span data-stu-id="98e6b-234">If you can't unit test the file system behavior directly, and you can't test the route, what is there to test?</span></span> <span data-ttu-id="98e6b-235">I po refaktorování, aby bylo možné testování jednotek, můžete zjistit některé testovací případy a chybějící chování, například zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="98e6b-235">Well, after refactoring to make unit testing possible, you may discover some test cases and missing behavior, such as error handling.</span></span> <span data-ttu-id="98e6b-236">Co metoda dělá, když se soubor nenajde?</span><span class="sxs-lookup"><span data-stu-id="98e6b-236">What does the method do when a file isn't found?</span></span> <span data-ttu-id="98e6b-237">Co by mělo dělat?</span><span class="sxs-lookup"><span data-stu-id="98e6b-237">What should it do?</span></span> <span data-ttu-id="98e6b-238">V tomto příkladu vypadá refaktoring Method takto:</span><span class="sxs-lookup"><span data-stu-id="98e6b-238">In this example, the refactored method looks like this:</span></span>

```csharp
[HttpGet("[controller]/pic/{id}")]
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

<span data-ttu-id="98e6b-239">`_logger` a `_imageService` jsou vloženy jako závislosti.</span><span class="sxs-lookup"><span data-stu-id="98e6b-239">`_logger` and `_imageService` are both injected as dependencies.</span></span> <span data-ttu-id="98e6b-240">Nyní můžete testovat, že stejné ID, které je předáno metodě akce, je předáno do `_imageService` a že výsledné bajty jsou vráceny jako součást výsledku.</span><span class="sxs-lookup"><span data-stu-id="98e6b-240">Now you can test that the same ID that is passed to the action method is passed to `_imageService`, and that the resulting bytes are returned as part of the FileResult.</span></span> <span data-ttu-id="98e6b-241">Můžete také otestovat, že protokolování chyb probíhá podle očekávání, a že `NotFound` se vrátí výsledek, pokud chybí obrázek. za předpokladu, že se jedná o důležité chování aplikace (tj. nejen dočasný kód, který vývojář přidal k diagnostice problému).</span><span class="sxs-lookup"><span data-stu-id="98e6b-241">You can also test that error logging is happening as expected, and that a `NotFound` result is returned if the image is missing, assuming this is important application behavior (that is, not just temporary code the developer added to diagnose an issue).</span></span> <span data-ttu-id="98e6b-242">Skutečná logika souboru se přesunula do samostatné implementační služby a rozšířila se, aby vracela výjimku specifickou pro danou aplikaci pro případ chybějícího souboru.</span><span class="sxs-lookup"><span data-stu-id="98e6b-242">The actual file logic has moved into a separate implementation service, and has been augmented to return an application-specific exception for the case of a missing file.</span></span> <span data-ttu-id="98e6b-243">Tuto implementaci můžete testovat nezávisle pomocí testu integrace.</span><span class="sxs-lookup"><span data-stu-id="98e6b-243">You can test this implementation independently, using an integration test.</span></span>

<span data-ttu-id="98e6b-244">Ve většině případů budete chtít použít globální obslužné rutiny výjimek v řadičích, takže v nich by měla být velikost logiky minimální a pravděpodobně nebude znamenat testování částí.</span><span class="sxs-lookup"><span data-stu-id="98e6b-244">In most cases, you'll want to use global exception handlers in your controllers, so the amount of logic in them should be minimal and probably not worth unit testing.</span></span> <span data-ttu-id="98e6b-245">Proveďte většinu testování akcí kontroleru pomocí funkčních testů a `TestServer` třídy popsané níže.</span><span class="sxs-lookup"><span data-stu-id="98e6b-245">Do most of your testing of controller actions using functional tests and the `TestServer` class described below.</span></span>

## <a name="integration-testing-aspnet-core-apps"></a><span data-ttu-id="98e6b-246">Testování integrace ASP.NET Core aplikací</span><span class="sxs-lookup"><span data-stu-id="98e6b-246">Integration testing ASP.NET Core apps</span></span>

<span data-ttu-id="98e6b-247">Většina testů integrace v aplikacích ASP.NET Core by měla být testovací služby a další typy implementace definované v projektu infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="98e6b-247">Most of the integration tests in your ASP.NET Core apps should be testing services and other implementation types defined in your Infrastructure project.</span></span> <span data-ttu-id="98e6b-248">Můžete například [otestovat, že EF Core úspěšně aktualizoval a načítá data, která očekáváte](https://docs.microsoft.com/ef/core/miscellaneous/testing/) z tříd přístupu k datům umístěných v projektu infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="98e6b-248">For example, you could [test that EF Core was successfully updating and retrieving the data that you expect](https://docs.microsoft.com/ef/core/miscellaneous/testing/) from your data access classes residing in the Infrastructure project.</span></span> <span data-ttu-id="98e6b-249">Nejlepším způsobem, jak otestovat, že se váš ASP.NET Core projekt MVC chová správně, je funkční testy, které běží na vaší aplikaci běžící na testovacím hostiteli.</span><span class="sxs-lookup"><span data-stu-id="98e6b-249">The best way to test that your ASP.NET Core MVC project is behaving correctly is with functional tests that run against your app running in a test host.</span></span>

## <a name="functional-testing-aspnet-core-apps"></a><span data-ttu-id="98e6b-250">Funkční testování ASP.NET Core aplikací</span><span class="sxs-lookup"><span data-stu-id="98e6b-250">Functional testing ASP.NET Core apps</span></span>

<span data-ttu-id="98e6b-251">U ASP.NET Corech aplikací `TestServer` třída provádí funkční testy poměrně snadného zápisu.</span><span class="sxs-lookup"><span data-stu-id="98e6b-251">For ASP.NET Core applications, the `TestServer` class makes functional tests fairly easy to write.</span></span> <span data-ttu-id="98e6b-252">Můžete nakonfigurovat `TestServer` `WebHostBuilder` přímým použitím (nebo `HostBuilder` ) přímo (jako obvykle pro aplikaci) nebo s `WebApplicationFactory` typem (k dispozici od verze 2,1).</span><span class="sxs-lookup"><span data-stu-id="98e6b-252">You configure a `TestServer` using a `WebHostBuilder` (or `HostBuilder`) directly (as you normally do for your application), or with the `WebApplicationFactory` type (available since version 2.1).</span></span> <span data-ttu-id="98e6b-253">Snažte se považovat svého testovacího hostitele na svého produkčního hostitele co nejpřesněji, takže vaše testy budou vypadat podobně jako u aplikace v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="98e6b-253">Try to match your test host to your production host as closely as possible, so your tests exercise behavior similar to what the app will do in production.</span></span> <span data-ttu-id="98e6b-254">Tato `WebApplicationFactory` Třída je užitečná pro konfiguraci ContentRootu TestServer, která je používána ASP.NET Core k nalezení statických prostředků, jako jsou zobrazení.</span><span class="sxs-lookup"><span data-stu-id="98e6b-254">The `WebApplicationFactory` class is helpful for configuring the TestServer's ContentRoot, which is used by ASP.NET Core to locate static resource like Views.</span></span>

<span data-ttu-id="98e6b-255">Jednoduché funkční testy můžete vytvořit vytvořením třídy testu, která implementuje IClassFixture \<WebApplicationFactory\<TEntry>>, kde TEntry je vaše spouštěcí třída vaší webové aplikace.</span><span class="sxs-lookup"><span data-stu-id="98e6b-255">You can create simple functional tests by creating a test class that implements IClassFixture\<WebApplicationFactory\<TEntry>> where TEntry is your web application's Startup class.</span></span> <span data-ttu-id="98e6b-256">Na tomto místě testovací přípravek může vytvořit klienta pomocí metody CreateClient objektu pro vytváření:</span><span class="sxs-lookup"><span data-stu-id="98e6b-256">With this in place, your test fixture can create a client using the factory's CreateClient method:</span></span>

```cs
public class BasicWebTests : IClassFixture<WebApplicationFactory<Startup>>
{
    protected readonly HttpClient _client;

    public BasicWebTests(WebApplicationFactory<Startup> factory)
    {
        _client = factory.CreateClient();
    }

    // write tests that use _client
}
```

<span data-ttu-id="98e6b-257">Často budete chtít před jednotlivými testovacími běhy provést nějakou další konfiguraci vašeho webu, jako je například konfigurace aplikace tak, aby používala úložiště dat v paměti a pak dosazení aplikace s testovacími daty.</span><span class="sxs-lookup"><span data-stu-id="98e6b-257">Frequently, you'll want to perform some additional configuration of your site before each test runs, such as configuring the application to use an in memory data store and then seeding the application with test data.</span></span> <span data-ttu-id="98e6b-258">K tomu byste měli vytvořit vlastní podtřídu třídy WebApplicationFactory \<TEntry> a přepsat její metodu ConfigureWebHost.</span><span class="sxs-lookup"><span data-stu-id="98e6b-258">To do this, you should create your own subclass of WebApplicationFactory\<TEntry> and override its ConfigureWebHost method.</span></span> <span data-ttu-id="98e6b-259">Níže uvedený příklad je z projektu eShopOnWeb FunctionalTests a slouží jako součást testů v hlavní webové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="98e6b-259">The example below is from the eShopOnWeb FunctionalTests project and is used as part of the tests on the main web application.</span></span>

```cs
using Microsoft.AspNetCore.Hosting;
using Microsoft.AspNetCore.Identity;
using Microsoft.AspNetCore.Mvc.Testing;
using Microsoft.EntityFrameworkCore;
using Microsoft.eShopWeb.Infrastructure.Data;
using Microsoft.eShopWeb.Infrastructure.Identity;
using Microsoft.eShopWeb.Web;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Logging;
using System;

namespace Microsoft.eShopWeb.FunctionalTests.Web
{
    public class WebTestFixture : WebApplicationFactory<Startup>
    {
        protected override void ConfigureWebHost(IWebHostBuilder builder)
        {
            builder.UseEnvironment("Testing");

            builder.ConfigureServices(services =>
            {
                 services.AddEntityFrameworkInMemoryDatabase();

                // Create a new service provider.
                var provider = services
                    .AddEntityFrameworkInMemoryDatabase()
                    .BuildServiceProvider();

                // Add a database context (ApplicationDbContext) using an in-memory
                // database for testing.
                services.AddDbContext<CatalogContext>(options =>
                {
                    options.UseInMemoryDatabase("InMemoryDbForTesting");
                    options.UseInternalServiceProvider(provider);
                });

                services.AddDbContext<AppIdentityDbContext>(options =>
                {
                    options.UseInMemoryDatabase("Identity");
                    options.UseInternalServiceProvider(provider);
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
                        .GetRequiredService<ILogger<WebTestFixture>>();

                    // Ensure the database is created.
                    db.Database.EnsureCreated();

                    try
                    {
                        // Seed the database with test data.
                        CatalogContextSeed.SeedAsync(db, loggerFactory).Wait();

                        // seed sample user data
                        var userManager = scopedServices.GetRequiredService<UserManager<ApplicationUser>>();
                        var roleManager = scopedServices.GetRequiredService<RoleManager<IdentityRole>>();
                        AppIdentityDbContextSeed.SeedAsync(userManager, roleManager).Wait();
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

<span data-ttu-id="98e6b-260">Testy mohou pomocí tohoto vlastního WebApplicationFactory vytvořit klienta a následně provádět požadavky na aplikaci pomocí této klientské instance.</span><span class="sxs-lookup"><span data-stu-id="98e6b-260">Tests can make use of this custom WebApplicationFactory by using it to create a client and then making requests to the application using this client instance.</span></span> <span data-ttu-id="98e6b-261">Aplikace bude mít osazená data, která lze použít jako součást kontrolních výrazů testu.</span><span class="sxs-lookup"><span data-stu-id="98e6b-261">The application will have data seeded that can be used as part of the test's assertions.</span></span> <span data-ttu-id="98e6b-262">Následující test ověří, zda se Domovská stránka aplikace eShopOnWeb správně načítá a obsahuje seznam produktů přidaných do aplikace v rámci počátečních dat.</span><span class="sxs-lookup"><span data-stu-id="98e6b-262">The following test verifies that the home page of the eShopOnWeb application loads correctly and includes a product listing that was added to the application as part of the seed data.</span></span>

```cs
using Microsoft.eShopWeb.FunctionalTests.Web;
using System.Net.Http;
using System.Threading.Tasks;
using Xunit;

namespace Microsoft.eShopWeb.FunctionalTests.WebRazorPages
{
    [Collection("Sequential")]
    public class HomePageOnGet : IClassFixture<WebTestFixture>
    {
        public HomePageOnGet(WebTestFixture factory)
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

<span data-ttu-id="98e6b-263">Tento funkční test vykonává úplný ASP.NET Core zásobník aplikací MVC/Razor Pages, včetně všech middlewarů, filtrů, pořadačů atd., které mohou být na místě.</span><span class="sxs-lookup"><span data-stu-id="98e6b-263">This functional test exercises the full ASP.NET Core MVC / Razor Pages application stack, including all middleware, filters, binders, etc. that may be in place.</span></span> <span data-ttu-id="98e6b-264">Ověřuje, že daná trasa ("/") vrací stavový kód očekávané úspěšnosti a výstup ve formátu HTML.</span><span class="sxs-lookup"><span data-stu-id="98e6b-264">It verifies that a given route ("/") returns the expected success status code and HTML output.</span></span> <span data-ttu-id="98e6b-265">Je to bez nastavování reálného webového serveru, takže předejdete většině brittleness, které používají skutečný webový server pro testování, může nastat (například problémy s nastavením brány firewall).</span><span class="sxs-lookup"><span data-stu-id="98e6b-265">It does so without setting up a real web server, and so avoids much of the brittleness that using a real web server for testing can experience (for example, problems with firewall settings).</span></span> <span data-ttu-id="98e6b-266">Funkční testy, které jsou spouštěny proti TestServer, jsou obvykle pomalejší než při integraci a testování částí, ale jsou mnohem rychlejší než testy, které by mohly být spuštěny přes síť s testovacím webovým serverem.</span><span class="sxs-lookup"><span data-stu-id="98e6b-266">Functional tests that run against TestServer are usually slower than integration and unit tests, but are much faster than tests that would run over the network to a test web server.</span></span> <span data-ttu-id="98e6b-267">Použijte funkční testy, abyste zajistili, že zásobník front-endu vaší aplikace funguje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="98e6b-267">Use functional tests to ensure your application's front-end stack is working as expected.</span></span> <span data-ttu-id="98e6b-268">Tyto testy jsou zvláště užitečné při hledání duplicity na vašich řadičích nebo na stránkách a při odstraňování duplicit pomocí přidávání filtrů.</span><span class="sxs-lookup"><span data-stu-id="98e6b-268">These tests are especially useful when you find duplication in your controllers or pages and you address the duplication by adding filters.</span></span> <span data-ttu-id="98e6b-269">V ideálním případě tento refaktoring nezmění chování aplikace a sada funkčních testů ověří, zda se jedná o tento případ.</span><span class="sxs-lookup"><span data-stu-id="98e6b-269">Ideally, this refactoring won't change the behavior of the application, and a suite of functional tests will verify this is the case.</span></span>

> ### <a name="references--test-aspnet-core-mvc-apps"></a><span data-ttu-id="98e6b-270">Odkazy – test ASP.NET Core aplikace MVC</span><span class="sxs-lookup"><span data-stu-id="98e6b-270">References – Test ASP.NET Core MVC apps</span></span>
>
> - <span data-ttu-id="98e6b-271">**Testování v ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="98e6b-271">**Testing in ASP.NET Core** </span></span>\
>   <https://docs.microsoft.com/aspnet/core/testing/>
> - <span data-ttu-id="98e6b-272">**Konvence pojmenování testů jednotek** </span><span class="sxs-lookup"><span data-stu-id="98e6b-272">**Unit Test Naming Convention** </span></span>\
>   <https://ardalis.com/unit-test-naming-convention>
> - <span data-ttu-id="98e6b-273">**EF Core testování** </span><span class="sxs-lookup"><span data-stu-id="98e6b-273">**Testing EF Core** </span></span>\
>   <https://docs.microsoft.com/ef/core/miscellaneous/testing/>
> - <span data-ttu-id="98e6b-274">**Integrační testy v ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="98e6b-274">**Integration tests in ASP.NET Core** </span></span>\
>   <https://docs.microsoft.com/aspnet/core/test/integration-tests>

>[!div class="step-by-step"]
><span data-ttu-id="98e6b-275">[Předchozí](work-with-data-in-asp-net-core-apps.md) 
> [Další](development-process-for-azure.md)</span><span class="sxs-lookup"><span data-stu-id="98e6b-275">[Previous](work-with-data-in-asp-net-core-apps.md)
[Next](development-process-for-azure.md)</span></span>
