---
title: Osvědčené postupy pro zápis testů jednotek
description: Naučte se osvědčené postupy pro psaní testů jednotek, které zajišťují kvalitu kódu a odolnost pro projekty .NET Core a .NET Standard.
author: jpreese
ms.author: wiwagn
ms.date: 07/28/2018
ms.openlocfilehash: ffeaa1e11512cab64695c120f844594b8c5014a8
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281105"
---
# <a name="unit-testing-best-practices-with-net-core-and-net-standard"></a><span data-ttu-id="2adec-103">Osvědčené postupy testování částí pomocí .NET Core a .NET Standard</span><span class="sxs-lookup"><span data-stu-id="2adec-103">Unit testing best practices with .NET Core and .NET Standard</span></span>

<span data-ttu-id="2adec-104">Při psaní testů jednotek je k dispozici mnoho výhod. pomáhají s regresí, poskytovat dokumentaci a usnadnit dobrý návrh.</span><span class="sxs-lookup"><span data-stu-id="2adec-104">There are numerous benefits to writing unit tests; they help with regression, provide documentation, and facilitate good design.</span></span> <span data-ttu-id="2adec-105">Nicméně těžko čitelný a poměrně křehký testování částí může wreak zmatek na vašem základu kódu.</span><span class="sxs-lookup"><span data-stu-id="2adec-105">However, hard to read and brittle unit tests can wreak havoc on your code base.</span></span> <span data-ttu-id="2adec-106">Tento článek popisuje některé osvědčené postupy týkající se návrhu testování částí pro projekty .NET Core a .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="2adec-106">This article describes some best practices regarding unit test design for your .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="2adec-107">V této příručce se dozvíte, jaké jsou osvědčené postupy při psaní testů jednotek pro zajištění odolnosti vašich testů a jejich snadné pochopení.</span><span class="sxs-lookup"><span data-stu-id="2adec-107">In this guide, you'll learn some best practices when writing unit tests to keep your tests resilient and easy to understand.</span></span>

