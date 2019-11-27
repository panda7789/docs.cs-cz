---
title: Instalace .NET Core SDK v systémech Windows, Linux a macOS – .NET Core
description: Přečtěte si, jak nainstalovat .NET Core v systému Windows, Linux a macOS. Objevte závislosti potřebné pro vývoj aplikací .NET Core.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 2f65e9dc39a4cd1076af1a70dfedfa671f20b42d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450875"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="6f04d-104">Instalace .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="6f04d-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="6f04d-105">V tomto článku se naučíte, jak nainstalovat .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="6f04d-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="6f04d-106">.NET Core SDK slouží k vytváření aplikací a knihoven .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6f04d-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="6f04d-107">Modul runtime .NET Core je vždy nainstalován společně se sadou SDK.</span><span class="sxs-lookup"><span data-stu-id="6f04d-107">The .NET Core runtime is always installed with the SDK.</span></span>

<span data-ttu-id="6f04d-108">.NET Core můžete stáhnout a nainstalovat přímo s jedním z následujících odkazů:</span><span class="sxs-lookup"><span data-stu-id="6f04d-108">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="6f04d-109">Soubory ke stažení pro .NET Core 3,1 Preview 3</span><span class="sxs-lookup"><span data-stu-id="6f04d-109">.NET Core 3.1 Preview 3 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="6f04d-110">Soubory ke stažení pro .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="6f04d-110">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="6f04d-111">Soubory ke stažení pro .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="6f04d-111">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="6f04d-112">Soubory ke stažení pro .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="6f04d-112">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

<span data-ttu-id="6f04d-113">.NET Core můžete nainstalovat také jako součást integrovaného vývojového prostředí (IDE), které jsou podrobně popsané v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="6f04d-113">You can also install .NET Core as part of an integrated development environment (IDE), detailed in the sections below.</span></span>

## <a name="install-with-an-installer"></a><span data-ttu-id="6f04d-114">Instalace pomocí instalačního programu</span><span class="sxs-lookup"><span data-stu-id="6f04d-114">Install with an installer</span></span>

<span data-ttu-id="6f04d-115">Windows i macOS mají samostatné instalační programy, které je možné použít k instalaci sady .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="6f04d-115">Both Windows and macOS have standalone installers that can be used to install the .NET Core 3.0 SDK.</span></span>

- <span data-ttu-id="6f04d-116">Procesory Windows [x64](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-windows-x64-installer) | [procesory x32](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-windows-x86-installer)</span><span class="sxs-lookup"><span data-stu-id="6f04d-116">Windows [x64 CPUs](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-windows-x64-installer) | [x32 CPUs](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-windows-x86-installer)</span></span>
- <span data-ttu-id="6f04d-117">macOS [procesory x64](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-macos-x64-installer)</span><span class="sxs-lookup"><span data-stu-id="6f04d-117">macOS [x64 CPUs](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-macos-x64-installer)</span></span>

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="6f04d-118">Instalace pomocí Správce balíčků</span><span class="sxs-lookup"><span data-stu-id="6f04d-118">Install with a package manager</span></span>

<span data-ttu-id="6f04d-119">.NET Core SDK můžete nainstalovat pomocí mnoha běžných správců balíčků pro Linux.</span><span class="sxs-lookup"><span data-stu-id="6f04d-119">You can install the .NET Core SDK with many of the common Linux package managers.</span></span> <span data-ttu-id="6f04d-120">Další informace najdete v tématu [Správce balíčků pro Linux – instalace .NET Core](linux-package-manager-rhel7.md).</span><span class="sxs-lookup"><span data-stu-id="6f04d-120">For more information, see [Linux Package Manager - Install .NET Core](linux-package-manager-rhel7.md).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="6f04d-121">Instalace se sadou Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6f04d-121">Install with Visual Studio</span></span>

