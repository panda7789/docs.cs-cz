---
title: Instalace .NET Core na RHEL – .NET Core
description: Ukazuje různé způsoby, jak nainstalovat .NET Core SDK a modul runtime .NET Core v RHEL.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 4a406fe1834c16bab9a5548b69206b51270b33fa
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324716"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-rhel"></a><span data-ttu-id="eafd3-103">Instalace .NET Core SDK nebo modulu runtime .NET Core v RHEL</span><span class="sxs-lookup"><span data-stu-id="eafd3-103">Install .NET Core SDK or .NET Core Runtime on RHEL</span></span>

<span data-ttu-id="eafd3-104">Rozhraní .NET Core je podporováno v RHEL.</span><span class="sxs-lookup"><span data-stu-id="eafd3-104">.NET Core is supported on RHEL.</span></span> <span data-ttu-id="eafd3-105">Tento článek popisuje, jak nainstalovat .NET Core na RHEL.</span><span class="sxs-lookup"><span data-stu-id="eafd3-105">This article describes how to install .NET Core on RHEL.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="eafd3-106">Zaregistrujte si předplatné Red Hat</span><span class="sxs-lookup"><span data-stu-id="eafd3-106">Register your Red Hat subscription</span></span>

<span data-ttu-id="eafd3-107">Pokud chcete nainstalovat .NET Core ze Red Hat na RHEL, musíte se nejdřív zaregistrovat pomocí Správce předplatných Red Hat.</span><span class="sxs-lookup"><span data-stu-id="eafd3-107">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="eafd3-108">Pokud jste to ještě neudělali v systému nebo pokud si nejste jistí, přečtěte si část [dokumentace k produktu Red Hat pro .NET Core](https://access.redhat.com/documentation/net_core/).</span><span class="sxs-lookup"><span data-stu-id="eafd3-108">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="eafd3-109">Podporované distribuce</span><span class="sxs-lookup"><span data-stu-id="eafd3-109">Supported distributions</span></span>

<span data-ttu-id="eafd3-110">Následující tabulka uvádí seznam aktuálně podporovaných vydání .NET Core na RHEL 7 a RHEL 8.</span><span class="sxs-lookup"><span data-stu-id="eafd3-110">The following table is a list of currently supported .NET Core releases on both RHEL 7 and RHEL 8.</span></span> <span data-ttu-id="eafd3-111">Tato verze zůstane podporovaná, dokud [nedosáhne žádné verze rozhraní .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) nebo pokud není podporovaná verze RHEL.</span><span class="sxs-lookup"><span data-stu-id="eafd3-111">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of RHEL is no longer supported.</span></span>

- <span data-ttu-id="eafd3-112">✔️ označuje, že je stále podporovaná verze RHEL nebo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="eafd3-112">A ✔️ indicates that the version of RHEL or .NET Core is still supported.</span></span>
- <span data-ttu-id="eafd3-113">❌Indikuje, že verze RHEL nebo .NET Core není v této verzi RHEL podporována.</span><span class="sxs-lookup"><span data-stu-id="eafd3-113">A ❌ indicates that the version of RHEL or .NET Core isn't supported on that RHEL release.</span></span>
- <span data-ttu-id="eafd3-114">Pokud se ✔️á jak verze RHEL, tak i verze .NET Core, je podporovaná kombinace operačních systémů a .NET.</span><span class="sxs-lookup"><span data-stu-id="eafd3-114">When both a version of RHEL and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="eafd3-115">RHEL</span><span class="sxs-lookup"><span data-stu-id="eafd3-115">RHEL</span></span>                   | <span data-ttu-id="eafd3-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="eafd3-116">.NET Core 2.1</span></span> | <span data-ttu-id="eafd3-117">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="eafd3-117">.NET Core 3.1</span></span> | <span data-ttu-id="eafd3-118">.NET 5 Preview (jenom ruční instalace)</span><span class="sxs-lookup"><span data-stu-id="eafd3-118">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="eafd3-119">✔️ [8](#rhel-8-)</span><span class="sxs-lookup"><span data-stu-id="eafd3-119">✔️ [8](#rhel-8-)</span></span> | <span data-ttu-id="eafd3-120">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="eafd3-120">✔️ 2.1</span></span>        | <span data-ttu-id="eafd3-121">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="eafd3-121">✔️ 3.1</span></span>        | <span data-ttu-id="eafd3-122">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="eafd3-122">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="eafd3-123">✔️ [7](#rhel-7-)</span><span class="sxs-lookup"><span data-stu-id="eafd3-123">✔️ [7](#rhel-7-)</span></span> | <span data-ttu-id="eafd3-124">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="eafd3-124">✔️ 2.1</span></span>        | <span data-ttu-id="eafd3-125">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="eafd3-125">✔️ 3.1</span></span>        | <span data-ttu-id="eafd3-126">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="eafd3-126">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="eafd3-127">Následující verze rozhraní .NET Core již nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="eafd3-127">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="eafd3-128">Soubory ke stažení pro tyto soubory zůstanou publikované:</span><span class="sxs-lookup"><span data-stu-id="eafd3-128">The downloads for these still remain published:</span></span>

- <span data-ttu-id="eafd3-129">3.0</span><span class="sxs-lookup"><span data-stu-id="eafd3-129">3.0</span></span>
- <span data-ttu-id="eafd3-130">2,2</span><span class="sxs-lookup"><span data-stu-id="eafd3-130">2.2</span></span>
- <span data-ttu-id="eafd3-131">2.0</span><span class="sxs-lookup"><span data-stu-id="eafd3-131">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="eafd3-132">Jak nainstalovat další verze</span><span class="sxs-lookup"><span data-stu-id="eafd3-132">How to install other versions</span></span>

<span data-ttu-id="eafd3-133">Projděte si [dokumentaci k Red Hat pro .NET Core](https://access.redhat.com/documentation/net_core/) podle kroků vyžadovaných k instalaci jiných verzí rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="eafd3-133">Consult the [Red Hat documentation for .NET Core](https://access.redhat.com/documentation/net_core/) on the steps required to install other releases of .NET Core.</span></span>

## <a name="rhel-8-"></a><span data-ttu-id="eafd3-134">RHEL 8 ✔️</span><span class="sxs-lookup"><span data-stu-id="eafd3-134">RHEL 8 ✔️</span></span>

<span data-ttu-id="eafd3-135">Rozhraní .NET Core je zahrnuté v úložištích AppStream pro RHEL 8.</span><span class="sxs-lookup"><span data-stu-id="eafd3-135">.NET Core is included in the AppStream repositories for RHEL 8.</span></span>

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="rhel-7-"></a><span data-ttu-id="eafd3-136">RHEL 7 ✔️</span><span class="sxs-lookup"><span data-stu-id="eafd3-136">RHEL 7 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

<span data-ttu-id="eafd3-137">Následující příkaz nainstaluje `scl-utils` balíček:</span><span class="sxs-lookup"><span data-stu-id="eafd3-137">The following command installs the `scl-utils` package:</span></span>

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a><span data-ttu-id="eafd3-138">Instalace sady SDK</span><span class="sxs-lookup"><span data-stu-id="eafd3-138">Install the SDK</span></span>

<span data-ttu-id="eafd3-139">.NET Core SDK umožňuje vyvíjet aplikace pomocí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="eafd3-139">.NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="eafd3-140">Pokud nainstalujete .NET Core SDK, nemusíte instalovat odpovídající modul runtime.</span><span class="sxs-lookup"><span data-stu-id="eafd3-140">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="eafd3-141">Chcete-li nainstalovat .NET Core SDK, spusťte následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="eafd3-141">To install .NET Core SDK, run the following commands:</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

<span data-ttu-id="eafd3-142">Red Hat nedoporučuje trvalé povolení `rh-dotnet31` , protože může ovlivnit jiné programy.</span><span class="sxs-lookup"><span data-stu-id="eafd3-142">Red Hat does not recommend permanently enabling `rh-dotnet31` because it may affect other programs.</span></span> <span data-ttu-id="eafd3-143">Například `rh-dotnet31` obsahuje verzi nástroje `libcurl` , která se liší od základní verze RHEL.</span><span class="sxs-lookup"><span data-stu-id="eafd3-143">For example, `rh-dotnet31` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="eafd3-144">To může vést k problémům v programech, které neočekávají jinou verzi `libcurl` .</span><span class="sxs-lookup"><span data-stu-id="eafd3-144">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="eafd3-145">Pokud chcete povolit možnost `rh-dotnet` trvale, přidejte do souboru _~/.bashrc_ následující řádek.</span><span class="sxs-lookup"><span data-stu-id="eafd3-145">If you want to enable `rh-dotnet` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31
```

### <a name="install-the-runtime"></a><span data-ttu-id="eafd3-146">Instalace modulu runtime</span><span class="sxs-lookup"><span data-stu-id="eafd3-146">Install the runtime</span></span>

<span data-ttu-id="eafd3-147">Modul runtime .NET Core umožňuje spouštět aplikace, které byly vytvořeny pomocí .NET Core, které neobsahovaly modul runtime.</span><span class="sxs-lookup"><span data-stu-id="eafd3-147">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="eafd3-148">Níže uvedené příkazy nainstalují modul runtime ASP.NET Core, což je nejvíce kompatibilní modul runtime pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="eafd3-148">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="eafd3-149">V terminálu spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="eafd3-149">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31-aspnetcore-runtime-3.1 bash
```

<span data-ttu-id="eafd3-150">Red Hat nedoporučuje trvalé povolení `rh-dotnet31-aspnetcore-runtime-3.1` , protože může ovlivnit jiné programy.</span><span class="sxs-lookup"><span data-stu-id="eafd3-150">Red Hat does not recommend permanently enabling `rh-dotnet31-aspnetcore-runtime-3.1` because it may affect other programs.</span></span> <span data-ttu-id="eafd3-151">Například `rh-dotnet31-aspnetcore-runtime-3.1` obsahuje verzi nástroje `libcurl` , která se liší od základní verze RHEL.</span><span class="sxs-lookup"><span data-stu-id="eafd3-151">For example, `rh-dotnet31-aspnetcore-runtime-3.1` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="eafd3-152">To může vést k problémům v programech, které neočekávají jinou verzi `libcurl` .</span><span class="sxs-lookup"><span data-stu-id="eafd3-152">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="eafd3-153">Pokud chcete povolit možnost `rh-dotnet31-aspnetcore-runtime-3.1` trvale, přidejte do souboru _~/.bashrc_ následující řádek.</span><span class="sxs-lookup"><span data-stu-id="eafd3-153">If you want to enable `rh-dotnet31-aspnetcore-runtime-3.1` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31-aspnetcore-runtime-3.1
```

<span data-ttu-id="eafd3-154">Jako alternativu k modulu runtime ASP.NET Core můžete nainstalovat modul runtime .NET Core, který neobsahuje podporu ASP.NET Core: Nahraďte `rh-dotnet31-aspnetcore-runtime-3.1` v příkazech uvedených výše `rh-dotnet31-dotnet-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="eafd3-154">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `rh-dotnet31-aspnetcore-runtime-3.1` in the commands above with `rh-dotnet31-dotnet-runtime-3.1`.</span></span>

## <a name="snap"></a><span data-ttu-id="eafd3-155">Moduly snap</span><span class="sxs-lookup"><span data-stu-id="eafd3-155">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="eafd3-156">Závislosti</span><span class="sxs-lookup"><span data-stu-id="eafd3-156">Dependencies</span></span>

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="eafd3-157">Skriptovaná instalace</span><span class="sxs-lookup"><span data-stu-id="eafd3-157">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="eafd3-158">Ruční instalace</span><span class="sxs-lookup"><span data-stu-id="eafd3-158">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="eafd3-159">Další kroky</span><span class="sxs-lookup"><span data-stu-id="eafd3-159">Next steps</span></span>

- [<span data-ttu-id="eafd3-160">Kurz: Vytvoření konzolové aplikace s .NET Core SDK pomocí Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="eafd3-160">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
