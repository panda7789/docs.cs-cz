---
title: Spouštění selektivních testů jednotek
description: Jak použít výraz filtru ke spuštění selektivních testů jednotek pomocí příkazu dotnet test v .NET Core.
author: smadala
ms.date: 05/18/2020
zone_pivot_groups: unit-testing-framework-set-one
ms.openlocfilehash: 6a6bbb0687742d1e3288d64fb88f6825dc678e28
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702991"
---
# <a name="run-selective-unit-tests"></a><span data-ttu-id="6ea93-103">Spouštění selektivních testů jednotek</span><span class="sxs-lookup"><span data-stu-id="6ea93-103">Run selective unit tests</span></span>

<span data-ttu-id="6ea93-104">Pomocí [`dotnet test`](../tools/dotnet-test.md) příkazu v .NET Core můžete použít výraz filtru ke spuštění selektivních testů.</span><span class="sxs-lookup"><span data-stu-id="6ea93-104">With the [`dotnet test`](../tools/dotnet-test.md) command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="6ea93-105">Tento článek ukazuje, jak filtrovat, které testy jsou spuštěny.</span><span class="sxs-lookup"><span data-stu-id="6ea93-105">This article demonstrates how to filter which tests are run.</span></span> <span data-ttu-id="6ea93-106">Následující příklady používají `dotnet test` .</span><span class="sxs-lookup"><span data-stu-id="6ea93-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="6ea93-107">Pokud používáte `vstest.console.exe` , nahraďte parametr `--filter` `--testcasefilter:` .</span><span class="sxs-lookup"><span data-stu-id="6ea93-107">If you're using `vstest.console.exe`, replace `--filter` with `--testcasefilter:`.</span></span>

## <a name="character-escaping"></a><span data-ttu-id="6ea93-108">Znakové uvozovací znaky</span><span class="sxs-lookup"><span data-stu-id="6ea93-108">Character escaping</span></span>

<span data-ttu-id="6ea93-109">Použití filtrů, které zahrnují vykřičník `!` on, `*nix` vyžaduje Uvozovací znak, protože `!` je vyhrazený.</span><span class="sxs-lookup"><span data-stu-id="6ea93-109">Using filters that include exclamation mark `!` on `*nix` requires escaping since `!` is reserved.</span></span> <span data-ttu-id="6ea93-110">Například tento filtr přeskočí všechny testy, pokud obor názvů obsahuje IntegrationTests:</span><span class="sxs-lookup"><span data-stu-id="6ea93-110">For example, this filter skips all tests if the namespace contains IntegrationTests:</span></span>

```dotnetcli
dotnet test --filter FullyQualifiedName\!~IntegrationTests
```

> [!IMPORTANT]
> <span data-ttu-id="6ea93-111">Zpětné lomítko předchází vykřičníku, která označuje, že se jedná o řídicí znak `\!` .</span><span class="sxs-lookup"><span data-stu-id="6ea93-111">The backslash precedes the exclamation mark to indicate it is an escaped character `\!`.</span></span>

<span data-ttu-id="6ea93-112">Pro `FullyQualifiedName` hodnoty, které obsahují čárku pro parametry obecného typu, oddělte čárku znakem `%2C` .</span><span class="sxs-lookup"><span data-stu-id="6ea93-112">For `FullyQualifiedName` values that include a comma for generic type parameters, escape the comma with `%2C`.</span></span> <span data-ttu-id="6ea93-113">Například:</span><span class="sxs-lookup"><span data-stu-id="6ea93-113">For example:</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName=MyNamespace.MyTestsClass<ParameterType1%2CParameterType2>.MyTestMethod"
```

:::zone pivot="mstest"

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace MSTestNamespace
{
    [TestClass]
    public class UnitTest1
    {
        [TestMethod, Priority(1), TestCategory("CategoryA")]
        public void TestMethod1()
        {
        }

        [TestMethod, Priority(2)]
        public void TestMethod2()
        {
        }
    }
}
```

| <span data-ttu-id="6ea93-114">Výraz</span><span class="sxs-lookup"><span data-stu-id="6ea93-114">Expression</span></span> | <span data-ttu-id="6ea93-115">Výsledek</span><span class="sxs-lookup"><span data-stu-id="6ea93-115">Result</span></span> |
|--|--|
| `dotnet test --filter Method` | <span data-ttu-id="6ea93-116">Spustí testy <xref:System.Reflection.Module.FullyQualifiedName> , jejichž obsahuje `Method` .</span><span class="sxs-lookup"><span data-stu-id="6ea93-116">Runs tests whose <xref:System.Reflection.Module.FullyQualifiedName> contains `Method`.</span></span> <span data-ttu-id="6ea93-117">K dispozici v `vstest 15.1+` .</span><span class="sxs-lookup"><span data-stu-id="6ea93-117">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="6ea93-118">Spustí testy, jejichž název obsahuje `TestMethod1` .</span><span class="sxs-lookup"><span data-stu-id="6ea93-118">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="6ea93-119">Spustí testy, které jsou ve třídě `MSTestNamespace.UnitTest1` .</span><span class="sxs-lookup"><span data-stu-id="6ea93-119">Runs tests that are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="6ea93-120">**Poznámka:** `ClassName`Hodnota by měla mít obor názvů, takže `ClassName=UnitTest1` nebude fungovat.</span><span class="sxs-lookup"><span data-stu-id="6ea93-120">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="6ea93-121">Spustí všechny testy s výjimkou `MSTestNamespace.UnitTest1.TestMethod1` .</span><span class="sxs-lookup"><span data-stu-id="6ea93-121">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="6ea93-122">Spustí testy, které jsou opatřeny poznámkami `[TestCategory("CategoryA")]` .</span><span class="sxs-lookup"><span data-stu-id="6ea93-122">Runs tests that are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="6ea93-123">Spustí testy, které jsou opatřeny poznámkami `[Priority(2)]` .</span><span class="sxs-lookup"><span data-stu-id="6ea93-123">Runs tests that are annotated with `[Priority(2)]`.</span></span> |

<span data-ttu-id="6ea93-124">Příklady použití podmíněných operátorů `|` a `&` :</span><span class="sxs-lookup"><span data-stu-id="6ea93-124">Examples using the conditional operators `|` and `&`:</span></span>

<span data-ttu-id="6ea93-125">Ke spuštění testů, které mají `UnitTest1` v <xref:System.Reflection.Module.FullyQualifiedName> **nebo** <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> jsou `"CategoryA"` .</span><span class="sxs-lookup"><span data-stu-id="6ea93-125">To run tests that have `UnitTest1` in their <xref:System.Reflection.Module.FullyQualifiedName> **or** <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> is `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1|TestCategory=CategoryA"
```

<span data-ttu-id="6ea93-126">Chcete-li spustit testy, které mají `UnitTest1` své <xref:System.Reflection.Module.FullyQualifiedName> **a** mají <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> `"CategoryA"` .</span><span class="sxs-lookup"><span data-stu-id="6ea93-126">To run tests that have `UnitTest1` in their <xref:System.Reflection.Module.FullyQualifiedName> **and** have a <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"
```

<span data-ttu-id="6ea93-127">Pro spuštění testů, které obsahují <xref:System.Reflection.Module.FullyQualifiedName> `UnitTest1` **a** mají <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> `"CategoryA"` **nebo** mají <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute> prioritu `1` .</span><span class="sxs-lookup"><span data-stu-id="6ea93-127">To run tests that have either <xref:System.Reflection.Module.FullyQualifiedName> containing `UnitTest1` **and** have a <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> of `"CategoryA"` **or** have a <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute> with a priority of `1`.</span></span>

```dotnetcli
dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)|Priority=1"
```

:::zone-end
:::zone pivot="xunit"

```csharp
using Xunit;

namespace XUnitNamespace
{
    public class TestClass1
    {
        [Fact, Trait("Priority", "1"), Trait("Category", "CategoryA")]
        public void Test1()
        {
        }

        [Fact, Trait("Priority", "2")]
        public void Test2()
        {
        }
    }
}
```

| <span data-ttu-id="6ea93-128">Výraz</span><span class="sxs-lookup"><span data-stu-id="6ea93-128">Expression</span></span> | <span data-ttu-id="6ea93-129">Výsledek</span><span class="sxs-lookup"><span data-stu-id="6ea93-129">Result</span></span> |
|--|--|
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="6ea93-130">Spustí pouze jeden test, `XUnitNamespace.TestClass1.Test1` .</span><span class="sxs-lookup"><span data-stu-id="6ea93-130">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="6ea93-131">Spustí všechny testy s výjimkou `XUnitNamespace.TestClass1.Test1` .</span><span class="sxs-lookup"><span data-stu-id="6ea93-131">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="6ea93-132">Spustí testy, jejichž zobrazovaný název obsahuje `TestClass1` .</span><span class="sxs-lookup"><span data-stu-id="6ea93-132">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="6ea93-133">V příkladu kódu jsou definované vlastnosti s klíči `"Category"` a `"Priority"` lze je použít pro filtrování.</span><span class="sxs-lookup"><span data-stu-id="6ea93-133">In the code example, the defined traits with keys `"Category"` and `"Priority"` can be used for filtering.</span></span>

| <span data-ttu-id="6ea93-134">Výraz</span><span class="sxs-lookup"><span data-stu-id="6ea93-134">Expression</span></span> | <span data-ttu-id="6ea93-135">Výsledek</span><span class="sxs-lookup"><span data-stu-id="6ea93-135">Result</span></span> |
|--|--|
| `dotnet test --filter XUnit` | <span data-ttu-id="6ea93-136">Spustí testy <xref:System.Reflection.Module.FullyQualifiedName> , jejichž obsahuje `XUnit` .</span><span class="sxs-lookup"><span data-stu-id="6ea93-136">Runs tests whose <xref:System.Reflection.Module.FullyQualifiedName> contains `XUnit`.</span></span>  <span data-ttu-id="6ea93-137">K dispozici v `vstest 15.1+` .</span><span class="sxs-lookup"><span data-stu-id="6ea93-137">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="6ea93-138">Spustí testy, které mají `[Trait("Category", "CategoryA")]` .</span><span class="sxs-lookup"><span data-stu-id="6ea93-138">Runs tests that have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="6ea93-139">Příklady použití podmíněných operátorů `|` a `&` :</span><span class="sxs-lookup"><span data-stu-id="6ea93-139">Examples using the conditional operators `|` and `&`:</span></span>

<span data-ttu-id="6ea93-140">Chcete-li spustit testy, které mají `TestClass1` <xref:System.Reflection.Module.FullyQualifiedName> **nebo** mají `Trait` klíč `"Category"` a hodnotu `"CategoryA"` .</span><span class="sxs-lookup"><span data-stu-id="6ea93-140">To run tests that have `TestClass1` in their <xref:System.Reflection.Module.FullyQualifiedName> **or** have a `Trait` with a key of `"Category"` and value of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~TestClass1|Category=CategoryA"
```

<span data-ttu-id="6ea93-141">Chcete-li spustit testy, které mají `TestClass1` své <xref:System.Reflection.Module.FullyQualifiedName> **a** mají `Trait` klíč `"Category"` a hodnotu `"CategoryA"` .</span><span class="sxs-lookup"><span data-stu-id="6ea93-141">To run tests that have `TestClass1` in their <xref:System.Reflection.Module.FullyQualifiedName> **and** have a `Trait` with a key of `"Category"` and value of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"
```

<span data-ttu-id="6ea93-142">Chcete-li spustit testy, které <xref:System.Reflection.Module.FullyQualifiedName> obsahují `TestClass1` **a** mají `Trait` klíč `"Category"` a hodnotu, `"CategoryA"` **nebo** musí mít `Trait` klíč `"Priority"` a hodnotu `1` .</span><span class="sxs-lookup"><span data-stu-id="6ea93-142">To run tests that have either <xref:System.Reflection.Module.FullyQualifiedName> containing `TestClass1` **and** have a `Trait` with a key of `"Category"` and value of `"CategoryA"` **or** have a `Trait` with a key of `"Priority"` and value of `1`.</span></span>

```dotnetcli
dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)|Priority=1"
```

:::zone-end
:::zone pivot="nunit"

```csharp
using NUnit.Framework;

namespace NUnitNamespace
{
    public class UnitTest1
    {
        [Test, Property("Priority", 1), Category("CategoryA")]
        public void TestMethod1()
        {
        }

