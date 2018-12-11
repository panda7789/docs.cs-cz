---
title: Odebrání modulu runtime .NET Core a sady SDK
description: Tento článek popisuje, jak určit, které verze modulu Runtime .NET Core a sady SDK jsou aktuálně nainstalované a poté jak odebrat Windows, Mac a Linux.
ms.date: 07/28/2018
author: billwagner
ms.author: wiwagn
ms.custom: seodec18
ms.openlocfilehash: 6204a28200f1db6350e695a9ab29502c46c25590
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129698"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a><span data-ttu-id="850c3-103">Odebrání modulu Runtime .NET Core a sady SDK</span><span class="sxs-lookup"><span data-stu-id="850c3-103">How to remove the .NET Core Runtime and SDK</span></span>

<span data-ttu-id="850c3-104">V průběhu času při instalaci aktualizované verze modulu runtime .NET Core a sady SDK, můžete chtít odebrat zastaralé verzích .NET Core z vašeho počítače.</span><span class="sxs-lookup"><span data-stu-id="850c3-104">Over time, as you install updated versions of the .NET Core runtime and SDK, you may want to remove outdated versions of .NET Core from your machine.</span></span> <span data-ttu-id="850c3-105">Odebírají se starší verze modulu runtime se může změnit modul runtime se rozhodli spustit sdílené architektuře aplikací podle popisu v článku na [výběr verze .NET Core](selection.md).</span><span class="sxs-lookup"><span data-stu-id="850c3-105">Removing older versions of the runtime may change the runtime chosen to run shared framework applications, as detailed in the article on [.NET Core version selection](selection.md).</span></span>

## <a name="should-i-remove-a-version"></a><span data-ttu-id="850c3-106">Můžu odebrat verzi?</span><span class="sxs-lookup"><span data-stu-id="850c3-106">Should I remove a version?</span></span>

<span data-ttu-id="850c3-107">[Výběr verze .NET Core](selection.md) chování a kompatibilitu modulu runtime .NET Core napříč aktualizace umožňuje bezpečné odebrání předchozí verze.</span><span class="sxs-lookup"><span data-stu-id="850c3-107">The [.NET Core version selection](selection.md) behaviors and the runtime compatibility of .NET Core across updates enables safe removal of previous versions.</span></span> <span data-ttu-id="850c3-108">Aktualizace modulu runtime .NET core jsou kompatibilní v rámci hlavní verzi "vzdálené", jako je například 1.x a 2.x.</span><span class="sxs-lookup"><span data-stu-id="850c3-108">.NET Core runtime updates are compatible within a major version 'band' such as 1.x and 2.x.</span></span> <span data-ttu-id="850c3-109">Kromě toho novější verze sady .NET Core SDK obecně zachována možnost vytvářet aplikace, které jsou cílové předchozí verze modulu runtime kompatibilní způsobem.</span><span class="sxs-lookup"><span data-stu-id="850c3-109">Additionally, newer releases of the .NET Core SDK generally maintain the ability to build applications that target previous versions of the runtime in a compatible manner.</span></span>

<span data-ttu-id="850c3-110">Obecně stačí pouze nejnovější sadu SDK a nejnovější opravy verzi modulů runtime, požadované pro vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="850c3-110">In general, you only need the latest SDK and latest patch version of the runtimes required for your application.</span></span> <span data-ttu-id="850c3-111">Pokud zachování starší verze sady SDK nebo modul Runtime patří Údržba instancí **project.json**– na základě aplikací.</span><span class="sxs-lookup"><span data-stu-id="850c3-111">Instances where retaining older SDK or Runtime versions include maintaining **project.json**-based applications.</span></span> <span data-ttu-id="850c3-112">Pokud aplikace nemá konkrétní důvod pro starší verzi sady SDK nebo modulů runtime, můžete bezpečně odstranit starší verze.</span><span class="sxs-lookup"><span data-stu-id="850c3-112">Unless your application has specific reasons for earlier SDKs or runtimes, you may safely remove older versions.</span></span>

## <a name="determine-what-is-installed"></a><span data-ttu-id="850c3-113">Zjistit, co je nainstalována</span><span class="sxs-lookup"><span data-stu-id="850c3-113">Determine what is installed</span></span>

