---
title: Odebrání modulu runtime .NET a sady SDK
description: Pokyny k odebrání součásti modulu Runtime .NET Core a sady SDK Windows, Mac a Linux
ms.date: 07/28/2018
author: billwagner
ms.author: wiwagn
ms.openlocfilehash: 1806d1af3b10e44ccc2eff788d8958ca976fe85b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43557193"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a><span data-ttu-id="6a2f5-103">Odebrání modulu Runtime .NET Core a sady SDK</span><span class="sxs-lookup"><span data-stu-id="6a2f5-103">How to remove the .NET Core Runtime and SDK</span></span>

<span data-ttu-id="6a2f5-104">V průběhu času při instalaci aktualizované verze modulu runtime .NET Core a sady SDK, můžete chtít odebrat zastaralé verzích .NET Core z vašeho počítače.</span><span class="sxs-lookup"><span data-stu-id="6a2f5-104">Over time, as you install updated versions of the .NET Core runtime and SDK, you may want to remove outdated versions of .NET Core from your machine.</span></span> <span data-ttu-id="6a2f5-105">Odebírají se starší verze modulu runtime se může změnit modul runtime se rozhodli spustit sdílené architektuře aplikací podle popisu v článku na [výběr verze .NET Core](selection.md).</span><span class="sxs-lookup"><span data-stu-id="6a2f5-105">Removing older versions of the runtime may change the runtime chosen to run shared framework applications, as detailed in the article on [.NET Core version selection](selection.md).</span></span>

<span data-ttu-id="6a2f5-106">Počínaje .NET Core 2.1, rozhraní příkazového řádku .NET poskytuje možnosti, které slouží k výpisu verze sady SDK a modulu runtime, který je na vašem počítači nainstalovaný.</span><span class="sxs-lookup"><span data-stu-id="6a2f5-106">Starting with .NET Core 2.1, the .NET CLI has options you can use to list the versions of the SDK and runtime that are installed on your machine.</span></span>  <span data-ttu-id="6a2f5-107">Použití [ `dotnet --list-sdks` ](../tools/dotnet.md#options) zobrazíte seznam sad SDK na vašem počítači nainstalovaný.</span><span class="sxs-lookup"><span data-stu-id="6a2f5-107">Use [`dotnet --list-sdks`](../tools/dotnet.md#options) to see the list of SDKs installed on your machine.</span></span> <span data-ttu-id="6a2f5-108">Použití [ `dotnet --list-runtimes` ](../tools/dotnet.md#options) zobrazíte seznam modulů runtime na vašem počítači nainstalovaný.</span><span class="sxs-lookup"><span data-stu-id="6a2f5-108">Use [`dotnet --list-runtimes`](../tools/dotnet.md#options) to see the list of runtimes installed on your machine.</span></span> <span data-ttu-id="6a2f5-109">Následující text uvádí typické výstup pro Windows, macOS nebo Linux:</span><span class="sxs-lookup"><span data-stu-id="6a2f5-109">The following text shows typical output for Windows, macOS, or Linux:</span></span>

# <a name="windowstabwindows"></a>[<span data-ttu-id="6a2f5-110">Windows</span><span class="sxs-lookup"><span data-stu-id="6a2f5-110">Windows</span></span>](#tab/Windows)

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

# <a name="linuxtablinux"></a>[<span data-ttu-id="6a2f5-111">Linux</span><span class="sxs-lookup"><span data-stu-id="6a2f5-111">Linux</span></span>](#tab/Linux)

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

# <a name="macostabmacos"></a>[<span data-ttu-id="6a2f5-112">macOS</span><span class="sxs-lookup"><span data-stu-id="6a2f5-112">macOS</span></span>](#tab/macOS)

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

## <a name="uninstalling-net-core"></a><span data-ttu-id="6a2f5-113">Odinstalování rozhraní .NET Core</span><span class="sxs-lookup"><span data-stu-id="6a2f5-113">Uninstalling .NET Core</span></span>

# <a name="windowstabwindows"></a>[<span data-ttu-id="6a2f5-114">Windows</span><span class="sxs-lookup"><span data-stu-id="6a2f5-114">Windows</span></span>](#tab/Windows)

<span data-ttu-id="6a2f5-115">.NET core používá Windows **přidat nebo odebrat programy** dialogové okno odebrat verze modulu runtime .NET Core a sady SDK.</span><span class="sxs-lookup"><span data-stu-id="6a2f5-115">.NET Core uses the Windows **Add/Remove Programs** dialog to remove versions of the .NET Core runtime and SDK.</span></span> <span data-ttu-id="6a2f5-116">Následující obrázek ukazuje **přidat nebo odebrat programy** dialogové okno s několika verzí modulu runtime .NET a nainstalované sady SDK.</span><span class="sxs-lookup"><span data-stu-id="6a2f5-116">The following figure shows the **Add/Remove Programs** dialog with several versions of the .NET runtime and SDK installed.</span></span>

![Přidat nebo odebrat programy se odebrat .NET Core](./media/remove-runtime-sdk-versions/programs-and-features.png)

<span data-ttu-id="6a2f5-118">Vyberte všechny verze, kterou chcete odebrat z počítače a klikněte na tlačítko **odinstalovat**.</span><span class="sxs-lookup"><span data-stu-id="6a2f5-118">Select any versions you want to remove from your machine and click **Uninstall**.</span></span>

# <a name="linuxtablinux"></a>[<span data-ttu-id="6a2f5-119">Linux</span><span class="sxs-lookup"><span data-stu-id="6a2f5-119">Linux</span></span>](#tab/Linux)

<span data-ttu-id="6a2f5-120">Existují další možnosti odinstalace .NET Core (SDK nebo modul runtime) v Linuxu.</span><span class="sxs-lookup"><span data-stu-id="6a2f5-120">There are more options to uninstall .NET Core (either SDK or runtime) on Linux.</span></span> <span data-ttu-id="6a2f5-121">Nejlepší způsob pro vás k odinstalaci .NET Core je zrcadlení akci, kterou jste použili k instalaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6a2f5-121">The best way for you to uninstall .NET Core is to mirror the action you used to install .NET Core.</span></span> <span data-ttu-id="6a2f5-122">Specifika závisí na zvoleném distribuce a metodu instalace.</span><span class="sxs-lookup"><span data-stu-id="6a2f5-122">The specifics depend on your chosen distribution and the installation method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6a2f5-123">Pro Red Hat zařízení, najdete [Red Hat – Příručka Začínáme](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) informace o instalaci a odinstalaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6a2f5-123">For Red Hat installations, consult the [Red Hat Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) for information on installing and uninstalling .NET Core.</span></span>

<span data-ttu-id="6a2f5-124">Počínaje .NET Core 2.1, není nutné odinstalovat sadu .NET Core SDK, při upgradu pomocí Správce balíčků.</span><span class="sxs-lookup"><span data-stu-id="6a2f5-124">Starting with .NET Core 2.1, there is no need to uninstall the .NET Core SDK when upgrading it using a package manager.</span></span> <span data-ttu-id="6a2f5-125">Správce balíčků `update` nebo `refresh` příkazy automaticky odebere starší verze po úspěšné instalaci novější verze.</span><span class="sxs-lookup"><span data-stu-id="6a2f5-125">The package manager `update` or `refresh` commands will automatically remove the older version upon the successful installation of a newer version.</span></span>

<span data-ttu-id="6a2f5-126">Pokud jste nainstalovali .NET Core pomocí Správce balíčků, použijte tento stejný správce balíčků pro odinstalaci sady .NET SDK nebo modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="6a2f5-126">If you installed .NET Core using a package manager, you use that same package manager to uninstall .NET SDK or runtime.</span></span> <span data-ttu-id="6a2f5-127">Instalace .NET core podporují nejoblíbenější správců balíčků.</span><span class="sxs-lookup"><span data-stu-id="6a2f5-127">.NET Core installations support most popular package managers.</span></span> <span data-ttu-id="6a2f5-128">Správce balíčků vaší distribuce pro přesné syntaxi ve vašem prostředí najdete v dokumentaci:</span><span class="sxs-lookup"><span data-stu-id="6a2f5-128">Consult the documentation for your distribution's package manager for the precise syntax on your environment:</span></span>

- <span data-ttu-id="6a2f5-129">[apt-Get(8)](https://linux.die.net/man/8/apt-get) používá Debian systémů, včetně Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="6a2f5-129">[apt-get(8)](https://linux.die.net/man/8/apt-get) is used by Debian based systems, including Ubuntu.</span></span>
- <span data-ttu-id="6a2f5-130">[YUM(8)](https://linux.die.net/man/8/yum) se používá na Fedora a CentOS, Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="6a2f5-130">[yum(8)](https://linux.die.net/man/8/yum) is used on Fedora, CentOS, and Oracle Linux.</span></span>
- <span data-ttu-id="6a2f5-131">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) se používá v openSUSE a operačním systémem SUSE Linux Enterprise systému (SLES).</span><span class="sxs-lookup"><span data-stu-id="6a2f5-131">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) is used on openSUSE and SUSE Linux Enterprise System (SLES).</span></span>
- <span data-ttu-id="6a2f5-132">[dnf(8)](https://dnf.readthedocs.io/latest/command_ref.html) se používá na Fedora.</span><span class="sxs-lookup"><span data-stu-id="6a2f5-132">[dnf(8)](https://dnf.readthedocs.io/latest/command_ref.html) is used on Fedora.</span></span>

<span data-ttu-id="6a2f5-133">V téměř všech případech se příkaz k odebrání balíčku je `remove`.</span><span class="sxs-lookup"><span data-stu-id="6a2f5-133">In almost all cases, the command to remove a package is `remove`.</span></span>

<span data-ttu-id="6a2f5-134">Název balíčku pro instalaci .NET Core SDK pro většinu Správce balíčků je `dotnet-sdk`následovaný číslo verze.</span><span class="sxs-lookup"><span data-stu-id="6a2f5-134">The package name for the .NET Core SDK installation for most package managers is `dotnet-sdk`, followed by the version number.</span></span> <span data-ttu-id="6a2f5-135">Počínaje verzí 2.1.300 .NET Core SDK a verze `2.1` modulu runtime jsou nezbytné pouze čísla hlavní verze a podverze: .NET Core SDK verze 2.1.300 například může být odkazováno jako balíček `dotnet-sdk-2.1`.</span><span class="sxs-lookup"><span data-stu-id="6a2f5-135">Starting with the version 2.1.300 of the .NET Core SDK and version `2.1` of the runtime, only the major and minor version numbers are necessary: for example, the .NET Core SDK version 2.1.300 can be referenced as the package `dotnet-sdk-2.1`.</span></span> <span data-ttu-id="6a2f5-136">Předchozí verze vyžadují celého řetězci verze: například `dotnet-sdk-2.1.200` by byla zapotřebí pro 2.1.200 verzi .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="6a2f5-136">Prior versions require the entire version string: for example, `dotnet-sdk-2.1.200` would be required for version 2.1.200 of the .NET Core SDK.</span></span>

<span data-ttu-id="6a2f5-137">Pro počítače, které jste nainstalovali pouze modul runtime a ne sadu SDK, je název balíčku `dotnet-runtime-<version>` pro modul runtime .NET Core a `aspnetcore-runtime-<version>` pro zásobník celý modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="6a2f5-137">For machines that have installed only the runtime, and not the SDK, the package name is `dotnet-runtime-<version>` for the .NET Core runtime, and `aspnetcore-runtime-<version>` for the entire runtime stack.</span></span>

<span data-ttu-id="6a2f5-138">Instalace .NET core před 2.0 neodinstalovali hostitelská aplikace, když sada SDK byla odinstalována pomocí Správce balíčků.</span><span class="sxs-lookup"><span data-stu-id="6a2f5-138">.NET Core installations prior to 2.0 did not uninstall the host application when the SDK was uninstalled using the package manager.</span></span> <span data-ttu-id="6a2f5-139">Pomocí `apt-get`, má příkaz tuto podobu:</span><span class="sxs-lookup"><span data-stu-id="6a2f5-139">Using `apt-get`, the command is:</span></span>

```bash
apt-get remove dotnet-host
```

<span data-ttu-id="6a2f5-140">Všimněte si, že neexistuje žádná verze připojené k `dotnet-host`.</span><span class="sxs-lookup"><span data-stu-id="6a2f5-140">Note that there is no version attached to `dotnet-host`.</span></span>

<span data-ttu-id="6a2f5-141">Pokud jste si nainstalovali pomocí tarballu, musíte odebrat .NET Core pomocí ruční metodu.</span><span class="sxs-lookup"><span data-stu-id="6a2f5-141">If you installed using a tarball, you must remove .NET Core using the manual method.</span></span>

<span data-ttu-id="6a2f5-142">Můžete odebrat sady SDK a moduly runtime samostatně, odebráním adresáře, který obsahuje tuto verzi.</span><span class="sxs-lookup"><span data-stu-id="6a2f5-142">You remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="6a2f5-143">Například, chcete-li odebrat 1.0.1 SDK a modul runtime, použili byste následující příkazy bash:</span><span class="sxs-lookup"><span data-stu-id="6a2f5-143">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="6a2f5-144">Nadřazené adresáře sady SDK a modulu runtime jsou uvedené ve výstupu `dotnet --list-sdks` a `dotnet --list-runtimes` příkaz, jak je znázorněno v předchozí tabulce.</span><span class="sxs-lookup"><span data-stu-id="6a2f5-144">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

# <a name="macostabmacos"></a>[<span data-ttu-id="6a2f5-145">macOS</span><span class="sxs-lookup"><span data-stu-id="6a2f5-145">macOS</span></span>](#tab/macOS)

<span data-ttu-id="6a2f5-146">Na počítači Mac je nutné odstranit sady SDK a moduly runtime samostatně, tak, že odeberete adresáře, který obsahuje tuto verzi.</span><span class="sxs-lookup"><span data-stu-id="6a2f5-146">On Mac, you must remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="6a2f5-147">Například, chcete-li odebrat 1.0.1 SDK a modul runtime, použili byste následující příkazy bash:</span><span class="sxs-lookup"><span data-stu-id="6a2f5-147">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/local/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="6a2f5-148">Nadřazené adresáře sady SDK a modulu runtime jsou uvedené ve výstupu `dotnet --list-sdks` a `dotnet --list-runtimes` příkaz, jak je znázorněno v předchozí tabulce.</span><span class="sxs-lookup"><span data-stu-id="6a2f5-148">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

<span data-ttu-id="6a2f5-149">Počínaje .NET Core 2.1, není nutné odinstalovat sadu .NET Core SDK, při upgradu pomocí Správce balíčků.</span><span class="sxs-lookup"><span data-stu-id="6a2f5-149">Starting with .NET Core 2.1, there is no need to uninstall the .NET Core SDK when upgrading it using a package manager.</span></span> <span data-ttu-id="6a2f5-150">Správce balíčků `update` nebo `refresh` příkazy automaticky odebere starší verze po úspěšné instalaci novější verze.</span><span class="sxs-lookup"><span data-stu-id="6a2f5-150">The package manager `update` or `refresh` commands will automatically remove the older version upon the successful installation of a newer version.</span></span>

---
