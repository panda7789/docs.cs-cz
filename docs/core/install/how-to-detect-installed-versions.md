---
title: Kontrolovat nainstalované verze .NET Core v systémech Windows, Linux a macOS – .NET Core
description: Naučte se, jak zobrazit seznam verzí rozhraní .NET Core, které jsou nainstalovány ve vašem počítači. To zahrnuje modul runtime .NET Core a sadu SDK.
author: adegeo
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 96db0d707cefed791d9c2c01a6615e9af5168cc5
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85802985"
---
# <a name="how-to-check-that-net-core-is-already-installed"></a><span data-ttu-id="9d88f-104">Jak ověřit, že je rozhraní .NET Core již nainstalováno</span><span class="sxs-lookup"><span data-stu-id="9d88f-104">How to check that .NET Core is already installed</span></span>

<span data-ttu-id="9d88f-105">V tomto článku se dozvíte, jak zjistit, které verze modulu runtime .NET Core a sady SDK jsou nainstalovány ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="9d88f-105">This article teaches you how to check which versions of the .NET Core runtime and SDK are installed on your computer.</span></span> <span data-ttu-id="9d88f-106">Pokud máte integrované vývojové prostředí, jako je například Visual Studio nebo Visual Studio pro Mac, je možné, že rozhraní .NET Core již bylo nainstalováno.</span><span class="sxs-lookup"><span data-stu-id="9d88f-106">.NET core may have already been installed if you have an integrated development environment, such as Visual Studio or Visual Studio for Mac.</span></span>

<span data-ttu-id="9d88f-107">Instalace sady SDK nainstaluje odpovídající modul runtime.</span><span class="sxs-lookup"><span data-stu-id="9d88f-107">Installing an SDK installs the corresponding runtime.</span></span>

<span data-ttu-id="9d88f-108">Pokud některý z příkazů v tomto článku neproběhne úspěšně, nemáte nainstalovaný modul runtime nebo sadu SDK.</span><span class="sxs-lookup"><span data-stu-id="9d88f-108">If any command in this article fails, you don't have the runtime or SDK installed.</span></span> <span data-ttu-id="9d88f-109">Další informace najdete v článcích věnovaném instalaci pro [Windows](windows.md), [MacOS](macos.md)nebo [Linux](linux.md).</span><span class="sxs-lookup"><span data-stu-id="9d88f-109">For more information, see the install articles for [Windows](windows.md), [macOS](macos.md), or [Linux](linux.md).</span></span>

## <a name="check-sdk-versions"></a><span data-ttu-id="9d88f-110">Kontrolovat verze sady SDK</span><span class="sxs-lookup"><span data-stu-id="9d88f-110">Check SDK versions</span></span>

<span data-ttu-id="9d88f-111">Můžete si prohlédnout, které verze .NET Core SDK jsou aktuálně nainstalovány s terminálem.</span><span class="sxs-lookup"><span data-stu-id="9d88f-111">You can see which versions of the .NET Core SDK are currently installed with a terminal.</span></span> <span data-ttu-id="9d88f-112">Otevřete terminál a spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="9d88f-112">Open a terminal and run the following command.</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="9d88f-113">Zobrazí se výstup podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="9d88f-113">You get output similar to the following.</span></span>

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

## <a name="check-runtime-versions"></a><span data-ttu-id="9d88f-114">Kontrolovat verze modulu runtime</span><span class="sxs-lookup"><span data-stu-id="9d88f-114">Check runtime versions</span></span>

<span data-ttu-id="9d88f-115">Verze modulu runtime .NET Core, které jsou aktuálně nainstalovány, můžete zobrazit pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="9d88f-115">You can see which versions of the .NET Core runtime are currently installed with the following command.</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="9d88f-116">Zobrazí se výstup podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="9d88f-116">You get output similar to the following.</span></span>

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

## <a name="check-for-install-folders"></a><span data-ttu-id="9d88f-117">Vyhledat složky pro instalaci</span><span class="sxs-lookup"><span data-stu-id="9d88f-117">Check for install folders</span></span>

<span data-ttu-id="9d88f-118">Je možné, že je rozhraní .NET Core nainstalované, ale není přidané do `PATH` proměnné pro váš operační systém nebo profil uživatele.</span><span class="sxs-lookup"><span data-stu-id="9d88f-118">It's possible that .NET Core is installed but not added to the `PATH` variable for your operating system or user profile.</span></span> <span data-ttu-id="9d88f-119">Spuštění příkazů z předchozích sekcí nemusí fungovat.</span><span class="sxs-lookup"><span data-stu-id="9d88f-119">Running the commands from the previous sections may not work.</span></span> <span data-ttu-id="9d88f-120">Alternativně můžete ověřit, zda existují instalační složky rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9d88f-120">As an alternative, you can check that the .NET Core install folders exist.</span></span>

<span data-ttu-id="9d88f-121">Když instalujete .NET Core z instalačního programu nebo skriptu, nainstaluje se do složky Standard.</span><span class="sxs-lookup"><span data-stu-id="9d88f-121">When you install .NET Core from an installer or script, it's installed to a standard folder.</span></span> <span data-ttu-id="9d88f-122">Většinu času instalačního programu nebo skriptu, který používáte k instalaci .NET Core, vám dává možnost nainstalovat do jiné složky.</span><span class="sxs-lookup"><span data-stu-id="9d88f-122">Much of the time the installer or script you're using to install .NET Core gives you an option to install to a different folder.</span></span> <span data-ttu-id="9d88f-123">Pokud se rozhodnete nainstalovat do jiné složky, upravte začátek cesty ke složce.</span><span class="sxs-lookup"><span data-stu-id="9d88f-123">If you choose to install to a different folder, adjust the start of the folder path.</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="9d88f-124">**dotnet – spustitelný soubor**</span><span class="sxs-lookup"><span data-stu-id="9d88f-124">**dotnet executable**</span></span>\
<span data-ttu-id="9d88f-125">_C: \\ Program Files \\ dotnet \\dotnet.exe_</span><span class="sxs-lookup"><span data-stu-id="9d88f-125">_C:\\program files\\dotnet\\dotnet.exe_</span></span>

