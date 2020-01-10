---
title: Spouštění selektivních testů jednotek
description: Jak použít výraz filtru ke spuštění selektivních testů jednotek pomocí příkazu dotnet test v .NET Core.
author: smadala
ms.date: 03/22/2017
ms.openlocfilehash: 57428dad2de6c2507ca2cdc42e3df9e83a1edd69
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715462"
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="6aad0-103">Spouštění selektivních testů jednotek</span><span class="sxs-lookup"><span data-stu-id="6aad0-103">Running selective unit tests</span></span>

<span data-ttu-id="6aad0-104">Pomocí příkazu `dotnet test` v rozhraní .NET Core můžete použít výraz filtru ke spuštění selektivních testů.</span><span class="sxs-lookup"><span data-stu-id="6aad0-104">With the `dotnet test` command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="6aad0-105">Tento článek ukazuje, jak filtrovat, který test se spouští.</span><span class="sxs-lookup"><span data-stu-id="6aad0-105">This article demonstrates how to filter which test are run.</span></span> <span data-ttu-id="6aad0-106">Následující příklady používají `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="6aad0-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="6aad0-107">Pokud používáte `vstest.console.exe`, nahraďte `--filter` `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="6aad0-107">If you're using `vstest.console.exe`, replace `--filter` with `--testcasefilter:`.</span></span>

## <a name="mstest"></a><span data-ttu-id="6aad0-108">MSTest</span><span class="sxs-lookup"><span data-stu-id="6aad0-108">MSTest</span></span>

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

| <span data-ttu-id="6aad0-109">Výraz</span><span class="sxs-lookup"><span data-stu-id="6aad0-109">Expression</span></span> | <span data-ttu-id="6aad0-110">Výsledek</span><span class="sxs-lookup"><span data-stu-id="6aad0-110">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="6aad0-111">Spustí testy, jejichž `FullyQualifiedName` obsahuje `Method`.</span><span class="sxs-lookup"><span data-stu-id="6aad0-111">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="6aad0-112">K dispozici v `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="6aad0-112">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="6aad0-113">Spustí testy, jejichž název obsahuje `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="6aad0-113">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="6aad0-114">Spustí testy, které jsou ve třídě `MSTestNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="6aad0-114">Runs tests which are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="6aad0-115">**Poznámka:** Hodnota `ClassName` by měla mít obor názvů, takže `ClassName=UnitTest1` nebude fungovat.</span><span class="sxs-lookup"><span data-stu-id="6aad0-115">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="6aad0-116">Spustí všechny testy s výjimkou `MSTestNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="6aad0-116">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="6aad0-117">Spustí testy, které jsou poznámy s `[TestCategory("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="6aad0-117">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="6aad0-118">Spustí testy, které jsou poznámy s `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="6aad0-118">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="6aad0-119">**Použití podmíněných operátorů | a &amp;**</span><span class="sxs-lookup"><span data-stu-id="6aad0-119">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="6aad0-120">Výraz</span><span class="sxs-lookup"><span data-stu-id="6aad0-120">Expression</span></span> | <span data-ttu-id="6aad0-121">Výsledek</span><span class="sxs-lookup"><span data-stu-id="6aad0-121">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="6aad0-122">Spustí testy, které mají `UnitTest1` v `FullyQualifiedName` **nebo** `TestCategory` `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="6aad0-122">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="6aad0-123">Spustí testy, které mají `UnitTest1` v `FullyQualifiedName` **a** `TestCategory` je `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="6aad0-123">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="6aad0-124">Spustí testy, které mají buď `FullyQualifiedName` obsahující `UnitTest1` **a** `TestCategory` jsou `CategoryA` **nebo** `Priority` 1.</span><span class="sxs-lookup"><span data-stu-id="6aad0-124">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="6aad0-125">xUnit</span><span class="sxs-lookup"><span data-stu-id="6aad0-125">xUnit</span></span>

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

| <span data-ttu-id="6aad0-126">Výraz</span><span class="sxs-lookup"><span data-stu-id="6aad0-126">Expression</span></span> | <span data-ttu-id="6aad0-127">Výsledek</span><span class="sxs-lookup"><span data-stu-id="6aad0-127">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="6aad0-128">Spustí pouze jeden test, `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="6aad0-128">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="6aad0-129">Spustí všechny testy s výjimkou `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="6aad0-129">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="6aad0-130">Spustí testy, jejichž zobrazovaný název obsahuje `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="6aad0-130">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="6aad0-131">V příkladu kódu lze pro filtrování použít definované vlastnosti s klíči `Category` a `Priority`.</span><span class="sxs-lookup"><span data-stu-id="6aad0-131">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="6aad0-132">Výraz</span><span class="sxs-lookup"><span data-stu-id="6aad0-132">Expression</span></span> | <span data-ttu-id="6aad0-133">Výsledek</span><span class="sxs-lookup"><span data-stu-id="6aad0-133">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="6aad0-134">Spustí testy, jejichž `FullyQualifiedName` obsahuje `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="6aad0-134">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="6aad0-135">K dispozici v `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="6aad0-135">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="6aad0-136">Spustí testy, které mají `[Trait("Category", "CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="6aad0-136">Runs tests which have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="6aad0-137">**Použití podmíněných operátorů | a &amp;**</span><span class="sxs-lookup"><span data-stu-id="6aad0-137">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="6aad0-138">Výraz</span><span class="sxs-lookup"><span data-stu-id="6aad0-138">Expression</span></span> | <span data-ttu-id="6aad0-139">Výsledek</span><span class="sxs-lookup"><span data-stu-id="6aad0-139">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="6aad0-140">Spustí testy, které mají `TestClass1` v `FullyQualifiedName` **nebo** `Category` `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="6aad0-140">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="6aad0-141">Spustí testy, které mají `TestClass1` v `FullyQualifiedName` **a** `Category` je `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="6aad0-141">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="6aad0-142">Spustí testy, které mají buď `FullyQualifiedName` obsahující `TestClass1` **a** `Category` jsou `CategoryA` **nebo** `Priority` 1.</span><span class="sxs-lookup"><span data-stu-id="6aad0-142">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="6aad0-143">NUnit</span><span class="sxs-lookup"><span data-stu-id="6aad0-143">NUnit</span></span>

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

| <span data-ttu-id="6aad0-144">Výraz</span><span class="sxs-lookup"><span data-stu-id="6aad0-144">Expression</span></span> | <span data-ttu-id="6aad0-145">Výsledek</span><span class="sxs-lookup"><span data-stu-id="6aad0-145">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="6aad0-146">Spustí testy, jejichž `FullyQualifiedName` obsahuje `Method`.</span><span class="sxs-lookup"><span data-stu-id="6aad0-146">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="6aad0-147">K dispozici v `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="6aad0-147">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="6aad0-148">Spustí testy, jejichž název obsahuje `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="6aad0-148">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="6aad0-149">Spustí testy, které jsou ve třídě `NUnitNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="6aad0-149">Runs tests which are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="6aad0-150">Spustí všechny testy s výjimkou `NUnitNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="6aad0-150">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="6aad0-151">Spustí testy, které jsou poznámy s `[Category("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="6aad0-151">Runs tests which are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="6aad0-152">Spustí testy, které jsou poznámy s `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="6aad0-152">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="6aad0-153">**Použití podmíněných operátorů | a &amp;**</span><span class="sxs-lookup"><span data-stu-id="6aad0-153">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="6aad0-154">Výraz</span><span class="sxs-lookup"><span data-stu-id="6aad0-154">Expression</span></span> | <span data-ttu-id="6aad0-155">Výsledek</span><span class="sxs-lookup"><span data-stu-id="6aad0-155">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="6aad0-156">Spustí testy, které mají `UnitTest1` v `FullyQualifiedName` **nebo** `TestCategory` `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="6aad0-156">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="6aad0-157">Spustí testy, které mají `UnitTest1` v `FullyQualifiedName` **a** `TestCategory` je `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="6aad0-157">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="6aad0-158">Spustí testy, které mají buď `FullyQualifiedName` obsahující `UnitTest1` **a** `TestCategory` jsou `CategoryA` **nebo** `Priority` 1.</span><span class="sxs-lookup"><span data-stu-id="6aad0-158">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |
