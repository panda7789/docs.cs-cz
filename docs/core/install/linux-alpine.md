---
title: Nainstalovat .NET Core na alpské – .NET Core
description: Ukazuje různé způsoby, jak nainstalovat .NET Core SDK a modul runtime .NET Core v alpské.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 92753933cbcedae28867b66293d1044f700d7baa
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324828"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-alpine"></a><span data-ttu-id="736b8-103">Nainstalovat .NET Core SDK nebo modul runtime .NET Core v alpské</span><span class="sxs-lookup"><span data-stu-id="736b8-103">Install .NET Core SDK or .NET Core Runtime on Alpine</span></span>

<span data-ttu-id="736b8-104">Tento článek popisuje, jak nainstalovat .NET Core na alpské.</span><span class="sxs-lookup"><span data-stu-id="736b8-104">This article describes how to install .NET Core on Alpine.</span></span> <span data-ttu-id="736b8-105">V případě, že se v alpské verzi nedostává podpora, .NET Core už tuto verzi nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="736b8-105">When a Alpine version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="736b8-106">Tyto pokyny vám ale můžou usnadnit práci s .NET Core na těchto verzích, i když není podporovaná.</span><span class="sxs-lookup"><span data-stu-id="736b8-106">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

<span data-ttu-id="736b8-107">Pro Alpine nejsou k dispozici žádní instalační programy.</span><span class="sxs-lookup"><span data-stu-id="736b8-107">There are no installers for Alpine.</span></span> <span data-ttu-id="736b8-108">Musíte buď použít [instalační skript](#scripted-install) , nebo postupovat podle pokynů k [ruční instalaci](#manual-install) .</span><span class="sxs-lookup"><span data-stu-id="736b8-108">You must either use the [install script](#scripted-install) or follow the [manual install](#manual-install) instructions.</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="736b8-109">Podporované distribuce</span><span class="sxs-lookup"><span data-stu-id="736b8-109">Supported distributions</span></span>

<span data-ttu-id="736b8-110">Následující tabulka uvádí seznam aktuálně podporovaných vydání .NET Core a verze alpské, na kterých jsou podporované.</span><span class="sxs-lookup"><span data-stu-id="736b8-110">The following table is a list of currently supported .NET Core releases and the versions of Alpine they're supported on.</span></span> <span data-ttu-id="736b8-111">Tyto verze zůstanou podporované, dokud verze [.NET Core nedosáhne konce podpory](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) nebo když verze [alpské dosáhne konce životnosti](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span><span class="sxs-lookup"><span data-stu-id="736b8-111">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Alpine reaches end-of-life](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span></span>

- <span data-ttu-id="736b8-112">✔️ označuje, že verze Alpine nebo .NET Core je stále podporovaná.</span><span class="sxs-lookup"><span data-stu-id="736b8-112">A ✔️ indicates that the version of Alpine or .NET Core is still supported.</span></span>
- <span data-ttu-id="736b8-113">❌Indikuje, že verze Alpine nebo .NET Core není v této alpské verzi podporovaná.</span><span class="sxs-lookup"><span data-stu-id="736b8-113">A ❌ indicates that the version of Alpine or .NET Core isn't supported on that Alpine release.</span></span>
- <span data-ttu-id="736b8-114">Pokud se ✔️á jak verze Alpine, tak i verze .NET Core, je podporovaná kombinace operačních systémů a .NET.</span><span class="sxs-lookup"><span data-stu-id="736b8-114">When both a version of Alpine and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="736b8-115">Alpine</span><span class="sxs-lookup"><span data-stu-id="736b8-115">Alpine</span></span>                   | <span data-ttu-id="736b8-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="736b8-116">.NET Core 2.1</span></span> | <span data-ttu-id="736b8-117">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="736b8-117">.NET Core 3.1</span></span> | <span data-ttu-id="736b8-118">.NET 5 Preview</span><span class="sxs-lookup"><span data-stu-id="736b8-118">.NET 5 Preview</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="736b8-119">✔️ 3,12</span><span class="sxs-lookup"><span data-stu-id="736b8-119">✔️ 3.12</span></span>  | <span data-ttu-id="736b8-120">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="736b8-120">✔️ 2.1</span></span>        | <span data-ttu-id="736b8-121">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="736b8-121">✔️ 3.1</span></span>        | <span data-ttu-id="736b8-122">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="736b8-122">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="736b8-123">✔️ 3,11</span><span class="sxs-lookup"><span data-stu-id="736b8-123">✔️ 3.11</span></span>  | <span data-ttu-id="736b8-124">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="736b8-124">✔️ 2.1</span></span>        | <span data-ttu-id="736b8-125">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="736b8-125">✔️ 3.1</span></span>        | <span data-ttu-id="736b8-126">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="736b8-126">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="736b8-127">✔️ 3,10</span><span class="sxs-lookup"><span data-stu-id="736b8-127">✔️ 3.10</span></span>  | <span data-ttu-id="736b8-128">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="736b8-128">✔️ 2.1</span></span>        | <span data-ttu-id="736b8-129">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="736b8-129">✔️ 3.1</span></span>        | <span data-ttu-id="736b8-130">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="736b8-130">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="736b8-131">✔️ 3,9</span><span class="sxs-lookup"><span data-stu-id="736b8-131">✔️ 3.9</span></span>   | <span data-ttu-id="736b8-132">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="736b8-132">✔️ 2.1</span></span>        | <span data-ttu-id="736b8-133">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="736b8-133">✔️ 3.1</span></span>        | <span data-ttu-id="736b8-134">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="736b8-134">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="736b8-135">❌3,8</span><span class="sxs-lookup"><span data-stu-id="736b8-135">❌ 3.8</span></span>   | <span data-ttu-id="736b8-136">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="736b8-136">✔️ 2.1</span></span>        | <span data-ttu-id="736b8-137">❌3,1</span><span class="sxs-lookup"><span data-stu-id="736b8-137">❌ 3.1</span></span>        | <span data-ttu-id="736b8-138">❌5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="736b8-138">❌ 5.0 Preview</span></span> |

<span data-ttu-id="736b8-139">Následující verze rozhraní .NET Core již nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="736b8-139">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="736b8-140">Soubory ke stažení pro tyto soubory zůstanou publikované:</span><span class="sxs-lookup"><span data-stu-id="736b8-140">The downloads for these still remain published:</span></span>

- <span data-ttu-id="736b8-141">3.0</span><span class="sxs-lookup"><span data-stu-id="736b8-141">3.0</span></span>
- <span data-ttu-id="736b8-142">2,2</span><span class="sxs-lookup"><span data-stu-id="736b8-142">2.2</span></span>
- <span data-ttu-id="736b8-143">2.0</span><span class="sxs-lookup"><span data-stu-id="736b8-143">2.0</span></span>

## <a name="dependencies"></a><span data-ttu-id="736b8-144">Závislosti</span><span class="sxs-lookup"><span data-stu-id="736b8-144">Dependencies</span></span>

<span data-ttu-id="736b8-145">.NET Core v systému Alpine Linux vyžaduje nainstalované následující závislosti:</span><span class="sxs-lookup"><span data-stu-id="736b8-145">.NET Core on Alpine Linux requires the following dependencies installed:</span></span>

- <span data-ttu-id="736b8-146">ICU – knihovny</span><span class="sxs-lookup"><span data-stu-id="736b8-146">icu-libs</span></span>
- <span data-ttu-id="736b8-147">krb5 – knihovny</span><span class="sxs-lookup"><span data-stu-id="736b8-147">krb5-libs</span></span>
- <span data-ttu-id="736b8-148">libintl</span><span class="sxs-lookup"><span data-stu-id="736b8-148">libintl</span></span>
- <span data-ttu-id="736b8-149">libssl 1.1 (Alpine v 3.9 nebo vyšší)</span><span class="sxs-lookup"><span data-stu-id="736b8-149">libssl1.1 (Alpine v3.9 or greater)</span></span>
- <span data-ttu-id="736b8-150">libssl 1.0 (Alpine v 3.8)</span><span class="sxs-lookup"><span data-stu-id="736b8-150">libssl1.0 (Alpine v3.8)</span></span>
- <span data-ttu-id="736b8-151">libstdc + +</span><span class="sxs-lookup"><span data-stu-id="736b8-151">libstdc++</span></span>
- <span data-ttu-id="736b8-152">lttng – tým UST</span><span class="sxs-lookup"><span data-stu-id="736b8-152">lttng-ust</span></span>
- <span data-ttu-id="736b8-153">numactl (volitelné)</span><span class="sxs-lookup"><span data-stu-id="736b8-153">numactl (optional)</span></span>
- <span data-ttu-id="736b8-154">ZLIB</span><span class="sxs-lookup"><span data-stu-id="736b8-154">zlib</span></span>

## <a name="scripted-install"></a><span data-ttu-id="736b8-155">Skriptovaná instalace</span><span class="sxs-lookup"><span data-stu-id="736b8-155">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="736b8-156">Ruční instalace</span><span class="sxs-lookup"><span data-stu-id="736b8-156">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="736b8-157">Další kroky</span><span class="sxs-lookup"><span data-stu-id="736b8-157">Next steps</span></span>

- [<span data-ttu-id="736b8-158">Kurz: Vytvoření konzolové aplikace s .NET Core SDK pomocí Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="736b8-158">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
