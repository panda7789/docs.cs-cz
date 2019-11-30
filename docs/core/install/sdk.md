---
title: Instalace .NET Core SDK v systémech Windows, Linux a macOS – .NET Core
description: Přečtěte si, jak nainstalovat .NET Core v systému Windows, Linux a macOS. Objevte závislosti potřebné pro vývoj aplikací .NET Core.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 54819b409422e8bda9efe25478aa3424683a380b
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567471"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="f892c-104">Instalace .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="f892c-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="f892c-105">V tomto článku se naučíte, jak nainstalovat .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="f892c-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="f892c-106">.NET Core SDK slouží k vytváření aplikací a knihoven .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f892c-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="f892c-107">Modul runtime .NET Core je vždy nainstalován společně se sadou SDK.</span><span class="sxs-lookup"><span data-stu-id="f892c-107">The .NET Core runtime is always installed with the SDK.</span></span>

::: zone pivot="os-windows,os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="f892c-108">Instalace pomocí instalačního programu</span><span class="sxs-lookup"><span data-stu-id="f892c-108">Install with an installer</span></span>

<span data-ttu-id="f892c-109">Windows i macOS mají samostatné instalační programy, které je možné použít k instalaci sady .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="f892c-109">Both Windows and macOS have standalone installers that can be used to install the .NET Core 3.0 SDK.</span></span>

- <span data-ttu-id="f892c-110">Procesory Windows [x64 (64-bit)](https://dotnet.microsoft.com/download/dotnet-core/3.0) | procesory [x86 (32 bitů)](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span><span class="sxs-lookup"><span data-stu-id="f892c-110">Windows [x64 (64-bit) CPUs](https://dotnet.microsoft.com/download/dotnet-core/3.0) | [x86 (32-bit) CPUs](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span></span>
- <span data-ttu-id="f892c-111">macOS [procesory x64 (64 bitů)](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span><span class="sxs-lookup"><span data-stu-id="f892c-111">macOS [x64 (64-bit) CPUs](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span></span>

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="f892c-112">Instalace pomocí Správce balíčků</span><span class="sxs-lookup"><span data-stu-id="f892c-112">Install with a package manager</span></span>

<span data-ttu-id="f892c-113">.NET Core SDK můžete nainstalovat pomocí mnoha běžných správců balíčků pro Linux.</span><span class="sxs-lookup"><span data-stu-id="f892c-113">You can install the .NET Core SDK with many of the common Linux package managers.</span></span> <span data-ttu-id="f892c-114">Další informace najdete v tématu [Správce balíčků pro Linux – instalace .NET Core](linux-package-managers.md).</span><span class="sxs-lookup"><span data-stu-id="f892c-114">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="f892c-115">Stažení a ruční instalace</span><span class="sxs-lookup"><span data-stu-id="f892c-115">Download and manually install</span></span>

<span data-ttu-id="f892c-116">K extrakci sady SDK a zpřístupnění příkazů v terminálu nejprve [Stáhněte](#all-net-core-downloads) binární verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f892c-116">To extract the SDK and make the commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="f892c-117">Pak otevřete terminál a spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="f892c-117">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-3.0.101-linux-musl-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="f892c-118">Výše uvedené příkazy zpřístupní pouze příkazy sady .NET SDK dostupné pro relaci terminálu, ve které byla spuštěna.</span><span class="sxs-lookup"><span data-stu-id="f892c-118">The above commands will only make the .NET SDK commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="f892c-119">Úpravou profilu prostředí můžete tyto příkazy trvale přidat.</span><span class="sxs-lookup"><span data-stu-id="f892c-119">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="f892c-120">K dispozici je řada různých prostředí pro Linux a každá má jiný profil.</span><span class="sxs-lookup"><span data-stu-id="f892c-120">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="f892c-121">Příklad:</span><span class="sxs-lookup"><span data-stu-id="f892c-121">For example:</span></span>
>
> - <span data-ttu-id="f892c-122">**Prostředí bash**: *~/. bash_profile*, *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="f892c-122">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="f892c-123">**Korn shell**: *~/.KSHRC* nebo *. Profile*</span><span class="sxs-lookup"><span data-stu-id="f892c-123">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="f892c-124">**Prostředí Z**: *~/.zshrc* nebo *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="f892c-124">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
> 
> <span data-ttu-id="f892c-125">Upravte příslušný zdrojový soubor pro prostředí a přidejte `:$HOME/dotnet` na konec existujícího příkazu `PATH`.</span><span class="sxs-lookup"><span data-stu-id="f892c-125">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="f892c-126">Pokud není zahrnutý žádný příkaz `PATH`, přidejte nový řádek s `export PATH=$PATH:$HOME/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="f892c-126">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="f892c-127">Přidejte také `export DOTNET_ROOT=$HOME/dotnet` na konec souboru.</span><span class="sxs-lookup"><span data-stu-id="f892c-127">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="f892c-128">Instalace se sadou Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f892c-128">Install with Visual Studio</span></span>

<span data-ttu-id="f892c-129">Pokud používáte Visual Studio pro vývoj aplikací .NET Core, v následující tabulce je popsána minimální požadovaná verze sady Visual Studio na základě cílové verze .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="f892c-129">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="f892c-130">Verze .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="f892c-130">.NET Core SDK version</span></span> | <span data-ttu-id="f892c-131">Verze sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f892c-131">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="f892c-132">3,1 Preview</span><span class="sxs-lookup"><span data-stu-id="f892c-132">3.1 Preview</span></span>           | <span data-ttu-id="f892c-133">Visual Studio 2019 verze 16,4 Preview nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="f892c-133">Visual Studio 2019 version 16.4 preview or higher.</span></span> |
| <span data-ttu-id="f892c-134">3,0</span><span class="sxs-lookup"><span data-stu-id="f892c-134">3.0</span></span>                   | <span data-ttu-id="f892c-135">Visual Studio 2019 verze 16,3 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="f892c-135">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="f892c-136">2,2</span><span class="sxs-lookup"><span data-stu-id="f892c-136">2.2</span></span>                   | <span data-ttu-id="f892c-137">Visual Studio 2017 verze 15,9 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="f892c-137">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="f892c-138">2,1</span><span class="sxs-lookup"><span data-stu-id="f892c-138">2.1</span></span>                   | <span data-ttu-id="f892c-139">Visual Studio 2017 verze 15,7 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="f892c-139">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="f892c-140">Pokud již máte nainstalováno Visual Studio, můžete si ověřit verzi pomocí následujících kroků.</span><span class="sxs-lookup"><span data-stu-id="f892c-140">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="f892c-141">Otevřete Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f892c-141">Open Visual Studio.</span></span>
01. <span data-ttu-id="f892c-142">Vyberte **nápovědu** > **o Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="f892c-142">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="f892c-143">Přečtěte si číslo verze v dialogovém okně **o produktu** .</span><span class="sxs-lookup"><span data-stu-id="f892c-143">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="f892c-144">Visual Studio může nainstalovat nejnovější .NET Core SDK a modul runtime.</span><span class="sxs-lookup"><span data-stu-id="f892c-144">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="f892c-145">[Stáhněte si Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="f892c-145">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="f892c-146">Vyberte úlohu.</span><span class="sxs-lookup"><span data-stu-id="f892c-146">Select a workload</span></span>

<span data-ttu-id="f892c-147">Při instalaci nebo úpravách sady Visual Studio vyberte jednu z následujících úloh v závislosti na typu aplikace, kterou sestavujete:</span><span class="sxs-lookup"><span data-stu-id="f892c-147">When installing or modifying Visual Studio, select one of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="f892c-148">Úloha **vývoje .NET Core pro více platforem** v části **Další sady nástrojů** .</span><span class="sxs-lookup"><span data-stu-id="f892c-148">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="f892c-149">Úlohy **vývoje ASP.NET a webu** v části **web & Cloud** .</span><span class="sxs-lookup"><span data-stu-id="f892c-149">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="f892c-150">Úlohy **vývoje Azure** v části **web & cloudu** .</span><span class="sxs-lookup"><span data-stu-id="f892c-150">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="f892c-151">Úloha **vývoj desktopových aplikací .NET** v části **Desktop & Mobile** .</span><span class="sxs-lookup"><span data-stu-id="f892c-151">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="f892c-152">[![Windows Visual Studio 2019 s úlohou .NET Core](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="f892c-152">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="f892c-153">Instalace pomocí Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="f892c-153">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="f892c-154">Visual Studio pro Mac nainstaluje .NET Core SDK při výběru úlohy **.NET Core** .</span><span class="sxs-lookup"><span data-stu-id="f892c-154">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="f892c-155">Chcete-li začít s vývojem .NET Core v macOS, přečtěte si téma [instalace sady Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="f892c-155">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span>

<span data-ttu-id="f892c-156">[![macOS sady Visual Studio 2019 pro Mac s funkcí úlohy .NET Core](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="f892c-156">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="f892c-157">Nainstalovat společně Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="f892c-157">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="f892c-158">Visual Studio Code je výkonný a prostý Editor zdrojového kódu, který běží na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="f892c-158">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="f892c-159">Visual Studio Code je k dispozici pro Windows, macOS a Linux.</span><span class="sxs-lookup"><span data-stu-id="f892c-159">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="f892c-160">I když Visual Studio Code nepřichází s automatizovaným instalačním programem .NET Core, jako je Visual Studio, přidání podpory .NET Core je jednoduché.</span><span class="sxs-lookup"><span data-stu-id="f892c-160">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="f892c-161">[Stáhněte a nainstalujte Visual Studio Code](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="f892c-161">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="f892c-162">[Stáhněte a nainstalujte .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="f892c-162">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="f892c-163">[Nainstalujte C# rozšíření z webu Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span><span class="sxs-lookup"><span data-stu-id="f892c-163">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span></span>

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="f892c-164">Instalace pomocí automatizace PowerShellu</span><span class="sxs-lookup"><span data-stu-id="f892c-164">Install with PowerShell automation</span></span>

<span data-ttu-id="f892c-165">[Dotnet – instalační skripty](../tools/dotnet-install-script.md) se používají pro automatizaci a pro instalaci sady SDK bez správy.</span><span class="sxs-lookup"><span data-stu-id="f892c-165">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="f892c-166">Skript si můžete stáhnout z [referenční stránky dotnet-install Script](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="f892c-166">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="f892c-167">Skript ve výchozím nastavení instaluje nejnovější verzi [LTS (Long Term support)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což je .net Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="f892c-167">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="f892c-168">Chcete-li nainstalovat aktuální vydání rozhraní .NET Core, spusťte skript s následujícím přepínačem.</span><span class="sxs-lookup"><span data-stu-id="f892c-168">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="f892c-169">Instalace pomocí služby bash Automation</span><span class="sxs-lookup"><span data-stu-id="f892c-169">Install with bash automation</span></span>

<span data-ttu-id="f892c-170">[Dotnet – instalační skripty](../tools/dotnet-install-script.md) se používají pro automatizaci a pro instalaci sady SDK bez správy.</span><span class="sxs-lookup"><span data-stu-id="f892c-170">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="f892c-171">Skript si můžete stáhnout z [referenční stránky dotnet-install Script](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="f892c-171">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="f892c-172">Skript ve výchozím nastavení instaluje nejnovější verzi [LTS (Long Term support)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což je .net Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="f892c-172">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="f892c-173">Chcete-li nainstalovat aktuální vydání rozhraní .NET Core, spusťte skript s následujícím přepínačem.</span><span class="sxs-lookup"><span data-stu-id="f892c-173">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="f892c-174">Všechny soubory ke stažení pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="f892c-174">All .NET Core downloads</span></span>

<span data-ttu-id="f892c-175">.NET Core můžete stáhnout a nainstalovat přímo s jedním z následujících odkazů:</span><span class="sxs-lookup"><span data-stu-id="f892c-175">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="f892c-176">Soubory ke stažení pro .NET Core 3,1 Preview</span><span class="sxs-lookup"><span data-stu-id="f892c-176">.NET Core 3.1 Preview downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="f892c-177">Soubory ke stažení pro .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="f892c-177">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="f892c-178">Soubory ke stažení pro .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="f892c-178">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="f892c-179">Soubory ke stažení pro .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="f892c-179">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="f892c-180">Docker</span><span class="sxs-lookup"><span data-stu-id="f892c-180">Docker</span></span>

<span data-ttu-id="f892c-181">Kontejnery poskytují jednoduchý způsob izolace vaší aplikace ze zbytku hostitelského systému.</span><span class="sxs-lookup"><span data-stu-id="f892c-181">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="f892c-182">Kontejnery na stejném počítači sdílejí jenom jádro a používají prostředky, které jsou dané aplikaci k.</span><span class="sxs-lookup"><span data-stu-id="f892c-182">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="f892c-183">.NET Core může běžet v kontejneru Docker.</span><span class="sxs-lookup"><span data-stu-id="f892c-183">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="f892c-184">Oficiální image Docker pro .NET Core jsou publikované ve službě Microsoft Container Registry (MCR) a jsou zjistitelné v [úložišti Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="f892c-184">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="f892c-185">Každé úložiště obsahuje obrázky pro různé kombinace rozhraní .NET (SDK nebo modulu runtime) a operačního systému, které můžete použít.</span><span class="sxs-lookup"><span data-stu-id="f892c-185">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="f892c-186">Společnost Microsoft poskytuje obrázky, které jsou upraveny pro konkrétní scénáře.</span><span class="sxs-lookup"><span data-stu-id="f892c-186">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="f892c-187">Například [úložiště ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) poskytuje obrázky, které jsou vytvořené pro spouštění ASP.NET Core aplikací v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="f892c-187">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="f892c-188">Další informace o použití .NET Core v kontejneru Docker najdete v tématu [Úvod do .NET a Docker](../docker/introduction.md) a [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="f892c-188">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="f892c-189">Další kroky</span><span class="sxs-lookup"><span data-stu-id="f892c-189">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="f892c-190">[Kurz: C# kurz Hello World](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="f892c-190">[Tutorial: C# Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="f892c-191">[Kurz: kurz Hello World Visual Basic](../tutorials/vb-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="f892c-191">[Tutorial: Visual Basic Hello World tutorial](../tutorials/vb-with-visual-studio.md).</span></span>
- <span data-ttu-id="f892c-192">[Kurz: vytvoření nové aplikace pomocí Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span><span class="sxs-lookup"><span data-stu-id="f892c-192">[Tutorial: Create a new app with Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span></span>
- <span data-ttu-id="f892c-193">[Kurz: kontejnerizace aplikace .NET Core](../docker/build-container.md)</span><span class="sxs-lookup"><span data-stu-id="f892c-193">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="f892c-194">[Kurz: Začínáme s MacOS](../tutorials/using-on-mac-vs.md).</span><span class="sxs-lookup"><span data-stu-id="f892c-194">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="f892c-195">[Kurz: vytvoření nové aplikace pomocí Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span><span class="sxs-lookup"><span data-stu-id="f892c-195">[Tutorial: Create a new app with Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span></span>
- <span data-ttu-id="f892c-196">[Kurz: kontejnerizace aplikace .NET Core](../docker/build-container.md)</span><span class="sxs-lookup"><span data-stu-id="f892c-196">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