- <span data-ttu-id="9d88f-126">**SADA .NET SDK**</span><span class="sxs-lookup"><span data-stu-id="9d88f-126">**.NET SDK**</span></span>\
<span data-ttu-id="9d88f-127">_C: \\ Program Files \\ dotnet \\ SDK \\ {Version}\\_</span><span class="sxs-lookup"><span data-stu-id="9d88f-127">_C:\\program files\\dotnet\\sdk\\{version}\\_</span></span>

- <span data-ttu-id="9d88f-128">**Modul runtime .NET**</span><span class="sxs-lookup"><span data-stu-id="9d88f-128">**.NET Runtime**</span></span>\
<span data-ttu-id="9d88f-129">_C: \\ Program Files \\ dotnet \\ Shared \\ {runtime-Type} \\ {Version}\\_</span><span class="sxs-lookup"><span data-stu-id="9d88f-129">_C:\\program files\\dotnet\\shared\\{runtime-type}\\{version}\\_</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="9d88f-130">**dotnet – spustitelný soubor**</span><span class="sxs-lookup"><span data-stu-id="9d88f-130">**dotnet executable**</span></span>\
<span data-ttu-id="9d88f-131">_/home/user/share/dotnet/dotnet_</span><span class="sxs-lookup"><span data-stu-id="9d88f-131">_/home/user/share/dotnet/dotnet_</span></span>

- <span data-ttu-id="9d88f-132">**SADA .NET SDK**</span><span class="sxs-lookup"><span data-stu-id="9d88f-132">**.NET SDK**</span></span>\
<span data-ttu-id="9d88f-133">_/home/user/share/dotnet/sdk/{version}/_</span><span class="sxs-lookup"><span data-stu-id="9d88f-133">_/home/user/share/dotnet/sdk/{version}/_</span></span>

- <span data-ttu-id="9d88f-134">**Modul runtime .NET**</span><span class="sxs-lookup"><span data-stu-id="9d88f-134">**.NET Runtime**</span></span>\
<span data-ttu-id="9d88f-135">_/home/user/share/dotnet/shared/{runtime-type}/{version}/_</span><span class="sxs-lookup"><span data-stu-id="9d88f-135">_/home/user/share/dotnet/shared/{runtime-type}/{version}/_</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="9d88f-136">**dotnet – spustitelný soubor**</span><span class="sxs-lookup"><span data-stu-id="9d88f-136">**dotnet executable**</span></span>\
<span data-ttu-id="9d88f-137">_/usr/local/share/dotnet/dotnet_</span><span class="sxs-lookup"><span data-stu-id="9d88f-137">_/usr/local/share/dotnet/dotnet_</span></span>

- <span data-ttu-id="9d88f-138">**SADA .NET SDK**</span><span class="sxs-lookup"><span data-stu-id="9d88f-138">**.NET SDK**</span></span>\
<span data-ttu-id="9d88f-139">_/usr/local/share/dotnet/sdk/{version}/_</span><span class="sxs-lookup"><span data-stu-id="9d88f-139">_/usr/local/share/dotnet/sdk/{version}/_</span></span>

- <span data-ttu-id="9d88f-140">**Modul runtime .NET**</span><span class="sxs-lookup"><span data-stu-id="9d88f-140">**.NET Runtime**</span></span>\
<span data-ttu-id="9d88f-141">_/usr/local/share/dotnet/shared/{runtime-type}/{version}/_</span><span class="sxs-lookup"><span data-stu-id="9d88f-141">_/usr/local/share/dotnet/shared/{runtime-type}/{version}/_</span></span>

::: zone-end

## <a name="more-information"></a><span data-ttu-id="9d88f-142">Další informace</span><span class="sxs-lookup"><span data-stu-id="9d88f-142">More information</span></span>

<span data-ttu-id="9d88f-143">Verze SDK a běhové verze můžete zobrazit pomocí příkazu `dotnet --info` .</span><span class="sxs-lookup"><span data-stu-id="9d88f-143">You can see both the SDK versions and runtime versions with the command `dotnet --info`.</span></span> <span data-ttu-id="9d88f-144">Získáte i další informace související s prostředím, jako je například verze operačního systému a identifikátor modulu runtime (RID).</span><span class="sxs-lookup"><span data-stu-id="9d88f-144">You'll also get other environmental related information, such as the operating system version and runtime identifier (RID).</span></span>

## <a name="next-steps"></a><span data-ttu-id="9d88f-145">Další kroky</span><span class="sxs-lookup"><span data-stu-id="9d88f-145">Next steps</span></span>

- <span data-ttu-id="9d88f-146">[Nainstalujte modul runtime .NET Core](runtime.md).</span><span class="sxs-lookup"><span data-stu-id="9d88f-146">[Install the .NET Core Runtime](runtime.md).</span></span>
- <span data-ttu-id="9d88f-147">[Nainstalujte .NET Core SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="9d88f-147">[Install the .NET Core SDK](sdk.md).</span></span>
