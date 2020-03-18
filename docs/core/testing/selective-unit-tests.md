---
title: Spouštění selektivních testů jednotek
description: Použití výrazu filtru ke spuštění selektivních testů částí pomocí příkazu dotnet test v rozhraní .NET Core.
author: smadala
ms.date: 03/22/2017
ms.openlocfilehash: b9156300587215e68c01c609e298dbc1a2c53d11
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77543505"
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="3f085-103">Spouštění selektivních testů jednotek</span><span class="sxs-lookup"><span data-stu-id="3f085-103">Running selective unit tests</span></span>

<span data-ttu-id="3f085-104">Pomocí `dotnet test` příkazu v majekně .NET Core můžete ke spuštění selektivních testů použít výraz filtru.</span><span class="sxs-lookup"><span data-stu-id="3f085-104">With the `dotnet test` command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="3f085-105">Tento článek ukazuje, jak filtrovat, které test jsou spuštěny.</span><span class="sxs-lookup"><span data-stu-id="3f085-105">This article demonstrates how to filter which test are run.</span></span> <span data-ttu-id="3f085-106">Následující příklady `dotnet test`používají .</span><span class="sxs-lookup"><span data-stu-id="3f085-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="3f085-107">Pokud používáte `vstest.console.exe`, `--filter` nahraďte na `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="3f085-107">If you're using `vstest.console.exe`, replace `--filter` with `--testcasefilter:`.</span></span>

> [!NOTE]
> <span data-ttu-id="3f085-108">Použití filtrů, které obsahují vykřičník (!) na `*nix` vyžaduje úniku, protože `!` je vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="3f085-108">Using filters that include exclamation mark (!) on `*nix` requires escaping since `!` is reserved.</span></span> <span data-ttu-id="3f085-109">Tento filtr například přeskočí všechny testy, pokud `dotnet test --filter FullyQualifiedName\!~IntegrationTests`obor názvů obsahuje IntegrationTests: .</span><span class="sxs-lookup"><span data-stu-id="3f085-109">For example, this filter skips all tests if the namespace contains IntegrationTests: `dotnet test --filter FullyQualifiedName\!~IntegrationTests`.</span></span>
> <span data-ttu-id="3f085-110">Všimněte si zpětného lomítka, které předchází vykřičník.</span><span class="sxs-lookup"><span data-stu-id="3f085-110">Note the backslash that precedes the exclamation mark.</span></span>

## <a name="mstest"></a><span data-ttu-id="3f085-111">MSTest</span><span class="sxs-lookup"><span data-stu-id="3f085-111">MSTest</span></span>

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

| <span data-ttu-id="3f085-112">Expression</span><span class="sxs-lookup"><span data-stu-id="3f085-112">Expression</span></span> | <span data-ttu-id="3f085-113">Výsledek</span><span class="sxs-lookup"><span data-stu-id="3f085-113">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="3f085-114">Spustí testy, jejichž `FullyQualifiedName` obsahuje `Method`.</span><span class="sxs-lookup"><span data-stu-id="3f085-114">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="3f085-115">K `vstest 15.1+`dispozici v .</span><span class="sxs-lookup"><span data-stu-id="3f085-115">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="3f085-116">Spustí testy, `TestMethod1`jejichž název obsahuje .</span><span class="sxs-lookup"><span data-stu-id="3f085-116">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="3f085-117">Spustí testy, které `MSTestNamespace.UnitTest1`jsou ve třídě .</span><span class="sxs-lookup"><span data-stu-id="3f085-117">Runs tests which are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="3f085-118">**Poznámka:** Hodnota `ClassName` by měla mít obor `ClassName=UnitTest1` názvů, takže nebude fungovat.</span><span class="sxs-lookup"><span data-stu-id="3f085-118">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="3f085-119">Spustí všechny `MSTestNamespace.UnitTest1.TestMethod1`testy s výjimkou .</span><span class="sxs-lookup"><span data-stu-id="3f085-119">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="3f085-120">Spustí testy, které jsou `[TestCategory("CategoryA")]`anotovány s .</span><span class="sxs-lookup"><span data-stu-id="3f085-120">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="3f085-121">Spustí testy, které jsou `[Priority(2)]`anotovány s .</span><span class="sxs-lookup"><span data-stu-id="3f085-121">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="3f085-122">**Použití podmíněných operátorů | A&amp;**</span><span class="sxs-lookup"><span data-stu-id="3f085-122">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="3f085-123">Expression</span><span class="sxs-lookup"><span data-stu-id="3f085-123">Expression</span></span> | <span data-ttu-id="3f085-124">Výsledek</span><span class="sxs-lookup"><span data-stu-id="3f085-124">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="3f085-125">Spustí testy, `UnitTest1` `FullyQualifiedName` které `CategoryA`mají v **nebo** `TestCategory` je .</span><span class="sxs-lookup"><span data-stu-id="3f085-125">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="3f085-126">Spustí testy, `UnitTest1` `FullyQualifiedName` které `CategoryA`mají v **.** `TestCategory`</span><span class="sxs-lookup"><span data-stu-id="3f085-126">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="3f085-127">Spustí testy, `FullyQualifiedName` které `UnitTest1` **and** `TestCategory` obsahují `CategoryA` a je **nebo** `Priority` je 1.</span><span class="sxs-lookup"><span data-stu-id="3f085-127">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="3f085-128">xJednotka</span><span class="sxs-lookup"><span data-stu-id="3f085-128">xUnit</span></span>

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

