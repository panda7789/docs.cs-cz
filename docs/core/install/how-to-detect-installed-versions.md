---
title: Kontrola nainstalovaných verzí .NET Core ve Windows, Linuxu a macOS - .NET Core
description: Přečtěte si, jak vypsat, které verze rozhraní .NET Core jsou v počítači nainstalovány. To zahrnuje běh .NET Core runtime a SDK.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 3a78acee6cf427085e98f14353fc2c0ac65d3d80
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645338"
---
# <a name="how-to-check-that-net-core-is-already-installed"></a><span data-ttu-id="8cdf1-104">Jak zkontrolovat, zda je jádro .NET Core již nainstalováno</span><span class="sxs-lookup"><span data-stu-id="8cdf1-104">How to check that .NET Core is already installed</span></span>

<span data-ttu-id="8cdf1-105">Tento článek vás naučí, jak zkontrolovat, které verze rozhraní .NET Core runtime a sady SDK jsou v počítači nainstalovány.</span><span class="sxs-lookup"><span data-stu-id="8cdf1-105">This article teaches you how to check which versions of the .NET Core runtime and SDK are installed on your computer.</span></span> <span data-ttu-id="8cdf1-106">Jádro .NET již bylo nainstalováno, pokud máte integrované vývojové prostředí, jako je visual studio nebo visual studio pro Mac.</span><span class="sxs-lookup"><span data-stu-id="8cdf1-106">.NET core may have already been installed if you have an integrated development environment, such as Visual Studio or Visual Studio for Mac.</span></span>

<span data-ttu-id="8cdf1-107">Instalace sady SDK nainstaluje odpovídající runtime.</span><span class="sxs-lookup"><span data-stu-id="8cdf1-107">Installing an SDK installs the corresponding runtime.</span></span>

<span data-ttu-id="8cdf1-108">Pokud některý příkaz v tomto článku selže, nemáte nainstalovaný runtime nebo SDK.</span><span class="sxs-lookup"><span data-stu-id="8cdf1-108">If any command in this article fails, you don't have the runtime or SDK installed.</span></span> <span data-ttu-id="8cdf1-109">Další informace naleznete v [tématu Stažení a instalace jádra .NET](index.md)Core .</span><span class="sxs-lookup"><span data-stu-id="8cdf1-109">For more information, see [Download and install .NET Core](index.md).</span></span>

## <a name="check-sdk-versions"></a><span data-ttu-id="8cdf1-110">Kontrola verzí sady SDK</span><span class="sxs-lookup"><span data-stu-id="8cdf1-110">Check SDK versions</span></span>

<span data-ttu-id="8cdf1-111">Můžete zjistit, které verze sady .NET Core SDK jsou aktuálně nainstalovány s terminálem.</span><span class="sxs-lookup"><span data-stu-id="8cdf1-111">You can see which versions of the .NET Core SDK are currently installed with a terminal.</span></span> <span data-ttu-id="8cdf1-112">Otevřete terminál a spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="8cdf1-112">Open a terminal and run the following command.</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="8cdf1-113">Získáte výstup podobný následující.</span><span class="sxs-lookup"><span data-stu-id="8cdf1-113">You get output similar to the following.</span></span>

::: zone pivot="os-windows"

```console
2.1.500 [C:\program files\dotnet\sdk]
2.1.502 [C:\program files\dotnet\sdk]
2.1.504 [C:\program files\dotnet\sdk]
2.1.600 [C:\program files\dotnet\sdk]
2.1.602 [C:\program files\dotnet\sdk]
2.2.101 [C:\program files\dotnet\sdk]
3.0.100 [C:\program files\dotnet\sdk]
3.1.100 [C:\program files\dotnet\sdk]
```

::: zone-end

::: zone pivot="os-linux"

```bash
2.1.500 [/home/user/dotnet/sdk]
2.1.502 [/home/user/dotnet/sdk]
2.1.504 [/home/user/dotnet/sdk]
2.1.600 [/home/user/dotnet/sdk]
2.1.602 [/home/user/dotnet/sdk]
2.2.101 [/home/user/dotnet/sdk]
3.0.100 [/home/user/dotnet/sdk]
3.1.100 [/home/user/dotnet/sdk]
```

::: zone-end

::: zone pivot="os-macos"

```bash
2.1.500 [/usr/local/share/dotnet/sdk]
2.1.502 [/usr/local/share/dotnet/sdk]
2.1.504 [/usr/local/share/dotnet/sdk]
2.1.600 [/usr/local/share/dotnet/sdk]
2.1.602 [/usr/local/share/dotnet/sdk]
2.2.101 [/usr/local/share/dotnet/sdk]
3.0.100 [/usr/local/share/dotnet/sdk]
3.1.100 [/usr/local/share/dotnet/sdk]
```

::: zone-end

## <a name="check-runtime-versions"></a><span data-ttu-id="8cdf1-114">Kontrola verzí za běhu</span><span class="sxs-lookup"><span data-stu-id="8cdf1-114">Check runtime versions</span></span>

<span data-ttu-id="8cdf1-115">Můžete zjistit, které verze runtime jádra .NET jsou aktuálně nainstalovány pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="8cdf1-115">You can see which versions of the .NET Core runtime are currently installed with the following command.</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="8cdf1-116">Získáte výstup podobný následující.</span><span class="sxs-lookup"><span data-stu-id="8cdf1-116">You get output similar to the following.</span></span>

::: zone pivot="os-windows"

```console
Microsoft.AspNetCore.All 2.1.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.3 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.6 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.0.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.3 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.7 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 3.0.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.WindowsDesktop.App 3.0.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
Microsoft.WindowsDesktop.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
```

::: zone-end

::: zone pivot="os-linux"

```bash
Microsoft.AspNetCore.All 2.1.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.3 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.6 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.0.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.3 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.7 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.0.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
```

::: zone-end

::: zone pivot="os-macos"

```bash
Microsoft.AspNetCore.All 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.3 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.6 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.0.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.3 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.7 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.0.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
```

::: zone-end

## <a name="check-for-install-folders"></a><span data-ttu-id="8cdf1-117">Kontrola instalačních složek</span><span class="sxs-lookup"><span data-stu-id="8cdf1-117">Check for install folders</span></span>

<span data-ttu-id="8cdf1-118">Je možné, že rozhraní .NET Core je `PATH` nainstalováno, ale není přidáno do proměnné pro váš operační systém nebo profil uživatele.</span><span class="sxs-lookup"><span data-stu-id="8cdf1-118">It's possible that .NET Core is installed but not added to the `PATH` variable for your operating system or user profile.</span></span> <span data-ttu-id="8cdf1-119">Spuštění příkazů z předchozích částí nemusí fungovat.</span><span class="sxs-lookup"><span data-stu-id="8cdf1-119">Running the commands from the previous sections may not work.</span></span> <span data-ttu-id="8cdf1-120">Jako alternativu můžete zkontrolovat, zda existují instalační složky .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8cdf1-120">As an alternative, you can check that the .NET Core install folders exist.</span></span>

<span data-ttu-id="8cdf1-121">Při instalaci rozhraní .NET Core z instalačního programu nebo skriptu je nainstalován do standardní složky.</span><span class="sxs-lookup"><span data-stu-id="8cdf1-121">When you install .NET Core from an installer or script, it's installed to a standard folder.</span></span> <span data-ttu-id="8cdf1-122">Většinu času instalační program nebo skript, který používáte k instalaci .NET Core vám dává možnost nainstalovat do jiné složky.</span><span class="sxs-lookup"><span data-stu-id="8cdf1-122">Much of the time the installer or script you're using to install .NET Core gives you an option to install to a different folder.</span></span> <span data-ttu-id="8cdf1-123">Pokud se rozhodnete nainstalovat do jiné složky, upravte začátek cesty ke složce.</span><span class="sxs-lookup"><span data-stu-id="8cdf1-123">If you choose to install to a different folder, adjust the start of the folder path.</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="8cdf1-124">**spustitelný soubor dotnet**</span><span class="sxs-lookup"><span data-stu-id="8cdf1-124">**dotnet executable**</span></span>\
<span data-ttu-id="8cdf1-125">_C:\\programové\\soubory\\dotnet dotnet.exe_</span><span class="sxs-lookup"><span data-stu-id="8cdf1-125">_C:\\program files\\dotnet\\dotnet.exe_</span></span>

- <span data-ttu-id="8cdf1-126">**Sada SDK rozhraní .NET**</span><span class="sxs-lookup"><span data-stu-id="8cdf1-126">**.NET SDK**</span></span>\
<span data-ttu-id="8cdf1-127">_C:\\programové\\soubory\\dotnet sdk\\{version}\\_</span><span class="sxs-lookup"><span data-stu-id="8cdf1-127">_C:\\program files\\dotnet\\sdk\\{version}\\_</span></span>

- <span data-ttu-id="8cdf1-128">**Doba běhu rozhraní .NET**</span><span class="sxs-lookup"><span data-stu-id="8cdf1-128">**.NET Runtime**</span></span>\
<span data-ttu-id="8cdf1-129">_C:\\programové\\soubory\\\\dotnet sdílené\\{runtime-type} {version}\\_</span><span class="sxs-lookup"><span data-stu-id="8cdf1-129">_C:\\program files\\dotnet\\shared\\{runtime-type}\\{version}\\_</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="8cdf1-130">**spustitelný soubor dotnet**</span><span class="sxs-lookup"><span data-stu-id="8cdf1-130">**dotnet executable**</span></span>\
<span data-ttu-id="8cdf1-131">_/home/user/share/dotnet/dotnet_</span><span class="sxs-lookup"><span data-stu-id="8cdf1-131">_/home/user/share/dotnet/dotnet_</span></span>

- <span data-ttu-id="8cdf1-132">**Sada SDK rozhraní .NET**</span><span class="sxs-lookup"><span data-stu-id="8cdf1-132">**.NET SDK**</span></span>\
<span data-ttu-id="8cdf1-133">_/home/user/share/dotnet/sdk/{version}/_</span><span class="sxs-lookup"><span data-stu-id="8cdf1-133">_/home/user/share/dotnet/sdk/{version}/_</span></span>

- <span data-ttu-id="8cdf1-134">**Doba běhu rozhraní .NET**</span><span class="sxs-lookup"><span data-stu-id="8cdf1-134">**.NET Runtime**</span></span>\
<span data-ttu-id="8cdf1-135">_/home/user/share/dotnet/shared/{runtime-type}/{version}/_</span><span class="sxs-lookup"><span data-stu-id="8cdf1-135">_/home/user/share/dotnet/shared/{runtime-type}/{version}/_</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="8cdf1-136">**spustitelný soubor dotnet**</span><span class="sxs-lookup"><span data-stu-id="8cdf1-136">**dotnet executable**</span></span>\
<span data-ttu-id="8cdf1-137">_/usr/local/share/dotnet/dotnet_</span><span class="sxs-lookup"><span data-stu-id="8cdf1-137">_/usr/local/share/dotnet/dotnet_</span></span>

- <span data-ttu-id="8cdf1-138">**Sada SDK rozhraní .NET**</span><span class="sxs-lookup"><span data-stu-id="8cdf1-138">**.NET SDK**</span></span>\
<span data-ttu-id="8cdf1-139">_/usr/local/share/dotnet/sdk/{version}/_</span><span class="sxs-lookup"><span data-stu-id="8cdf1-139">_/usr/local/share/dotnet/sdk/{version}/_</span></span>

- <span data-ttu-id="8cdf1-140">**Doba běhu rozhraní .NET**</span><span class="sxs-lookup"><span data-stu-id="8cdf1-140">**.NET Runtime**</span></span>\
<span data-ttu-id="8cdf1-141">_/usr/local/share/dotnet/shared/{runtime-type}/{version}/_</span><span class="sxs-lookup"><span data-stu-id="8cdf1-141">_/usr/local/share/dotnet/shared/{runtime-type}/{version}/_</span></span>

::: zone-end

## <a name="more-information"></a><span data-ttu-id="8cdf1-142">Další informace</span><span class="sxs-lookup"><span data-stu-id="8cdf1-142">More information</span></span>

<span data-ttu-id="8cdf1-143">Pomocí příkazu `dotnet --info`můžete zobrazit verze sady SDK i verze runtime .</span><span class="sxs-lookup"><span data-stu-id="8cdf1-143">You can see both the SDK versions and runtime versions with the command `dotnet --info`.</span></span> <span data-ttu-id="8cdf1-144">Získáte také další informace týkající se životního prostředí, jako je například verze operačního systému a identifikátor runtime (RID).</span><span class="sxs-lookup"><span data-stu-id="8cdf1-144">You'll also get other environmental related information, such as the operating system version and runtime identifier (RID).</span></span>

## <a name="next-steps"></a><span data-ttu-id="8cdf1-145">Další kroky</span><span class="sxs-lookup"><span data-stu-id="8cdf1-145">Next steps</span></span>

- <span data-ttu-id="8cdf1-146">[Nainstalujte rozhraní .NET Core Runtime](runtime.md).</span><span class="sxs-lookup"><span data-stu-id="8cdf1-146">[Install the .NET Core Runtime](runtime.md).</span></span>
- <span data-ttu-id="8cdf1-147">[Nainstalujte sadu .NET Core SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="8cdf1-147">[Install the .NET Core SDK](sdk.md).</span></span>
