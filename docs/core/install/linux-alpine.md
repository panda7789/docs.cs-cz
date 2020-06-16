---
title: Nainstalovat .NET Core na alpské – .NET Core
description: Ukazuje různé způsoby, jak nainstalovat .NET Core SDK a modul runtime .NET Core v alpské.
author: thraka
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: bbaf4ee9020dcd33c894b5376bf04ad65db8d378
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84771501"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-alpine"></a><span data-ttu-id="c48a7-103">Nainstalovat .NET Core SDK nebo modul runtime .NET Core v alpské</span><span class="sxs-lookup"><span data-stu-id="c48a7-103">Install .NET Core SDK or .NET Core Runtime on Alpine</span></span>

<span data-ttu-id="c48a7-104">Tento článek popisuje, jak nainstalovat .NET Core na alpské.</span><span class="sxs-lookup"><span data-stu-id="c48a7-104">This article describes how to install .NET Core on Alpine.</span></span> <span data-ttu-id="c48a7-105">V případě, že se v alpské verzi nedostává podpora, .NET Core už tuto verzi nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="c48a7-105">When a Alpine version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="c48a7-106">Tyto pokyny vám ale můžou usnadnit práci s .NET Core na těchto verzích, i když není podporovaná.</span><span class="sxs-lookup"><span data-stu-id="c48a7-106">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

<span data-ttu-id="c48a7-107">Pro Alpine nejsou k dispozici žádní instalační programy.</span><span class="sxs-lookup"><span data-stu-id="c48a7-107">There are no installers for Alpine.</span></span> <span data-ttu-id="c48a7-108">Musíte buď použít [instalační skript](#scripted-install) , nebo postupovat podle pokynů k [ruční instalaci](#manual-install) .</span><span class="sxs-lookup"><span data-stu-id="c48a7-108">You must either use the [install script](#scripted-install) or follow the [manual install](#manual-install) instructions.</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="c48a7-109">Podporované distribuce</span><span class="sxs-lookup"><span data-stu-id="c48a7-109">Supported distributions</span></span>

<span data-ttu-id="c48a7-110">Následující tabulka uvádí seznam aktuálně podporovaných vydání .NET Core a verze alpské, na kterých jsou podporované.</span><span class="sxs-lookup"><span data-stu-id="c48a7-110">The following table is a list of currently supported .NET Core releases and the versions of Alpine they're supported on.</span></span> <span data-ttu-id="c48a7-111">Tyto verze zůstanou podporované, dokud verze [.NET Core nedosáhne konce podpory](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) nebo když verze [alpské dosáhne konce životnosti](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span><span class="sxs-lookup"><span data-stu-id="c48a7-111">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Alpine reaches end-of-life](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span></span>

- <span data-ttu-id="c48a7-112">✔️ označuje, že verze Alpine nebo .NET Core je stále podporovaná.</span><span class="sxs-lookup"><span data-stu-id="c48a7-112">A ✔️ indicates that the version of Alpine or .NET Core is still supported.</span></span>
- <span data-ttu-id="c48a7-113">❌Indikuje, že verze Alpine nebo .NET Core není v této alpské verzi podporovaná.</span><span class="sxs-lookup"><span data-stu-id="c48a7-113">A ❌ indicates that the version of Alpine or .NET Core isn't supported on that Alpine release.</span></span>
- <span data-ttu-id="c48a7-114">Pokud se ✔️á jak verze Alpine, tak i verze .NET Core, je podporovaná kombinace operačních systémů a .NET.</span><span class="sxs-lookup"><span data-stu-id="c48a7-114">When both a version of Alpine and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="c48a7-115">Alpine</span><span class="sxs-lookup"><span data-stu-id="c48a7-115">Alpine</span></span>                   | <span data-ttu-id="c48a7-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="c48a7-116">.NET Core 2.1</span></span> | <span data-ttu-id="c48a7-117">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="c48a7-117">.NET Core 3.1</span></span> | <span data-ttu-id="c48a7-118">.NET 5 Preview</span><span class="sxs-lookup"><span data-stu-id="c48a7-118">.NET 5 Preview</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="c48a7-119">✔️ 3,12</span><span class="sxs-lookup"><span data-stu-id="c48a7-119">✔️ 3.12</span></span>  | <span data-ttu-id="c48a7-120">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="c48a7-120">✔️ 2.1</span></span>        | <span data-ttu-id="c48a7-121">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="c48a7-121">✔️ 3.1</span></span>        | <span data-ttu-id="c48a7-122">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="c48a7-122">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="c48a7-123">✔️ 3,11</span><span class="sxs-lookup"><span data-stu-id="c48a7-123">✔️ 3.11</span></span>  | <span data-ttu-id="c48a7-124">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="c48a7-124">✔️ 2.1</span></span>        | <span data-ttu-id="c48a7-125">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="c48a7-125">✔️ 3.1</span></span>        | <span data-ttu-id="c48a7-126">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="c48a7-126">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="c48a7-127">✔️ 3,10</span><span class="sxs-lookup"><span data-stu-id="c48a7-127">✔️ 3.10</span></span>  | <span data-ttu-id="c48a7-128">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="c48a7-128">✔️ 2.1</span></span>        | <span data-ttu-id="c48a7-129">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="c48a7-129">✔️ 3.1</span></span>        | <span data-ttu-id="c48a7-130">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="c48a7-130">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="c48a7-131">✔️ 3,9</span><span class="sxs-lookup"><span data-stu-id="c48a7-131">✔️ 3.9</span></span>   | <span data-ttu-id="c48a7-132">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="c48a7-132">✔️ 2.1</span></span>        | <span data-ttu-id="c48a7-133">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="c48a7-133">✔️ 3.1</span></span>        | <span data-ttu-id="c48a7-134">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="c48a7-134">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="c48a7-135">❌3,8</span><span class="sxs-lookup"><span data-stu-id="c48a7-135">❌ 3.8</span></span>   | <span data-ttu-id="c48a7-136">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="c48a7-136">✔️ 2.1</span></span>        | <span data-ttu-id="c48a7-137">❌3,1</span><span class="sxs-lookup"><span data-stu-id="c48a7-137">❌ 3.1</span></span>        | <span data-ttu-id="c48a7-138">❌5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="c48a7-138">❌ 5.0 Preview</span></span> |

<span data-ttu-id="c48a7-139">Následující verze rozhraní .NET Core již nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="c48a7-139">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="c48a7-140">Soubory ke stažení pro tyto soubory zůstanou publikované:</span><span class="sxs-lookup"><span data-stu-id="c48a7-140">The downloads for these still remain published:</span></span>

- <span data-ttu-id="c48a7-141">3.0</span><span class="sxs-lookup"><span data-stu-id="c48a7-141">3.0</span></span>
- <span data-ttu-id="c48a7-142">2,2</span><span class="sxs-lookup"><span data-stu-id="c48a7-142">2.2</span></span>
- <span data-ttu-id="c48a7-143">2.0</span><span class="sxs-lookup"><span data-stu-id="c48a7-143">2.0</span></span>

## <a name="dependencies"></a><span data-ttu-id="c48a7-144">Závislosti</span><span class="sxs-lookup"><span data-stu-id="c48a7-144">Dependencies</span></span>

<span data-ttu-id="c48a7-145">.NET Core v systému Alpine Linux vyžaduje nainstalované následující závislosti:</span><span class="sxs-lookup"><span data-stu-id="c48a7-145">.NET Core on Alpine Linux requires the following dependencies installed:</span></span>

- <span data-ttu-id="c48a7-146">ICU – knihovny</span><span class="sxs-lookup"><span data-stu-id="c48a7-146">icu-libs</span></span>
- <span data-ttu-id="c48a7-147">krb5 – knihovny</span><span class="sxs-lookup"><span data-stu-id="c48a7-147">krb5-libs</span></span>
- <span data-ttu-id="c48a7-148">libintl</span><span class="sxs-lookup"><span data-stu-id="c48a7-148">libintl</span></span>
- <span data-ttu-id="c48a7-149">libssl 1.1 (Alpine v 3.9 nebo vyšší)</span><span class="sxs-lookup"><span data-stu-id="c48a7-149">libssl1.1 (Alpine v3.9 or greater)</span></span>
- <span data-ttu-id="c48a7-150">libssl 1.0 (Alpine v 3.8)</span><span class="sxs-lookup"><span data-stu-id="c48a7-150">libssl1.0 (Alpine v3.8)</span></span>
- <span data-ttu-id="c48a7-151">libstdc + +</span><span class="sxs-lookup"><span data-stu-id="c48a7-151">libstdc++</span></span>
- <span data-ttu-id="c48a7-152">lttng – tým UST</span><span class="sxs-lookup"><span data-stu-id="c48a7-152">lttng-ust</span></span>
- <span data-ttu-id="c48a7-153">numactl (volitelné)</span><span class="sxs-lookup"><span data-stu-id="c48a7-153">numactl (optional)</span></span>
- <span data-ttu-id="c48a7-154">ZLIB</span><span class="sxs-lookup"><span data-stu-id="c48a7-154">zlib</span></span>

## <a name="scripted-install"></a><span data-ttu-id="c48a7-155">Skriptovaná instalace</span><span class="sxs-lookup"><span data-stu-id="c48a7-155">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="c48a7-156">Ruční instalace</span><span class="sxs-lookup"><span data-stu-id="c48a7-156">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="c48a7-157">Další kroky</span><span class="sxs-lookup"><span data-stu-id="c48a7-157">Next steps</span></span>

- [<span data-ttu-id="c48a7-158">Kurz: Vytvoření konzolové aplikace s .NET Core SDK pomocí Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c48a7-158">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
