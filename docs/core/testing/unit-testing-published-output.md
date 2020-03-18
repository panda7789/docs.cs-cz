---
title: Test publikovaný výstup s dotnet vstest
description: Naučte se, jak spustit testy na publikovaných knihoven, nikoli na zdrojový kód, s dotnet vstest příkazu.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.openlocfilehash: 7618d37782de3a16f1963380bbb56945fb73e8eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714257"
---
# <a name="test-published-output-with-dotnet-vstest"></a><span data-ttu-id="33c34-103">Test publikovaný výstup s dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="33c34-103">Test published output with dotnet vstest</span></span>

<span data-ttu-id="33c34-104">Testy již publikovaného výstupu můžete spustit `dotnet vstest` pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="33c34-104">You can run tests on already published output by using the `dotnet vstest` command.</span></span> <span data-ttu-id="33c34-105">To bude fungovat na xUnit, MSTest a NUnit testy.</span><span class="sxs-lookup"><span data-stu-id="33c34-105">This will work on xUnit, MSTest, and NUnit tests.</span></span> <span data-ttu-id="33c34-106">Jednoduše vyhledejte soubor DLL, který byl součástí publikovaného výstupu, a spusťte:</span><span class="sxs-lookup"><span data-stu-id="33c34-106">Simply locate the DLL file that was part of your published output and run:</span></span>

```dotnetcli
dotnet vstest <MyPublishedTests>.dll
```

<span data-ttu-id="33c34-107">Kde `<MyPublishedTests>` je název publikovaného testovacího projektu.</span><span class="sxs-lookup"><span data-stu-id="33c34-107">Where `<MyPublishedTests>` is the name of your published test project.</span></span>

## <a name="example"></a><span data-ttu-id="33c34-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="33c34-108">Example</span></span>

<span data-ttu-id="33c34-109">Níže uvedené příkazy ukazují spuštění testů na publikované dll.</span><span class="sxs-lookup"><span data-stu-id="33c34-109">The commands below demonstrate running tests on a published DLL.</span></span>

```dotnetcli
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> <span data-ttu-id="33c34-110">Poznámka: Pokud vaše aplikace cílí na jiné rozhraní než `netcoreapp`, můžete příkaz spustit `dotnet vstest` předáním v cílovém rámci s příznakem architektury.</span><span class="sxs-lookup"><span data-stu-id="33c34-110">Note: If your app targets a framework other than `netcoreapp`, you can still run the `dotnet vstest` command by passing in the targeted framework with a framework flag.</span></span> <span data-ttu-id="33c34-111">Například, `dotnet vstest <MyPublishedTests>.dll --Framework:".NETFramework,Version=v4.6"`.</span><span class="sxs-lookup"><span data-stu-id="33c34-111">For example, `dotnet vstest <MyPublishedTests>.dll --Framework:".NETFramework,Version=v4.6"`.</span></span> <span data-ttu-id="33c34-112">V aktualizaci Visual Studio 2017 Update 5 a novější se automaticky zjistí požadovaný rámec.</span><span class="sxs-lookup"><span data-stu-id="33c34-112">In Visual Studio 2017 Update 5 and later, the desired framework is automatically detected.</span></span>

## <a name="see-also"></a><span data-ttu-id="33c34-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="33c34-113">See also</span></span>

- [<span data-ttu-id="33c34-114">Testování částí s dotnetovým testem a xUnit</span><span class="sxs-lookup"><span data-stu-id="33c34-114">Unit Testing with dotnet test and xUnit</span></span>](unit-testing-with-dotnet-test.md)
- [<span data-ttu-id="33c34-115">Testování částí s dotnetovým testem a NUnit</span><span class="sxs-lookup"><span data-stu-id="33c34-115">Unit Testing with dotnet test and NUnit</span></span>](unit-testing-with-nunit.md)
- [<span data-ttu-id="33c34-116">Testování částí s dotnet testem a MSTest</span><span class="sxs-lookup"><span data-stu-id="33c34-116">Unit Testing with dotnet test and MSTest</span></span>](unit-testing-with-mstest.md)
