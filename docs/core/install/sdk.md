---
title: Instalace .NET Core SDK v systémech Windows, Linux a macOS – .NET Core
description: Přečtěte si, jak nainstalovat .NET Core v systému Windows, Linux a macOS. Objevte závislosti potřebné pro vývoj aplikací .NET Core.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 290bdfb05b328bb311e6ff5ef493048b05985899
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74801940"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="c19ad-104">Instalace .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="c19ad-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="c19ad-105">V tomto článku se naučíte, jak nainstalovat .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="c19ad-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="c19ad-106">.NET Core SDK slouží k vytváření aplikací a knihoven .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c19ad-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="c19ad-107">Modul runtime .NET Core je vždy nainstalován společně se sadou SDK.</span><span class="sxs-lookup"><span data-stu-id="c19ad-107">The .NET Core runtime is always installed with the SDK.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="c19ad-108">Instalace pomocí instalačního programu</span><span class="sxs-lookup"><span data-stu-id="c19ad-108">Install with an installer</span></span>

<span data-ttu-id="c19ad-109">Systém Windows obsahuje samostatné instalační programy, které lze použít k instalaci sady .NET Core 3,0 SDK:</span><span class="sxs-lookup"><span data-stu-id="c19ad-109">Windows has standalone installers that can be used to install the .NET Core 3.0 SDK:</span></span>

