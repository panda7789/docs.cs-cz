---
title: Pořadí testů jednotek
description: Přečtěte si, jak objednat testy jednotek pomocí .NET Core.
author: IEvangelist
ms.date: 05/18/2020
zone_pivot_groups: unit-testing-framework-set-one
ms.openlocfilehash: ce0d01c924075ffcc9ad49ef8aca49222c10c921
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83704557"
---
# <a name="order-unit-tests"></a><span data-ttu-id="95986-103">Pořadí testů jednotek</span><span class="sxs-lookup"><span data-stu-id="95986-103">Order unit tests</span></span>

<span data-ttu-id="95986-104">V některých případech možná budete chtít, aby testy jednotek běžely v určitém pořadí.</span><span class="sxs-lookup"><span data-stu-id="95986-104">Occasionally, you may want to have unit tests run in a specific order.</span></span> <span data-ttu-id="95986-105">V ideálním případě pořadí, ve _kterém by testy_ jednotek běžely, nezáleží a je [osvědčeným postupem](unit-testing-best-practices.md) vyhnout se řazení jednotek.</span><span class="sxs-lookup"><span data-stu-id="95986-105">Ideally, the order in which unit tests run should _not_ matter, and it is [best practice](unit-testing-best-practices.md) to avoid ordering unit tests.</span></span> <span data-ttu-id="95986-106">Bez ohledu na to může být potřeba.</span><span class="sxs-lookup"><span data-stu-id="95986-106">Regardless, there may be a need to do so.</span></span> <span data-ttu-id="95986-107">V takovém případě tento článek ukazuje, jak objednat testovací běhy.</span><span class="sxs-lookup"><span data-stu-id="95986-107">In that case, this article demonstrates how to order test runs.</span></span>

<span data-ttu-id="95986-108">Pokud dáváte přednost procházení zdrojového kódu, přečtěte si téma úložiště ukázkového úložiště [test jednotek .NET Core](/samples/dotnet/samples/order-unit-tests-cs) .</span><span class="sxs-lookup"><span data-stu-id="95986-108">If you prefer to browse the source code, see the [order .NET Core unit tests](/samples/dotnet/samples/order-unit-tests-cs) sample repository.</span></span>

> [!TIP]
> <span data-ttu-id="95986-109">Kromě možností řazení uvedených v tomto článku zvažte možnost [vytvořit vlastní seznamy stop v aplikaci Visual Studio](/visualstudio/test/run-unit-tests-with-test-explorer?view=vs-2019#create-custom-playlists) jako alternativu.</span><span class="sxs-lookup"><span data-stu-id="95986-109">In addition to the ordering capabilities outlined in this article, consider [creating custom playlists with Visual Studio](/visualstudio/test/run-unit-tests-with-test-explorer?view=vs-2019#create-custom-playlists) as an alternative.</span></span>

:::zone pivot="mstest"

## <a name="order-alphabetically"></a><span data-ttu-id="95986-110">Seřadit abecedně</span><span class="sxs-lookup"><span data-stu-id="95986-110">Order alphabetically</span></span>

<span data-ttu-id="95986-111">Pomocí MSTest jsou testy automaticky seřazeny podle názvu testu.</span><span class="sxs-lookup"><span data-stu-id="95986-111">With MSTest, tests are automatically ordered by their test name.</span></span>

> [!NOTE]
> <span data-ttu-id="95986-112">Test s názvem `Test14` bude spuštěn před, `Test2` i když `2` je číslo menší než `14` .</span><span class="sxs-lookup"><span data-stu-id="95986-112">A test named `Test14` will run before `Test2` even though the number  `2` is less than `14`.</span></span> <span data-ttu-id="95986-113">Důvodem je, že řazení názvu testu používá textový název testu.</span><span class="sxs-lookup"><span data-stu-id="95986-113">This is because, test name ordering uses the text name of the test.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/MSTest.Project/ByAlphabeticalOrder.cs":::

:::zone-end
:::zone pivot="xunit"

<span data-ttu-id="95986-114">Testovací rozhraní xUnit umožňuje více členitosti a kontrolu nad pořadím testovacích běhů.</span><span class="sxs-lookup"><span data-stu-id="95986-114">The xUnit test framework allows for more granularity and control of test run order.</span></span> <span data-ttu-id="95986-115">`ITestCaseOrderer`Rozhraní a implementujete `ITestCollectionOrderer` pro řízení pořadí testovacích případů pro třídu nebo kolekce testů.</span><span class="sxs-lookup"><span data-stu-id="95986-115">You implement the `ITestCaseOrderer` and `ITestCollectionOrderer` interfaces to control the order of test cases for a class, or test collections.</span></span>

## <a name="order-by-test-case-alphabetically"></a><span data-ttu-id="95986-116">Objednat podle abecedy podle testovacího případu</span><span class="sxs-lookup"><span data-stu-id="95986-116">Order by test case alphabetically</span></span>

<span data-ttu-id="95986-117">Pro seřazení testovacích případů podle jejich názvu metody implementujete `ITestCaseOrderer` a zadáte mechanizmus pro řazení.</span><span class="sxs-lookup"><span data-stu-id="95986-117">To order test cases by their method name, you implement the `ITestCaseOrderer` and provide an ordering mechanism.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Orderers/AlphabeticalOrderer.cs":::

<span data-ttu-id="95986-118">Poté v testovací třídě, kterou nastavíte pořadí testovacího případu s `TestCaseOrdererAttribute` .</span><span class="sxs-lookup"><span data-stu-id="95986-118">Then in a test class you set the test case order with the `TestCaseOrdererAttribute`.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/ByAlphabeticalOrder.cs":::

## <a name="order-by-collection-alphabetically"></a><span data-ttu-id="95986-119">Seřadit podle kolekce abecedně</span><span class="sxs-lookup"><span data-stu-id="95986-119">Order by collection alphabetically</span></span>

<span data-ttu-id="95986-120">Pro seřazení kolekcí testů podle zobrazovaného názvu implementujete `ITestCollectionOrderer` a poskytněte mechanizmus.</span><span class="sxs-lookup"><span data-stu-id="95986-120">To order test collections by their display name, you implement the `ITestCollectionOrderer` and provide an ordering mechanism.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Orderers/DisplayNameOrderer.cs":::

<span data-ttu-id="95986-121">Vzhledem k tomu, že kolekce testů mohou být potenciálně spouštěny paralelně, je nutné explicitně zakázat test paralelismu kolekcí pomocí `CollectionBehaviorAttribute` .</span><span class="sxs-lookup"><span data-stu-id="95986-121">Since test collections potentially run in parallel, you must explicitly disable test parallelization of the collections with the `CollectionBehaviorAttribute`.</span></span> <span data-ttu-id="95986-122">Pak zadejte implementaci do `TestCollectionOrdererAttribute` .</span><span class="sxs-lookup"><span data-stu-id="95986-122">Then specify the implementation to the `TestCollectionOrdererAttribute`.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/ByDisplayName.cs":::

## <a name="order-by-custom-attribute"></a><span data-ttu-id="95986-123">Seřadit podle vlastního atributu</span><span class="sxs-lookup"><span data-stu-id="95986-123">Order by custom attribute</span></span>

<span data-ttu-id="95986-124">Chcete-li seřadit xUnit testy s vlastními atributy, budete nejprve potřebovat atribut, který by měl být závislý.</span><span class="sxs-lookup"><span data-stu-id="95986-124">To order xUnit tests with custom attributes, you first need an attribute to rely on.</span></span> <span data-ttu-id="95986-125">Definujte a `TestPriorityAttribute` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="95986-125">Define a `TestPriorityAttribute` as follows:</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Attributes/TestPriorityAttribute.cs":::

<span data-ttu-id="95986-126">Dále zvažte následující `PriorityOrderer` implementaci `ITestCaseOrderer` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="95986-126">Next, consider the following `PriorityOrderer` implementation of the `ITestCaseOrderer` interface.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Orderers/PriorityOrderer.cs":::

<span data-ttu-id="95986-127">Poté v testovací třídě, kterou nastavíte pořadí testovacího případu s na `TestCaseOrdererAttribute` `PriorityOrderer` .</span><span class="sxs-lookup"><span data-stu-id="95986-127">Then in a test class you set the test case order with the `TestCaseOrdererAttribute` to the `PriorityOrderer`.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/ByPriorityOrder.cs":::

:::zone-end
:::zone pivot="nunit"

## <a name="order-by-priority"></a><span data-ttu-id="95986-128">Pořadí podle priority</span><span class="sxs-lookup"><span data-stu-id="95986-128">Order by priority</span></span>

<span data-ttu-id="95986-129">Pro explicitní seřazení testů NUnit poskytuje [`OrderAttribute`](https://github.com/nunit/docs/wiki/Order-Attribute) .</span><span class="sxs-lookup"><span data-stu-id="95986-129">To order tests explicitly, NUnit provides an [`OrderAttribute`](https://github.com/nunit/docs/wiki/Order-Attribute).</span></span> <span data-ttu-id="95986-130">Testy s tímto atributem jsou spuštěny před testy bez.</span><span class="sxs-lookup"><span data-stu-id="95986-130">Tests with this attribute are started before tests without.</span></span> <span data-ttu-id="95986-131">Hodnota pořadí se používá ke zjištění pořadí spuštění testů jednotek.</span><span class="sxs-lookup"><span data-stu-id="95986-131">The order value is used to determined the order to run the unit tests.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/NUnit.TestProject/ByOrder.cs":::

:::zone-end

## <a name="next-steps"></a><span data-ttu-id="95986-132">Další kroky</span><span class="sxs-lookup"><span data-stu-id="95986-132">Next Steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="95986-133">Osvědčené postupy pro testování částí</span><span class="sxs-lookup"><span data-stu-id="95986-133">Unit testing best practices</span></span>](unit-testing-best-practices.md)