<span data-ttu-id="2adec-108">Od [Jan Reese](https://reese.dev) se speciálním poděkováním [Roy Osherove](https://osherove.com/)</span><span class="sxs-lookup"><span data-stu-id="2adec-108">By [John Reese](https://reese.dev) with special thanks to [Roy Osherove](https://osherove.com/)</span></span>

## <a name="why-unit-test"></a><span data-ttu-id="2adec-109">Proč testování částí?</span><span class="sxs-lookup"><span data-stu-id="2adec-109">Why unit test?</span></span>

### <a name="less-time-performing-functional-tests"></a><span data-ttu-id="2adec-110">Méně času provádění funkčních testů</span><span class="sxs-lookup"><span data-stu-id="2adec-110">Less time performing functional tests</span></span>

<span data-ttu-id="2adec-111">Funkční testy jsou nákladné.</span><span class="sxs-lookup"><span data-stu-id="2adec-111">Functional tests are expensive.</span></span> <span data-ttu-id="2adec-112">Obvykle zahrnují otevření aplikace a provedení posloupnosti kroků (nebo někoho jiného), které je nutné provést, aby bylo možné ověřit očekávané chování.</span><span class="sxs-lookup"><span data-stu-id="2adec-112">They typically involve opening up the application and performing a series of steps that you (or someone else), must follow in order to validate the expected behavior.</span></span> <span data-ttu-id="2adec-113">Tyto kroky nemusí být vždy známy testerovi, což znamená, že se budou muset obrátit na více znalostí v oblasti, aby bylo možné provést test.</span><span class="sxs-lookup"><span data-stu-id="2adec-113">These steps may not always be known to the tester, which means they will have to reach out to someone more knowledgeable in the area in order to carry out the test.</span></span> <span data-ttu-id="2adec-114">Testování může trvat několik sekund, než se u triviálních změn nebo minut pro větší změny.</span><span class="sxs-lookup"><span data-stu-id="2adec-114">Testing itself could take seconds for trivial changes, or minutes for larger changes.</span></span> <span data-ttu-id="2adec-115">Nakonec je třeba tento proces opakovat pro každou změnu, kterou v systému provedete.</span><span class="sxs-lookup"><span data-stu-id="2adec-115">Lastly, this process must be repeated for every change that you make in the system.</span></span>

<span data-ttu-id="2adec-116">Testování částí na druhé straně trvá milisekundy, můžete je spustit při stisknutí tlačítka a nemusíte nutně vyžadovat, aby byly v systému velké znalosti.</span><span class="sxs-lookup"><span data-stu-id="2adec-116">Unit tests, on the other hand, take milliseconds, can be run at the press of a button, and don't necessarily require any knowledge of the system at large.</span></span> <span data-ttu-id="2adec-117">Bez ohledu na to, zda test projde nebo se nezdařil, je až do nástroje Test Runner, nikoli z jednotlivce.</span><span class="sxs-lookup"><span data-stu-id="2adec-117">Whether or not the test passes or fails is up to the test runner, not the individual.</span></span>

### <a name="protection-against-regression"></a><span data-ttu-id="2adec-118">Ochrana před regresí</span><span class="sxs-lookup"><span data-stu-id="2adec-118">Protection against regression</span></span>

<span data-ttu-id="2adec-119">Chyby regrese jsou chyby, které jsou představeny, když je provedena změna aplikace.</span><span class="sxs-lookup"><span data-stu-id="2adec-119">Regression defects are defects that are introduced when a change is made to the application.</span></span> <span data-ttu-id="2adec-120">Pro testery je běžné, že netestují pouze své nové funkce, ale také funkce, které existovaly předem, aby bylo možné ověřit, že dříve implementované funkce stále fungují podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="2adec-120">It is common for testers to not only test their new feature but also features that existed beforehand in order to verify that previously implemented features still function as expected.</span></span>

<span data-ttu-id="2adec-121">Při testování částí je možné znovu spustit celou sadu testů po každém sestavení nebo dokonce i po změně řádku kódu.</span><span class="sxs-lookup"><span data-stu-id="2adec-121">With unit testing, it's possible to rerun your entire suite of tests after every build or even after you change a line of code.</span></span> <span data-ttu-id="2adec-122">Máte jistotu, že nový kód neruší existující funkce.</span><span class="sxs-lookup"><span data-stu-id="2adec-122">Giving you confidence that your new code does not break existing functionality.</span></span>

### <a name="executable-documentation"></a><span data-ttu-id="2adec-123">Dokumentace ke spustitelnému souboru</span><span class="sxs-lookup"><span data-stu-id="2adec-123">Executable documentation</span></span>

<span data-ttu-id="2adec-124">Nemusí vždy být zřejmé, co konkrétní metoda dělá nebo jak se chová podle určitého vstupu.</span><span class="sxs-lookup"><span data-stu-id="2adec-124">It may not always be obvious what a particular method does or how it behaves given a certain input.</span></span> <span data-ttu-id="2adec-125">Můžete se zeptat sami: jak se tato metoda chová, když ji předáte do prázdného řetězce?</span><span class="sxs-lookup"><span data-stu-id="2adec-125">You may ask yourself: How does this method behave if I pass it a blank string?</span></span> <span data-ttu-id="2adec-126">Platnost?</span><span class="sxs-lookup"><span data-stu-id="2adec-126">Null?</span></span>

<span data-ttu-id="2adec-127">Máte-li sadu dobře pojmenovaných testů jednotek, každý test by měl být schopný jasně vysvětlit očekávaný výstup pro daný vstup.</span><span class="sxs-lookup"><span data-stu-id="2adec-127">When you have a suite of well-named unit tests, each test should be able to clearly explain the expected output for a given input.</span></span> <span data-ttu-id="2adec-128">Kromě toho by měl být schopný ověřit, zda skutečně funguje.</span><span class="sxs-lookup"><span data-stu-id="2adec-128">In addition, it should be able to verify that it actually works.</span></span>

### <a name="less-coupled-code"></a><span data-ttu-id="2adec-129">Méně spojený kód</span><span class="sxs-lookup"><span data-stu-id="2adec-129">Less coupled code</span></span>

<span data-ttu-id="2adec-130">Když je kód pevně spojený, může být obtížné testování částí.</span><span class="sxs-lookup"><span data-stu-id="2adec-130">When code is tightly coupled, it can be difficult to unit test.</span></span> <span data-ttu-id="2adec-131">Bez vytváření testů jednotek pro kód, který zapisujete, může být spojení neviditelné.</span><span class="sxs-lookup"><span data-stu-id="2adec-131">Without creating unit tests for the code that you're writing, coupling may be less apparent.</span></span>

<span data-ttu-id="2adec-132">Zápis testů pro váš kód bude přirozeně oddělit váš kód, protože by bylo obtížnější ho testovat jinak.</span><span class="sxs-lookup"><span data-stu-id="2adec-132">Writing tests for your code will naturally decouple your code, because it would be more difficult to test otherwise.</span></span>

## <a name="characteristics-of-a-good-unit-test"></a><span data-ttu-id="2adec-133">Charakteristiky dobrého testu jednotek</span><span class="sxs-lookup"><span data-stu-id="2adec-133">Characteristics of a good unit test</span></span>

- <span data-ttu-id="2adec-134">**Rychle**.</span><span class="sxs-lookup"><span data-stu-id="2adec-134">**Fast**.</span></span> <span data-ttu-id="2adec-135">Pro vyspělé projekty nemusíte mít k dispozici tisíce testů jednotek.</span><span class="sxs-lookup"><span data-stu-id="2adec-135">It is not uncommon for mature projects to have thousands of unit tests.</span></span> <span data-ttu-id="2adec-136">Spuštění testů jednotek by mělo trvat velmi málo času.</span><span class="sxs-lookup"><span data-stu-id="2adec-136">Unit tests should take very little time to run.</span></span> <span data-ttu-id="2adec-137">Milisekund.</span><span class="sxs-lookup"><span data-stu-id="2adec-137">Milliseconds.</span></span>
- <span data-ttu-id="2adec-138">**Izolované**.</span><span class="sxs-lookup"><span data-stu-id="2adec-138">**Isolated**.</span></span> <span data-ttu-id="2adec-139">Jednotkové testy jsou samostatné, můžou být spouštěny izolovaně a nesmí mít žádné závislosti na žádných jiných faktorech, jako je třeba systém souborů nebo databáze.</span><span class="sxs-lookup"><span data-stu-id="2adec-139">Unit tests are standalone, can be run in isolation, and have no dependencies on any outside factors such as a file system or database.</span></span>
- <span data-ttu-id="2adec-140">**Opakuje**se.</span><span class="sxs-lookup"><span data-stu-id="2adec-140">**Repeatable**.</span></span> <span data-ttu-id="2adec-141">Spuštění testu jednotky by mělo být konzistentní s jeho výsledky, to znamená, že vždy vrátí stejný výsledek, pokud neměníte cokoli v průběhu spuštění.</span><span class="sxs-lookup"><span data-stu-id="2adec-141">Running a unit test should be consistent with its results, that is, it always returns the same result if you do not change anything in between runs.</span></span>
- <span data-ttu-id="2adec-142">**Automatická kontrola**.</span><span class="sxs-lookup"><span data-stu-id="2adec-142">**Self-Checking**.</span></span> <span data-ttu-id="2adec-143">Test by měl být schopný automaticky zjistit, jestli byl úspěšný nebo neúspěšný, bez jakékoli lidské interakce.</span><span class="sxs-lookup"><span data-stu-id="2adec-143">The test should be able to automatically detect if it passed or failed without any human interaction.</span></span>
- <span data-ttu-id="2adec-144">**Včas**.</span><span class="sxs-lookup"><span data-stu-id="2adec-144">**Timely**.</span></span> <span data-ttu-id="2adec-145">Testování částí by nemělo mít v porovnání s testovaným kódem neúměrně dlouhou dobu.</span><span class="sxs-lookup"><span data-stu-id="2adec-145">A unit test should not take a disproportionately long time to write compared to the code being tested.</span></span> <span data-ttu-id="2adec-146">Pokud najdete testování kódu, které trvá v porovnání s psaním kódu velké množství času, zvažte návrh, který je více testovatelné.</span><span class="sxs-lookup"><span data-stu-id="2adec-146">If you find testing the code taking a large amount of time compared to writing the code, consider a design that is more testable.</span></span>

## <a name="code-coverage"></a><span data-ttu-id="2adec-147">Pokrytí kódu</span><span class="sxs-lookup"><span data-stu-id="2adec-147">Code coverage</span></span>

<span data-ttu-id="2adec-148">Vysoké procento pokrytí kódu je často spojeno s vyšší kvalitou kódu.</span><span class="sxs-lookup"><span data-stu-id="2adec-148">A high code coverage percentage is often associated with a higher quality of code.</span></span> <span data-ttu-id="2adec-149">Měření samotné ale *nemůže* určit kvalitu kódu.</span><span class="sxs-lookup"><span data-stu-id="2adec-149">However, the measurement itself *cannot* determine the quality of code.</span></span> <span data-ttu-id="2adec-150">Nastavení procentuálního cíle pokrytí kódu po výzvám souvisejícím může být counterproductive.</span><span class="sxs-lookup"><span data-stu-id="2adec-150">Setting an overly ambitious code coverage percentage goal can be counterproductive.</span></span> <span data-ttu-id="2adec-151">Představte si složitý projekt s tisíci podmíněných větví a Představte si, že jste nastavili cíl 95% pokrytí kódu.</span><span class="sxs-lookup"><span data-stu-id="2adec-151">Imagine a complex project with thousands of conditional branches, and imagine that you set a goal of 95% code coverage.</span></span> <span data-ttu-id="2adec-152">V současné době projekt udržuje 90% pokrytí kódu.</span><span class="sxs-lookup"><span data-stu-id="2adec-152">Currently the project maintains 90% code coverage.</span></span> <span data-ttu-id="2adec-153">Doba, kterou bere v úvahu pro všechny hraniční případy v zbývajících 5%, by mohla být obrovským podnikem a rychle se zmenšuje její velikost.</span><span class="sxs-lookup"><span data-stu-id="2adec-153">The amount of time it takes to account for all of the edge cases in the remaining 5% could be a massive undertaking, and the value proposition quickly diminishes.</span></span>

<span data-ttu-id="2adec-154">Vysoké procento pokrytí kódu není indikátorem úspěchu, ani to neznamená vysokou kvalitu kódu.</span><span class="sxs-lookup"><span data-stu-id="2adec-154">A high code coverage percentage is not an indicator of success, nor does it imply high code quality.</span></span> <span data-ttu-id="2adec-155">Pouze představuje množství kódu, který je pokryt jednotkovým testováním.</span><span class="sxs-lookup"><span data-stu-id="2adec-155">It just represents the amount of code that is covered by unit tests.</span></span> <span data-ttu-id="2adec-156">Další informace najdete v tématu [testování rozsahu pokrytí kódu](unit-testing-code-coverage.md).</span><span class="sxs-lookup"><span data-stu-id="2adec-156">For more information, see [unit testing code coverage](unit-testing-code-coverage.md).</span></span>

## <a name="lets-speak-the-same-language"></a><span data-ttu-id="2adec-157">Pojďme hovořit o stejný jazyk</span><span class="sxs-lookup"><span data-stu-id="2adec-157">Let's speak the same language</span></span>

<span data-ttu-id="2adec-158">Tento pojem *je často* při komunikaci s testováním často nepoužit.</span><span class="sxs-lookup"><span data-stu-id="2adec-158">The term *mock* is unfortunately often misused when talking about testing.</span></span> <span data-ttu-id="2adec-159">Následující body definují nejběžnější typy *napodobenin* při psaní jednotkových testů:</span><span class="sxs-lookup"><span data-stu-id="2adec-159">The following points define the most common types of *fakes* when writing unit tests:</span></span>

<span data-ttu-id="2adec-160">*Napodobeniny* – napodobenina je obecný termín, který lze použít k popisu buď zástupné procedury nebo objektu typu.</span><span class="sxs-lookup"><span data-stu-id="2adec-160">*Fake* - A fake is a generic term that can be used to describe either a stub or a mock object.</span></span> <span data-ttu-id="2adec-161">Bez ohledu na to, zda se jedná o zástupnou proceduru nebo objekt, závisí na kontextu, ve kterém se používá.</span><span class="sxs-lookup"><span data-stu-id="2adec-161">Whether it's a stub or a mock depends on the context in which it's used.</span></span> <span data-ttu-id="2adec-162">Jinak řečeno, napodobenina může být zástupná procedura nebo maketa.</span><span class="sxs-lookup"><span data-stu-id="2adec-162">So in other words, a fake can be a stub or a mock.</span></span>

<span data-ttu-id="2adec-163">*Model* – objekt typu Object je falešným objektem v systému, který určuje, zda nebo není test jednotky úspěšný nebo neúspěšný.</span><span class="sxs-lookup"><span data-stu-id="2adec-163">*Mock* - A mock object is a fake object in the system that decides whether or not a unit test has passed or failed.</span></span> <span data-ttu-id="2adec-164">Napodobení se zahájí jako napodobenina, dokud se neuplatní.</span><span class="sxs-lookup"><span data-stu-id="2adec-164">A mock starts out as a Fake until it's asserted against.</span></span>

<span data-ttu-id="2adec-165">*Zástupná* procedura – zástupný kód pro existující závislost (nebo spolupracovníka) v systému je ovladatelné přístupnou náhradou.</span><span class="sxs-lookup"><span data-stu-id="2adec-165">*Stub* - A stub is a controllable replacement for an existing dependency (or collaborator) in the system.</span></span> <span data-ttu-id="2adec-166">Pomocí zástupné procedury můžete testovat kód bez nutnosti pracovat přímo se závislostí.</span><span class="sxs-lookup"><span data-stu-id="2adec-166">By using a stub, you can test your code without dealing with the dependency directly.</span></span> <span data-ttu-id="2adec-167">Ve výchozím nastavení se napodobenina zahájí jako zástupná procedura.</span><span class="sxs-lookup"><span data-stu-id="2adec-167">By default, a fake starts out as a stub.</span></span>

<span data-ttu-id="2adec-168">Vezměte v úvahu následující fragment kódu:</span><span class="sxs-lookup"><span data-stu-id="2adec-168">Consider the following code snippet:</span></span>

```csharp
var mockOrder = new MockOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="2adec-169">Toto je příklad zástupné procedury, která se označuje jako objekt typu.</span><span class="sxs-lookup"><span data-stu-id="2adec-169">This would be an example of stub being referred to as a mock.</span></span> <span data-ttu-id="2adec-170">V tomto případě se jedná o zástupnou proceduru.</span><span class="sxs-lookup"><span data-stu-id="2adec-170">In this case, it is a stub.</span></span> <span data-ttu-id="2adec-171">Právě předáváte v pořadí jako prostředek, který je možné vytvořit `Purchase` (testovaný systém).</span><span class="sxs-lookup"><span data-stu-id="2adec-171">You're just passing in the Order as a means to be able to instantiate `Purchase` (the system under test).</span></span> <span data-ttu-id="2adec-172">Název `MockOrder` je také zavádějící, protože znovu není pořadím.</span><span class="sxs-lookup"><span data-stu-id="2adec-172">The name `MockOrder` is also misleading because again, the order is not a mock.</span></span>

<span data-ttu-id="2adec-173">Lepší přístup by byl</span><span class="sxs-lookup"><span data-stu-id="2adec-173">A better approach would be</span></span>

```csharp
var stubOrder = new FakeOrder();
var purchase = new Purchase(stubOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="2adec-174">Přejmenováním třídy na `FakeOrder` , jste vytvořili třídu a mnohem obecnější, třídu lze použít jako objekt typu nebo jako zástupnou proceduru.</span><span class="sxs-lookup"><span data-stu-id="2adec-174">By renaming the class to `FakeOrder`, you've made the class a lot more generic, the class can be used as a mock or a stub.</span></span> <span data-ttu-id="2adec-175">Podle toho, co je vhodnější pro testovací případ.</span><span class="sxs-lookup"><span data-stu-id="2adec-175">Whichever is better for the test case.</span></span> <span data-ttu-id="2adec-176">Ve výše uvedeném příkladu `FakeOrder` se používá jako zástupná procedura.</span><span class="sxs-lookup"><span data-stu-id="2adec-176">In the above example, `FakeOrder` is used as a stub.</span></span> <span data-ttu-id="2adec-177">Nepoužíváte ho `FakeOrder` v žádném tvaru nebo formuláři během kontrolního výrazu.</span><span class="sxs-lookup"><span data-stu-id="2adec-177">You're not using the `FakeOrder` in any shape or form during the assert.</span></span> <span data-ttu-id="2adec-178">`FakeOrder`byla předána do `Purchase` třídy, aby splňovala požadavky konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="2adec-178">`FakeOrder` was passed into the `Purchase` class to satisfy the requirements of the constructor.</span></span>

<span data-ttu-id="2adec-179">Pokud ho chcete použít jako objekt, může to vypadat nějak takto.</span><span class="sxs-lookup"><span data-stu-id="2adec-179">To use it as a Mock, you could do something like this</span></span>

```csharp
var mockOrder = new FakeOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(mockOrder.Validated);
```

<span data-ttu-id="2adec-180">V tomto případě kontrolujete vlastnost s napodobeninou (pro kterou je uplatněno), takže ve výše uvedeném fragmentu kódu `mockOrder` je objekt typu.</span><span class="sxs-lookup"><span data-stu-id="2adec-180">In this case, you are checking a property on the Fake (asserting against it), so in the above code snippet, the `mockOrder` is a Mock.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2adec-181">Je důležité získat správnou opravu této terminologie.</span><span class="sxs-lookup"><span data-stu-id="2adec-181">It's important to get this terminology correct.</span></span> <span data-ttu-id="2adec-182">Pokud voláte své zástupné procedury, ostatní vývojáři budou mít na záměr nepravdivé předpoklady.</span><span class="sxs-lookup"><span data-stu-id="2adec-182">If you call your stubs "mocks", other developers are going to make false assumptions about your intent.</span></span>

<span data-ttu-id="2adec-183">Hlavním aspektem, který si zapamatujete o postupných objektech oproti zástupným procedurám, je to, že jsou jako zástupné procedury stejné jako zástupné procedury.</span><span class="sxs-lookup"><span data-stu-id="2adec-183">The main thing to remember about mocks versus stubs is that mocks are just like stubs, but you assert against the mock object, whereas you do not assert against a stub.</span></span>

## <a name="best-practices"></a><span data-ttu-id="2adec-184">Osvědčené postupy</span><span class="sxs-lookup"><span data-stu-id="2adec-184">Best practices</span></span>

### <a name="naming-your-tests"></a><span data-ttu-id="2adec-185">Pojmenovávání testů</span><span class="sxs-lookup"><span data-stu-id="2adec-185">Naming your tests</span></span>

<span data-ttu-id="2adec-186">Název testu by měl sestávat ze tří částí:</span><span class="sxs-lookup"><span data-stu-id="2adec-186">The name of your test should consist of three parts:</span></span>

- <span data-ttu-id="2adec-187">Název testované metody.</span><span class="sxs-lookup"><span data-stu-id="2adec-187">The name of the method being tested.</span></span>
- <span data-ttu-id="2adec-188">Scénář, pod kterým se testuje.</span><span class="sxs-lookup"><span data-stu-id="2adec-188">The scenario under which it's being tested.</span></span>
- <span data-ttu-id="2adec-189">Očekávané chování při vyvolání scénáře.</span><span class="sxs-lookup"><span data-stu-id="2adec-189">The expected behavior when the scenario is invoked.</span></span>

#### <a name="why"></a><span data-ttu-id="2adec-190">Proč?</span><span class="sxs-lookup"><span data-stu-id="2adec-190">Why?</span></span>

- <span data-ttu-id="2adec-191">Standardy pojmenování jsou důležité, protože explicitně vyjadřují záměr testu.</span><span class="sxs-lookup"><span data-stu-id="2adec-191">Naming standards are important because they explicitly express the intent of the test.</span></span>

<span data-ttu-id="2adec-192">Testy jsou více, než pouze zajištění, že váš kód funguje, ale také poskytují dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="2adec-192">Tests are more than just making sure your code works, they also provide documentation.</span></span> <span data-ttu-id="2adec-193">Stejně jako při prohlížení sady jednotkových testů byste měli být schopni odvodit chování kódu bez ohledu na samotný kód.</span><span class="sxs-lookup"><span data-stu-id="2adec-193">Just by looking at the suite of unit tests, you should be able to infer the behavior of your code without even looking at the code itself.</span></span> <span data-ttu-id="2adec-194">Kromě toho, když testy selžou, vidíte přesně ty scénáře, které nesplňují vaše očekávání.</span><span class="sxs-lookup"><span data-stu-id="2adec-194">Additionally, when tests fail, you can see exactly which scenarios do not meet your expectations.</span></span>

#### <a name="bad"></a><span data-ttu-id="2adec-195">Chybně:</span><span class="sxs-lookup"><span data-stu-id="2adec-195">Bad:</span></span>

[!code-csharp[BeforeNaming](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeNaming)]

#### <a name="better"></a><span data-ttu-id="2adec-196">Zájmu</span><span class="sxs-lookup"><span data-stu-id="2adec-196">Better:</span></span>

[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="arranging-your-tests"></a><span data-ttu-id="2adec-197">Uspořádání testů</span><span class="sxs-lookup"><span data-stu-id="2adec-197">Arranging your tests</span></span>

<span data-ttu-id="2adec-198">**Uspořádat, ACT a Assert** je běžný vzor při testování částí.</span><span class="sxs-lookup"><span data-stu-id="2adec-198">**Arrange, Act, Assert** is a common pattern when unit testing.</span></span> <span data-ttu-id="2adec-199">Jak název naznačuje, skládá se ze tří hlavních akcí:</span><span class="sxs-lookup"><span data-stu-id="2adec-199">As the name implies, it consists of three main actions:</span></span>

- <span data-ttu-id="2adec-200">*Uspořádejte* své objekty, vytvářejte je a nastavte je podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="2adec-200">*Arrange* your objects, creating and setting them up as necessary.</span></span>
- <span data-ttu-id="2adec-201">*Pracovat* na objektu.</span><span class="sxs-lookup"><span data-stu-id="2adec-201">*Act* on an object.</span></span>
- <span data-ttu-id="2adec-202">Vyhodnotit *, že* je něco podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="2adec-202">*Assert* that something is as expected.</span></span>

#### <a name="why"></a><span data-ttu-id="2adec-203">Proč?</span><span class="sxs-lookup"><span data-stu-id="2adec-203">Why?</span></span>

- <span data-ttu-id="2adec-204">Jasně odděluje, co je testováno z kroků *uspořádání* a *vyhodnocení* .</span><span class="sxs-lookup"><span data-stu-id="2adec-204">Clearly separates what is being tested from the *arrange* and *assert* steps.</span></span>
- <span data-ttu-id="2adec-205">Možnost Intermix kontrolní výrazy s kódem Act je menší.</span><span class="sxs-lookup"><span data-stu-id="2adec-205">Less chance to intermix assertions with "Act" code.</span></span>

<span data-ttu-id="2adec-206">Čitelnost je jedním z nejdůležitějších aspektů při psaní testu.</span><span class="sxs-lookup"><span data-stu-id="2adec-206">Readability is one of the most important aspects when writing a test.</span></span> <span data-ttu-id="2adec-207">Oddělení každé z těchto akcí v rámci testu jasně zvýrazní závislosti vyžadované pro volání vašeho kódu, způsob, jakým je váš kód volán a co se snažíte uplatnit.</span><span class="sxs-lookup"><span data-stu-id="2adec-207">Separating each of these actions within the test clearly highlight the dependencies required to call your code, how your code is being called, and what you are trying to assert.</span></span> <span data-ttu-id="2adec-208">I když může být možné zkombinovat některé kroky a zmenšit velikost testu, primárním cílem je udělat co možná čitelnou zkoušku.</span><span class="sxs-lookup"><span data-stu-id="2adec-208">While it may be possible to combine some steps and reduce the size of your test, the primary goal is to make the test as readable as possible.</span></span>

#### <a name="bad"></a><span data-ttu-id="2adec-209">Chybně:</span><span class="sxs-lookup"><span data-stu-id="2adec-209">Bad:</span></span>

[!code-csharp[BeforeArranging](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeArranging)]

#### <a name="better"></a><span data-ttu-id="2adec-210">Zájmu</span><span class="sxs-lookup"><span data-stu-id="2adec-210">Better:</span></span>

[!code-csharp[AfterArranging](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterArranging)]

### <a name="write-minimally-passing-tests"></a><span data-ttu-id="2adec-211">Zápis s minimálním předáním testů</span><span class="sxs-lookup"><span data-stu-id="2adec-211">Write minimally passing tests</span></span>

<span data-ttu-id="2adec-212">Vstup, který se má použít v testu jednotek, by měl být nejjednodušší, aby bylo možné ověřit chování, které právě testujete.</span><span class="sxs-lookup"><span data-stu-id="2adec-212">The input to be used in a unit test should be the simplest possible in order to verify the behavior that you are currently testing.</span></span>

#### <a name="why"></a><span data-ttu-id="2adec-213">Proč?</span><span class="sxs-lookup"><span data-stu-id="2adec-213">Why?</span></span>

- <span data-ttu-id="2adec-214">Testy jsou odolnější vůči budoucím změnám v základu kódu.</span><span class="sxs-lookup"><span data-stu-id="2adec-214">Tests become more resilient to future changes in the codebase.</span></span>
- <span data-ttu-id="2adec-215">Blíže k testovacímu chování při implementaci.</span><span class="sxs-lookup"><span data-stu-id="2adec-215">Closer to testing behavior over implementation.</span></span>

<span data-ttu-id="2adec-216">Testy, které obsahují více informací, než je nutné k předání testu, mají větší šanci na zavedení chyb do testu a může udělat záměr méně jasného záměru testu.</span><span class="sxs-lookup"><span data-stu-id="2adec-216">Tests that include more information than required to pass the test have a higher chance of introducing errors into the test and can make the intent of the test less clear.</span></span> <span data-ttu-id="2adec-217">Při psaní testů se chcete zaměřit na chování.</span><span class="sxs-lookup"><span data-stu-id="2adec-217">When writing tests, you want to focus on the behavior.</span></span> <span data-ttu-id="2adec-218">Nastavení zvláštních vlastností pro modely nebo použití nenulových hodnot v případě potřeby, pouze odčítání od toho, co se snažíte prokázat.</span><span class="sxs-lookup"><span data-stu-id="2adec-218">Setting extra properties on models or using non-zero values when not required, only detracts from what you are trying to prove.</span></span>

#### <a name="bad"></a><span data-ttu-id="2adec-219">Chybně:</span><span class="sxs-lookup"><span data-stu-id="2adec-219">Bad:</span></span>

[!code-csharp[BeforeMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMinimallyPassing)]

#### <a name="better"></a><span data-ttu-id="2adec-220">Zájmu</span><span class="sxs-lookup"><span data-stu-id="2adec-220">Better:</span></span>

[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="avoid-magic-strings"></a><span data-ttu-id="2adec-221">Nepoužívejte řetězce Magic</span><span class="sxs-lookup"><span data-stu-id="2adec-221">Avoid magic strings</span></span>

<span data-ttu-id="2adec-222">Při pojmenování proměnných v testování částí je důležité, pokud není důležitější, než proměnné pojmenování v produkčním kódu.</span><span class="sxs-lookup"><span data-stu-id="2adec-222">Naming variables in unit tests is as important, if not more important, than naming variables in production code.</span></span> <span data-ttu-id="2adec-223">Testy jednotek by neměly obsahovat řetězce Magic.</span><span class="sxs-lookup"><span data-stu-id="2adec-223">Unit tests should not contain magic strings.</span></span>

#### <a name="why"></a><span data-ttu-id="2adec-224">Proč?</span><span class="sxs-lookup"><span data-stu-id="2adec-224">Why?</span></span>

- <span data-ttu-id="2adec-225">Brání nutnosti čtenářům testu zkontrolovat kód v produkčním prostředí, aby bylo možné zjistit, co dělá tuto hodnotu jako speciální.</span><span class="sxs-lookup"><span data-stu-id="2adec-225">Prevents the need for the reader of the test to inspect the production code in order to figure out what makes the value special.</span></span>
- <span data-ttu-id="2adec-226">Explicitně ukazuje, co se snažíte *dokázat* , a ne pokusit se o jeho *provedení*.</span><span class="sxs-lookup"><span data-stu-id="2adec-226">Explicitly shows what you're trying to *prove* rather than trying to *accomplish*.</span></span>

<span data-ttu-id="2adec-227">Řetězce Magic můžou způsobit nejasnost čtenářů vašich testů.</span><span class="sxs-lookup"><span data-stu-id="2adec-227">Magic strings can cause confusion to the reader of your tests.</span></span> <span data-ttu-id="2adec-228">Pokud je řetězec vyhledáný běžným způsobem, může se stát, že se pro parametr nebo návratovou hodnotu vybere určitá hodnota.</span><span class="sxs-lookup"><span data-stu-id="2adec-228">If a string looks out of the ordinary, they may wonder why a certain value was chosen for a parameter or return value.</span></span> <span data-ttu-id="2adec-229">To může způsobit, že se podíváme na podrobnosti implementace, ale nemusíte se zaměřit na test.</span><span class="sxs-lookup"><span data-stu-id="2adec-229">This may lead them to take a closer look at the implementation details, rather than focus on the test.</span></span>

> [!TIP]
> <span data-ttu-id="2adec-230">Při psaní testů byste se měli zaměřit na co nejvíc záměrů.</span><span class="sxs-lookup"><span data-stu-id="2adec-230">When writing tests, you should aim to express as much intent as possible.</span></span> <span data-ttu-id="2adec-231">V případě řetězců Magic je dobrým přístupem přiřadit tyto hodnoty konstantám.</span><span class="sxs-lookup"><span data-stu-id="2adec-231">In the case of magic strings, a good approach is to assign these values to constants.</span></span>

#### <a name="bad"></a><span data-ttu-id="2adec-232">Chybně:</span><span class="sxs-lookup"><span data-stu-id="2adec-232">Bad:</span></span>

[!code-csharp[BeforeMagicString](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMagicString)]

#### <a name="better"></a><span data-ttu-id="2adec-233">Zájmu</span><span class="sxs-lookup"><span data-stu-id="2adec-233">Better:</span></span>

[!code-csharp[AfterMagicString](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterMagicString)]

### <a name="avoid-logic-in-tests"></a><span data-ttu-id="2adec-234">Vyhnout se logice v testech</span><span class="sxs-lookup"><span data-stu-id="2adec-234">Avoid logic in tests</span></span>

<span data-ttu-id="2adec-235">Při psaní testů jednotek vyhnout se ručnímu zřetězení řetězců a logickým podmínkám, jako například,,, `if` `while` `for` `switch` atd.</span><span class="sxs-lookup"><span data-stu-id="2adec-235">When writing your unit tests avoid manual string concatenation and logical conditions such as `if`, `while`, `for`, `switch`, etc.</span></span>

#### <a name="why"></a><span data-ttu-id="2adec-236">Proč?</span><span class="sxs-lookup"><span data-stu-id="2adec-236">Why?</span></span>

- <span data-ttu-id="2adec-237">Menší šance na zavedení chyby uvnitř testů.</span><span class="sxs-lookup"><span data-stu-id="2adec-237">Less chance to introduce a bug inside of your tests.</span></span>
- <span data-ttu-id="2adec-238">Zaměřte se na konečný výsledek místo podrobností implementace.</span><span class="sxs-lookup"><span data-stu-id="2adec-238">Focus on the end result, rather than implementation details.</span></span>

<span data-ttu-id="2adec-239">Když zavedete logiku do sady testů, šance na to, že dojde k chybě, se výrazně zvyšuje.</span><span class="sxs-lookup"><span data-stu-id="2adec-239">When you introduce logic into your test suite, the chance of introducing a bug into it increases dramatically.</span></span> <span data-ttu-id="2adec-240">Poslední místo, kde chcete najít chybu, je v rámci sady testů.</span><span class="sxs-lookup"><span data-stu-id="2adec-240">The last place that you want to find a bug is within your test suite.</span></span> <span data-ttu-id="2adec-241">Měli byste mít vysokou úroveň spolehlivosti, kterou testy fungují, jinak je nebudete důvěřovat.</span><span class="sxs-lookup"><span data-stu-id="2adec-241">You should have a high level of confidence that your tests work, otherwise, you will not trust them.</span></span> <span data-ttu-id="2adec-242">Testy, kterým nedůvěřujete, nezadávají žádnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2adec-242">Tests that you do not trust, do not provide any value.</span></span> <span data-ttu-id="2adec-243">Pokud se test nezdaří, chcete mít smysl, že něco je ve skutečnosti chybné s vaším kódem a že jej nelze ignorovat.</span><span class="sxs-lookup"><span data-stu-id="2adec-243">When a test fails, you want to have a sense that something is actually wrong with your code and that it cannot be ignored.</span></span>

> [!TIP]
> <span data-ttu-id="2adec-244">Pokud se logika v testu jeví jako nenevyhnutelná, zvažte rozdělení testu na dva nebo více různých testů.</span><span class="sxs-lookup"><span data-stu-id="2adec-244">If logic in your test seems unavoidable, consider splitting the test up into two or more different tests.</span></span>

#### <a name="bad"></a><span data-ttu-id="2adec-245">Chybně:</span><span class="sxs-lookup"><span data-stu-id="2adec-245">Bad:</span></span>

[!code-csharp[LogicInTests](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#LogicInTests)]

#### <a name="better"></a><span data-ttu-id="2adec-246">Zájmu</span><span class="sxs-lookup"><span data-stu-id="2adec-246">Better:</span></span>

[!code-csharp[AfterTestLogic](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterTestLogic)]

### <a name="prefer-helper-methods-to-setup-and-teardown"></a><span data-ttu-id="2adec-247">Preferovat pomocné metody nastavení a rozboru</span><span class="sxs-lookup"><span data-stu-id="2adec-247">Prefer helper methods to setup and teardown</span></span>

<span data-ttu-id="2adec-248">Pokud pro testy požadujete podobný objekt nebo stav, preferovat pomocnou metodu než využití atributů Setup a rozboru, pokud existují.</span><span class="sxs-lookup"><span data-stu-id="2adec-248">If you require a similar object or state for your tests, prefer a helper method than leveraging Setup and Teardown attributes if they exist.</span></span>

#### <a name="why"></a><span data-ttu-id="2adec-249">Proč?</span><span class="sxs-lookup"><span data-stu-id="2adec-249">Why?</span></span>

- <span data-ttu-id="2adec-250">Při čtení testů došlo k méně nejasnostem, protože veškerý kód je viditelný v rámci každého testu.</span><span class="sxs-lookup"><span data-stu-id="2adec-250">Less confusion when reading the tests since all of the code is visible from within each test.</span></span>
- <span data-ttu-id="2adec-251">Menší pravděpodobnost nastavení pro daný test je příliš velká nebo příliš malá.</span><span class="sxs-lookup"><span data-stu-id="2adec-251">Less chance of setting up too much or too little for the given test.</span></span>
- <span data-ttu-id="2adec-252">Menší šance na stav sdílení mezi testy, který vytváří nežádoucí závislosti mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="2adec-252">Less chance of sharing state between tests, which creates unwanted dependencies between them.</span></span>

<span data-ttu-id="2adec-253">V rozhraních testování částí `Setup` je volána před každou a každou jednotkovou zkouškou v rámci sady testů.</span><span class="sxs-lookup"><span data-stu-id="2adec-253">In unit testing frameworks, `Setup` is called before each and every unit test within your test suite.</span></span> <span data-ttu-id="2adec-254">I když se některý z nich může zobrazit jako užitečný nástroj, obvykle končí na bloated a těžko čte testy.</span><span class="sxs-lookup"><span data-stu-id="2adec-254">While some may see this as a useful tool, it generally ends up leading to bloated and hard to read tests.</span></span> <span data-ttu-id="2adec-255">Každý test bude mít k dispozici různé požadavky, aby bylo možné spustit test a začít.</span><span class="sxs-lookup"><span data-stu-id="2adec-255">Each test will generally have different requirements in order to get the test up and running.</span></span> <span data-ttu-id="2adec-256">Bohužel `Setup` vynutí, abyste pro každý test používali přesně stejné požadavky.</span><span class="sxs-lookup"><span data-stu-id="2adec-256">Unfortunately, `Setup` forces you to use the exact same requirements for each test.</span></span>

> [!NOTE]
> <span data-ttu-id="2adec-257">xUnit odebral SetUp i rozboru od verze 2. x</span><span class="sxs-lookup"><span data-stu-id="2adec-257">xUnit has removed both SetUp and TearDown as of version 2.x</span></span>

#### <a name="bad"></a><span data-ttu-id="2adec-258">Chybně:</span><span class="sxs-lookup"><span data-stu-id="2adec-258">Bad:</span></span>

[!code-csharp[BeforeSetup](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeSetup)]

```csharp
// more tests...
```

[!code-csharp[BeforeHelperMethod](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeHelperMethod)]

#### <a name="better"></a><span data-ttu-id="2adec-259">Zájmu</span><span class="sxs-lookup"><span data-stu-id="2adec-259">Better:</span></span>

[!code-csharp[AfterHelperMethod](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterHelperMethod)]

```csharp
// more tests...
```

[!code-csharp[AfterSetup](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterSetup)]

### <a name="avoid-multiple-asserts"></a><span data-ttu-id="2adec-260">Vyhněte se několika kontrolním výrazům</span><span class="sxs-lookup"><span data-stu-id="2adec-260">Avoid multiple asserts</span></span>

<span data-ttu-id="2adec-261">Při psaní testů se pokuste zahrnout pouze jeden kontrolní výraz na test.</span><span class="sxs-lookup"><span data-stu-id="2adec-261">When writing your tests, try to only include one Assert per test.</span></span> <span data-ttu-id="2adec-262">Mezi běžné přístupy k použití pouze jednoho vyhodnocení patří:</span><span class="sxs-lookup"><span data-stu-id="2adec-262">Common approaches to using only one assert include:</span></span>

- <span data-ttu-id="2adec-263">Vytvořte samostatný test pro každý kontrolní výraz.</span><span class="sxs-lookup"><span data-stu-id="2adec-263">Create a separate test for each assert.</span></span>
- <span data-ttu-id="2adec-264">Použijte parametrizované testy.</span><span class="sxs-lookup"><span data-stu-id="2adec-264">Use parameterized tests.</span></span>

#### <a name="why"></a><span data-ttu-id="2adec-265">Proč?</span><span class="sxs-lookup"><span data-stu-id="2adec-265">Why?</span></span>

- <span data-ttu-id="2adec-266">Pokud jeden kontrolní výraz selže, následné kontrolní výrazy nebudou vyhodnoceny.</span><span class="sxs-lookup"><span data-stu-id="2adec-266">If one Assert fails, the subsequent Asserts will not be evaluated.</span></span>
- <span data-ttu-id="2adec-267">Zajistíte, že ve svých testech neuplatňujete více případů.</span><span class="sxs-lookup"><span data-stu-id="2adec-267">Ensures you are not asserting multiple cases in your tests.</span></span>
- <span data-ttu-id="2adec-268">Poskytuje celý obrázek jako důvod selhání testů.</span><span class="sxs-lookup"><span data-stu-id="2adec-268">Gives you the entire picture as to why your tests are failing.</span></span>

<span data-ttu-id="2adec-269">Při zavedení více kontrolních výrazů do testovacího případu není zaručeno, že budou provedeny všechny kontrolní výrazy.</span><span class="sxs-lookup"><span data-stu-id="2adec-269">When introducing multiple asserts into a test case, it is not guaranteed that all of the asserts will be executed.</span></span> <span data-ttu-id="2adec-270">Ve většině rozhraních testování částí se po selhání kontrolního výrazu v testu jednotky automaticky považují testy pokračování za neúspěšné.</span><span class="sxs-lookup"><span data-stu-id="2adec-270">In most unit testing frameworks, once an assertion fails in a unit test, the proceeding tests are automatically considered to be failing.</span></span> <span data-ttu-id="2adec-271">To může být matoucí, protože funkce, které skutečně fungují, se budou zobrazovat jako neúspěšné.</span><span class="sxs-lookup"><span data-stu-id="2adec-271">This can be confusing as functionality that is actually working, will be shown as failing.</span></span>

> [!NOTE]
> <span data-ttu-id="2adec-272">Běžnou výjimkou z tohoto pravidla je při uplatnění na objekt.</span><span class="sxs-lookup"><span data-stu-id="2adec-272">A common exception to this rule is when asserting against an object.</span></span> <span data-ttu-id="2adec-273">V tomto případě je všeobecně přijatelné mít více kontrolních výrazů proti každé vlastnosti, aby bylo zajištěno, že objekt je ve stavu, ve kterém očekáváte.</span><span class="sxs-lookup"><span data-stu-id="2adec-273">In this case, it is generally acceptable to have multiple asserts against each property to ensure the object is in the state that you expect it to be in.</span></span>

#### <a name="bad"></a><span data-ttu-id="2adec-274">Chybně:</span><span class="sxs-lookup"><span data-stu-id="2adec-274">Bad:</span></span>

[!code-csharp[BeforeMultipleAsserts](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMultipleAsserts)]

#### <a name="better"></a><span data-ttu-id="2adec-275">Zájmu</span><span class="sxs-lookup"><span data-stu-id="2adec-275">Better:</span></span>

[!code-csharp[AfterMultipleAsserts](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterMultipleAsserts)]

### <a name="validate-private-methods-by-unit-testing-public-methods"></a><span data-ttu-id="2adec-276">Ověřit soukromé metody pomocí veřejných metod testování částí</span><span class="sxs-lookup"><span data-stu-id="2adec-276">Validate private methods by unit testing public methods</span></span>

<span data-ttu-id="2adec-277">Ve většině případů by nemělo být nutné testovat soukromou metodu.</span><span class="sxs-lookup"><span data-stu-id="2adec-277">In most cases, there should not be a need to test a private method.</span></span> <span data-ttu-id="2adec-278">Soukromé metody jsou podrobné informace o implementaci.</span><span class="sxs-lookup"><span data-stu-id="2adec-278">Private methods are an implementation detail.</span></span> <span data-ttu-id="2adec-279">Tímto způsobem si můžete představit: soukromé metody nikdy neexistují v izolaci.</span><span class="sxs-lookup"><span data-stu-id="2adec-279">You can think of it this way: private methods never exist in isolation.</span></span> <span data-ttu-id="2adec-280">V určitém okamžiku se jedná o veřejnou metodu, která volá soukromou metodu jako součást její implementace.</span><span class="sxs-lookup"><span data-stu-id="2adec-280">At some point, there is going to be a public facing method that calls the private method as part of its implementation.</span></span> <span data-ttu-id="2adec-281">To, co byste měli dbát, je konečný výsledek veřejné metody, která volá do privátního.</span><span class="sxs-lookup"><span data-stu-id="2adec-281">What you should care about is the end result of the public method that calls into the private one.</span></span>

<span data-ttu-id="2adec-282">Vezměte v úvahu následující případ:</span><span class="sxs-lookup"><span data-stu-id="2adec-282">Consider the following case</span></span>

```csharp
public string ParseLogLine(string input)
{
    var sanitizedInput = TrimInput(input);
    return sanitizedInput;
}

private string TrimInput(string input)
{
    return input.Trim();
}
```

<span data-ttu-id="2adec-283">První reakce může být začít psát test pro `TrimInput` , protože chcete zajistit, aby metoda fungovala podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="2adec-283">Your first reaction may be to start writing a test for `TrimInput` because you want to make sure that the method is working as expected.</span></span> <span data-ttu-id="2adec-284">Je však možné, že je zcela možné `ParseLogLine` manipulovat `sanitizedInput` takovým způsobem, že neočekáváte, vygenerování testu proti nevýhodám `TrimInput` .</span><span class="sxs-lookup"><span data-stu-id="2adec-284">However, it is entirely possible that `ParseLogLine` manipulates `sanitizedInput` in such a way that you do not expect, rendering a test against `TrimInput` useless.</span></span>

<span data-ttu-id="2adec-285">Skutečný test by měl být proveden proti veřejné metodě `ParseLogLine` , protože to je to, co byste měli v konečném případě zajímat.</span><span class="sxs-lookup"><span data-stu-id="2adec-285">The real test should be done against the public facing method `ParseLogLine` because that is what you should ultimately care about.</span></span>

```csharp
public void ParseLogLine_StartsAndEndsWithSpace_ReturnsTrimmedResult()
{
    var parser = new Parser();

    var result = parser.ParseLogLine(" a ");

    Assert.Equals("a", result);
}
```

<span data-ttu-id="2adec-286">S tímto pohledem, pokud vidíte soukromou metodu, vyhledejte veřejnou metodu a zapište testy proti této metodě.</span><span class="sxs-lookup"><span data-stu-id="2adec-286">With this viewpoint, if you see a private method, find the public method and write your tests against that method.</span></span> <span data-ttu-id="2adec-287">Vzhledem k tomu, že soukromá metoda vrátí očekávaný výsledek, neznamená to, že systém, který nakonec volá privátní metodu, používá výsledek správně.</span><span class="sxs-lookup"><span data-stu-id="2adec-287">Just because a private method returns the expected result, does not mean the system that eventually calls the private method uses the result correctly.</span></span>

### <a name="stub-static-references"></a><span data-ttu-id="2adec-288">Statické odkazy na zástupné procedury</span><span class="sxs-lookup"><span data-stu-id="2adec-288">Stub static references</span></span>

<span data-ttu-id="2adec-289">Jedním ze zásad testování částí je, že musí mít plnou kontrolu nad testovaným systémem.</span><span class="sxs-lookup"><span data-stu-id="2adec-289">One of the principles of a unit test is that it must have full control of the system under test.</span></span> <span data-ttu-id="2adec-290">To může být problematické, pokud výrobní kód zahrnuje volání statických odkazů (například `DateTime.Now` ).</span><span class="sxs-lookup"><span data-stu-id="2adec-290">This can be problematic when production code includes calls to static references (for example, `DateTime.Now`).</span></span> <span data-ttu-id="2adec-291">Vezměte v úvahu následující kód:</span><span class="sxs-lookup"><span data-stu-id="2adec-291">Consider the following code</span></span>

```csharp
public int GetDiscountedPrice(int price)
{
    if (DateTime.Now.DayOfWeek == DayOfWeek.Tuesday)
    {
        return price / 2;
    }
    else
    {
        return price;
    }
}
```

<span data-ttu-id="2adec-292">Jak může být tento kód testován jednotkou?</span><span class="sxs-lookup"><span data-stu-id="2adec-292">How can this code possibly be unit tested?</span></span> <span data-ttu-id="2adec-293">Můžete vyzkoušet přístup jako</span><span class="sxs-lookup"><span data-stu-id="2adec-293">You may try an approach such as</span></span>

```csharp
public void GetDiscountedPrice_NotTuesday_ReturnsFullPrice()
{
    var priceCalculator = new PriceCalculator();

    var actual = priceCalculator.GetDiscountedPrice(2);

    Assert.Equals(2, actual)
}

public void GetDiscountedPrice_OnTuesday_ReturnsHalfPrice()
{
    var priceCalculator = new PriceCalculator();

    var actual = priceCalculator.GetDiscountedPrice(2);

    Assert.Equals(1, actual);
}
```

<span data-ttu-id="2adec-294">Bohužel rychle zjistíte, že existuje několik problémů s vašimi testy.</span><span class="sxs-lookup"><span data-stu-id="2adec-294">Unfortunately, you will quickly realize that there are a couple problems with your tests.</span></span>

- <span data-ttu-id="2adec-295">Pokud je testovací sada spuštěna v úterý, druhý test projde, ale první test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="2adec-295">If the test suite is run on a Tuesday, the second test will pass, but the first test will fail.</span></span>
- <span data-ttu-id="2adec-296">Pokud je testovací sada spuštěna v jakémkoli jiném dni, bude první test úspěšný, ale druhý test selže.</span><span class="sxs-lookup"><span data-stu-id="2adec-296">If the test suite is run on any other day, the first test will pass, but the second test will fail.</span></span>

<span data-ttu-id="2adec-297">Chcete-li tyto problémy vyřešit, budete muset uvést do svého produkčního kódu *spojku* .</span><span class="sxs-lookup"><span data-stu-id="2adec-297">To solve these problems, you'll need to introduce a *seam* into your production code.</span></span> <span data-ttu-id="2adec-298">Jedním z možností je zabalit kód, který je třeba ovládat v rozhraní a mít kód produkčního prostředí závislý na tomto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2adec-298">One approach is to wrap the code that you need to control in an interface and have the production code depend on that interface.</span></span>

```csharp
public interface IDateTimeProvider
{
    DayOfWeek DayOfWeek();
}

public int GetDiscountedPrice(int price, IDateTimeProvider dateTimeProvider)
{
    if (dateTimeProvider.DayOfWeek() == DayOfWeek.Tuesday)
    {
        return price / 2;
    }
    else
    {
        return price;
    }
}
```

<span data-ttu-id="2adec-299">Vaše sada testů se teď bude</span><span class="sxs-lookup"><span data-stu-id="2adec-299">Your test suite now becomes</span></span>

```csharp
public void GetDiscountedPrice_NotTuesday_ReturnsFullPrice()
{
    var priceCalculator = new PriceCalculator();
    var dateTimeProviderStub = new Mock<IDateTimeProvider>();
    dateTimeProviderStub.Setup(dtp => dtp.DayOfWeek()).Returns(DayOfWeek.Monday);

    var actual = priceCalculator.GetDiscountedPrice(2, dateTimeProviderStub);

    Assert.Equals(2, actual);
}

public void GetDiscountedPrice_OnTuesday_ReturnsHalfPrice()
{
    var priceCalculator = new PriceCalculator();
    var dateTimeProviderStub = new Mock<IDateTimeProvider>();
    dateTimeProviderStub.Setup(dtp => dtp.DayOfWeek()).Returns(DayOfWeek.Tuesday);

    var actual = priceCalculator.GetDiscountedPrice(2, dateTimeProviderStub);

    Assert.Equals(1, actual);
}
```

<span data-ttu-id="2adec-300">Sada testů nyní má úplnou kontrolu nad `DateTime.Now` a může při volání metody do této metody zástupné procedury jakékoli hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2adec-300">Now the test suite has full control over `DateTime.Now` and can stub any value when calling into the method.</span></span>
