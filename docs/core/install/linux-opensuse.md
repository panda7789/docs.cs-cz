---
title: Instalace .NET Core na openSUSE – .NET Core
description: Ukazuje různé způsoby, jak nainstalovat .NET Core SDK a modul runtime .NET Core v openSUSE.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 24f0a5b5278d038c2f941b0984efcacd91dcbe31
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619465"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-opensuse"></a><span data-ttu-id="11092-103">Instalace .NET Core SDK nebo modulu runtime .NET Core v openSUSE</span><span class="sxs-lookup"><span data-stu-id="11092-103">Install .NET Core SDK or .NET Core Runtime on openSUSE</span></span>

<span data-ttu-id="11092-104">Rozhraní .NET Core je podporováno v openSUSE.</span><span class="sxs-lookup"><span data-stu-id="11092-104">.NET Core is supported on openSUSE.</span></span> <span data-ttu-id="11092-105">Tento článek popisuje, jak nainstalovat .NET Core na openSUSE.</span><span class="sxs-lookup"><span data-stu-id="11092-105">This article describes how to install .NET Core on openSUSE.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="11092-106">Podporované distribuce</span><span class="sxs-lookup"><span data-stu-id="11092-106">Supported distributions</span></span>

<span data-ttu-id="11092-107">Následující tabulka uvádí seznam aktuálně podporovaných vydání .NET Core na openSUSE 15.</span><span class="sxs-lookup"><span data-stu-id="11092-107">The following table is a list of currently supported .NET Core releases on openSUSE 15.</span></span> <span data-ttu-id="11092-108">Tato verze zůstane podporovaná, dokud [nedosáhne žádné verze rozhraní .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) nebo pokud není podporovaná verze openSUSE.</span><span class="sxs-lookup"><span data-stu-id="11092-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of openSUSE is no longer supported.</span></span>

- <span data-ttu-id="11092-109">✔️ označuje, že je stále podporovaná verze openSUSE nebo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="11092-109">A ✔️ indicates that the version of openSUSE or .NET Core is still supported.</span></span>
- <span data-ttu-id="11092-110">❌Indikuje, že verze openSUSE nebo .NET Core není v této verzi openSUSE podporována.</span><span class="sxs-lookup"><span data-stu-id="11092-110">A ❌ indicates that the version of openSUSE or .NET Core isn't supported on that openSUSE release.</span></span>
- <span data-ttu-id="11092-111">Pokud se ✔️á jak verze openSUSE, tak i verze .NET Core, je podporovaná kombinace operačních systémů a .NET.</span><span class="sxs-lookup"><span data-stu-id="11092-111">When both a version of openSUSE and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="11092-112">openSUSE</span><span class="sxs-lookup"><span data-stu-id="11092-112">openSUSE</span></span>                   | <span data-ttu-id="11092-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="11092-113">.NET Core 2.1</span></span> | <span data-ttu-id="11092-114">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="11092-114">.NET Core 3.1</span></span> | <span data-ttu-id="11092-115">.NET 5 Preview (jenom ruční instalace)</span><span class="sxs-lookup"><span data-stu-id="11092-115">.NET 5 Preview (manual install only)</span></span> |
|----------------------------|---------------|---------------|----------------|
| <span data-ttu-id="11092-116">✔️ [15](#opensuse-15-)</span><span class="sxs-lookup"><span data-stu-id="11092-116">✔️ [15](#opensuse-15-)</span></span>     | <span data-ttu-id="11092-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="11092-117">✔️ 2.1</span></span>        | <span data-ttu-id="11092-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="11092-118">✔️ 3.1</span></span>        | <span data-ttu-id="11092-119">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="11092-119">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="11092-120">Následující verze rozhraní .NET Core již nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="11092-120">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="11092-121">Soubory ke stažení pro tyto soubory zůstanou publikované:</span><span class="sxs-lookup"><span data-stu-id="11092-121">The downloads for these still remain published:</span></span>

- <span data-ttu-id="11092-122">3.0</span><span class="sxs-lookup"><span data-stu-id="11092-122">3.0</span></span>
- <span data-ttu-id="11092-123">2,2</span><span class="sxs-lookup"><span data-stu-id="11092-123">2.2</span></span>
- <span data-ttu-id="11092-124">2.0</span><span class="sxs-lookup"><span data-stu-id="11092-124">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="11092-125">Jak nainstalovat další verze</span><span class="sxs-lookup"><span data-stu-id="11092-125">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="opensuse-15-"></a><span data-ttu-id="11092-126">openSUSE 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="11092-126">openSUSE 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="11092-127">Řešení potíží se správcem balíčků</span><span class="sxs-lookup"><span data-stu-id="11092-127">Troubleshoot the package manager</span></span>

<span data-ttu-id="11092-128">V této části najdete informace o běžných chybách, ke kterým může dojít při použití Správce balíčků k instalaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="11092-128">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="11092-129">Nepovedlo se načíst</span><span class="sxs-lookup"><span data-stu-id="11092-129">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="11092-130">Moduly snap</span><span class="sxs-lookup"><span data-stu-id="11092-130">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="11092-131">Závislosti</span><span class="sxs-lookup"><span data-stu-id="11092-131">Dependencies</span></span>

<span data-ttu-id="11092-132">Při instalaci nástroje pomocí Správce balíčků se tyto knihovny nainstalují za vás.</span><span class="sxs-lookup"><span data-stu-id="11092-132">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="11092-133">Pokud ale ručně nainstalujete rozhraní .NET Core nebo publikujete samostatnou aplikaci, musíte se ujistit, že jsou nainstalované tyto knihovny:</span><span class="sxs-lookup"><span data-stu-id="11092-133">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="11092-134">krb5</span><span class="sxs-lookup"><span data-stu-id="11092-134">krb5</span></span>
- <span data-ttu-id="11092-135">libicu</span><span class="sxs-lookup"><span data-stu-id="11092-135">libicu</span></span>
- <span data-ttu-id="11092-136">libopenssl1_0_0</span><span class="sxs-lookup"><span data-stu-id="11092-136">libopenssl1_0_0</span></span>

<span data-ttu-id="11092-137">Pokud je verze OpenSSL cílového běhového prostředí 1,1 nebo novější, budete muset nainstalovat **kompatibilní openssl10**.</span><span class="sxs-lookup"><span data-stu-id="11092-137">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="11092-138">Další informace o závislostech najdete v tématu [samostatné aplikace pro Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="11092-138">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="11092-139">Pro aplikace .NET Core, které používají sestavení *System. Drawing. Common* , budete také potřebovat následující závislost:</span><span class="sxs-lookup"><span data-stu-id="11092-139">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="11092-140">libgdiplus (verze 6.0.1 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="11092-140">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="11092-141">Můžete nainstalovat nejnovější verzi *libgdiplus* přidáním úložiště mono do systému.</span><span class="sxs-lookup"><span data-stu-id="11092-141">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="11092-142">Další informace naleznete v tématu <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="11092-142">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="11092-143">Skriptovaná instalace</span><span class="sxs-lookup"><span data-stu-id="11092-143">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="11092-144">Ruční instalace</span><span class="sxs-lookup"><span data-stu-id="11092-144">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="11092-145">Další kroky</span><span class="sxs-lookup"><span data-stu-id="11092-145">Next steps</span></span>

- [<span data-ttu-id="11092-146">Kurz: Vytvoření konzolové aplikace s .NET Core SDK pomocí Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="11092-146">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