- [<span data-ttu-id="c19ad-110">Procesory x64 (64 bitů)</span><span class="sxs-lookup"><span data-stu-id="c19ad-110">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0) 
- [<span data-ttu-id="c19ad-111">Procesory x86 (32 bitů)</span><span class="sxs-lookup"><span data-stu-id="c19ad-111">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="c19ad-112">Instalace pomocí instalačního programu</span><span class="sxs-lookup"><span data-stu-id="c19ad-112">Install with an installer</span></span>

<span data-ttu-id="c19ad-113">macOS má samostatné instalační programy, které se dají použít k instalaci sady .NET Core 3,0 SDK:</span><span class="sxs-lookup"><span data-stu-id="c19ad-113">macOS has standalone installers that can be used to install the .NET Core 3.0 SDK:</span></span>

- [<span data-ttu-id="c19ad-114">Procesory x64 (64 bitů)</span><span class="sxs-lookup"><span data-stu-id="c19ad-114">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="c19ad-115">Instalace pomocí Správce balíčků</span><span class="sxs-lookup"><span data-stu-id="c19ad-115">Install with a package manager</span></span>

<span data-ttu-id="c19ad-116">.NET Core SDK můžete nainstalovat pomocí mnoha běžných správců balíčků pro Linux.</span><span class="sxs-lookup"><span data-stu-id="c19ad-116">You can install the .NET Core SDK with many of the common Linux package managers.</span></span> <span data-ttu-id="c19ad-117">Další informace najdete v tématu [Správce balíčků pro Linux – instalace .NET Core](linux-package-managers.md).</span><span class="sxs-lookup"><span data-stu-id="c19ad-117">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="c19ad-118">Stažení a ruční instalace</span><span class="sxs-lookup"><span data-stu-id="c19ad-118">Download and manually install</span></span>

<span data-ttu-id="c19ad-119">K extrakci sady SDK a zpřístupnění příkazů v terminálu nejprve [Stáhněte](#all-net-core-downloads) binární verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c19ad-119">To extract the SDK and make the commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="c19ad-120">Pak otevřete terminál a spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="c19ad-120">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-3.0.101-linux-musl-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="c19ad-121">Výše uvedené příkazy zpřístupní pouze příkazy sady .NET SDK dostupné pro relaci terminálu, ve které byla spuštěna.</span><span class="sxs-lookup"><span data-stu-id="c19ad-121">The above commands will only make the .NET SDK commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="c19ad-122">Úpravou profilu prostředí můžete tyto příkazy trvale přidat.</span><span class="sxs-lookup"><span data-stu-id="c19ad-122">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="c19ad-123">K dispozici je řada různých prostředí pro Linux a každá má jiný profil.</span><span class="sxs-lookup"><span data-stu-id="c19ad-123">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="c19ad-124">Příklad:</span><span class="sxs-lookup"><span data-stu-id="c19ad-124">For example:</span></span>
>
> - <span data-ttu-id="c19ad-125">**Prostředí bash**: *~/. bash_profile*, *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="c19ad-125">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="c19ad-126">**Korn shell**: *~/.KSHRC* nebo *. Profile*</span><span class="sxs-lookup"><span data-stu-id="c19ad-126">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="c19ad-127">**Prostředí Z**: *~/.zshrc* nebo *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="c19ad-127">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
> 
> <span data-ttu-id="c19ad-128">Upravte příslušný zdrojový soubor pro prostředí a přidejte `:$HOME/dotnet` na konec existujícího příkazu `PATH`.</span><span class="sxs-lookup"><span data-stu-id="c19ad-128">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="c19ad-129">Pokud není zahrnutý žádný příkaz `PATH`, přidejte nový řádek s `export PATH=$PATH:$HOME/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="c19ad-129">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="c19ad-130">Přidejte také `export DOTNET_ROOT=$HOME/dotnet` na konec souboru.</span><span class="sxs-lookup"><span data-stu-id="c19ad-130">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="c19ad-131">Instalace se sadou Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c19ad-131">Install with Visual Studio</span></span>

<span data-ttu-id="c19ad-132">Pokud používáte Visual Studio pro vývoj aplikací .NET Core, v následující tabulce je popsána minimální požadovaná verze sady Visual Studio na základě cílové verze .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="c19ad-132">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="c19ad-133">Verze .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="c19ad-133">.NET Core SDK version</span></span> | <span data-ttu-id="c19ad-134">Verze sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c19ad-134">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="c19ad-135">3,1 Preview</span><span class="sxs-lookup"><span data-stu-id="c19ad-135">3.1 Preview</span></span>           | <span data-ttu-id="c19ad-136">Visual Studio 2019 verze 16,4 Preview nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="c19ad-136">Visual Studio 2019 version 16.4 preview or higher.</span></span> |
| <span data-ttu-id="c19ad-137">3,0</span><span class="sxs-lookup"><span data-stu-id="c19ad-137">3.0</span></span>                   | <span data-ttu-id="c19ad-138">Visual Studio 2019 verze 16,3 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="c19ad-138">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="c19ad-139">2.2</span><span class="sxs-lookup"><span data-stu-id="c19ad-139">2.2</span></span>                   | <span data-ttu-id="c19ad-140">Visual Studio 2017 verze 15,9 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="c19ad-140">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="c19ad-141">2.1</span><span class="sxs-lookup"><span data-stu-id="c19ad-141">2.1</span></span>                   | <span data-ttu-id="c19ad-142">Visual Studio 2017 verze 15,7 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="c19ad-142">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="c19ad-143">Pokud již máte nainstalováno Visual Studio, můžete si ověřit verzi pomocí následujících kroků.</span><span class="sxs-lookup"><span data-stu-id="c19ad-143">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="c19ad-144">Otevřít Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c19ad-144">Open Visual Studio.</span></span>
01. <span data-ttu-id="c19ad-145">Vyberte **nápovědu** > **o Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="c19ad-145">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="c19ad-146">Přečtěte si číslo verze v dialogovém okně **o produktu** .</span><span class="sxs-lookup"><span data-stu-id="c19ad-146">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="c19ad-147">Visual Studio může nainstalovat nejnovější .NET Core SDK a modul runtime.</span><span class="sxs-lookup"><span data-stu-id="c19ad-147">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="c19ad-148">[Stáhněte si Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="c19ad-148">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="c19ad-149">Vyberte úlohu.</span><span class="sxs-lookup"><span data-stu-id="c19ad-149">Select a workload</span></span>

<span data-ttu-id="c19ad-150">Při instalaci nebo úpravách sady Visual Studio vyberte jednu z následujících úloh v závislosti na typu aplikace, kterou sestavujete:</span><span class="sxs-lookup"><span data-stu-id="c19ad-150">When installing or modifying Visual Studio, select one of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="c19ad-151">Úloha **vývoje .NET Core pro více platforem** v části **Další sady nástrojů** .</span><span class="sxs-lookup"><span data-stu-id="c19ad-151">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="c19ad-152">Úlohy **vývoje ASP.NET a webu** v části **web & Cloud** .</span><span class="sxs-lookup"><span data-stu-id="c19ad-152">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="c19ad-153">Úlohy **vývoje Azure** v části **web & cloudu** .</span><span class="sxs-lookup"><span data-stu-id="c19ad-153">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="c19ad-154">Úloha **vývoj desktopových aplikací .NET** v části **Desktop & Mobile** .</span><span class="sxs-lookup"><span data-stu-id="c19ad-154">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="c19ad-155">[![Windows Visual Studio 2019 s úlohou .NET Core](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="c19ad-155">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="c19ad-156">Instalace pomocí Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="c19ad-156">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="c19ad-157">Visual Studio pro Mac nainstaluje .NET Core SDK při výběru úlohy **.NET Core** .</span><span class="sxs-lookup"><span data-stu-id="c19ad-157">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="c19ad-158">Chcete-li začít s vývojem .NET Core v macOS, přečtěte si téma [instalace sady Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="c19ad-158">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span>

<span data-ttu-id="c19ad-159">[![macOS sady Visual Studio 2019 pro Mac s funkcí úlohy .NET Core](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="c19ad-159">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="c19ad-160">Nainstalovat společně Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c19ad-160">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="c19ad-161">Visual Studio Code je výkonný a prostý Editor zdrojového kódu, který běží na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="c19ad-161">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="c19ad-162">Visual Studio Code je k dispozici pro Windows, macOS a Linux.</span><span class="sxs-lookup"><span data-stu-id="c19ad-162">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="c19ad-163">I když Visual Studio Code nepřichází s automatizovaným instalačním programem .NET Core, jako je Visual Studio, přidání podpory .NET Core je jednoduché.</span><span class="sxs-lookup"><span data-stu-id="c19ad-163">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="c19ad-164">[Stáhněte a nainstalujte Visual Studio Code](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="c19ad-164">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="c19ad-165">[Stáhněte a nainstalujte .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="c19ad-165">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="c19ad-166">[Nainstalujte C# rozšíření z webu Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span><span class="sxs-lookup"><span data-stu-id="c19ad-166">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span></span>

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="c19ad-167">Instalace pomocí automatizace PowerShellu</span><span class="sxs-lookup"><span data-stu-id="c19ad-167">Install with PowerShell automation</span></span>

<span data-ttu-id="c19ad-168">[Dotnet – instalační skripty](../tools/dotnet-install-script.md) se používají pro automatizaci a pro instalaci sady SDK bez správy.</span><span class="sxs-lookup"><span data-stu-id="c19ad-168">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="c19ad-169">Skript si můžete stáhnout z [referenční stránky dotnet-install Script](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="c19ad-169">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="c19ad-170">Skript ve výchozím nastavení instaluje nejnovější verzi [LTS (Long Term support)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což je .net Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="c19ad-170">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="c19ad-171">Chcete-li nainstalovat aktuální vydání rozhraní .NET Core, spusťte skript s následujícím přepínačem.</span><span class="sxs-lookup"><span data-stu-id="c19ad-171">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="c19ad-172">Instalace pomocí služby bash Automation</span><span class="sxs-lookup"><span data-stu-id="c19ad-172">Install with bash automation</span></span>

<span data-ttu-id="c19ad-173">[Dotnet – instalační skripty](../tools/dotnet-install-script.md) se používají pro automatizaci a pro instalaci sady SDK bez správy.</span><span class="sxs-lookup"><span data-stu-id="c19ad-173">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="c19ad-174">Skript si můžete stáhnout z [referenční stránky dotnet-install Script](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="c19ad-174">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="c19ad-175">Skript ve výchozím nastavení instaluje nejnovější verzi [LTS (Long Term support)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což je .net Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="c19ad-175">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="c19ad-176">Chcete-li nainstalovat aktuální vydání rozhraní .NET Core, spusťte skript s následujícím přepínačem.</span><span class="sxs-lookup"><span data-stu-id="c19ad-176">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="c19ad-177">Všechny soubory ke stažení pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="c19ad-177">All .NET Core downloads</span></span>

<span data-ttu-id="c19ad-178">.NET Core můžete stáhnout a nainstalovat přímo s jedním z následujících odkazů:</span><span class="sxs-lookup"><span data-stu-id="c19ad-178">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="c19ad-179">Soubory ke stažení pro .NET Core 3,1 Preview</span><span class="sxs-lookup"><span data-stu-id="c19ad-179">.NET Core 3.1 Preview downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="c19ad-180">Soubory ke stažení pro .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="c19ad-180">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="c19ad-181">Soubory ke stažení pro .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="c19ad-181">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="c19ad-182">Soubory ke stažení pro .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="c19ad-182">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="c19ad-183">Docker</span><span class="sxs-lookup"><span data-stu-id="c19ad-183">Docker</span></span>

<span data-ttu-id="c19ad-184">Kontejnery poskytují jednoduchý způsob izolace vaší aplikace ze zbytku hostitelského systému.</span><span class="sxs-lookup"><span data-stu-id="c19ad-184">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="c19ad-185">Kontejnery na stejném počítači sdílejí jenom jádro a používají prostředky, které jsou dané aplikaci k.</span><span class="sxs-lookup"><span data-stu-id="c19ad-185">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="c19ad-186">.NET Core může běžet v kontejneru Docker.</span><span class="sxs-lookup"><span data-stu-id="c19ad-186">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="c19ad-187">Oficiální image Docker pro .NET Core jsou publikované ve službě Microsoft Container Registry (MCR) a jsou zjistitelné v [úložišti Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="c19ad-187">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="c19ad-188">Každé úložiště obsahuje obrázky pro různé kombinace rozhraní .NET (SDK nebo modulu runtime) a operačního systému, které můžete použít.</span><span class="sxs-lookup"><span data-stu-id="c19ad-188">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="c19ad-189">Společnost Microsoft poskytuje obrázky, které jsou upraveny pro konkrétní scénáře.</span><span class="sxs-lookup"><span data-stu-id="c19ad-189">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="c19ad-190">Například [úložiště ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) poskytuje obrázky, které jsou vytvořené pro spouštění ASP.NET Core aplikací v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="c19ad-190">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="c19ad-191">Další informace o použití .NET Core v kontejneru Docker najdete v tématu [Úvod do .NET a Docker](../docker/introduction.md) a [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="c19ad-191">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="c19ad-192">Další kroky</span><span class="sxs-lookup"><span data-stu-id="c19ad-192">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="c19ad-193">[Kurz: C# kurz Hello World](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="c19ad-193">[Tutorial: C# Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="c19ad-194">[Kurz: kurz Hello World Visual Basic](../tutorials/vb-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="c19ad-194">[Tutorial: Visual Basic Hello World tutorial](../tutorials/vb-with-visual-studio.md).</span></span>
- <span data-ttu-id="c19ad-195">[Kurz: vytvoření nové aplikace pomocí Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span><span class="sxs-lookup"><span data-stu-id="c19ad-195">[Tutorial: Create a new app with Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span></span>
- <span data-ttu-id="c19ad-196">[Kurz: kontejnerizace aplikace .NET Core](../docker/build-container.md)</span><span class="sxs-lookup"><span data-stu-id="c19ad-196">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="c19ad-197">[Kurz: Začínáme s MacOS](../tutorials/using-on-mac-vs.md).</span><span class="sxs-lookup"><span data-stu-id="c19ad-197">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="c19ad-198">[Kurz: vytvoření nové aplikace pomocí Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span><span class="sxs-lookup"><span data-stu-id="c19ad-198">[Tutorial: Create a new app with Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span></span>
- <span data-ttu-id="c19ad-199">[Kurz: kontejnerizace aplikace .NET Core](../docker/build-container.md)</span><span class="sxs-lookup"><span data-stu-id="c19ad-199">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
