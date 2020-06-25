---
title: Odebrání modulu runtime .NET Core a sady SDK
description: Tento článek popisuje, jak určit, které verze modulu runtime .NET Core a sady SDK jsou momentálně nainstalované, a jak je odstranit v systémech Windows, Mac a Linux.
author: adegeo
ms.author: adegeo
ms.date: 04/28/2020
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 1e4a846cf5e3d0209f5ade873520ef64abc12e7c
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324645"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a><span data-ttu-id="55695-103">Postup odebrání modulu runtime .NET Core a sady SDK</span><span class="sxs-lookup"><span data-stu-id="55695-103">How to remove the .NET Core Runtime and SDK</span></span>

<span data-ttu-id="55695-104">V průběhu času, při instalaci aktualizovaných verzí modulu runtime .NET Core a sady SDK, můžete chtít z počítače odebrat zastaralé verze rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="55695-104">Over time, as you install updated versions of the .NET Core runtime and SDK, you may want to remove outdated versions of .NET Core from your machine.</span></span> <span data-ttu-id="55695-105">Odebrání starších verzí modulu runtime může změnit modul runtime zvolený tak, aby spouštěl aplikace sdíleného rozhraní, jak je popsáno v článku [Výběr verze .NET Core](../versions/selection.md).</span><span class="sxs-lookup"><span data-stu-id="55695-105">Removing older versions of the runtime may change the runtime chosen to run shared framework applications, as detailed in the article on [.NET Core version selection](../versions/selection.md).</span></span>

## <a name="should-i-remove-a-version"></a><span data-ttu-id="55695-106">Mám odebrat verzi?</span><span class="sxs-lookup"><span data-stu-id="55695-106">Should I remove a version?</span></span>

<span data-ttu-id="55695-107">Chování při [výběru verze .NET Core](../versions/selection.md) a kompatibilita modulu runtime .NET Core napříč aktualizacemi umožňují bezpečné odebrání předchozích verzí.</span><span class="sxs-lookup"><span data-stu-id="55695-107">The [.NET Core version selection](../versions/selection.md) behaviors and the runtime compatibility of .NET Core across updates enables safe removal of previous versions.</span></span> <span data-ttu-id="55695-108">Aktualizace modulu runtime .NET Core jsou kompatibilní s hlavní verzí "pásma", jako je například 1. x a 2. x.</span><span class="sxs-lookup"><span data-stu-id="55695-108">.NET Core runtime updates are compatible within a major version 'band' such as 1.x and 2.x.</span></span> <span data-ttu-id="55695-109">Kromě toho novější verze .NET Core SDK obecně udržují možnost vytvářet aplikace, které cílí na předchozí verze modulu runtime kompatibilním způsobem.</span><span class="sxs-lookup"><span data-stu-id="55695-109">Additionally, newer releases of the .NET Core SDK generally maintain the ability to build applications that target previous versions of the runtime in a compatible manner.</span></span>

<span data-ttu-id="55695-110">Obecně platí, že potřebujete jenom nejnovější sadu SDK a nejnovější verzi patch runtime, která je pro vaši aplikaci nutná.</span><span class="sxs-lookup"><span data-stu-id="55695-110">In general, you only need the latest SDK and latest patch version of the runtimes required for your application.</span></span> <span data-ttu-id="55695-111">Instance, kde byste mohli chtít zachovat starší verze sady SDK nebo běhové verze, zahrnují údržbu *project.jsch*aplikací.</span><span class="sxs-lookup"><span data-stu-id="55695-111">Instances where you might want to keep older SDK or runtime versions include maintaining *project.json*-based applications.</span></span> <span data-ttu-id="55695-112">Pokud vaše aplikace nemá konkrétní důvody pro předchozí sady SDK nebo moduly runtime, můžete starší verze odstranit bezpečně.</span><span class="sxs-lookup"><span data-stu-id="55695-112">Unless your application has specific reasons for earlier SDKs or runtimes, you may safely remove older versions.</span></span>

## <a name="determine-what-is-installed"></a><span data-ttu-id="55695-113">Určete, co je nainstalováno</span><span class="sxs-lookup"><span data-stu-id="55695-113">Determine what is installed</span></span>

<span data-ttu-id="55695-114">Počínaje rozhraním .NET Core 2,1 mají rozhraní .NET CLI možnosti, které můžete použít k vypsání verzí sady SDK a modulu runtime, které jsou nainstalovány na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="55695-114">Starting with .NET Core 2.1, the .NET CLI has options you can use to list the versions of the SDK and runtime that are installed on your machine.</span></span>  <span data-ttu-id="55695-115">Pomocí [`dotnet --list-sdks`](../tools/dotnet.md#options) zobrazíte seznam sad SDK nainstalovaných v počítači.</span><span class="sxs-lookup"><span data-stu-id="55695-115">Use [`dotnet --list-sdks`](../tools/dotnet.md#options) to see the list of SDKs installed on your machine.</span></span> <span data-ttu-id="55695-116">Použijte [`dotnet --list-runtimes`](../tools/dotnet.md#options) k zobrazení seznamu modulů runtime instalovaných v počítači.</span><span class="sxs-lookup"><span data-stu-id="55695-116">Use [`dotnet --list-runtimes`](../tools/dotnet.md#options) to see the list of runtimes installed on your machine.</span></span> <span data-ttu-id="55695-117">Další informace najdete v tématu [Jak ověřit, zda je rozhraní .NET Core již nainstalováno](how-to-detect-installed-versions.md).</span><span class="sxs-lookup"><span data-stu-id="55695-117">For more information, see [How to check that .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>

## <a name="uninstall-net-core"></a><span data-ttu-id="55695-118">Odinstalace .NET Core</span><span class="sxs-lookup"><span data-stu-id="55695-118">Uninstall .NET Core</span></span>

::: zone pivot="os-windows"

<span data-ttu-id="55695-119">.NET Core používá pro odebrání verzí modulu runtime .NET Core a sady SDK dialogové okno **funkce & aplikace** systému Windows.</span><span class="sxs-lookup"><span data-stu-id="55695-119">.NET Core uses the Windows **Apps & features** dialog to remove versions of the .NET Core runtime and SDK.</span></span> <span data-ttu-id="55695-120">Následující obrázek ukazuje dialogové okno **aplikace & funkce** .</span><span class="sxs-lookup"><span data-stu-id="55695-120">The following figure shows the **Apps & features** dialog.</span></span> <span data-ttu-id="55695-121">Můžete vyhledat **základní sadu SDK** pro filtrování a zobrazení nainstalovaných verzí rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="55695-121">You can search for **core sdk** to filter and show installed versions of .NET Core.</span></span>

![Přidat nebo odebrat programy pro odebrání .NET Core](./media/remove-runtime-sdk-versions/programs-and-features.png)

<span data-ttu-id="55695-123">Vyberte všechny verze, které chcete z počítače odebrat, a klikněte na **odinstalovat**.</span><span class="sxs-lookup"><span data-stu-id="55695-123">Select any versions you want to remove from your machine and click **Uninstall**.</span></span>

::: zone-end

::: zone pivot="os-linux"

<span data-ttu-id="55695-124">K dispozici je více možností pro odinstalaci rozhraní .NET Core (buď sady SDK nebo modulu runtime) v systému Linux.</span><span class="sxs-lookup"><span data-stu-id="55695-124">There are more options to uninstall .NET Core (either SDK or runtime) on Linux.</span></span> <span data-ttu-id="55695-125">Nejlepším způsobem, jak odinstalovat .NET Core, je zrcadlit akci, kterou jste použili k instalaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="55695-125">The best way for you to uninstall .NET Core is to mirror the action you used to install .NET Core.</span></span> <span data-ttu-id="55695-126">Konkrétní závislosti závisí na zvolené distribuci a metodě instalace.</span><span class="sxs-lookup"><span data-stu-id="55695-126">The specifics depend on your chosen distribution and the installation method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="55695-127">V případě instalací Red Hat si přečtěte informace o instalaci a odinstalaci .NET Core v [příručce pro Red hat Začínáme](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) .</span><span class="sxs-lookup"><span data-stu-id="55695-127">For Red Hat installations, consult the [Red Hat Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) for information on installing and uninstalling .NET Core.</span></span>

<span data-ttu-id="55695-128">Počínaje rozhraním .NET Core 2,1 není nutné při upgradu pomocí Správce balíčků .NET Core SDK odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="55695-128">Starting with .NET Core 2.1, there's no need to uninstall the .NET Core SDK when upgrading it using a package manager.</span></span> <span data-ttu-id="55695-129">Správce balíčků `update` nebo `refresh` příkazy automaticky odebere starší verzi po úspěšné instalaci novější verze.</span><span class="sxs-lookup"><span data-stu-id="55695-129">The package manager `update` or `refresh` commands will automatically remove the older version upon the successful installation of a newer version.</span></span>

<span data-ttu-id="55695-130">Pokud jste nainstalovali .NET Core pomocí Správce balíčků, použijte stejného správce balíčků pro odinstalaci sady .NET SDK nebo modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="55695-130">If you installed .NET Core using a package manager, you use that same package manager to uninstall .NET SDK or runtime.</span></span> <span data-ttu-id="55695-131">Instalace .NET Core podporují většinu oblíbených správců balíčků.</span><span class="sxs-lookup"><span data-stu-id="55695-131">.NET Core installations support most popular package managers.</span></span> <span data-ttu-id="55695-132">Přesnou syntaxi správce balíčků distribuce najdete v dokumentaci ke konkrétní syntaxi prostředí:</span><span class="sxs-lookup"><span data-stu-id="55695-132">Consult the documentation for your distribution's package manager for the precise syntax in your environment:</span></span>

- <span data-ttu-id="55695-133">[apt-get (8)](https://linux.die.net/man/8/apt-get) se používá v systémech založených na Debian, včetně Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="55695-133">[apt-get(8)](https://linux.die.net/man/8/apt-get) is used by Debian based systems, including Ubuntu.</span></span>
- <span data-ttu-id="55695-134">[Yumu (8)](https://linux.die.net/man/8/yum) se používá na Fedora, CentOS a Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="55695-134">[yum(8)](https://linux.die.net/man/8/yum) is used on Fedora, CentOS, and Oracle Linux.</span></span>
- <span data-ttu-id="55695-135">[zypperu (8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) se používá v systémech OPENSUSE a SUSE Linux Enterprise (SLES).</span><span class="sxs-lookup"><span data-stu-id="55695-135">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) is used on openSUSE and SUSE Linux Enterprise System (SLES).</span></span>
- <span data-ttu-id="55695-136">[DNF (8)](https://dnf.readthedocs.io/en/latest/command_ref.html) se používá v Fedora.</span><span class="sxs-lookup"><span data-stu-id="55695-136">[dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) is used on Fedora.</span></span>

<span data-ttu-id="55695-137">V téměř všech případech je příkaz k odebrání balíčku `remove` .</span><span class="sxs-lookup"><span data-stu-id="55695-137">In almost all cases, the command to remove a package is `remove`.</span></span>

<span data-ttu-id="55695-138">Název balíčku pro instalaci .NET Core SDK pro většinu správců balíčků je `dotnet-sdk` následovaný číslem verze.</span><span class="sxs-lookup"><span data-stu-id="55695-138">The package name for the .NET Core SDK installation for most package managers is `dotnet-sdk`, followed by the version number.</span></span> <span data-ttu-id="55695-139">Počínaje verzí 2.1.300 .NET Core SDK a verzí `2.1` modulu runtime jsou nutná pouze čísla hlavní verze a podverze. například .NET Core SDK verze 2.1.300 může být odkazována jako balíček `dotnet-sdk-2.1` .</span><span class="sxs-lookup"><span data-stu-id="55695-139">Starting with the version 2.1.300 of the .NET Core SDK and version `2.1` of the runtime, only the major and minor version numbers are necessary: for example, the .NET Core SDK version 2.1.300 can be referenced as the package `dotnet-sdk-2.1`.</span></span> <span data-ttu-id="55695-140">Předchozí verze vyžadují řetězec celé verze: například `dotnet-sdk-2.1.200` by vyžadovala 2.1.200 verze .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="55695-140">Prior versions require the entire version string: for example, `dotnet-sdk-2.1.200` would be required for version 2.1.200 of the .NET Core SDK.</span></span>

<span data-ttu-id="55695-141">Pro počítače, které mají nainstalované pouze modul runtime a nikoli sadu SDK, je název balíčku `dotnet-runtime-<version>` pro modul runtime .NET Core a `aspnetcore-runtime-<version>` pro celý zásobník modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="55695-141">For machines that have installed only the runtime, and not the SDK, the package name is `dotnet-runtime-<version>` for the .NET Core runtime, and `aspnetcore-runtime-<version>` for the entire runtime stack.</span></span>

<span data-ttu-id="55695-142">Instalace .NET Core starší než 2,0 odinstalovaly hostitelskou aplikaci, když se sada SDK odinstalovala pomocí Správce balíčků.</span><span class="sxs-lookup"><span data-stu-id="55695-142">.NET Core installations earlier than 2.0 didn't uninstall the host application when the SDK was uninstalled using the package manager.</span></span> <span data-ttu-id="55695-143">Pomocí `apt-get` příkazu je tento příkaz:</span><span class="sxs-lookup"><span data-stu-id="55695-143">Using `apt-get`, the command is:</span></span>

```bash
apt-get remove dotnet-host
```

<span data-ttu-id="55695-144">Všimněte si, že není připojená žádná verze `dotnet-host` .</span><span class="sxs-lookup"><span data-stu-id="55695-144">Note that there's no version attached to `dotnet-host`.</span></span>

<span data-ttu-id="55695-145">Pokud jste nainstalovali tarballu pomocí nástroje, je nutné pomocí ruční metody odebrat rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="55695-145">If you installed using a tarball, you must remove .NET Core using the manual method.</span></span>

<span data-ttu-id="55695-146">V systému Linux musíte sady SDK a moduly runtime odebrat samostatně odebráním adresářů se správou verzí.</span><span class="sxs-lookup"><span data-stu-id="55695-146">On Linux, you must remove the SDKs and runtimes separately, by removing the versioned directories.</span></span> <span data-ttu-id="55695-147">Jejich odebráním se odstraní sada SDK a modul runtime z disku.</span><span class="sxs-lookup"><span data-stu-id="55695-147">Removing them deletes the SDK and runtime from disk.</span></span> <span data-ttu-id="55695-148">Chcete-li například odebrat sadu 1.0.1 SDK a modul runtime, použijte následující příkazy bash:</span><span class="sxs-lookup"><span data-stu-id="55695-148">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
version="1.0.1"
sudo rm -rf /usr/local/share/dotnet/sdk/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.All/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/$version
sudo rm -rf /usr/local/share/dotnet/host/fxr/$version
```

<span data-ttu-id="55695-149">Nadřazené adresáře pro sadu SDK a modul runtime jsou uvedeny ve výstupu `dotnet --list-sdks` `dotnet --list-runtimes` příkazu a, jak je znázorněno v předchozí tabulce.</span><span class="sxs-lookup"><span data-stu-id="55695-149">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="55695-150">V systému Mac musíte sady SDK a moduly runtime odebrat samostatně tak, že odeberete adresáře s verzemi.</span><span class="sxs-lookup"><span data-stu-id="55695-150">On Mac, you must remove the SDKs and runtimes separately, by removing the versioned directories.</span></span> <span data-ttu-id="55695-151">Jejich odebráním se odstraní sada SDK a modul runtime z disku.</span><span class="sxs-lookup"><span data-stu-id="55695-151">Removing them deletes the SDK and runtime from disk.</span></span> <span data-ttu-id="55695-152">Chcete-li například odebrat sadu 1.0.1 SDK a modul runtime, použijte následující příkazy bash:</span><span class="sxs-lookup"><span data-stu-id="55695-152">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
version="1.0.1"
sudo rm -rf /usr/local/share/dotnet/sdk/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.All/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/$version
sudo rm -rf /usr/local/share/dotnet/host/fxr/$version
```

<span data-ttu-id="55695-153">Nadřazené adresáře pro sadu SDK a modul runtime jsou uvedeny ve výstupu `dotnet --list-sdks` `dotnet --list-runtimes` příkazu a, jak je znázorněno v předchozí tabulce.</span><span class="sxs-lookup"><span data-stu-id="55695-153">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

::: zone-end

## <a name="net-core-uninstall-tool"></a><span data-ttu-id="55695-154">Nástroj pro odinstalaci .NET Core</span><span class="sxs-lookup"><span data-stu-id="55695-154">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="55695-155">[Nástroj pro odinstalaci .NET Core](../additional-tools/uninstall-tool.md) ( `dotnet-core-uninstall` ) umožňuje odebrat sady SDK a moduly runtime .NET Core ze systému.</span><span class="sxs-lookup"><span data-stu-id="55695-155">The [.NET Core Uninstall Tool](../additional-tools/uninstall-tool.md) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and runtimes from a system.</span></span> <span data-ttu-id="55695-156">K dispozici je kolekce možností, pomocí kterých určíte, které verze se mají odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="55695-156">A collection of options is available to specify which versions should be uninstalled.</span></span>

## <a name="visual-studio-dependency-on-net-core-sdk-versions"></a><span data-ttu-id="55695-157">Závislost sady Visual Studio na .NET Core SDK verzích</span><span class="sxs-lookup"><span data-stu-id="55695-157">Visual Studio dependency on .NET Core SDK versions</span></span>

<span data-ttu-id="55695-158">Před Visual Studio 2019 verze 16,3 se instalátory sady Visual Studio nazývají samostatné instalační služby .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="55695-158">Before Visual Studio 2019 version 16.3, Visual Studio installers called the standalone .NET Core SDK installer.</span></span> <span data-ttu-id="55695-159">V důsledku toho se verze sady SDK zobrazí v dialogovém okně **aplikace pro Windows & funkce** .</span><span class="sxs-lookup"><span data-stu-id="55695-159">As a result, the SDK versions appear in the Windows **Apps & features** dialog.</span></span> <span data-ttu-id="55695-160">Odebrání sady .NET Core SDK, které byly nainstalovány v aplikaci Visual Studio pomocí samostatného instalačního programu, může poškodit aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="55695-160">Removing .NET Core SDKs that were installed by Visual Studio using the standalone installer may break Visual Studio.</span></span> <span data-ttu-id="55695-161">Pokud má aplikace Visual Studio problémy po odinstalaci sad SDK, spusťte v této konkrétní verzi sady Visual Studio opravu.</span><span class="sxs-lookup"><span data-stu-id="55695-161">If Visual Studio has problems after you uninstall SDKs, run Repair on that specific version of Visual Studio.</span></span> <span data-ttu-id="55695-162">V následující tabulce jsou uvedeny některé závislosti sady Visual Studio na .NET Core SDK verzích:</span><span class="sxs-lookup"><span data-stu-id="55695-162">The following table shows some of the Visual Studio dependencies on .NET Core SDK versions:</span></span>

| <span data-ttu-id="55695-163">Verze sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="55695-163">Visual Studio version</span></span>           | <span data-ttu-id="55695-164">Verze .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="55695-164">.NET Core SDK version</span></span>          |
|---------------------------------|--------------------------------|
| <span data-ttu-id="55695-165"> Visual Studio 2019 verze 16.2 </span><span class="sxs-lookup"><span data-stu-id="55695-165">Visual Studio 2019 version 16.2</span></span> | <span data-ttu-id="55695-166">.NET Core SDK 2.2.4 xx, 2.1.8 XX</span><span class="sxs-lookup"><span data-stu-id="55695-166">.NET Core SDK 2.2.4xx, 2.1.8xx</span></span> |
| <span data-ttu-id="55695-167"> Visual Studio 2019 verze 16.1</span><span class="sxs-lookup"><span data-stu-id="55695-167">Visual Studio 2019 version 16.1</span></span> | <span data-ttu-id="55695-168">.NET Core SDK 2.2.3 xx, 2.1.7 XX</span><span class="sxs-lookup"><span data-stu-id="55695-168">.NET Core SDK 2.2.3xx, 2.1.7xx</span></span> |
| <span data-ttu-id="55695-169">Visual Studio 2019 verze 16,0</span><span class="sxs-lookup"><span data-stu-id="55695-169">Visual Studio 2019 version 16.0</span></span> | <span data-ttu-id="55695-170">.NET Core SDK 2.2.2 xx, 2.1.6 xx</span><span class="sxs-lookup"><span data-stu-id="55695-170">.NET Core SDK 2.2.2xx, 2.1.6xx</span></span> |
| <span data-ttu-id="55695-171">Visual Studio 2017 verze 15,9</span><span class="sxs-lookup"><span data-stu-id="55695-171">Visual Studio 2017 version 15.9</span></span> | <span data-ttu-id="55695-172">.NET Core SDK 2.2.1 xx xx, 2.1.5 XX</span><span class="sxs-lookup"><span data-stu-id="55695-172">.NET Core SDK 2.2.1xx, 2.1.5xx</span></span> |
| <span data-ttu-id="55695-173">Visual Studio 2017 verze 15,8</span><span class="sxs-lookup"><span data-stu-id="55695-173">Visual Studio 2017 version 15.8</span></span> | <span data-ttu-id="55695-174">.NET Core SDK 2.1.4 XX</span><span class="sxs-lookup"><span data-stu-id="55695-174">.NET Core SDK 2.1.4xx</span></span>          |

<span data-ttu-id="55695-175">Počínaje verzí Visual Studio 2019 verze 16,3 se Visual Studio účtuje na vlastní kopii .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="55695-175">Starting with Visual Studio 2019 version 16.3, Visual Studio is in charge of its own copy of the .NET Core SDK.</span></span> <span data-ttu-id="55695-176">Z tohoto důvodu se tyto verze sady SDK už nezobrazuje v dialogovém okně **aplikace & funkce** .</span><span class="sxs-lookup"><span data-stu-id="55695-176">For that reason, you no longer see those SDK versions in the **Apps & features** dialog.</span></span>

## <a name="remove-the-nuget-fallback-folder"></a><span data-ttu-id="55695-177">Odebrat záložní složku NuGet</span><span class="sxs-lookup"><span data-stu-id="55695-177">Remove the NuGet fallback folder</span></span>

<span data-ttu-id="55695-178">Před sadou .NET Core 3,0 SDK .NET Core SDK Instalační programy používaly složku s názvem *NuGetFallbackFolder* k uložení mezipaměti balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="55695-178">Before .NET Core 3.0 SDK, the .NET Core SDK installers used a folder named *NuGetFallbackFolder* to store a cache of NuGet packages.</span></span> <span data-ttu-id="55695-179">Tato mezipaměť se použila během operací, jako je `dotnet restore` nebo `dotnet build /t:Restore` .</span><span class="sxs-lookup"><span data-stu-id="55695-179">This cache was used during operations such as `dotnet restore` or `dotnet build /t:Restore`.</span></span> <span data-ttu-id="55695-180">*NuGetFallbackFolder* se nachází v adresáři *C:\Program Files\dotnet\sdk* v systému Windows a v */usr/local/share/dotnet/SDK* na MacOS.</span><span class="sxs-lookup"><span data-stu-id="55695-180">The *NuGetFallbackFolder* is located at *C:\Program Files\dotnet\sdk* on Windows and at */usr/local/share/dotnet/sdk* on macOS.</span></span>

<span data-ttu-id="55695-181">Tuto složku můžete chtít odebrat, pokud:</span><span class="sxs-lookup"><span data-stu-id="55695-181">You may want to remove this folder, if:</span></span>

- <span data-ttu-id="55695-182">Vyvíjíte pouze pomocí .NET Core 3,0 SDK nebo novějších verzí.</span><span class="sxs-lookup"><span data-stu-id="55695-182">You're only developing using .NET Core 3.0 SDK or later versions.</span></span>
- <span data-ttu-id="55695-183">Vyvíjíte pomocí .NET Core SDK verzí starších než 3,0, ale můžete pracovat online.</span><span class="sxs-lookup"><span data-stu-id="55695-183">You're developing using .NET Core SDK versions earlier than 3.0, but you can work online.</span></span>

<span data-ttu-id="55695-184">Pokud chcete odebrat záložní složku NuGet, můžete ji odstranit, ale budete k tomu potřebovat oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="55695-184">If you want to remove the NuGet fallback folder, you can delete it, but you'll need admin privileges to do so.</span></span>

<span data-ttu-id="55695-185">Nedoporučuje se odstranit složku *dotnet* .</span><span class="sxs-lookup"><span data-stu-id="55695-185">It's not recommended to delete the *dotnet* folder.</span></span> <span data-ttu-id="55695-186">Tím by se odebraly všechny globální nástroje, které jste předtím nainstalovali.</span><span class="sxs-lookup"><span data-stu-id="55695-186">Doing so would remove any global tools you've previously installed.</span></span> <span data-ttu-id="55695-187">Také ve Windows:</span><span class="sxs-lookup"><span data-stu-id="55695-187">Also, on Windows:</span></span>

- <span data-ttu-id="55695-188">Budete přerušit Visual Studio 2019 verze 16,3 a novější.</span><span class="sxs-lookup"><span data-stu-id="55695-188">You'll break Visual Studio 2019 version 16.3 and later versions.</span></span> <span data-ttu-id="55695-189">Můžete spustit **opravu** pro obnovení.</span><span class="sxs-lookup"><span data-stu-id="55695-189">You can run **Repair** to recover.</span></span>
- <span data-ttu-id="55695-190">Pokud v dialogovém okně **aplikace & funkce** existují .NET Core SDKé položky, budou osamocené.</span><span class="sxs-lookup"><span data-stu-id="55695-190">If there are .NET Core SDK entries in the **Apps & features** dialog, they'll be orphaned.</span></span>