<span data-ttu-id="850c3-114">Počínaje .NET Core 2.1, rozhraní příkazového řádku .NET poskytuje možnosti, které slouží k výpisu verze sady SDK a modulu runtime, který je na vašem počítači nainstalovaný.</span><span class="sxs-lookup"><span data-stu-id="850c3-114">Starting with .NET Core 2.1, the .NET CLI has options you can use to list the versions of the SDK and runtime that are installed on your machine.</span></span>  <span data-ttu-id="850c3-115">Použití [ `dotnet --list-sdks` ](../tools/dotnet.md#options) zobrazíte seznam sad SDK na vašem počítači nainstalovaný.</span><span class="sxs-lookup"><span data-stu-id="850c3-115">Use [`dotnet --list-sdks`](../tools/dotnet.md#options) to see the list of SDKs installed on your machine.</span></span> <span data-ttu-id="850c3-116">Použití [ `dotnet --list-runtimes` ](../tools/dotnet.md#options) zobrazíte seznam modulů runtime na vašem počítači nainstalovaný.</span><span class="sxs-lookup"><span data-stu-id="850c3-116">Use [`dotnet --list-runtimes`](../tools/dotnet.md#options) to see the list of runtimes installed on your machine.</span></span> <span data-ttu-id="850c3-117">Následující text uvádí typické výstup pro Windows, macOS nebo Linux:</span><span class="sxs-lookup"><span data-stu-id="850c3-117">The following text shows typical output for Windows, macOS, or Linux:</span></span>

# <a name="windowstabwindows"></a>[<span data-ttu-id="850c3-118">Windows</span><span class="sxs-lookup"><span data-stu-id="850c3-118">Windows</span></span>](#tab/windows)

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

# <a name="linuxtablinux"></a>[<span data-ttu-id="850c3-119">Linux</span><span class="sxs-lookup"><span data-stu-id="850c3-119">Linux</span></span>](#tab/linux)

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

# <a name="macostabmacos"></a>[<span data-ttu-id="850c3-120">macOS</span><span class="sxs-lookup"><span data-stu-id="850c3-120">macOS</span></span>](#tab/macos)

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

***

## <a name="uninstalling-net-core"></a><span data-ttu-id="850c3-121">Odinstalování rozhraní .NET Core</span><span class="sxs-lookup"><span data-stu-id="850c3-121">Uninstalling .NET Core</span></span>

# <a name="windowstabwindows"></a>[<span data-ttu-id="850c3-122">Windows</span><span class="sxs-lookup"><span data-stu-id="850c3-122">Windows</span></span>](#tab/windows)

<span data-ttu-id="850c3-123">.NET core používá Windows **přidat nebo odebrat programy** dialogové okno odebrat verze modulu runtime .NET Core a sady SDK.</span><span class="sxs-lookup"><span data-stu-id="850c3-123">.NET Core uses the Windows **Add/Remove Programs** dialog to remove versions of the .NET Core runtime and SDK.</span></span> <span data-ttu-id="850c3-124">Následující obrázek ukazuje **přidat nebo odebrat programy** dialogové okno s několika verzí modulu runtime .NET a nainstalované sady SDK.</span><span class="sxs-lookup"><span data-stu-id="850c3-124">The following figure shows the **Add/Remove Programs** dialog with several versions of the .NET runtime and SDK installed.</span></span>

![Přidat nebo odebrat programy se odebrat .NET Core](./media/remove-runtime-sdk-versions/programs-and-features.png)

<span data-ttu-id="850c3-126">Vyberte všechny verze, kterou chcete odebrat z počítače a klikněte na tlačítko **odinstalovat**.</span><span class="sxs-lookup"><span data-stu-id="850c3-126">Select any versions you want to remove from your machine and click **Uninstall**.</span></span>

# <a name="linuxtablinux"></a>[<span data-ttu-id="850c3-127">Linux</span><span class="sxs-lookup"><span data-stu-id="850c3-127">Linux</span></span>](#tab/linux)

<span data-ttu-id="850c3-128">Existují další možnosti odinstalace .NET Core (SDK nebo modul runtime) v Linuxu.</span><span class="sxs-lookup"><span data-stu-id="850c3-128">There are more options to uninstall .NET Core (either SDK or runtime) on Linux.</span></span> <span data-ttu-id="850c3-129">Nejlepší způsob pro vás k odinstalaci .NET Core je zrcadlení akci, kterou jste použili k instalaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="850c3-129">The best way for you to uninstall .NET Core is to mirror the action you used to install .NET Core.</span></span> <span data-ttu-id="850c3-130">Specifika závisí na zvoleném distribuce a metodu instalace.</span><span class="sxs-lookup"><span data-stu-id="850c3-130">The specifics depend on your chosen distribution and the installation method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="850c3-131">Pro Red Hat zařízení, najdete [Red Hat – Příručka Začínáme](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) informace o instalaci a odinstalaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="850c3-131">For Red Hat installations, consult the [Red Hat Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) for information on installing and uninstalling .NET Core.</span></span>

<span data-ttu-id="850c3-132">Počínaje .NET Core 2.1, není nutné odinstalovat sadu .NET Core SDK, při upgradu pomocí Správce balíčků.</span><span class="sxs-lookup"><span data-stu-id="850c3-132">Starting with .NET Core 2.1, there is no need to uninstall the .NET Core SDK when upgrading it using a package manager.</span></span> <span data-ttu-id="850c3-133">Správce balíčků `update` nebo `refresh` příkazy automaticky odebere starší verze po úspěšné instalaci novější verze.</span><span class="sxs-lookup"><span data-stu-id="850c3-133">The package manager `update` or `refresh` commands will automatically remove the older version upon the successful installation of a newer version.</span></span>

<span data-ttu-id="850c3-134">Pokud jste nainstalovali .NET Core pomocí Správce balíčků, použijte tento stejný správce balíčků pro odinstalaci sady .NET SDK nebo modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="850c3-134">If you installed .NET Core using a package manager, you use that same package manager to uninstall .NET SDK or runtime.</span></span> <span data-ttu-id="850c3-135">Instalace .NET core podporují nejoblíbenější správců balíčků.</span><span class="sxs-lookup"><span data-stu-id="850c3-135">.NET Core installations support most popular package managers.</span></span> <span data-ttu-id="850c3-136">Správce balíčků vaší distribuce pro přesné syntaxi ve vašem prostředí najdete v dokumentaci:</span><span class="sxs-lookup"><span data-stu-id="850c3-136">Consult the documentation for your distribution's package manager for the precise syntax on your environment:</span></span>

- <span data-ttu-id="850c3-137">[apt-Get(8)](https://linux.die.net/man/8/apt-get) používá Debian systémů, včetně Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="850c3-137">[apt-get(8)](https://linux.die.net/man/8/apt-get) is used by Debian based systems, including Ubuntu.</span></span>
- <span data-ttu-id="850c3-138">[YUM(8)](https://linux.die.net/man/8/yum) se používá na Fedora a CentOS, Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="850c3-138">[yum(8)](https://linux.die.net/man/8/yum) is used on Fedora, CentOS, and Oracle Linux.</span></span>
- <span data-ttu-id="850c3-139">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) se používá v openSUSE a operačním systémem SUSE Linux Enterprise systému (SLES).</span><span class="sxs-lookup"><span data-stu-id="850c3-139">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) is used on openSUSE and SUSE Linux Enterprise System (SLES).</span></span>
- <span data-ttu-id="850c3-140">[dnf(8)](https://dnf.readthedocs.io/latest/command_ref.html) se používá na Fedora.</span><span class="sxs-lookup"><span data-stu-id="850c3-140">[dnf(8)](https://dnf.readthedocs.io/latest/command_ref.html) is used on Fedora.</span></span>

<span data-ttu-id="850c3-141">V téměř všech případech se příkaz k odebrání balíčku je `remove`.</span><span class="sxs-lookup"><span data-stu-id="850c3-141">In almost all cases, the command to remove a package is `remove`.</span></span>

<span data-ttu-id="850c3-142">Název balíčku pro instalaci .NET Core SDK pro většinu Správce balíčků je `dotnet-sdk`následovaný číslo verze.</span><span class="sxs-lookup"><span data-stu-id="850c3-142">The package name for the .NET Core SDK installation for most package managers is `dotnet-sdk`, followed by the version number.</span></span> <span data-ttu-id="850c3-143">Počínaje verzí 2.1.300 .NET Core SDK a verze `2.1` modulu runtime jsou nezbytné pouze čísla hlavní verze a podverze: .NET Core SDK verze 2.1.300 například může být odkazováno jako balíček `dotnet-sdk-2.1`.</span><span class="sxs-lookup"><span data-stu-id="850c3-143">Starting with the version 2.1.300 of the .NET Core SDK and version `2.1` of the runtime, only the major and minor version numbers are necessary: for example, the .NET Core SDK version 2.1.300 can be referenced as the package `dotnet-sdk-2.1`.</span></span> <span data-ttu-id="850c3-144">Předchozí verze vyžadují celého řetězci verze: například `dotnet-sdk-2.1.200` by byla zapotřebí pro 2.1.200 verzi .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="850c3-144">Prior versions require the entire version string: for example, `dotnet-sdk-2.1.200` would be required for version 2.1.200 of the .NET Core SDK.</span></span>

<span data-ttu-id="850c3-145">Pro počítače, které jste nainstalovali pouze modul runtime a ne sadu SDK, je název balíčku `dotnet-runtime-<version>` pro modul runtime .NET Core a `aspnetcore-runtime-<version>` pro zásobník celý modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="850c3-145">For machines that have installed only the runtime, and not the SDK, the package name is `dotnet-runtime-<version>` for the .NET Core runtime, and `aspnetcore-runtime-<version>` for the entire runtime stack.</span></span>

<span data-ttu-id="850c3-146">Instalace .NET core před 2.0 neodinstalovali hostitelská aplikace, když sada SDK byla odinstalována pomocí Správce balíčků.</span><span class="sxs-lookup"><span data-stu-id="850c3-146">.NET Core installations prior to 2.0 did not uninstall the host application when the SDK was uninstalled using the package manager.</span></span> <span data-ttu-id="850c3-147">Pomocí `apt-get`, má příkaz tuto podobu:</span><span class="sxs-lookup"><span data-stu-id="850c3-147">Using `apt-get`, the command is:</span></span>

```bash
apt-get remove dotnet-host
```

<span data-ttu-id="850c3-148">Všimněte si, že neexistuje žádná verze připojené k `dotnet-host`.</span><span class="sxs-lookup"><span data-stu-id="850c3-148">Note that there is no version attached to `dotnet-host`.</span></span>

<span data-ttu-id="850c3-149">Pokud jste si nainstalovali pomocí tarballu, musíte odebrat .NET Core pomocí ruční metodu.</span><span class="sxs-lookup"><span data-stu-id="850c3-149">If you installed using a tarball, you must remove .NET Core using the manual method.</span></span>

<span data-ttu-id="850c3-150">Můžete odebrat sady SDK a moduly runtime samostatně, odebráním adresáře, který obsahuje tuto verzi.</span><span class="sxs-lookup"><span data-stu-id="850c3-150">You remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="850c3-151">Například, chcete-li odebrat 1.0.1 SDK a modul runtime, použili byste následující příkazy bash:</span><span class="sxs-lookup"><span data-stu-id="850c3-151">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="850c3-152">Nadřazené adresáře sady SDK a modulu runtime jsou uvedené ve výstupu `dotnet --list-sdks` a `dotnet --list-runtimes` příkaz, jak je znázorněno v předchozí tabulce.</span><span class="sxs-lookup"><span data-stu-id="850c3-152">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

# <a name="macostabmacos"></a>[<span data-ttu-id="850c3-153">macOS</span><span class="sxs-lookup"><span data-stu-id="850c3-153">macOS</span></span>](#tab/macos)

<span data-ttu-id="850c3-154">Na počítači Mac je nutné odstranit sady SDK a moduly runtime samostatně, tak, že odeberete adresáře, který obsahuje tuto verzi.</span><span class="sxs-lookup"><span data-stu-id="850c3-154">On Mac, you must remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="850c3-155">Například, chcete-li odebrat 1.0.1 SDK a modul runtime, použili byste následující příkazy bash:</span><span class="sxs-lookup"><span data-stu-id="850c3-155">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/local/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="850c3-156">Nadřazené adresáře sady SDK a modulu runtime jsou uvedené ve výstupu `dotnet --list-sdks` a `dotnet --list-runtimes` příkaz, jak je znázorněno v předchozí tabulce.</span><span class="sxs-lookup"><span data-stu-id="850c3-156">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

---
