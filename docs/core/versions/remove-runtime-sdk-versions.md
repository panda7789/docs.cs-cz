---
title: Odebrání modulu runtime .NET Core a sady SDK
description: Tento článek popisuje, jak určit, které verze modulu runtime .NET Core a sady SDK jsou momentálně nainstalované, a jak je odstranit v systémech Windows, Mac a Linux.
ms.date: 04/22/2020
author: billwagner
ms.author: wiwagn
ms.custom: updateeachrelease
ms.openlocfilehash: 0b3501bf7c730120d3885b8c3f29b901fb131215
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135760"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a><span data-ttu-id="916be-103">Postup odebrání modulu runtime .NET Core a sady SDK</span><span class="sxs-lookup"><span data-stu-id="916be-103">How to remove the .NET Core Runtime and SDK</span></span>

<span data-ttu-id="916be-104">V průběhu času, při instalaci aktualizovaných verzí modulu runtime .NET Core a sady SDK, můžete chtít z počítače odebrat zastaralé verze rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="916be-104">Over time, as you install updated versions of the .NET Core runtime and SDK, you may want to remove outdated versions of .NET Core from your machine.</span></span> <span data-ttu-id="916be-105">Odebrání starších verzí modulu runtime může změnit modul runtime zvolený tak, aby spouštěl aplikace sdíleného rozhraní, jak je popsáno v článku [Výběr verze .NET Core](selection.md).</span><span class="sxs-lookup"><span data-stu-id="916be-105">Removing older versions of the runtime may change the runtime chosen to run shared framework applications, as detailed in the article on [.NET Core version selection](selection.md).</span></span>

## <a name="should-i-remove-a-version"></a><span data-ttu-id="916be-106">Mám odebrat verzi?</span><span class="sxs-lookup"><span data-stu-id="916be-106">Should I remove a version?</span></span>

<span data-ttu-id="916be-107">Chování při [výběru verze .NET Core](selection.md) a kompatibilita modulu runtime .NET Core napříč aktualizacemi umožňují bezpečné odebrání předchozích verzí.</span><span class="sxs-lookup"><span data-stu-id="916be-107">The [.NET Core version selection](selection.md) behaviors and the runtime compatibility of .NET Core across updates enables safe removal of previous versions.</span></span> <span data-ttu-id="916be-108">Aktualizace modulu runtime .NET Core jsou kompatibilní s hlavní verzí "pásma", jako je například 1. x a 2. x.</span><span class="sxs-lookup"><span data-stu-id="916be-108">.NET Core runtime updates are compatible within a major version 'band' such as 1.x and 2.x.</span></span> <span data-ttu-id="916be-109">Kromě toho novější verze .NET Core SDK obecně udržují možnost vytvářet aplikace, které cílí na předchozí verze modulu runtime kompatibilním způsobem.</span><span class="sxs-lookup"><span data-stu-id="916be-109">Additionally, newer releases of the .NET Core SDK generally maintain the ability to build applications that target previous versions of the runtime in a compatible manner.</span></span>

<span data-ttu-id="916be-110">Obecně platí, že potřebujete jenom nejnovější sadu SDK a nejnovější verzi patch runtime, která je pro vaši aplikaci nutná.</span><span class="sxs-lookup"><span data-stu-id="916be-110">In general, you only need the latest SDK and latest patch version of the runtimes required for your application.</span></span> <span data-ttu-id="916be-111">Instance, které udržují starší verze sady SDK nebo modulu runtime, zahrnují údržbu aplikací založených na **Project. JSON**.</span><span class="sxs-lookup"><span data-stu-id="916be-111">Instances where keeping older SDK or Runtime versions include maintaining **project.json**-based applications.</span></span> <span data-ttu-id="916be-112">Pokud vaše aplikace nemá konkrétní důvody pro předchozí sady SDK nebo moduly runtime, můžete starší verze odstranit bezpečně.</span><span class="sxs-lookup"><span data-stu-id="916be-112">Unless your application has specific reasons for earlier SDKs or runtimes, you may safely remove older versions.</span></span>

