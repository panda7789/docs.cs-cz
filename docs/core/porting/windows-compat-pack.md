---
title: Použití sady Windows Compatibility Pack port kódu až po .NET Core
description: Další informace o Windows Compatibility Pack a jak můžete pomocí jeho port existujícího kódu rozhraní .NET Framework do .NET Core
author: terrajobst
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: c4fd888e0fbce86ab317f18fd77374af5d3ca244
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717892"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a><span data-ttu-id="b0dd9-103">Použití sady Windows Compatibility Pack port kódu až po .NET Core</span><span class="sxs-lookup"><span data-stu-id="b0dd9-103">Use the Windows Compatibility Pack to port code to .NET Core</span></span>

<span data-ttu-id="b0dd9-104">Některé z nejběžnějších problémů zjištěných při přenášíte stávající kód až po .NET Core jsou závislosti na rozhraní API a technologií, které se nacházejí pouze v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b0dd9-104">Some of the most common issues found when porting existing code to .NET Core are dependencies on APIs and technologies that are only found in the .NET Framework.</span></span> <span data-ttu-id="b0dd9-105">*Windows Compatibility Pack* poskytuje mnoho z těchto technologií tak, aby byl mnohem jednodušší vytvářet aplikace .NET Core a knihovny .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="b0dd9-105">The *Windows Compatibility Pack* provides many of these technologies, so it's much easier to build .NET Core applications and .NET Standard libraries.</span></span>

<span data-ttu-id="b0dd9-106">Tento balíček je logické [rozšíření .NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) , výrazně zvyšuje sada rozhraní API a existující kód zkompiluje téměř bez možnosti úprav.</span><span class="sxs-lookup"><span data-stu-id="b0dd9-106">This package is a logical [extension of .NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) that significantly increases API set and existing code compiles with almost no modifications.</span></span> <span data-ttu-id="b0dd9-107">Ale pokud chcete zachovat uskutečnění .NET Standard ("je sada rozhraní API, která poskytují všechny implementace .NET"), to nezahrnuli technologie, které nemůže pracovat na všech platformách, jako je například registru Windows Management Instrumentation (WMI), nebo generování reflexe Rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="b0dd9-107">But in order to keep the promise of .NET Standard ("it is the set of APIs that all .NET implementations provide"), this didn't include technologies that can't work across all platforms, such as registry, Windows Management Instrumentation (WMI), or reflection emit APIs.</span></span>

<span data-ttu-id="b0dd9-108">*Windows Compatibility Pack* nachází nad .NET Standard a poskytuje přístup k technologiím, které jsou pouze Windows.</span><span class="sxs-lookup"><span data-stu-id="b0dd9-108">The *Windows Compatibility Pack* sits on top of .NET Standard and provides access to technologies that are Windows only.</span></span> <span data-ttu-id="b0dd9-109">To je obzvláště užitečné pro zákazníky, které chcete přesunout do .NET Core, ale plán zůstat na Windows jako první krok.</span><span class="sxs-lookup"><span data-stu-id="b0dd9-109">It's especially useful for customers that want to move to .NET Core but plan to stay on Windows as a first step.</span></span> <span data-ttu-id="b0dd9-110">V takovém scénáři nebude moct používat jenom pro Windows technologie je pouze mezní migrace s nulovou výhody architektury.</span><span class="sxs-lookup"><span data-stu-id="b0dd9-110">In that scenario, not being able to use Windows-only technologies is only a migration hurdle with zero architectural benefits.</span></span>

## <a name="package-contents"></a><span data-ttu-id="b0dd9-111">Obsah balíčku</span><span class="sxs-lookup"><span data-stu-id="b0dd9-111">Package contents</span></span>

<span data-ttu-id="b0dd9-112">*Windows Compatibility Pack* je k dispozici prostřednictvím balíčku NuGet [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) a můžete na něj odkazovat z projektů, které cílí na .NET Core nebo .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="b0dd9-112">The *Windows Compatibility Pack* is provided via the NuGet Package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) and can be referenced from projects targeting .NET Core or .NET Standard.</span></span>

<span data-ttu-id="b0dd9-113">Poskytuje informace o 20 000 rozhraní API, včetně jen pro Windows i multiplatformní rozhraní API z těchto oblastí technologie:</span><span class="sxs-lookup"><span data-stu-id="b0dd9-113">It provides about 20,000 APIs, including Windows-only as well as cross-platform APIs from the following technology areas:</span></span>

