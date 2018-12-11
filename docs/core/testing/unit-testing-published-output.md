---
title: Testování publikované výstup s dotnet test
description: Zjistěte, jak spustit testy na publikované knihovny, místo na zdrojový kód, pomocí příkazu dotnet vstest.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.custom: seodec18
ms.openlocfilehash: 9d842f26336d0ddf5375d49676523086bb632684
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239524"
---
# <a name="test-published-output-with-dotnet-vstest"></a><span data-ttu-id="63f75-103">Testování publikované výstup s dotnet test</span><span class="sxs-lookup"><span data-stu-id="63f75-103">Test published output with dotnet vstest</span></span>

<span data-ttu-id="63f75-104">Je možné spustit testy na výstupu už byla publikována s použitím `dotnet vstest` příkazu.</span><span class="sxs-lookup"><span data-stu-id="63f75-104">You can run tests on already published output by using the `dotnet vstest` command.</span></span> <span data-ttu-id="63f75-105">Bude to fungovat u xUnit, MSTest a NUnit testy.</span><span class="sxs-lookup"><span data-stu-id="63f75-105">This will work on xUnit, MSTest, and NUnit tests.</span></span> <span data-ttu-id="63f75-106">Jednoduše vyhledejte soubor knihovny DLL, která byla součástí publikovaný výstup a spusťte:</span><span class="sxs-lookup"><span data-stu-id="63f75-106">Simply locate the DLL file that was part of your published output and run:</span></span>

```
dotnet vstest <MyPublishedTests>.dll
```

<span data-ttu-id="63f75-107">kde `<MyPublishedTests>` je název publikované testovacího projektu.</span><span class="sxs-lookup"><span data-stu-id="63f75-107">Where `<MyPublishedTests>` is the name of your published test project.</span></span>

## <a name="example"></a><span data-ttu-id="63f75-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="63f75-108">Example</span></span>

<span data-ttu-id="63f75-109">Následující příkazy ukazují, spouštění testů na publikované knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="63f75-109">The commands below demonstrate running tests on a published DLL.</span></span>

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> <span data-ttu-id="63f75-110">Poznámka: Pokud vaše aplikace cílí na rozhraní než `netcoreapp` můžete nadále spouštět `dotnet vstest` příkaz předáním s příznakem framework cíleného rozhraní.</span><span class="sxs-lookup"><span data-stu-id="63f75-110">Note: If your app is targeting a framework other than `netcoreapp` you can still run the `dotnet vstest` command by passing in the targeted framework with a framework flag.</span></span> <span data-ttu-id="63f75-111">Například, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span><span class="sxs-lookup"><span data-stu-id="63f75-111">For example, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span></span> <span data-ttu-id="63f75-112">Ve verzi Visual Studio 2017 Update 5 je automaticky rozpoznán požadované rozhraní.</span><span class="sxs-lookup"><span data-stu-id="63f75-112">In Visual Studio 2017 Update 5 the desired framework is automatically detected.</span></span>

## <a name="see-also"></a><span data-ttu-id="63f75-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="63f75-113">See also</span></span>
- [<span data-ttu-id="63f75-114">Testování částí pomocí příkazu dotnet test a xUnit</span><span class="sxs-lookup"><span data-stu-id="63f75-114">Unit Testing with dotnet test and xUnit</span></span>](unit-testing-with-dotnet-test.md)
- [<span data-ttu-id="63f75-115">Testování částí pomocí příkazu dotnet test a NUnit</span><span class="sxs-lookup"><span data-stu-id="63f75-115">Unit Testing with dotnet test and NUnit</span></span>](unit-testing-with-nunit.md)
- [<span data-ttu-id="63f75-116">Testování částí pomocí příkazu dotnet test a MSTest</span><span class="sxs-lookup"><span data-stu-id="63f75-116">Unit Testing with dotnet test and MSTest</span></span>](unit-testing-with-mstest.md)
