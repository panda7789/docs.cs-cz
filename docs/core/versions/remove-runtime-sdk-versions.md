---
title: Odebrání modulu runtime .NET Core a sady SDK
description: Tento článek popisuje, jak určit, které verze modulu runtime .NET Core a sady SDK jsou momentálně nainstalované, a jak je odstranit v systémech Windows, Mac a Linux.
ms.date: 07/28/2018
author: billwagner
ms.author: wiwagn
ms.custom: seodec18
ms.openlocfilehash: 6d1012b8ddc5fd4a5ee8227902886727dbb10739
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970295"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a><span data-ttu-id="80b01-103">Postup odebrání modulu runtime .NET Core a sady SDK</span><span class="sxs-lookup"><span data-stu-id="80b01-103">How to remove the .NET Core Runtime and SDK</span></span>

<span data-ttu-id="80b01-104">V průběhu času, při instalaci aktualizovaných verzí modulu runtime .NET Core a sady SDK, můžete chtít z počítače odebrat zastaralé verze rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="80b01-104">Over time, as you install updated versions of the .NET Core runtime and SDK, you may want to remove outdated versions of .NET Core from your machine.</span></span> <span data-ttu-id="80b01-105">Odebrání starších verzí modulu runtime může změnit modul runtime zvolený tak, aby spouštěl aplikace sdíleného rozhraní, jak je popsáno v článku [Výběr verze .NET Core](selection.md).</span><span class="sxs-lookup"><span data-stu-id="80b01-105">Removing older versions of the runtime may change the runtime chosen to run shared framework applications, as detailed in the article on [.NET Core version selection](selection.md).</span></span>

## <a name="should-i-remove-a-version"></a><span data-ttu-id="80b01-106">Mám odebrat verzi?</span><span class="sxs-lookup"><span data-stu-id="80b01-106">Should I remove a version?</span></span>

<span data-ttu-id="80b01-107">Chování při [výběru verze .NET Core](selection.md) a kompatibilita modulu runtime .NET Core napříč aktualizacemi umožňují bezpečné odebrání předchozích verzí.</span><span class="sxs-lookup"><span data-stu-id="80b01-107">The [.NET Core version selection](selection.md) behaviors and the runtime compatibility of .NET Core across updates enables safe removal of previous versions.</span></span> <span data-ttu-id="80b01-108">Aktualizace modulu runtime .NET Core jsou kompatibilní s hlavní verzí "pásma", jako je například 1. x a 2. x.</span><span class="sxs-lookup"><span data-stu-id="80b01-108">.NET Core runtime updates are compatible within a major version 'band' such as 1.x and 2.x.</span></span> <span data-ttu-id="80b01-109">Kromě toho novější verze .NET Core SDK obecně udržují možnost vytvářet aplikace, které cílí na předchozí verze modulu runtime kompatibilním způsobem.</span><span class="sxs-lookup"><span data-stu-id="80b01-109">Additionally, newer releases of the .NET Core SDK generally maintain the ability to build applications that target previous versions of the runtime in a compatible manner.</span></span>

<span data-ttu-id="80b01-110">Obecně platí, že potřebujete jenom nejnovější sadu SDK a nejnovější verzi patch runtime, která je pro vaši aplikaci nutná.</span><span class="sxs-lookup"><span data-stu-id="80b01-110">In general, you only need the latest SDK and latest patch version of the runtimes required for your application.</span></span> <span data-ttu-id="80b01-111">Instance, ve kterých uchovává starší sada SDK nebo běhové verze, zahrnují údržbu aplikací založených na **projektech. JSON**.</span><span class="sxs-lookup"><span data-stu-id="80b01-111">Instances where retaining older SDK or Runtime versions include maintaining **project.json**-based applications.</span></span> <span data-ttu-id="80b01-112">Pokud vaše aplikace nemá konkrétní důvody pro předchozí sady SDK nebo moduly runtime, můžete starší verze odstranit bezpečně.</span><span class="sxs-lookup"><span data-stu-id="80b01-112">Unless your application has specific reasons for earlier SDKs or runtimes, you may safely remove older versions.</span></span>

## <a name="determine-what-is-installed"></a><span data-ttu-id="80b01-113">Určete, co je nainstalováno</span><span class="sxs-lookup"><span data-stu-id="80b01-113">Determine what is installed</span></span>

<span data-ttu-id="80b01-114">Počínaje rozhraním .NET Core 2,1 mají rozhraní .NET CLI možnosti, které můžete použít k vypsání verzí sady SDK a modulu runtime, které jsou nainstalovány na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="80b01-114">Starting with .NET Core 2.1, the .NET CLI has options you can use to list the versions of the SDK and runtime that are installed on your machine.</span></span>  <span data-ttu-id="80b01-115">Pomocí [`dotnet --list-sdks`](../tools/dotnet.md#options) zobrazíte seznam sad SDK nainstalovaných v počítači.</span><span class="sxs-lookup"><span data-stu-id="80b01-115">Use [`dotnet --list-sdks`](../tools/dotnet.md#options) to see the list of SDKs installed on your machine.</span></span> <span data-ttu-id="80b01-116">Použijte [`dotnet --list-runtimes`](../tools/dotnet.md#options) k zobrazení seznamu modulů runtime instalovaných v počítači.</span><span class="sxs-lookup"><span data-stu-id="80b01-116">Use [`dotnet --list-runtimes`](../tools/dotnet.md#options) to see the list of runtimes installed on your machine.</span></span> <span data-ttu-id="80b01-117">Následující text zobrazuje typický výstup pro Windows, macOS nebo Linux:</span><span class="sxs-lookup"><span data-stu-id="80b01-117">The following text shows typical output for Windows, macOS, or Linux:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[<span data-ttu-id="80b01-118">Windows</span><span class="sxs-lookup"><span data-stu-id="80b01-118">Windows</span></span>](#tab/windows)

```console
C:\> dotnet --list-sdks
2.1.200-preview-007474 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007480 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007509 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007570 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007576 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007587 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007589 [C:\Program Files\dotnet\sdk]
2.1.200 [C:\Program Files\dotnet\sdk]
2.1.201 [C:\Program Files\dotnet\sdk]
2.1.202 [C:\Program Files\dotnet\sdk]
2.1.300-preview2-008533 [C:\Program Files\dotnet\sdk]
2.1.300 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009063 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009088 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009171 [C:\Program Files\dotnet\sdk]

C:\> dotnet --list-runtimes
Microsoft.AspNetCore.All 2.1.0-preview2-final [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.0.6 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.7 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.9 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
```

# <a name="linuxtablinux"></a>[<span data-ttu-id="80b01-119">Linux</span><span class="sxs-lookup"><span data-stu-id="80b01-119">Linux</span></span>](#tab/linux)

```console
$ dotnet --list-sdks
1.0.1 [/usr/share/dotnet/sdk]
1.0.4 [/usr/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/share/dotnet/sdk]
2.0.0 [/usr/share/dotnet/sdk]
2.1.4 [/usr/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/share/dotnet/sdk]
2.1.300 [/usr/share/dotnet/sdk]
2.1.301 [/usr/share/dotnet/sdk]

$ dotnet --list-runtimes
Microsoft.AspNetCore.All 2.1.0-preview2-final [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 1.0.4 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.0.5 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.1 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.2 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview1-002111-00 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview2-25407-01 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.5 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
```

# <a name="macostabmacos"></a>[<span data-ttu-id="80b01-120">macOS</span><span class="sxs-lookup"><span data-stu-id="80b01-120">macOS</span></span>](#tab/macos)

```console
$ dotnet --list-sdks
1.0.1 [/usr/local/share/dotnet/sdk]
1.0.4 [/usr/local/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/local/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/local/share/dotnet/sdk]
2.0.0 [/usr/local/share/dotnet/sdk]
2.1.4 [/usr/local/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/local/share/dotnet/sdk]
2.1.300 [/usr/local/share/dotnet/sdk]
2.1.301 [/usr/local/share/dotnet/sdk]

$ dotnet --list-runtimes
Microsoft.AspNetCore.All 2.1.0-preview2-final [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 1.0.4 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.0.5 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.1 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.2 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview1-002111-00 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview2-25407-01 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.5 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
```

---

## <a name="uninstalling-net-core"></a><span data-ttu-id="80b01-121">Odinstalace .NET Core</span><span class="sxs-lookup"><span data-stu-id="80b01-121">Uninstalling .NET Core</span></span>

# <a name="windowstabwindows"></a>[<span data-ttu-id="80b01-122">Windows</span><span class="sxs-lookup"><span data-stu-id="80b01-122">Windows</span></span>](#tab/windows)

<span data-ttu-id="80b01-123">.NET Core používá dialogové okno **Přidat nebo odebrat programy** v systému Windows k odebrání verzí modulu runtime .NET Core a sady SDK.</span><span class="sxs-lookup"><span data-stu-id="80b01-123">.NET Core uses the Windows **Add/Remove Programs** dialog to remove versions of the .NET Core runtime and SDK.</span></span> <span data-ttu-id="80b01-124">Následující obrázek ukazuje dialog **Přidat nebo odebrat programy** s nainstalovaným několika verzemi modulu .NET runtime a sady SDK.</span><span class="sxs-lookup"><span data-stu-id="80b01-124">The following figure shows the **Add/Remove Programs** dialog with several versions of the .NET runtime and SDK installed.</span></span>

![Přidat nebo odebrat programy pro odebrání .NET Core](./media/remove-runtime-sdk-versions/programs-and-features.png)

<span data-ttu-id="80b01-126">Vyberte všechny verze, které chcete z počítače odebrat, a klikněte na **odinstalovat**.</span><span class="sxs-lookup"><span data-stu-id="80b01-126">Select any versions you want to remove from your machine and click **Uninstall**.</span></span>

# <a name="linuxtablinux"></a>[<span data-ttu-id="80b01-127">Linux</span><span class="sxs-lookup"><span data-stu-id="80b01-127">Linux</span></span>](#tab/linux)

<span data-ttu-id="80b01-128">K dispozici je více možností pro odinstalaci rozhraní .NET Core (buď sady SDK nebo modulu runtime) v systému Linux.</span><span class="sxs-lookup"><span data-stu-id="80b01-128">There are more options to uninstall .NET Core (either SDK or runtime) on Linux.</span></span> <span data-ttu-id="80b01-129">Nejlepším způsobem, jak odinstalovat .NET Core, je zrcadlit akci, kterou jste použili k instalaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="80b01-129">The best way for you to uninstall .NET Core is to mirror the action you used to install .NET Core.</span></span> <span data-ttu-id="80b01-130">Konkrétní závislosti závisí na zvolené distribuci a metodě instalace.</span><span class="sxs-lookup"><span data-stu-id="80b01-130">The specifics depend on your chosen distribution and the installation method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="80b01-131">V případě instalací Red Hat si přečtěte informace o instalaci a odinstalaci .NET Core v [příručce pro Red hat Začínáme](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) .</span><span class="sxs-lookup"><span data-stu-id="80b01-131">For Red Hat installations, consult the [Red Hat Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) for information on installing and uninstalling .NET Core.</span></span>

<span data-ttu-id="80b01-132">Počínaje rozhraním .NET Core 2,1 není nutné při upgradu pomocí Správce balíčků .NET Core SDK odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="80b01-132">Starting with .NET Core 2.1, there is no need to uninstall the .NET Core SDK when upgrading it using a package manager.</span></span> <span data-ttu-id="80b01-133">Správce `update` balíčků nebo `refresh` příkazy automaticky odebere starší verzi po úspěšné instalaci novější verze.</span><span class="sxs-lookup"><span data-stu-id="80b01-133">The package manager `update` or `refresh` commands will automatically remove the older version upon the successful installation of a newer version.</span></span>

<span data-ttu-id="80b01-134">Pokud jste nainstalovali .NET Core pomocí Správce balíčků, použijte stejného správce balíčků pro odinstalaci sady .NET SDK nebo modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="80b01-134">If you installed .NET Core using a package manager, you use that same package manager to uninstall .NET SDK or runtime.</span></span> <span data-ttu-id="80b01-135">Instalace .NET Core podporují většinu oblíbených správců balíčků.</span><span class="sxs-lookup"><span data-stu-id="80b01-135">.NET Core installations support most popular package managers.</span></span> <span data-ttu-id="80b01-136">V dokumentaci pro správce balíčků distribuce vyhledejte přesnou syntaxi vašeho prostředí.</span><span class="sxs-lookup"><span data-stu-id="80b01-136">Consult the documentation for your distribution's package manager for the precise syntax on your environment:</span></span>

- <span data-ttu-id="80b01-137">[apt-get (8)](https://linux.die.net/man/8/apt-get) se používá v systémech založených na Debian, včetně Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="80b01-137">[apt-get(8)](https://linux.die.net/man/8/apt-get) is used by Debian based systems, including Ubuntu.</span></span>
- <span data-ttu-id="80b01-138">[Yumu (8)](https://linux.die.net/man/8/yum) se používá na Fedora, CentOS a Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="80b01-138">[yum(8)](https://linux.die.net/man/8/yum) is used on Fedora, CentOS, and Oracle Linux.</span></span>
- <span data-ttu-id="80b01-139">[zypperu (8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) se používá v systémech OPENSUSE a SUSE Linux Enterprise (SLES).</span><span class="sxs-lookup"><span data-stu-id="80b01-139">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) is used on openSUSE and SUSE Linux Enterprise System (SLES).</span></span>
- <span data-ttu-id="80b01-140">[DNF (8)](https://dnf.readthedocs.io/en/latest/command_ref.html) se používá v Fedora.</span><span class="sxs-lookup"><span data-stu-id="80b01-140">[dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) is used on Fedora.</span></span>

<span data-ttu-id="80b01-141">V téměř všech případech je `remove`příkaz k odebrání balíčku.</span><span class="sxs-lookup"><span data-stu-id="80b01-141">In almost all cases, the command to remove a package is `remove`.</span></span>

<span data-ttu-id="80b01-142">Název balíčku pro instalaci .NET Core SDK pro většinu správců balíčků je `dotnet-sdk`následovaný číslem verze.</span><span class="sxs-lookup"><span data-stu-id="80b01-142">The package name for the .NET Core SDK installation for most package managers is `dotnet-sdk`, followed by the version number.</span></span> <span data-ttu-id="80b01-143">Počínaje verzí 2.1.300 .NET Core SDK a verzí `2.1` modulu runtime jsou nutná pouze čísla hlavní verze a podverze. například .NET Core SDK verze 2.1.300 může být odkazována jako balíček. `dotnet-sdk-2.1`</span><span class="sxs-lookup"><span data-stu-id="80b01-143">Starting with the version 2.1.300 of the .NET Core SDK and version `2.1` of the runtime, only the major and minor version numbers are necessary: for example, the .NET Core SDK version 2.1.300 can be referenced as the package `dotnet-sdk-2.1`.</span></span> <span data-ttu-id="80b01-144">Předchozí verze vyžadují řetězec celé verze: například `dotnet-sdk-2.1.200` by vyžadovala 2.1.200 verze .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="80b01-144">Prior versions require the entire version string: for example, `dotnet-sdk-2.1.200` would be required for version 2.1.200 of the .NET Core SDK.</span></span>

<span data-ttu-id="80b01-145">Pro počítače, které mají nainstalované pouze modul runtime a nikoli sadu SDK, je `dotnet-runtime-<version>` název balíčku pro modul runtime .NET Core a `aspnetcore-runtime-<version>` pro celý zásobník modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="80b01-145">For machines that have installed only the runtime, and not the SDK, the package name is `dotnet-runtime-<version>` for the .NET Core runtime, and `aspnetcore-runtime-<version>` for the entire runtime stack.</span></span>

<span data-ttu-id="80b01-146">Instalace .NET Core před 2,0 nenainstalovala hostitelskou aplikaci, pokud byla sada SDK odinstalována pomocí Správce balíčků.</span><span class="sxs-lookup"><span data-stu-id="80b01-146">.NET Core installations prior to 2.0 did not uninstall the host application when the SDK was uninstalled using the package manager.</span></span> <span data-ttu-id="80b01-147">Pomocí `apt-get`příkazu je tento příkaz:</span><span class="sxs-lookup"><span data-stu-id="80b01-147">Using `apt-get`, the command is:</span></span>

```bash
apt-get remove dotnet-host
```

<span data-ttu-id="80b01-148">Všimněte si, že není připojená `dotnet-host`žádná verze.</span><span class="sxs-lookup"><span data-stu-id="80b01-148">Note that there is no version attached to `dotnet-host`.</span></span>

<span data-ttu-id="80b01-149">Pokud jste nainstalovali tarballu pomocí nástroje, je nutné pomocí ruční metody odebrat rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="80b01-149">If you installed using a tarball, you must remove .NET Core using the manual method.</span></span>

<span data-ttu-id="80b01-150">Sady SDK a moduly runtime odeberete samostatně tak, že odeberete adresář, který obsahuje tuto verzi.</span><span class="sxs-lookup"><span data-stu-id="80b01-150">You remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="80b01-151">Chcete-li například odebrat sadu 1.0.1 SDK a modul runtime, použijte následující příkazy bash:</span><span class="sxs-lookup"><span data-stu-id="80b01-151">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="80b01-152">Nadřazené adresáře pro sadu SDK a modul runtime jsou uvedeny ve výstupu `dotnet --list-sdks` příkazu a `dotnet --list-runtimes` , jak je znázorněno v předchozí tabulce.</span><span class="sxs-lookup"><span data-stu-id="80b01-152">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

# <a name="macostabmacos"></a>[<span data-ttu-id="80b01-153">macOS</span><span class="sxs-lookup"><span data-stu-id="80b01-153">macOS</span></span>](#tab/macos)

<span data-ttu-id="80b01-154">V systému Mac musíte sady SDK a moduly runtime odebrat samostatně odebráním adresáře, který tuto verzi obsahuje.</span><span class="sxs-lookup"><span data-stu-id="80b01-154">On Mac, you must remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="80b01-155">Chcete-li například odebrat sadu 1.0.1 SDK a modul runtime, použijte následující příkazy bash:</span><span class="sxs-lookup"><span data-stu-id="80b01-155">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/local/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="80b01-156">Nadřazené adresáře pro sadu SDK a modul runtime jsou uvedeny ve výstupu `dotnet --list-sdks` příkazu a `dotnet --list-runtimes` , jak je znázorněno v předchozí tabulce.</span><span class="sxs-lookup"><span data-stu-id="80b01-156">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

---
