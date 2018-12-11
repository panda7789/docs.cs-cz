---
title: Testování publikované výstup s dotnet test
description: Zjistěte, jak spustit testy na publikované výstupu pomocí příkazu dotnet vstest.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.custom: seodec18
ms.openlocfilehash: 8930ec5c19254423fcdc9f0790ccf6748c595d6b
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170289"
---
# <a name="test-published-output-with-dotnet-vstest"></a><span data-ttu-id="b0774-103">Testování publikované výstup s dotnet test</span><span class="sxs-lookup"><span data-stu-id="b0774-103">Test published output with dotnet vstest</span></span>

<span data-ttu-id="b0774-104">Je možné spustit testy na výstupu už byla publikována s použitím `dotnet vstest` příkazu.</span><span class="sxs-lookup"><span data-stu-id="b0774-104">You can run tests on already published output by using the `dotnet vstest` command.</span></span> <span data-ttu-id="b0774-105">Bude to fungovat u xUnit, MSTest a NUnit testy.</span><span class="sxs-lookup"><span data-stu-id="b0774-105">This will work on xUnit, MSTest, and NUnit tests.</span></span> <span data-ttu-id="b0774-106">Jednoduše vyhledejte soubor knihovny DLL, která byla součástí publikovaný výstup a spusťte:</span><span class="sxs-lookup"><span data-stu-id="b0774-106">Simply locate the DLL file that was part of your published output and run:</span></span>

```
dotnet vstest <MyPublishedTests>.dll
```

<span data-ttu-id="b0774-107">kde `<MyPublishedTests>` je název publikované testovacího projektu.</span><span class="sxs-lookup"><span data-stu-id="b0774-107">where `<MyPublishedTests>` is the name of your published test project.</span></span>

## <a name="example-of-running-tests-on-a-published-dll"></a><span data-ttu-id="b0774-108">Příklad spouštění testů v publikované knihovny DLL</span><span class="sxs-lookup"><span data-stu-id="b0774-108">Example of running tests on a published DLL</span></span>

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> <span data-ttu-id="b0774-109">Poznámka: Pokud vaše aplikace cílí na rozhraní než `netcoreapp` můžete nadále spouštět `dotnet vstest` příkaz předáním s příznakem framework cíleného rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b0774-109">Note: If your app is targeting a framework other than `netcoreapp` you can still run the `dotnet vstest` command by passing in the targeted framework with a framework flag.</span></span> <span data-ttu-id="b0774-110">Například, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span><span class="sxs-lookup"><span data-stu-id="b0774-110">For example, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span></span> <span data-ttu-id="b0774-111">Ve verzi Visual Studio 2017 Update 5 je automaticky rozpoznán požadované rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b0774-111">In Visual Studio 2017 Update 5 the desired framework is automatically detected.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0774-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b0774-112">See also</span></span>
- [<span data-ttu-id="b0774-113">Testování částí pomocí příkazu dotnet test a xUnit</span><span class="sxs-lookup"><span data-stu-id="b0774-113">Unit Testing with dotnet test and xUnit</span></span>](unit-testing-with-dotnet-test.md)
- [<span data-ttu-id="b0774-114">Testování částí pomocí příkazu dotnet test a NUnit</span><span class="sxs-lookup"><span data-stu-id="b0774-114">Unit Testing with dotnet test and NUnit</span></span>](unit-testing-with-nunit.md)
- [<span data-ttu-id="b0774-115">Testování částí pomocí příkazu dotnet test a MSTest</span><span class="sxs-lookup"><span data-stu-id="b0774-115">Unit Testing with dotnet test and MSTest</span></span>](unit-testing-with-mstest.md)