* <span data-ttu-id="b0dd9-114">Znakové stránky</span><span class="sxs-lookup"><span data-stu-id="b0dd9-114">Code Pages</span></span>
* <span data-ttu-id="b0dd9-115">CodeDom</span><span class="sxs-lookup"><span data-stu-id="b0dd9-115">CodeDom</span></span>
* <span data-ttu-id="b0dd9-116">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="b0dd9-116">Configuration</span></span>
* <span data-ttu-id="b0dd9-117">Adresářové služby</span><span class="sxs-lookup"><span data-stu-id="b0dd9-117">Directory Services</span></span>
* <span data-ttu-id="b0dd9-118">Kreslení</span><span class="sxs-lookup"><span data-stu-id="b0dd9-118">Drawing</span></span>
* <span data-ttu-id="b0dd9-119">ODBC</span><span class="sxs-lookup"><span data-stu-id="b0dd9-119">ODBC</span></span>
* <span data-ttu-id="b0dd9-120">Oprávnění</span><span class="sxs-lookup"><span data-stu-id="b0dd9-120">Permissions</span></span>
* <span data-ttu-id="b0dd9-121">Porty</span><span class="sxs-lookup"><span data-stu-id="b0dd9-121">Ports</span></span>
* <span data-ttu-id="b0dd9-122">Windows seznamy řízení přístupu (ACL)</span><span class="sxs-lookup"><span data-stu-id="b0dd9-122">Windows Access Control Lists (ACL)</span></span>
* <span data-ttu-id="b0dd9-123">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="b0dd9-123">Windows Communication Foundation (WCF)</span></span>
* <span data-ttu-id="b0dd9-124">Windows Cryptography</span><span class="sxs-lookup"><span data-stu-id="b0dd9-124">Windows Cryptography</span></span>
* <span data-ttu-id="b0dd9-125">Windows EventLog</span><span class="sxs-lookup"><span data-stu-id="b0dd9-125">Windows EventLog</span></span>
* <span data-ttu-id="b0dd9-126">Windows Management Instrumentation (WMI)</span><span class="sxs-lookup"><span data-stu-id="b0dd9-126">Windows Management Instrumentation (WMI)</span></span>
* <span data-ttu-id="b0dd9-127">Čítače výkonu Windows</span><span class="sxs-lookup"><span data-stu-id="b0dd9-127">Windows Performance Counters</span></span>
* <span data-ttu-id="b0dd9-128">Registru Windows</span><span class="sxs-lookup"><span data-stu-id="b0dd9-128">Windows Registry</span></span>
* <span data-ttu-id="b0dd9-129">Ukládání do mezipaměti Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="b0dd9-129">Windows Runtime Caching</span></span>
* <span data-ttu-id="b0dd9-130">Služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="b0dd9-130">Windows Services</span></span>

<span data-ttu-id="b0dd9-131">Další informace najdete v tématu [specifikace sady kompatibility](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span><span class="sxs-lookup"><span data-stu-id="b0dd9-131">For more information, see the [spec of the compatibility pack](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="b0dd9-132">Začínáme</span><span class="sxs-lookup"><span data-stu-id="b0dd9-132">Get started</span></span>

1. <span data-ttu-id="b0dd9-133">Před přenos, ujistěte se, že se podívat na [portování procesu](index.md).</span><span class="sxs-lookup"><span data-stu-id="b0dd9-133">Before porting, make sure to take a look at the [Porting Process](index.md).</span></span>

2. <span data-ttu-id="b0dd9-134">Pokud přenášíte stávající kód .NET Core nebo .NET Standard, nainstalujte balíček NuGet [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span><span class="sxs-lookup"><span data-stu-id="b0dd9-134">When porting existing code to .NET Core or .NET Standard, install the NuGet package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span>

3. <span data-ttu-id="b0dd9-135">Pokud budete chtít zůstat na Windows, všechno je nastavené.</span><span class="sxs-lookup"><span data-stu-id="b0dd9-135">If you want to stay on Windows, you're all set.</span></span>

4. <span data-ttu-id="b0dd9-136">Pokud chcete spustit aplikaci .NET Core nebo .NET Standard knihovny v Linuxu nebo macOS, použijte [analyzátor rozhraní API](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/) najít využití rozhraní API, která nebude fungovat napříč platformami.</span><span class="sxs-lookup"><span data-stu-id="b0dd9-136">If you want to run the .NET Core application or .NET Standard library on Linux or macOS, use the [API Analyzer](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/) to find usage of APIs that won't work cross-platform.</span></span>

5. <span data-ttu-id="b0dd9-137">Odeberte použití těchto rozhraní API, je nahradit alternativami napříč platformami nebo chránit je pomocí kontroly platformy, jako jsou:</span><span class="sxs-lookup"><span data-stu-id="b0dd9-137">Either remove the usages of those APIs, replace them with cross-platform alternatives, or guard them using a platform check, like:</span></span>

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

<span data-ttu-id="b0dd9-138">Předváděcí akci, podívejte se [videa Channel 9 sady Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span><span class="sxs-lookup"><span data-stu-id="b0dd9-138">For a demo, check out the [Channel 9 video of the Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span></span>
