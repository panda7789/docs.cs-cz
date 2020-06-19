---
title: Seřazení testů jednotek
description: Přečtěte si, jak objednat testy jednotek pomocí .NET Core.
author: IEvangelist
ms.date: 05/18/2020
zone_pivot_groups: unit-testing-framework-set-one
ms.openlocfilehash: 3400ae440a828054624d67c14807ee72783e466a
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989260"
---
# <a name="order-unit-tests"></a><span data-ttu-id="b6518-103">Seřazení testů jednotek</span><span class="sxs-lookup"><span data-stu-id="b6518-103">Order unit tests</span></span>

<span data-ttu-id="b6518-104">V některých případech možná budete chtít, aby testy jednotek běžely v určitém pořadí.</span><span class="sxs-lookup"><span data-stu-id="b6518-104">Occasionally, you may want to have unit tests run in a specific order.</span></span> <span data-ttu-id="b6518-105">V ideálním případě pořadí, ve _kterém by testy_ jednotek běžely, nezáleží a je [osvědčeným postupem](unit-testing-best-practices.md) vyhnout se řazení jednotek.</span><span class="sxs-lookup"><span data-stu-id="b6518-105">Ideally, the order in which unit tests run should _not_ matter, and it is [best practice](unit-testing-best-practices.md) to avoid ordering unit tests.</span></span> <span data-ttu-id="b6518-106">Bez ohledu na to může být potřeba.</span><span class="sxs-lookup"><span data-stu-id="b6518-106">Regardless, there may be a need to do so.</span></span> <span data-ttu-id="b6518-107">V takovém případě tento článek ukazuje, jak objednat testovací běhy.</span><span class="sxs-lookup"><span data-stu-id="b6518-107">In that case, this article demonstrates how to order test runs.</span></span>

<span data-ttu-id="b6518-108">Pokud dáváte přednost procházení zdrojového kódu, přečtěte si téma úložiště ukázkového úložiště [test jednotek .NET Core](/samples/dotnet/samples/order-unit-tests-cs) .</span><span class="sxs-lookup"><span data-stu-id="b6518-108">If you prefer to browse the source code, see the [order .NET Core unit tests](/samples/dotnet/samples/order-unit-tests-cs) sample repository.</span></span>

> [!TIP]
> <span data-ttu-id="b6518-109">Kromě možností řazení uvedených v tomto článku zvažte možnost [vytvořit vlastní seznamy stop v aplikaci Visual Studio](/visualstudio/test/run-unit-tests-with-test-explorer?view=vs-2019#create-custom-playlists) jako alternativu.</span><span class="sxs-lookup"><span data-stu-id="b6518-109">In addition to the ordering capabilities outlined in this article, consider [creating custom playlists with Visual Studio](/visualstudio/test/run-unit-tests-with-test-explorer?view=vs-2019#create-custom-playlists) as an alternative.</span></span>

:::zone pivot="mstest"

## <a name="order-alphabetically"></a><span data-ttu-id="b6518-110">Seřadit abecedně</span><span class="sxs-lookup"><span data-stu-id="b6518-110">Order alphabetically</span></span>

<span data-ttu-id="b6518-111">Pomocí MSTest jsou testy automaticky seřazeny podle názvu testu.</span><span class="sxs-lookup"><span data-stu-id="b6518-111">With MSTest, tests are automatically ordered by their test name.</span></span>

> [!NOTE]
> <span data-ttu-id="b6518-112">Test s názvem `Test14` bude spuštěn před, `Test2` i když `2` je číslo menší než `14` .</span><span class="sxs-lookup"><span data-stu-id="b6518-112">A test named `Test14` will run before `Test2` even though the number  `2` is less than `14`.</span></span> <span data-ttu-id="b6518-113">Důvodem je, že řazení názvu testu používá textový název testu.</span><span class="sxs-lookup"><span data-stu-id="b6518-113">This is because, test name ordering uses the text name of the test.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/MSTest.Project/ByAlphabeticalOrder.cs":::

:::zone-end
:::zone pivot="xunit"

<span data-ttu-id="b6518-114">Testovací rozhraní xUnit umožňuje více členitosti a kontrolu nad pořadím testovacích běhů.</span><span class="sxs-lookup"><span data-stu-id="b6518-114">The xUnit test framework allows for more granularity and control of test run order.</span></span> <span data-ttu-id="b6518-115">`ITestCaseOrderer`Rozhraní a implementujete `ITestCollectionOrderer` pro řízení pořadí testovacích případů pro třídu nebo kolekce testů.</span><span class="sxs-lookup"><span data-stu-id="b6518-115">You implement the `ITestCaseOrderer` and `ITestCollectionOrderer` interfaces to control the order of test cases for a class, or test collections.</span></span>

## <a name="order-by-test-case-alphabetically"></a><span data-ttu-id="b6518-116">Objednat podle abecedy podle testovacího případu</span><span class="sxs-lookup"><span data-stu-id="b6518-116">Order by test case alphabetically</span></span>

<span data-ttu-id="b6518-117">Pro seřazení testovacích případů podle jejich názvu metody implementujete `ITestCaseOrderer` a zadáte mechanizmus pro řazení.</span><span class="sxs-lookup"><span data-stu-id="b6518-117">To order test cases by their method name, you implement the `ITestCaseOrderer` and provide an ordering mechanism.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Orderers/AlphabeticalOrderer.cs":::

<span data-ttu-id="b6518-118">Poté v testovací třídě, kterou nastavíte pořadí testovacího případu s `TestCaseOrdererAttribute` .</span><span class="sxs-lookup"><span data-stu-id="b6518-118">Then in a test class you set the test case order with the `TestCaseOrdererAttribute`.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/ByAlphabeticalOrder.cs":::

## <a name="order-by-collection-alphabetically"></a><span data-ttu-id="b6518-119">Seřadit podle kolekce abecedně</span><span class="sxs-lookup"><span data-stu-id="b6518-119">Order by collection alphabetically</span></span>

<span data-ttu-id="b6518-120">Pro seřazení kolekcí testů podle zobrazovaného názvu implementujete `ITestCollectionOrderer` a poskytněte mechanizmus.</span><span class="sxs-lookup"><span data-stu-id="b6518-120">To order test collections by their display name, you implement the `ITestCollectionOrderer` and provide an ordering mechanism.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Orderers/DisplayNameOrderer.cs":::

<span data-ttu-id="b6518-121">Vzhledem k tomu, že kolekce testů mohou být potenciálně spouštěny paralelně, je nutné explicitně zakázat test paralelismu kolekcí pomocí `CollectionBehaviorAttribute` .</span><span class="sxs-lookup"><span data-stu-id="b6518-121">Since test collections potentially run in parallel, you must explicitly disable test parallelization of the collections with the `CollectionBehaviorAttribute`.</span></span> <span data-ttu-id="b6518-122">Pak zadejte implementaci do `TestCollectionOrdererAttribute` .</span><span class="sxs-lookup"><span data-stu-id="b6518-122">Then specify the implementation to the `TestCollectionOrdererAttribute`.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/ByDisplayName.cs":::

## <a name="order-by-custom-attribute"></a><span data-ttu-id="b6518-123">Seřadit podle vlastního atributu</span><span class="sxs-lookup"><span data-stu-id="b6518-123">Order by custom attribute</span></span>

<span data-ttu-id="b6518-124">Chcete-li seřadit xUnit testy s vlastními atributy, budete nejprve potřebovat atribut, který by měl být závislý.</span><span class="sxs-lookup"><span data-stu-id="b6518-124">To order xUnit tests with custom attributes, you first need an attribute to rely on.</span></span> <span data-ttu-id="b6518-125">Definujte a `TestPriorityAttribute` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="b6518-125">Define a `TestPriorityAttribute` as follows:</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Attributes/TestPriorityAttribute.cs":::

<span data-ttu-id="b6518-126">Dále zvažte následující `PriorityOrderer` implementaci `ITestCaseOrderer` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b6518-126">Next, consider the following `PriorityOrderer` implementation of the `ITestCaseOrderer` interface.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Orderers/PriorityOrderer.cs":::

<span data-ttu-id="b6518-127">Poté v testovací třídě, kterou nastavíte pořadí testovacího případu s na `TestCaseOrdererAttribute` `PriorityOrderer` .</span><span class="sxs-lookup"><span data-stu-id="b6518-127">Then in a test class you set the test case order with the `TestCaseOrdererAttribute` to the `PriorityOrderer`.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/ByPriorityOrder.cs":::

:::zone-end
:::zone pivot="nunit"

## <a name="order-by-priority"></a><span data-ttu-id="b6518-128">Pořadí podle priority</span><span class="sxs-lookup"><span data-stu-id="b6518-128">Order by priority</span></span>

<span data-ttu-id="b6518-129">Pro explicitní seřazení testů NUnit poskytuje [`OrderAttribute`](https://github.com/nunit/docs/wiki/Order-Attribute) .</span><span class="sxs-lookup"><span data-stu-id="b6518-129">To order tests explicitly, NUnit provides an [`OrderAttribute`](https://github.com/nunit/docs/wiki/Order-Attribute).</span></span> <span data-ttu-id="b6518-130">Testy s tímto atributem jsou spuštěny před testy bez.</span><span class="sxs-lookup"><span data-stu-id="b6518-130">Tests with this attribute are started before tests without.</span></span> <span data-ttu-id="b6518-131">Hodnota pořadí se používá ke zjištění pořadí spuštění testů jednotek.</span><span class="sxs-lookup"><span data-stu-id="b6518-131">The order value is used to determined the order to run the unit tests.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/NUnit.TestProject/ByOrder.cs":::

:::zone-end

## <a name="next-steps"></a><span data-ttu-id="b6518-132">Další kroky</span><span class="sxs-lookup"><span data-stu-id="b6518-132">Next Steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b6518-133">Pokrytí kódu testu jednotek</span><span class="sxs-lookup"><span data-stu-id="b6518-133">Unit test code coverage</span></span>](unit-testing-code-coverage.md)
