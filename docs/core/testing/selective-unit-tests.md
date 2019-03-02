---
title: Spouštění selektivních testů jednotek
description: Jak pomocí výrazu filtru spouštění selektivních testů jednotek pomocí příkazu dotnet test v .NET Core.
author: smadala
ms.date: 03/22/2017
ms.custom: seodec18
ms.openlocfilehash: 6160a8b9184d031fcc06356b5b489ee24b765e84
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57201414"
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="51ab9-103">Spouštění selektivních testů jednotek</span><span class="sxs-lookup"><span data-stu-id="51ab9-103">Running selective unit tests</span></span>

<span data-ttu-id="51ab9-104">S `dotnet test` příkaz v .NET Core, vám pomůže výraz filtru spouštění selektivních testů.</span><span class="sxs-lookup"><span data-stu-id="51ab9-104">With the `dotnet test` command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="51ab9-105">Tento článek ukazuje, jak filtrovat, kterou test běží.</span><span class="sxs-lookup"><span data-stu-id="51ab9-105">This article demonstrates how to filter which test are run.</span></span> <span data-ttu-id="51ab9-106">Následující příklady používají `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="51ab9-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="51ab9-107">Pokud používáte `vstest.console.exe`, nahraďte `--filter` s `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="51ab9-107">If you're using `vstest.console.exe`, replace `--filter` with `--testcasefilter:`.</span></span>

## <a name="mstest"></a><span data-ttu-id="51ab9-108">MSTest</span><span class="sxs-lookup"><span data-stu-id="51ab9-108">MSTest</span></span>

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace MSTestNamespace
{
    [TestClass]
    public class UnitTest1
    {
        [TestCategory("CategoryA")]
        [Priority(1)]
        [TestMethod]
        public void TestMethod1()
        {
        }

        [Priority(2)]
        [TestMethod]
        public void TestMethod2()
        {
        }
    }
}
```

| <span data-ttu-id="51ab9-109">Výraz</span><span class="sxs-lookup"><span data-stu-id="51ab9-109">Expression</span></span> | <span data-ttu-id="51ab9-110">Výsledek</span><span class="sxs-lookup"><span data-stu-id="51ab9-110">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="51ab9-111">Spustí testy, jejichž `FullyQualifiedName` obsahuje `Method`.</span><span class="sxs-lookup"><span data-stu-id="51ab9-111">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="51ab9-112">K dispozici v `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="51ab9-112">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="51ab9-113">Spustí testy, jejichž název obsahuje `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="51ab9-113">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="51ab9-114">Spustí testy, které jsou ve třídě `MSTestNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="51ab9-114">Runs tests which are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="51ab9-115">**Poznámka:** `ClassName` Hodnota by měla mít oboru názvů, tak `ClassName=UnitTest1` nebude fungovat.</span><span class="sxs-lookup"><span data-stu-id="51ab9-115">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="51ab9-116">Spustí všechny testy s výjimkou `MSTestNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="51ab9-116">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="51ab9-117">Spustí testy, které jsou opatřeny poznámkami s `[TestCategory("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="51ab9-117">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="51ab9-118">Spustí testy, které jsou opatřeny poznámkami s `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="51ab9-118">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="51ab9-119">**Použití podmíněných operátorů | a &amp;**</span><span class="sxs-lookup"><span data-stu-id="51ab9-119">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="51ab9-120">Výraz</span><span class="sxs-lookup"><span data-stu-id="51ab9-120">Expression</span></span> | <span data-ttu-id="51ab9-121">Výsledek</span><span class="sxs-lookup"><span data-stu-id="51ab9-121">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="51ab9-122">Spustí testy, které mají `UnitTest1` v `FullyQualifiedName` **nebo** `TestCategory` je `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="51ab9-122">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="51ab9-123">Spustí testy, které mají `UnitTest1` v `FullyQualifiedName` **a** `TestCategory` je `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="51ab9-123">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="51ab9-124">Spustí testy, které mají buď `FullyQualifiedName` obsahující `UnitTest1` **a** `TestCategory` je `CategoryA` **nebo** `Priority` 1.</span><span class="sxs-lookup"><span data-stu-id="51ab9-124">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="51ab9-125">xUnit</span><span class="sxs-lookup"><span data-stu-id="51ab9-125">xUnit</span></span>

```csharp
using Xunit;

namespace XUnitNamespace
{
    public class TestClass1
    {
        [Trait("Category", "CategoryA")]
        [Trait("Priority", "1")]
        [Fact]
        public void Test1()
        {
        }

        [Trait("Priority", "2")]
        [Fact]
        public void Test2()
        {
        }
    }
}
```

| <span data-ttu-id="51ab9-126">Výraz</span><span class="sxs-lookup"><span data-stu-id="51ab9-126">Expression</span></span> | <span data-ttu-id="51ab9-127">Výsledek</span><span class="sxs-lookup"><span data-stu-id="51ab9-127">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="51ab9-128">Pouze jeden test spouští `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="51ab9-128">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="51ab9-129">Spustí všechny testy s výjimkou `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="51ab9-129">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="51ab9-130">Spustí testy, jejichž zobrazované jméno obsahuje `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="51ab9-130">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="51ab9-131">V příkladu kódu, jsou definované vlastnosti s klíči `Category` a `Priority` lze použít pro filtrování.</span><span class="sxs-lookup"><span data-stu-id="51ab9-131">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="51ab9-132">Výraz</span><span class="sxs-lookup"><span data-stu-id="51ab9-132">Expression</span></span> | <span data-ttu-id="51ab9-133">Výsledek</span><span class="sxs-lookup"><span data-stu-id="51ab9-133">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="51ab9-134">Spustí testy, jejichž `FullyQualifiedName` obsahuje `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="51ab9-134">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="51ab9-135">K dispozici v `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="51ab9-135">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="51ab9-136">Spustí testy, které mají `[Trait("Category", "CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="51ab9-136">Runs tests which have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="51ab9-137">**Použití podmíněných operátorů | a &amp;**</span><span class="sxs-lookup"><span data-stu-id="51ab9-137">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="51ab9-138">Výraz</span><span class="sxs-lookup"><span data-stu-id="51ab9-138">Expression</span></span> | <span data-ttu-id="51ab9-139">Výsledek</span><span class="sxs-lookup"><span data-stu-id="51ab9-139">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="51ab9-140">Spuštění testů, které má `TestClass1` v `FullyQualifiedName` **nebo** `Category` je `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="51ab9-140">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="51ab9-141">Spuštění testů, které má `TestClass1` v `FullyQualifiedName` **a** `Category` je `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="51ab9-141">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="51ab9-142">Spustí testy, které mají buď `FullyQualifiedName` obsahující `TestClass1` **a** `Category` je `CategoryA` **nebo** `Priority` 1.</span><span class="sxs-lookup"><span data-stu-id="51ab9-142">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="51ab9-143">NUnit</span><span class="sxs-lookup"><span data-stu-id="51ab9-143">NUnit</span></span>

```csharp
using NUnit.Framework;

namespace NUnitNamespace
{
    public class UnitTest1
    {
        [Category("CategoryA")]
        [Property("Priority", 1)]
        [Test]
        public void TestMethod1()
        {
        }

        [Property("Priority", 2)]
        [Test]
        public void TestMethod2()
        {
        }
    }
}
```

| <span data-ttu-id="51ab9-144">Výraz</span><span class="sxs-lookup"><span data-stu-id="51ab9-144">Expression</span></span> | <span data-ttu-id="51ab9-145">Výsledek</span><span class="sxs-lookup"><span data-stu-id="51ab9-145">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="51ab9-146">Spustí testy, jejichž `FullyQualifiedName` obsahuje `Method`.</span><span class="sxs-lookup"><span data-stu-id="51ab9-146">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="51ab9-147">K dispozici v `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="51ab9-147">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="51ab9-148">Spustí testy, jejichž název obsahuje `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="51ab9-148">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="51ab9-149">Spustí testy, které jsou ve třídě `NUnitNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="51ab9-149">Runs tests which are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="51ab9-150">Spustí všechny testy s výjimkou `NUnitNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="51ab9-150">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="51ab9-151">Spustí testy, které jsou opatřeny poznámkami s `[Category("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="51ab9-151">Runs tests which are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="51ab9-152">Spustí testy, které jsou opatřeny poznámkami s `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="51ab9-152">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="51ab9-153">**Použití podmíněných operátorů | a &amp;**</span><span class="sxs-lookup"><span data-stu-id="51ab9-153">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="51ab9-154">Výraz</span><span class="sxs-lookup"><span data-stu-id="51ab9-154">Expression</span></span> | <span data-ttu-id="51ab9-155">Výsledek</span><span class="sxs-lookup"><span data-stu-id="51ab9-155">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="51ab9-156">Spustí testy, které mají `UnitTest1` v `FullyQualifiedName` **nebo** `TestCategory` je `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="51ab9-156">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="51ab9-157">Spustí testy, které mají `UnitTest1` v `FullyQualifiedName` **a** `TestCategory` je `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="51ab9-157">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="51ab9-158">Spustí testy, které mají buď `FullyQualifiedName` obsahující `UnitTest1` **a** `TestCategory` je `CategoryA` **nebo** `Priority` 1.</span><span class="sxs-lookup"><span data-stu-id="51ab9-158">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |
