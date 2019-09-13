---
title: Osvědčené postupy pro zápis testů jednotek
description: Naučte se osvědčené postupy pro psaní testů jednotek, které zajišťují kvalitu kódu a odolnost pro projekty .NET Core a .NET Standard.
author: jpreese
ms.author: wiwagn
ms.date: 07/28/2018
ms.custom: seodec18
ms.openlocfilehash: afd6e7e25573cbb571b225c263b9bcfccfca5647
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926389"
---
# <a name="unit-testing-best-practices-with-net-core-and-net-standard"></a><span data-ttu-id="4a8eb-103">Osvědčené postupy testování částí pomocí .NET Core a .NET Standard</span><span class="sxs-lookup"><span data-stu-id="4a8eb-103">Unit testing best practices with .NET Core and .NET Standard</span></span>

<span data-ttu-id="4a8eb-104">Při psaní testů jednotek je k dispozici mnoho výhod. pomáhají s regresí, poskytovat dokumentaci a usnadnit dobrý návrh.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-104">There are numerous benefits to writing unit tests; they help with regression, provide documentation, and facilitate good design.</span></span> <span data-ttu-id="4a8eb-105">Nicméně těžko čitelný a poměrně křehký testování částí může wreak zmatek na vašem základu kódu.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-105">However, hard to read and brittle unit tests can wreak havoc on your code base.</span></span> <span data-ttu-id="4a8eb-106">Tento článek popisuje některé osvědčené postupy týkající se návrhu testování částí pro projekty .NET Core a .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-106">This article describes some best practices regarding unit test design for your .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="4a8eb-107">V této příručce se dozvíte, jaké jsou osvědčené postupy při psaní testů jednotek pro zajištění odolnosti vašich testů a jejich snadné pochopení.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-107">In this guide, you'll learn some best practices when writing unit tests to keep your tests resilient and easy to understand.</span></span>

<span data-ttu-id="4a8eb-108">Od [Jan Reese](https://reese.dev) se speciálním poděkováním [Roy Osherove](https://osherove.com/)</span><span class="sxs-lookup"><span data-stu-id="4a8eb-108">By [John Reese](https://reese.dev) with special thanks to [Roy Osherove](https://osherove.com/)</span></span>

## <a name="why-unit-test"></a><span data-ttu-id="4a8eb-109">Proč testování částí?</span><span class="sxs-lookup"><span data-stu-id="4a8eb-109">Why unit test?</span></span>

### <a name="less-time-performing-functional-tests"></a><span data-ttu-id="4a8eb-110">Méně času provádění funkčních testů</span><span class="sxs-lookup"><span data-stu-id="4a8eb-110">Less time performing functional tests</span></span>
<span data-ttu-id="4a8eb-111">Funkční testy jsou nákladné.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-111">Functional tests are expensive.</span></span> <span data-ttu-id="4a8eb-112">Obvykle zahrnují otevření aplikace a provedení posloupnosti kroků (nebo někoho jiného), které je nutné provést, aby bylo možné ověřit očekávané chování.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-112">They typically involve opening up the application and performing a series of steps that you (or someone else), must follow in order to validate the expected behavior.</span></span> <span data-ttu-id="4a8eb-113">Tyto kroky nemusí být vždy známy testerovi, což znamená, že se budou muset obrátit na více znalostí v oblasti, aby bylo možné provést test.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-113">These steps may not always be known to the tester, which means they will have to reach out to someone more knowledgeable in the area in order to carry out the test.</span></span> <span data-ttu-id="4a8eb-114">Testování může trvat několik sekund, než se u triviálních změn nebo minut pro větší změny.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-114">Testing itself could take seconds for trivial changes, or minutes for larger changes.</span></span> <span data-ttu-id="4a8eb-115">Nakonec je třeba tento proces opakovat pro každou změnu, kterou v systému provedete.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-115">Lastly, this process must be repeated for every change that you make in the system.</span></span>

<span data-ttu-id="4a8eb-116">Testování částí na druhé straně může trvat milisekundy, které je možné spustit při stisknutí tlačítka a nemusí nutně vyžadovat, aby byly v systému velké znalosti.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-116">Unit tests, on the other hand, take milliseconds, can be run at the press of a button and do not necessarily require any knowledge of the system at large.</span></span> <span data-ttu-id="4a8eb-117">Bez ohledu na to, zda test projde nebo se nezdařil, je až do nástroje Test Runner, nikoli z jednotlivce.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-117">Whether or not the test passes or fails is up to the test runner, not the individual.</span></span>

### <a name="protection-against-regression"></a><span data-ttu-id="4a8eb-118">Ochrana před regresí</span><span class="sxs-lookup"><span data-stu-id="4a8eb-118">Protection against regression</span></span>
<span data-ttu-id="4a8eb-119">Chyby regrese jsou chyby, které jsou představeny, když je provedena změna aplikace.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-119">Regression defects are defects that are introduced when a change is made to the application.</span></span> <span data-ttu-id="4a8eb-120">Pro testery je běžné, že netestují pouze své nové funkce, ale také funkce, které existovaly předem, aby bylo možné ověřit, že dříve implementované funkce stále fungují podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-120">It is common for testers to not only test their new feature but also features that existed beforehand in order to verify that previously implemented features still function as expected.</span></span>

<span data-ttu-id="4a8eb-121">Při testování částí je možné znovu spustit celou sadu testů po každém sestavení nebo dokonce i po změně řádku kódu.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-121">With unit testing, it's possible to rerun your entire suite of tests after every build or even after you change a line of code.</span></span> <span data-ttu-id="4a8eb-122">Máte jistotu, že nový kód neruší existující funkce.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-122">Giving you confidence that your new code does not break existing functionality.</span></span>

### <a name="executable-documentation"></a><span data-ttu-id="4a8eb-123">Dokumentace ke spustitelnému souboru</span><span class="sxs-lookup"><span data-stu-id="4a8eb-123">Executable documentation</span></span>
<span data-ttu-id="4a8eb-124">Nemusí vždy být zřejmé, co konkrétní metoda dělá nebo jak se chová podle určitého vstupu.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-124">It may not always be obvious what a particular method does or how it behaves given a certain input.</span></span> <span data-ttu-id="4a8eb-125">Můžete se zeptat sami: Jak se tato metoda chová, když ji předáte do prázdného řetězce?</span><span class="sxs-lookup"><span data-stu-id="4a8eb-125">You may ask yourself: How does this method behave if I pass it a blank string?</span></span> <span data-ttu-id="4a8eb-126">Platnost?</span><span class="sxs-lookup"><span data-stu-id="4a8eb-126">Null?</span></span>

<span data-ttu-id="4a8eb-127">Máte-li sadu dobře pojmenovaných testů jednotek, každý test by měl být schopný jasně vysvětlit očekávaný výstup pro daný vstup.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-127">When you have a suite of well-named unit tests, each test should be able to clearly explain the expected output for a given input.</span></span> <span data-ttu-id="4a8eb-128">Kromě toho by měl být schopný ověřit, zda skutečně funguje.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-128">In addition, it should be able to verify that it actually works.</span></span>

### <a name="less-coupled-code"></a><span data-ttu-id="4a8eb-129">Méně spojený kód</span><span class="sxs-lookup"><span data-stu-id="4a8eb-129">Less coupled code</span></span>
<span data-ttu-id="4a8eb-130">Když je kód pevně spojený, může být obtížné testování částí.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-130">When code is tightly coupled, it can be difficult to unit test.</span></span> <span data-ttu-id="4a8eb-131">Bez vytváření testů jednotek pro kód, který zapisujete, může být spojení neviditelné.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-131">Without creating unit tests for the code that you're writing, coupling may be less apparent.</span></span>

<span data-ttu-id="4a8eb-132">Zápis testů pro váš kód bude přirozeně oddělit váš kód, protože by bylo obtížnější ho testovat jinak.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-132">Writing tests for your code will naturally decouple your code, because it would be more difficult to test otherwise.</span></span>

## <a name="characteristics-of-a-good-unit-test"></a><span data-ttu-id="4a8eb-133">Charakteristiky dobrého testu jednotek</span><span class="sxs-lookup"><span data-stu-id="4a8eb-133">Characteristics of a good unit test</span></span>

- <span data-ttu-id="4a8eb-134">**Rychle**.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-134">**Fast**.</span></span> <span data-ttu-id="4a8eb-135">Pro vyspělé projekty nemusíte mít k dispozici tisíce testů jednotek.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-135">It is not uncommon for mature projects to have thousands of unit tests.</span></span> <span data-ttu-id="4a8eb-136">Spuštění testů jednotek by mělo trvat velmi málo času.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-136">Unit tests should take very little time to run.</span></span> <span data-ttu-id="4a8eb-137">Milisekund.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-137">Milliseconds.</span></span>
- <span data-ttu-id="4a8eb-138">**Izolované**.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-138">**Isolated**.</span></span> <span data-ttu-id="4a8eb-139">Jednotkové testy jsou samostatné, můžou být spouštěny izolovaně a nesmí mít žádné závislosti na žádných jiných faktorech, jako je třeba systém souborů nebo databáze.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-139">Unit tests are standalone, can be run in isolation, and have no dependencies on any outside factors such as a file system or database.</span></span>
- <span data-ttu-id="4a8eb-140">**Opakuje**se.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-140">**Repeatable**.</span></span> <span data-ttu-id="4a8eb-141">Spuštění testu jednotky by mělo být konzistentní s jeho výsledky, to znamená, že vždy vrátí stejný výsledek, pokud neměníte cokoli v průběhu spuštění.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-141">Running a unit test should be consistent with its results, that is, it always returns the same result if you do not change anything in between runs.</span></span>
- <span data-ttu-id="4a8eb-142">**Automatická kontrola**.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-142">**Self-Checking**.</span></span> <span data-ttu-id="4a8eb-143">Test by měl být schopný automaticky zjistit, jestli byl úspěšný nebo neúspěšný, bez jakékoli lidské interakce.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-143">The test should be able to automatically detect if it passed or failed without any human interaction.</span></span>
- <span data-ttu-id="4a8eb-144">**Včas**.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-144">**Timely**.</span></span> <span data-ttu-id="4a8eb-145">Testování částí by nemělo mít v porovnání s testovaným kódem neúměrně dlouhou dobu.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-145">A unit test should not take a disproportionately long time to write compared to the code being tested.</span></span> <span data-ttu-id="4a8eb-146">Pokud najdete testování kódu, které trvá v porovnání s psaním kódu velké množství času, zvažte návrh, který je více testovatelné.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-146">If you find testing the code taking a large amount of time compared to writing the code, consider a design that is more testable.</span></span>

## <a name="lets-speak-the-same-language"></a><span data-ttu-id="4a8eb-147">Pojďme hovořit o stejný jazyk</span><span class="sxs-lookup"><span data-stu-id="4a8eb-147">Let's speak the same language</span></span>
<span data-ttu-id="4a8eb-148">Při komunikaci s testováním je *Tento pojem velmi* nepoužit.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-148">The term *mock* is unfortunately very misused when talking about testing.</span></span> <span data-ttu-id="4a8eb-149">Následující text definuje nejběžnější typy *napodobenin* při psaní testů jednotek:</span><span class="sxs-lookup"><span data-stu-id="4a8eb-149">The following defines the most common types of *fakes* when writing unit tests:</span></span>

<span data-ttu-id="4a8eb-150">*Napodobeniny* – napodobenina je obecný termín, který lze použít k popisu zástupné procedury nebo objektu objektu.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-150">*Fake* - A fake is a generic term which can be used to describe either a stub or a mock object.</span></span> <span data-ttu-id="4a8eb-151">Bez ohledu na to, jestli se jedná o zástupnou proceduru nebo objekt, závisí na kontextu, ve kterém se používá.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-151">Whether it is a stub or a mock depends on the context in which it's used.</span></span> <span data-ttu-id="4a8eb-152">Jinak řečeno, napodobenina může být zástupná procedura nebo maketa.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-152">So in other words, a fake can be a stub or a mock.</span></span>

<span data-ttu-id="4a8eb-153">*Model* – objekt typu Object je falešným objektem v systému, který určuje, zda nebo není test jednotky úspěšný nebo neúspěšný.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-153">*Mock* - A mock object is a fake object in the system that decides whether or not a unit test has passed or failed.</span></span> <span data-ttu-id="4a8eb-154">Napodobení se zahájí jako napodobenina, dokud není uplatněna na.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-154">A mock starts out as a Fake until it is asserted against.</span></span>

<span data-ttu-id="4a8eb-155">*Zástupná* procedura – zástupný kód pro existující závislost (nebo spolupracovníka) v systému je ovladatelné přístupnou náhradou.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-155">*Stub* - A stub is a controllable replacement for an existing dependency (or collaborator) in the system.</span></span> <span data-ttu-id="4a8eb-156">Pomocí zástupné procedury můžete testovat kód bez nutnosti pracovat přímo se závislostí.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-156">By using a stub, you can test your code without dealing with the dependency directly.</span></span> <span data-ttu-id="4a8eb-157">Ve výchozím nastavení se napodobenina zahájí jako zástupná procedura.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-157">By default, a fake starts out as a stub.</span></span>

<span data-ttu-id="4a8eb-158">Vezměte v úvahu následující fragment kódu:</span><span class="sxs-lookup"><span data-stu-id="4a8eb-158">Consider the following code snippet:</span></span>

```csharp
var mockOrder = new MockOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="4a8eb-159">Toto je příklad zástupné procedury, která se označuje jako objekt typu.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-159">This would be an example of stub being referred to as a mock.</span></span> <span data-ttu-id="4a8eb-160">V tomto případě se jedná o zástupnou proceduru.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-160">In this case, it is a stub.</span></span> <span data-ttu-id="4a8eb-161">Právě předáváte v pořadí jako prostředek, který je možné vytvořit `Purchase` (testovaný systém).</span><span class="sxs-lookup"><span data-stu-id="4a8eb-161">You're just passing in the Order as a means to be able to instantiate `Purchase` (the system under test).</span></span> <span data-ttu-id="4a8eb-162">Název `MockOrder` je také velmi zavádějící, protože znovu není v pořádku.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-162">The name `MockOrder` is also very misleading because again, the order is not a mock.</span></span>

<span data-ttu-id="4a8eb-163">Lepší přístup by byl</span><span class="sxs-lookup"><span data-stu-id="4a8eb-163">A better approach would be</span></span>

```csharp
var stubOrder = new FakeOrder();
var purchase = new Purchase(stubOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="4a8eb-164">Přejmenováním třídy na `FakeOrder`, jste vytvořili třídu a mnohem obecnější, třídu lze použít jako objekt typu nebo jako zástupnou proceduru.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-164">By renaming the class to `FakeOrder`, you've made the class a lot more generic, the class can be used as a mock or a stub.</span></span> <span data-ttu-id="4a8eb-165">Podle toho, co je vhodnější pro testovací případ.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-165">Whichever is better for the test case.</span></span> <span data-ttu-id="4a8eb-166">Ve výše uvedeném příkladu `FakeOrder` se používá jako zástupná procedura.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-166">In the above example, `FakeOrder` is used as a stub.</span></span> <span data-ttu-id="4a8eb-167">Nepoužíváte `FakeOrder` ho v žádném tvaru nebo formuláři během kontrolního výrazu.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-167">You're not using the `FakeOrder` in any shape or form during the assert.</span></span> <span data-ttu-id="4a8eb-168">`FakeOrder`byla právě předána do `Purchase` třídy, aby splňovala požadavky konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-168">`FakeOrder` was just passed into the `Purchase` class to satisfy the requirements of the constructor.</span></span>

<span data-ttu-id="4a8eb-169">Pokud ho chcete použít jako objekt, může to vypadat nějak takto.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-169">To use it as a Mock, you could do something like this</span></span>

```csharp
var mockOrder = new FakeOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(mockOrder.Validated);
```

<span data-ttu-id="4a8eb-170">V tomto případě kontrolujete vlastnost s napodobeninou (pro kterou je uplatněno), takže ve výše uvedeném fragmentu `mockOrder` kódu je objekt typu.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-170">In this case, you are checking a property on the Fake (asserting against it), so in the above code snippet, the `mockOrder` is a Mock.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4a8eb-171">Je důležité získat správnou opravu této terminologie.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-171">It's important to get this terminology correct.</span></span> <span data-ttu-id="4a8eb-172">Pokud voláte své zástupné procedury, ostatní vývojáři budou mít na záměr nepravdivé předpoklady.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-172">If you call your stubs "mocks", other developers are going to make false assumptions about your intent.</span></span>

<span data-ttu-id="4a8eb-173">Hlavním aspektem, který si zapamatujete o postupných objektech oproti zástupným procedurám, je to, že jsou jako zástupné procedury stejné jako zástupné procedury.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-173">The main thing to remember about mocks versus stubs is that mocks are just like stubs, but you assert against the mock object, whereas you do not assert against a stub.</span></span>

## <a name="best-practices"></a><span data-ttu-id="4a8eb-174">Osvědčené postupy</span><span class="sxs-lookup"><span data-stu-id="4a8eb-174">Best practices</span></span>

### <a name="naming-your-tests"></a><span data-ttu-id="4a8eb-175">Pojmenovávání testů</span><span class="sxs-lookup"><span data-stu-id="4a8eb-175">Naming your tests</span></span>
<span data-ttu-id="4a8eb-176">Název testu by měl sestávat ze tří částí:</span><span class="sxs-lookup"><span data-stu-id="4a8eb-176">The name of your test should consist of three parts:</span></span>

- <span data-ttu-id="4a8eb-177">Název testované metody.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-177">The name of the method being tested.</span></span>
- <span data-ttu-id="4a8eb-178">Scénář, pod kterým se testuje.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-178">The scenario under which it's being tested.</span></span>
- <span data-ttu-id="4a8eb-179">Očekávané chování při vyvolání scénáře.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-179">The expected behavior when the scenario is invoked.</span></span>

#### <a name="why"></a><span data-ttu-id="4a8eb-180">Proč?</span><span class="sxs-lookup"><span data-stu-id="4a8eb-180">Why?</span></span>

- <span data-ttu-id="4a8eb-181">Standardy pojmenování jsou důležité, protože explicitně vyjadřují záměr testu.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-181">Naming standards are important because they explicitly express the intent of the test.</span></span>

<span data-ttu-id="4a8eb-182">Testy jsou více, než pouze zajištění, že váš kód funguje, ale také poskytují dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-182">Tests are more than just making sure your code works, they also provide documentation.</span></span> <span data-ttu-id="4a8eb-183">Stejně jako při prohlížení sady jednotkových testů byste měli být schopni odvodit chování kódu bez ohledu na samotný kód.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-183">Just by looking at the suite of unit tests, you should be able to infer the behavior of your code without even looking at the code itself.</span></span> <span data-ttu-id="4a8eb-184">Kromě toho, když testy selžou, vidíte přesně ty scénáře, které nesplňují vaše očekávání.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-184">Additionally, when tests fail, you can see exactly which scenarios do not meet your expectations.</span></span>

#### <a name="bad"></a><span data-ttu-id="4a8eb-185">Špatné:</span><span class="sxs-lookup"><span data-stu-id="4a8eb-185">Bad:</span></span>
[!code-csharp[BeforeNaming](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeNaming)]

#### <a name="better"></a><span data-ttu-id="4a8eb-186">Zájmu</span><span class="sxs-lookup"><span data-stu-id="4a8eb-186">Better:</span></span>
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="arranging-your-tests"></a><span data-ttu-id="4a8eb-187">Uspořádání testů</span><span class="sxs-lookup"><span data-stu-id="4a8eb-187">Arranging your tests</span></span>
<span data-ttu-id="4a8eb-188">**Uspořádat, ACT a Assert** je běžný vzor při testování částí.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-188">**Arrange, Act, Assert** is a common pattern when unit testing.</span></span> <span data-ttu-id="4a8eb-189">Jak název naznačuje, skládá se ze tří hlavních akcí:</span><span class="sxs-lookup"><span data-stu-id="4a8eb-189">As the name implies, it consists of three main actions:</span></span>

- <span data-ttu-id="4a8eb-190">*Uspořádejte* své objekty, vytvářejte je a nastavte je podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-190">*Arrange* your objects, creating and setting them up as necessary.</span></span>
- <span data-ttu-id="4a8eb-191">*Pracovat* na objektu.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-191">*Act* on an object.</span></span>
- <span data-ttu-id="4a8eb-192">Vyhodnotit *, že* je něco podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-192">*Assert* that something is as expected.</span></span>

#### <a name="why"></a><span data-ttu-id="4a8eb-193">Proč?</span><span class="sxs-lookup"><span data-stu-id="4a8eb-193">Why?</span></span>

- <span data-ttu-id="4a8eb-194">Jasně odděluje, co je testováno z kroků *uspořádání* a *vyhodnocení* .</span><span class="sxs-lookup"><span data-stu-id="4a8eb-194">Clearly separates what is being tested from the *arrange* and *assert* steps.</span></span>
- <span data-ttu-id="4a8eb-195">Možnost Intermix kontrolní výrazy s kódem Act je menší.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-195">Less chance to intermix assertions with "Act" code.</span></span>

<span data-ttu-id="4a8eb-196">Čitelnost je jedním z nejdůležitějších aspektů při psaní testu.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-196">Readability is one of the most important aspects when writing a test.</span></span> <span data-ttu-id="4a8eb-197">Oddělení každé z těchto akcí v rámci testu jasně zvýrazní závislosti vyžadované pro volání vašeho kódu, způsob, jakým je váš kód volán a co se snažíte uplatnit.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-197">Separating each of these actions within the test clearly highlight the dependencies required to call your code, how your code is being called, and what you are trying to assert.</span></span> <span data-ttu-id="4a8eb-198">I když může být možné zkombinovat některé kroky a zmenšit velikost testu, primárním cílem je udělat co možná čitelnou zkoušku.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-198">While it may be possible to combine some steps and reduce the size of your test, the primary goal is to make the test as readable as possible.</span></span>

#### <a name="bad"></a><span data-ttu-id="4a8eb-199">Špatné:</span><span class="sxs-lookup"><span data-stu-id="4a8eb-199">Bad:</span></span>
[!code-csharp[BeforeArranging](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeArranging)]

#### <a name="better"></a><span data-ttu-id="4a8eb-200">Zájmu</span><span class="sxs-lookup"><span data-stu-id="4a8eb-200">Better:</span></span>
[!code-csharp[AfterArranging](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterArranging)]

### <a name="write-minimally-passing-tests"></a><span data-ttu-id="4a8eb-201">Zápis s minimálním předáním testů</span><span class="sxs-lookup"><span data-stu-id="4a8eb-201">Write minimally passing tests</span></span>
<span data-ttu-id="4a8eb-202">Vstup, který se má použít v testu jednotek, by měl být nejjednodušší, aby bylo možné ověřit chování, které právě testujete.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-202">The input to be used in a unit test should be the simplest possible in order to verify the behavior that you are currently testing.</span></span>

#### <a name="why"></a><span data-ttu-id="4a8eb-203">Proč?</span><span class="sxs-lookup"><span data-stu-id="4a8eb-203">Why?</span></span>

- <span data-ttu-id="4a8eb-204">Testy jsou odolnější vůči budoucím změnám v základu kódu.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-204">Tests become more resilient to future changes in the codebase.</span></span>
- <span data-ttu-id="4a8eb-205">Blíže k testovacímu chování při implementaci.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-205">Closer to testing behavior over implementation.</span></span>

<span data-ttu-id="4a8eb-206">Testy, které obsahují více informací, než je nutné k předání testu, mají větší šanci na zavedení chyb do testu a může udělat záměr méně jasného záměru testu.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-206">Tests that include more information than required to pass the test have a higher chance of introducing errors into the test and can make the intent of the test less clear.</span></span> <span data-ttu-id="4a8eb-207">Při psaní testů, které chcete zaměřit na chování.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-207">When writing tests you want to focus on the behavior.</span></span> <span data-ttu-id="4a8eb-208">Nastavení zvláštních vlastností pro modely nebo použití nenulových hodnot v případě potřeby, pouze odčítání od toho, co se snažíte prokázat.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-208">Setting extra properties on models or using non-zero values when not required, only detracts from what you are trying to prove.</span></span>

#### <a name="bad"></a><span data-ttu-id="4a8eb-209">Špatné:</span><span class="sxs-lookup"><span data-stu-id="4a8eb-209">Bad:</span></span>
[!code-csharp[BeforeMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMinimallyPassing)]

#### <a name="better"></a><span data-ttu-id="4a8eb-210">Zájmu</span><span class="sxs-lookup"><span data-stu-id="4a8eb-210">Better:</span></span>
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="avoid-magic-strings"></a><span data-ttu-id="4a8eb-211">Nepoužívejte řetězce Magic</span><span class="sxs-lookup"><span data-stu-id="4a8eb-211">Avoid magic strings</span></span>
<span data-ttu-id="4a8eb-212">Při pojmenování proměnných v testování částí je důležité, pokud není důležitější, než proměnné pojmenování v produkčním kódu.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-212">Naming variables in unit tests is as important, if not more important, than naming variables in production code.</span></span> <span data-ttu-id="4a8eb-213">Testy jednotek by neměly obsahovat řetězce Magic.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-213">Unit tests should not contain magic strings.</span></span>

#### <a name="why"></a><span data-ttu-id="4a8eb-214">Proč?</span><span class="sxs-lookup"><span data-stu-id="4a8eb-214">Why?</span></span>

- <span data-ttu-id="4a8eb-215">Brání nutnosti čtenářům testu zkontrolovat kód v produkčním prostředí, aby bylo možné zjistit, co dělá tuto hodnotu jako speciální.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-215">Prevents the need for the reader of the test to inspect the production code in order to figure out what makes the value special.</span></span>
- <span data-ttu-id="4a8eb-216">Explicitně ukazuje, co se snažíte *dokázat* , a ne pokusit se o jeho *provedení*.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-216">Explicitly shows what you're trying to *prove* rather than trying to *accomplish*.</span></span>

<span data-ttu-id="4a8eb-217">Řetězce Magic můžou způsobit nejasnost čtenářů vašich testů.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-217">Magic strings can cause confusion to the reader of your tests.</span></span> <span data-ttu-id="4a8eb-218">Pokud je řetězec vyhledáný běžným způsobem, může se stát, že se pro parametr nebo návratovou hodnotu vybere určitá hodnota.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-218">If a string looks out of the ordinary, they may wonder why a certain value was chosen for a parameter or return value.</span></span> <span data-ttu-id="4a8eb-219">To může způsobit, že se podíváme na podrobnosti implementace, ale nemusíte se zaměřit na test.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-219">This may lead them to take a closer look at the implementation details, rather than focus on the test.</span></span>

> [!TIP] 
> <span data-ttu-id="4a8eb-220">Při psaní testů byste se měli zaměřit na co nejvíc záměrů.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-220">When writing tests, you should aim to express as much intent as possible.</span></span> <span data-ttu-id="4a8eb-221">V případě řetězců Magic je dobrým přístupem přiřadit tyto hodnoty konstantám.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-221">In the case of magic strings, a good approach is to assign these values to constants.</span></span>

#### <a name="bad"></a><span data-ttu-id="4a8eb-222">Špatné:</span><span class="sxs-lookup"><span data-stu-id="4a8eb-222">Bad:</span></span>
[!code-csharp[BeforeMagicString](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMagicString)]

#### <a name="better"></a><span data-ttu-id="4a8eb-223">Zájmu</span><span class="sxs-lookup"><span data-stu-id="4a8eb-223">Better:</span></span>
[!code-csharp[AfterMagicString](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterMagicString)]

### <a name="avoid-logic-in-tests"></a><span data-ttu-id="4a8eb-224">Vyhnout se logice v testech</span><span class="sxs-lookup"><span data-stu-id="4a8eb-224">Avoid logic in tests</span></span>
<span data-ttu-id="4a8eb-225">Při psaní testů jednotek vyhnout se ručnímu zřetězení řetězců a logickým podmínkám `if` `for`, `while`jako například `switch`,,, atd.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-225">When writing your unit tests avoid manual string concatenation and logical conditions such as `if`, `while`, `for`, `switch`, etc.</span></span>

#### <a name="why"></a><span data-ttu-id="4a8eb-226">Proč?</span><span class="sxs-lookup"><span data-stu-id="4a8eb-226">Why?</span></span>

- <span data-ttu-id="4a8eb-227">Menší šance na zavedení chyby uvnitř testů.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-227">Less chance to introduce a bug inside of your tests.</span></span>
- <span data-ttu-id="4a8eb-228">Zaměřte se na konečný výsledek místo podrobností implementace.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-228">Focus on the end result, rather than implementation details.</span></span>

<span data-ttu-id="4a8eb-229">Když zavedete logiku do sady testů, šance na to, že dojde k chybě, se výrazně zvyšuje.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-229">When you introduce logic into your test suite, the chance of introducing a bug into it increases dramatically.</span></span> <span data-ttu-id="4a8eb-230">Poslední místo, kde chcete najít chybu, je v rámci sady testů.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-230">The last place that you want to find a bug is within your test suite.</span></span> <span data-ttu-id="4a8eb-231">Měli byste mít vysokou úroveň spolehlivosti, kterou testy fungují, jinak je nebudete důvěřovat.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-231">You should have a high level of confidence that your tests work, otherwise, you will not trust them.</span></span> <span data-ttu-id="4a8eb-232">Testy, kterým nedůvěřujete, nezadávají žádnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-232">Tests that you do not trust, do not provide any value.</span></span> <span data-ttu-id="4a8eb-233">Pokud se test nezdaří, chcete mít smysl, že něco je ve skutečnosti chybné s vaším kódem a že jej nelze ignorovat.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-233">When a test fails, you want to have a sense that something is actually wrong with your code and that it cannot be ignored.</span></span>

> [!TIP]
> <span data-ttu-id="4a8eb-234">Pokud se logika v testu jeví jako nenevyhnutelná, zvažte rozdělení testu na dva nebo více různých testů.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-234">If logic in your test seems unavoidable, consider splitting the test up into two or more different tests.</span></span>

#### <a name="bad"></a><span data-ttu-id="4a8eb-235">Špatné:</span><span class="sxs-lookup"><span data-stu-id="4a8eb-235">Bad:</span></span>
[!code-csharp[LogicInTests](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#LogicInTests)]

#### <a name="better"></a><span data-ttu-id="4a8eb-236">Zájmu</span><span class="sxs-lookup"><span data-stu-id="4a8eb-236">Better:</span></span>
[!code-csharp[AfterTestLogic](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterTestLogic)]

### <a name="prefer-helper-methods-to-setup-and-teardown"></a><span data-ttu-id="4a8eb-237">Preferovat pomocné metody nastavení a rozboru</span><span class="sxs-lookup"><span data-stu-id="4a8eb-237">Prefer helper methods to setup and teardown</span></span>
<span data-ttu-id="4a8eb-238">Pokud pro testy požadujete podobný objekt nebo stav, preferovat pomocnou metodu než využití atributů Setup a rozboru, pokud existují.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-238">If you require a similar object or state for your tests, prefer a helper method than leveraging Setup and Teardown attributes if they exist.</span></span>

#### <a name="why"></a><span data-ttu-id="4a8eb-239">Proč?</span><span class="sxs-lookup"><span data-stu-id="4a8eb-239">Why?</span></span>

- <span data-ttu-id="4a8eb-240">Při čtení testů došlo k méně nejasnostem, protože veškerý kód je viditelný v rámci každého testu.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-240">Less confusion when reading the tests since all of the code is visible from within each test.</span></span>
- <span data-ttu-id="4a8eb-241">Menší pravděpodobnost nastavení pro daný test je příliš velká nebo příliš malá.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-241">Less chance of setting up too much or too little for the given test.</span></span>
- <span data-ttu-id="4a8eb-242">Menší šance na stav sdílení mezi testy, které mezi nimi vytváří nežádoucí závislosti.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-242">Less chance of sharing state between tests which creates unwanted dependencies between them.</span></span>

<span data-ttu-id="4a8eb-243">V rozhraních `Setup` testování částí je volána před každou a každou jednotkovou zkouškou v rámci sady testů.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-243">In unit testing frameworks, `Setup` is called before each and every unit test within your test suite.</span></span> <span data-ttu-id="4a8eb-244">I když se některý z nich může zobrazit jako užitečný nástroj, obvykle končí na bloated a těžko čte testy.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-244">While some may see this as a useful tool, it generally ends up leading to bloated and hard to read tests.</span></span> <span data-ttu-id="4a8eb-245">Každý test bude mít k dispozici různé požadavky, aby bylo možné spustit test a začít.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-245">Each test will generally have different requirements in order to get the test up and running.</span></span> <span data-ttu-id="4a8eb-246">Bohužel vynutí, `Setup` abyste pro každý test používali přesně stejné požadavky.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-246">Unfortunately, `Setup` forces you to use the exact same requirements for each test.</span></span>

> [!NOTE] 
> <span data-ttu-id="4a8eb-247">xUnit odebral SetUp i rozboru od verze 2. x</span><span class="sxs-lookup"><span data-stu-id="4a8eb-247">xUnit has removed both SetUp and TearDown as of version 2.x</span></span>

#### <a name="bad"></a><span data-ttu-id="4a8eb-248">Špatné:</span><span class="sxs-lookup"><span data-stu-id="4a8eb-248">Bad:</span></span>
[!code-csharp[BeforeSetup](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeSetup)]

```csharp
// more tests...
```

[!code-csharp[BeforeHelperMethod](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeHelperMethod)]

#### <a name="better"></a><span data-ttu-id="4a8eb-249">Zájmu</span><span class="sxs-lookup"><span data-stu-id="4a8eb-249">Better:</span></span>
[!code-csharp[AfterHelperMethod](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterHelperMethod)]

```csharp
// more tests...
```

[!code-csharp[AfterSetup](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterSetup)]

### <a name="avoid-multiple-asserts"></a><span data-ttu-id="4a8eb-250">Vyhněte se několika kontrolním výrazům</span><span class="sxs-lookup"><span data-stu-id="4a8eb-250">Avoid multiple asserts</span></span>
<span data-ttu-id="4a8eb-251">Při psaní testů se pokuste zahrnout pouze jeden kontrolní výraz na test.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-251">When writing your tests, try to only include one Assert per test.</span></span> <span data-ttu-id="4a8eb-252">Mezi běžné přístupy k použití pouze jednoho vyhodnocení patří:</span><span class="sxs-lookup"><span data-stu-id="4a8eb-252">Common approaches to using only one assert include:</span></span>

- <span data-ttu-id="4a8eb-253">Vytvořte samostatný test pro každý kontrolní výraz.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-253">Create a separate test for each assert.</span></span>
- <span data-ttu-id="4a8eb-254">Použijte parametrizované testy.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-254">Use parameterized tests.</span></span>

#### <a name="why"></a><span data-ttu-id="4a8eb-255">Proč?</span><span class="sxs-lookup"><span data-stu-id="4a8eb-255">Why?</span></span>

- <span data-ttu-id="4a8eb-256">Pokud jeden kontrolní výraz selže, následné kontrolní výrazy nebudou vyhodnoceny.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-256">If one Assert fails, the subsequent Asserts will not be evaluated.</span></span>
- <span data-ttu-id="4a8eb-257">Zajistíte, že ve svých testech neuplatňujete více případů.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-257">Ensures you are not asserting multiple cases in your tests.</span></span>
- <span data-ttu-id="4a8eb-258">Poskytuje celý obrázek jako důvod selhání testů.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-258">Gives you the entire picture as to why your tests are failing.</span></span> 

<span data-ttu-id="4a8eb-259">Při zavedení více kontrolních výrazů do testovacího případu není zaručeno, že budou provedeny všechny kontrolní výrazy.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-259">When introducing multiple asserts into a test case, it is not guaranteed that all of the asserts will be executed.</span></span> <span data-ttu-id="4a8eb-260">Ve většině rozhraních testování částí se po selhání kontrolního výrazu v testu jednotky automaticky považují testy pokračování za neúspěšné.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-260">In most unit testing frameworks, once an assertion fails in a unit test, the proceeding tests are automatically considered to be failing.</span></span> <span data-ttu-id="4a8eb-261">To může být matoucí, protože funkce, které skutečně fungují, se budou zobrazovat jako neúspěšné.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-261">This can be confusing as functionality that is actually working, will be shown as failing.</span></span>

> [!NOTE]
> <span data-ttu-id="4a8eb-262">Běžnou výjimkou z tohoto pravidla je při uplatnění na objekt.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-262">A common exception to this rule is when asserting against an object.</span></span> <span data-ttu-id="4a8eb-263">V tomto případě je všeobecně přijatelné mít více kontrolních výrazů proti každé vlastnosti, aby bylo zajištěno, že objekt je ve stavu, ve kterém očekáváte.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-263">In this case, it is generally acceptable to have multiple asserts against each property to ensure the object is in the state that you expect it to be in.</span></span>

#### <a name="bad"></a><span data-ttu-id="4a8eb-264">Špatné:</span><span class="sxs-lookup"><span data-stu-id="4a8eb-264">Bad:</span></span>
[!code-csharp[BeforeMultipleAsserts](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMultipleAsserts)]

#### <a name="better"></a><span data-ttu-id="4a8eb-265">Zájmu</span><span class="sxs-lookup"><span data-stu-id="4a8eb-265">Better:</span></span>
[!code-csharp[AfterMultipleAsserts](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterMultipleAsserts)]

### <a name="validate-private-methods-by-unit-testing-public-methods"></a><span data-ttu-id="4a8eb-266">Ověřit soukromé metody pomocí veřejných metod testování částí</span><span class="sxs-lookup"><span data-stu-id="4a8eb-266">Validate private methods by unit testing public methods</span></span>
<span data-ttu-id="4a8eb-267">Ve většině případů by nemělo být nutné testovat soukromou metodu.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-267">In most cases, there should not be a need to test a private method.</span></span> <span data-ttu-id="4a8eb-268">Soukromé metody jsou podrobné informace o implementaci.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-268">Private methods are an implementation detail.</span></span> <span data-ttu-id="4a8eb-269">Tímto způsobem si můžete představit: soukromé metody nikdy neexistují v izolaci.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-269">You can think of it this way: private methods never exist in isolation.</span></span> <span data-ttu-id="4a8eb-270">V určitém okamžiku se jedná o veřejnou metodu, která volá soukromou metodu jako součást její implementace.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-270">At some point, there is going to be a public facing method that calls the private method as part of its implementation.</span></span> <span data-ttu-id="4a8eb-271">To, co byste měli dbát, je konečný výsledek veřejné metody, která volá do privátního.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-271">What you should care about is the end result of the public method that calls into the private one.</span></span> 

<span data-ttu-id="4a8eb-272">Vezměte v úvahu následující případ:</span><span class="sxs-lookup"><span data-stu-id="4a8eb-272">Consider the following case</span></span>

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

<span data-ttu-id="4a8eb-273">První reakce může být začít psát test pro `TrimInput` , protože chcete zajistit, aby metoda fungovala podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-273">Your first reaction may be to start writing a test for `TrimInput` because you want to make sure that the method is working as expected.</span></span> <span data-ttu-id="4a8eb-274">Je však možné, že `ParseLogLine` je zcela možné `sanitizedInput` manipulovat takovým způsobem, že neočekáváte, vygenerování testu proti `TrimInput` nevýhodám.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-274">However, it is entirely possible that `ParseLogLine` manipulates `sanitizedInput` in such a way that you do not expect, rendering a test against `TrimInput` useless.</span></span> 

<span data-ttu-id="4a8eb-275">Skutečný test by měl být proveden proti veřejné metodě `ParseLogLine` , protože to je to, co byste měli v konečném případě zajímat.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-275">The real test should be done against the public facing method `ParseLogLine` because that is what you should ultimately care about.</span></span> 

```csharp
public void ParseLogLine_ByDefault_ReturnsTrimmedResult()
{
    var parser = new Parser();

    var result = parser.ParseLogLine(" a ");

    Assert.Equals("a", result);
}
```

<span data-ttu-id="4a8eb-276">S tímto pohledem, pokud vidíte soukromou metodu, vyhledejte veřejnou metodu a zapište testy proti této metodě.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-276">With this viewpoint, if you see a private method, find the public method and write your tests against that method.</span></span> <span data-ttu-id="4a8eb-277">Vzhledem k tomu, že soukromá metoda vrátí očekávaný výsledek, neznamená to, že systém, který nakonec volá privátní metodu, používá výsledek správně.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-277">Just because a private method returns the expected result, does not mean the system that eventually calls the private method uses the result correctly.</span></span>

### <a name="stub-static-references"></a><span data-ttu-id="4a8eb-278">Statické odkazy na zástupné procedury</span><span class="sxs-lookup"><span data-stu-id="4a8eb-278">Stub static references</span></span>
<span data-ttu-id="4a8eb-279">Jedním ze zásad testování částí je, že musí mít plnou kontrolu nad testovaným systémem.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-279">One of the principles of a unit test is that it must have full control of the system under test.</span></span> <span data-ttu-id="4a8eb-280">To může být problematické, pokud výrobní kód zahrnuje volání statických odkazů ( `DateTime.Now`např.).</span><span class="sxs-lookup"><span data-stu-id="4a8eb-280">This can be problematic when production code includes calls to static references (e.g. `DateTime.Now`).</span></span> <span data-ttu-id="4a8eb-281">Vezměte v úvahu následující kód:</span><span class="sxs-lookup"><span data-stu-id="4a8eb-281">Consider the following code</span></span>

```csharp
public int GetDiscountedPrice(int price)
{
    if(DateTime.Now.DayOfWeek == DayOfWeek.Tuesday) 
    {
        return price / 2;
    }
    else 
    {
        return price;
    }
}
```

<span data-ttu-id="4a8eb-282">Jak může být tento kód testován jednotkou?</span><span class="sxs-lookup"><span data-stu-id="4a8eb-282">How can this code possibly be unit tested?</span></span> <span data-ttu-id="4a8eb-283">Můžete vyzkoušet přístup jako</span><span class="sxs-lookup"><span data-stu-id="4a8eb-283">You may try an approach such as</span></span>

```csharp
public void GetDiscountedPrice_ByDefault_ReturnsFullPrice()
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

<span data-ttu-id="4a8eb-284">Bohužel rychle zjistíte, že existuje několik problémů s vašimi testy.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-284">Unfortunately, you will quickly realize that there are a couple problems with your tests.</span></span> 

- <span data-ttu-id="4a8eb-285">Pokud je testovací sada spuštěna v úterý, druhý test projde, ale první test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-285">If the test suite is run on a Tuesday, the second test will pass, but the first test will fail.</span></span>
- <span data-ttu-id="4a8eb-286">Pokud je testovací sada spuštěna v jakémkoli jiném dni, bude první test úspěšný, ale druhý test selže.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-286">If the test suite is run on any other day, the first test will pass, but the second test will fail.</span></span>

<span data-ttu-id="4a8eb-287">Chcete-li tyto problémy vyřešit, budete muset uvést do svého produkčního kódu *spojku* .</span><span class="sxs-lookup"><span data-stu-id="4a8eb-287">To solve these problems, you'll need to introduce a *seam* into your production code.</span></span> <span data-ttu-id="4a8eb-288">Jedním z možností je zabalit kód, který je třeba ovládat v rozhraní a mít kód produkčního prostředí závislý na tomto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-288">One approach is to wrap the code that you need to control in an interface and have the production code depend on that interface.</span></span>

```csharp
public interface IDateTimeProvider
{
    DayOfWeek DayOfWeek();
}

public int GetDiscountedPrice(int price, IDateTimeProvider dateTimeProvider)
{
    if(dateTimeProvider.DayOfWeek() == DayOfWeek.Tuesday) 
    {
        return price / 2;
    }
    else 
    {
        return price;
    }
}
```

<span data-ttu-id="4a8eb-289">Vaše sada testů se teď bude</span><span class="sxs-lookup"><span data-stu-id="4a8eb-289">Your test suite now becomes</span></span>

```csharp
public void GetDiscountedPrice_ByDefault_ReturnsFullPrice()
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

<span data-ttu-id="4a8eb-290">Sada testů nyní má úplnou kontrolu nad `DateTime.Now` a může při volání metody do této metody zástupné procedury jakékoli hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4a8eb-290">Now the test suite has full control over `DateTime.Now` and can stub any value when calling into the method.</span></span>
