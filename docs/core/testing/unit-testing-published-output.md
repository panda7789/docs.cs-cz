---
title: Testování publikované výstup s vstest dotnet.
description: Zjistěte, jak spustit testy na publikované výstup pomocí příkazu vstest dotnet.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.workload:
- dotnetcore
ms.openlocfilehash: 2f750a8bb0907069691c4a4491beeb4b1733df29
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="test-published-output-with-dotnet-vstest"></a><span data-ttu-id="2c3e3-103">Testování publikované výstup s vstest dotnet.</span><span class="sxs-lookup"><span data-stu-id="2c3e3-103">Test published output with dotnet vstest</span></span>

<span data-ttu-id="2c3e3-104">Testy můžete spustit na výstupu již publikované pomocí `dotnet vstest` příkaz.</span><span class="sxs-lookup"><span data-stu-id="2c3e3-104">You can run tests on already published output by using the `dotnet vstest` command.</span></span> <span data-ttu-id="2c3e3-105">To bude fungovat na xUnit, Mstestu a NUnit testy.</span><span class="sxs-lookup"><span data-stu-id="2c3e3-105">This will work on xUnit, MSTest, and NUnit tests.</span></span> <span data-ttu-id="2c3e3-106">Jednoduše vyhledejte soubor knihovny DLL, který byl součástí publikované výstupu a spusťte:</span><span class="sxs-lookup"><span data-stu-id="2c3e3-106">Simply locate the DLL file that was part of your published output and run:</span></span>

```
dotnet vstest <MyPublishedTests>.dll
```

<span data-ttu-id="2c3e3-107">kde `<MyPublishedTests>` je název publikované testovacího projektu.</span><span class="sxs-lookup"><span data-stu-id="2c3e3-107">where `<MyPublishedTests>` is the name of your published test project.</span></span>

## <a name="example-of-running-tests-on-a-published-dll"></a><span data-ttu-id="2c3e3-108">Příklad spuštění testů na publikované knihovny DLL</span><span class="sxs-lookup"><span data-stu-id="2c3e3-108">Example of running tests on a published DLL</span></span>

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> <span data-ttu-id="2c3e3-109">Poznámka: Pokud aplikace cílí rozhraní než `netcoreapp` pořád se dá spustit `dotnet vstest` příkaz předáním v cílové rozhraní s příznakem framework.</span><span class="sxs-lookup"><span data-stu-id="2c3e3-109">Note: If your app is targeting a framework other than `netcoreapp` you can still run the `dotnet vstest` command by passing in the targeted framework with a framework flag.</span></span> <span data-ttu-id="2c3e3-110">Například `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span><span class="sxs-lookup"><span data-stu-id="2c3e3-110">For example, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span></span> <span data-ttu-id="2c3e3-111">V sadě Visual Studio 2017 aktualizace 5 je automaticky zjišťován požadované rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2c3e3-111">In Visual Studio 2017 Update 5 the desired framework is automatically detected.</span></span>

## <a name="see-also"></a><span data-ttu-id="2c3e3-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="2c3e3-112">See also</span></span>
 [<span data-ttu-id="2c3e3-113">Testování částí s dotnet test a xUnit</span><span class="sxs-lookup"><span data-stu-id="2c3e3-113">Unit Testing with dotnet test and xUnit</span></span>](unit-testing-with-dotnet-test.md)  
 [<span data-ttu-id="2c3e3-114">Testování částí s dotnet test a Mstestu</span><span class="sxs-lookup"><span data-stu-id="2c3e3-114">Unit Testing with dotnet test and MSTest</span></span>](unit-testing-with-mstest.md)  