        [Test, Property("Priority", 2)]
        public void TestMethod2()
        {
        }
    }
}
```

| <span data-ttu-id="6ea93-143">Výraz</span><span class="sxs-lookup"><span data-stu-id="6ea93-143">Expression</span></span> | <span data-ttu-id="6ea93-144">Výsledek</span><span class="sxs-lookup"><span data-stu-id="6ea93-144">Result</span></span> |
|--|--|
| `dotnet test --filter Method` | <span data-ttu-id="6ea93-145">Spustí testy <xref:System.Reflection.Module.FullyQualifiedName> , jejichž obsahuje `Method` .</span><span class="sxs-lookup"><span data-stu-id="6ea93-145">Runs tests whose <xref:System.Reflection.Module.FullyQualifiedName> contains `Method`.</span></span> <span data-ttu-id="6ea93-146">K dispozici v `vstest 15.1+` .</span><span class="sxs-lookup"><span data-stu-id="6ea93-146">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="6ea93-147">Spustí testy, jejichž název obsahuje `TestMethod1` .</span><span class="sxs-lookup"><span data-stu-id="6ea93-147">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="6ea93-148">Spustí testy, které jsou ve třídě `NUnitNamespace.UnitTest1` .</span><span class="sxs-lookup"><span data-stu-id="6ea93-148">Runs tests that are in class `NUnitNamespace.UnitTest1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="6ea93-149">Spustí všechny testy s výjimkou `NUnitNamespace.UnitTest1.TestMethod1` .</span><span class="sxs-lookup"><span data-stu-id="6ea93-149">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="6ea93-150">Spustí testy, které jsou opatřeny poznámkami `[Category("CategoryA")]` .</span><span class="sxs-lookup"><span data-stu-id="6ea93-150">Runs tests that are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="6ea93-151">Spustí testy, které jsou opatřeny poznámkami `[Priority(2)]` .</span><span class="sxs-lookup"><span data-stu-id="6ea93-151">Runs tests that are annotated with `[Priority(2)]`.</span></span> |

<span data-ttu-id="6ea93-152">Příklady použití podmíněných operátorů `|` a `&` :</span><span class="sxs-lookup"><span data-stu-id="6ea93-152">Examples using the conditional operators `|` and `&`:</span></span>

<span data-ttu-id="6ea93-153">Chcete-li spustit testy, které mají `UnitTest1` <xref:System.Reflection.Module.FullyQualifiedName> **nebo** mají `Category` `"CategoryA"` .</span><span class="sxs-lookup"><span data-stu-id="6ea93-153">To run tests that have `UnitTest1` in their <xref:System.Reflection.Module.FullyQualifiedName> **or** have a `Category` of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1|TestCategory=CategoryA"
```

<span data-ttu-id="6ea93-154">Chcete-li spustit testy, které mají `UnitTest1` své <xref:System.Reflection.Module.FullyQualifiedName> **a** mají `Category` `"CategoryA"` .</span><span class="sxs-lookup"><span data-stu-id="6ea93-154">To run tests that have `UnitTest1` in their <xref:System.Reflection.Module.FullyQualifiedName> **and** have a `Category` of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"
```

<span data-ttu-id="6ea93-155">Chcete-li spustit testy, které mají, <xref:System.Reflection.Module.FullyQualifiedName> obsahující `UnitTest1` **a** mají `Category` nebo, `"CategoryA"` **nebo** musí mít a `Property` `"Priority"` `1` .</span><span class="sxs-lookup"><span data-stu-id="6ea93-155">To run tests that have either a <xref:System.Reflection.Module.FullyQualifiedName> containing `UnitTest1` **and** have a `Category` of `"CategoryA"` **or** have a `Property` with a `"Priority"` of `1`.</span></span>

```dotnetcli
dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)|Priority=1"
```

<span data-ttu-id="6ea93-156">Další informace najdete v tématu [testovací případ Filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span><span class="sxs-lookup"><span data-stu-id="6ea93-156">For more information, see [TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span></span>

:::zone-end

## <a name="see-also"></a><span data-ttu-id="6ea93-157">Viz také</span><span class="sxs-lookup"><span data-stu-id="6ea93-157">See also</span></span>

- [<span data-ttu-id="6ea93-158">dotnet test</span><span class="sxs-lookup"><span data-stu-id="6ea93-158">dotnet test</span></span>](../tools/dotnet-test.md)
- [<span data-ttu-id="6ea93-159">dotnet – test – filtr</span><span class="sxs-lookup"><span data-stu-id="6ea93-159">dotnet test --filter</span></span>](../tools/dotnet-test.md#filter-option-details)

## <a name="next-steps"></a><span data-ttu-id="6ea93-160">Další kroky</span><span class="sxs-lookup"><span data-stu-id="6ea93-160">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6ea93-161">Pořadí testů jednotek</span><span class="sxs-lookup"><span data-stu-id="6ea93-161">Order unit tests</span></span>](order-unit-tests.md)
