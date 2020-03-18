---
title: Odebrání runtime jádra .NET a sady SDK
description: Tento článek popisuje, jak určit, které verze rozhraní .NET Core Runtime a sady SDK jsou aktuálně nainstalovány, a potom, jak je odebrat v systémech Windows, Mac a Linux.
ms.date: 12/17/2019
author: billwagner
ms.author: wiwagn
ms.custom: updateeachrelease
ms.openlocfilehash: 71c11825981c6259a779e1ac8f947a41618e922d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398837"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a><span data-ttu-id="8d850-103">Odebrání sady .NET Core Runtime a sady SDK</span><span class="sxs-lookup"><span data-stu-id="8d850-103">How to remove the .NET Core Runtime and SDK</span></span>

<span data-ttu-id="8d850-104">V průběhu času při instalaci aktualizovaných verzí rozhraní .NET Core runtime a sady SDK můžete chtít odebrat zastaralé verze rozhraní .NET Core z počítače.</span><span class="sxs-lookup"><span data-stu-id="8d850-104">Over time, as you install updated versions of the .NET Core runtime and SDK, you may want to remove outdated versions of .NET Core from your machine.</span></span> <span data-ttu-id="8d850-105">Odebrání starších verzí runtime může změnit za běhu zvoleného ke spuštění aplikací sdíleného frameworku, jak je podrobně popsáno v článku o [výběru verze .NET Core](selection.md).</span><span class="sxs-lookup"><span data-stu-id="8d850-105">Removing older versions of the runtime may change the runtime chosen to run shared framework applications, as detailed in the article on [.NET Core version selection](selection.md).</span></span>

## <a name="should-i-remove-a-version"></a><span data-ttu-id="8d850-106">Mám odebrat verzi?</span><span class="sxs-lookup"><span data-stu-id="8d850-106">Should I remove a version?</span></span>

<span data-ttu-id="8d850-107">Chování [výběru verze .NET Core](selection.md) a kompatibilita rozhraní .NET Core za běhu mezi aktualizacemi umožňují bezpečné odebrání předchozích verzí.</span><span class="sxs-lookup"><span data-stu-id="8d850-107">The [.NET Core version selection](selection.md) behaviors and the runtime compatibility of .NET Core across updates enables safe removal of previous versions.</span></span> <span data-ttu-id="8d850-108">Aktualizace runtime .NET Core jsou kompatibilní v rámci hlavní verze 'pásmo', jako je 1.x a 2.x.</span><span class="sxs-lookup"><span data-stu-id="8d850-108">.NET Core runtime updates are compatible within a major version 'band' such as 1.x and 2.x.</span></span> <span data-ttu-id="8d850-109">Kromě toho novější verze sady .NET Core SDK obecně zachovat schopnost vytvářet aplikace, které se zaměřují na předchozí verze runtime kompatibilním způsobem.</span><span class="sxs-lookup"><span data-stu-id="8d850-109">Additionally, newer releases of the .NET Core SDK generally maintain the ability to build applications that target previous versions of the runtime in a compatible manner.</span></span>

<span data-ttu-id="8d850-110">Obecně platí, že potřebujete pouze nejnovější sdk a nejnovější verzi opravy runtimes požadované pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8d850-110">In general, you only need the latest SDK and latest patch version of the runtimes required for your application.</span></span> <span data-ttu-id="8d850-111">Instance, kde zachování starší verze Sady SDK nebo Runtime patří udržování **project.json-založené**aplikace.</span><span class="sxs-lookup"><span data-stu-id="8d850-111">Instances where keeping older SDK or Runtime versions include maintaining **project.json**-based applications.</span></span> <span data-ttu-id="8d850-112">Pokud vaše aplikace nemá konkrétní důvody pro starší sady SDK nebo runtimes, můžete bezpečně odebrat starší verze.</span><span class="sxs-lookup"><span data-stu-id="8d850-112">Unless your application has specific reasons for earlier SDKs or runtimes, you may safely remove older versions.</span></span>

## <a name="determine-what-is-installed"></a><span data-ttu-id="8d850-113">Určení nainstalovaného</span><span class="sxs-lookup"><span data-stu-id="8d850-113">Determine what is installed</span></span>

<span data-ttu-id="8d850-114">Počínaje rozhraním .NET Core 2.1 obsahuje rozhraní .NET CLI možnosti, které můžete použít k zobrazení seznamu verzí sady SDK a runtime nainstalovaných v počítači.</span><span class="sxs-lookup"><span data-stu-id="8d850-114">Starting with .NET Core 2.1, the .NET CLI has options you can use to list the versions of the SDK and runtime that are installed on your machine.</span></span>  <span data-ttu-id="8d850-115">Slouží [`dotnet --list-sdks`](../tools/dotnet.md#options) k zobrazení seznamu sad SDK nainstalovaných v počítači.</span><span class="sxs-lookup"><span data-stu-id="8d850-115">Use [`dotnet --list-sdks`](../tools/dotnet.md#options) to see the list of SDKs installed on your machine.</span></span> <span data-ttu-id="8d850-116">Slouží [`dotnet --list-runtimes`](../tools/dotnet.md#options) k zobrazení seznamu runčasů nainstalovaných v počítači.</span><span class="sxs-lookup"><span data-stu-id="8d850-116">Use [`dotnet --list-runtimes`](../tools/dotnet.md#options) to see the list of runtimes installed on your machine.</span></span> <span data-ttu-id="8d850-117">Následující text ukazuje typický výstup pro Windows, macOS nebo Linux:</span><span class="sxs-lookup"><span data-stu-id="8d850-117">The following text shows typical output for Windows, macOS, or Linux:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="8d850-118">Windows</span><span class="sxs-lookup"><span data-stu-id="8d850-118">Windows</span></span>](#tab/windows)

<span data-ttu-id="8d850-119">Spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="8d850-119">By running the following command:</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="8d850-120">Získáte výstup podobný následující:</span><span class="sxs-lookup"><span data-stu-id="8d850-120">You get output similar to the following:</span></span>

```console
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
```

<span data-ttu-id="8d850-121">A spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="8d850-121">And by running the following command:</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="8d850-122">Získáte výstup podobný následující:</span><span class="sxs-lookup"><span data-stu-id="8d850-122">You get output similar to the following:</span></span>

```console
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

# <a name="linux"></a>[<span data-ttu-id="8d850-123">Linux</span><span class="sxs-lookup"><span data-stu-id="8d850-123">Linux</span></span>](#tab/linux)

<span data-ttu-id="8d850-124">Spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="8d850-124">By running the following command:</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="8d850-125">Získáte výstup podobný následující:</span><span class="sxs-lookup"><span data-stu-id="8d850-125">You get output similar to the following:</span></span>

```console
1.0.1 [/usr/share/dotnet/sdk]
1.0.4 [/usr/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/share/dotnet/sdk]
2.0.0 [/usr/share/dotnet/sdk]
2.1.4 [/usr/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/share/dotnet/sdk]
2.1.300 [/usr/share/dotnet/sdk]
2.1.301 [/usr/share/dotnet/sdk]
```

<span data-ttu-id="8d850-126">A spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="8d850-126">And by running the following command:</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="8d850-127">Získáte výstup podobný následující:</span><span class="sxs-lookup"><span data-stu-id="8d850-127">You get output similar to the following:</span></span>

```console
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

# <a name="macos"></a>[<span data-ttu-id="8d850-128">Macos</span><span class="sxs-lookup"><span data-stu-id="8d850-128">macOS</span></span>](#tab/macos)

<span data-ttu-id="8d850-129">Spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="8d850-129">By running the following command:</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="8d850-130">Získáte výstup podobný následující:</span><span class="sxs-lookup"><span data-stu-id="8d850-130">You get output similar to the following:</span></span>

```console
1.0.1 [/usr/local/share/dotnet/sdk]
1.0.4 [/usr/local/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/local/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/local/share/dotnet/sdk]
2.0.0 [/usr/local/share/dotnet/sdk]
2.1.4 [/usr/local/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/local/share/dotnet/sdk]
2.1.300 [/usr/local/share/dotnet/sdk]
2.1.301 [/usr/local/share/dotnet/sdk]
```

<span data-ttu-id="8d850-131">A spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="8d850-131">And by running the following command:</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="8d850-132">Získáte výstup podobný následující:</span><span class="sxs-lookup"><span data-stu-id="8d850-132">You get output similar to the following:</span></span>

```console
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

## <a name="uninstall-net-core"></a><span data-ttu-id="8d850-133">Odinstalace jádra .NET Core</span><span class="sxs-lookup"><span data-stu-id="8d850-133">Uninstall .NET Core</span></span>

# <a name="windows"></a>[<span data-ttu-id="8d850-134">Windows</span><span class="sxs-lookup"><span data-stu-id="8d850-134">Windows</span></span>](#tab/windows)

<span data-ttu-id="8d850-135">Jádro .NET používá dialogové okno **Přidat nebo odebrat programy** systému Windows k odebrání verzí runtime .NET Core a sady SDK.</span><span class="sxs-lookup"><span data-stu-id="8d850-135">.NET Core uses the Windows **Add/Remove Programs** dialog to remove versions of the .NET Core runtime and SDK.</span></span> <span data-ttu-id="8d850-136">Následující obrázek znázorňuje dialogové okno **Přidat nebo odebrat programy** s několika nainstalovanými verzemi běhu .NET a sady SDK.</span><span class="sxs-lookup"><span data-stu-id="8d850-136">The following figure shows the **Add/Remove Programs** dialog with several versions of the .NET runtime and SDK installed.</span></span>

![Přidat nebo odebrat programy pro odebrání rozhraní .NET Core](./media/remove-runtime-sdk-versions/programs-and-features.png)

<span data-ttu-id="8d850-138">Vyberte všechny verze, které chcete odebrat ze zařízení, a klepněte na tlačítko **Odinstalovat**.</span><span class="sxs-lookup"><span data-stu-id="8d850-138">Select any versions you want to remove from your machine and click **Uninstall**.</span></span>

# <a name="linux"></a>[<span data-ttu-id="8d850-139">Linux</span><span class="sxs-lookup"><span data-stu-id="8d850-139">Linux</span></span>](#tab/linux)

<span data-ttu-id="8d850-140">Existuje více možností odinstalace .NET Core (buď SDK nebo runtime) na Linuxu.</span><span class="sxs-lookup"><span data-stu-id="8d850-140">There are more options to uninstall .NET Core (either SDK or runtime) on Linux.</span></span> <span data-ttu-id="8d850-141">Nejlepší způsob, jak odinstalovat jádro .NET Core, je zrcadlit akci použitou k instalaci jádra .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8d850-141">The best way for you to uninstall .NET Core is to mirror the action you used to install .NET Core.</span></span> <span data-ttu-id="8d850-142">Specifika závisí na zvolené distribuci a způsobu instalace.</span><span class="sxs-lookup"><span data-stu-id="8d850-142">The specifics depend on your chosen distribution and the installation method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8d850-143">Informace o instalaci rozhraní .NET Core naleznete v [průvodci začínám](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) s red hatem.</span><span class="sxs-lookup"><span data-stu-id="8d850-143">For Red Hat installations, consult the [Red Hat Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) for information on installing and uninstalling .NET Core.</span></span>

<span data-ttu-id="8d850-144">Počínaje rozhraním .NET Core 2.1 není nutné odinstalovat sadu .NET Core SDK při upgradu pomocí správce balíčků.</span><span class="sxs-lookup"><span data-stu-id="8d850-144">Starting with .NET Core 2.1, there's no need to uninstall the .NET Core SDK when upgrading it using a package manager.</span></span> <span data-ttu-id="8d850-145">Správce `update` balíčků `refresh` nebo příkazy automaticky odeberou starší verzi po úspěšné instalaci novější verze.</span><span class="sxs-lookup"><span data-stu-id="8d850-145">The package manager `update` or `refresh` commands will automatically remove the older version upon the successful installation of a newer version.</span></span>

<span data-ttu-id="8d850-146">Pokud jste nainstalovali .NET Core pomocí správce balíčků, použijte stejný správce balíčků k odinstalaci sady .NET SDK nebo runtime.</span><span class="sxs-lookup"><span data-stu-id="8d850-146">If you installed .NET Core using a package manager, you use that same package manager to uninstall .NET SDK or runtime.</span></span> <span data-ttu-id="8d850-147">Instalace .NET Core podporují nejoblíbenější správce balíčků.</span><span class="sxs-lookup"><span data-stu-id="8d850-147">.NET Core installations support most popular package managers.</span></span> <span data-ttu-id="8d850-148">Přesné syntaxe ve vašem prostředí naleznete v dokumentaci správce balíčků vaší distribuce:</span><span class="sxs-lookup"><span data-stu-id="8d850-148">Consult the documentation for your distribution's package manager for the precise syntax on your environment:</span></span>

- <span data-ttu-id="8d850-149">[apt-get(8)](https://linux.die.net/man/8/apt-get) používají systémy založené na Debianu, včetně Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="8d850-149">[apt-get(8)](https://linux.die.net/man/8/apt-get) is used by Debian based systems, including Ubuntu.</span></span>
- <span data-ttu-id="8d850-150">[yum(8)](https://linux.die.net/man/8/yum) se používá na Fedora, CentOS a Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="8d850-150">[yum(8)](https://linux.die.net/man/8/yum) is used on Fedora, CentOS, and Oracle Linux.</span></span>
- <span data-ttu-id="8d850-151">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) se používá na openSUSE a SUSE Linux Enterprise System (SLES).</span><span class="sxs-lookup"><span data-stu-id="8d850-151">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) is used on openSUSE and SUSE Linux Enterprise System (SLES).</span></span>
- <span data-ttu-id="8d850-152">[dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) se používá na Fedoru.</span><span class="sxs-lookup"><span data-stu-id="8d850-152">[dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) is used on Fedora.</span></span>

<span data-ttu-id="8d850-153">Téměř ve všech případech je `remove`příkaz k odebrání balíčku .</span><span class="sxs-lookup"><span data-stu-id="8d850-153">In almost all cases, the command to remove a package is `remove`.</span></span>

<span data-ttu-id="8d850-154">Název balíčku pro instalaci sady .NET Core SDK pro většinu správců balíčků je `dotnet-sdk`následovaný číslem verze.</span><span class="sxs-lookup"><span data-stu-id="8d850-154">The package name for the .NET Core SDK installation for most package managers is `dotnet-sdk`, followed by the version number.</span></span> <span data-ttu-id="8d850-155">Počínaje verzí 2.1.300 sady .NET Core SDK a verzí `2.1` runtime jsou potřebná pouze čísla hlavních a dílčích verzí: například sada .NET Core SDK verze 2.1.300 může být považována za balíček `dotnet-sdk-2.1`.</span><span class="sxs-lookup"><span data-stu-id="8d850-155">Starting with the version 2.1.300 of the .NET Core SDK and version `2.1` of the runtime, only the major and minor version numbers are necessary: for example, the .NET Core SDK version 2.1.300 can be referenced as the package `dotnet-sdk-2.1`.</span></span> <span data-ttu-id="8d850-156">Předchozí verze vyžadují celý řetězec verze: `dotnet-sdk-2.1.200` například by bylo vyžadováno pro verzi 2.1.200 sady .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="8d850-156">Prior versions require the entire version string: for example, `dotnet-sdk-2.1.200` would be required for version 2.1.200 of the .NET Core SDK.</span></span>

<span data-ttu-id="8d850-157">Pro počítače, které nainstalovaly pouze runtime a nikoli SDK, je `dotnet-runtime-<version>` název balíčku `aspnetcore-runtime-<version>` pro soubor .NET Core runtime a pro celý zásobník runtime.</span><span class="sxs-lookup"><span data-stu-id="8d850-157">For machines that have installed only the runtime, and not the SDK, the package name is `dotnet-runtime-<version>` for the .NET Core runtime, and `aspnetcore-runtime-<version>` for the entire runtime stack.</span></span>

<span data-ttu-id="8d850-158">Instalace jádra .NET starší než 2.0 neodinstalovaly hostitelskou aplikaci při odinstalaci sady SDK pomocí správce balíčků.</span><span class="sxs-lookup"><span data-stu-id="8d850-158">.NET Core installations earlier than 2.0 didn't uninstall the host application when the SDK was uninstalled using the package manager.</span></span> <span data-ttu-id="8d850-159">Pomocí `apt-get`příkazu je:</span><span class="sxs-lookup"><span data-stu-id="8d850-159">Using `apt-get`, the command is:</span></span>

```bash
apt-get remove dotnet-host
```

<span data-ttu-id="8d850-160">Všimněte si, že neexistuje `dotnet-host`žádná verze připojena k .</span><span class="sxs-lookup"><span data-stu-id="8d850-160">Note that there's no version attached to `dotnet-host`.</span></span>

<span data-ttu-id="8d850-161">Pokud jste nainstalovali pomocí tarballu, musíte odebrat .NET Core pomocí ruční metody.</span><span class="sxs-lookup"><span data-stu-id="8d850-161">If you installed using a tarball, you must remove .NET Core using the manual method.</span></span>

<span data-ttu-id="8d850-162">Sady SDK a runtimes odeberete samostatně odebráním adresáře, který tuto verzi obsahuje.</span><span class="sxs-lookup"><span data-stu-id="8d850-162">You remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="8d850-163">Chcete-li například odebrat 1.0.1 SDK a runtime, použijte následující příkazy bash:</span><span class="sxs-lookup"><span data-stu-id="8d850-163">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="8d850-164">Nadřazené adresáře pro sadu SDK a `dotnet --list-sdks` `dotnet --list-runtimes` runtime jsou uvedeny ve výstupu z příkazu a, jak je znázorněno v předchozí tabulce.</span><span class="sxs-lookup"><span data-stu-id="8d850-164">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

# <a name="macos"></a>[<span data-ttu-id="8d850-165">Macos</span><span class="sxs-lookup"><span data-stu-id="8d850-165">macOS</span></span>](#tab/macos)

<span data-ttu-id="8d850-166">Na Macu je nutné odebrat sady SDK a runtimes samostatně odebráním adresáře, který tuto verzi obsahuje.</span><span class="sxs-lookup"><span data-stu-id="8d850-166">On Mac, you must remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="8d850-167">Chcete-li například odebrat 1.0.1 SDK a runtime, použijte následující příkazy bash:</span><span class="sxs-lookup"><span data-stu-id="8d850-167">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/local/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="8d850-168">Nadřazené adresáře pro sadu SDK a `dotnet --list-sdks` `dotnet --list-runtimes` runtime jsou uvedeny ve výstupu z příkazu a, jak je znázorněno v předchozí tabulce.</span><span class="sxs-lookup"><span data-stu-id="8d850-168">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

---

## <a name="net-core-uninstall-tool"></a><span data-ttu-id="8d850-169">Nástroj pro odinstalaci .NET Core</span><span class="sxs-lookup"><span data-stu-id="8d850-169">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="8d850-170">[Nástroj .NET Core Uninstall Tool](../additional-tools/uninstall-tool.md) (`dotnet-core-uninstall`) umožňuje odebrat sady .NET Core SDK a runtimes ze systému.</span><span class="sxs-lookup"><span data-stu-id="8d850-170">The [.NET Core Uninstall Tool](../additional-tools/uninstall-tool.md) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and runtimes from a system.</span></span> <span data-ttu-id="8d850-171">K dispozici je kolekce možností, které určují, které verze by měly být odinstalovány.</span><span class="sxs-lookup"><span data-stu-id="8d850-171">A collection of options is available to specify which versions should be uninstalled.</span></span>

## <a name="visual-studio-dependency-on-net-core-sdk-versions"></a><span data-ttu-id="8d850-172">Závislost sady Visual Studio na verzích sady .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="8d850-172">Visual Studio dependency on .NET Core SDK versions</span></span>

<span data-ttu-id="8d850-173">Před Visual Studio 2019 verze 16.3, Visual Studio instalátory volal samostatný instalační program .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="8d850-173">Before Visual Studio 2019 version 16.3, Visual Studio installers called the standalone .NET Core SDK installer.</span></span> <span data-ttu-id="8d850-174">V důsledku toho se verze sady SDK zobrazí v dialogovém okně **Přidat nebo odebrat programy systému** Windows.</span><span class="sxs-lookup"><span data-stu-id="8d850-174">As a result, the SDK versions appear in the Windows **Add/Remove Programs** dialog.</span></span> <span data-ttu-id="8d850-175">Odebrání sad SDK jádra .NET, které byly nainstalovány aplikací Visual Studio pomocí samostatného instalačního programu, může dojít k přerušení sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8d850-175">Removing .NET Core SDKs that were installed by Visual Studio using the standalone installer may break Visual Studio.</span></span> <span data-ttu-id="8d850-176">Pokud visual studio má problémy po odinstalaci sad SDK, spusťte opravit v této konkrétní verzi sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8d850-176">If Visual Studio has problems after you uninstall SDKs, run Repair on that specific version of Visual Studio.</span></span> <span data-ttu-id="8d850-177">V následující tabulce jsou uvedeny některé závislosti sady Visual Studio na verzích sady .NET Core SDK:</span><span class="sxs-lookup"><span data-stu-id="8d850-177">The following table shows some of the Visual Studio dependencies on .NET Core SDK versions:</span></span>

| <span data-ttu-id="8d850-178">Verze sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8d850-178">Visual Studio version</span></span> | <span data-ttu-id="8d850-179">Verze sady .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="8d850-179">.NET Core SDK version</span></span> |
| -- | -- |
| <span data-ttu-id="8d850-180"> Visual Studio 2019 verze 16.2 </span><span class="sxs-lookup"><span data-stu-id="8d850-180">Visual Studio 2019 version 16.2</span></span> | <span data-ttu-id="8d850-181">.NET Jádro SDK 2.2.4xx, 2.1.8xx</span><span class="sxs-lookup"><span data-stu-id="8d850-181">.NET Core SDK 2.2.4xx, 2.1.8xx</span></span> |
| <span data-ttu-id="8d850-182"> Visual Studio 2019 verze 16.1</span><span class="sxs-lookup"><span data-stu-id="8d850-182">Visual Studio 2019 version 16.1</span></span> | <span data-ttu-id="8d850-183">.NET Jádro SDK 2.2.3xx, 2.1.7xx</span><span class="sxs-lookup"><span data-stu-id="8d850-183">.NET Core SDK 2.2.3xx, 2.1.7xx</span></span> |
| <span data-ttu-id="8d850-184">Visual Studio 2019 verze 16.0</span><span class="sxs-lookup"><span data-stu-id="8d850-184">Visual Studio 2019 version 16.0</span></span> | <span data-ttu-id="8d850-185">.NET Jádro SDK 2.2.2xx, 2.1.6xx</span><span class="sxs-lookup"><span data-stu-id="8d850-185">.NET Core SDK 2.2.2xx, 2.1.6xx</span></span> |
| <span data-ttu-id="8d850-186">Visual Studio 2017 verze 15.9</span><span class="sxs-lookup"><span data-stu-id="8d850-186">Visual Studio 2017 version 15.9</span></span> | <span data-ttu-id="8d850-187">.NET Jádro SDK 2.2.1xx, 2.1.5xx</span><span class="sxs-lookup"><span data-stu-id="8d850-187">.NET Core SDK 2.2.1xx, 2.1.5xx</span></span> |
| <span data-ttu-id="8d850-188">Visual Studio 2017 verze 15.8</span><span class="sxs-lookup"><span data-stu-id="8d850-188">Visual Studio 2017 version 15.8</span></span> | <span data-ttu-id="8d850-189">Sada .NET Core SDK 2.1.4xx</span><span class="sxs-lookup"><span data-stu-id="8d850-189">.NET Core SDK 2.1.4xx</span></span> |

<span data-ttu-id="8d850-190">Počínaje Visual Studio 2019 verze 16.3, Visual Studio má na starosti vlastní kopii .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="8d850-190">Starting with Visual Studio 2019 version 16.3, Visual Studio is in charge of its own copy of the .NET Core SDK.</span></span> <span data-ttu-id="8d850-191">Z tohoto důvodu již tyto verze sady SDK nevidíte v dialogovém okně **Přidat nebo odebrat programy.**</span><span class="sxs-lookup"><span data-stu-id="8d850-191">For that reason, you no longer see those SDK versions in the **Add/Remove Programs** dialog.</span></span>

## <a name="remove-the-nuget-fallback-folder"></a><span data-ttu-id="8d850-192">Odebrání záložní složky NuGet</span><span class="sxs-lookup"><span data-stu-id="8d850-192">Remove the NuGet fallback folder</span></span>

<span data-ttu-id="8d850-193">Před sadou .NET Core 3.0 SDK instalační programy .NET Core SDK používaly *nugetfallbackfolder* k uložení mezipaměti balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="8d850-193">Before .NET Core 3.0 SDK, the .NET Core SDK installers used the *NuGetFallbackFolder* to store a cache of NuGet packages.</span></span> <span data-ttu-id="8d850-194">Tato mezipaměť byla použita při operacích, jako `dotnet restore` je například nebo `dotnet build /t:Restore`.</span><span class="sxs-lookup"><span data-stu-id="8d850-194">This cache was used during operations such as `dotnet restore` or `dotnet build /t:Restore`.</span></span> <span data-ttu-id="8d850-195">Je `NuGetFallbackFolder` umístěn na *adrese C:\Program Files\dotnet\sdk* v systému Windows a na adrese */usr/local/share/dotnet/sdk* v systému macOS.</span><span class="sxs-lookup"><span data-stu-id="8d850-195">The `NuGetFallbackFolder` is located at *C:\Program Files\dotnet\sdk* on Windows and at */usr/local/share/dotnet/sdk* on macOS.</span></span>

<span data-ttu-id="8d850-196">Tuto složku můžete odebrat, pokud:</span><span class="sxs-lookup"><span data-stu-id="8d850-196">You may want to remove this folder, if:</span></span>

* <span data-ttu-id="8d850-197">Vyvíjíte pouze pomocí sady .NET Core 3.0 SDK nebo novějších verzí.</span><span class="sxs-lookup"><span data-stu-id="8d850-197">You're only developing using .NET Core 3.0 SDK or later versions.</span></span>
* <span data-ttu-id="8d850-198">Vyvíjíte pomocí .NET Core SDK verze starší než 3.0, ale můžete pracovat online a věci mohou být pomalejší jednou.</span><span class="sxs-lookup"><span data-stu-id="8d850-198">You're developing using .NET Core SDK versions earlier than 3.0, but you can work online and things can be slower once.</span></span>

<span data-ttu-id="8d850-199">Pokud chcete odebrat záložní složku NuGet, můžete ji odstranit, ale budete potřebovat oprávnění správce, abyste tak učinili.</span><span class="sxs-lookup"><span data-stu-id="8d850-199">If you want to remove the NuGet fallback folder, you can delete it, but you'll need admin privileges to do so.</span></span>

<span data-ttu-id="8d850-200">Není doporučeno odstranit složku *dotnet.*</span><span class="sxs-lookup"><span data-stu-id="8d850-200">It's not recommended to delete the *dotnet* folder.</span></span> <span data-ttu-id="8d850-201">Tím byste odstranili všechny globální nástroje, které jste dříve nainstalovali.</span><span class="sxs-lookup"><span data-stu-id="8d850-201">Doing so would remove any global tools you've previously installed.</span></span> <span data-ttu-id="8d850-202">Také v systému Windows:</span><span class="sxs-lookup"><span data-stu-id="8d850-202">Also, on Windows:</span></span>

- <span data-ttu-id="8d850-203">Přerušíte verzi Visual Studia 2019 verze 16.3 a novější.</span><span class="sxs-lookup"><span data-stu-id="8d850-203">You'll break Visual Studio 2019 version 16.3 and later versions.</span></span> <span data-ttu-id="8d850-204">Můžete spustit **opravit** obnovit.</span><span class="sxs-lookup"><span data-stu-id="8d850-204">You can run **Repair** to recover.</span></span>
- <span data-ttu-id="8d850-205">Pokud jsou v dialogovém okně **Přidat nebo odebrat programy** položky .NET Core SDK, budou osamocené.</span><span class="sxs-lookup"><span data-stu-id="8d850-205">If there are .NET Core SDK entries in the **Add/Remove Programs** dialog, they'll be orphaned.</span></span>