<span data-ttu-id="6f04d-122">Pokud používáte Visual Studio pro vývoj aplikací .NET Core, v následující tabulce je popsána minimální požadovaná verze sady Visual Studio na základě cílové verze .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="6f04d-122">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="6f04d-123">Verze .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="6f04d-123">.NET Core SDK version</span></span> | <span data-ttu-id="6f04d-124">Verze Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6f04d-124">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="6f04d-125">3,0</span><span class="sxs-lookup"><span data-stu-id="6f04d-125">3.0</span></span>                   | <span data-ttu-id="6f04d-126">Visual Studio 2019 verze 16,3 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="6f04d-126">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="6f04d-127">2.2</span><span class="sxs-lookup"><span data-stu-id="6f04d-127">2.2</span></span>                   | <span data-ttu-id="6f04d-128">Visual Studio 2017 verze 15,9 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="6f04d-128">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="6f04d-129">2.1</span><span class="sxs-lookup"><span data-stu-id="6f04d-129">2.1</span></span>                   | <span data-ttu-id="6f04d-130">Visual Studio 2017 verze 15,7 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="6f04d-130">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="6f04d-131">Pokud již máte nainstalováno Visual Studio, můžete si ověřit verzi pomocí následujících kroků.</span><span class="sxs-lookup"><span data-stu-id="6f04d-131">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="6f04d-132">Otevřít Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6f04d-132">Open Visual Studio.</span></span>
01. <span data-ttu-id="6f04d-133">Vyberte **nápovědu** > **o Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="6f04d-133">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="6f04d-134">Přečtěte si číslo verze v dialogovém okně **o produktu** .</span><span class="sxs-lookup"><span data-stu-id="6f04d-134">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="6f04d-135">Visual Studio může nainstalovat nejnovější .NET Core SDK a modul runtime.</span><span class="sxs-lookup"><span data-stu-id="6f04d-135">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="6f04d-136">[Stáhněte si Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="6f04d-136">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="6f04d-137">Vyberte úlohu.</span><span class="sxs-lookup"><span data-stu-id="6f04d-137">Select a workload</span></span>

<span data-ttu-id="6f04d-138">Při instalaci nebo úpravách sady Visual Studio vyberte jednu z následujících úloh v závislosti na typu aplikace, kterou sestavujete:</span><span class="sxs-lookup"><span data-stu-id="6f04d-138">When installing or modifying Visual Studio, select one of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="6f04d-139">Úloha **vývoje .NET Core pro více platforem** v části **Další sady nástrojů** .</span><span class="sxs-lookup"><span data-stu-id="6f04d-139">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="6f04d-140">Úlohy **vývoje ASP.NET a webu** v části **web & Cloud** .</span><span class="sxs-lookup"><span data-stu-id="6f04d-140">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="6f04d-141">Úlohy **vývoje Azure** v části **web & cloudu** .</span><span class="sxs-lookup"><span data-stu-id="6f04d-141">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="6f04d-142">Úloha **vývoj desktopových aplikací .NET** v části **Desktop & Mobile** .</span><span class="sxs-lookup"><span data-stu-id="6f04d-142">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="6f04d-143">[![Windows Visual Studio 2019 s úlohou .NET Core](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="6f04d-143">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="6f04d-144">Instalace pomocí Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="6f04d-144">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="6f04d-145">Visual Studio pro Mac nainstaluje .NET Core SDK při výběru úlohy **.NET Core** .</span><span class="sxs-lookup"><span data-stu-id="6f04d-145">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="6f04d-146">Chcete-li začít s vývojem .NET Core v macOS, přečtěte si téma [instalace sady Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="6f04d-146">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span>

<span data-ttu-id="6f04d-147">[![macOS sady Visual Studio 2019 pro Mac s funkcí úlohy .NET Core](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="6f04d-147">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

## <a name="install-from-visual-studio-code"></a><span data-ttu-id="6f04d-148">Nainstalovat z Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="6f04d-148">Install from Visual Studio Code</span></span>

<span data-ttu-id="6f04d-149">Visual Studio Code je výkonný a prostý Editor zdrojového kódu, který běží na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="6f04d-149">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="6f04d-150">Visual Studio Code je k dispozici pro Windows, macOS a Linux.</span><span class="sxs-lookup"><span data-stu-id="6f04d-150">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="6f04d-151">I když Visual Studio Code nepřináší podporu .NET Core, je přidání podpory .NET Core jednoduché.</span><span class="sxs-lookup"><span data-stu-id="6f04d-151">While Visual Studio Code doesn't come with .NET Core support, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="6f04d-152">[Stáhněte a nainstalujte Visual Studio Code](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="6f04d-152">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="6f04d-153">[Stáhněte a nainstalujte .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="6f04d-153">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>
01. <span data-ttu-id="6f04d-154">[Nainstalujte C# rozšíření z webu Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span><span class="sxs-lookup"><span data-stu-id="6f04d-154">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span></span>

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="6f04d-155">Instalace pomocí automatizace PowerShellu</span><span class="sxs-lookup"><span data-stu-id="6f04d-155">Install with PowerShell automation</span></span>

<span data-ttu-id="6f04d-156">[Dotnet – instalační skripty](../tools/dotnet-install-script.md) se používají pro automatizaci a pro instalaci sady SDK bez správy.</span><span class="sxs-lookup"><span data-stu-id="6f04d-156">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="6f04d-157">Skript si můžete stáhnout z [referenční stránky dotnet-install Script](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="6f04d-157">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="6f04d-158">Skript ve výchozím nastavení instaluje nejnovější verzi [LTS (Long Term support)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což je .net Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="6f04d-158">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="6f04d-159">Chcete-li nainstalovat aktuální vydání rozhraní .NET Core, spusťte skript s následujícím přepínačem.</span><span class="sxs-lookup"><span data-stu-id="6f04d-159">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="6f04d-160">Instalace pomocí služby bash Automation</span><span class="sxs-lookup"><span data-stu-id="6f04d-160">Install with bash automation</span></span>

<span data-ttu-id="6f04d-161">[Dotnet – instalační skripty](../tools/dotnet-install-script.md) se používají pro automatizaci a pro instalaci sady SDK bez správy.</span><span class="sxs-lookup"><span data-stu-id="6f04d-161">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="6f04d-162">Skript si můžete stáhnout z [referenční stránky dotnet-install Script](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="6f04d-162">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="6f04d-163">Skript ve výchozím nastavení instaluje nejnovější verzi [LTS (Long Term support)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což je .net Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="6f04d-163">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="6f04d-164">Chcete-li nainstalovat aktuální vydání rozhraní .NET Core, spusťte skript s následujícím přepínačem.</span><span class="sxs-lookup"><span data-stu-id="6f04d-164">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="docker"></a><span data-ttu-id="6f04d-165">Docker</span><span class="sxs-lookup"><span data-stu-id="6f04d-165">Docker</span></span>

<span data-ttu-id="6f04d-166">Kontejnery poskytují jednoduchý způsob izolace vaší aplikace ze zbytku hostitelského systému.</span><span class="sxs-lookup"><span data-stu-id="6f04d-166">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="6f04d-167">Kontejnery na stejném počítači sdílejí jenom jádro a používají prostředky, které jsou dané aplikaci k.</span><span class="sxs-lookup"><span data-stu-id="6f04d-167">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="6f04d-168">.NET Core může běžet v kontejneru Docker.</span><span class="sxs-lookup"><span data-stu-id="6f04d-168">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="6f04d-169">Oficiální image Docker pro .NET Core jsou publikované ve službě Microsoft Container Registry (MCR) a jsou zjistitelné v [úložišti Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="6f04d-169">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="6f04d-170">Každé úložiště obsahuje obrázky pro různé kombinace rozhraní .NET (SDK nebo modulu runtime) a operačního systému, které můžete použít.</span><span class="sxs-lookup"><span data-stu-id="6f04d-170">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="6f04d-171">Společnost Microsoft poskytuje obrázky, které jsou upraveny pro konkrétní scénáře.</span><span class="sxs-lookup"><span data-stu-id="6f04d-171">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="6f04d-172">Například [úložiště ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) poskytuje obrázky, které jsou vytvořené pro spouštění ASP.NET Core aplikací v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="6f04d-172">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="6f04d-173">Další informace o použití .NET Core v kontejneru Docker najdete v tématu [Úvod do .NET a Docker](../docker/introduction.md) a [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="6f04d-173">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="6f04d-174">Další kroky</span><span class="sxs-lookup"><span data-stu-id="6f04d-174">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="6f04d-175">[Kurz: C# kurz Hello World](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="6f04d-175">[Tutorial: C# Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="6f04d-176">[Kurz: kurz Hello World Visual Basic](../tutorials/vb-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="6f04d-176">[Tutorial: Visual Basic Hello World tutorial](../tutorials/vb-with-visual-studio.md).</span></span>
- <span data-ttu-id="6f04d-177">[Kurz: vytvoření nové aplikace pomocí Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span><span class="sxs-lookup"><span data-stu-id="6f04d-177">[Tutorial: Create a new app with Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span></span>
- <span data-ttu-id="6f04d-178">[Kurz: kontejnerizace aplikace .NET Core](../docker/build-container.md)</span><span class="sxs-lookup"><span data-stu-id="6f04d-178">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="6f04d-179">[Kurz: Začínáme s MacOS](../tutorials/using-on-mac-vs.md).</span><span class="sxs-lookup"><span data-stu-id="6f04d-179">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="6f04d-180">[Kurz: vytvoření nové aplikace pomocí Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span><span class="sxs-lookup"><span data-stu-id="6f04d-180">[Tutorial: Create a new app with Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span></span>
- <span data-ttu-id="6f04d-181">[Kurz: kontejnerizace aplikace .NET Core](../docker/build-container.md)</span><span class="sxs-lookup"><span data-stu-id="6f04d-181">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
