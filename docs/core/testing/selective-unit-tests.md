---
title: Testy spuštění selektivní jednotek
description: Ukazuje, jak se použije ke spuštění testů jednotek selektivní test příkazem dotnet výraz filtru.
author: smadala
ms.author: mairaw
ms.date: 03/22/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 77ac7ab5a46150bd3654d50e6686087c804b8440
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="3df0c-103">Testy spuštění selektivní jednotek</span><span class="sxs-lookup"><span data-stu-id="3df0c-103">Running selective unit tests</span></span>

<span data-ttu-id="3df0c-104">Následující příklady použití `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="3df0c-104">The following examples use `dotnet test`.</span></span> <span data-ttu-id="3df0c-105">Pokud používáte `vstest.console.exe`, nahraďte `--filter ` s `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="3df0c-105">If you're using `vstest.console.exe`, replace `--filter ` with `--testcasefilter:`.</span></span>

## <a name="mstest"></a><span data-ttu-id="3df0c-106">MSTest</span><span class="sxs-lookup"><span data-stu-id="3df0c-106">MSTest</span></span>

```csharp
namespace MSTestNamespace
{
    using Microsoft.VisualStudio.TestTools.UnitTesting;

    [TestClass]
    public class UnitTestClass1
    {
        [Priority(2)]
        [TestMethod]
        public void TestMethod1()
        {
        }

        [TestCategory("CategoryA")]
        [Priority(3)]
        [TestMethod]
        public void TestMethod2()
        {
        }
    }
}
```

| <span data-ttu-id="3df0c-107">Výraz</span><span class="sxs-lookup"><span data-stu-id="3df0c-107">Expression</span></span> | <span data-ttu-id="3df0c-108">Výsledek</span><span class="sxs-lookup"><span data-stu-id="3df0c-108">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="3df0c-109">Spuštění testů, jehož `FullyQualifiedName` obsahuje `Method`.</span><span class="sxs-lookup"><span data-stu-id="3df0c-109">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="3df0c-110">K dispozici v `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="3df0c-110">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="3df0c-111">Spustí testy, jejichž název obsahuje `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="3df0c-111">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTestClass1` | <span data-ttu-id="3df0c-112">Spustí testy, které jsou ve třídě `MSTestNamespace.UnitTestClass1`.</span><span class="sxs-lookup"><span data-stu-id="3df0c-112">Runs tests which are in class `MSTestNamespace.UnitTestClass1`.</span></span><br><span data-ttu-id="3df0c-113">**Poznámka:** `ClassName` hodnota musí mít obor názvů, takže `ClassName=UnitTestClass1` nebude fungovat.</span><span class="sxs-lookup"><span data-stu-id="3df0c-113">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTestClass1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTestClass1.TestMethod1` | <span data-ttu-id="3df0c-114">Spustí všechny testy kromě `MSTestNamespace.UnitTestClass1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="3df0c-114">Runs all tests except `MSTestNamespace.UnitTestClass1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="3df0c-115">Spustí testy, které jsou opatřen poznámkou `[TestCategory("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="3df0c-115">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=3` | <span data-ttu-id="3df0c-116">Spustí testy, které jsou opatřen poznámkou `[Priority(3)]`.</span><span class="sxs-lookup"><span data-stu-id="3df0c-116">Runs tests which are annotated with `[Priority(3)]`.</span></span><br><span data-ttu-id="3df0c-117">**Poznámka:** `Priority~3` je neplatná hodnota, protože není řetězec.</span><span class="sxs-lookup"><span data-stu-id="3df0c-117">**Note:** `Priority~3` is an invalid value, as it isn't a string.</span></span> |

<span data-ttu-id="3df0c-118">**Podmíněné operátory pomocí | a &amp;**</span><span class="sxs-lookup"><span data-stu-id="3df0c-118">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="3df0c-119">Výraz</span><span class="sxs-lookup"><span data-stu-id="3df0c-119">Expression</span></span> | <span data-ttu-id="3df0c-120">Výsledek</span><span class="sxs-lookup"><span data-stu-id="3df0c-120">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTestClass1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="3df0c-121">Spustí testy, které mají `UnitTestClass1` v `FullyQualifiedName` **nebo** `TestCategory` je `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="3df0c-121">Runs tests which have `UnitTestClass1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA"` | <span data-ttu-id="3df0c-122">Spustí testy, které mají `UnitTestClass1` v `FullyQualifiedName` **a** `TestCategory` je `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="3df0c-122">Runs tests which have `UnitTestClass1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="3df0c-123">Spustí testy, které mají buď `FullyQualifiedName` obsahující `UnitTestClass1` **a** `TestCategory` je `CategoryA` **nebo** `Priority` je 1.</span><span class="sxs-lookup"><span data-stu-id="3df0c-123">Runs tests which have either `FullyQualifiedName` containing `UnitTestClass1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="3df0c-124">xUnit</span><span class="sxs-lookup"><span data-stu-id="3df0c-124">xUnit</span></span>

```csharp
namespace XUnitNamespace
{
    public class TestClass1
    {
        [Trait("Category", "bvt")]
        [Trait("Priority", "1")]
        [Fact]
        public void foo()
        {
        }

        [Trait("Category", "Nightly")]
        [Trait("Priority", "2")]
        [Fact]
        public void bar()
        {
        }
    }
}
```

| <span data-ttu-id="3df0c-125">Výraz</span><span class="sxs-lookup"><span data-stu-id="3df0c-125">Expression</span></span> | <span data-ttu-id="3df0c-126">Výsledek</span><span class="sxs-lookup"><span data-stu-id="3df0c-126">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="3df0c-127">Spouští pouze jeden test `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="3df0c-127">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="3df0c-128">Spustí všechny testy kromě `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="3df0c-128">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="3df0c-129">Spustí testy, jejichž název zobrazení obsahuje `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="3df0c-129">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="3df0c-130">V příkladu kódu, jsou definované vlastnosti s klíči `Category` a `Priority` lze použít pro filtrování.</span><span class="sxs-lookup"><span data-stu-id="3df0c-130">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="3df0c-131">Výraz</span><span class="sxs-lookup"><span data-stu-id="3df0c-131">Expression</span></span> | <span data-ttu-id="3df0c-132">Výsledek</span><span class="sxs-lookup"><span data-stu-id="3df0c-132">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="3df0c-133">Spuštění testů, jehož `FullyQualifiedName` obsahuje `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="3df0c-133">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="3df0c-134">K dispozici v `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="3df0c-134">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=bvt` | <span data-ttu-id="3df0c-135">Spustí testy, které mají `[Trait("Category", "bvt")]`.</span><span class="sxs-lookup"><span data-stu-id="3df0c-135">Runs tests which have `[Trait("Category", "bvt")]`.</span></span> |

<span data-ttu-id="3df0c-136">**Podmíněné operátory pomocí | a &amp;**</span><span class="sxs-lookup"><span data-stu-id="3df0c-136">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="3df0c-137">Výraz</span><span class="sxs-lookup"><span data-stu-id="3df0c-137">Expression</span></span> | <span data-ttu-id="3df0c-138">Výsledek</span><span class="sxs-lookup"><span data-stu-id="3df0c-138">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=Nightly"</code> | <span data-ttu-id="3df0c-139">Spustí testy, které má `TestClass1` v `FullyQualifiedName` **nebo** `Category` je `Nightly`.</span><span class="sxs-lookup"><span data-stu-id="3df0c-139">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `Nightly`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=Nightly"` | <span data-ttu-id="3df0c-140">Spustí testy, které má `TestClass1` v `FullyQualifiedName` **a** `Category` je `Nightly`.</span><span class="sxs-lookup"><span data-stu-id="3df0c-140">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `Nightly`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=Nightly)&#124;Priority=1"</code> | <span data-ttu-id="3df0c-141">Spustí testy, které mají buď `FullyQualifiedName` obsahující `TestClass1` **a** `Category` je `CategoryA` **nebo** `Priority` je 1.</span><span class="sxs-lookup"><span data-stu-id="3df0c-141">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |
