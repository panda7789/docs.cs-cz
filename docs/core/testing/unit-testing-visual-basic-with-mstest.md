---
title: Unit testing Visual Basic in .NET Core with dotnet test and MSTest
description: Learn unit test concepts in .NET Core through an interactive experience building a sample Visual Basic solution step-by-step using MSTest.
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
ms.custom: seodec18
ms.openlocfilehash: c52fc7393718f6af44bd85dd23353f3e32f29f79
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428729"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-mstest"></a><span data-ttu-id="53e1b-103">Unit testing Visual Basic .NET Core libraries using dotnet test and MSTest</span><span class="sxs-lookup"><span data-stu-id="53e1b-103">Unit testing Visual Basic .NET Core libraries using dotnet test and MSTest</span></span>

<span data-ttu-id="53e1b-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span><span class="sxs-lookup"><span data-stu-id="53e1b-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="53e1b-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-mstest/) before you begin.</span><span class="sxs-lookup"><span data-stu-id="53e1b-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-mstest/) before you begin.</span></span> <span data-ttu-id="53e1b-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="53e1b-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a><span data-ttu-id="53e1b-107">Creating the source project</span><span class="sxs-lookup"><span data-stu-id="53e1b-107">Creating the source project</span></span>

<span data-ttu-id="53e1b-108">Open a shell window.</span><span class="sxs-lookup"><span data-stu-id="53e1b-108">Open a shell window.</span></span> <span data-ttu-id="53e1b-109">Create a directory called *unit-testing-vb-mstest* to hold the solution.</span><span class="sxs-lookup"><span data-stu-id="53e1b-109">Create a directory called *unit-testing-vb-mstest* to hold the solution.</span></span>
<span data-ttu-id="53e1b-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span><span class="sxs-lookup"><span data-stu-id="53e1b-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="53e1b-111">This practice makes it easier to manage both the class library and the unit test project.</span><span class="sxs-lookup"><span data-stu-id="53e1b-111">This practice makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="53e1b-112">Inside the solution directory, create a *PrimeService* directory.</span><span class="sxs-lookup"><span data-stu-id="53e1b-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="53e1b-113">You have the following directory and file structure thus far:</span><span class="sxs-lookup"><span data-stu-id="53e1b-113">You have the following directory and file structure thus far:</span></span>

```console
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
```

<span data-ttu-id="53e1b-114">Make *PrimeService* the current directory and run [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) to create the source project.</span><span class="sxs-lookup"><span data-stu-id="53e1b-114">Make *PrimeService* the current directory and run [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="53e1b-115">Rename *Class1.VB* to *PrimeService.VB*.</span><span class="sxs-lookup"><span data-stu-id="53e1b-115">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="53e1b-116">You create a failing implementation of the `PrimeService` class:</span><span class="sxs-lookup"><span data-stu-id="53e1b-116">You create a failing implementation of the `PrimeService` class:</span></span>

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="53e1b-117">Change the directory back to the *unit-testing-vb-using-mstest* directory.</span><span class="sxs-lookup"><span data-stu-id="53e1b-117">Change the directory back to the *unit-testing-vb-using-mstest* directory.</span></span> <span data-ttu-id="53e1b-118">Run [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span><span class="sxs-lookup"><span data-stu-id="53e1b-118">Run [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="53e1b-119">Creating the test project</span><span class="sxs-lookup"><span data-stu-id="53e1b-119">Creating the test project</span></span>

<span data-ttu-id="53e1b-120">Next, create the *PrimeService.Tests* directory.</span><span class="sxs-lookup"><span data-stu-id="53e1b-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="53e1b-121">The following outline shows the directory structure:</span><span class="sxs-lookup"><span data-stu-id="53e1b-121">The following outline shows the directory structure:</span></span>

```console
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="53e1b-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest -lang VB`](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="53e1b-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest -lang VB`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="53e1b-123">This command creates a test project that uses MSTest as the test library.</span><span class="sxs-lookup"><span data-stu-id="53e1b-123">This command creates a test project that uses MSTest as the test library.</span></span> <span data-ttu-id="53e1b-124">The generated template configures the test runner in the *PrimeServiceTests.vbproj*:</span><span class="sxs-lookup"><span data-stu-id="53e1b-124">The generated template configures the test runner in the *PrimeServiceTests.vbproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="53e1b-125">The test project requires other packages to create and run unit tests.</span><span class="sxs-lookup"><span data-stu-id="53e1b-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="53e1b-126">`dotnet new` in the previous step added MSTest and the MSTest runner.</span><span class="sxs-lookup"><span data-stu-id="53e1b-126">`dotnet new` in the previous step added MSTest and the MSTest runner.</span></span> <span data-ttu-id="53e1b-127">Now, add the `PrimeService` class library as another dependency to the project.</span><span class="sxs-lookup"><span data-stu-id="53e1b-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="53e1b-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span><span class="sxs-lookup"><span data-stu-id="53e1b-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="53e1b-129">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span><span class="sxs-lookup"><span data-stu-id="53e1b-129">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="53e1b-130">You have the following final solution layout:</span><span class="sxs-lookup"><span data-stu-id="53e1b-130">You have the following final solution layout:</span></span>

```console
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

<span data-ttu-id="53e1b-131">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) in the *unit-testing-vb-mstest* directory.</span><span class="sxs-lookup"><span data-stu-id="53e1b-131">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) in the *unit-testing-vb-mstest* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="53e1b-132">Creating the first test</span><span class="sxs-lookup"><span data-stu-id="53e1b-132">Creating the first test</span></span>

<span data-ttu-id="53e1b-133">You write one failing test, make it pass, then repeat the process.</span><span class="sxs-lookup"><span data-stu-id="53e1b-133">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="53e1b-134">Remove *UnitTest1.vb* from the *PrimeService.Tests* directory and create a new Visual Basic file named *PrimeService_IsPrimeShould.VB*.</span><span class="sxs-lookup"><span data-stu-id="53e1b-134">Remove *UnitTest1.vb* from the *PrimeService.Tests* directory and create a new Visual Basic file named *PrimeService_IsPrimeShould.VB*.</span></span> <span data-ttu-id="53e1b-135">Add the following code:</span><span class="sxs-lookup"><span data-stu-id="53e1b-135">Add the following code:</span></span>

```vb
Imports Microsoft.VisualStudio.TestTools.UnitTesting

Namespace PrimeService.Tests
    <TestClass>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <TestMethod>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.IsFalse(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="53e1b-136">The `<TestClass>` attribute indicates a class that contains tests.</span><span class="sxs-lookup"><span data-stu-id="53e1b-136">The `<TestClass>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="53e1b-137">The `<TestMethod>` attribute denotes a method that is run by the test runner.</span><span class="sxs-lookup"><span data-stu-id="53e1b-137">The `<TestMethod>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="53e1b-138">From the *unit-testing-vb-mstest*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span><span class="sxs-lookup"><span data-stu-id="53e1b-138">From the *unit-testing-vb-mstest*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="53e1b-139">The MSTest test runner contains the program entry point to run your tests.</span><span class="sxs-lookup"><span data-stu-id="53e1b-139">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="53e1b-140">`dotnet test` starts the test runner using the unit test project you've created.</span><span class="sxs-lookup"><span data-stu-id="53e1b-140">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="53e1b-141">Your test fails.</span><span class="sxs-lookup"><span data-stu-id="53e1b-141">Your test fails.</span></span> <span data-ttu-id="53e1b-142">You haven't created the implementation yet.</span><span class="sxs-lookup"><span data-stu-id="53e1b-142">You haven't created the implementation yet.</span></span> <span data-ttu-id="53e1b-143">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span><span class="sxs-lookup"><span data-stu-id="53e1b-143">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

<span data-ttu-id="53e1b-144">In the *unit-testing-vb-mstest* directory, run `dotnet test` again.</span><span class="sxs-lookup"><span data-stu-id="53e1b-144">In the *unit-testing-vb-mstest* directory, run `dotnet test` again.</span></span> <span data-ttu-id="53e1b-145">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span><span class="sxs-lookup"><span data-stu-id="53e1b-145">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="53e1b-146">After building both projects, it runs this single test.</span><span class="sxs-lookup"><span data-stu-id="53e1b-146">After building both projects, it runs this single test.</span></span> <span data-ttu-id="53e1b-147">It passes.</span><span class="sxs-lookup"><span data-stu-id="53e1b-147">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="53e1b-148">Adding more features</span><span class="sxs-lookup"><span data-stu-id="53e1b-148">Adding more features</span></span>

<span data-ttu-id="53e1b-149">Now that you've made one test pass, it's time to write more.</span><span class="sxs-lookup"><span data-stu-id="53e1b-149">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="53e1b-150">There are a few other simple cases for prime numbers: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="53e1b-150">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="53e1b-151">You could add those cases as new tests with the `<TestMethod>` attribute, but that quickly becomes tedious.</span><span class="sxs-lookup"><span data-stu-id="53e1b-151">You could add those cases as new tests with the `<TestMethod>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="53e1b-152">There are other MSTest attributes that enable you to write a suite of similar tests.</span><span class="sxs-lookup"><span data-stu-id="53e1b-152">There are other MSTest attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="53e1b-153">A `<DataTestMethod>` attribute represents a suite of tests that execute the same code but have different input arguments.</span><span class="sxs-lookup"><span data-stu-id="53e1b-153">A `<DataTestMethod>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="53e1b-154">You can use the `<DataRow>` attribute to specify values for those inputs.</span><span class="sxs-lookup"><span data-stu-id="53e1b-154">You can use the `<DataRow>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="53e1b-155">Instead of creating new tests, apply these two attributes to create a single theory.</span><span class="sxs-lookup"><span data-stu-id="53e1b-155">Instead of creating new tests, apply these two attributes to create a single theory.</span></span> <span data-ttu-id="53e1b-156">The theory is a method that tests several values less than two, which is the lowest prime number:</span><span class="sxs-lookup"><span data-stu-id="53e1b-156">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="53e1b-157">Run `dotnet test`, and two of these tests fail.</span><span class="sxs-lookup"><span data-stu-id="53e1b-157">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="53e1b-158">To make all of the tests pass, change the `if` clause at the beginning of the method:</span><span class="sxs-lookup"><span data-stu-id="53e1b-158">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="53e1b-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span><span class="sxs-lookup"><span data-stu-id="53e1b-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="53e1b-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="53e1b-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="53e1b-161">You've built a small library and a set of unit tests for that library.</span><span class="sxs-lookup"><span data-stu-id="53e1b-161">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="53e1b-162">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span><span class="sxs-lookup"><span data-stu-id="53e1b-162">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="53e1b-163">You've concentrated most of your time and effort on solving the goals of the application.</span><span class="sxs-lookup"><span data-stu-id="53e1b-163">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
