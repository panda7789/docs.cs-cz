---
title: Spouštění selektivních testů jednotek
description: Jak použít výraz filtru ke spuštění selektivních testů jednotek pomocí příkazu dotnet test v .NET Core.
author: smadala
ms.date: 03/22/2017
ms.openlocfilehash: b9156300587215e68c01c609e298dbc1a2c53d11
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543505"
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="a1486-103">Spouštění selektivních testů jednotek</span><span class="sxs-lookup"><span data-stu-id="a1486-103">Running selective unit tests</span></span>

<span data-ttu-id="a1486-104">Pomocí příkazu `dotnet test` v rozhraní .NET Core můžete použít výraz filtru ke spuštění selektivních testů.</span><span class="sxs-lookup"><span data-stu-id="a1486-104">With the `dotnet test` command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="a1486-105">Tento článek ukazuje, jak filtrovat, který test se spouští.</span><span class="sxs-lookup"><span data-stu-id="a1486-105">This article demonstrates how to filter which test are run.</span></span> <span data-ttu-id="a1486-106">Následující příklady používají `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="a1486-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="a1486-107">Pokud používáte `vstest.console.exe`, nahraďte `--filter` `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="a1486-107">If you're using `vstest.console.exe`, replace `--filter` with `--testcasefilter:`.</span></span>

> [!NOTE]
> <span data-ttu-id="a1486-108">Použití filtrů, které zahrnují vykřičník (!) na `*nix` vyžaduje uvozovací znaky, protože je `!` vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="a1486-108">Using filters that include exclamation mark (!) on `*nix` requires escaping since `!` is reserved.</span></span> <span data-ttu-id="a1486-109">Například tento filtr přeskočí všechny testy, pokud obor názvů obsahuje IntegrationTests: `dotnet test --filter FullyQualifiedName\!~IntegrationTests`.</span><span class="sxs-lookup"><span data-stu-id="a1486-109">For example, this filter skips all tests if the namespace contains IntegrationTests: `dotnet test --filter FullyQualifiedName\!~IntegrationTests`.</span></span>
> <span data-ttu-id="a1486-110">Všimněte si zpětného lomítka před vykřičníkem.</span><span class="sxs-lookup"><span data-stu-id="a1486-110">Note the backslash that precedes the exclamation mark.</span></span>

## <a name="mstest"></a><span data-ttu-id="a1486-111">MSTest</span><span class="sxs-lookup"><span data-stu-id="a1486-111">MSTest</span></span>

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

| <span data-ttu-id="a1486-112">Výraz</span><span class="sxs-lookup"><span data-stu-id="a1486-112">Expression</span></span> | <span data-ttu-id="a1486-113">Výsledek</span><span class="sxs-lookup"><span data-stu-id="a1486-113">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="a1486-114">Spustí testy, jejichž `FullyQualifiedName` obsahuje `Method`.</span><span class="sxs-lookup"><span data-stu-id="a1486-114">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="a1486-115">K dispozici v `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="a1486-115">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="a1486-116">Spustí testy, jejichž název obsahuje `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="a1486-116">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="a1486-117">Spustí testy, které jsou ve třídě `MSTestNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="a1486-117">Runs tests which are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="a1486-118">**Poznámka:** Hodnota `ClassName` by měla mít obor názvů, takže `ClassName=UnitTest1` nebude fungovat.</span><span class="sxs-lookup"><span data-stu-id="a1486-118">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="a1486-119">Spustí všechny testy s výjimkou `MSTestNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="a1486-119">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="a1486-120">Spustí testy, které jsou poznámy s `[TestCategory("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="a1486-120">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="a1486-121">Spustí testy, které jsou poznámy s `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="a1486-121">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="a1486-122">**Použití podmíněných operátorů | a &amp;**</span><span class="sxs-lookup"><span data-stu-id="a1486-122">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="a1486-123">Výraz</span><span class="sxs-lookup"><span data-stu-id="a1486-123">Expression</span></span> | <span data-ttu-id="a1486-124">Výsledek</span><span class="sxs-lookup"><span data-stu-id="a1486-124">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="a1486-125">Spustí testy, které mají `UnitTest1` v `FullyQualifiedName` **nebo** `TestCategory` `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="a1486-125">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="a1486-126">Spustí testy, které mají `UnitTest1` v `FullyQualifiedName` **a** `TestCategory` je `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="a1486-126">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="a1486-127">Spustí testy, které mají buď `FullyQualifiedName` obsahující `UnitTest1` **a** `TestCategory` jsou `CategoryA` **nebo** `Priority` 1.</span><span class="sxs-lookup"><span data-stu-id="a1486-127">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="a1486-128">xUnit</span><span class="sxs-lookup"><span data-stu-id="a1486-128">xUnit</span></span>

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

| <span data-ttu-id="a1486-129">Výraz</span><span class="sxs-lookup"><span data-stu-id="a1486-129">Expression</span></span> | <span data-ttu-id="a1486-130">Výsledek</span><span class="sxs-lookup"><span data-stu-id="a1486-130">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="a1486-131">Spustí pouze jeden test, `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="a1486-131">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="a1486-132">Spustí všechny testy s výjimkou `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="a1486-132">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="a1486-133">Spustí testy, jejichž zobrazovaný název obsahuje `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="a1486-133">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="a1486-134">V příkladu kódu lze pro filtrování použít definované vlastnosti s klíči `Category` a `Priority`.</span><span class="sxs-lookup"><span data-stu-id="a1486-134">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="a1486-135">Výraz</span><span class="sxs-lookup"><span data-stu-id="a1486-135">Expression</span></span> | <span data-ttu-id="a1486-136">Výsledek</span><span class="sxs-lookup"><span data-stu-id="a1486-136">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="a1486-137">Spustí testy, jejichž `FullyQualifiedName` obsahuje `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="a1486-137">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="a1486-138">K dispozici v `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="a1486-138">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="a1486-139">Spustí testy, které mají `[Trait("Category", "CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="a1486-139">Runs tests which have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="a1486-140">**Použití podmíněných operátorů | a &amp;**</span><span class="sxs-lookup"><span data-stu-id="a1486-140">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="a1486-141">Výraz</span><span class="sxs-lookup"><span data-stu-id="a1486-141">Expression</span></span> | <span data-ttu-id="a1486-142">Výsledek</span><span class="sxs-lookup"><span data-stu-id="a1486-142">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="a1486-143">Spustí testy, které mají `TestClass1` v `FullyQualifiedName` **nebo** `Category` `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="a1486-143">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="a1486-144">Spustí testy, které mají `TestClass1` v `FullyQualifiedName` **a** `Category` je `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="a1486-144">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="a1486-145">Spustí testy, které mají buď `FullyQualifiedName` obsahující `TestClass1` **a** `Category` jsou `CategoryA` **nebo** `Priority` 1.</span><span class="sxs-lookup"><span data-stu-id="a1486-145">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="a1486-146">NUnit</span><span class="sxs-lookup"><span data-stu-id="a1486-146">NUnit</span></span>

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

| <span data-ttu-id="a1486-147">Výraz</span><span class="sxs-lookup"><span data-stu-id="a1486-147">Expression</span></span> | <span data-ttu-id="a1486-148">Výsledek</span><span class="sxs-lookup"><span data-stu-id="a1486-148">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="a1486-149">Spustí testy, jejichž `FullyQualifiedName` obsahuje `Method`.</span><span class="sxs-lookup"><span data-stu-id="a1486-149">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="a1486-150">K dispozici v `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="a1486-150">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="a1486-151">Spustí testy, jejichž název obsahuje `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="a1486-151">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="a1486-152">Spustí testy, které jsou ve třídě `NUnitNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="a1486-152">Runs tests which are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="a1486-153">Spustí všechny testy s výjimkou `NUnitNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="a1486-153">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="a1486-154">Spustí testy, které jsou poznámy s `[Category("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="a1486-154">Runs tests which are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="a1486-155">Spustí testy, které jsou poznámy s `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="a1486-155">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="a1486-156">**Použití podmíněných operátorů | a &amp;**</span><span class="sxs-lookup"><span data-stu-id="a1486-156">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="a1486-157">Výraz</span><span class="sxs-lookup"><span data-stu-id="a1486-157">Expression</span></span> | <span data-ttu-id="a1486-158">Výsledek</span><span class="sxs-lookup"><span data-stu-id="a1486-158">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="a1486-159">Spustí testy, které mají `UnitTest1` v `FullyQualifiedName` **nebo** `TestCategory` `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="a1486-159">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="a1486-160">Spustí testy, které mají `UnitTest1` v `FullyQualifiedName` **a** `TestCategory` je `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="a1486-160">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="a1486-161">Spustí testy, které mají buď `FullyQualifiedName` obsahující `UnitTest1` **a** `TestCategory` jsou `CategoryA` **nebo** `Priority` 1.</span><span class="sxs-lookup"><span data-stu-id="a1486-161">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |
