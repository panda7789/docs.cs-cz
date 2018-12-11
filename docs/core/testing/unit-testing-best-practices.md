---
title: Osvědčené postupy pro zápis testů jednotek
description: Přečtěte si osvědčené postupy pro zápis testů jednotek, které řídí kvalitu kódu a odolnosti
author: jpreese
ms.author: wiwagn
ms.date: 07/28/2018
ms.custom: seodec18
ms.openlocfilehash: 60baa533a8f4dc2fb715b813018f8f84000777d7
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169616"
---
# <a name="unit-testing-best-practices"></a><span data-ttu-id="22a1e-103">Testování osvědčených postupů</span><span class="sxs-lookup"><span data-stu-id="22a1e-103">Unit testing best practices</span></span>

<span data-ttu-id="22a1e-104">Podle [Jan Reese](http://reesespieces.io) se zvláštními k [Roy Osherove](http://osherove.com/)</span><span class="sxs-lookup"><span data-stu-id="22a1e-104">By [John Reese](http://reesespieces.io) with special thanks to [Roy Osherove](http://osherove.com/)</span></span>

<span data-ttu-id="22a1e-105">Existuje mnoho výhod zápis testů jednotek; pomáhají s regrese, poskytují dokumentaci a usnadňují dobrý návrh.</span><span class="sxs-lookup"><span data-stu-id="22a1e-105">There are numerous benefits to writing unit tests; they help with regression, provide documentation, and facilitate good design.</span></span> <span data-ttu-id="22a1e-106">Obtížné číst a křehký jednotkové testy lze však způsobí zmatek v vašeho základu kódu.</span><span class="sxs-lookup"><span data-stu-id="22a1e-106">However, hard to read and brittle unit tests can wreak havoc on your code base.</span></span>

<span data-ttu-id="22a1e-107">V této příručce se dozvíte některé osvědčené postupy při psaní testů jednotek se testy odolné a snadno pochopitelná.</span><span class="sxs-lookup"><span data-stu-id="22a1e-107">In this guide, you'll learn some best practices when writing unit tests to keep your tests resilient and easy to understand.</span></span>

## <a name="why-unit-test"></a><span data-ttu-id="22a1e-108">Proč pro testování částí?</span><span class="sxs-lookup"><span data-stu-id="22a1e-108">Why unit test?</span></span>

### <a name="less-time-performing-functional-tests"></a><span data-ttu-id="22a1e-109">Méně času provádění funkční testy</span><span class="sxs-lookup"><span data-stu-id="22a1e-109">Less time performing functional tests</span></span>
<span data-ttu-id="22a1e-110">Funkční testy jsou nákladné.</span><span class="sxs-lookup"><span data-stu-id="22a1e-110">Functional tests are expensive.</span></span> <span data-ttu-id="22a1e-111">Obvykle zahrnují pouhému spuštění aplikace a provádění posloupnosti kroků, které můžete (nebo někomu jinému), musíte provést, chcete-li ověřit, že očekávané chování.</span><span class="sxs-lookup"><span data-stu-id="22a1e-111">They typically involve opening up the application and performing a series of steps that you (or someone else), must follow in order to validate the expected behavior.</span></span> <span data-ttu-id="22a1e-112">Tyto kroky nemusí být vždy známá testerovi, což znamená, že budou muset kontaktovat někomu více-li hlubší znalosti v oblasti za účelem provádění testu.</span><span class="sxs-lookup"><span data-stu-id="22a1e-112">These steps may not always be known to the tester, which means they will have to reach out to someone more knowledgeable in the area in order to carry out the test.</span></span> <span data-ttu-id="22a1e-113">Vlastní testování může trvat sekund pro jednoduché změny nebo minut, než větší změny.</span><span class="sxs-lookup"><span data-stu-id="22a1e-113">Testing itself could take seconds for trivial changes, or minutes for larger changes.</span></span> <span data-ttu-id="22a1e-114">A konečně tento proces opakuje pro každé změny provedené v systému.</span><span class="sxs-lookup"><span data-stu-id="22a1e-114">Lastly, this process must be repeated for every change that you make in the system.</span></span>

<span data-ttu-id="22a1e-115">Testy jednotek, na druhé straně, trvat milisekund, můžete spustit stisknutím tlačítka a nevyžadují žádnou znalost systému ve velkém.</span><span class="sxs-lookup"><span data-stu-id="22a1e-115">Unit tests, on the other hand, take milliseconds, can be run at the press of a button and do not necessarily require any knowledge of the system at large.</span></span> <span data-ttu-id="22a1e-116">Určuje, jestli test projde nebo selže záleží nástroje test runner, ne jednotlivec.</span><span class="sxs-lookup"><span data-stu-id="22a1e-116">Whether or not the test passes or fails is up to the test runner, not the individual.</span></span>

### <a name="protection-against-regression"></a><span data-ttu-id="22a1e-117">Ochrana proti regrese</span><span class="sxs-lookup"><span data-stu-id="22a1e-117">Protection against regression</span></span>
<span data-ttu-id="22a1e-118">Vady regrese jsou chyby, které se zavedly při změně do aplikace.</span><span class="sxs-lookup"><span data-stu-id="22a1e-118">Regression defects are defects that are introduced when a change is made to the application.</span></span> <span data-ttu-id="22a1e-119">Je běžné pro testery, nejen otestovat jejich novou funkci, ale také funkce, které existovaly předem za účelem ověření, které dřív implementovaná funkce fungují i podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="22a1e-119">It is common for testers to not only test their new feature but also features that existed beforehand in order to verify that previously implemented features still function as expected.</span></span>

<span data-ttu-id="22a1e-120">S testováním částí je možné spustit znovu vaše celou sadu testů po každém sestavení nebo dokonce i po změně řádku kódu.</span><span class="sxs-lookup"><span data-stu-id="22a1e-120">With unit testing, it's possible to rerun your entire suite of tests after every build or even after you change a line of code.</span></span> <span data-ttu-id="22a1e-121">Díky tomu získáte jistotu, že váš nový kód nedojde k poškození stávajících funkcí.</span><span class="sxs-lookup"><span data-stu-id="22a1e-121">Giving you confidence that your new code does not break existing functionality.</span></span>

### <a name="executable-documentation"></a><span data-ttu-id="22a1e-122">Spustitelný soubor dokumentace</span><span class="sxs-lookup"><span data-stu-id="22a1e-122">Executable documentation</span></span>
<span data-ttu-id="22a1e-123">Nemusí být vždy zřejmé čemu konkrétní metody nebo chování dané určité vstup.</span><span class="sxs-lookup"><span data-stu-id="22a1e-123">It may not always be obvious what a particular method does or how it behaves given a certain input.</span></span> <span data-ttu-id="22a1e-124">Vám může položte si otázku: Jak tato metoda chovat když překročím je prázdný řetězec?</span><span class="sxs-lookup"><span data-stu-id="22a1e-124">You may ask yourself: How does this method behave if I pass it a blank string?</span></span> <span data-ttu-id="22a1e-125">Hodnota Null?</span><span class="sxs-lookup"><span data-stu-id="22a1e-125">Null?</span></span>

<span data-ttu-id="22a1e-126">Pokud máte sadu dobře pojmenované jednotkové testy, měli být schopni jasně vysvětlit očekávaný výstup pro daný vstup každého testu.</span><span class="sxs-lookup"><span data-stu-id="22a1e-126">When you have a suite of well-named unit tests, each test should be able to clearly explain the expected output for a given input.</span></span> <span data-ttu-id="22a1e-127">Kromě toho by měl být schopen ověřit, že ve skutečnosti funguje.</span><span class="sxs-lookup"><span data-stu-id="22a1e-127">In addition, it should be able to verify that it actually works.</span></span>

### <a name="less-coupled-code"></a><span data-ttu-id="22a1e-128">Méně propojených kódu</span><span class="sxs-lookup"><span data-stu-id="22a1e-128">Less coupled code</span></span>
<span data-ttu-id="22a1e-129">Pokud kód je úzce svázány, může být obtížné testování částí.</span><span class="sxs-lookup"><span data-stu-id="22a1e-129">When code is tightly coupled, it can be difficult to unit test.</span></span> <span data-ttu-id="22a1e-130">Bez vytvoření testů jednotek pro kód, který píšete, může být méně zřejmé párování.</span><span class="sxs-lookup"><span data-stu-id="22a1e-130">Without creating unit tests for the code that you're writing, coupling may be less apparent.</span></span>

<span data-ttu-id="22a1e-131">Psaní testů pro váš kód bude přirozeně oddělit váš kód, protože by byla obtížnější testovat jinak.</span><span class="sxs-lookup"><span data-stu-id="22a1e-131">Writing tests for your code will naturally decouple your code, because it would be more difficult to test otherwise.</span></span>

## <a name="characteristics-of-a-good-unit-test"></a><span data-ttu-id="22a1e-132">Vlastnosti dobré Jednotkový test</span><span class="sxs-lookup"><span data-stu-id="22a1e-132">Characteristics of a good unit test</span></span>
- <span data-ttu-id="22a1e-133">**Rychlé**.</span><span class="sxs-lookup"><span data-stu-id="22a1e-133">**Fast**.</span></span> <span data-ttu-id="22a1e-134">Není, až po zralé projekty tisícovky rozhraní testování částí.</span><span class="sxs-lookup"><span data-stu-id="22a1e-134">It is not uncommon for mature projects to have thousands of unit tests.</span></span> <span data-ttu-id="22a1e-135">Testy jednotek by měla trvat velmi málo času spuštění.</span><span class="sxs-lookup"><span data-stu-id="22a1e-135">Unit tests should take very little time to run.</span></span> <span data-ttu-id="22a1e-136">Milisekundy.</span><span class="sxs-lookup"><span data-stu-id="22a1e-136">Milliseconds.</span></span>
- <span data-ttu-id="22a1e-137">**Izolované**.</span><span class="sxs-lookup"><span data-stu-id="22a1e-137">**Isolated**.</span></span> <span data-ttu-id="22a1e-138">Testování částí jsou samostatný, můžete spustit v izolaci a nemají žádné závislosti na jakýkoli vnější faktory, jako je systém souborů nebo databáze.</span><span class="sxs-lookup"><span data-stu-id="22a1e-138">Unit tests are standalone, can be run in isolation, and have no dependencies on any outside factors such as a file system or database.</span></span>
- <span data-ttu-id="22a1e-139">**Opakovatelné**.</span><span class="sxs-lookup"><span data-stu-id="22a1e-139">**Repeatable**.</span></span> <span data-ttu-id="22a1e-140">Testování částí by měl být konzistentní s jeho výsledky, to znamená, vždy vrátí stejného výsledku Pokud něco mezi spuštění nelze změnit.</span><span class="sxs-lookup"><span data-stu-id="22a1e-140">Running a unit test should be consistent with its results, that is, it always returns the same result if you do not change anything in between runs.</span></span>
- <span data-ttu-id="22a1e-141">**Kontroluje se svým**.</span><span class="sxs-lookup"><span data-stu-id="22a1e-141">**Self-Checking**.</span></span> <span data-ttu-id="22a1e-142">Test by měl být dokáže automaticky rozpoznat, pokud byl úspěšný, nebo bez zásahu člověka.</span><span class="sxs-lookup"><span data-stu-id="22a1e-142">The test should be able to automatically detect if it passed or failed without any human interaction.</span></span>
- <span data-ttu-id="22a1e-143">**Včasné**.</span><span class="sxs-lookup"><span data-stu-id="22a1e-143">**Timely**.</span></span> <span data-ttu-id="22a1e-144">Testování částí, neměla by mít Neproporcionální změna dlouhou dobu pro zápis ve srovnání s testovaný kód.</span><span class="sxs-lookup"><span data-stu-id="22a1e-144">A unit test should not take a disproportionally long time to write compared to the code being tested.</span></span> <span data-ttu-id="22a1e-145">Pokud zjistíte testování kódu, přičemž velké množství času ve srovnání s psaní kódu, zvažte návrh, který je víc možností intenzivního testování.</span><span class="sxs-lookup"><span data-stu-id="22a1e-145">If you find testing the code taking a large amount of time compared to writing the code, consider a design that is more testable.</span></span>

## <a name="lets-speak-the-same-language"></a><span data-ttu-id="22a1e-146">Můžeme mluvit stejný jazyk</span><span class="sxs-lookup"><span data-stu-id="22a1e-146">Let's speak the same language</span></span>
<span data-ttu-id="22a1e-147">Termín *napodobení* je bohužel chybná, když mluvíme o testování.</span><span class="sxs-lookup"><span data-stu-id="22a1e-147">The term *mock* is unfortunately very misused when talking about testing.</span></span> <span data-ttu-id="22a1e-148">Definuje následující nejběžnější typy *napodobenin* při psaní testů jednotek:</span><span class="sxs-lookup"><span data-stu-id="22a1e-148">The following defines the most common types of *fakes* when writing unit tests:</span></span>

<span data-ttu-id="22a1e-149">*Falešné* – phishing je obecný termín, který slouží k popisu zástupnou proceduru nebo mock objektu.</span><span class="sxs-lookup"><span data-stu-id="22a1e-149">*Fake* - A fake is a generic term which can be used to describe either a stub or a mock object.</span></span> <span data-ttu-id="22a1e-150">Zda je zástupná procedura nebo model závisí na kontextu, ve kterém se používá.</span><span class="sxs-lookup"><span data-stu-id="22a1e-150">Whether it is a stub or a mock depends on the context in which it's used.</span></span> <span data-ttu-id="22a1e-151">Tak jinými slovy, phishing může být zástupnou proceduru nebo model.</span><span class="sxs-lookup"><span data-stu-id="22a1e-151">So in other words, a fake can be a stub or a mock.</span></span>

<span data-ttu-id="22a1e-152">*Napodobení* -mock objektu je objekt falešné v systému, která určuje, zda má testování částí úspěšný nebo neúspěšný.</span><span class="sxs-lookup"><span data-stu-id="22a1e-152">*Mock* - A mock object is a fake object in the system that decides whether or not a unit test has passed or failed.</span></span> <span data-ttu-id="22a1e-153">Model vychází phishing dokud je uplatněna proti.</span><span class="sxs-lookup"><span data-stu-id="22a1e-153">A mock starts out as a Fake until it is asserted against.</span></span>

<span data-ttu-id="22a1e-154">*Zástupná procedura* -zástupná procedura představuje může ovládat nahrazení existujícího závislosti (nebo spolupracovníka) v systému.</span><span class="sxs-lookup"><span data-stu-id="22a1e-154">*Stub* - A stub is a controllable replacement for an existing dependency (or collaborator) in the system.</span></span> <span data-ttu-id="22a1e-155">Pomocí zástupné procedury můžete otestovat váš kód se schématy závislost přímo.</span><span class="sxs-lookup"><span data-stu-id="22a1e-155">By using a stub, you can test your code without dealing with the dependency directly.</span></span> <span data-ttu-id="22a1e-156">Ve výchozím nastavení phishing začíná jako zástupná procedura.</span><span class="sxs-lookup"><span data-stu-id="22a1e-156">By default, a fake starts out as a stub.</span></span>

<span data-ttu-id="22a1e-157">Vezměte v úvahu následující fragment kódu:</span><span class="sxs-lookup"><span data-stu-id="22a1e-157">Consider the following code snippet:</span></span>

```csharp
var mockOrder = new MockOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="22a1e-158">To může být příklad zástupné procedury jsou označovány jako model.</span><span class="sxs-lookup"><span data-stu-id="22a1e-158">This would be an example of stub being referred to as a mock.</span></span> <span data-ttu-id="22a1e-159">V takovém případě je zástupná procedura.</span><span class="sxs-lookup"><span data-stu-id="22a1e-159">In this case, it is a stub.</span></span> <span data-ttu-id="22a1e-160">Už se v pořadí, jako prostředky, abyste mohli vytvořit instanci jen předání `Purchase` (testovaného systému).</span><span class="sxs-lookup"><span data-stu-id="22a1e-160">You're just passing in the Order as a means to be able to instantiate `Purchase` (the system under test).</span></span> <span data-ttu-id="22a1e-161">Název `MockOrder` je také velmi matoucí, protože znovu, pořadí, není model.</span><span class="sxs-lookup"><span data-stu-id="22a1e-161">The name `MockOrder` is also very misleading because again, the order is not a mock.</span></span>

<span data-ttu-id="22a1e-162">Lepším řešením by</span><span class="sxs-lookup"><span data-stu-id="22a1e-162">A better approach would be</span></span>

```csharp
var stubOrder = new FakeOrder();
var purchase = new Purchase(stubOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="22a1e-163">Při přejmenování třídy, která se `FakeOrder`provedené třídy mnohem více obecný, třída může sloužit jako model nebo zástupné procedury.</span><span class="sxs-lookup"><span data-stu-id="22a1e-163">By renaming the class to `FakeOrder`, you've made the class a lot more generic, the class can be used as a mock or a stub.</span></span> <span data-ttu-id="22a1e-164">Podle toho, co je lepší pro testovací případ.</span><span class="sxs-lookup"><span data-stu-id="22a1e-164">Whichever is better for the test case.</span></span> <span data-ttu-id="22a1e-165">Ve výše uvedeném příkladu `FakeOrder` slouží jako zástupné procedury.</span><span class="sxs-lookup"><span data-stu-id="22a1e-165">In the above example, `FakeOrder` is used as a stub.</span></span> <span data-ttu-id="22a1e-166">Nepoužíváte `FakeOrder` v libovolné formě během vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="22a1e-166">You're not using the `FakeOrder` in any shape or form during the assert.</span></span> <span data-ttu-id="22a1e-167">`FakeOrder` právě se předal `Purchase` vyhovět jejich požadavkům konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="22a1e-167">`FakeOrder` was just passed into the `Purchase` class to satisfy the requirements of the constructor.</span></span>

<span data-ttu-id="22a1e-168">Pokud chcete použít ho jako model, to můžeme asi takhle nějak.</span><span class="sxs-lookup"><span data-stu-id="22a1e-168">To use it as a Mock, you could do something like this</span></span>

```csharp
var mockOrder = new FakeOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(mockOrder.Validated);
```

<span data-ttu-id="22a1e-169">V takovém případě se kontroluje vlastnosti phishing (uplatnění u ní), takže ve výše uvedeném fragmentu kódu `mockOrder` je model.</span><span class="sxs-lookup"><span data-stu-id="22a1e-169">In this case, you are checking a property on the Fake (asserting against it), so in the above code snippet, the `mockOrder` is a Mock.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="22a1e-170">Je důležité získat Tato terminologie správné.</span><span class="sxs-lookup"><span data-stu-id="22a1e-170">It's important to get this terminology correct.</span></span> <span data-ttu-id="22a1e-171">Při volání vaše zástupné procedury "mocks", jinými vývojáři se chystáte vytvořit false předpoklady o vašich představ.</span><span class="sxs-lookup"><span data-stu-id="22a1e-171">If you call your stubs "mocks", other developers are going to make false assumptions about your intent.</span></span>

<span data-ttu-id="22a1e-172">Hlavní mít na paměti mocks oproti zástupné procedury je, že mocks jsou stejné jako zástupné procedury, ale vyhodnocení proti mock objektu, že není kontrolní výraz proti zástupnou proceduru.</span><span class="sxs-lookup"><span data-stu-id="22a1e-172">The main thing to remember about mocks versus stubs is that mocks are just like stubs, but you assert against the mock object, whereas you do not assert against a stub.</span></span>

## <a name="best-practices"></a><span data-ttu-id="22a1e-173">Osvědčené postupy</span><span class="sxs-lookup"><span data-stu-id="22a1e-173">Best practices</span></span>

### <a name="naming-your-tests"></a><span data-ttu-id="22a1e-174">Názvy testů</span><span class="sxs-lookup"><span data-stu-id="22a1e-174">Naming your tests</span></span>
<span data-ttu-id="22a1e-175">Název testu by měla obsahovat tři části:</span><span class="sxs-lookup"><span data-stu-id="22a1e-175">The name of your test should consist of three parts:</span></span>
- <span data-ttu-id="22a1e-176">Název metody testování.</span><span class="sxs-lookup"><span data-stu-id="22a1e-176">The name of the method being tested.</span></span>
- <span data-ttu-id="22a1e-177">Scénář, ve které je právě testováno.</span><span class="sxs-lookup"><span data-stu-id="22a1e-177">The scenario under which it's being tested.</span></span>
- <span data-ttu-id="22a1e-178">Očekávané chování při vyvolání scénář.</span><span class="sxs-lookup"><span data-stu-id="22a1e-178">The expected behavior when the scenario is invoked.</span></span>

#### <a name="why"></a><span data-ttu-id="22a1e-179">Proč?</span><span class="sxs-lookup"><span data-stu-id="22a1e-179">Why?</span></span>
- <span data-ttu-id="22a1e-180">Standardy pro vytváření názvů jsou důležité, protože explicitně vyjadřují záměr testu.</span><span class="sxs-lookup"><span data-stu-id="22a1e-180">Naming standards are important because they explicitly express the intent of the test.</span></span>

<span data-ttu-id="22a1e-181">Testy se více než jen zajistit váš kód funguje, také poskytují dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="22a1e-181">Tests are more than just making sure your code works, they also provide documentation.</span></span> <span data-ttu-id="22a1e-182">Jenom podle sady testů jednotek, je třeba možnost odvodit chování kódu bez i postupného prohlížení samotný kód.</span><span class="sxs-lookup"><span data-stu-id="22a1e-182">Just by looking at the suite of unit tests, you should be able to infer the behavior of your code without even looking at the code itself.</span></span> <span data-ttu-id="22a1e-183">Navíc když dojde k selhání testů, zobrazí se přesně scénáře, které nebudou vyhovovat vašim požadavkům.</span><span class="sxs-lookup"><span data-stu-id="22a1e-183">Additionally, when tests fail, you can see exactly which scenarios do not meet your expectations.</span></span>

#### <a name="bad"></a><span data-ttu-id="22a1e-184">Špatné:</span><span class="sxs-lookup"><span data-stu-id="22a1e-184">Bad:</span></span>
[!code-csharp[BeforeNaming](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeNaming)]

#### <a name="better"></a><span data-ttu-id="22a1e-185">Lepší:</span><span class="sxs-lookup"><span data-stu-id="22a1e-185">Better:</span></span>
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="arranging-your-tests"></a><span data-ttu-id="22a1e-186">Uspořádání testů</span><span class="sxs-lookup"><span data-stu-id="22a1e-186">Arranging your tests</span></span>
<span data-ttu-id="22a1e-187">**Uspořádat, fungovat, vyhodnocení** je běžný vzor při testování částí.</span><span class="sxs-lookup"><span data-stu-id="22a1e-187">**Arrange, Act, Assert** is a common pattern when unit testing.</span></span> <span data-ttu-id="22a1e-188">Jak již název napovídá, se skládá ze tří hlavních akcí:</span><span class="sxs-lookup"><span data-stu-id="22a1e-188">As the name implies, it consists of three main actions:</span></span>
- <span data-ttu-id="22a1e-189">*Uspořádat* objektů, vytváření a jejich nastavení podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="22a1e-189">*Arrange* your objects, creating and setting them up as necessary.</span></span>
- <span data-ttu-id="22a1e-190">*ACT* na objekt.</span><span class="sxs-lookup"><span data-stu-id="22a1e-190">*Act* on an object.</span></span>
- <span data-ttu-id="22a1e-191">*Assert –* , který je podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="22a1e-191">*Assert* that something is as expected.</span></span>

#### <a name="why"></a><span data-ttu-id="22a1e-192">Proč?</span><span class="sxs-lookup"><span data-stu-id="22a1e-192">Why?</span></span>
- <span data-ttu-id="22a1e-193">Jasně odděluje, co je právě testováno z *uspořádat* a *vyhodnocení* kroky.</span><span class="sxs-lookup"><span data-stu-id="22a1e-193">Clearly separates what is being tested from the *arrange* and *assert* steps.</span></span>
- <span data-ttu-id="22a1e-194">Menší pravděpodobnost kombinovat výrazy s kódem "Akce".</span><span class="sxs-lookup"><span data-stu-id="22a1e-194">Less chance to intermix assertions with "Act" code.</span></span>

<span data-ttu-id="22a1e-195">Čitelnost je jedním z nejdůležitějších aspektů při psaní testu.</span><span class="sxs-lookup"><span data-stu-id="22a1e-195">Readability is one of the most important aspects when writing a test.</span></span> <span data-ttu-id="22a1e-196">Každá z těchto akcí v rámci testu oddělení jasně zvýrazněte závislosti, které vyžaduje pro volání kódu, jak se váš kód volá a co se snažíte uplatnit.</span><span class="sxs-lookup"><span data-stu-id="22a1e-196">Separating each of these actions within the test clearly highlight the dependencies required to call your code, how your code is being called, and what you are trying to assert.</span></span> <span data-ttu-id="22a1e-197">Může být možné kombinovat několik kroků a zmenšete velikost vašeho testu, primární cílem je čitelnost test co nejrychleji.</span><span class="sxs-lookup"><span data-stu-id="22a1e-197">While it may be possible to combine some steps and reduce the size of your test, the primary goal is to make the test as readable as possible.</span></span>

#### <a name="bad"></a><span data-ttu-id="22a1e-198">Špatné:</span><span class="sxs-lookup"><span data-stu-id="22a1e-198">Bad:</span></span>
[!code-csharp[BeforeArranging](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeArranging)]

#### <a name="better"></a><span data-ttu-id="22a1e-199">Lepší:</span><span class="sxs-lookup"><span data-stu-id="22a1e-199">Better:</span></span>
[!code-csharp[AfterArranging](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterArranging)]

### <a name="write-minimally-passing-tests"></a><span data-ttu-id="22a1e-200">Zápis minimálně předávání testů</span><span class="sxs-lookup"><span data-stu-id="22a1e-200">Write minimally passing tests</span></span>
<span data-ttu-id="22a1e-201">Vstup pro použití v testu jednotek by měl být nejjednodušší možný ověří chování, které právě testujete.</span><span class="sxs-lookup"><span data-stu-id="22a1e-201">The input to be used in a unit test should be the simplest possible in order to verify the behavior that you are currently testing.</span></span>

#### <a name="why"></a><span data-ttu-id="22a1e-202">Proč?</span><span class="sxs-lookup"><span data-stu-id="22a1e-202">Why?</span></span>
- <span data-ttu-id="22a1e-203">Testy se stanou odolnější vůči budoucím změnám v základu kódu.</span><span class="sxs-lookup"><span data-stu-id="22a1e-203">Tests become more resilient to future changes in the codebase.</span></span>
- <span data-ttu-id="22a1e-204">Blíže k testování chování nad implementací.</span><span class="sxs-lookup"><span data-stu-id="22a1e-204">Closer to testing behavior over implementation.</span></span>

<span data-ttu-id="22a1e-205">Testy, které obsahují další informace, než se požaduje projde testem mají vyšší riziko zavlečení chyby do testu a mohl provádět záměr testovacího méně jasné.</span><span class="sxs-lookup"><span data-stu-id="22a1e-205">Tests that include more information than required to pass the test have a higher chance of introducing errors into the test and can make the intent of the test less clear.</span></span> <span data-ttu-id="22a1e-206">Při psaní testů chcete zaměřit na chování.</span><span class="sxs-lookup"><span data-stu-id="22a1e-206">When writing tests you want to focus on the behavior.</span></span> <span data-ttu-id="22a1e-207">Nastavení dalších vlastností u modelů nebo pomocí nenulové hodnoty, pokud není vyžadována, pouze nesnižuje co se pokoušíte prokázat, že.</span><span class="sxs-lookup"><span data-stu-id="22a1e-207">Setting extra properties on models or using non-zero values when not required, only detracts from what you are trying to prove.</span></span>

#### <a name="bad"></a><span data-ttu-id="22a1e-208">Špatné:</span><span class="sxs-lookup"><span data-stu-id="22a1e-208">Bad:</span></span>
[!code-csharp[BeforeMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMinimallyPassing)]

#### <a name="better"></a><span data-ttu-id="22a1e-209">Lepší:</span><span class="sxs-lookup"><span data-stu-id="22a1e-209">Better:</span></span>
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="avoid-magic-strings"></a><span data-ttu-id="22a1e-210">Vyhněte se magic řetězce</span><span class="sxs-lookup"><span data-stu-id="22a1e-210">Avoid magic strings</span></span>
<span data-ttu-id="22a1e-211">Názvy proměnných v jednotce testů je jako důležité, pokud není mnohem důležitější než názvů proměnných v produkčním kódu.</span><span class="sxs-lookup"><span data-stu-id="22a1e-211">Naming variables in unit tests is as important, if not more important, than naming variables in production code.</span></span> <span data-ttu-id="22a1e-212">Testy jednotek by neměla obsahovat magic řetězce.</span><span class="sxs-lookup"><span data-stu-id="22a1e-212">Unit tests should not contain magic strings.</span></span>

#### <a name="why"></a><span data-ttu-id="22a1e-213">Proč?</span><span class="sxs-lookup"><span data-stu-id="22a1e-213">Why?</span></span>
- <span data-ttu-id="22a1e-214">Zabraňuje potřebu čtecí modul testu ke kontrole produkčního kódu. Pokud chcete zjistit, co dělá hodnota speciální.</span><span class="sxs-lookup"><span data-stu-id="22a1e-214">Prevents the need for the reader of the test to inspect the production code in order to figure out what makes the value special.</span></span>
- <span data-ttu-id="22a1e-215">Explicitně ukazuje, co se pokoušíte *prokázat* namísto pokusu o *dosáhnout*.</span><span class="sxs-lookup"><span data-stu-id="22a1e-215">Explicitly shows what you're trying to *prove* rather than trying to *accomplish*.</span></span>

<span data-ttu-id="22a1e-216">Magický řetězce může způsobit zmatení čtečku testy.</span><span class="sxs-lookup"><span data-stu-id="22a1e-216">Magic strings can cause confusion to the reader of your tests.</span></span> <span data-ttu-id="22a1e-217">Pokud řetězec vypadá neobvyklého, mohou divit, proč byla vybrána určitou hodnotu pro parametr nebo návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="22a1e-217">If a string looks out of the ordinary, they may wonder why a certain value was chosen for a parameter or return value.</span></span> <span data-ttu-id="22a1e-218">Může to vést je se na ně podívat podrobnosti implementace, místo zaměření na test.</span><span class="sxs-lookup"><span data-stu-id="22a1e-218">This may lead them to take a closer look at the implementation details, rather than focus on the test.</span></span>

> [!TIP] 
> <span data-ttu-id="22a1e-219">Při psaní testů, bychom se měli snažit co nejvíce záměr nejvíce express.</span><span class="sxs-lookup"><span data-stu-id="22a1e-219">When writing tests, you should aim to express as much intent as possible.</span></span> <span data-ttu-id="22a1e-220">V případě magic řetězce je dobrý přístup přiřadit tyto hodnoty konstant.</span><span class="sxs-lookup"><span data-stu-id="22a1e-220">In the case of magic strings, a good approach is to assign these values to constants.</span></span>

#### <a name="bad"></a><span data-ttu-id="22a1e-221">Špatné:</span><span class="sxs-lookup"><span data-stu-id="22a1e-221">Bad:</span></span>
[!code-csharp[BeforeMagicString](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMagicString)]

#### <a name="better"></a><span data-ttu-id="22a1e-222">Lepší:</span><span class="sxs-lookup"><span data-stu-id="22a1e-222">Better:</span></span>
[!code-csharp[AfterMagicString](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterMagicString)]

### <a name="avoid-logic-in-tests"></a><span data-ttu-id="22a1e-223">Vyhněte se logika v testech</span><span class="sxs-lookup"><span data-stu-id="22a1e-223">Avoid logic in tests</span></span>
<span data-ttu-id="22a1e-224">Při zápisu jednotky testů Vyhněte se řetězení řetězců ruční a logické podmínky, jako například `if`, `while`, `for`, `switch`atd.</span><span class="sxs-lookup"><span data-stu-id="22a1e-224">When writing your unit tests avoid manual string concatenation and logical conditions such as `if`, `while`, `for`, `switch`, etc.</span></span>

#### <a name="why"></a><span data-ttu-id="22a1e-225">Proč?</span><span class="sxs-lookup"><span data-stu-id="22a1e-225">Why?</span></span>
- <span data-ttu-id="22a1e-226">Menší pravděpodobnost zavést chybu v rámci testů.</span><span class="sxs-lookup"><span data-stu-id="22a1e-226">Less chance to introduce a bug inside of your tests.</span></span>
- <span data-ttu-id="22a1e-227">Zaměřte se na konečný výsledek, spíše než podrobnosti implementace.</span><span class="sxs-lookup"><span data-stu-id="22a1e-227">Focus on the end result, rather than implementation details.</span></span>

<span data-ttu-id="22a1e-228">Když zavádíte logiky do testovací sady, výrazně zvyšuje riziko zavlečení chybu do něj.</span><span class="sxs-lookup"><span data-stu-id="22a1e-228">When you introduce logic into your test suite, the chance of introducing a bug into it increases dramatically.</span></span> <span data-ttu-id="22a1e-229">Poslední místo, které chcete najít chybu se do testovací sady.</span><span class="sxs-lookup"><span data-stu-id="22a1e-229">The last place that you want to find a bug is within your test suite.</span></span> <span data-ttu-id="22a1e-230">Byste měli mít vysoký stupeň spolehnout, že testy pracovat, jinak jim nebude důvěřovat.</span><span class="sxs-lookup"><span data-stu-id="22a1e-230">You should have a high level of confidence that your tests work, otherwise, you will not trust them.</span></span> <span data-ttu-id="22a1e-231">Testy, které nepovažujete za důvěryhodný, se neposkytuje žádnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="22a1e-231">Tests that you do not trust, do not provide any value.</span></span> <span data-ttu-id="22a1e-232">Pokud test selže, budete chtít mít pocit, že je ve skutečnosti chyba s kódem a že nelze ignorovat.</span><span class="sxs-lookup"><span data-stu-id="22a1e-232">When a test fails, you want to have a sense that something is actually wrong with your code and that it cannot be ignored.</span></span>

> [!TIP]
> <span data-ttu-id="22a1e-233">Logika v testu zdá se, že nevyhnutelné, vezměte v úvahu test rozdělení do dvou nebo více různých testy.</span><span class="sxs-lookup"><span data-stu-id="22a1e-233">If logic in your test seems unavoidable, consider splitting the test up into two or more different tests.</span></span>

#### <a name="bad"></a><span data-ttu-id="22a1e-234">Špatné:</span><span class="sxs-lookup"><span data-stu-id="22a1e-234">Bad:</span></span>
[!code-csharp[LogicInTests](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#LogicInTests)]

#### <a name="better"></a><span data-ttu-id="22a1e-235">Lepší:</span><span class="sxs-lookup"><span data-stu-id="22a1e-235">Better:</span></span>
[!code-csharp[AfterTestLogic](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterTestLogic)]

### <a name="prefer-helper-methods-to-setup-and-teardown"></a><span data-ttu-id="22a1e-236">Preferovat pomocné metody pro nastavení a jejich vyřazování z provozu</span><span class="sxs-lookup"><span data-stu-id="22a1e-236">Prefer helper methods to setup and teardown</span></span>
<span data-ttu-id="22a1e-237">Pokud požadujete podobných objektu nebo stav testů, raději metodu helper než využitím atributy instalační program a jejich vyřazování z provozu, pokud existují.</span><span class="sxs-lookup"><span data-stu-id="22a1e-237">If you require a similar object or state for your tests, prefer a helper method than leveraging Setup and Teardown attributes if they exist.</span></span>

#### <a name="why"></a><span data-ttu-id="22a1e-238">Proč?</span><span class="sxs-lookup"><span data-stu-id="22a1e-238">Why?</span></span>
- <span data-ttu-id="22a1e-239">Méně nedorozumění při čtení testů od veškerý kód je viditelná z v rámci každého testu.</span><span class="sxs-lookup"><span data-stu-id="22a1e-239">Less confusion when reading the tests since all of the code is visible from within each test.</span></span>
- <span data-ttu-id="22a1e-240">Menší pravděpodobnost, že nastavení příliš mnoho nebo příliš málo pro daný test.</span><span class="sxs-lookup"><span data-stu-id="22a1e-240">Less chance of setting up too much or too little for the given test.</span></span>
- <span data-ttu-id="22a1e-241">Menší riziko sdílení stavu mezi testů, které vytvoří nechtěné závislosti mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="22a1e-241">Less chance of sharing state between tests which creates unwanted dependencies between them.</span></span>

<span data-ttu-id="22a1e-242">V jednotce testování rozhraní, `Setup` je volána před testováním jednotky každého v rámci vaší sady testů.</span><span class="sxs-lookup"><span data-stu-id="22a1e-242">In unit testing frameworks, `Setup` is called before each and every unit test within your test suite.</span></span> <span data-ttu-id="22a1e-243">Zatímco některé to vidí jako užitečný nástroj, obvykle ukončí si vede na opakovaném a těžko čitelný testy.</span><span class="sxs-lookup"><span data-stu-id="22a1e-243">While some may see this as a useful tool, it generally ends up leading to bloated and hard to read tests.</span></span> <span data-ttu-id="22a1e-244">Každý test obvykle má jiné požadavky zajistí test rychle zprovoznit.</span><span class="sxs-lookup"><span data-stu-id="22a1e-244">Each test will generally have different requirements in order to get the test up and running.</span></span> <span data-ttu-id="22a1e-245">Bohužel `Setup` vynutí použití přesně stejné požadavky pro každý test.</span><span class="sxs-lookup"><span data-stu-id="22a1e-245">Unfortunately, `Setup` forces you to use the exact same requirements for each test.</span></span>

> [!NOTE] 
> <span data-ttu-id="22a1e-246">xUnit odebral instalační program a jejich vyřazování z provozu od verze 2.x</span><span class="sxs-lookup"><span data-stu-id="22a1e-246">xUnit has removed both SetUp and TearDown as of version 2.x</span></span>

#### <a name="bad"></a><span data-ttu-id="22a1e-247">Špatné:</span><span class="sxs-lookup"><span data-stu-id="22a1e-247">Bad:</span></span>
[!code-csharp[BeforeSetup](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeSetup)]

```csharp
// more tests...
```

[!code-csharp[BeforeHelperMethod](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeHelperMethod)]

#### <a name="better"></a><span data-ttu-id="22a1e-248">Lepší:</span><span class="sxs-lookup"><span data-stu-id="22a1e-248">Better:</span></span>
[!code-csharp[AfterHelperMethod](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterHelperMethod)]

```csharp
// more tests...
```

[!code-csharp[AfterSetup](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterSetup)]

### <a name="avoid-multiple-asserts"></a><span data-ttu-id="22a1e-249">Vyhněte se více nepodmíněné výrazy</span><span class="sxs-lookup"><span data-stu-id="22a1e-249">Avoid multiple asserts</span></span>
<span data-ttu-id="22a1e-250">Při psaní testů, zkuste obsahovat jenom jeden kontrolní výraz na test.</span><span class="sxs-lookup"><span data-stu-id="22a1e-250">When writing your tests, try to only include one Assert per test.</span></span> <span data-ttu-id="22a1e-251">Běžné způsoby používání pouze jeden výraz patří:</span><span class="sxs-lookup"><span data-stu-id="22a1e-251">Common approaches to using only one assert include:</span></span>
- <span data-ttu-id="22a1e-252">Vytvoření samostatné testu pro každý kontrolní výraz.</span><span class="sxs-lookup"><span data-stu-id="22a1e-252">Create a separate test for each assert.</span></span>
- <span data-ttu-id="22a1e-253">Parametrizované testy použijte.</span><span class="sxs-lookup"><span data-stu-id="22a1e-253">Use parameterized tests.</span></span>

#### <a name="why"></a><span data-ttu-id="22a1e-254">Proč?</span><span class="sxs-lookup"><span data-stu-id="22a1e-254">Why?</span></span>
- <span data-ttu-id="22a1e-255">Pokud selže jeden kontrolní výraz nebude vyhodnocen následné nepodmíněné výrazy.</span><span class="sxs-lookup"><span data-stu-id="22a1e-255">If one Assert fails, the subsequent Asserts will not be evaluated.</span></span>
- <span data-ttu-id="22a1e-256">Zajišťuje, že v testech nejsou uplatnění více případů.</span><span class="sxs-lookup"><span data-stu-id="22a1e-256">Ensures you are not asserting multiple cases in your tests.</span></span>
- <span data-ttu-id="22a1e-257">Poskytuje celého obrázku, proč jsou neúspěšné testy.</span><span class="sxs-lookup"><span data-stu-id="22a1e-257">Gives you the entire picture as to why your tests are failing.</span></span> 

<span data-ttu-id="22a1e-258">Při zavedení více nepodmíněné výrazy do testovacího případu, to není zaručeno, že všechny aplikace nepodmíněné výrazy se provést.</span><span class="sxs-lookup"><span data-stu-id="22a1e-258">When introducing multiple asserts into a test case, it is not guaranteed that all of the asserts will be executed.</span></span> <span data-ttu-id="22a1e-259">Ve většině rozhraní testování částí jakmile kontrolní výraz selže v testování částí, řízení testy jsou automaticky považovány za docházet k selháním.</span><span class="sxs-lookup"><span data-stu-id="22a1e-259">In most unit testing frameworks, once an assertion fails in a unit test, the proceeding tests are automatically considered to be failing.</span></span> <span data-ttu-id="22a1e-260">To může být matoucí, tak, jak funkce, které skutečně funguje, bude zobrazovat jako selhání.</span><span class="sxs-lookup"><span data-stu-id="22a1e-260">This can be confusing as functionality that is actually working, will be shown as failing.</span></span>

> [!NOTE]
> <span data-ttu-id="22a1e-261">Běžné výjimky tohoto pravidla je po uplatnění proti objektu.</span><span class="sxs-lookup"><span data-stu-id="22a1e-261">A common exception to this rule is when asserting against an object.</span></span> <span data-ttu-id="22a1e-262">V takovém případě je obecně přijatelné mít více nepodmíněné výrazy pro každou vlastnost zajistit objekt je ve stavu, který očekáváte, že bude v.</span><span class="sxs-lookup"><span data-stu-id="22a1e-262">In this case, it is generally acceptable to have multiple asserts against each property to ensure the object is in the state that you expect it to be in.</span></span>

#### <a name="bad"></a><span data-ttu-id="22a1e-263">Špatné:</span><span class="sxs-lookup"><span data-stu-id="22a1e-263">Bad:</span></span>
[!code-csharp[BeforeMultipleAsserts](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMultipleAsserts)]

#### <a name="better"></a><span data-ttu-id="22a1e-264">Lepší:</span><span class="sxs-lookup"><span data-stu-id="22a1e-264">Better:</span></span>
[!code-csharp[AfterMultipleAsserts](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterMultipleAsserts)]

### <a name="validate-private-methods-by-unit-testing-public-methods"></a><span data-ttu-id="22a1e-265">Ověření privátní metody testování veřejné metody jednotky</span><span class="sxs-lookup"><span data-stu-id="22a1e-265">Validate private methods by unit testing public methods</span></span>
<span data-ttu-id="22a1e-266">Ve většině případů by neměl být potřeba testovat privátní metodu.</span><span class="sxs-lookup"><span data-stu-id="22a1e-266">In most cases, there should not be a need to test a private method.</span></span> <span data-ttu-id="22a1e-267">Privátní metody jsou podrobnosti implementace.</span><span class="sxs-lookup"><span data-stu-id="22a1e-267">Private methods are an implementation detail.</span></span> <span data-ttu-id="22a1e-268">Můžete si ho představit tímto způsobem: privátní metody nikdy existovat v izolaci.</span><span class="sxs-lookup"><span data-stu-id="22a1e-268">You can think of it this way: private methods never exist in isolation.</span></span> <span data-ttu-id="22a1e-269">V určitém okamžiku se chystají se protilehlé veřejnou metodu, která volá metodu privátní jako součást jeho implementace.</span><span class="sxs-lookup"><span data-stu-id="22a1e-269">At some point, there is going to be a public facing method that calls the private method as part of its implementation.</span></span> <span data-ttu-id="22a1e-270">By měl postaral o je konečný výsledek veřejnou metodu, která volá do privátní objektu.</span><span class="sxs-lookup"><span data-stu-id="22a1e-270">What you should care about is the end result of the public method that calls into the private one.</span></span> 

<span data-ttu-id="22a1e-271">Zvažte následující případ</span><span class="sxs-lookup"><span data-stu-id="22a1e-271">Consider the following case</span></span>

```csharp
public string ParseLogLine(string input)
{
    var sanitizedInput = trimInput(input);
    return sanitizedInput;
}

private string trimInput(string input)
{
    return input.Trim();
}
```

<span data-ttu-id="22a1e-272">Aby vám začali psát test může být první reakci `trimInput` proto, abyste měli jistotu, že metoda funguje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="22a1e-272">Your first reaction may be to start writing a test for `trimInput` because you want to make sure that the method is working as expected.</span></span> <span data-ttu-id="22a1e-273">Je však šíři, který `ParseLogLine` manipuluje `sanitizedInput` takovým způsobem, který nepočítáte, testují splnění vykreslování `trimInput` zbytečné.</span><span class="sxs-lookup"><span data-stu-id="22a1e-273">However, it is entirely possible that `ParseLogLine` manipulates `sanitizedInput` in such a way that you do not expect, rendering a test against `trimInput` useless.</span></span> 

<span data-ttu-id="22a1e-274">Skutečný test by mělo být provedeno proti veřejnou metodu protilehlé `ParseLogLine` protože to je, co vám by nakonec záleží.</span><span class="sxs-lookup"><span data-stu-id="22a1e-274">The real test should be done against the public facing method `ParseLogLine` because that is what you should ultimately care about.</span></span> 

```csharp
public void ParseLogLine_ByDefault_ReturnsTrimmedResult()
{
    var parser = new Parser();

    var result = parser.ParseLogLine(" a ");

    Assert.Equals("a", result);
}
```

<span data-ttu-id="22a1e-275">Pomocí této základní vlastností viru Pokud se zobrazí privátní metodu, Najít veřejnou metodu a zápis testování proti dané metody.</span><span class="sxs-lookup"><span data-stu-id="22a1e-275">With this viewpoint, if you see a private method, find the public method and write your tests against that method.</span></span> <span data-ttu-id="22a1e-276">Pouze z důvodu privátní metoda vrátí očekávaný výsledek, neznamená, že systém, který nakonec volá metodu privátní používá výsledek správně.</span><span class="sxs-lookup"><span data-stu-id="22a1e-276">Just because a private method returns the expected result, does not mean the system that eventually calls the private method uses the result correctly.</span></span>

### <a name="stub-static-references"></a><span data-ttu-id="22a1e-277">Zástupná procedura statických odkazů.</span><span class="sxs-lookup"><span data-stu-id="22a1e-277">Stub static references</span></span>
<span data-ttu-id="22a1e-278">Jedním z principů testování částí je, že musí mít úplnou kontrolu nad testovaného systému.</span><span class="sxs-lookup"><span data-stu-id="22a1e-278">One of the principles of a unit test is that it must have full control of the system under test.</span></span> <span data-ttu-id="22a1e-279">To může být problematické, pokud je produkční kód obsahuje volání statických odkazů (třeba `DateTime.Now`).</span><span class="sxs-lookup"><span data-stu-id="22a1e-279">This can be problematic when production code includes calls to static references (e.g. `DateTime.Now`).</span></span> <span data-ttu-id="22a1e-280">Uvažujme následující kód</span><span class="sxs-lookup"><span data-stu-id="22a1e-280">Consider the following code</span></span>

```csharp
public int GetDiscountedPrice(int price)
{
    if(DateTime.Now == DayOfWeek.Tuesday) 
    {
        return price / 2;
    }
    else 
    {
        return price;
    }
}
```

<span data-ttu-id="22a1e-281">Jak tento kód může být lze testování částí?</span><span class="sxs-lookup"><span data-stu-id="22a1e-281">How can this code possibly be unit tested?</span></span> <span data-ttu-id="22a1e-282">Zkuste přístup, jako</span><span class="sxs-lookup"><span data-stu-id="22a1e-282">You may try an approach such as</span></span>

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

<span data-ttu-id="22a1e-283">Bohužel se rychle dobré si uvědomit, že existuje několik problémů s testy.</span><span class="sxs-lookup"><span data-stu-id="22a1e-283">Unfortunately, you will quickly realize that there are a couple problems with your tests.</span></span> 

- <span data-ttu-id="22a1e-284">Pokud sadu testů je spuštěn úterý, druhý test bude úspěšný, ale první test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="22a1e-284">If the test suite is run on a Tuesday, the second test will pass, but the first test will fail.</span></span>
- <span data-ttu-id="22a1e-285">Pokud sadu testů je spuštěn na libovolný den, bude první test úspěšný, ale druhý test se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="22a1e-285">If the test suite is run on any other day, the first test will pass, but the second test will fail.</span></span>

<span data-ttu-id="22a1e-286">K řešení těchto problémů, je potřeba zavést *švu* do produkčního kódu.</span><span class="sxs-lookup"><span data-stu-id="22a1e-286">To solve these problems, you'll need to introduce a *seam* into your production code.</span></span> <span data-ttu-id="22a1e-287">Jedním z přístupů je zabalit kód, který je potřeba řídit v rozhraní a produkční kód závisí na tomto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="22a1e-287">One approach is to wrap the code that you need to control in an interface and have the production code depend on that interface.</span></span>

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

<span data-ttu-id="22a1e-288">Teď bude vaše testovací sada</span><span class="sxs-lookup"><span data-stu-id="22a1e-288">Your test suite now becomes</span></span>

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

<span data-ttu-id="22a1e-289">Nyní sada testů má plnou kontrolu nad `DateTime.Now` a můžete se zakázaným inzerováním libovolnou hodnotu při volání do metody.</span><span class="sxs-lookup"><span data-stu-id="22a1e-289">Now the test suite has full control over `DateTime.Now` and can stub any value when calling into the method.</span></span>
