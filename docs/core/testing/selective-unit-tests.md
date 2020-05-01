---
title: Spouštění selektivních testů jednotek
description: Jak použít výraz filtru ke spuštění selektivních testů jednotek pomocí příkazu dotnet test v .NET Core.
author: smadala
ms.date: 04/29/2020
ms.openlocfilehash: e66455b5ac012114c45d998fae11da7ee769fbe2
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624914"
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="9bab0-103">Spouštění selektivních testů jednotek</span><span class="sxs-lookup"><span data-stu-id="9bab0-103">Running selective unit tests</span></span>

<span data-ttu-id="9bab0-104">Pomocí `dotnet test` příkazu v .NET Core můžete použít výraz filtru ke spuštění selektivních testů.</span><span class="sxs-lookup"><span data-stu-id="9bab0-104">With the `dotnet test` command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="9bab0-105">Tento článek ukazuje, jak filtrovat, který test se spouští.</span><span class="sxs-lookup"><span data-stu-id="9bab0-105">This article demonstrates how to filter which test are run.</span></span> <span data-ttu-id="9bab0-106">Následující příklady používají `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="9bab0-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="9bab0-107">Pokud používáte `vstest.console.exe`, nahraďte parametr `--filter` `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="9bab0-107">If you're using `vstest.console.exe`, replace `--filter` with `--testcasefilter:`.</span></span>

## <a name="character-escaping"></a><span data-ttu-id="9bab0-108">Znakové uvozovací znaky</span><span class="sxs-lookup"><span data-stu-id="9bab0-108">Character escaping</span></span>

<span data-ttu-id="9bab0-109">Použití filtrů, které zahrnují vykřičník (!) v `*nix` vyžaduje, aby `!` bylo vyhradit Uvozovací znak.</span><span class="sxs-lookup"><span data-stu-id="9bab0-109">Using filters that include exclamation mark (!) on `*nix` requires escaping since `!` is reserved.</span></span> <span data-ttu-id="9bab0-110">Například tento filtr přeskočí všechny testy, pokud obor názvů obsahuje IntegrationTests: `dotnet test --filter FullyQualifiedName\!~IntegrationTests`.</span><span class="sxs-lookup"><span data-stu-id="9bab0-110">For example, this filter skips all tests if the namespace contains IntegrationTests: `dotnet test --filter FullyQualifiedName\!~IntegrationTests`.</span></span>
<span data-ttu-id="9bab0-111">Všimněte si zpětného lomítka před vykřičníkem.</span><span class="sxs-lookup"><span data-stu-id="9bab0-111">Note the backslash that precedes the exclamation mark.</span></span>

<span data-ttu-id="9bab0-112">Pro `FullyQualifiedName` hodnoty, které obsahují čárku pro parametry obecného typu, oddělte čárku znakem `%2C`.</span><span class="sxs-lookup"><span data-stu-id="9bab0-112">For `FullyQualifiedName` values that include a comma for generic type parameters, escape the comma with `%2C`.</span></span> <span data-ttu-id="9bab0-113">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9bab0-113">For example:</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName=MyNamespace.MyTestsClass<ParameterType1%2CParameterType2>.MyTestMethod"
```

## <a name="mstest"></a><span data-ttu-id="9bab0-114">MSTest</span><span class="sxs-lookup"><span data-stu-id="9bab0-114">MSTest</span></span>

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

| <span data-ttu-id="9bab0-115">Expression</span><span class="sxs-lookup"><span data-stu-id="9bab0-115">Expression</span></span> | <span data-ttu-id="9bab0-116">Výsledek</span><span class="sxs-lookup"><span data-stu-id="9bab0-116">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="9bab0-117">Spustí testy, `FullyQualifiedName` jejichž `Method`obsahuje.</span><span class="sxs-lookup"><span data-stu-id="9bab0-117">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="9bab0-118">K dispozici v `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="9bab0-118">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="9bab0-119">Spustí testy, jejichž název `TestMethod1`obsahuje.</span><span class="sxs-lookup"><span data-stu-id="9bab0-119">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="9bab0-120">Spustí testy, které jsou ve `MSTestNamespace.UnitTest1`třídě.</span><span class="sxs-lookup"><span data-stu-id="9bab0-120">Runs tests which are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="9bab0-121">**Poznámka:** `ClassName` Hodnota by měla mít obor názvů, takže `ClassName=UnitTest1` nebude fungovat.</span><span class="sxs-lookup"><span data-stu-id="9bab0-121">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="9bab0-122">Spustí všechny testy s `MSTestNamespace.UnitTest1.TestMethod1`výjimkou.</span><span class="sxs-lookup"><span data-stu-id="9bab0-122">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="9bab0-123">Spustí testy, které jsou opatřeny `[TestCategory("CategoryA")]`poznámkami.</span><span class="sxs-lookup"><span data-stu-id="9bab0-123">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="9bab0-124">Spustí testy, které jsou opatřeny `[Priority(2)]`poznámkami.</span><span class="sxs-lookup"><span data-stu-id="9bab0-124">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="9bab0-125">**Použití podmíněných operátorů | ani&amp;**</span><span class="sxs-lookup"><span data-stu-id="9bab0-125">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="9bab0-126">Expression</span><span class="sxs-lookup"><span data-stu-id="9bab0-126">Expression</span></span> | <span data-ttu-id="9bab0-127">Výsledek</span><span class="sxs-lookup"><span data-stu-id="9bab0-127">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="9bab0-128">Spustí testy, které `UnitTest1` jsou `FullyQualifiedName` v **nebo** `TestCategory` `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="9bab0-128">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="9bab0-129">Spustí testy, které `UnitTest1` mají `FullyQualifiedName` v **a** `TestCategory` `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="9bab0-129">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="9bab0-130">`FullyQualifiedName` Spustí testy, které obsahují `UnitTest1` **a** `TestCategory` jsou `CategoryA` **nebo** `Priority` 1.</span><span class="sxs-lookup"><span data-stu-id="9bab0-130">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="9bab0-131">xUnit</span><span class="sxs-lookup"><span data-stu-id="9bab0-131">xUnit</span></span>

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

