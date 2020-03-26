---
title: Testování aplikací ASP.NET Core MVC
description: Architekt moderní webové aplikace s ASP.NET core a Azure | Testování ASP.NET základních aplikací MVC
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: fa87fdba830398786cce8951d353e86bc4ff7491
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111046"
---
# <a name="test-aspnet-core-mvc-apps"></a><span data-ttu-id="e8685-103">Testování aplikací ASP.NET Core MVC</span><span class="sxs-lookup"><span data-stu-id="e8685-103">Test ASP.NET Core MVC apps</span></span>

> <span data-ttu-id="e8685-104">*"Pokud se vám nelíbí testování částí produktu, s největší pravděpodobností vaši zákazníci nebudou chtít testovat, a to buď."*</span><span class="sxs-lookup"><span data-stu-id="e8685-104">*"If you don't like unit testing your product, most likely your customers won't like to test it, either."*</span></span>
 > <span data-ttu-id="e8685-105">\_- Anonymní-</span><span class="sxs-lookup"><span data-stu-id="e8685-105">\_- Anonymous-</span></span>

<span data-ttu-id="e8685-106">Software jakékoliv složitosti může selhat neočekávaným způsobem v reakci na změny.</span><span class="sxs-lookup"><span data-stu-id="e8685-106">Software of any complexity can fail in unexpected ways in response to changes.</span></span> <span data-ttu-id="e8685-107">Testování po provedení změn je tedy vyžadováno pro všechny aplikace kromě nejbanálnějších (nebo nejméně kritických).</span><span class="sxs-lookup"><span data-stu-id="e8685-107">Thus, testing after making changes is required for all but the most trivial (or least critical) applications.</span></span> <span data-ttu-id="e8685-108">Ruční testování je nejpomalejší, nejméně spolehlivý a nejdražší způsob testování softwaru.</span><span class="sxs-lookup"><span data-stu-id="e8685-108">Manual testing is the slowest, least reliable, most expensive way to test software.</span></span> <span data-ttu-id="e8685-109">Bohužel, pokud aplikace nejsou navrženy tak, aby byly testovatelné, může to být jediný dostupný prostředek.</span><span class="sxs-lookup"><span data-stu-id="e8685-109">Unfortunately, if applications aren't designed to be testable, it can be the only means available.</span></span> <span data-ttu-id="e8685-110">Aplikace napsané tak, aby se řídily architektonickými zásadami stanovenými v [kapitole 4,](architectural-principles.md) by měly být testovatelné částí.</span><span class="sxs-lookup"><span data-stu-id="e8685-110">Applications written to follow the architectural principles laid out in [chapter 4](architectural-principles.md) should be unit testable.</span></span> <span data-ttu-id="e8685-111">ASP.NET základní aplikace podporují automatizovanou integraci a funkční testování.</span><span class="sxs-lookup"><span data-stu-id="e8685-111">ASP.NET Core applications support automated integration and functional testing.</span></span>

## <a name="kinds-of-automated-tests"></a><span data-ttu-id="e8685-112">Druhy automatizovaných testů</span><span class="sxs-lookup"><span data-stu-id="e8685-112">Kinds of automated tests</span></span>

<span data-ttu-id="e8685-113">Existuje mnoho druhů automatizovaných testů softwarových aplikací.</span><span class="sxs-lookup"><span data-stu-id="e8685-113">There are many kinds of automated tests for software applications.</span></span> <span data-ttu-id="e8685-114">Nejjednodušší, nejnižší úroveň testu je test jednotky.</span><span class="sxs-lookup"><span data-stu-id="e8685-114">The simplest, lowest level test is the unit test.</span></span> <span data-ttu-id="e8685-115">Na mírně vyšší úrovni existují integrační testy a funkční testy.</span><span class="sxs-lookup"><span data-stu-id="e8685-115">At a slightly higher level, there are integration tests and functional tests.</span></span> <span data-ttu-id="e8685-116">Jiné druhy testů, jako jsou například testy ui, zátěžové testy, zátěžové testy a kouřové testy, jsou nad rámec tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="e8685-116">Other kinds of tests, such as UI tests, load tests, stress tests, and smoke tests, are beyond the scope of this document.</span></span>

### <a name="unit-tests"></a><span data-ttu-id="e8685-117">Testování částí</span><span class="sxs-lookup"><span data-stu-id="e8685-117">Unit tests</span></span>

<span data-ttu-id="e8685-118">Testování částí testuje jednu část logiky vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="e8685-118">A unit test tests a single part of your application's logic.</span></span> <span data-ttu-id="e8685-119">Jeden může dále popsat tím, že uvádí některé z věcí, které to není.</span><span class="sxs-lookup"><span data-stu-id="e8685-119">One can further describe it by listing some of the things that it isn't.</span></span> <span data-ttu-id="e8685-120">Testování částí netestuje, jak váš kód funguje se závislostmi nebo infrastrukturou – to je to, co jsou testy integrace.</span><span class="sxs-lookup"><span data-stu-id="e8685-120">A unit test doesn't test how your code works with dependencies or infrastructure – that's what integration tests are for.</span></span> <span data-ttu-id="e8685-121">Testování částí netestuje rozhraní, na které je váš kód napsán – měli byste předpokládat, že funguje, nebo pokud zjistíte, že ne, zadejte chybu a kód řešení.</span><span class="sxs-lookup"><span data-stu-id="e8685-121">A unit test doesn't test the framework your code is written on – you should assume it works or, if you find it doesn't, file a bug and code a workaround.</span></span> <span data-ttu-id="e8685-122">Test jednotky běží zcela v paměti a probíhá.</span><span class="sxs-lookup"><span data-stu-id="e8685-122">A unit test runs completely in memory and in process.</span></span> <span data-ttu-id="e8685-123">Nekomunikuje se systémem souborů, sítí ani s databází.</span><span class="sxs-lookup"><span data-stu-id="e8685-123">It doesn't communicate with the file system, the network, or a database.</span></span> <span data-ttu-id="e8685-124">Testy částí by měly pouze testovat váš kód.</span><span class="sxs-lookup"><span data-stu-id="e8685-124">Unit tests should only test your code.</span></span>

<span data-ttu-id="e8685-125">Testování částí, na základě skutečnosti, že testují pouze jednu jednotku vašeho kódu, bez externích závislostí, by měly být provedeny velmi rychle.</span><span class="sxs-lookup"><span data-stu-id="e8685-125">Unit tests, by virtue of the fact that they test only a single unit of your code, with no external dependencies, should execute extremely quickly.</span></span> <span data-ttu-id="e8685-126">Proto byste měli být schopni spustit testovací sady stovky testů částí během několika sekund.</span><span class="sxs-lookup"><span data-stu-id="e8685-126">Thus, you should be able to run test suites of hundreds of unit tests in a few seconds.</span></span> <span data-ttu-id="e8685-127">Spouštějte je často, ideálně před každým nabízením do sdíleného úložiště správy zdrojového kódu, a určitě s každým automatizovaným sestavením na serveru sestavení.</span><span class="sxs-lookup"><span data-stu-id="e8685-127">Run them frequently, ideally before every push to a shared source control repository, and certainly with every automated build on your build server.</span></span>

### <a name="integration-tests"></a><span data-ttu-id="e8685-128">Integrační testy</span><span class="sxs-lookup"><span data-stu-id="e8685-128">Integration tests</span></span>

<span data-ttu-id="e8685-129">I když je vhodné zapouzdřit kód, který interaguje s infrastrukturou, jako jsou databáze a systémy souborů, budete mít stále některé z tohoto kódu a pravděpodobně budete chtít otestovat.</span><span class="sxs-lookup"><span data-stu-id="e8685-129">Although it's a good idea to encapsulate your code that interacts with infrastructure like databases and file systems, you will still have some of that code, and you will probably want to test it.</span></span> <span data-ttu-id="e8685-130">Kromě toho byste měli ověřit, že vrstvy kódu interagují podle očekávání, když jsou plně vyřešeny závislosti vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="e8685-130">Additionally, you should verify that your code's layers interact as you expect when your application's dependencies are fully resolved.</span></span> <span data-ttu-id="e8685-131">To je odpovědností integračních testů.</span><span class="sxs-lookup"><span data-stu-id="e8685-131">This is the responsibility of integration tests.</span></span> <span data-ttu-id="e8685-132">Integrační testy mají tendenci být pomalejší a obtížnější než testování částí, protože často závisí na externízávislosti a infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="e8685-132">Integration tests tend to be slower and more difficult to set up than unit tests, because they often depend on external dependencies and infrastructure.</span></span> <span data-ttu-id="e8685-133">Proto byste se měli vyhnout testování věcí, které by mohly být testovány s testy částí v integračních testech.</span><span class="sxs-lookup"><span data-stu-id="e8685-133">Thus, you should avoid testing things that could be tested with unit tests in integration tests.</span></span> <span data-ttu-id="e8685-134">Pokud můžete otestovat daný scénář s testování částí, měli byste jej otestovat s testování částí.</span><span class="sxs-lookup"><span data-stu-id="e8685-134">If you can test a given scenario with a unit test, you should test it with a unit test.</span></span> <span data-ttu-id="e8685-135">Pokud nemůžete, zvažte použití testu integrace.</span><span class="sxs-lookup"><span data-stu-id="e8685-135">If you can't, then consider using an integration test.</span></span>

<span data-ttu-id="e8685-136">Integrační testy budou mít často složitější postupy nastavení a stržení než testy částí.</span><span class="sxs-lookup"><span data-stu-id="e8685-136">Integration tests will often have more complex setup and teardown procedures than unit tests.</span></span> <span data-ttu-id="e8685-137">Například test integrace, který je v rozporu se skutečnou databází, bude potřebovat způsob, jak vrátit databázi do známého stavu před každým spuštěním testu.</span><span class="sxs-lookup"><span data-stu-id="e8685-137">For example, an integration test that goes against an actual database will need a way to return the database to a known state before each test run.</span></span> <span data-ttu-id="e8685-138">Při přidávání nových testů a vývoji schématu produkční databáze budou mít tyto testovací skripty tendenci zvětšovat se co do velikosti a složitosti.</span><span class="sxs-lookup"><span data-stu-id="e8685-138">As new tests are added and the production database schema evolves, these test scripts will tend to grow in size and complexity.</span></span> <span data-ttu-id="e8685-139">V mnoha velkých systémech je nepraktické spouštět úplné sady integračních testů na vývojářských pracovních stanicích před vrácením změn sdílenésprávy zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="e8685-139">In many large systems, it is impractical to run full suites of integration tests on developer workstations before checking in changes to shared source control.</span></span> <span data-ttu-id="e8685-140">V těchto případech mohou být na serveru sestavení spuštěny integrační testy.</span><span class="sxs-lookup"><span data-stu-id="e8685-140">In these cases, integration tests may be run on a build server.</span></span>

### <a name="functional-tests"></a><span data-ttu-id="e8685-141">Funkční testy</span><span class="sxs-lookup"><span data-stu-id="e8685-141">Functional tests</span></span>

<span data-ttu-id="e8685-142">Integrační testy jsou zapsány z pohledu vývojáře, aby se ověřilo, že některé součásti systému pracují správně společně.</span><span class="sxs-lookup"><span data-stu-id="e8685-142">Integration tests are written from the perspective of the developer, to verify that some components of the system work correctly together.</span></span> <span data-ttu-id="e8685-143">Funkční testy jsou psány z pohledu uživatele a ověřují správnost systému na základě jeho požadavků.</span><span class="sxs-lookup"><span data-stu-id="e8685-143">Functional tests are written from the perspective of the user, and verify the correctness of the system based on its requirements.</span></span> <span data-ttu-id="e8685-144">Následující výňatek nabízí užitečnou analogii, jak přemýšlet o funkčních testech ve srovnání s testy částí:</span><span class="sxs-lookup"><span data-stu-id="e8685-144">The following excerpt offers a useful analogy for how to think about functional tests, compared to unit tests:</span></span>

> <span data-ttu-id="e8685-145">"Mnohokrát je vývoj systému přirovnáván k výstavbě domu.</span><span class="sxs-lookup"><span data-stu-id="e8685-145">"Many times the development of a system is likened to the building of a house.</span></span> <span data-ttu-id="e8685-146">I když tato analogie není zcela správná, můžeme ji rozšířit pro účely pochopení rozdílu mezi jednotkovými a funkčními testy.</span><span class="sxs-lookup"><span data-stu-id="e8685-146">While this analogy isn't quite correct, we can extend it for the purposes of understanding the difference between unit and functional tests.</span></span> <span data-ttu-id="e8685-147">Testování částí je obdobou stavebního inspektora, který navštíví staveniště domu.</span><span class="sxs-lookup"><span data-stu-id="e8685-147">Unit testing is analogous to a building inspector visiting a house's construction site.</span></span> <span data-ttu-id="e8685-148">Zaměřuje se na různé vnitřní systémy domu, základy, rámování, elektroinstalace, instalatérské a tak dále.</span><span class="sxs-lookup"><span data-stu-id="e8685-148">He is focused on the various internal systems of the house, the foundation, framing, electrical, plumbing, and so on.</span></span> <span data-ttu-id="e8685-149">Zajišťuje (testy), že části domu budou fungovat správně a bezpečně, to znamená, že splňují stavební předpisy.</span><span class="sxs-lookup"><span data-stu-id="e8685-149">He ensures (tests) that the parts of the house will work correctly and safely, that is, meet the building code.</span></span> <span data-ttu-id="e8685-150">Funkční testy v tomto scénáři jsou obdobou majitele domu, který navštíví stejné staveniště.</span><span class="sxs-lookup"><span data-stu-id="e8685-150">Functional tests in this scenario are analogous to the homeowner visiting this same construction site.</span></span> <span data-ttu-id="e8685-151">Předpokládá, že vnitřní systémy se budou chovat vhodně, že stavební inspektor plní svůj úkol.</span><span class="sxs-lookup"><span data-stu-id="e8685-151">He assumes that the internal systems will behave appropriately, that the building inspector is performing his task.</span></span> <span data-ttu-id="e8685-152">Majitel domu se zaměřuje na to, jaké to bude žít v tomto domě.</span><span class="sxs-lookup"><span data-stu-id="e8685-152">The homeowner is focused on what it will be like to live in this house.</span></span> <span data-ttu-id="e8685-153">On se zabývá tím, jak dům vypadá, jsou různé pokoje pohodlné velikosti, se dům hodí rodiny potřeby, jsou okna v dobrém místě chytit ranní slunce.</span><span class="sxs-lookup"><span data-stu-id="e8685-153">He is concerned with how the house looks, are the various rooms a comfortable size, does the house fit the family's needs, are the windows in a good spot to catch the morning sun.</span></span> <span data-ttu-id="e8685-154">Majitel domu provádí funkční testy na domě.</span><span class="sxs-lookup"><span data-stu-id="e8685-154">The homeowner is performing functional tests on the house.</span></span> <span data-ttu-id="e8685-155">Má pohled uživatele.</span><span class="sxs-lookup"><span data-stu-id="e8685-155">He has the user's perspective.</span></span> <span data-ttu-id="e8685-156">Stavební inspektor provádí jednotkové testy domu.</span><span class="sxs-lookup"><span data-stu-id="e8685-156">The building inspector is performing unit tests on the house.</span></span> <span data-ttu-id="e8685-157">Má pohled na stavitele."</span><span class="sxs-lookup"><span data-stu-id="e8685-157">He has the builder's perspective."</span></span>

<span data-ttu-id="e8685-158">Zdroj: [Testování částí versus funkční testy](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)</span><span class="sxs-lookup"><span data-stu-id="e8685-158">Source: [Unit Testing versus Functional Tests](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)</span></span>

<span data-ttu-id="e8685-159">Jsem rád říká: "Jako vývojáři, se nám nepodaří dvěma způsoby: stavíme věc špatně, nebo jsme stavět špatnou věc."</span><span class="sxs-lookup"><span data-stu-id="e8685-159">I'm fond of saying "As developers, we fail in two ways: we build the thing wrong, or we build the wrong thing."</span></span> <span data-ttu-id="e8685-160">Jednotkové testy zajistí, že vytváříte věc správně; funkční testy zajistí, že budujete správnou věc.</span><span class="sxs-lookup"><span data-stu-id="e8685-160">Unit tests ensure you are building the thing right; functional tests ensure you are building the right thing.</span></span>

<span data-ttu-id="e8685-161">Vzhledem k tomu, že funkční testy pracují na úrovni systému, mohou vyžadovat určitý stupeň automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e8685-161">Since functional tests operate at the system level, they may require some degree of UI automation.</span></span> <span data-ttu-id="e8685-162">Stejně jako integrační testy, obvykle pracují s nějakou testovací infrastrukturou.</span><span class="sxs-lookup"><span data-stu-id="e8685-162">Like integration tests, they usually work with some kind of test infrastructure as well.</span></span> <span data-ttu-id="e8685-163">Díky tomu jsou pomalejší a křehčí než testy jednotek a integrace.</span><span class="sxs-lookup"><span data-stu-id="e8685-163">This makes them slower and more brittle than unit and integration tests.</span></span> <span data-ttu-id="e8685-164">Měli byste mít pouze tolik funkčních testů, kolik potřebujete, abyste si byli jisti, že se systém chová tak, jak uživatelé očekávají.</span><span class="sxs-lookup"><span data-stu-id="e8685-164">You should have only as many functional tests as you need to be confident the system is behaving as users expect.</span></span>

### <a name="testing-pyramid"></a><span data-ttu-id="e8685-165">Testovací pyramida</span><span class="sxs-lookup"><span data-stu-id="e8685-165">Testing Pyramid</span></span>

<span data-ttu-id="e8685-166">Martin Fowler psal o testovací pyramidě, jejíž příklad je znázorněn na obrázku 9-1.</span><span class="sxs-lookup"><span data-stu-id="e8685-166">Martin Fowler wrote about the testing pyramid, an example of which is shown in Figure 9-1.</span></span>

![Testovací pyramida](./media/image9-1.png)

<span data-ttu-id="e8685-168">**Obrázek 9-1**.</span><span class="sxs-lookup"><span data-stu-id="e8685-168">**Figure 9-1**.</span></span> <span data-ttu-id="e8685-169">Testovací pyramida</span><span class="sxs-lookup"><span data-stu-id="e8685-169">Testing Pyramid</span></span>

<span data-ttu-id="e8685-170">Různé vrstvy pyramidy a jejich relativní velikosti představují různé druhy testů a kolik byste měli napsat pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e8685-170">The different layers of the pyramid, and their relative sizes, represent different kinds of tests and how many you should write for your application.</span></span> <span data-ttu-id="e8685-171">Jak můžete vidět, doporučení je mít velkou základnu testů částí, podporované menší vrstvou integračních testů, s ještě menší vrstvou funkčních testů.</span><span class="sxs-lookup"><span data-stu-id="e8685-171">As you can see, the recommendation is to have a large base of unit tests, supported by a smaller layer of integration tests, with an even smaller layer of functional tests.</span></span> <span data-ttu-id="e8685-172">Každá vrstva by v ideálním případě měla mít pouze testy, které nelze provést adekvátně v nižší vrstvě.</span><span class="sxs-lookup"><span data-stu-id="e8685-172">Each layer should ideally only have tests in it that cannot be performed adequately at a lower layer.</span></span> <span data-ttu-id="e8685-173">Mějte na paměti testovací pyramidu, když se snažíte rozhodnout, jaký druh testu potřebujete pro konkrétní scénář.</span><span class="sxs-lookup"><span data-stu-id="e8685-173">Keep the testing pyramid in mind when you are trying to decide which kind of test you need for a particular scenario.</span></span>

### <a name="what-to-test"></a><span data-ttu-id="e8685-174">Co testovat</span><span class="sxs-lookup"><span data-stu-id="e8685-174">What to test</span></span>

<span data-ttu-id="e8685-175">Běžným problémem pro vývojáře, kteří mají zkušenosti s psaním automatizovaných testů, je přijít s tím, co testovat.</span><span class="sxs-lookup"><span data-stu-id="e8685-175">A common problem for developers who are inexperienced with writing automated tests is coming up with what to test.</span></span> <span data-ttu-id="e8685-176">Dobrým výchozím bodem je testování podmíněné logiky.</span><span class="sxs-lookup"><span data-stu-id="e8685-176">A good starting point is to test conditional logic.</span></span> <span data-ttu-id="e8685-177">Kdekoli máte metodu s chováním, které se mění na základě podmíněného příkazu (if-else, switch a tak dále), měli byste být schopni přijít s alespoň několika testy, které potvrzují správné chování za určitých podmínek.</span><span class="sxs-lookup"><span data-stu-id="e8685-177">Anywhere you have a method with behavior that changes based on a conditional statement (if-else, switch, and so on), you should be able to come up with at least a couple of tests that confirm the correct behavior for certain conditions.</span></span> <span data-ttu-id="e8685-178">Pokud váš kód obsahuje chybové stavy, je vhodné napsat alespoň jeden test pro "happy path" prostřednictvím kódu (bez chyb) a alespoň jeden test pro "smutnou cestu" (s chybami nebo atypickými výsledky) k potvrzení, že se aplikace chová podle očekávání tváří v tvář chybám.</span><span class="sxs-lookup"><span data-stu-id="e8685-178">If your code has error conditions, it's good to write at least one test for the "happy path" through the code (with no errors), and at least one test for the "sad path" (with errors or atypical results) to confirm your application behaves as expected in the face of errors.</span></span> <span data-ttu-id="e8685-179">Nakonec se pokuste zaměřit na testování věcí, které mohou selhat, spíše než se zaměřit na metriky, jako je pokrytí kódu.</span><span class="sxs-lookup"><span data-stu-id="e8685-179">Finally, try to focus on testing things that can fail, rather than focusing on metrics like code coverage.</span></span> <span data-ttu-id="e8685-180">Více pokrytí kódu je lepší než méně, obecně.</span><span class="sxs-lookup"><span data-stu-id="e8685-180">More code coverage is better than less, generally.</span></span> <span data-ttu-id="e8685-181">Psaní několika dalších testů složité a důležité metody pro podnikání je však obvykle lepší využití času než psaní testů pro automatické vlastnosti, jen aby se zlepšily metriky pokrytí testovacího kódu.</span><span class="sxs-lookup"><span data-stu-id="e8685-181">However, writing a few more tests of a complex and business-critical method is usually a better use of time than writing tests for auto-properties just to improve test code coverage metrics.</span></span>

## <a name="organizing-test-projects"></a><span data-ttu-id="e8685-182">Uspořádání testovacích projektů</span><span class="sxs-lookup"><span data-stu-id="e8685-182">Organizing test projects</span></span>

<span data-ttu-id="e8685-183">Testovací projekty mohou být organizovány, ale funguje nejlépe pro vás.</span><span class="sxs-lookup"><span data-stu-id="e8685-183">Test projects can be organized however works best for you.</span></span> <span data-ttu-id="e8685-184">Je vhodné oddělit testy podle typu (testování částí, test integrace) a podle toho, co testují (podle projektu, podle oboru názvů).</span><span class="sxs-lookup"><span data-stu-id="e8685-184">It's a good idea to separate tests by type (unit test, integration test) and by what they are testing (by project, by namespace).</span></span> <span data-ttu-id="e8685-185">Zda toto oddělení se skládá ze složek v rámci jednoho testovacího projektu nebo více testovacích projektů, je rozhodnutí o návrhu.</span><span class="sxs-lookup"><span data-stu-id="e8685-185">Whether this separation consists of folders within a single test project, or multiple test projects, is a design decision.</span></span> <span data-ttu-id="e8685-186">Jeden projekt je nejjednodušší, ale pro velké projekty s mnoha testy nebo za účelem snadněji spustit různé sady testů, můžete chtít mít několik různých testovacích projektů.</span><span class="sxs-lookup"><span data-stu-id="e8685-186">One project is simplest, but for large projects with many tests, or in order to more easily run different sets of tests, you might want to have several different test projects.</span></span> <span data-ttu-id="e8685-187">Mnoho týmů organizuje testovací projekty na základě projektu, který testují, což pro aplikace s více než několika projekty může mít za následek velký počet testovacích projektů, zejména pokud je stále rozkládáte podle toho, jaký druh testů je v každém projektu.</span><span class="sxs-lookup"><span data-stu-id="e8685-187">Many teams organize test projects based on the project they are testing, which for applications with more than a few projects can result in a large number of test projects, especially if you still break these down according to what kind of tests are in each project.</span></span> <span data-ttu-id="e8685-188">Kompromisní přístup je mít jeden projekt na druh testu, na aplikaci, se složkami uvnitř testovacích projektů k označení projektu (a třídy) testovány.</span><span class="sxs-lookup"><span data-stu-id="e8685-188">A compromise approach is to have one project per kind of test, per application, with folders inside the test projects to indicate the project (and class) being tested.</span></span>

<span data-ttu-id="e8685-189">Běžným přístupem je uspořádání projektů aplikace ve složce "src" a testovacích projektů aplikace pod paralelní složky "testy".</span><span class="sxs-lookup"><span data-stu-id="e8685-189">A common approach is to organize the application projects under a 'src' folder, and the application's test projects under a parallel 'tests' folder.</span></span> <span data-ttu-id="e8685-190">Pokud se vám tato organizace bude hodit, můžete v sadě Visual Studio vytvořit složky odpovídajících řešení.</span><span class="sxs-lookup"><span data-stu-id="e8685-190">You can create matching solution folders in Visual Studio, if you find this organization useful.</span></span>

![Testovací organizace ve vašem řešení](./media/image9-2.png)

<span data-ttu-id="e8685-192">**Obrázek 9-2**.</span><span class="sxs-lookup"><span data-stu-id="e8685-192">**Figure 9-2**.</span></span> <span data-ttu-id="e8685-193">Testovací organizace ve vašem řešení</span><span class="sxs-lookup"><span data-stu-id="e8685-193">Test organization in your solution</span></span>

<span data-ttu-id="e8685-194">Můžete použít podle toho, co test rozhraní, které dáváte přednost.</span><span class="sxs-lookup"><span data-stu-id="e8685-194">You can use whichever test framework you prefer.</span></span> <span data-ttu-id="e8685-195">XUnit framework funguje dobře a je to, co všechny ASP.NET core a EF core testy jsou zapsány v.</span><span class="sxs-lookup"><span data-stu-id="e8685-195">The xUnit framework works well and is what all of the ASP.NET Core and EF Core tests are written in.</span></span> <span data-ttu-id="e8685-196">Testovací projekt xUnit můžete přidat v sadě Visual Studio pomocí šablony znázorněné na `dotnet new xunit`obrázku 9-3 nebo z cli pomocí .</span><span class="sxs-lookup"><span data-stu-id="e8685-196">You can add an xUnit test project in Visual Studio using the template shown in Figure 9-3, or from the CLI using `dotnet new xunit`.</span></span>

![Přidání testovacího projektu xUnit v sadě Visual Studio](./media/image9-3.png)

<span data-ttu-id="e8685-198">**Obrázek 9-3**.</span><span class="sxs-lookup"><span data-stu-id="e8685-198">**Figure 9-3**.</span></span> <span data-ttu-id="e8685-199">Přidání testovacího projektu xUnit v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e8685-199">Add an xUnit Test Project in Visual Studio</span></span>

### <a name="test-naming"></a><span data-ttu-id="e8685-200">Testovat pojmenování</span><span class="sxs-lookup"><span data-stu-id="e8685-200">Test naming</span></span>

<span data-ttu-id="e8685-201">Pojmenujte testy konzistentním způsobem s názvy, které označují, co každý test dělá.</span><span class="sxs-lookup"><span data-stu-id="e8685-201">Name your tests in a consistent fashion, with names that indicate what each test does.</span></span> <span data-ttu-id="e8685-202">Jeden přístup jsem měl velký úspěch s je název testovacítřídy podle třídy a metody, které jsou testování.</span><span class="sxs-lookup"><span data-stu-id="e8685-202">One approach I've had great success with is to name test classes according to the class and method they are testing.</span></span> <span data-ttu-id="e8685-203">To má za následek mnoho malých testovacích tříd, ale je velmi jasné, co každý test je zodpovědný za.</span><span class="sxs-lookup"><span data-stu-id="e8685-203">This results in many small test classes, but it makes it extremely clear what each test is responsible for.</span></span> <span data-ttu-id="e8685-204">S názvem testovací třídy nastavena k identifikaci třídy a metody, které mají být testovány, název zkušební metody lze použít k určení chování, které jsou testovány.</span><span class="sxs-lookup"><span data-stu-id="e8685-204">With the test class name set up to identify the class and method to be tested, the test method name can be used to specify the behavior being tested.</span></span> <span data-ttu-id="e8685-205">To by mělo zahrnovat očekávané chování a všechny vstupy nebo předpoklady, které by měly výnos toto chování.</span><span class="sxs-lookup"><span data-stu-id="e8685-205">This should include the expected behavior and any inputs or assumptions that should yield this behavior.</span></span> <span data-ttu-id="e8685-206">Některé příklady testovacích názvů:</span><span class="sxs-lookup"><span data-stu-id="e8685-206">Some example test names:</span></span>

- `CatalogControllerGetImage.CallsImageServiceWithId`

- `CatalogControllerGetImage.LogsWarningGivenImageMissingException`

- `CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess`

- `CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException`

<span data-ttu-id="e8685-207">Změna tohoto přístupu ukončí každý název zkušební třídy s "Should" a mírně upraví čas:</span><span class="sxs-lookup"><span data-stu-id="e8685-207">A variation of this approach ends each test class name with "Should" and modifies the tense slightly:</span></span>

- <span data-ttu-id="e8685-208">`CatalogControllerGetImage`**By měl**`.`**volat**`ImageServiceWithId`</span><span class="sxs-lookup"><span data-stu-id="e8685-208">`CatalogControllerGetImage`**Should**`.`**Call**`ImageServiceWithId`</span></span>

- <span data-ttu-id="e8685-209">`CatalogControllerGetImage`**By se**`.`**přihlásit**`WarningGivenImageMissingException`</span><span class="sxs-lookup"><span data-stu-id="e8685-209">`CatalogControllerGetImage`**Should**`.`**Log**`WarningGivenImageMissingException`</span></span>

<span data-ttu-id="e8685-210">Některé týmy považují druhý přístup pojmenování za jasnější, i když o něco podrobnější.</span><span class="sxs-lookup"><span data-stu-id="e8685-210">Some teams find the second naming approach clearer, though slightly more verbose.</span></span> <span data-ttu-id="e8685-211">V každém případě zkuste použít konvenci pojmenování, která poskytuje přehled o chování testu, takže když jeden nebo více testů nezdaří, je zřejmé z jejich názvů, jaké případy selhaly.</span><span class="sxs-lookup"><span data-stu-id="e8685-211">In any case, try to use a naming convention that provides insight into test behavior, so that when one or more tests fail, it's obvious from their names what cases have failed.</span></span> <span data-ttu-id="e8685-212">Vyhněte se pojmenování testů vágně, jako je například ControllerTests.Test1, protože tyto nabízejí žádnou hodnotu, když je vidíte ve výsledcích testu.</span><span class="sxs-lookup"><span data-stu-id="e8685-212">Avoid naming your tests vaguely, such as ControllerTests.Test1, as these offer no value when you see them in test results.</span></span>

<span data-ttu-id="e8685-213">Pokud se řídíte konvence pojmenování, jako je výše, která vytváří mnoho malých testovacích tříd, je vhodné dále organizovat testy pomocí složek a oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="e8685-213">If you follow a naming convention like the one above that produces many small test classes, it's a good idea to further organize your tests using folders and namespaces.</span></span> <span data-ttu-id="e8685-214">Obrázek 9-4 ukazuje jeden přístup k uspořádání testů podle složky v rámci několika testovacích projektů.</span><span class="sxs-lookup"><span data-stu-id="e8685-214">Figure 9-4 shows one approach to organizing tests by folder within several test projects.</span></span>

![Uspořádání testovacích tříd podle složky na základě testované třídy](./media/image9-4.png)

<span data-ttu-id="e8685-216">**Obrázek 9-4.**</span><span class="sxs-lookup"><span data-stu-id="e8685-216">**Figure 9-4.**</span></span> <span data-ttu-id="e8685-217">Uspořádání testovacích tříd podle složky na základě testované třídy.</span><span class="sxs-lookup"><span data-stu-id="e8685-217">Organizing test classes by folder based on class being tested.</span></span>

<span data-ttu-id="e8685-218">Pokud má určitá třída aplikace mnoho testovaných metod (a tedy mnoho testovacích tříd), může mít smysl je umístit do složky odpovídající třídě aplikace.</span><span class="sxs-lookup"><span data-stu-id="e8685-218">If a particular application class has many methods being tested (and thus many test classes), it may make sense to place these in a folder corresponding to the application class.</span></span> <span data-ttu-id="e8685-219">Tato organizace se nijak neliší od uspořádání souborů do složek jinde.</span><span class="sxs-lookup"><span data-stu-id="e8685-219">This organization is no different than how you might organize files into folders elsewhere.</span></span> <span data-ttu-id="e8685-220">Pokud máte ve složce více než tři nebo čtyři související soubory obsahující mnoho dalších souborů, je často užitečné je přesunout do vlastní podsložky.</span><span class="sxs-lookup"><span data-stu-id="e8685-220">If you have more than three or four related files in a folder containing many other files, it's often helpful to move them into their own subfolder.</span></span>

## <a name="unit-testing-aspnet-core-apps"></a><span data-ttu-id="e8685-221">Testování částí ASP.NET základní aplikace</span><span class="sxs-lookup"><span data-stu-id="e8685-221">Unit testing ASP.NET Core apps</span></span>

<span data-ttu-id="e8685-222">V dobře navržené aplikaci ASP.NET Core bude většina složitosti a obchodní logiky zapouzdřena v obchodních entitách a různých službách.</span><span class="sxs-lookup"><span data-stu-id="e8685-222">In a well-designed ASP.NET Core application, most of the complexity and business logic will be encapsulated in business entities and a variety of services.</span></span> <span data-ttu-id="e8685-223">Samotná aplikace ASP.NET Core MVC se svými řadiči, filtry, zobrazeními a zobrazeními by měla vyžadovat velmi málo testů částí.</span><span class="sxs-lookup"><span data-stu-id="e8685-223">The ASP.NET Core MVC app itself, with its controllers, filters, viewmodels, and views, should require very few unit tests.</span></span> <span data-ttu-id="e8685-224">Velká část funkce dané akce leží mimo samotnou metodu akce.</span><span class="sxs-lookup"><span data-stu-id="e8685-224">Much of the functionality of a given action lies outside the action method itself.</span></span> <span data-ttu-id="e8685-225">Testování, zda směrování funguje správně, nebo globální zpracování chyb, nelze provést efektivně s testování částí.</span><span class="sxs-lookup"><span data-stu-id="e8685-225">Testing whether routing works correctly, or global error handling, cannot be done effectively with a unit test.</span></span> <span data-ttu-id="e8685-226">Stejně tak žádné filtry, včetně ověřování modelu a ověřování a autorizace filtry, nelze testovat jednotku s testem cílení na metodu akce řadiče.</span><span class="sxs-lookup"><span data-stu-id="e8685-226">Likewise, any filters, including model validation and authentication and authorization filters, cannot be unit tested with a test targeting a controller's action method.</span></span> <span data-ttu-id="e8685-227">Bez těchto zdrojů chování by většina metod akce měla být triviálně malá a delegovat většinu své práce na služby, které lze testovat nezávisle na řadiči, který je používá.</span><span class="sxs-lookup"><span data-stu-id="e8685-227">Without these sources of behavior, most action methods should be trivially small, delegating the bulk of their work to services that can be tested independent of the controller that uses them.</span></span>

<span data-ttu-id="e8685-228">Někdy budete muset refaktorovat kód, aby bylo možné jej otestovat.</span><span class="sxs-lookup"><span data-stu-id="e8685-228">Sometimes you'll need to refactor your code in order to unit test it.</span></span> <span data-ttu-id="e8685-229">Často to zahrnuje identifikaci abstrakce a použití vkládání závislostí pro přístup k abstrakci v kódu, který chcete testovat, spíše než kódování přímo proti infrastruktuře.</span><span class="sxs-lookup"><span data-stu-id="e8685-229">Frequently this involves identifying abstractions and using dependency injection to access the abstraction in the code you'd like to test, rather than coding directly against infrastructure.</span></span> <span data-ttu-id="e8685-230">Zvažte například tuto jednoduchou metodu akce pro zobrazení obrázků:</span><span class="sxs-lookup"><span data-stu-id="e8685-230">For example, consider this simple action method for displaying images:</span></span>

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

<span data-ttu-id="e8685-231">Testování částí této metody je obtížné jeho `System.IO.File`přímou závislostí na , kterou používá ke čtení ze systému souborů.</span><span class="sxs-lookup"><span data-stu-id="e8685-231">Unit testing this method is made difficult by its direct dependency on `System.IO.File`, which it uses to read from the file system.</span></span> <span data-ttu-id="e8685-232">Toto chování můžete otestovat, abyste zajistili, že funguje podle očekávání, ale pokud tak učiníte se skutečnými soubory, je test integrace.</span><span class="sxs-lookup"><span data-stu-id="e8685-232">You can test this behavior to ensure it works as expected, but doing so with real files is an integration test.</span></span> <span data-ttu-id="e8685-233">Stojí za zmínku, že nemůžete jednotkový test této metody trasy - uvidíte, jak to udělat s funkčnítest krátce.</span><span class="sxs-lookup"><span data-stu-id="e8685-233">It's worth noting you can't unit test this method's route – you'll see how to do this with a functional test shortly.</span></span>

<span data-ttu-id="e8685-234">Pokud nemůžete otestovat chování systému souborů přímo a nemůžete otestovat trasu, co je k testování?</span><span class="sxs-lookup"><span data-stu-id="e8685-234">If you can't unit test the file system behavior directly, and you can't test the route, what is there to test?</span></span> <span data-ttu-id="e8685-235">No, po refaktoringu, aby bylo možné testování částí, můžete zjistit některé testovací případy a chybějící chování, jako je například zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="e8685-235">Well, after refactoring to make unit testing possible, you may discover some test cases and missing behavior, such as error handling.</span></span> <span data-ttu-id="e8685-236">K čemu tato metoda dochází, když soubor není nalezen?</span><span class="sxs-lookup"><span data-stu-id="e8685-236">What does the method do when a file isn't found?</span></span> <span data-ttu-id="e8685-237">Co by to mělo dělat?</span><span class="sxs-lookup"><span data-stu-id="e8685-237">What should it do?</span></span> <span data-ttu-id="e8685-238">V tomto příkladu refaktorovaná metoda vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="e8685-238">In this example, the refactored method looks like this:</span></span>

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

<span data-ttu-id="e8685-239">`_logger`a `_imageService` jsou oba injekčně jako závislosti.</span><span class="sxs-lookup"><span data-stu-id="e8685-239">`_logger` and `_imageService` are both injected as dependencies.</span></span> <span data-ttu-id="e8685-240">Nyní můžete otestovat, že stejné ID, které je `_imageService`předáno metodě akce, je předáno a že výsledné bajty jsou vráceny jako součást FileResult.</span><span class="sxs-lookup"><span data-stu-id="e8685-240">Now you can test that the same ID that is passed to the action method is passed to `_imageService`, and that the resulting bytes are returned as part of the FileResult.</span></span> <span data-ttu-id="e8685-241">Můžete také otestovat, že protokolování chyb `NotFound` se děje podle očekávání a že výsledek je vrácena, pokud chybí obrázek, za předpokladu, že je důležité chování aplikace (to znamená, že nejen dočasný kód vývojář přidal k diagnostice problému).</span><span class="sxs-lookup"><span data-stu-id="e8685-241">You can also test that error logging is happening as expected, and that a `NotFound` result is returned if the image is missing, assuming this is important application behavior (that is, not just temporary code the developer added to diagnose an issue).</span></span> <span data-ttu-id="e8685-242">Skutečná logika souboru byla přesunuta do samostatné implementační služby a byla rozšířena tak, aby vrátila výjimku specifickou pro aplikaci pro případ chybějícího souboru.</span><span class="sxs-lookup"><span data-stu-id="e8685-242">The actual file logic has moved into a separate implementation service, and has been augmented to return an application-specific exception for the case of a missing file.</span></span> <span data-ttu-id="e8685-243">Tuto implementaci můžete otestovat nezávisle pomocí integračního testu.</span><span class="sxs-lookup"><span data-stu-id="e8685-243">You can test this implementation independently, using an integration test.</span></span>

<span data-ttu-id="e8685-244">Ve většině případů budete chtít použít globální obslužné rutiny výjimek ve vašich řadičích, takže množství logiky v nich by mělo být minimální a pravděpodobně nestojí za testování částí.</span><span class="sxs-lookup"><span data-stu-id="e8685-244">In most cases, you'll want to use global exception handlers in your controllers, so the amount of logic in them should be minimal and probably not worth unit testing.</span></span> <span data-ttu-id="e8685-245">Proveďte většinu testování akcí řadiče pomocí `TestServer` funkčních testů a třídy popsané níže.</span><span class="sxs-lookup"><span data-stu-id="e8685-245">Do most of your testing of controller actions using functional tests and the `TestServer` class described below.</span></span>

## <a name="integration-testing-aspnet-core-apps"></a><span data-ttu-id="e8685-246">Testování integrace ASP.NET základní aplikace</span><span class="sxs-lookup"><span data-stu-id="e8685-246">Integration testing ASP.NET Core apps</span></span>

<span data-ttu-id="e8685-247">Většina testů integrace ve vašich ASP.NET základních aplikacích by měla být testování služeb a dalších typů implementací definovaných v projektu Infrastruktura.</span><span class="sxs-lookup"><span data-stu-id="e8685-247">Most of the integration tests in your ASP.NET Core apps should be testing services and other implementation types defined in your Infrastructure project.</span></span> <span data-ttu-id="e8685-248">Můžete například [otestovat, že EF Core úspěšně aktualizoval a načítal data, která očekáváte](https://docs.microsoft.com/ef/core/miscellaneous/testing/) od tříd přístupu k datům v projektu Infrastruktura.</span><span class="sxs-lookup"><span data-stu-id="e8685-248">For example, you could [test that EF Core was successfully updating and retrieving the data that you expect](https://docs.microsoft.com/ef/core/miscellaneous/testing/) from your data access classes residing in the Infrastructure project.</span></span> <span data-ttu-id="e8685-249">Nejlepší způsob, jak otestovat, že váš ASP.NET core MVC projekt se chová správně, je s funkční testy, které běží proti vaší aplikaci spuštěné v testovacím hostiteli.</span><span class="sxs-lookup"><span data-stu-id="e8685-249">The best way to test that your ASP.NET Core MVC project is behaving correctly is with functional tests that run against your app running in a test host.</span></span>

## <a name="functional-testing-aspnet-core-apps"></a><span data-ttu-id="e8685-250">Funkční testování ASP.NET základní aplikace</span><span class="sxs-lookup"><span data-stu-id="e8685-250">Functional testing ASP.NET Core apps</span></span>

<span data-ttu-id="e8685-251">Pro ASP.NET základní `TestServer` aplikace, třída umožňuje funkční testy poměrně snadno psát.</span><span class="sxs-lookup"><span data-stu-id="e8685-251">For ASP.NET Core applications, the `TestServer` class makes functional tests fairly easy to write.</span></span> <span data-ttu-id="e8685-252">`TestServer` Nakonfigurujete `WebHostBuilder` pomocí (nebo `HostBuilder`) přímo (jako obvykle `WebApplicationFactory` pro vaši aplikaci) nebo s typem (k dispozici od verze 2.1).</span><span class="sxs-lookup"><span data-stu-id="e8685-252">You configure a `TestServer` using a `WebHostBuilder` (or `HostBuilder`) directly (as you normally do for your application), or with the `WebApplicationFactory` type (available since version 2.1).</span></span> <span data-ttu-id="e8685-253">Pokuste se co nejpřesněji přizpůsobit testovacího hostitele vašemu produkčnímu hostiteli, aby vaše testy vyvíjely chování podobné tomu, co bude aplikace dělat v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="e8685-253">Try to match your test host to your production host as closely as possible, so your tests exercise behavior similar to what the app will do in production.</span></span> <span data-ttu-id="e8685-254">Třída `WebApplicationFactory` je užitečná pro konfiguraci Kořenové kořenové stránky Obsahu serveru TestServer, který používá ASP.NET Core k vyhledání statického prostředku, jako je zobrazení.</span><span class="sxs-lookup"><span data-stu-id="e8685-254">The `WebApplicationFactory` class is helpful for configuring the TestServer's ContentRoot, which is used by ASP.NET Core to locate static resource like Views.</span></span>

<span data-ttu-id="e8685-255">Jednoduché funkční testy můžete vytvořit vytvořením testovací třídy, která implementuje IClassFixture\<WebApplicationFactory\<TEntry>> kde TEntry je třída startupvaší webové aplikace.</span><span class="sxs-lookup"><span data-stu-id="e8685-255">You can create simple functional tests by creating a test class that implements IClassFixture\<WebApplicationFactory\<TEntry>> where TEntry is your web application's Startup class.</span></span> <span data-ttu-id="e8685-256">S tímto na místě, testovací svítidlo můžete vytvořit klienta pomocí metody CreateClient výroby:</span><span class="sxs-lookup"><span data-stu-id="e8685-256">With this in place, your test fixture can create a client using the factory's CreateClient method:</span></span>

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

<span data-ttu-id="e8685-257">Často budete chtít provést některé další konfigurace webu před každým spuštěním testu, jako je například konfigurace aplikace pro použití úložiště dat v paměti a potom osetí aplikace s testovacími daty.</span><span class="sxs-lookup"><span data-stu-id="e8685-257">Frequently, you'll want to perform some additional configuration of your site before each test runs, such as configuring the application to use an in memory data store and then seeding the application with test data.</span></span> <span data-ttu-id="e8685-258">Chcete-li to provést, měli byste vytvořit\<vlastní podtřídu WebApplicationFactory TEntry> a přepsat jeho ConfigureWebHost metoda.</span><span class="sxs-lookup"><span data-stu-id="e8685-258">To do this, you should create your own subclass of WebApplicationFactory\<TEntry> and override its ConfigureWebHost method.</span></span> <span data-ttu-id="e8685-259">Níže uvedený příklad je z projektu eShopOnWeb FunctionalTests a používá se jako součást testů na hlavní webové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e8685-259">The example below is from the eShopOnWeb FunctionalTests project and is used as part of the tests on the main web application.</span></span>

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

<span data-ttu-id="e8685-260">Testy můžete využít této vlastní WebApplicationFactory pomocí k vytvoření klienta a potom vytváření požadavků na aplikaci pomocí této instance klienta.</span><span class="sxs-lookup"><span data-stu-id="e8685-260">Tests can make use of this custom WebApplicationFactory by using it to create a client and then making requests to the application using this client instance.</span></span> <span data-ttu-id="e8685-261">Aplikace bude mít data osévání, které lze použít jako součást kontrolní výrazy testu.</span><span class="sxs-lookup"><span data-stu-id="e8685-261">The application will have data seeded that can be used as part of the test's assertions.</span></span> <span data-ttu-id="e8685-262">Následující test ověří, zda se domovská stránka aplikace eShopOnWeb načte správně a obsahuje výpis produktu, který byl do aplikace přidán jako součást údajů o osivu.</span><span class="sxs-lookup"><span data-stu-id="e8685-262">The following test verifies that the home page of the eShopOnWeb application loads correctly and includes a product listing that was added to the application as part of the seed data.</span></span>

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

<span data-ttu-id="e8685-263">Tento funkční test vykonává plnou ASP.NET Core MVC / Razor Pages aplikační zásobník, včetně všech middleware, filtry, pojiva, atd., které mohou být na místě.</span><span class="sxs-lookup"><span data-stu-id="e8685-263">This functional test exercises the full ASP.NET Core MVC / Razor Pages application stack, including all middleware, filters, binders, etc. that may be in place.</span></span> <span data-ttu-id="e8685-264">Ověří, že daná trasa ("/" vrátí kód stavu očekávaného úspěchu a výstup HTML.</span><span class="sxs-lookup"><span data-stu-id="e8685-264">It verifies that a given route ("/") returns the expected success status code and HTML output.</span></span> <span data-ttu-id="e8685-265">Činí tak bez nastavení skutečného webového serveru, a tak se vyhýbá velké části křehkosti, kterou může zažít použití skutečného webového serveru pro testování (například problémy s nastavením brány firewall).</span><span class="sxs-lookup"><span data-stu-id="e8685-265">It does so without setting up a real web server, and so avoids much of the brittleness that using a real web server for testing can experience (for example, problems with firewall settings).</span></span> <span data-ttu-id="e8685-266">Funkční testy, které běží proti TestServer jsou obvykle pomalejší než integrace a testování částí, ale jsou mnohem rychlejší než testy, které by běžely přes síť na testovací webový server.</span><span class="sxs-lookup"><span data-stu-id="e8685-266">Functional tests that run against TestServer are usually slower than integration and unit tests, but are much faster than tests that would run over the network to a test web server.</span></span> <span data-ttu-id="e8685-267">Pomocí funkčních testů můžete zajistit, aby front-endový zásobník vaší aplikace fungoval podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="e8685-267">Use functional tests to ensure your application's front-end stack is working as expected.</span></span> <span data-ttu-id="e8685-268">Tyto testy jsou užitečné zejména při zjištění duplicity v řadičích nebo stránkách a řešíte duplikaci přidáním filtrů.</span><span class="sxs-lookup"><span data-stu-id="e8685-268">These tests are especially useful when you find duplication in your controllers or pages and you address the duplication by adding filters.</span></span> <span data-ttu-id="e8685-269">V ideálním případě toto refaktoring nezmění chování aplikace a sada funkčních testů ověří tento případ.</span><span class="sxs-lookup"><span data-stu-id="e8685-269">Ideally, this refactoring won't change the behavior of the application, and a suite of functional tests will verify this is the case.</span></span>

> ### <a name="references--test-aspnet-core-mvc-apps"></a><span data-ttu-id="e8685-270">Reference – Testování ASP.NET aplikace Core MVC</span><span class="sxs-lookup"><span data-stu-id="e8685-270">References – Test ASP.NET Core MVC apps</span></span>
>
> - <span data-ttu-id="e8685-271">**Testování v ASP.NET jádru** </span><span class="sxs-lookup"><span data-stu-id="e8685-271">**Testing in ASP.NET Core** </span></span>\
>   <https://docs.microsoft.com/aspnet/core/testing/>
> - <span data-ttu-id="e8685-272">**Konvence pojmenování testu částí** </span><span class="sxs-lookup"><span data-stu-id="e8685-272">**Unit Test Naming Convention** </span></span>\
>   <https://ardalis.com/unit-test-naming-convention>
> - <span data-ttu-id="e8685-273">**Testování EF core** </span><span class="sxs-lookup"><span data-stu-id="e8685-273">**Testing EF Core** </span></span>\
>   <https://docs.microsoft.com/ef/core/miscellaneous/testing/>
> - <span data-ttu-id="e8685-274">**Integrační testy v ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="e8685-274">**Integration tests in ASP.NET Core** </span></span>\
>   <https://docs.microsoft.com/aspnet/core/test/integration-tests>

>[!div class="step-by-step"]
><span data-ttu-id="e8685-275">[Předchozí](work-with-data-in-asp-net-core-apps.md)
>[další](development-process-for-azure.md)</span><span class="sxs-lookup"><span data-stu-id="e8685-275">[Previous](work-with-data-in-asp-net-core-apps.md)
[Next](development-process-for-azure.md)</span></span>
