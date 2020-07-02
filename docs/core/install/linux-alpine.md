---
title: Nainstalovat .NET Core na alpské – .NET Core
description: Ukazuje různé způsoby, jak nainstalovat .NET Core SDK a modul runtime .NET Core v alpské.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 0efe3bbacbe573b77eae8818ea29b5a3867e4570
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619517"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-alpine"></a><span data-ttu-id="cd173-103">Nainstalovat .NET Core SDK nebo modul runtime .NET Core v alpské</span><span class="sxs-lookup"><span data-stu-id="cd173-103">Install .NET Core SDK or .NET Core Runtime on Alpine</span></span>

<span data-ttu-id="cd173-104">Tento článek popisuje, jak nainstalovat .NET Core na alpské.</span><span class="sxs-lookup"><span data-stu-id="cd173-104">This article describes how to install .NET Core on Alpine.</span></span> <span data-ttu-id="cd173-105">V případě, že se v alpské verzi nedostává podpora, .NET Core už tuto verzi nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="cd173-105">When a Alpine version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="cd173-106">Tyto pokyny vám ale můžou usnadnit práci s .NET Core na těchto verzích, i když není podporovaná.</span><span class="sxs-lookup"><span data-stu-id="cd173-106">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

<span data-ttu-id="cd173-107">Pro Alpine nejsou k dispozici žádní instalační programy.</span><span class="sxs-lookup"><span data-stu-id="cd173-107">There are no installers for Alpine.</span></span> <span data-ttu-id="cd173-108">Musíte buď použít [instalační skript](#scripted-install) , nebo postupovat podle pokynů k [ruční instalaci](#manual-install) .</span><span class="sxs-lookup"><span data-stu-id="cd173-108">You must either use the [install script](#scripted-install) or follow the [manual install](#manual-install) instructions.</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="cd173-109">Podporované distribuce</span><span class="sxs-lookup"><span data-stu-id="cd173-109">Supported distributions</span></span>

<span data-ttu-id="cd173-110">Následující tabulka uvádí seznam aktuálně podporovaných vydání .NET Core a verze alpské, na kterých jsou podporované.</span><span class="sxs-lookup"><span data-stu-id="cd173-110">The following table is a list of currently supported .NET Core releases and the versions of Alpine they're supported on.</span></span> <span data-ttu-id="cd173-111">Tyto verze zůstanou podporované, dokud verze [.NET Core nedosáhne konce podpory](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) nebo když verze [alpské dosáhne konce životnosti](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span><span class="sxs-lookup"><span data-stu-id="cd173-111">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Alpine reaches end-of-life](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span></span>

- <span data-ttu-id="cd173-112">✔️ označuje, že verze Alpine nebo .NET Core je stále podporovaná.</span><span class="sxs-lookup"><span data-stu-id="cd173-112">A ✔️ indicates that the version of Alpine or .NET Core is still supported.</span></span>
- <span data-ttu-id="cd173-113">❌Indikuje, že verze Alpine nebo .NET Core není v této alpské verzi podporovaná.</span><span class="sxs-lookup"><span data-stu-id="cd173-113">A ❌ indicates that the version of Alpine or .NET Core isn't supported on that Alpine release.</span></span>
- <span data-ttu-id="cd173-114">Pokud se ✔️á jak verze Alpine, tak i verze .NET Core, je podporovaná kombinace operačních systémů a .NET.</span><span class="sxs-lookup"><span data-stu-id="cd173-114">When both a version of Alpine and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="cd173-115">Alpine</span><span class="sxs-lookup"><span data-stu-id="cd173-115">Alpine</span></span>                   | <span data-ttu-id="cd173-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="cd173-116">.NET Core 2.1</span></span> | <span data-ttu-id="cd173-117">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="cd173-117">.NET Core 3.1</span></span> | <span data-ttu-id="cd173-118">.NET 5 Preview</span><span class="sxs-lookup"><span data-stu-id="cd173-118">.NET 5 Preview</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="cd173-119">✔️ 3,12</span><span class="sxs-lookup"><span data-stu-id="cd173-119">✔️ 3.12</span></span>  | <span data-ttu-id="cd173-120">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="cd173-120">✔️ 2.1</span></span>        | <span data-ttu-id="cd173-121">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="cd173-121">✔️ 3.1</span></span>        | <span data-ttu-id="cd173-122">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="cd173-122">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="cd173-123">✔️ 3,11</span><span class="sxs-lookup"><span data-stu-id="cd173-123">✔️ 3.11</span></span>  | <span data-ttu-id="cd173-124">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="cd173-124">✔️ 2.1</span></span>        | <span data-ttu-id="cd173-125">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="cd173-125">✔️ 3.1</span></span>        | <span data-ttu-id="cd173-126">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="cd173-126">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="cd173-127">✔️ 3,10</span><span class="sxs-lookup"><span data-stu-id="cd173-127">✔️ 3.10</span></span>  | <span data-ttu-id="cd173-128">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="cd173-128">✔️ 2.1</span></span>        | <span data-ttu-id="cd173-129">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="cd173-129">✔️ 3.1</span></span>        | <span data-ttu-id="cd173-130">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="cd173-130">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="cd173-131">✔️ 3,9</span><span class="sxs-lookup"><span data-stu-id="cd173-131">✔️ 3.9</span></span>   | <span data-ttu-id="cd173-132">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="cd173-132">✔️ 2.1</span></span>        | <span data-ttu-id="cd173-133">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="cd173-133">✔️ 3.1</span></span>        | <span data-ttu-id="cd173-134">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="cd173-134">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="cd173-135">❌3,8</span><span class="sxs-lookup"><span data-stu-id="cd173-135">❌ 3.8</span></span>   | <span data-ttu-id="cd173-136">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="cd173-136">✔️ 2.1</span></span>        | <span data-ttu-id="cd173-137">❌3,1</span><span class="sxs-lookup"><span data-stu-id="cd173-137">❌ 3.1</span></span>        | <span data-ttu-id="cd173-138">❌5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="cd173-138">❌ 5.0 Preview</span></span> |

<span data-ttu-id="cd173-139">Následující verze rozhraní .NET Core již nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="cd173-139">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="cd173-140">Soubory ke stažení pro tyto soubory zůstanou publikované:</span><span class="sxs-lookup"><span data-stu-id="cd173-140">The downloads for these still remain published:</span></span>

- <span data-ttu-id="cd173-141">3.0</span><span class="sxs-lookup"><span data-stu-id="cd173-141">3.0</span></span>
- <span data-ttu-id="cd173-142">2,2</span><span class="sxs-lookup"><span data-stu-id="cd173-142">2.2</span></span>
- <span data-ttu-id="cd173-143">2.0</span><span class="sxs-lookup"><span data-stu-id="cd173-143">2.0</span></span>

## <a name="dependencies"></a><span data-ttu-id="cd173-144">Závislosti</span><span class="sxs-lookup"><span data-stu-id="cd173-144">Dependencies</span></span>

<span data-ttu-id="cd173-145">.NET Core v systému Alpine Linux vyžaduje nainstalované následující závislosti:</span><span class="sxs-lookup"><span data-stu-id="cd173-145">.NET Core on Alpine Linux requires the following dependencies installed:</span></span>

- <span data-ttu-id="cd173-146">ICU – knihovny</span><span class="sxs-lookup"><span data-stu-id="cd173-146">icu-libs</span></span>
- <span data-ttu-id="cd173-147">krb5 – knihovny</span><span class="sxs-lookup"><span data-stu-id="cd173-147">krb5-libs</span></span>
- <span data-ttu-id="cd173-148">libgcc</span><span class="sxs-lookup"><span data-stu-id="cd173-148">libgcc</span></span>
- <span data-ttu-id="cd173-149">libintl</span><span class="sxs-lookup"><span data-stu-id="cd173-149">libintl</span></span>
- <span data-ttu-id="cd173-150">libssl 1.1 (Alpine v 3.9 nebo vyšší)</span><span class="sxs-lookup"><span data-stu-id="cd173-150">libssl1.1 (Alpine v3.9 or greater)</span></span>
- <span data-ttu-id="cd173-151">libssl 1.0 (Alpine v 3.8 nebo nižší)</span><span class="sxs-lookup"><span data-stu-id="cd173-151">libssl1.0 (Alpine v3.8 or lower)</span></span>
- <span data-ttu-id="cd173-152">libstdc + +</span><span class="sxs-lookup"><span data-stu-id="cd173-152">libstdc++</span></span>
- <span data-ttu-id="cd173-153">ZLIB</span><span class="sxs-lookup"><span data-stu-id="cd173-153">zlib</span></span>

## <a name="scripted-install"></a><span data-ttu-id="cd173-154">Skriptovaná instalace</span><span class="sxs-lookup"><span data-stu-id="cd173-154">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="cd173-155">Ruční instalace</span><span class="sxs-lookup"><span data-stu-id="cd173-155">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="cd173-156">Další kroky</span><span class="sxs-lookup"><span data-stu-id="cd173-156">Next steps</span></span>

- [<span data-ttu-id="cd173-157">Kurz: Vytvoření konzolové aplikace s .NET Core SDK pomocí Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="cd173-157">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