## <a name="determine-what-is-installed"></a><span data-ttu-id="916be-113">Určete, co je nainstalováno</span><span class="sxs-lookup"><span data-stu-id="916be-113">Determine what is installed</span></span>

<span data-ttu-id="916be-114">Počínaje rozhraním .NET Core 2,1 mají rozhraní .NET CLI možnosti, které můžete použít k vypsání verzí sady SDK a modulu runtime, které jsou nainstalovány na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="916be-114">Starting with .NET Core 2.1, the .NET CLI has options you can use to list the versions of the SDK and runtime that are installed on your machine.</span></span>  <span data-ttu-id="916be-115">Pomocí [`dotnet --list-sdks`](../tools/dotnet.md#options) zobrazíte seznam sad SDK nainstalovaných v počítači.</span><span class="sxs-lookup"><span data-stu-id="916be-115">Use [`dotnet --list-sdks`](../tools/dotnet.md#options) to see the list of SDKs installed on your machine.</span></span> <span data-ttu-id="916be-116">Použijte [`dotnet --list-runtimes`](../tools/dotnet.md#options) k zobrazení seznamu modulů runtime instalovaných v počítači.</span><span class="sxs-lookup"><span data-stu-id="916be-116">Use [`dotnet --list-runtimes`](../tools/dotnet.md#options) to see the list of runtimes installed on your machine.</span></span> <span data-ttu-id="916be-117">Následující text zobrazuje typický výstup pro Windows, macOS nebo Linux:</span><span class="sxs-lookup"><span data-stu-id="916be-117">The following text shows typical output for Windows, macOS, or Linux:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="916be-118">Windows</span><span class="sxs-lookup"><span data-stu-id="916be-118">Windows</span></span>](#tab/windows)

<span data-ttu-id="916be-119">Spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="916be-119">By running the following command:</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="916be-120">Získáte výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="916be-120">You get output similar to the following:</span></span>

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

<span data-ttu-id="916be-121">A spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="916be-121">And by running the following command:</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="916be-122">Získáte výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="916be-122">You get output similar to the following:</span></span>

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

# <a name="linux"></a>[<span data-ttu-id="916be-123">Linux</span><span class="sxs-lookup"><span data-stu-id="916be-123">Linux</span></span>](#tab/linux)

<span data-ttu-id="916be-124">Spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="916be-124">By running the following command:</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="916be-125">Získáte výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="916be-125">You get output similar to the following:</span></span>

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

<span data-ttu-id="916be-126">A spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="916be-126">And by running the following command:</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="916be-127">Získáte výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="916be-127">You get output similar to the following:</span></span>

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

# <a name="macos"></a>[<span data-ttu-id="916be-128">macOS</span><span class="sxs-lookup"><span data-stu-id="916be-128">macOS</span></span>](#tab/macos)

<span data-ttu-id="916be-129">Spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="916be-129">By running the following command:</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="916be-130">Získáte výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="916be-130">You get output similar to the following:</span></span>

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

<span data-ttu-id="916be-131">A spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="916be-131">And by running the following command:</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="916be-132">Získáte výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="916be-132">You get output similar to the following:</span></span>

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

## <a name="uninstall-net-core"></a><span data-ttu-id="916be-133">Odinstalace .NET Core</span><span class="sxs-lookup"><span data-stu-id="916be-133">Uninstall .NET Core</span></span>

# <a name="windows"></a>[<span data-ttu-id="916be-134">Windows</span><span class="sxs-lookup"><span data-stu-id="916be-134">Windows</span></span>](#tab/windows)

<span data-ttu-id="916be-135">.NET Core používá dialogové okno **Přidat nebo odebrat programy** v systému Windows k odebrání verzí modulu runtime .NET Core a sady SDK.</span><span class="sxs-lookup"><span data-stu-id="916be-135">.NET Core uses the Windows **Add/Remove Programs** dialog to remove versions of the .NET Core runtime and SDK.</span></span> <span data-ttu-id="916be-136">Následující obrázek ukazuje dialog **Přidat nebo odebrat programy** s nainstalovaným několika verzemi modulu .NET runtime a sady SDK.</span><span class="sxs-lookup"><span data-stu-id="916be-136">The following figure shows the **Add/Remove Programs** dialog with several versions of the .NET runtime and SDK installed.</span></span>

![Přidat nebo odebrat programy pro odebrání .NET Core](./media/remove-runtime-sdk-versions/programs-and-features.png)

<span data-ttu-id="916be-138">Vyberte všechny verze, které chcete z počítače odebrat, a klikněte na **odinstalovat**.</span><span class="sxs-lookup"><span data-stu-id="916be-138">Select any versions you want to remove from your machine and click **Uninstall**.</span></span>

# <a name="linux"></a>[<span data-ttu-id="916be-139">Linux</span><span class="sxs-lookup"><span data-stu-id="916be-139">Linux</span></span>](#tab/linux)

<span data-ttu-id="916be-140">K dispozici je více možností pro odinstalaci rozhraní .NET Core (buď sady SDK nebo modulu runtime) v systému Linux.</span><span class="sxs-lookup"><span data-stu-id="916be-140">There are more options to uninstall .NET Core (either SDK or runtime) on Linux.</span></span> <span data-ttu-id="916be-141">Nejlepším způsobem, jak odinstalovat .NET Core, je zrcadlit akci, kterou jste použili k instalaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="916be-141">The best way for you to uninstall .NET Core is to mirror the action you used to install .NET Core.</span></span> <span data-ttu-id="916be-142">Konkrétní závislosti závisí na zvolené distribuci a metodě instalace.</span><span class="sxs-lookup"><span data-stu-id="916be-142">The specifics depend on your chosen distribution and the installation method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="916be-143">V případě instalací Red Hat si přečtěte informace o instalaci a odinstalaci .NET Core v [příručce pro Red hat Začínáme](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) .</span><span class="sxs-lookup"><span data-stu-id="916be-143">For Red Hat installations, consult the [Red Hat Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) for information on installing and uninstalling .NET Core.</span></span>

<span data-ttu-id="916be-144">Počínaje rozhraním .NET Core 2,1 není nutné při upgradu pomocí Správce balíčků .NET Core SDK odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="916be-144">Starting with .NET Core 2.1, there's no need to uninstall the .NET Core SDK when upgrading it using a package manager.</span></span> <span data-ttu-id="916be-145">Správce `update` balíčků nebo `refresh` příkazy automaticky odebere starší verzi po úspěšné instalaci novější verze.</span><span class="sxs-lookup"><span data-stu-id="916be-145">The package manager `update` or `refresh` commands will automatically remove the older version upon the successful installation of a newer version.</span></span>

<span data-ttu-id="916be-146">Pokud jste nainstalovali .NET Core pomocí Správce balíčků, použijte stejného správce balíčků pro odinstalaci sady .NET SDK nebo modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="916be-146">If you installed .NET Core using a package manager, you use that same package manager to uninstall .NET SDK or runtime.</span></span> <span data-ttu-id="916be-147">Instalace .NET Core podporují většinu oblíbených správců balíčků.</span><span class="sxs-lookup"><span data-stu-id="916be-147">.NET Core installations support most popular package managers.</span></span> <span data-ttu-id="916be-148">V dokumentaci pro správce balíčků distribuce vyhledejte přesnou syntaxi vašeho prostředí.</span><span class="sxs-lookup"><span data-stu-id="916be-148">Consult the documentation for your distribution's package manager for the precise syntax on your environment:</span></span>

- <span data-ttu-id="916be-149">[apt-get (8)](https://linux.die.net/man/8/apt-get) se používá v systémech založených na Debian, včetně Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="916be-149">[apt-get(8)](https://linux.die.net/man/8/apt-get) is used by Debian based systems, including Ubuntu.</span></span>
- <span data-ttu-id="916be-150">[Yumu (8)](https://linux.die.net/man/8/yum) se používá na Fedora, CentOS a Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="916be-150">[yum(8)](https://linux.die.net/man/8/yum) is used on Fedora, CentOS, and Oracle Linux.</span></span>
- <span data-ttu-id="916be-151">[zypperu (8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) se používá v systémech OPENSUSE a SUSE Linux Enterprise (SLES).</span><span class="sxs-lookup"><span data-stu-id="916be-151">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) is used on openSUSE and SUSE Linux Enterprise System (SLES).</span></span>
- <span data-ttu-id="916be-152">[DNF (8)](https://dnf.readthedocs.io/en/latest/command_ref.html) se používá v Fedora.</span><span class="sxs-lookup"><span data-stu-id="916be-152">[dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) is used on Fedora.</span></span>

<span data-ttu-id="916be-153">V téměř všech případech je `remove`příkaz k odebrání balíčku.</span><span class="sxs-lookup"><span data-stu-id="916be-153">In almost all cases, the command to remove a package is `remove`.</span></span>

<span data-ttu-id="916be-154">Název balíčku pro instalaci .NET Core SDK pro většinu správců balíčků je `dotnet-sdk`následovaný číslem verze.</span><span class="sxs-lookup"><span data-stu-id="916be-154">The package name for the .NET Core SDK installation for most package managers is `dotnet-sdk`, followed by the version number.</span></span> <span data-ttu-id="916be-155">Počínaje verzí 2.1.300 .NET Core SDK a verzí `2.1` modulu runtime jsou nutná pouze čísla hlavní verze a podverze. například .NET Core SDK verze 2.1.300 může být odkazována jako balíček. `dotnet-sdk-2.1`</span><span class="sxs-lookup"><span data-stu-id="916be-155">Starting with the version 2.1.300 of the .NET Core SDK and version `2.1` of the runtime, only the major and minor version numbers are necessary: for example, the .NET Core SDK version 2.1.300 can be referenced as the package `dotnet-sdk-2.1`.</span></span> <span data-ttu-id="916be-156">Předchozí verze vyžadují řetězec celé verze: například `dotnet-sdk-2.1.200` by vyžadovala 2.1.200 verze .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="916be-156">Prior versions require the entire version string: for example, `dotnet-sdk-2.1.200` would be required for version 2.1.200 of the .NET Core SDK.</span></span>

<span data-ttu-id="916be-157">Pro počítače, které mají nainstalované pouze modul runtime a nikoli sadu SDK, je `dotnet-runtime-<version>` název balíčku pro modul runtime .NET Core a `aspnetcore-runtime-<version>` pro celý zásobník modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="916be-157">For machines that have installed only the runtime, and not the SDK, the package name is `dotnet-runtime-<version>` for the .NET Core runtime, and `aspnetcore-runtime-<version>` for the entire runtime stack.</span></span>

<span data-ttu-id="916be-158">Instalace .NET Core starší než 2,0 odinstalovaly hostitelskou aplikaci, když se sada SDK odinstalovala pomocí Správce balíčků.</span><span class="sxs-lookup"><span data-stu-id="916be-158">.NET Core installations earlier than 2.0 didn't uninstall the host application when the SDK was uninstalled using the package manager.</span></span> <span data-ttu-id="916be-159">Pomocí `apt-get`příkazu je tento příkaz:</span><span class="sxs-lookup"><span data-stu-id="916be-159">Using `apt-get`, the command is:</span></span>

```bash
apt-get remove dotnet-host
```

<span data-ttu-id="916be-160">Všimněte si, že není připojená žádná `dotnet-host`verze.</span><span class="sxs-lookup"><span data-stu-id="916be-160">Note that there's no version attached to `dotnet-host`.</span></span>

<span data-ttu-id="916be-161">Pokud jste nainstalovali tarballu pomocí nástroje, je nutné pomocí ruční metody odebrat rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="916be-161">If you installed using a tarball, you must remove .NET Core using the manual method.</span></span>

<span data-ttu-id="916be-162">V systému Linux musíte sady SDK a moduly runtime odebrat samostatně odebráním adresářů se správou verzí.</span><span class="sxs-lookup"><span data-stu-id="916be-162">On Linux, you must remove the SDKs and runtimes separately, by removing the versioned directories.</span></span> <span data-ttu-id="916be-163">Aby bylo jasné, tak se odstraní sada SDK a modul runtime z disku.</span><span class="sxs-lookup"><span data-stu-id="916be-163">To be clear, this deletes the SDK and runtime from disk.</span></span> <span data-ttu-id="916be-164">Chcete-li například odebrat sadu 1.0.1 SDK a modul runtime, použijte následující příkazy bash:</span><span class="sxs-lookup"><span data-stu-id="916be-164">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
version="1.0.1"
sudo rm -rf /usr/local/share/dotnet/sdk/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.All/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/$version
sudo rm -rf /usr/local/share/dotnet/host/fxr/$version
```

<span data-ttu-id="916be-165">Nadřazené adresáře pro sadu SDK a modul runtime jsou uvedeny ve výstupu příkazu `dotnet --list-sdks` a `dotnet --list-runtimes` , jak je znázorněno v předchozí tabulce.</span><span class="sxs-lookup"><span data-stu-id="916be-165">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

# <a name="macos"></a>[<span data-ttu-id="916be-166">macOS</span><span class="sxs-lookup"><span data-stu-id="916be-166">macOS</span></span>](#tab/macos)

<span data-ttu-id="916be-167">V systému Mac musíte sady SDK a moduly runtime odebrat samostatně tak, že odeberete adresáře s verzemi.</span><span class="sxs-lookup"><span data-stu-id="916be-167">On Mac, you must remove the SDKs and runtimes separately, by removing the versioned directories.</span></span> <span data-ttu-id="916be-168">Aby bylo jasné, tak se odstraní sada SDK a modul runtime z disku.</span><span class="sxs-lookup"><span data-stu-id="916be-168">To be clear, this deletes the SDK and runtime from disk.</span></span> <span data-ttu-id="916be-169">Chcete-li například odebrat sadu 1.0.1 SDK a modul runtime, použijte následující příkazy bash:</span><span class="sxs-lookup"><span data-stu-id="916be-169">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
version="1.0.1"
sudo rm -rf /usr/local/share/dotnet/sdk/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.All/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/$version
sudo rm -rf /usr/local/share/dotnet/host/fxr/$version
```

<span data-ttu-id="916be-170">Nadřazené adresáře pro sadu SDK a modul runtime jsou uvedeny ve výstupu příkazu `dotnet --list-sdks` a `dotnet --list-runtimes` , jak je znázorněno v předchozí tabulce.</span><span class="sxs-lookup"><span data-stu-id="916be-170">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

---

## <a name="net-core-uninstall-tool"></a><span data-ttu-id="916be-171">Nástroj pro odinstalaci .NET Core</span><span class="sxs-lookup"><span data-stu-id="916be-171">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="916be-172">[Nástroj pro odinstalaci .NET Core](../additional-tools/uninstall-tool.md) (`dotnet-core-uninstall`) umožňuje odebrat sady SDK a moduly runtime .NET Core ze systému.</span><span class="sxs-lookup"><span data-stu-id="916be-172">The [.NET Core Uninstall Tool](../additional-tools/uninstall-tool.md) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and runtimes from a system.</span></span> <span data-ttu-id="916be-173">K dispozici je kolekce možností, pomocí kterých určíte, které verze se mají odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="916be-173">A collection of options is available to specify which versions should be uninstalled.</span></span>

## <a name="visual-studio-dependency-on-net-core-sdk-versions"></a><span data-ttu-id="916be-174">Závislost sady Visual Studio na .NET Core SDK verzích</span><span class="sxs-lookup"><span data-stu-id="916be-174">Visual Studio dependency on .NET Core SDK versions</span></span>

<span data-ttu-id="916be-175">Před Visual Studio 2019 verze 16,3 se instalátory sady Visual Studio nazývají samostatné instalační služby .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="916be-175">Before Visual Studio 2019 version 16.3, Visual Studio installers called the standalone .NET Core SDK installer.</span></span> <span data-ttu-id="916be-176">V důsledku toho se verze sady SDK zobrazí v dialogovém okně **Přidat nebo odebrat programy** v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="916be-176">As a result, the SDK versions appear in the Windows **Add/Remove Programs** dialog.</span></span> <span data-ttu-id="916be-177">Odebrání sady .NET Core SDK, které byly nainstalovány v aplikaci Visual Studio pomocí samostatného instalačního programu, může poškodit aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="916be-177">Removing .NET Core SDKs that were installed by Visual Studio using the standalone installer may break Visual Studio.</span></span> <span data-ttu-id="916be-178">Pokud má aplikace Visual Studio problémy po odinstalaci sad SDK, spusťte v této konkrétní verzi sady Visual Studio opravu.</span><span class="sxs-lookup"><span data-stu-id="916be-178">If Visual Studio has problems after you uninstall SDKs, run Repair on that specific version of Visual Studio.</span></span> <span data-ttu-id="916be-179">V následující tabulce jsou uvedeny některé závislosti sady Visual Studio na .NET Core SDK verzích:</span><span class="sxs-lookup"><span data-stu-id="916be-179">The following table shows some of the Visual Studio dependencies on .NET Core SDK versions:</span></span>

| <span data-ttu-id="916be-180">Verze sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="916be-180">Visual Studio version</span></span> | <span data-ttu-id="916be-181">Verze .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="916be-181">.NET Core SDK version</span></span> |
| -- | -- |
| <span data-ttu-id="916be-182"> Visual Studio 2019 verze 16.2 </span><span class="sxs-lookup"><span data-stu-id="916be-182">Visual Studio 2019 version 16.2</span></span> | <span data-ttu-id="916be-183">.NET Core SDK 2.2.4 xx, 2.1.8 XX</span><span class="sxs-lookup"><span data-stu-id="916be-183">.NET Core SDK 2.2.4xx, 2.1.8xx</span></span> |
| <span data-ttu-id="916be-184"> Visual Studio 2019 verze 16.1</span><span class="sxs-lookup"><span data-stu-id="916be-184">Visual Studio 2019 version 16.1</span></span> | <span data-ttu-id="916be-185">.NET Core SDK 2.2.3 xx, 2.1.7 XX</span><span class="sxs-lookup"><span data-stu-id="916be-185">.NET Core SDK 2.2.3xx, 2.1.7xx</span></span> |
| <span data-ttu-id="916be-186">Visual Studio 2019 verze 16,0</span><span class="sxs-lookup"><span data-stu-id="916be-186">Visual Studio 2019 version 16.0</span></span> | <span data-ttu-id="916be-187">.NET Core SDK 2.2.2 xx, 2.1.6 xx</span><span class="sxs-lookup"><span data-stu-id="916be-187">.NET Core SDK 2.2.2xx, 2.1.6xx</span></span> |
| <span data-ttu-id="916be-188">Visual Studio 2017 verze 15,9</span><span class="sxs-lookup"><span data-stu-id="916be-188">Visual Studio 2017 version 15.9</span></span> | <span data-ttu-id="916be-189">.NET Core SDK 2.2.1 xx xx, 2.1.5 XX</span><span class="sxs-lookup"><span data-stu-id="916be-189">.NET Core SDK 2.2.1xx, 2.1.5xx</span></span> |
| <span data-ttu-id="916be-190">Visual Studio 2017 verze 15,8</span><span class="sxs-lookup"><span data-stu-id="916be-190">Visual Studio 2017 version 15.8</span></span> | <span data-ttu-id="916be-191">.NET Core SDK 2.1.4 XX</span><span class="sxs-lookup"><span data-stu-id="916be-191">.NET Core SDK 2.1.4xx</span></span> |

<span data-ttu-id="916be-192">Počínaje verzí Visual Studio 2019 verze 16,3 se Visual Studio účtuje na vlastní kopii .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="916be-192">Starting with Visual Studio 2019 version 16.3, Visual Studio is in charge of its own copy of the .NET Core SDK.</span></span> <span data-ttu-id="916be-193">Z tohoto důvodu se tyto verze sady SDK už nezobrazuje v dialogovém okně **Přidat nebo odebrat programy** .</span><span class="sxs-lookup"><span data-stu-id="916be-193">For that reason, you no longer see those SDK versions in the **Add/Remove Programs** dialog.</span></span>

## <a name="remove-the-nuget-fallback-folder"></a><span data-ttu-id="916be-194">Odebrat záložní složku NuGet</span><span class="sxs-lookup"><span data-stu-id="916be-194">Remove the NuGet fallback folder</span></span>

<span data-ttu-id="916be-195">Před sadou .NET Core 3,0 SDK .NET Core SDK Instalační programy používaly *NuGetFallbackFolder* k ukládání mezipaměti balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="916be-195">Before .NET Core 3.0 SDK, the .NET Core SDK installers used the *NuGetFallbackFolder* to store a cache of NuGet packages.</span></span> <span data-ttu-id="916be-196">Tato mezipaměť se použila během operací, `dotnet restore` jako `dotnet build /t:Restore`je nebo.</span><span class="sxs-lookup"><span data-stu-id="916be-196">This cache was used during operations such as `dotnet restore` or `dotnet build /t:Restore`.</span></span> <span data-ttu-id="916be-197">`NuGetFallbackFolder` Je umístěný ve *složce C:\Program Files\dotnet\sdk* ve Windows a v */usr/local/share/dotnet/SDK* na MacOS.</span><span class="sxs-lookup"><span data-stu-id="916be-197">The `NuGetFallbackFolder` is located at *C:\Program Files\dotnet\sdk* on Windows and at */usr/local/share/dotnet/sdk* on macOS.</span></span>

<span data-ttu-id="916be-198">Tuto složku můžete chtít odebrat, pokud:</span><span class="sxs-lookup"><span data-stu-id="916be-198">You may want to remove this folder, if:</span></span>

* <span data-ttu-id="916be-199">Vyvíjíte pouze pomocí .NET Core 3,0 SDK nebo novějších verzí.</span><span class="sxs-lookup"><span data-stu-id="916be-199">You're only developing using .NET Core 3.0 SDK or later versions.</span></span>
* <span data-ttu-id="916be-200">Vyvíjíte pomocí .NET Core SDK verzí starších než 3,0, ale můžete pracovat online a věci můžou být pomalejší.</span><span class="sxs-lookup"><span data-stu-id="916be-200">You're developing using .NET Core SDK versions earlier than 3.0, but you can work online and things can be slower once.</span></span>

<span data-ttu-id="916be-201">Pokud chcete odebrat záložní složku NuGet, můžete ji odstranit, ale budete k tomu potřebovat oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="916be-201">If you want to remove the NuGet fallback folder, you can delete it, but you'll need admin privileges to do so.</span></span>

<span data-ttu-id="916be-202">Nedoporučuje se odstranit složku *dotnet* .</span><span class="sxs-lookup"><span data-stu-id="916be-202">It's not recommended to delete the *dotnet* folder.</span></span> <span data-ttu-id="916be-203">Tím by se odebraly všechny globální nástroje, které jste předtím nainstalovali.</span><span class="sxs-lookup"><span data-stu-id="916be-203">Doing so would remove any global tools you've previously installed.</span></span> <span data-ttu-id="916be-204">Také ve Windows:</span><span class="sxs-lookup"><span data-stu-id="916be-204">Also, on Windows:</span></span>

- <span data-ttu-id="916be-205">Budete přerušit Visual Studio 2019 verze 16,3 a novější.</span><span class="sxs-lookup"><span data-stu-id="916be-205">You'll break Visual Studio 2019 version 16.3 and later versions.</span></span> <span data-ttu-id="916be-206">Můžete spustit **opravu** pro obnovení.</span><span class="sxs-lookup"><span data-stu-id="916be-206">You can run **Repair** to recover.</span></span>
- <span data-ttu-id="916be-207">Pokud v dialogovém okně **Přidat nebo odebrat programy** existují .NET Core SDK položky, budou osamocené.</span><span class="sxs-lookup"><span data-stu-id="916be-207">If there are .NET Core SDK entries in the **Add/Remove Programs** dialog, they'll be orphaned.</span></span>
