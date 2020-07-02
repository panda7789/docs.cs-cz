---
title: Instalace .NET Core na SLES – .NET Core
description: Ukazuje různé způsoby, jak nainstalovat .NET Core SDK a modul runtime .NET Core v SLES.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 8f64efcc8206b47855871104e5b6914570c06da0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619413"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-sles"></a><span data-ttu-id="9e741-103">Instalace .NET Core SDK nebo modulu runtime .NET Core v SLES</span><span class="sxs-lookup"><span data-stu-id="9e741-103">Install .NET Core SDK or .NET Core Runtime on SLES</span></span>

<span data-ttu-id="9e741-104">Rozhraní .NET Core je podporováno v SLES.</span><span class="sxs-lookup"><span data-stu-id="9e741-104">.NET Core is supported on SLES.</span></span> <span data-ttu-id="9e741-105">Tento článek popisuje, jak nainstalovat .NET Core na SLES.</span><span class="sxs-lookup"><span data-stu-id="9e741-105">This article describes how to install .NET Core on SLES.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="supported-distributions"></a><span data-ttu-id="9e741-106">Podporované distribuce</span><span class="sxs-lookup"><span data-stu-id="9e741-106">Supported distributions</span></span>

<span data-ttu-id="9e741-107">Následující tabulka uvádí seznam aktuálně podporovaných vydání .NET Core na SLES 12 SP2 a SLES 15.</span><span class="sxs-lookup"><span data-stu-id="9e741-107">The following table is a list of currently supported .NET Core releases on both SLES 12 SP2 and SLES 15.</span></span> <span data-ttu-id="9e741-108">Tato verze zůstane podporovaná, dokud [nedosáhne žádné verze rozhraní .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) nebo pokud není podporovaná verze SLES.</span><span class="sxs-lookup"><span data-stu-id="9e741-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of SLES is no longer supported.</span></span>

- <span data-ttu-id="9e741-109">✔️ označuje, že je stále podporovaná verze SLES nebo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9e741-109">A ✔️ indicates that the version of SLES or .NET Core is still supported.</span></span>
- <span data-ttu-id="9e741-110">❌Indikuje, že verze SLES nebo .NET Core není v této verzi SLES podporována.</span><span class="sxs-lookup"><span data-stu-id="9e741-110">A ❌ indicates that the version of SLES or .NET Core isn't supported on that SLES release.</span></span>
- <span data-ttu-id="9e741-111">Pokud se ✔️á jak verze SLES, tak i verze .NET Core, je podporovaná kombinace operačních systémů a .NET.</span><span class="sxs-lookup"><span data-stu-id="9e741-111">When both a version of SLES and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="9e741-112">SLES</span><span class="sxs-lookup"><span data-stu-id="9e741-112">SLES</span></span>                   | <span data-ttu-id="9e741-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="9e741-113">.NET Core 2.1</span></span> | <span data-ttu-id="9e741-114">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="9e741-114">.NET Core 3.1</span></span> | <span data-ttu-id="9e741-115">.NET 5 Preview (jenom ruční instalace)</span><span class="sxs-lookup"><span data-stu-id="9e741-115">.NET 5 Preview (manual install only)</span></span> |
|------------------------|---------------|---------------|----------------|
| <span data-ttu-id="9e741-116">✔️ [15](#sles-15-)</span><span class="sxs-lookup"><span data-stu-id="9e741-116">✔️ [15](#sles-15-)</span></span>     | <span data-ttu-id="9e741-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="9e741-117">✔️ 2.1</span></span>        | <span data-ttu-id="9e741-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="9e741-118">✔️ 3.1</span></span>        | <span data-ttu-id="9e741-119">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="9e741-119">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="9e741-120">✔️ [12 SP2](#sles-12-)</span><span class="sxs-lookup"><span data-stu-id="9e741-120">✔️ [12 SP2](#sles-12-)</span></span> | <span data-ttu-id="9e741-121">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="9e741-121">✔️ 2.1</span></span>        | <span data-ttu-id="9e741-122">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="9e741-122">✔️ 3.1</span></span>        | <span data-ttu-id="9e741-123">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="9e741-123">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="9e741-124">Následující verze rozhraní .NET Core již nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="9e741-124">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="9e741-125">Soubory ke stažení pro tyto soubory zůstanou publikované:</span><span class="sxs-lookup"><span data-stu-id="9e741-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="9e741-126">3.0</span><span class="sxs-lookup"><span data-stu-id="9e741-126">3.0</span></span>
- <span data-ttu-id="9e741-127">2,2</span><span class="sxs-lookup"><span data-stu-id="9e741-127">2.2</span></span>
- <span data-ttu-id="9e741-128">2.0</span><span class="sxs-lookup"><span data-stu-id="9e741-128">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="9e741-129">Jak nainstalovat další verze</span><span class="sxs-lookup"><span data-stu-id="9e741-129">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="sles-15-"></a><span data-ttu-id="9e741-130">SLES 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="9e741-130">SLES 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

<span data-ttu-id="9e741-131">V současné době balíček pro nastavení úložiště Microsoft SLES 15 nainstaluje soubor *Microsoft-prod. úložiště* do nesprávného adresáře, takže zypperu nebude vyhledávat balíčky .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9e741-131">Currently, the SLES 15 Microsoft repository setup package installs the *microsoft-prod.repo* file to the wrong directory, preventing zypper from finding the .NET Core packages.</span></span> <span data-ttu-id="9e741-132">Chcete-li tento problém vyřešit, vytvořte symlink ve správném adresáři.</span><span class="sxs-lookup"><span data-stu-id="9e741-132">To fix this problem, create a symlink in the correct directory.</span></span>

```bash
sudo ln -s /etc/yum.repos.d/microsoft-prod.repo /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="sles-12-"></a><span data-ttu-id="9e741-133">SLES 12 ✔️</span><span class="sxs-lookup"><span data-stu-id="9e741-133">SLES 12 ✔️</span></span>

<span data-ttu-id="9e741-134">.NET Core vyžaduje pro SLES 12 Family minimální verzi SP2.</span><span class="sxs-lookup"><span data-stu-id="9e741-134">.NET Core requires SP2 as a minimum for the SLES 12 family.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="9e741-135">Řešení potíží se správcem balíčků</span><span class="sxs-lookup"><span data-stu-id="9e741-135">Troubleshoot the package manager</span></span>

<span data-ttu-id="9e741-136">V této části najdete informace o běžných chybách, ke kterým může dojít při použití Správce balíčků k instalaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9e741-136">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="9e741-137">Nepovedlo se načíst</span><span class="sxs-lookup"><span data-stu-id="9e741-137">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="dependencies"></a><span data-ttu-id="9e741-138">Závislosti</span><span class="sxs-lookup"><span data-stu-id="9e741-138">Dependencies</span></span>

<span data-ttu-id="9e741-139">Při instalaci nástroje pomocí Správce balíčků se tyto knihovny nainstalují za vás.</span><span class="sxs-lookup"><span data-stu-id="9e741-139">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="9e741-140">Pokud ale ručně nainstalujete rozhraní .NET Core nebo publikujete samostatnou aplikaci, musíte se ujistit, že jsou nainstalované tyto knihovny:</span><span class="sxs-lookup"><span data-stu-id="9e741-140">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="9e741-141">krb5</span><span class="sxs-lookup"><span data-stu-id="9e741-141">krb5</span></span>
- <span data-ttu-id="9e741-142">libicu</span><span class="sxs-lookup"><span data-stu-id="9e741-142">libicu</span></span>
- <span data-ttu-id="9e741-143">libopenssl1_1</span><span class="sxs-lookup"><span data-stu-id="9e741-143">libopenssl1_1</span></span>

<span data-ttu-id="9e741-144">Pokud je verze OpenSSL cílového běhového prostředí 1,1 nebo novější, budete muset nainstalovat **kompatibilní openssl10**.</span><span class="sxs-lookup"><span data-stu-id="9e741-144">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="9e741-145">Další informace o závislostech najdete v tématu [samostatné aplikace pro Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="9e741-145">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="9e741-146">Pro aplikace .NET Core, které používají sestavení *System. Drawing. Common* , budete také potřebovat následující závislost:</span><span class="sxs-lookup"><span data-stu-id="9e741-146">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="9e741-147">libgdiplus (verze 6.0.1 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="9e741-147">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="9e741-148">Můžete nainstalovat nejnovější verzi *libgdiplus* přidáním úložiště mono do systému.</span><span class="sxs-lookup"><span data-stu-id="9e741-148">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="9e741-149">Další informace naleznete v tématu <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="9e741-149">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="9e741-150">Skriptovaná instalace</span><span class="sxs-lookup"><span data-stu-id="9e741-150">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="9e741-151">Ruční instalace</span><span class="sxs-lookup"><span data-stu-id="9e741-151">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="9e741-152">Další kroky</span><span class="sxs-lookup"><span data-stu-id="9e741-152">Next steps</span></span>

- [<span data-ttu-id="9e741-153">Kurz: Vytvoření konzolové aplikace s .NET Core SDK pomocí Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="9e741-153">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
