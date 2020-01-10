---
title: Testování publikovaného výstupu pomocí dotnet VSTest
description: Naučte se spouštět testy publikovaných knihoven místo ve zdrojovém kódu pomocí příkazu dotnet VSTest.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.openlocfilehash: 7618d37782de3a16f1963380bbb56945fb73e8eb
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714257"
---
# <a name="test-published-output-with-dotnet-vstest"></a><span data-ttu-id="2438b-103">Testování publikovaného výstupu pomocí dotnet VSTest</span><span class="sxs-lookup"><span data-stu-id="2438b-103">Test published output with dotnet vstest</span></span>

<span data-ttu-id="2438b-104">Můžete spustit testy na již publikovaný výstup pomocí příkazu `dotnet vstest`.</span><span class="sxs-lookup"><span data-stu-id="2438b-104">You can run tests on already published output by using the `dotnet vstest` command.</span></span> <span data-ttu-id="2438b-105">To bude fungovat na testech xUnit, MSTest a NUnit.</span><span class="sxs-lookup"><span data-stu-id="2438b-105">This will work on xUnit, MSTest, and NUnit tests.</span></span> <span data-ttu-id="2438b-106">Jednoduše Najděte soubor DLL, který byl součástí publikovaného výstupu a spusťte:</span><span class="sxs-lookup"><span data-stu-id="2438b-106">Simply locate the DLL file that was part of your published output and run:</span></span>

```dotnetcli
dotnet vstest <MyPublishedTests>.dll
```

<span data-ttu-id="2438b-107">Kde `<MyPublishedTests>` je název vašeho publikovaného testovacího projektu.</span><span class="sxs-lookup"><span data-stu-id="2438b-107">Where `<MyPublishedTests>` is the name of your published test project.</span></span>

## <a name="example"></a><span data-ttu-id="2438b-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="2438b-108">Example</span></span>

<span data-ttu-id="2438b-109">Následující příkazy ukazují spuštění testů na publikované knihovně DLL.</span><span class="sxs-lookup"><span data-stu-id="2438b-109">The commands below demonstrate running tests on a published DLL.</span></span>

```dotnetcli
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> <span data-ttu-id="2438b-110">Poznámka: Pokud se vaše aplikace zaměřuje na jiný rámec než `netcoreapp`, můžete přesto spustit příkaz `dotnet vstest` předáním cílového rozhraní s příznakem rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2438b-110">Note: If your app targets a framework other than `netcoreapp`, you can still run the `dotnet vstest` command by passing in the targeted framework with a framework flag.</span></span> <span data-ttu-id="2438b-111">Například `dotnet vstest <MyPublishedTests>.dll --Framework:".NETFramework,Version=v4.6"`.</span><span class="sxs-lookup"><span data-stu-id="2438b-111">For example, `dotnet vstest <MyPublishedTests>.dll --Framework:".NETFramework,Version=v4.6"`.</span></span> <span data-ttu-id="2438b-112">V aplikaci Visual Studio 2017 Update 5 a novějších se požadované rozhraní detekuje automaticky.</span><span class="sxs-lookup"><span data-stu-id="2438b-112">In Visual Studio 2017 Update 5 and later, the desired framework is automatically detected.</span></span>

## <a name="see-also"></a><span data-ttu-id="2438b-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2438b-113">See also</span></span>

- [<span data-ttu-id="2438b-114">Testování částí pomocí příkazu dotnet test a xUnit</span><span class="sxs-lookup"><span data-stu-id="2438b-114">Unit Testing with dotnet test and xUnit</span></span>](unit-testing-with-dotnet-test.md)
- [<span data-ttu-id="2438b-115">Testování částí pomocí příkazu dotnet test a NUnit</span><span class="sxs-lookup"><span data-stu-id="2438b-115">Unit Testing with dotnet test and NUnit</span></span>](unit-testing-with-nunit.md)
- [<span data-ttu-id="2438b-116">Testování částí pomocí příkazu dotnet test a MSTest</span><span class="sxs-lookup"><span data-stu-id="2438b-116">Unit Testing with dotnet test and MSTest</span></span>](unit-testing-with-mstest.md)