| <span data-ttu-id="9bab0-132">Expression</span><span class="sxs-lookup"><span data-stu-id="9bab0-132">Expression</span></span> | <span data-ttu-id="9bab0-133">Výsledek</span><span class="sxs-lookup"><span data-stu-id="9bab0-133">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="9bab0-134">Spustí pouze jeden test, `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="9bab0-134">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="9bab0-135">Spustí všechny testy s `XUnitNamespace.TestClass1.Test1`výjimkou.</span><span class="sxs-lookup"><span data-stu-id="9bab0-135">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="9bab0-136">Spustí testy, jejichž zobrazovaný název `TestClass1`obsahuje.</span><span class="sxs-lookup"><span data-stu-id="9bab0-136">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="9bab0-137">V příkladu kódu jsou definované vlastnosti s klíči `Category` a `Priority` lze je použít pro filtrování.</span><span class="sxs-lookup"><span data-stu-id="9bab0-137">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="9bab0-138">Expression</span><span class="sxs-lookup"><span data-stu-id="9bab0-138">Expression</span></span> | <span data-ttu-id="9bab0-139">Výsledek</span><span class="sxs-lookup"><span data-stu-id="9bab0-139">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="9bab0-140">Spustí testy, `FullyQualifiedName` jejichž `XUnit`obsahuje.</span><span class="sxs-lookup"><span data-stu-id="9bab0-140">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="9bab0-141">K dispozici v `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="9bab0-141">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="9bab0-142">Spustí testy, které `[Trait("Category", "CategoryA")]`mají.</span><span class="sxs-lookup"><span data-stu-id="9bab0-142">Runs tests which have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="9bab0-143">**Použití podmíněných operátorů | ani&amp;**</span><span class="sxs-lookup"><span data-stu-id="9bab0-143">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="9bab0-144">Expression</span><span class="sxs-lookup"><span data-stu-id="9bab0-144">Expression</span></span> | <span data-ttu-id="9bab0-145">Výsledek</span><span class="sxs-lookup"><span data-stu-id="9bab0-145">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="9bab0-146">Spustí testy, které `TestClass1` jsou `FullyQualifiedName` v **nebo** `Category` `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="9bab0-146">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="9bab0-147">Spustí testy, které `TestClass1` jsou `FullyQualifiedName` v **a** `Category` `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="9bab0-147">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="9bab0-148">`FullyQualifiedName` Spustí testy, které obsahují `TestClass1` **a** `Category` jsou `CategoryA` **nebo** `Priority` 1.</span><span class="sxs-lookup"><span data-stu-id="9bab0-148">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="9bab0-149">NUnit</span><span class="sxs-lookup"><span data-stu-id="9bab0-149">NUnit</span></span>

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

| <span data-ttu-id="9bab0-150">Expression</span><span class="sxs-lookup"><span data-stu-id="9bab0-150">Expression</span></span> | <span data-ttu-id="9bab0-151">Výsledek</span><span class="sxs-lookup"><span data-stu-id="9bab0-151">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="9bab0-152">Spustí testy, `FullyQualifiedName` jejichž `Method`obsahuje.</span><span class="sxs-lookup"><span data-stu-id="9bab0-152">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="9bab0-153">K dispozici v `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="9bab0-153">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="9bab0-154">Spustí testy, jejichž název `TestMethod1`obsahuje.</span><span class="sxs-lookup"><span data-stu-id="9bab0-154">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="9bab0-155">Spustí testy, které jsou ve `NUnitNamespace.UnitTest1`třídě.</span><span class="sxs-lookup"><span data-stu-id="9bab0-155">Runs tests which are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="9bab0-156">Spustí všechny testy s `NUnitNamespace.UnitTest1.TestMethod1`výjimkou.</span><span class="sxs-lookup"><span data-stu-id="9bab0-156">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="9bab0-157">Spustí testy, které jsou opatřeny `[Category("CategoryA")]`poznámkami.</span><span class="sxs-lookup"><span data-stu-id="9bab0-157">Runs tests which are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="9bab0-158">Spustí testy, které jsou opatřeny `[Priority(2)]`poznámkami.</span><span class="sxs-lookup"><span data-stu-id="9bab0-158">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="9bab0-159">**Použití podmíněných operátorů | ani&amp;**</span><span class="sxs-lookup"><span data-stu-id="9bab0-159">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="9bab0-160">Expression</span><span class="sxs-lookup"><span data-stu-id="9bab0-160">Expression</span></span> | <span data-ttu-id="9bab0-161">Výsledek</span><span class="sxs-lookup"><span data-stu-id="9bab0-161">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="9bab0-162">Spustí testy, které `UnitTest1` jsou `FullyQualifiedName` v **nebo** `TestCategory` `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="9bab0-162">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="9bab0-163">Spustí testy, které `UnitTest1` mají `FullyQualifiedName` v **a** `TestCategory` `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="9bab0-163">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="9bab0-164">`FullyQualifiedName` Spustí testy, které obsahují `UnitTest1` **a** `TestCategory` jsou `CategoryA` **nebo** `Priority` 1.</span><span class="sxs-lookup"><span data-stu-id="9bab0-164">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

<span data-ttu-id="9bab0-165">Další informace najdete v tématu [testovací případ Filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span><span class="sxs-lookup"><span data-stu-id="9bab0-165">For more information, see [TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span></span>