| <span data-ttu-id="3f085-129">Expression</span><span class="sxs-lookup"><span data-stu-id="3f085-129">Expression</span></span> | <span data-ttu-id="3f085-130">Výsledek</span><span class="sxs-lookup"><span data-stu-id="3f085-130">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="3f085-131">Spustí pouze jeden `XUnitNamespace.TestClass1.Test1`test, .</span><span class="sxs-lookup"><span data-stu-id="3f085-131">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="3f085-132">Spustí všechny `XUnitNamespace.TestClass1.Test1`testy s výjimkou .</span><span class="sxs-lookup"><span data-stu-id="3f085-132">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="3f085-133">Spustí testy, jejichž `TestClass1`zobrazovaný název obsahuje .</span><span class="sxs-lookup"><span data-stu-id="3f085-133">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="3f085-134">V příkladu kódu definované vlastnosti `Category` `Priority` s klíči a lze použít pro filtrování.</span><span class="sxs-lookup"><span data-stu-id="3f085-134">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="3f085-135">Expression</span><span class="sxs-lookup"><span data-stu-id="3f085-135">Expression</span></span> | <span data-ttu-id="3f085-136">Výsledek</span><span class="sxs-lookup"><span data-stu-id="3f085-136">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="3f085-137">Spustí testy, jejichž `FullyQualifiedName` obsahuje `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="3f085-137">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="3f085-138">K `vstest 15.1+`dispozici v .</span><span class="sxs-lookup"><span data-stu-id="3f085-138">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="3f085-139">Spustí testy, `[Trait("Category", "CategoryA")]`které mají .</span><span class="sxs-lookup"><span data-stu-id="3f085-139">Runs tests which have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="3f085-140">**Použití podmíněných operátorů | A&amp;**</span><span class="sxs-lookup"><span data-stu-id="3f085-140">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="3f085-141">Expression</span><span class="sxs-lookup"><span data-stu-id="3f085-141">Expression</span></span> | <span data-ttu-id="3f085-142">Výsledek</span><span class="sxs-lookup"><span data-stu-id="3f085-142">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="3f085-143">Spustí testy, `TestClass1` `FullyQualifiedName` které `CategoryA`má v **nebo** `Category` je .</span><span class="sxs-lookup"><span data-stu-id="3f085-143">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="3f085-144">Spustí testy, `TestClass1` `FullyQualifiedName` které `CategoryA`má v **a** `Category` je .</span><span class="sxs-lookup"><span data-stu-id="3f085-144">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="3f085-145">Spustí testy, `FullyQualifiedName` které `TestClass1` **and** `Category` obsahují `CategoryA` a je **nebo** `Priority` je 1.</span><span class="sxs-lookup"><span data-stu-id="3f085-145">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="3f085-146">NJednotka</span><span class="sxs-lookup"><span data-stu-id="3f085-146">NUnit</span></span>

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

| <span data-ttu-id="3f085-147">Expression</span><span class="sxs-lookup"><span data-stu-id="3f085-147">Expression</span></span> | <span data-ttu-id="3f085-148">Výsledek</span><span class="sxs-lookup"><span data-stu-id="3f085-148">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="3f085-149">Spustí testy, jejichž `FullyQualifiedName` obsahuje `Method`.</span><span class="sxs-lookup"><span data-stu-id="3f085-149">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="3f085-150">K `vstest 15.1+`dispozici v .</span><span class="sxs-lookup"><span data-stu-id="3f085-150">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="3f085-151">Spustí testy, `TestMethod1`jejichž název obsahuje .</span><span class="sxs-lookup"><span data-stu-id="3f085-151">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="3f085-152">Spustí testy, které `NUnitNamespace.UnitTest1`jsou ve třídě .</span><span class="sxs-lookup"><span data-stu-id="3f085-152">Runs tests which are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="3f085-153">Spustí všechny `NUnitNamespace.UnitTest1.TestMethod1`testy s výjimkou .</span><span class="sxs-lookup"><span data-stu-id="3f085-153">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="3f085-154">Spustí testy, které jsou `[Category("CategoryA")]`anotovány s .</span><span class="sxs-lookup"><span data-stu-id="3f085-154">Runs tests which are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="3f085-155">Spustí testy, které jsou `[Priority(2)]`anotovány s .</span><span class="sxs-lookup"><span data-stu-id="3f085-155">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="3f085-156">**Použití podmíněných operátorů | A&amp;**</span><span class="sxs-lookup"><span data-stu-id="3f085-156">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="3f085-157">Expression</span><span class="sxs-lookup"><span data-stu-id="3f085-157">Expression</span></span> | <span data-ttu-id="3f085-158">Výsledek</span><span class="sxs-lookup"><span data-stu-id="3f085-158">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="3f085-159">Spustí testy, `UnitTest1` `FullyQualifiedName` které `CategoryA`mají v **nebo** `TestCategory` je .</span><span class="sxs-lookup"><span data-stu-id="3f085-159">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="3f085-160">Spustí testy, `UnitTest1` `FullyQualifiedName` které `CategoryA`mají v **.** `TestCategory`</span><span class="sxs-lookup"><span data-stu-id="3f085-160">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="3f085-161">Spustí testy, `FullyQualifiedName` které `UnitTest1` **and** `TestCategory` obsahují `CategoryA` a je **nebo** `Priority` je 1.</span><span class="sxs-lookup"><span data-stu-id="3f085-161">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |
