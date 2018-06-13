---
title: Testy spuštění selektivní jednotek
description: Ukazuje, jak se použije ke spuštění testů jednotek selektivní test příkazem dotnet výraz filtru.
author: smadala
ms.author: mairaw
ms.date: 03/22/2017
ms.openlocfilehash: caea91e9884dba6bc07a7ef6a99699e43d23399c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33210831"
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="f19e0-103">Testy spuštění selektivní jednotek</span><span class="sxs-lookup"><span data-stu-id="f19e0-103">Running selective unit tests</span></span>

<span data-ttu-id="f19e0-104">Následující příklady použití `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="f19e0-104">The following examples use `dotnet test`.</span></span> <span data-ttu-id="f19e0-105">Pokud používáte `vstest.console.exe`, nahraďte `--filter ` s `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="f19e0-105">If you're using `vstest.console.exe`, replace `--filter ` with `--testcasefilter:`.</span></span>

## <a name="mstest"></a><span data-ttu-id="f19e0-106">MSTest</span><span class="sxs-lookup"><span data-stu-id="f19e0-106">MSTest</span></span>

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

| <span data-ttu-id="f19e0-107">Výraz</span><span class="sxs-lookup"><span data-stu-id="f19e0-107">Expression</span></span> | <span data-ttu-id="f19e0-108">Výsledek</span><span class="sxs-lookup"><span data-stu-id="f19e0-108">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="f19e0-109">Spuštění testů, jehož `FullyQualifiedName` obsahuje `Method`.</span><span class="sxs-lookup"><span data-stu-id="f19e0-109">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="f19e0-110">K dispozici v `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="f19e0-110">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="f19e0-111">Spustí testy, jejichž název obsahuje `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="f19e0-111">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTestClass1` | <span data-ttu-id="f19e0-112">Spustí testy, které jsou ve třídě `MSTestNamespace.UnitTestClass1`.</span><span class="sxs-lookup"><span data-stu-id="f19e0-112">Runs tests which are in class `MSTestNamespace.UnitTestClass1`.</span></span><br><span data-ttu-id="f19e0-113">**Poznámka:** `ClassName` hodnota musí mít obor názvů, takže `ClassName=UnitTestClass1` nebude fungovat.</span><span class="sxs-lookup"><span data-stu-id="f19e0-113">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTestClass1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTestClass1.TestMethod1` | <span data-ttu-id="f19e0-114">Spustí všechny testy kromě `MSTestNamespace.UnitTestClass1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="f19e0-114">Runs all tests except `MSTestNamespace.UnitTestClass1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="f19e0-115">Spustí testy, které jsou opatřen poznámkou `[TestCategory("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="f19e0-115">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=3` | <span data-ttu-id="f19e0-116">Spustí testy, které jsou opatřen poznámkou `[Priority(3)]`.</span><span class="sxs-lookup"><span data-stu-id="f19e0-116">Runs tests which are annotated with `[Priority(3)]`.</span></span><br><span data-ttu-id="f19e0-117">**Poznámka:** `Priority~3` je neplatná hodnota, protože není řetězec.</span><span class="sxs-lookup"><span data-stu-id="f19e0-117">**Note:** `Priority~3` is an invalid value, as it isn't a string.</span></span> |

<span data-ttu-id="f19e0-118">**Podmíněné operátory pomocí | a &amp;**</span><span class="sxs-lookup"><span data-stu-id="f19e0-118">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="f19e0-119">Výraz</span><span class="sxs-lookup"><span data-stu-id="f19e0-119">Expression</span></span> | <span data-ttu-id="f19e0-120">Výsledek</span><span class="sxs-lookup"><span data-stu-id="f19e0-120">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTestClass1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="f19e0-121">Spustí testy, které mají `UnitTestClass1` v `FullyQualifiedName` **nebo** `TestCategory` je `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="f19e0-121">Runs tests which have `UnitTestClass1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA"` | <span data-ttu-id="f19e0-122">Spustí testy, které mají `UnitTestClass1` v `FullyQualifiedName` **a** `TestCategory` je `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="f19e0-122">Runs tests which have `UnitTestClass1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="f19e0-123">Spustí testy, které mají buď `FullyQualifiedName` obsahující `UnitTestClass1` **a** `TestCategory` je `CategoryA` **nebo** `Priority` je 1.</span><span class="sxs-lookup"><span data-stu-id="f19e0-123">Runs tests which have either `FullyQualifiedName` containing `UnitTestClass1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="f19e0-124">xUnit</span><span class="sxs-lookup"><span data-stu-id="f19e0-124">xUnit</span></span>

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

| <span data-ttu-id="f19e0-125">Výraz</span><span class="sxs-lookup"><span data-stu-id="f19e0-125">Expression</span></span> | <span data-ttu-id="f19e0-126">Výsledek</span><span class="sxs-lookup"><span data-stu-id="f19e0-126">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="f19e0-127">Spouští pouze jeden test `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="f19e0-127">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="f19e0-128">Spustí všechny testy kromě `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="f19e0-128">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="f19e0-129">Spustí testy, jejichž název zobrazení obsahuje `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="f19e0-129">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="f19e0-130">V příkladu kódu, jsou definované vlastnosti s klíči `Category` a `Priority` lze použít pro filtrování.</span><span class="sxs-lookup"><span data-stu-id="f19e0-130">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="f19e0-131">Výraz</span><span class="sxs-lookup"><span data-stu-id="f19e0-131">Expression</span></span> | <span data-ttu-id="f19e0-132">Výsledek</span><span class="sxs-lookup"><span data-stu-id="f19e0-132">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="f19e0-133">Spuštění testů, jehož `FullyQualifiedName` obsahuje `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="f19e0-133">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="f19e0-134">K dispozici v `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="f19e0-134">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=bvt` | <span data-ttu-id="f19e0-135">Spustí testy, které mají `[Trait("Category", "bvt")]`.</span><span class="sxs-lookup"><span data-stu-id="f19e0-135">Runs tests which have `[Trait("Category", "bvt")]`.</span></span> |

<span data-ttu-id="f19e0-136">**Podmíněné operátory pomocí | a &amp;**</span><span class="sxs-lookup"><span data-stu-id="f19e0-136">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="f19e0-137">Výraz</span><span class="sxs-lookup"><span data-stu-id="f19e0-137">Expression</span></span> | <span data-ttu-id="f19e0-138">Výsledek</span><span class="sxs-lookup"><span data-stu-id="f19e0-138">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=Nightly"</code> | <span data-ttu-id="f19e0-139">Spustí testy, které má `TestClass1` v `FullyQualifiedName` **nebo** `Category` je `Nightly`.</span><span class="sxs-lookup"><span data-stu-id="f19e0-139">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `Nightly`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=Nightly"` | <span data-ttu-id="f19e0-140">Spustí testy, které má `TestClass1` v `FullyQualifiedName` **a** `Category` je `Nightly`.</span><span class="sxs-lookup"><span data-stu-id="f19e0-140">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `Nightly`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=Nightly)&#124;Priority=1"</code> | <span data-ttu-id="f19e0-141">Spustí testy, které mají buď `FullyQualifiedName` obsahující `TestClass1` **a** `Category` je `CategoryA` **nebo** `Priority` je 1.</span><span class="sxs-lookup"><span data-stu-id="f19e0-141">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |
