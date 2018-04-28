---
title: Portování do .NET Core - pomocí balíčku Windows kompatibility
description: Další informace o Windows Pack kompatibility a jak můžete ji použít k portu existující kód rozhraní .NET Framework na .NET Core
author: terrajobst
ms.author: mairaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.workload:
- dotnetcore
ms.openlocfilehash: 4ef7d9c847d48ae7bbb2d553b1c05cb90a1c5a7a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="using-the-windows-compatibility-pack"></a><span data-ttu-id="f909f-103">Pomocí balíčku Windows kompatibility</span><span class="sxs-lookup"><span data-stu-id="f909f-103">Using the Windows Compatibility Pack</span></span>

<span data-ttu-id="f909f-104">Jednou z nejběžnějších problémů, které vývojáři čelí při portování svůj existující kód na .NET Core je, jsou závislé na rozhraní API a technologie, které existují pouze v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f909f-104">One of the most common issues that developers face when porting their existing code to .NET Core is that they depend on APIs and technologies that only exist in the .NET Framework.</span></span> <span data-ttu-id="f909f-105">*Windows kompatibility Pack* je o zajišťování řada těchto technologii tak, aby vytváření aplikace .NET Core a také .NET standardní knihovny stalo mnohem víc přijatelná pro existující kód.</span><span class="sxs-lookup"><span data-stu-id="f909f-105">The *Windows Compatibility Pack* is about providing many of these technologies so that building .NET Core applications as well as .NET Standard libraries becomes much more viable for existing code.</span></span>

<span data-ttu-id="f909f-106">Tento balíček je logickou [rozšíření rozhraní .NET 2.0 standardní](../whats-new/index.md#api-changes-and-library-support) že výrazně zvyšuje sada rozhraní API a existující kód zkompiluje téměř beze změn.</span><span class="sxs-lookup"><span data-stu-id="f909f-106">This package is a logical [extension of .NET Standard 2.0](../whats-new/index.md#api-changes-and-library-support) that significantly increases API set and existing code compiles with almost no modifications.</span></span> <span data-ttu-id="f909f-107">Ale chcete-li zachovat potenciálu .NET Standard ("je sada rozhraní API, které poskytují všechny implementace rozhraní .NET"), to nezahrnuli technologie, které nemůže pracovat pro všechny platformy, jako je například registr, systém Windows Management Instrumentation (WMI), nebo emitování reflexe Rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="f909f-107">But in order to keep the promise of .NET Standard ("it is the set of APIs that all .NET implementations provide"), this didn't include technologies that can't work across all platforms, such as registry, Windows Management Instrumentation (WMI), or reflection emit APIs.</span></span>

<span data-ttu-id="f909f-108">*Windows kompatibility Pack* je umístěna nad .NET Standard a poskytuje přístup k technologie, které jsou pouze v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="f909f-108">The *Windows Compatibility Pack* sits on top of .NET Standard and provides access to technologies that are Windows only.</span></span> <span data-ttu-id="f909f-109">Je obzvláště užitečná pro zákazníky, které chcete přesunout do .NET Core, ale chcete zůstat v systému Windows jako první krok.</span><span class="sxs-lookup"><span data-stu-id="f909f-109">It's especially useful for customers that want to move to .NET Core but plan to stay on Windows as a first step.</span></span> <span data-ttu-id="f909f-110">V tomto scénáři nebude moci používat pouze pro systém Windows technologie je pouze mezní migrace nulové architektury výhod.</span><span class="sxs-lookup"><span data-stu-id="f909f-110">In that scenario, not being able to use Windows-only technologies is only a migration hurdle with zero architectural benefits.</span></span>

## <a name="package-contents"></a><span data-ttu-id="f909f-111">Obsah balíčku</span><span class="sxs-lookup"><span data-stu-id="f909f-111">Package contents</span></span>

<span data-ttu-id="f909f-112">*Windows kompatibility Pack* je k dispozici prostřednictvím balíčku NuGet [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) a můžete na něj odkazovat z projektů cílení na .NET Core nebo .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="f909f-112">The *Windows Compatibility Pack* is provided via the NuGet Package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) and can be referenced from projects targeting .NET Core or .NET Standard.</span></span>

<span data-ttu-id="f909f-113">Poskytuje přibližně 20 000 rozhraní API, včetně pouze pro systém Windows a také napříč platformami rozhraní API z těchto oblastí technologie:</span><span class="sxs-lookup"><span data-stu-id="f909f-113">It provides about 20,000 APIs, including Windows-only as well as cross-platform APIs from the following technology areas:</span></span>

* <span data-ttu-id="f909f-114">Znakové stránky</span><span class="sxs-lookup"><span data-stu-id="f909f-114">Code Pages</span></span>
* <span data-ttu-id="f909f-115">Modelu codeDom</span><span class="sxs-lookup"><span data-stu-id="f909f-115">CodeDom</span></span>
* <span data-ttu-id="f909f-116">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="f909f-116">Configuration</span></span>
* <span data-ttu-id="f909f-117">Adresářové služby</span><span class="sxs-lookup"><span data-stu-id="f909f-117">Directory Services</span></span>
* <span data-ttu-id="f909f-118">Kreslení</span><span class="sxs-lookup"><span data-stu-id="f909f-118">Drawing</span></span>
* <span data-ttu-id="f909f-119">ODBC</span><span class="sxs-lookup"><span data-stu-id="f909f-119">ODBC</span></span>
* <span data-ttu-id="f909f-120">Oprávnění</span><span class="sxs-lookup"><span data-stu-id="f909f-120">Permissions</span></span>
* <span data-ttu-id="f909f-121">Porty</span><span class="sxs-lookup"><span data-stu-id="f909f-121">Ports</span></span>
* <span data-ttu-id="f909f-122">Seznamy řízení přístupu (ACL)</span><span class="sxs-lookup"><span data-stu-id="f909f-122">Windows Access Control Lists (ACL)</span></span>
* <span data-ttu-id="f909f-123">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="f909f-123">Windows Communication Foundation (WCF)</span></span>
* <span data-ttu-id="f909f-124">Kryptografie systému Windows</span><span class="sxs-lookup"><span data-stu-id="f909f-124">Windows Cryptography</span></span>
* <span data-ttu-id="f909f-125">Protokol událostí systému Windows</span><span class="sxs-lookup"><span data-stu-id="f909f-125">Windows EventLog</span></span>
* <span data-ttu-id="f909f-126">Windows Management Instrumentation (WMI)</span><span class="sxs-lookup"><span data-stu-id="f909f-126">Windows Management Instrumentation (WMI)</span></span>
* <span data-ttu-id="f909f-127">Čítače výkonu systému Windows</span><span class="sxs-lookup"><span data-stu-id="f909f-127">Windows Performance Counters</span></span>
* <span data-ttu-id="f909f-128">Registru systému Windows</span><span class="sxs-lookup"><span data-stu-id="f909f-128">Windows Registry</span></span>
* <span data-ttu-id="f909f-129">Ukládání do mezipaměti Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="f909f-129">Windows Runtime Caching</span></span>
* <span data-ttu-id="f909f-130">Služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="f909f-130">Windows Services</span></span>

<span data-ttu-id="f909f-131">Další informace najdete v tématu [specifikace sady kompatibility](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span><span class="sxs-lookup"><span data-stu-id="f909f-131">For more information, see the [spec of the compatibility pack](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="f909f-132">Začínáme</span><span class="sxs-lookup"><span data-stu-id="f909f-132">Get started</span></span>

1. <span data-ttu-id="f909f-133">Před přenosem, nezapomeňte si prohlédněte [portování proces](index.md).</span><span class="sxs-lookup"><span data-stu-id="f909f-133">Before porting, make sure to take a look at the [Porting Process](index.md).</span></span>

2. <span data-ttu-id="f909f-134">Když portování stávajícího kódu pro .NET Core nebo .NET Standard, nainstalujte balíček NuGet [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span><span class="sxs-lookup"><span data-stu-id="f909f-134">When porting existing code to .NET Core or .NET Standard, install the NuGet package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span>

3. <span data-ttu-id="f909f-135">Pokud chcete zůstat v systému Windows, je vše připraveno.</span><span class="sxs-lookup"><span data-stu-id="f909f-135">If you want to stay on Windows, you're all set.</span></span>

4. <span data-ttu-id="f909f-136">Pokud chcete spustit aplikace .NET Core nebo .NET Standard knihovny na Linuxu nebo systému macOS, použijte [API Analyzer](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) najít využití rozhraní API, která nebude fungovat napříč platformami.</span><span class="sxs-lookup"><span data-stu-id="f909f-136">If you want to run the .NET Core application or .NET Standard library on Linux or macOS, use the [API Analyzer](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) to find usage of APIs that won't work cross-platform.</span></span>

5. <span data-ttu-id="f909f-137">Buď odeberte použití těchto rozhraní API, je nahradit alternativami napříč platformami nebo pomocí platformy kontrolu, jako je ochrana:</span><span class="sxs-lookup"><span data-stu-id="f909f-137">Either remove the usages of those APIs, replace them with cross-platform alternatives, or guard them using a platform check, like:</span></span>

    ```csharp
    private static string GetLoggingPath()
    {
        // Verify the code is running on Windows.
        if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
        {
            using (var key = Registry.CurrentUser.OpenSubKey(@"Software\Fabrikam\AssetManagement"))
            {
                if (key?.GetValue("LoggingDirectoryPath") is string configuredPath)
                    return configuredPath;
            }
        }

        // This is either not running on Windows or no logging path was configured,
        // so just use the path for non-roaming user-specific data files.
        var appDataPath = Environment.GetFolderPath(Environment.SpecialFolder.LocalApplicationData);
        return Path.Combine(appDataPath, "Fabrikam", "AssetManagement", "Logging");
    }
    ```

<span data-ttu-id="f909f-138">Pro ukázku, podívejte se [Channel 9 video kompatibility sady Windows](https://channel9.msdn.com/Events/Connect/2017/T123).</span><span class="sxs-lookup"><span data-stu-id="f909f-138">For a demo, check out the [Channel 9 video of the Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span></span>

