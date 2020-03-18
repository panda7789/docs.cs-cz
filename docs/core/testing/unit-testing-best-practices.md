---
title: Doporučené postupy pro psaní testů částí
description: Seznamte se s osvědčenými postupy pro psaní testů částí, které pohánějí kvalitu a odolnost kódu pro projekty .NET Core a .NET Standard.
author: jpreese
ms.author: wiwagn
ms.date: 07/28/2018
ms.openlocfilehash: 586373381bcb18384cbf29bb2ca2bd220a2b2d3d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240958"
---
# <a name="unit-testing-best-practices-with-net-core-and-net-standard"></a><span data-ttu-id="8d6ae-103">Doporučené postupy testování částí pomocí rozhraní .NET Core a .NET Standard</span><span class="sxs-lookup"><span data-stu-id="8d6ae-103">Unit testing best practices with .NET Core and .NET Standard</span></span>

<span data-ttu-id="8d6ae-104">Existuje mnoho výhod pro psaní testů částí; pomáhají s regresí, poskytují dokumentaci a usnadňují dobrý design.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-104">There are numerous benefits to writing unit tests; they help with regression, provide documentation, and facilitate good design.</span></span> <span data-ttu-id="8d6ae-105">Však těžko čitelné a křehké testy částí může způsobit zmatek na základu kódu.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-105">However, hard to read and brittle unit tests can wreak havoc on your code base.</span></span> <span data-ttu-id="8d6ae-106">Tento článek popisuje některé osvědčené postupy týkající se návrhu testování částí pro projekty .NET Core a .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-106">This article describes some best practices regarding unit test design for your .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="8d6ae-107">V této příručce se dozvíte některé osvědčené postupy při psaní testů částí, aby vaše testy odolné a snadno pochopitelné.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-107">In this guide, you'll learn some best practices when writing unit tests to keep your tests resilient and easy to understand.</span></span>

<span data-ttu-id="8d6ae-108">[John Reese](https://reese.dev) se zvláštním poděkováním [Roy Osherove](https://osherove.com/)</span><span class="sxs-lookup"><span data-stu-id="8d6ae-108">By [John Reese](https://reese.dev) with special thanks to [Roy Osherove](https://osherove.com/)</span></span>

## <a name="why-unit-test"></a><span data-ttu-id="8d6ae-109">Proč jednotkový test?</span><span class="sxs-lookup"><span data-stu-id="8d6ae-109">Why unit test?</span></span>

### <a name="less-time-performing-functional-tests"></a><span data-ttu-id="8d6ae-110">Méně času při provádění funkčních testů</span><span class="sxs-lookup"><span data-stu-id="8d6ae-110">Less time performing functional tests</span></span>
<span data-ttu-id="8d6ae-111">Funkční testy jsou drahé.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-111">Functional tests are expensive.</span></span> <span data-ttu-id="8d6ae-112">Obvykle zahrnují otevření aplikace a provedení řady kroků, které musíte (nebo někdo jiný) provést, abyste ověřili očekávané chování.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-112">They typically involve opening up the application and performing a series of steps that you (or someone else), must follow in order to validate the expected behavior.</span></span> <span data-ttu-id="8d6ae-113">Tyto kroky nemusí být vždy známy testerovi, což znamená, že budou muset oslovit někoho, kdo je v této oblasti znalější, aby mohl provést test.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-113">These steps may not always be known to the tester, which means they will have to reach out to someone more knowledgeable in the area in order to carry out the test.</span></span> <span data-ttu-id="8d6ae-114">Testování samo o sobě může trvat několik sekund pro triviální změny nebo minuty pro větší změny.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-114">Testing itself could take seconds for trivial changes, or minutes for larger changes.</span></span> <span data-ttu-id="8d6ae-115">A konečně, tento proces musí být opakován pro každou změnu, kterou provedete v systému.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-115">Lastly, this process must be repeated for every change that you make in the system.</span></span>

<span data-ttu-id="8d6ae-116">Jednotkové testy, na druhé straně trvat milisekundy, lze spustit stisknutím tlačítka a nemusí nutně vyžadovat žádné znalosti systému jako celku.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-116">Unit tests, on the other hand, take milliseconds, can be run at the press of a button and do not necessarily require any knowledge of the system at large.</span></span> <span data-ttu-id="8d6ae-117">Zda test projde nebo neselže, je na testovacím běžci, ne na jednotlivci.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-117">Whether or not the test passes or fails is up to the test runner, not the individual.</span></span>

### <a name="protection-against-regression"></a><span data-ttu-id="8d6ae-118">Ochrana proti regresi</span><span class="sxs-lookup"><span data-stu-id="8d6ae-118">Protection against regression</span></span>
<span data-ttu-id="8d6ae-119">Regresní vady jsou vady, které jsou zavedeny při změně aplikace.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-119">Regression defects are defects that are introduced when a change is made to the application.</span></span> <span data-ttu-id="8d6ae-120">Je běžné, že testeři nejen otestují svou novou funkci, ale také funkce, které existovaly předem, aby ověřili, že dříve implementované funkce stále fungují podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-120">It is common for testers to not only test their new feature but also features that existed beforehand in order to verify that previously implemented features still function as expected.</span></span>

<span data-ttu-id="8d6ae-121">S testování částí, je možné znovu spustit celou sadu testů po každém sestavení nebo dokonce po změně řádku kódu.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-121">With unit testing, it's possible to rerun your entire suite of tests after every build or even after you change a line of code.</span></span> <span data-ttu-id="8d6ae-122">Dává vám jistotu, že váš nový kód nepřeruší existující funkce.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-122">Giving you confidence that your new code does not break existing functionality.</span></span>

### <a name="executable-documentation"></a><span data-ttu-id="8d6ae-123">Spustitelná dokumentace</span><span class="sxs-lookup"><span data-stu-id="8d6ae-123">Executable documentation</span></span>
<span data-ttu-id="8d6ae-124">Nemusí být vždy zřejmé, co konkrétní metoda dělá nebo jak se chová daný vstup.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-124">It may not always be obvious what a particular method does or how it behaves given a certain input.</span></span> <span data-ttu-id="8d6ae-125">Můžete se ptát sami sebe: Jak se tato metoda chová, když jí předávám prázdný řetězec?</span><span class="sxs-lookup"><span data-stu-id="8d6ae-125">You may ask yourself: How does this method behave if I pass it a blank string?</span></span> <span data-ttu-id="8d6ae-126">Null?</span><span class="sxs-lookup"><span data-stu-id="8d6ae-126">Null?</span></span>

<span data-ttu-id="8d6ae-127">Pokud máte sadu dobře pojmenované testy částí, každý test by měl být schopen jasně vysvětlit očekávaný výstup pro daný vstup.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-127">When you have a suite of well-named unit tests, each test should be able to clearly explain the expected output for a given input.</span></span> <span data-ttu-id="8d6ae-128">Kromě toho by měl být schopen ověřit, že skutečně funguje.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-128">In addition, it should be able to verify that it actually works.</span></span>

### <a name="less-coupled-code"></a><span data-ttu-id="8d6ae-129">Méně svázaný kód</span><span class="sxs-lookup"><span data-stu-id="8d6ae-129">Less coupled code</span></span>
<span data-ttu-id="8d6ae-130">Pokud je kód pevně spojen, může být obtížné jednotkový test.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-130">When code is tightly coupled, it can be difficult to unit test.</span></span> <span data-ttu-id="8d6ae-131">Bez vytváření testů částí pro kód, který píšete, může být párování méně zřejmé.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-131">Without creating unit tests for the code that you're writing, coupling may be less apparent.</span></span>

<span data-ttu-id="8d6ae-132">Psaní testů pro váš kód bude přirozeně oddělit váš kód, protože by bylo obtížnější otestovat jinak.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-132">Writing tests for your code will naturally decouple your code, because it would be more difficult to test otherwise.</span></span>

## <a name="characteristics-of-a-good-unit-test"></a><span data-ttu-id="8d6ae-133">Charakteristika dobré jednotkové zkoušky</span><span class="sxs-lookup"><span data-stu-id="8d6ae-133">Characteristics of a good unit test</span></span>

- <span data-ttu-id="8d6ae-134">**Rychle**.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-134">**Fast**.</span></span> <span data-ttu-id="8d6ae-135">Není neobvyklé pro vyspělé projekty mít tisíce testů částí.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-135">It is not uncommon for mature projects to have thousands of unit tests.</span></span> <span data-ttu-id="8d6ae-136">Testy částí by mělo trvat velmi málo času ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-136">Unit tests should take very little time to run.</span></span> <span data-ttu-id="8d6ae-137">Milisekund.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-137">Milliseconds.</span></span>
- <span data-ttu-id="8d6ae-138">**Izolované**.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-138">**Isolated**.</span></span> <span data-ttu-id="8d6ae-139">Testy částí jsou samostatné, lze spustit izolovaně a nemají žádné závislosti na externích faktorech, jako je například systém souborů nebo databáze.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-139">Unit tests are standalone, can be run in isolation, and have no dependencies on any outside factors such as a file system or database.</span></span>
- <span data-ttu-id="8d6ae-140">**Opakovatelné**.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-140">**Repeatable**.</span></span> <span data-ttu-id="8d6ae-141">Spuštění testování částí by měla být v souladu s jeho výsledky, to znamená, že vždy vrátí stejný výsledek, pokud nezměníte nic mezi spuštění.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-141">Running a unit test should be consistent with its results, that is, it always returns the same result if you do not change anything in between runs.</span></span>
- <span data-ttu-id="8d6ae-142">**Samokontroly**.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-142">**Self-Checking**.</span></span> <span data-ttu-id="8d6ae-143">Test by měl být schopen automaticky zjistit, zda prošel nebo selhal bez lidské interakce.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-143">The test should be able to automatically detect if it passed or failed without any human interaction.</span></span>
- <span data-ttu-id="8d6ae-144">**Včas**.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-144">**Timely**.</span></span> <span data-ttu-id="8d6ae-145">Testování částí by nemělo trvat nepřiměřeně dlouho psát ve srovnání s testovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-145">A unit test should not take a disproportionately long time to write compared to the code being tested.</span></span> <span data-ttu-id="8d6ae-146">Pokud zjistíte, testování kódu trvá velké množství času ve srovnání s psaní kódu, zvažte návrh, který je více testovatelné.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-146">If you find testing the code taking a large amount of time compared to writing the code, consider a design that is more testable.</span></span>

## <a name="lets-speak-the-same-language"></a><span data-ttu-id="8d6ae-147">Mluvme stejným jazykem.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-147">Let's speak the same language</span></span>
<span data-ttu-id="8d6ae-148">Termín *mock* je bohužel velmi zneužita, když mluví o testování.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-148">The term *mock* is unfortunately very misused when talking about testing.</span></span> <span data-ttu-id="8d6ae-149">Následující definuje nejběžnější typy *padělků* při psaní testů částí:</span><span class="sxs-lookup"><span data-stu-id="8d6ae-149">The following defines the most common types of *fakes* when writing unit tests:</span></span>

<span data-ttu-id="8d6ae-150">*Fake* - Falešný je obecný termín, který lze použít k popisu buď pahýl nebo mock objektu.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-150">*Fake* - A fake is a generic term which can be used to describe either a stub or a mock object.</span></span> <span data-ttu-id="8d6ae-151">Zda se jedná o zástupný kód nebo mock, závisí na kontextu, ve kterém se používá.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-151">Whether it is a stub or a mock depends on the context in which it's used.</span></span> <span data-ttu-id="8d6ae-152">Takže jinými slovy, padělek může být pahýl nebo výsměch.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-152">So in other words, a fake can be a stub or a mock.</span></span>

<span data-ttu-id="8d6ae-153">*Mock* - Mock objekt je falešný objekt v systému, který určuje, zda test jednotky prošel nebo se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-153">*Mock* - A mock object is a fake object in the system that decides whether or not a unit test has passed or failed.</span></span> <span data-ttu-id="8d6ae-154">Výsměch začíná jako Fake, dokud není uplatněna proti.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-154">A mock starts out as a Fake until it is asserted against.</span></span>

<span data-ttu-id="8d6ae-155">*Se zakázaným inzerováním* – zástupný kód je kontrolovatelnou náhradou existující závislosti (nebo spolupracovníka) v systému.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-155">*Stub* - A stub is a controllable replacement for an existing dependency (or collaborator) in the system.</span></span> <span data-ttu-id="8d6ae-156">Pomocí se zakázaným inzerováním můžete otestovat kód bez přímého řešení závislosti.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-156">By using a stub, you can test your code without dealing with the dependency directly.</span></span> <span data-ttu-id="8d6ae-157">Ve výchozím nastavení začíná falešný jako pahýl.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-157">By default, a fake starts out as a stub.</span></span>

<span data-ttu-id="8d6ae-158">Zvažte následující fragment kódu:</span><span class="sxs-lookup"><span data-stu-id="8d6ae-158">Consider the following code snippet:</span></span>

```csharp
var mockOrder = new MockOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="8d6ae-159">To by byl příklad pahýlu, který je označován jako výsměch.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-159">This would be an example of stub being referred to as a mock.</span></span> <span data-ttu-id="8d6ae-160">V tomto případě je to pahýl.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-160">In this case, it is a stub.</span></span> <span data-ttu-id="8d6ae-161">Jste právě kolem pořadí jako prostředek, aby bylo možné `Purchase` vytvořit konkretizovat (testovce systému).</span><span class="sxs-lookup"><span data-stu-id="8d6ae-161">You're just passing in the Order as a means to be able to instantiate `Purchase` (the system under test).</span></span> <span data-ttu-id="8d6ae-162">Název `MockOrder` je také velmi zavádějící, protože opět, pořadí není výsměch.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-162">The name `MockOrder` is also very misleading because again, the order is not a mock.</span></span>

<span data-ttu-id="8d6ae-163">Lepším přístupem by bylo</span><span class="sxs-lookup"><span data-stu-id="8d6ae-163">A better approach would be</span></span>

```csharp
var stubOrder = new FakeOrder();
var purchase = new Purchase(stubOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="8d6ae-164">Přejmenováním třídy `FakeOrder`na , jste udělali třídy mnohem obecnější, třídy lze použít jako mock nebo se zakázaným inzerováním.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-164">By renaming the class to `FakeOrder`, you've made the class a lot more generic, the class can be used as a mock or a stub.</span></span> <span data-ttu-id="8d6ae-165">Podle toho, co je lepší pro testovací případ.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-165">Whichever is better for the test case.</span></span> <span data-ttu-id="8d6ae-166">Ve výše uvedeném příkladu se `FakeOrder` používá jako zástupný kód.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-166">In the above example, `FakeOrder` is used as a stub.</span></span> <span data-ttu-id="8d6ae-167">Nepoužíváte `FakeOrder` v žádném tvaru nebo formě během assert.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-167">You're not using the `FakeOrder` in any shape or form during the assert.</span></span> <span data-ttu-id="8d6ae-168">`FakeOrder`byl právě předán `Purchase` do třídy, aby splňovaly požadavky konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-168">`FakeOrder` was just passed into the `Purchase` class to satisfy the requirements of the constructor.</span></span>

<span data-ttu-id="8d6ae-169">Chcete-li jej použít jako mock, můžete udělat něco takového</span><span class="sxs-lookup"><span data-stu-id="8d6ae-169">To use it as a Mock, you could do something like this</span></span>

```csharp
var mockOrder = new FakeOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(mockOrder.Validated);
```

<span data-ttu-id="8d6ae-170">V tomto případě kontrolujete vlastnost na Fake (uplatnění proti němu), takže ve výše uvedeném fragmentu `mockOrder` kódu je Mock.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-170">In this case, you are checking a property on the Fake (asserting against it), so in the above code snippet, the `mockOrder` is a Mock.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8d6ae-171">Je důležité, aby si tuto terminologii správné.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-171">It's important to get this terminology correct.</span></span> <span data-ttu-id="8d6ae-172">Pokud nazýváte vaše zástupné procedury "mocks", ostatní vývojáři budou dělat falešné předpoklady o vašem záměru.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-172">If you call your stubs "mocks", other developers are going to make false assumptions about your intent.</span></span>

<span data-ttu-id="8d6ae-173">Hlavní věc, kterou je třeba mít na paměti o mocks versus zástupné procedury je, že mocks jsou stejně jako zástupné procedury, ale tvrdíte proti mock objektu, zatímco vy netvrdí proti pahýl.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-173">The main thing to remember about mocks versus stubs is that mocks are just like stubs, but you assert against the mock object, whereas you do not assert against a stub.</span></span>

## <a name="best-practices"></a><span data-ttu-id="8d6ae-174">Osvědčené postupy</span><span class="sxs-lookup"><span data-stu-id="8d6ae-174">Best practices</span></span>

### <a name="naming-your-tests"></a><span data-ttu-id="8d6ae-175">Pojmenování testů</span><span class="sxs-lookup"><span data-stu-id="8d6ae-175">Naming your tests</span></span>
<span data-ttu-id="8d6ae-176">Název testu by se měl skládat ze tří částí:</span><span class="sxs-lookup"><span data-stu-id="8d6ae-176">The name of your test should consist of three parts:</span></span>

- <span data-ttu-id="8d6ae-177">Název testované metody.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-177">The name of the method being tested.</span></span>
- <span data-ttu-id="8d6ae-178">Scénář, podle kterého je testován.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-178">The scenario under which it's being tested.</span></span>
- <span data-ttu-id="8d6ae-179">Očekávané chování při vyvolání scénáře.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-179">The expected behavior when the scenario is invoked.</span></span>

#### <a name="why"></a><span data-ttu-id="8d6ae-180">Proč?</span><span class="sxs-lookup"><span data-stu-id="8d6ae-180">Why?</span></span>

- <span data-ttu-id="8d6ae-181">Pojmenování standardy jsou důležité, protože explicitně vyjádřit záměr testu.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-181">Naming standards are important because they explicitly express the intent of the test.</span></span>

<span data-ttu-id="8d6ae-182">Testy jsou více než jen ujistěte se, že váš kód funguje, ale také poskytují dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-182">Tests are more than just making sure your code works, they also provide documentation.</span></span> <span data-ttu-id="8d6ae-183">Jen při pohledu na sadu testů částí, měli byste být schopni odvodit chování kódu, aniž by i při pohledu na samotný kód.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-183">Just by looking at the suite of unit tests, you should be able to infer the behavior of your code without even looking at the code itself.</span></span> <span data-ttu-id="8d6ae-184">Navíc při selhání testů můžete přesně zobrazit scénáře, které nesplňují vaše očekávání.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-184">Additionally, when tests fail, you can see exactly which scenarios do not meet your expectations.</span></span>

#### <a name="bad"></a><span data-ttu-id="8d6ae-185">Chybně:</span><span class="sxs-lookup"><span data-stu-id="8d6ae-185">Bad:</span></span>
[!code-csharp[BeforeNaming](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeNaming)]

#### <a name="better"></a><span data-ttu-id="8d6ae-186">Lepší:</span><span class="sxs-lookup"><span data-stu-id="8d6ae-186">Better:</span></span>
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="arranging-your-tests"></a><span data-ttu-id="8d6ae-187">Uspořádání testů</span><span class="sxs-lookup"><span data-stu-id="8d6ae-187">Arranging your tests</span></span>
<span data-ttu-id="8d6ae-188">**Uspořádat, jednat, assert** je společný vzor při testování částí.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-188">**Arrange, Act, Assert** is a common pattern when unit testing.</span></span> <span data-ttu-id="8d6ae-189">Jak název napovídá, skládá se ze tří hlavních akcí:</span><span class="sxs-lookup"><span data-stu-id="8d6ae-189">As the name implies, it consists of three main actions:</span></span>

- <span data-ttu-id="8d6ae-190">*Uspořádejte* objekty, vytvářejte a nastavujte je podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-190">*Arrange* your objects, creating and setting them up as necessary.</span></span>
- <span data-ttu-id="8d6ae-191">*Jednat* na objekt.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-191">*Act* on an object.</span></span>
- <span data-ttu-id="8d6ae-192">*Tvrdí,* že něco je podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-192">*Assert* that something is as expected.</span></span>

#### <a name="why"></a><span data-ttu-id="8d6ae-193">Proč?</span><span class="sxs-lookup"><span data-stu-id="8d6ae-193">Why?</span></span>

- <span data-ttu-id="8d6ae-194">Jasně odděluje to, co je testováno, od *kroků uspořádat* a *uplatnit.*</span><span class="sxs-lookup"><span data-stu-id="8d6ae-194">Clearly separates what is being tested from the *arrange* and *assert* steps.</span></span>
- <span data-ttu-id="8d6ae-195">Menší šance na promíchání tvrzení s kódem "Act".</span><span class="sxs-lookup"><span data-stu-id="8d6ae-195">Less chance to intermix assertions with "Act" code.</span></span>

<span data-ttu-id="8d6ae-196">Čitelnost je jedním z nejdůležitějších aspektů při psaní testu.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-196">Readability is one of the most important aspects when writing a test.</span></span> <span data-ttu-id="8d6ae-197">Oddělení každé z těchto akcí v rámci testu jasně zvýraznit závislosti potřebné k volání kódu, jak je volán kód a co se pokoušíte uplatnit.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-197">Separating each of these actions within the test clearly highlight the dependencies required to call your code, how your code is being called, and what you are trying to assert.</span></span> <span data-ttu-id="8d6ae-198">I když může být možné kombinovat některé kroky a zmenšit velikost testu, primárním cílem je, aby byl test co nejčitelnější.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-198">While it may be possible to combine some steps and reduce the size of your test, the primary goal is to make the test as readable as possible.</span></span>

#### <a name="bad"></a><span data-ttu-id="8d6ae-199">Chybně:</span><span class="sxs-lookup"><span data-stu-id="8d6ae-199">Bad:</span></span>
[!code-csharp[BeforeArranging](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeArranging)]

#### <a name="better"></a><span data-ttu-id="8d6ae-200">Lepší:</span><span class="sxs-lookup"><span data-stu-id="8d6ae-200">Better:</span></span>
[!code-csharp[AfterArranging](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterArranging)]

### <a name="write-minimally-passing-tests"></a><span data-ttu-id="8d6ae-201">Zapsat minimálně absolvování testů</span><span class="sxs-lookup"><span data-stu-id="8d6ae-201">Write minimally passing tests</span></span>
<span data-ttu-id="8d6ae-202">Vstup, který má být použit v testování částí by měl být nejjednodušší možné za účelem ověření chování, které jsou aktuálně testování.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-202">The input to be used in a unit test should be the simplest possible in order to verify the behavior that you are currently testing.</span></span>

#### <a name="why"></a><span data-ttu-id="8d6ae-203">Proč?</span><span class="sxs-lookup"><span data-stu-id="8d6ae-203">Why?</span></span>

- <span data-ttu-id="8d6ae-204">Testy se stanou odolnější vůči budoucím změnám v základu kódu.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-204">Tests become more resilient to future changes in the codebase.</span></span>
- <span data-ttu-id="8d6ae-205">Blíže k testování chování nad implementací.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-205">Closer to testing behavior over implementation.</span></span>

<span data-ttu-id="8d6ae-206">Testy, které obsahují více informací, než je nutné projít testmají vyšší pravděpodobnost zavedení chyby do testu a může záměr testu méně jasné.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-206">Tests that include more information than required to pass the test have a higher chance of introducing errors into the test and can make the intent of the test less clear.</span></span> <span data-ttu-id="8d6ae-207">Při psaní testů se chcete zaměřit na chování.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-207">When writing tests you want to focus on the behavior.</span></span> <span data-ttu-id="8d6ae-208">Nastavení dalších vlastností u modelů nebo použití nenulových hodnot, pokud není požadováno, pouze snižuje to, co se pokoušíte prokázat.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-208">Setting extra properties on models or using non-zero values when not required, only detracts from what you are trying to prove.</span></span>

#### <a name="bad"></a><span data-ttu-id="8d6ae-209">Chybně:</span><span class="sxs-lookup"><span data-stu-id="8d6ae-209">Bad:</span></span>
[!code-csharp[BeforeMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMinimallyPassing)]

#### <a name="better"></a><span data-ttu-id="8d6ae-210">Lepší:</span><span class="sxs-lookup"><span data-stu-id="8d6ae-210">Better:</span></span>
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="avoid-magic-strings"></a><span data-ttu-id="8d6ae-211">Vyhněte se magické struny</span><span class="sxs-lookup"><span data-stu-id="8d6ae-211">Avoid magic strings</span></span>
<span data-ttu-id="8d6ae-212">Pojmenování proměnných v jednotkových testech je stejně důležité, ne-li důležitější než pojmenování proměnných v produkčním kódu.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-212">Naming variables in unit tests is as important, if not more important, than naming variables in production code.</span></span> <span data-ttu-id="8d6ae-213">Testy částí by neměly obsahovat magické řetězce.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-213">Unit tests should not contain magic strings.</span></span>

#### <a name="why"></a><span data-ttu-id="8d6ae-214">Proč?</span><span class="sxs-lookup"><span data-stu-id="8d6ae-214">Why?</span></span>

- <span data-ttu-id="8d6ae-215">Zabraňuje nutnosti pro čtenáře testu zkontrolovat výrobní kód, aby zjistili, co dělá hodnotu zvláštní.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-215">Prevents the need for the reader of the test to inspect the production code in order to figure out what makes the value special.</span></span>
- <span data-ttu-id="8d6ae-216">Výslovně ukazuje, co se snažíte *dokázat,* spíše než se snaží *dosáhnout*.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-216">Explicitly shows what you're trying to *prove* rather than trying to *accomplish*.</span></span>

<span data-ttu-id="8d6ae-217">Magické řetězce mohou způsobit zmatek pro čtenáře testů.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-217">Magic strings can cause confusion to the reader of your tests.</span></span> <span data-ttu-id="8d6ae-218">Pokud řetězec vypadá neobvyklé, mohou se divit, proč byla vybrána určitá hodnota pro parametr nebo vrácenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-218">If a string looks out of the ordinary, they may wonder why a certain value was chosen for a parameter or return value.</span></span> <span data-ttu-id="8d6ae-219">To může vést k bližšímu pohledu na podrobnosti implementace, spíše než se zaměřit na test.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-219">This may lead them to take a closer look at the implementation details, rather than focus on the test.</span></span>

> [!TIP]
> <span data-ttu-id="8d6ae-220">Při psaní testů, měli byste se snažit vyjádřit co největší záměr, jak je to možné.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-220">When writing tests, you should aim to express as much intent as possible.</span></span> <span data-ttu-id="8d6ae-221">V případě magických řetězců je dobrým přístupem přiřadit tyto hodnoty konstantám.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-221">In the case of magic strings, a good approach is to assign these values to constants.</span></span>

#### <a name="bad"></a><span data-ttu-id="8d6ae-222">Chybně:</span><span class="sxs-lookup"><span data-stu-id="8d6ae-222">Bad:</span></span>
[!code-csharp[BeforeMagicString](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMagicString)]

#### <a name="better"></a><span data-ttu-id="8d6ae-223">Lepší:</span><span class="sxs-lookup"><span data-stu-id="8d6ae-223">Better:</span></span>
[!code-csharp[AfterMagicString](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterMagicString)]

### <a name="avoid-logic-in-tests"></a><span data-ttu-id="8d6ae-224">Vyhněte se logice v testech</span><span class="sxs-lookup"><span data-stu-id="8d6ae-224">Avoid logic in tests</span></span>
<span data-ttu-id="8d6ae-225">Při psaní testů částí se vyhněte ručnímu `if` `while`zřetězení řetězců a logickým podmínkám, jako je například , , `for` `switch`, atd.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-225">When writing your unit tests avoid manual string concatenation and logical conditions such as `if`, `while`, `for`, `switch`, etc.</span></span>

#### <a name="why"></a><span data-ttu-id="8d6ae-226">Proč?</span><span class="sxs-lookup"><span data-stu-id="8d6ae-226">Why?</span></span>

- <span data-ttu-id="8d6ae-227">Menší šance na zavedení chyby uvnitř vašich testů.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-227">Less chance to introduce a bug inside of your tests.</span></span>
- <span data-ttu-id="8d6ae-228">Zaměřte se na konečný výsledek, spíše než podrobnosti implementace.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-228">Focus on the end result, rather than implementation details.</span></span>

<span data-ttu-id="8d6ae-229">Když do testovací sady zavedete logiku, šance na zavedení chyby do ní se dramaticky zvyšuje.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-229">When you introduce logic into your test suite, the chance of introducing a bug into it increases dramatically.</span></span> <span data-ttu-id="8d6ae-230">Poslední místo, které chcete najít chybu je ve vaší testovací sadě.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-230">The last place that you want to find a bug is within your test suite.</span></span> <span data-ttu-id="8d6ae-231">Měli byste mít vysokou úroveň důvěry, že vaše testy fungují, jinak jim nebudete věřit.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-231">You should have a high level of confidence that your tests work, otherwise, you will not trust them.</span></span> <span data-ttu-id="8d6ae-232">Testy, kterým nedůvěřujete, neposkytují žádnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-232">Tests that you do not trust, do not provide any value.</span></span> <span data-ttu-id="8d6ae-233">Pokud test selže, chcete mít pocit, že je něco skutečně v nepořádku s kódem a že jej nelze ignorovat.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-233">When a test fails, you want to have a sense that something is actually wrong with your code and that it cannot be ignored.</span></span>

> [!TIP]
> <span data-ttu-id="8d6ae-234">Pokud logika v testu se zdá nevyhnutelné, zvažte rozdělení testu do dvou nebo více různých testů.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-234">If logic in your test seems unavoidable, consider splitting the test up into two or more different tests.</span></span>

#### <a name="bad"></a><span data-ttu-id="8d6ae-235">Chybně:</span><span class="sxs-lookup"><span data-stu-id="8d6ae-235">Bad:</span></span>
[!code-csharp[LogicInTests](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#LogicInTests)]

#### <a name="better"></a><span data-ttu-id="8d6ae-236">Lepší:</span><span class="sxs-lookup"><span data-stu-id="8d6ae-236">Better:</span></span>
[!code-csharp[AfterTestLogic](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterTestLogic)]

### <a name="prefer-helper-methods-to-setup-and-teardown"></a><span data-ttu-id="8d6ae-237">Preferujte pomocné metody pro nastavení a stržení</span><span class="sxs-lookup"><span data-stu-id="8d6ae-237">Prefer helper methods to setup and teardown</span></span>
<span data-ttu-id="8d6ae-238">Pokud požadujete podobný objekt nebo stav pro testy, raději pomocnou metodu před využitím setup a Teardown atributy, pokud existují.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-238">If you require a similar object or state for your tests, prefer a helper method than leveraging Setup and Teardown attributes if they exist.</span></span>

#### <a name="why"></a><span data-ttu-id="8d6ae-239">Proč?</span><span class="sxs-lookup"><span data-stu-id="8d6ae-239">Why?</span></span>

- <span data-ttu-id="8d6ae-240">Méně nejasnosti při čtení testů, protože všechny kód je viditelný z každého testu.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-240">Less confusion when reading the tests since all of the code is visible from within each test.</span></span>
- <span data-ttu-id="8d6ae-241">Menší šance na nastavení příliš mnoho nebo příliš málo pro daný test.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-241">Less chance of setting up too much or too little for the given test.</span></span>
- <span data-ttu-id="8d6ae-242">Menší pravděpodobnost sdílení stavu mezi testy, které vytváří nežádoucí závislosti mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-242">Less chance of sharing state between tests which creates unwanted dependencies between them.</span></span>

<span data-ttu-id="8d6ae-243">V rámci testování `Setup` částí je volána před každý test jednotky v rámci testovací sady.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-243">In unit testing frameworks, `Setup` is called before each and every unit test within your test suite.</span></span> <span data-ttu-id="8d6ae-244">Zatímco někteří mohou vidět jako užitečný nástroj, to obecně skončí vedoucí k nafouklé a těžko čitelné testy.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-244">While some may see this as a useful tool, it generally ends up leading to bloated and hard to read tests.</span></span> <span data-ttu-id="8d6ae-245">Každý test bude mít obecně různé požadavky, aby se test zprovoznit.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-245">Each test will generally have different requirements in order to get the test up and running.</span></span> <span data-ttu-id="8d6ae-246">Bohužel, `Setup` nutí vás používat přesně stejné požadavky pro každý test.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-246">Unfortunately, `Setup` forces you to use the exact same requirements for each test.</span></span>

> [!NOTE]
> <span data-ttu-id="8d6ae-247">xUnit odebral jak SetUp, tak TearDown od verze 2.x</span><span class="sxs-lookup"><span data-stu-id="8d6ae-247">xUnit has removed both SetUp and TearDown as of version 2.x</span></span>

#### <a name="bad"></a><span data-ttu-id="8d6ae-248">Chybně:</span><span class="sxs-lookup"><span data-stu-id="8d6ae-248">Bad:</span></span>
[!code-csharp[BeforeSetup](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeSetup)]

```csharp
// more tests...
```

[!code-csharp[BeforeHelperMethod](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeHelperMethod)]

#### <a name="better"></a><span data-ttu-id="8d6ae-249">Lepší:</span><span class="sxs-lookup"><span data-stu-id="8d6ae-249">Better:</span></span>
[!code-csharp[AfterHelperMethod](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterHelperMethod)]

```csharp
// more tests...
```

[!code-csharp[AfterSetup](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterSetup)]

### <a name="avoid-multiple-asserts"></a><span data-ttu-id="8d6ae-250">Vyhněte se více násobným nepodmíněným výrazům</span><span class="sxs-lookup"><span data-stu-id="8d6ae-250">Avoid multiple asserts</span></span>
<span data-ttu-id="8d6ae-251">Při psaní testů se pokuste zahrnout pouze jeden assert na test.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-251">When writing your tests, try to only include one Assert per test.</span></span> <span data-ttu-id="8d6ae-252">Běžné přístupy k použití pouze jeden assert patří:</span><span class="sxs-lookup"><span data-stu-id="8d6ae-252">Common approaches to using only one assert include:</span></span>

- <span data-ttu-id="8d6ae-253">Vytvořte samostatný test pro každou neplatič.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-253">Create a separate test for each assert.</span></span>
- <span data-ttu-id="8d6ae-254">Použijte parametrizované testy.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-254">Use parameterized tests.</span></span>

#### <a name="why"></a><span data-ttu-id="8d6ae-255">Proč?</span><span class="sxs-lookup"><span data-stu-id="8d6ae-255">Why?</span></span>

- <span data-ttu-id="8d6ae-256">Pokud jeden Assert selže, následné Asserts nebudou vyhodnoceny.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-256">If one Assert fails, the subsequent Asserts will not be evaluated.</span></span>
- <span data-ttu-id="8d6ae-257">Zajišťuje, že neuplatňujete více případů v testech.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-257">Ensures you are not asserting multiple cases in your tests.</span></span>
- <span data-ttu-id="8d6ae-258">Dává vám celý obraz o tom, proč vaše testy selhávají.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-258">Gives you the entire picture as to why your tests are failing.</span></span>

<span data-ttu-id="8d6ae-259">Při zavádění více nepodmíněných výrazů do testovacího případu není zaručeno, že všechny nepodmíněných výrazů budou provedeny.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-259">When introducing multiple asserts into a test case, it is not guaranteed that all of the asserts will be executed.</span></span> <span data-ttu-id="8d6ae-260">Ve většině rozhraní testování částí, jakmile kontrolní výraz selže v testování částí, zkoušky řízení jsou automaticky považovány za selhání.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-260">In most unit testing frameworks, once an assertion fails in a unit test, the proceeding tests are automatically considered to be failing.</span></span> <span data-ttu-id="8d6ae-261">To může být matoucí jako funkce, která je skutečně funguje, se zobrazí jako selhání.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-261">This can be confusing as functionality that is actually working, will be shown as failing.</span></span>

> [!NOTE]
> <span data-ttu-id="8d6ae-262">Obvyklou výjimkou z tohoto pravidla je při uplatnění proti objektu.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-262">A common exception to this rule is when asserting against an object.</span></span> <span data-ttu-id="8d6ae-263">V tomto případě je obecně přijatelné mít více nepodmíněných výrazů proti každé vlastnosti, aby bylo zajištěno, že objekt je ve stavu, ve které očekáváte, že bude.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-263">In this case, it is generally acceptable to have multiple asserts against each property to ensure the object is in the state that you expect it to be in.</span></span>

#### <a name="bad"></a><span data-ttu-id="8d6ae-264">Chybně:</span><span class="sxs-lookup"><span data-stu-id="8d6ae-264">Bad:</span></span>
[!code-csharp[BeforeMultipleAsserts](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMultipleAsserts)]

#### <a name="better"></a><span data-ttu-id="8d6ae-265">Lepší:</span><span class="sxs-lookup"><span data-stu-id="8d6ae-265">Better:</span></span>
[!code-csharp[AfterMultipleAsserts](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterMultipleAsserts)]

### <a name="validate-private-methods-by-unit-testing-public-methods"></a><span data-ttu-id="8d6ae-266">Ověření soukromých metod pomocí testování veřejných metod testování částí</span><span class="sxs-lookup"><span data-stu-id="8d6ae-266">Validate private methods by unit testing public methods</span></span>
<span data-ttu-id="8d6ae-267">Ve většině případů by nemělo být nutné testovat soukromou metodu.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-267">In most cases, there should not be a need to test a private method.</span></span> <span data-ttu-id="8d6ae-268">Soukromé metody jsou podrobnosti implementace.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-268">Private methods are an implementation detail.</span></span> <span data-ttu-id="8d6ae-269">Můžete si to myslet takto: soukromé metody nikdy neexistují izolovaně.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-269">You can think of it this way: private methods never exist in isolation.</span></span> <span data-ttu-id="8d6ae-270">V určitém okamžiku bude existovat metoda, která bude čelit veřejnosti, která volá soukromou metodu jako součást jeho implementace.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-270">At some point, there is going to be a public facing method that calls the private method as part of its implementation.</span></span> <span data-ttu-id="8d6ae-271">Co byste měli starat o konečný výsledek veřejné metody, která volá do soukromého.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-271">What you should care about is the end result of the public method that calls into the private one.</span></span>

<span data-ttu-id="8d6ae-272">Vezměme si následující případ</span><span class="sxs-lookup"><span data-stu-id="8d6ae-272">Consider the following case</span></span>

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

<span data-ttu-id="8d6ae-273">Vaše první reakce může být začít `TrimInput` psát test, protože chcete, aby se ujistil, že metoda funguje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-273">Your first reaction may be to start writing a test for `TrimInput` because you want to make sure that the method is working as expected.</span></span> <span data-ttu-id="8d6ae-274">Je však zcela možné, `ParseLogLine` `sanitizedInput` že manipuluje takovým způsobem, že neočekáváte, vykreslování test proti `TrimInput` k ničemu.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-274">However, it is entirely possible that `ParseLogLine` manipulates `sanitizedInput` in such a way that you do not expect, rendering a test against `TrimInput` useless.</span></span>

<span data-ttu-id="8d6ae-275">Skutečný test by měl být proveden `ParseLogLine` proti veřejnosti čelí metoda, protože to je to, co byste měli nakonec záleží.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-275">The real test should be done against the public facing method `ParseLogLine` because that is what you should ultimately care about.</span></span>

```csharp
public void ParseLogLine_ByDefault_ReturnsTrimmedResult()
{
    var parser = new Parser();

    var result = parser.ParseLogLine(" a ");

    Assert.Equals("a", result);
}
```

<span data-ttu-id="8d6ae-276">S tímto hlediskem, pokud vidíte soukromou metodu, najděte veřejnou metodu a napište testy proti této metodě.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-276">With this viewpoint, if you see a private method, find the public method and write your tests against that method.</span></span> <span data-ttu-id="8d6ae-277">Jen proto, že soukromá metoda vrátí očekávaný výsledek, neznamená, že systém, který nakonec volá soukromou metodu, používá výsledek správně.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-277">Just because a private method returns the expected result, does not mean the system that eventually calls the private method uses the result correctly.</span></span>

### <a name="stub-static-references"></a><span data-ttu-id="8d6ae-278">Statické odkazy se zakázaným inzerováním</span><span class="sxs-lookup"><span data-stu-id="8d6ae-278">Stub static references</span></span>
<span data-ttu-id="8d6ae-279">Jednou ze zásad jednotkové zkoušky je, že musí mít plnou kontrolu nad zkoušenou soustavou.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-279">One of the principles of a unit test is that it must have full control of the system under test.</span></span> <span data-ttu-id="8d6ae-280">To může být problematické, pokud výrobní kód obsahuje volání `DateTime.Now`statických odkazů (např. ).</span><span class="sxs-lookup"><span data-stu-id="8d6ae-280">This can be problematic when production code includes calls to static references (e.g. `DateTime.Now`).</span></span> <span data-ttu-id="8d6ae-281">Zvažte následující kód</span><span class="sxs-lookup"><span data-stu-id="8d6ae-281">Consider the following code</span></span>

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

<span data-ttu-id="8d6ae-282">Jak může být tento kód testován na jednotku?</span><span class="sxs-lookup"><span data-stu-id="8d6ae-282">How can this code possibly be unit tested?</span></span> <span data-ttu-id="8d6ae-283">Můžete zkusit přístup, jako je</span><span class="sxs-lookup"><span data-stu-id="8d6ae-283">You may try an approach such as</span></span>

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

<span data-ttu-id="8d6ae-284">Bohužel si rychle uvědomíte, že s testy máte několik problémů.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-284">Unfortunately, you will quickly realize that there are a couple problems with your tests.</span></span>

- <span data-ttu-id="8d6ae-285">Pokud testovací sada je spuštěna v úterý, druhý test projde, ale první test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-285">If the test suite is run on a Tuesday, the second test will pass, but the first test will fail.</span></span>
- <span data-ttu-id="8d6ae-286">Pokud testovací sada je spuštěna na jiný den, první test projde, ale druhý test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-286">If the test suite is run on any other day, the first test will pass, but the second test will fail.</span></span>

<span data-ttu-id="8d6ae-287">Chcete-li tyto problémy vyřešit, budete muset zavést *šev* do produkčního kódu.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-287">To solve these problems, you'll need to introduce a *seam* into your production code.</span></span> <span data-ttu-id="8d6ae-288">Jedním z přístupů je zalomit kód, který je třeba řídit v rozhraní a mají produkční kód závisí na tomto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-288">One approach is to wrap the code that you need to control in an interface and have the production code depend on that interface.</span></span>

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

<span data-ttu-id="8d6ae-289">Testovací sada se nyní stává</span><span class="sxs-lookup"><span data-stu-id="8d6ae-289">Your test suite now becomes</span></span>

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

<span data-ttu-id="8d6ae-290">Nyní testovací sada má `DateTime.Now` plnou kontrolu nad a můžete se zakázaným inzerováním libovolnou hodnotu při volání do metody.</span><span class="sxs-lookup"><span data-stu-id="8d6ae-290">Now the test suite has full control over `DateTime.Now` and can stub any value when calling into the method.</span></span>
