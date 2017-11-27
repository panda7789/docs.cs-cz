---
title: "Testování publikované výstup s vstest dotnet."
description: "Zjistěte, jak spustit testy na publikované výstup pomocí příkazu vstest dotnet."
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 3965e4ca-75b8-4969-b3af-ca993c397a15
ms.openlocfilehash: 217787d41a9da6000941ded6caaa4f44d124644b
ms.sourcegitcommit: 8a4f8e6a7f1341764abcd188a332cc28d1e2d8ec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="test-published-output-with-dotnet-vstest"></a><span data-ttu-id="19209-103">Testování publikované výstup s vstest dotnet.</span><span class="sxs-lookup"><span data-stu-id="19209-103">Test published output with dotnet vstest</span></span>

<span data-ttu-id="19209-104">Testy můžete spustit na výstupu již publikované pomocí `dotnet vstest` příkaz.</span><span class="sxs-lookup"><span data-stu-id="19209-104">You can run tests on already published output by using the `dotnet vstest` command.</span></span> <span data-ttu-id="19209-105">To bude fungovat na xUnit, Mstestu a NUnit testy.</span><span class="sxs-lookup"><span data-stu-id="19209-105">This will work on xUnit, MSTest, and NUnit tests.</span></span> <span data-ttu-id="19209-106">Jednoduše vyhledejte soubor knihovny DLL, který byl součástí publikované výstupu a spusťte:</span><span class="sxs-lookup"><span data-stu-id="19209-106">Simply locate the DLL file that was part of your published output and run:</span></span>
```
dotnet vstest <MyPublishedTests>.dll
```
<span data-ttu-id="19209-107">kde `<MyPublishedTests>` je název publikované testovacího projektu.</span><span class="sxs-lookup"><span data-stu-id="19209-107">where `<MyPublishedTests>` is the name of your published test project.</span></span>

### <a name="example-of-running-tests-on-a-published-dll"></a><span data-ttu-id="19209-108">Příklad spuštění testů na publikované knihovny DLL</span><span class="sxs-lookup"><span data-stu-id="19209-108">Example of running tests on a published DLL</span></span>

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE] <span data-ttu-id="19209-109">Poznámka: Pokud aplikace cílí rozhraní než `netcoreapp` pořád se dá spustit `dotnet vstest` příkaz předáním v cílové rozhraní s příznakem framework.</span><span class="sxs-lookup"><span data-stu-id="19209-109">Note: If your app is targeting a framework other than `netcoreapp` you can still run the `dotnet vstest` command by passing in the targeted framework with a framework flag.</span></span> <span data-ttu-id="19209-110">Například `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span><span class="sxs-lookup"><span data-stu-id="19209-110">For example, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span></span> <span data-ttu-id="19209-111">V sadě Visual Studio 2017 aktualizace 5 je automaticky zjišťován požadované rozhraní.</span><span class="sxs-lookup"><span data-stu-id="19209-111">In Visual Studio 2017 Update 5 the desired framework is automatically detected.</span></span>

### <a name="related-topics"></a><span data-ttu-id="19209-112">Související témata</span><span class="sxs-lookup"><span data-stu-id="19209-112">Related topics</span></span>
- [<span data-ttu-id="19209-113">Testování částí s dotnet test a xUnit</span><span class="sxs-lookup"><span data-stu-id="19209-113">Unit Testing with dotnet test and xUnit</span></span>](unit-testing-with-dotnet-test.md)
- [<span data-ttu-id="19209-114">Testování částí s dotnet test a Mstestu</span><span class="sxs-lookup"><span data-stu-id="19209-114">Unit Testing with dotnet test and MSTest</span></span>](unit-testing-with-mstest.md)
