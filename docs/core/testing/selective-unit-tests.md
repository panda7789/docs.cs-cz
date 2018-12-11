---
title: Spouštění selektivních testů jednotek
description: Jak pomocí výrazu filtru spouštění selektivních testů jednotek pomocí příkazu dotnet test v .NET Core.
author: smadala
ms.date: 03/22/2017
ms.custom: seodec18
ms.openlocfilehash: 1a90438e3b0b2eb095124208010bbe9558424d91
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170186"
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="f4a0e-103">Spouštění selektivních testů jednotek</span><span class="sxs-lookup"><span data-stu-id="f4a0e-103">Running selective unit tests</span></span>

<span data-ttu-id="f4a0e-104">Následující příklady používají `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="f4a0e-104">The following examples use `dotnet test`.</span></span> <span data-ttu-id="f4a0e-105">Pokud používáte `vstest.console.exe`, nahraďte `--filter ` s `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="f4a0e-105">If you're using `vstest.console.exe`, replace `--filter ` with `--testcasefilter:`.</span></span>

## <a name="mstest"></a><span data-ttu-id="f4a0e-106">MSTest</span><span class="sxs-lookup"><span data-stu-id="f4a0e-106">MSTest</span></span>

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

| <span data-ttu-id="f4a0e-107">Výraz</span><span class="sxs-lookup"><span data-stu-id="f4a0e-107">Expression</span></span> | <span data-ttu-id="f4a0e-108">Výsledek</span><span class="sxs-lookup"><span data-stu-id="f4a0e-108">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="f4a0e-109">Spustí testy, jejichž `FullyQualifiedName` obsahuje `Method`.</span><span class="sxs-lookup"><span data-stu-id="f4a0e-109">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="f4a0e-110">K dispozici v `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="f4a0e-110">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="f4a0e-111">Spustí testy, jejichž název obsahuje `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="f4a0e-111">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="f4a0e-112">Spustí testy, které jsou ve třídě `MSTestNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="f4a0e-112">Runs tests which are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="f4a0e-113">**Poznámka:** `ClassName` Hodnota by měla mít oboru názvů, tak `ClassName=UnitTest1` nebude fungovat.</span><span class="sxs-lookup"><span data-stu-id="f4a0e-113">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="f4a0e-114">Spustí všechny testy s výjimkou `MSTestNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="f4a0e-114">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="f4a0e-115">Spustí testy, které jsou opatřeny poznámkami s `[TestCategory("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="f4a0e-115">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="f4a0e-116">Spustí testy, které jsou opatřeny poznámkami s `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="f4a0e-116">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="f4a0e-117">**Použití podmíněných operátorů | a &amp;**</span><span class="sxs-lookup"><span data-stu-id="f4a0e-117">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="f4a0e-118">Výraz</span><span class="sxs-lookup"><span data-stu-id="f4a0e-118">Expression</span></span> | <span data-ttu-id="f4a0e-119">Výsledek</span><span class="sxs-lookup"><span data-stu-id="f4a0e-119">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="f4a0e-120">Spustí testy, které mají `UnitTest1` v `FullyQualifiedName` **nebo** `TestCategory` je `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="f4a0e-120">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="f4a0e-121">Spustí testy, které mají `UnitTest1` v `FullyQualifiedName` **a** `TestCategory` je `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="f4a0e-121">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="f4a0e-122">Spustí testy, které mají buď `FullyQualifiedName` obsahující `UnitTest1` **a** `TestCategory` je `CategoryA` **nebo** `Priority` 1.</span><span class="sxs-lookup"><span data-stu-id="f4a0e-122">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="f4a0e-123">xUnit</span><span class="sxs-lookup"><span data-stu-id="f4a0e-123">xUnit</span></span>

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

| <span data-ttu-id="f4a0e-124">Výraz</span><span class="sxs-lookup"><span data-stu-id="f4a0e-124">Expression</span></span> | <span data-ttu-id="f4a0e-125">Výsledek</span><span class="sxs-lookup"><span data-stu-id="f4a0e-125">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="f4a0e-126">Pouze jeden test spouští `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="f4a0e-126">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="f4a0e-127">Spustí všechny testy s výjimkou `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="f4a0e-127">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="f4a0e-128">Spustí testy, jejichž zobrazované jméno obsahuje `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="f4a0e-128">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="f4a0e-129">V příkladu kódu, jsou definované vlastnosti s klíči `Category` a `Priority` lze použít pro filtrování.</span><span class="sxs-lookup"><span data-stu-id="f4a0e-129">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="f4a0e-130">Výraz</span><span class="sxs-lookup"><span data-stu-id="f4a0e-130">Expression</span></span> | <span data-ttu-id="f4a0e-131">Výsledek</span><span class="sxs-lookup"><span data-stu-id="f4a0e-131">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="f4a0e-132">Spustí testy, jejichž `FullyQualifiedName` obsahuje `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="f4a0e-132">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="f4a0e-133">K dispozici v `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="f4a0e-133">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="f4a0e-134">Spustí testy, které mají `[Trait("Category", "CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="f4a0e-134">Runs tests which have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="f4a0e-135">**Použití podmíněných operátorů | a &amp;**</span><span class="sxs-lookup"><span data-stu-id="f4a0e-135">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="f4a0e-136">Výraz</span><span class="sxs-lookup"><span data-stu-id="f4a0e-136">Expression</span></span> | <span data-ttu-id="f4a0e-137">Výsledek</span><span class="sxs-lookup"><span data-stu-id="f4a0e-137">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="f4a0e-138">Spuštění testů, které má `TestClass1` v `FullyQualifiedName` **nebo** `Category` je `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="f4a0e-138">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="f4a0e-139">Spuštění testů, které má `TestClass1` v `FullyQualifiedName` **a** `Category` je `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="f4a0e-139">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="f4a0e-140">Spustí testy, které mají buď `FullyQualifiedName` obsahující `TestClass1` **a** `Category` je `CategoryA` **nebo** `Priority` 1.</span><span class="sxs-lookup"><span data-stu-id="f4a0e-140">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="f4a0e-141">NUnit</span><span class="sxs-lookup"><span data-stu-id="f4a0e-141">NUnit</span></span>

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

| <span data-ttu-id="f4a0e-142">Výraz</span><span class="sxs-lookup"><span data-stu-id="f4a0e-142">Expression</span></span> | <span data-ttu-id="f4a0e-143">Výsledek</span><span class="sxs-lookup"><span data-stu-id="f4a0e-143">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="f4a0e-144">Spustí testy, jejichž `FullyQualifiedName` obsahuje `Method`.</span><span class="sxs-lookup"><span data-stu-id="f4a0e-144">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="f4a0e-145">K dispozici v `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="f4a0e-145">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="f4a0e-146">Spustí testy, jejichž název obsahuje `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="f4a0e-146">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="f4a0e-147">Spustí testy, které jsou ve třídě `NUnitNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="f4a0e-147">Runs tests which are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="f4a0e-148">Spustí všechny testy s výjimkou `NUnitNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="f4a0e-148">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="f4a0e-149">Spustí testy, které jsou opatřeny poznámkami s `[Category("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="f4a0e-149">Runs tests which are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="f4a0e-150">Spustí testy, které jsou opatřeny poznámkami s `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="f4a0e-150">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="f4a0e-151">**Použití podmíněných operátorů | a &amp;**</span><span class="sxs-lookup"><span data-stu-id="f4a0e-151">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="f4a0e-152">Výraz</span><span class="sxs-lookup"><span data-stu-id="f4a0e-152">Expression</span></span> | <span data-ttu-id="f4a0e-153">Výsledek</span><span class="sxs-lookup"><span data-stu-id="f4a0e-153">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="f4a0e-154">Spustí testy, které mají `UnitTest1` v `FullyQualifiedName` **nebo** `TestCategory` je `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="f4a0e-154">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="f4a0e-155">Spustí testy, které mají `UnitTest1` v `FullyQualifiedName` **a** `TestCategory` je `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="f4a0e-155">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="f4a0e-156">Spustí testy, které mají buď `FullyQualifiedName` obsahující `UnitTest1` **a** `TestCategory` je `CategoryA` **nebo** `Priority` 1.</span><span class="sxs-lookup"><span data-stu-id="f4a0e-156">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |
