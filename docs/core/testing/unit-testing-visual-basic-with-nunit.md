---
title: Unit testing Visual Basic in .NET Core with dotnet test and NUnit
description: Learn unit test concepts in .NET Core through an interactive experience building a sample Visual Basic solution step-by-step using NUnit.
author: rprouse
ms.date: 10/04/2018
ms.custom: seodec18
ms.openlocfilehash: 4776916c316e18de954c8ccaa985075dc2ea0fc5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428720"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-nunit"></a><span data-ttu-id="f0f6e-103">Unit testing Visual Basic .NET Core libraries using dotnet test and NUnit</span><span class="sxs-lookup"><span data-stu-id="f0f6e-103">Unit testing Visual Basic .NET Core libraries using dotnet test and NUnit</span></span>

<span data-ttu-id="f0f6e-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="f0f6e-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) before you begin.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) before you begin.</span></span> <span data-ttu-id="f0f6e-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="f0f6e-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a><span data-ttu-id="f0f6e-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f0f6e-107">Prerequisites</span></span>

- <span data-ttu-id="f0f6e-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="f0f6e-109">A text editor or code editor of your choice.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="f0f6e-110">Creating the source project</span><span class="sxs-lookup"><span data-stu-id="f0f6e-110">Creating the source project</span></span>

<span data-ttu-id="f0f6e-111">Open a shell window.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-111">Open a shell window.</span></span> <span data-ttu-id="f0f6e-112">Create a directory called *unit-testing-vb-nunit* to hold the solution.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-112">Create a directory called *unit-testing-vb-nunit* to hold the solution.</span></span> <span data-ttu-id="f0f6e-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span><span class="sxs-lookup"><span data-stu-id="f0f6e-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```dotnetcli
dotnet new sln
```

<span data-ttu-id="f0f6e-114">Next, create a *PrimeService* directory.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-114">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="f0f6e-115">The following outline shows the file structure so far:</span><span class="sxs-lookup"><span data-stu-id="f0f6e-115">The following outline shows the file structure so far:</span></span>

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
```

<span data-ttu-id="f0f6e-116">Make *PrimeService* the current directory and run the following command to create the source project:</span><span class="sxs-lookup"><span data-stu-id="f0f6e-116">Make *PrimeService* the current directory and run the following command to create the source project:</span></span>

```dotnetcli
dotnet new classlib -lang VB
```

<span data-ttu-id="f0f6e-117">Rename *Class1.VB* to *PrimeService.VB*.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-117">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="f0f6e-118">You create a failing implementation of the `PrimeService` class:</span><span class="sxs-lookup"><span data-stu-id="f0f6e-118">You create a failing implementation of the `PrimeService` class:</span></span>

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first.")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="f0f6e-119">Change the directory back to the *unit-testing-vb-using-mstest* directory.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-119">Change the directory back to the *unit-testing-vb-using-mstest* directory.</span></span> <span data-ttu-id="f0f6e-120">Run the following command to add the class library project to the solution:</span><span class="sxs-lookup"><span data-stu-id="f0f6e-120">Run the following command to add the class library project to the solution:</span></span>

```dotnetcli
dotnet sln add .\PrimeService\PrimeService.vbproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="f0f6e-121">Creating the test project</span><span class="sxs-lookup"><span data-stu-id="f0f6e-121">Creating the test project</span></span>

<span data-ttu-id="f0f6e-122">Next, create the *PrimeService.Tests* directory.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-122">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="f0f6e-123">The following outline shows the directory structure:</span><span class="sxs-lookup"><span data-stu-id="f0f6e-123">The following outline shows the directory structure:</span></span>

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="f0f6e-124">Make the *PrimeService.Tests* directory the current directory and create a new project using the following command:</span><span class="sxs-lookup"><span data-stu-id="f0f6e-124">Make the *PrimeService.Tests* directory the current directory and create a new project using the following command:</span></span>

```dotnetcli
dotnet new nunit -lang VB
```

<span data-ttu-id="f0f6e-125">The [dotnet new](../tools/dotnet-new.md) command creates a test project that uses NUnit as the test library.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-125">The [dotnet new](../tools/dotnet-new.md) command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="f0f6e-126">The generated template configures the test runner in the *PrimeServiceTests.vbproj* file:</span><span class="sxs-lookup"><span data-stu-id="f0f6e-126">The generated template configures the test runner in the *PrimeServiceTests.vbproj* file:</span></span>

[!code-xml[Packages](~/samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj#Packages)]

<span data-ttu-id="f0f6e-127">The test project requires other packages to create and run unit tests.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-127">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="f0f6e-128">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-128">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="f0f6e-129">Now, add the `PrimeService` class library as another dependency to the project.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-129">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="f0f6e-130">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span><span class="sxs-lookup"><span data-stu-id="f0f6e-130">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="f0f6e-131">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-131">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="f0f6e-132">You have the following final solution layout:</span><span class="sxs-lookup"><span data-stu-id="f0f6e-132">You have the following final solution layout:</span></span>

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.vbproj
```

<span data-ttu-id="f0f6e-133">Execute the following command in the *unit-testing-vb-nunit* directory:</span><span class="sxs-lookup"><span data-stu-id="f0f6e-133">Execute the following command in the *unit-testing-vb-nunit* directory:</span></span>

```dotnetcli
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="f0f6e-134">Creating the first test</span><span class="sxs-lookup"><span data-stu-id="f0f6e-134">Creating the first test</span></span>

<span data-ttu-id="f0f6e-135">You write one failing test, make it pass, then repeat the process.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-135">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="f0f6e-136">In the *PrimeService.Tests* directory, rename the *UnitTest1.vb* file to *PrimeService_IsPrimeShould.VB* and replace its entire contents with the following code:</span><span class="sxs-lookup"><span data-stu-id="f0f6e-136">In the *PrimeService.Tests* directory, rename the *UnitTest1.vb* file to *PrimeService_IsPrimeShould.VB* and replace its entire contents with the following code:</span></span>

```vb
Imports NUnit.Framework

Namespace PrimeService.Tests
    <TestFixture>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Test>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="f0f6e-137">The `<TestFixture>` attribute indicates a class that contains tests.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-137">The `<TestFixture>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="f0f6e-138">The `<Test>` attribute denotes a method that is run by the test runner.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-138">The `<Test>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="f0f6e-139">From the *unit-testing-vb-nunit*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-139">From the *unit-testing-vb-nunit*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="f0f6e-140">The NUnit test runner contains the program entry point to run your tests.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-140">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="f0f6e-141">`dotnet test` starts the test runner using the unit test project you've created.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-141">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="f0f6e-142">Your test fails.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-142">Your test fails.</span></span> <span data-ttu-id="f0f6e-143">You haven't created the implementation yet.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-143">You haven't created the implementation yet.</span></span> <span data-ttu-id="f0f6e-144">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span><span class="sxs-lookup"><span data-stu-id="f0f6e-144">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

<span data-ttu-id="f0f6e-145">In the *unit-testing-vb-nunit* directory, run `dotnet test` again.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-145">In the *unit-testing-vb-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="f0f6e-146">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-146">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="f0f6e-147">After building both projects, it runs this single test.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-147">After building both projects, it runs this single test.</span></span> <span data-ttu-id="f0f6e-148">It passes.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-148">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="f0f6e-149">Adding more features</span><span class="sxs-lookup"><span data-stu-id="f0f6e-149">Adding more features</span></span>

<span data-ttu-id="f0f6e-150">Now that you've made one test pass, it's time to write more.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-150">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="f0f6e-151">There are a few other simple cases for prime numbers: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-151">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="f0f6e-152">You could add those cases as new tests with the `<Test>` attribute, but that quickly becomes tedious.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-152">You could add those cases as new tests with the `<Test>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="f0f6e-153">There are other xUnit attributes that enable you to write a suite of similar tests.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-153">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="f0f6e-154">A `<TestCase>` attribute represents a suite of tests that execute the same code but have different input arguments.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-154">A `<TestCase>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="f0f6e-155">You can use the `<TestCase>` attribute to specify values for those inputs.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-155">You can use the `<TestCase>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="f0f6e-156">Instead of creating new tests, apply these two attributes to create a series of tests that test several values less than two, which is the lowest prime number:</span><span class="sxs-lookup"><span data-stu-id="f0f6e-156">Instead of creating new tests, apply these two attributes to create a series of tests that test several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="f0f6e-157">Run `dotnet test`, and two of these tests fail.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-157">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="f0f6e-158">To make all of the tests pass, change the `if` clause at the beginning of the `Main` method in the *PrimeServices.cs* file:</span><span class="sxs-lookup"><span data-stu-id="f0f6e-158">To make all of the tests pass, change the `if` clause at the beginning of the `Main` method in the *PrimeServices.cs* file:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="f0f6e-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="f0f6e-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="f0f6e-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="f0f6e-161">You've built a small library and a set of unit tests for that library.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-161">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="f0f6e-162">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-162">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="f0f6e-163">You've concentrated most of your time and effort on solving the goals of the application.</span><span class="sxs-lookup"><span data-stu-id="f0f6e-163">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
