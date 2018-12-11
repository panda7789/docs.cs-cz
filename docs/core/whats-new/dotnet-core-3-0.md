---
title: Co je nového v .NET Core 3.0
description: Informace o nových funkcích v rozhraní .NET Core 3.0.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 12/04/2018
ms.openlocfilehash: 3ca833031eb8bb0f43a334f833f2e0075842d57d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155480"
---
# <a name="whats-new-in-net-core-30-preview-1"></a><span data-ttu-id="117bb-103">Co je nového v .NET Core 3.0 (ve verzi Preview 1)</span><span class="sxs-lookup"><span data-stu-id="117bb-103">What's new in .NET Core 3.0 (Preview 1)</span></span>

<span data-ttu-id="117bb-104">Tento článek popisuje, co je nového v .NET Core 3.0 (ve verzi preview 1).</span><span class="sxs-lookup"><span data-stu-id="117bb-104">This article describes what is new in .NET Core 3.0 (preview 1).</span></span> <span data-ttu-id="117bb-105">Jedním z největších vylepšení je podpora aplikací klasické pracovní plochy Windows (jenom Windows).</span><span class="sxs-lookup"><span data-stu-id="117bb-105">One of the biggest enhancements is support for Windows desktop applications (Windows only).</span></span> <span data-ttu-id="117bb-106">S využitím .NET Core 3.0 komponenty s názvem Windows Desktop, můžete port aplikace Windows Forms Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="117bb-106">By utilizing a .NET Core 3.0 component called Windows Desktop, you can port your Windows Forms Windows Presentation Foundation (WPF) applications.</span></span> <span data-ttu-id="117bb-107">Aby bylo jasno, komponenta Windows Desktop se podporuje jenom na Windows.</span><span class="sxs-lookup"><span data-stu-id="117bb-107">To be clear, the Windows Desktop component is only supported on Windows.</span></span> <span data-ttu-id="117bb-108">Další informace najdete v části [Windows desktop](#windows-desktop) níže.</span><span class="sxs-lookup"><span data-stu-id="117bb-108">For more information, see the section [Windows desktop](#windows-desktop) below.</span></span>

<span data-ttu-id="117bb-109">Přidává podporu pro .NET core 3.0 C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="117bb-109">.NET Core 3.0 adds support for C# 8.0.</span></span>

<span data-ttu-id="117bb-110">[Stáhnout a začít pracovat s .NET Core 3 Preview 1](https://aka.ms/netcore3download) teď na Windows, Mac a Linux.</span><span class="sxs-lookup"><span data-stu-id="117bb-110">[Download and get started with .NET Core 3 Preview 1](https://aka.ms/netcore3download) right now on Windows, Mac and Linux.</span></span> <span data-ttu-id="117bb-111">Zobrazí se podrobné informace o verzi v [poznámky k verzi .NET Core 3 Preview 1](https://aka.ms/netcore3releasenotes).</span><span class="sxs-lookup"><span data-stu-id="117bb-111">You can see complete details of the release in the [.NET Core 3 Preview 1 release notes](https://aka.ms/netcore3releasenotes).</span></span>

<span data-ttu-id="117bb-112">Další informace najdete v tématu [.NET Core 3.0 ve verzi Preview 1 oznámení](https://blogs.msdn.microsoft.com/dotnet/2018/12/04/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/).</span><span class="sxs-lookup"><span data-stu-id="117bb-112">For more information, see the [.NET Core 3.0 Preview 1 announcement](https://blogs.msdn.microsoft.com/dotnet/2018/12/04/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/).</span></span>

## <a name="net-standard-21"></a><span data-ttu-id="117bb-113">.NET standard 2.1</span><span class="sxs-lookup"><span data-stu-id="117bb-113">.NET Standard 2.1</span></span>

<span data-ttu-id="117bb-114">.NET core 3.0 implementuje .NET Standard 2.1.</span><span class="sxs-lookup"><span data-stu-id="117bb-114">.NET Core 3.0 implements .NET Standard 2.1.</span></span>

## <a name="default-executables"></a><span data-ttu-id="117bb-115">Výchozí spustitelné soubory</span><span class="sxs-lookup"><span data-stu-id="117bb-115">Default executables</span></span>

<span data-ttu-id="117bb-116">.NET core teď bude vytvářet spustitelné soubory ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="117bb-116">.NET Core will now build executables by default.</span></span> <span data-ttu-id="117bb-117">Toto je nová pro aplikace, které používají globálně nainstalovanou verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="117bb-117">This is new for applications that use a globally installed version of .NET Core.</span></span> <span data-ttu-id="117bb-118">Až doteď jenom [samostatná nasazení](../deploying/index.md#self-contained-deployments-scd) měl spustitelné soubory.</span><span class="sxs-lookup"><span data-stu-id="117bb-118">Until now, only [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) had executables.</span></span>

<span data-ttu-id="117bb-119">Během `dotnet build` nebo `dotnet publish`, spustitelný soubor je vytvořen, za předpokladu, který odpovídá prostředí a platforma sady SDK, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="117bb-119">During `dotnet build` or `dotnet publish`, an executable is created provided that matches the environment and platform of the SDK you are using.</span></span> <span data-ttu-id="117bb-120">Můžete očekávat, že stejné operace tyto spustitelné soubory stejně jako další nativní spustitelné soubory, jako například:</span><span class="sxs-lookup"><span data-stu-id="117bb-120">You can expect the same things with these executables as you would other native executables, such as:</span></span>

* <span data-ttu-id="117bb-121">Můžete dvakrát kliknout na spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="117bb-121">You can double-click on the executable.</span></span>
* <span data-ttu-id="117bb-122">Aplikace z příkazového řádku můžete spustit přímo, jako například `myapp.exe` na Windows, a `./myapp` v Linuxu a macOS.</span><span class="sxs-lookup"><span data-stu-id="117bb-122">You can launch the application from a command prompt directly, such as `myapp.exe` on Windows, and `./myapp` on Linux and macOS.</span></span>

> [!NOTE]
> <span data-ttu-id="117bb-123">Určení konkrétního modulu runtime s `dotnet publish -r` nebo `dotnet build -r` argumenty pro jiná prostředí modulu runtime není podporován.</span><span class="sxs-lookup"><span data-stu-id="117bb-123">Specifying a specific runtime with `dotnet publish -r` or `dotnet build -r` arguments for other runtime environments isn't supported.</span></span>

## <a name="build-copies-dependencies"></a><span data-ttu-id="117bb-124">Vytvoření kopie závislosti</span><span class="sxs-lookup"><span data-stu-id="117bb-124">Build copies dependencies</span></span>

<span data-ttu-id="117bb-125">`dotnet build` Nyní zkopíruje závislostí NuGet pro vaši aplikaci z mezipaměti NuGet k výstupní složce sestavení.</span><span class="sxs-lookup"><span data-stu-id="117bb-125">`dotnet build` now copies NuGet dependencies for your application from the NuGet cache to the build output folder.</span></span> <span data-ttu-id="117bb-126">Dříve byly závislosti pouze zkopírovány jako součást `dotnet publish`.</span><span class="sxs-lookup"><span data-stu-id="117bb-126">Previously, dependencies were only copied as part of `dotnet publish`.</span></span> 

<span data-ttu-id="117bb-127">Existují některé operace, jako je stránka propojení a razor publikování, který se stále vyžadují publikování.</span><span class="sxs-lookup"><span data-stu-id="117bb-127">There are some operations, like linking and razor page publishing that will still require publishing.</span></span>


## <a name="local-dotnet-tools"></a><span data-ttu-id="117bb-128">Nástroje pro místní dotnet</span><span class="sxs-lookup"><span data-stu-id="117bb-128">Local dotnet tools</span></span>

<span data-ttu-id="117bb-129">I když .NET Core 2.1 podporuje globální nástroje, .NET Core 3.0 teď má místní nástroje.</span><span class="sxs-lookup"><span data-stu-id="117bb-129">While .NET Core 2.1 supported global tools, .NET Core 3.0 now has local tools.</span></span> <span data-ttu-id="117bb-130">Místní nástroje se podobají globální nástroje, ale jsou spojeny s konkrétní umístění na disku.</span><span class="sxs-lookup"><span data-stu-id="117bb-130">Local tools are similar to global tools but are associated with a particular location on disk.</span></span> <span data-ttu-id="117bb-131">Díky tomu jednotlivých projektů a nástrojů na úložiště.</span><span class="sxs-lookup"><span data-stu-id="117bb-131">This enables per-project and per-repository tooling.</span></span> <span data-ttu-id="117bb-132">Libovolný nástroj nainstalovaný místně není k dispozici globálně.</span><span class="sxs-lookup"><span data-stu-id="117bb-132">Any tool installed locally isn't available globally.</span></span>

<span data-ttu-id="117bb-133">Místní nástroje spoléhají na název souboru manifestu `dotnet-tools.json` v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="117bb-133">Local tools rely on a manifest file name `dotnet-tools.json` in your current directory.</span></span> <span data-ttu-id="117bb-134">Tento soubor manifestu definuje nástroje k dispozici.</span><span class="sxs-lookup"><span data-stu-id="117bb-134">This manifest file defines the tools to be available.</span></span> <span data-ttu-id="117bb-135">Vytvořením tento soubor manifestu v kořenovém adresáři vašeho úložiště, zajistíte všem uživatelům klonování kódu obnovit a použít nástroje, které jsou potřeba k úspěšné práci s kódem.</span><span class="sxs-lookup"><span data-stu-id="117bb-135">By creating this manifest file at the root of your repository, you ensure anyone cloning your code can restore and use the tools that are needed to successfully work with your code.</span></span>

<span data-ttu-id="117bb-136">Pokud je k dispozici soubor manifestu místní nástroje, použijte následující příkaz automaticky stáhnout a nainstalovat místně tyto nástroje:</span><span class="sxs-lookup"><span data-stu-id="117bb-136">When the local tools manifest file is available, use the following command to automatically download and install those tools locally:</span></span>

```console
dotnet tool restore
```

<span data-ttu-id="117bb-137">Místní nástroj spusťte pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="117bb-137">Run a local tool with the following command:</span></span>

```console
dotnet tool run <tool-command-name>
```

<span data-ttu-id="117bb-138">Při volání místní nástroj vyhledá dotnet manifestu do struktury adresářů.</span><span class="sxs-lookup"><span data-stu-id="117bb-138">When a local tool is called, dotnet searches for a manifest up the directory structure.</span></span> <span data-ttu-id="117bb-139">Když je nalezen soubor manifestu nástroj, se hledá požadovaný nástroj.</span><span class="sxs-lookup"><span data-stu-id="117bb-139">When a tool manifest file is found, it is searched for the requested tool.</span></span> <span data-ttu-id="117bb-140">Pokud se nástroj nachází, obsahuje informace potřebné k vyhledání nástroje v umístění globálních balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="117bb-140">If the tool is found, it includes the information needed to find the tool in the NuGet global packages location.</span></span> 

<span data-ttu-id="117bb-141">Pokud nástroj je nalezena v manifestu, ale ne do mezipaměti, zobrazí se uživateli chybu.</span><span class="sxs-lookup"><span data-stu-id="117bb-141">If the tool is found in the manifest, but not the cache, the user receives an error.</span></span> <span data-ttu-id="117bb-142">Zpráva se vylepší po 1 ve verzi Preview požádat o uživateli spustit `dotnet tool restore`.</span><span class="sxs-lookup"><span data-stu-id="117bb-142">The message will be improved after Preview 1 to request the user run `dotnet tool restore`.</span></span>

<span data-ttu-id="117bb-143">Přidat místní nástroje do adresáře, musíte nejprve vytvořit soubor manifestu nástroje.</span><span class="sxs-lookup"><span data-stu-id="117bb-143">To add local tools to a directory, you need to first create the tool manifest file.</span></span> <span data-ttu-id="117bb-144">Po 1 ve verzi Preview nabízíme mechanismus pro nástroj pro vytváření souborů manifestu, jako je například dotnet novou šablonu.</span><span class="sxs-lookup"><span data-stu-id="117bb-144">After Preview 1, we will offer a mechanism for creating tool manifest files, such as a dotnet new template.</span></span> <span data-ttu-id="117bb-145">Pro verzi Preview 1, musíte vytvořit soubor s názvem `dotnet-tools.json` s následujícím obsahem:</span><span class="sxs-lookup"><span data-stu-id="117bb-145">For Preview 1 you must create the file named `dotnet-tools.json` with the following contents:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {}
}
```

<span data-ttu-id="117bb-146">Po vytvoření manifestu můžete přidat místní nástroje pomocí:</span><span class="sxs-lookup"><span data-stu-id="117bb-146">Once the manifest is created, you can add local tools to it using:</span></span>

```console
dotnet tool install <toolPackageId>
```

<span data-ttu-id="117bb-147">Tento příkaz nainstaluje nejnovější verzi nástroje, pokud není zadána jiná verze.</span><span class="sxs-lookup"><span data-stu-id="117bb-147">This command installs the latest version of the tool, unless another version is specified.</span></span>  <span data-ttu-id="117bb-148">I v případě, že jste vybrali na nejnovější verzi automaticky verzi nástroje jsou zapsána do souboru manifestu nástroj umožňující správnou verzi nástroje pro obnovení nebo spustit.</span><span class="sxs-lookup"><span data-stu-id="117bb-148">Even if the latest version was automatically chosen, the version of the tool is written into the tool manifest file to allow the correct version of the tool to be restored or run.</span></span>

<span data-ttu-id="117bb-149">Soubor manifestu nástroje je navržena k umožnění ruční úpravě – které můžete využít k aktualizaci požadovaná verze pro práci s úložištěm.</span><span class="sxs-lookup"><span data-stu-id="117bb-149">The tool manifest file is designed to allow hand editing – which you might do to update the required version for working with the repository.</span></span>

<span data-ttu-id="117bb-150">Tady je příklad `dotnet-tools.json` souboru:</span><span class="sxs-lookup"><span data-stu-id="117bb-150">Here is an example `dotnet-tools.json` file:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "dotnetsay": {
      "version": "2.1.4",
      "commands": [
        "dotnetsay"
      ]
    },
    "t-rex": {
      "version": "1.0.103",
      "commands": [
        "t-rex"
      ]
    }
  }
}
```

<span data-ttu-id="117bb-151">K odebrání nástroje ze souboru manifestu nástroje, spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="117bb-151">To remove a tool from the tool manifest file, run the following command:</span></span>

```console
dotnet tool uninstall <toolPackageId>
```

<span data-ttu-id="117bb-152">Pro globální a místní nástroje se vyžaduje kompatibilní verze modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="117bb-152">For both global and local tools, a compatible version of the runtime is required.</span></span> <span data-ttu-id="117bb-153">Mnoho nástrojů aktuálně na NuGet.org cílit na .NET Core Runtime 2.1.</span><span class="sxs-lookup"><span data-stu-id="117bb-153">Many tools currently on NuGet.org target .NET Core Runtime 2.1.</span></span> <span data-ttu-id="117bb-154">Instalovat ty, globálně nebo místně, je stále třeba k instalaci [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="117bb-154">To install those globally or locally, you would still need to install the [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

<span data-ttu-id="117bb-155">Další informace najdete v tématu [místní nástroje dřívější verze Preview dokumentace](https://github.com/dotnet/cli/issues/10288).</span><span class="sxs-lookup"><span data-stu-id="117bb-155">For more information, see [Local Tools Early Preview Documentation](https://github.com/dotnet/cli/issues/10288).</span></span>

## <a name="windows-desktop"></a><span data-ttu-id="117bb-156">Plocha Windows</span><span class="sxs-lookup"><span data-stu-id="117bb-156">Windows desktop</span></span>

<span data-ttu-id="117bb-157">Od verze rozhraní .NET Core 3.0 ve verzi Preview 1, můžete vytvářet aplikace klasické pracovní plochy Windows pomocí technologií WPF a Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="117bb-157">Starting with .NET Core 3.0 Preview 1, you can build Windows desktop applications using WPF and Windows Forms.</span></span> <span data-ttu-id="117bb-158">Tyto architektury podporují také pomocí moderních ovládací prvky a Fluent stylů v knihovně Windows uživatelského rozhraní XAML (WinUI) prostřednictvím [XAML ostrovy](/windows/uwp/xaml-platform/xaml-host-controls).</span><span class="sxs-lookup"><span data-stu-id="117bb-158">These frameworks also support using modern controls and Fluent styling from the Windows UI XAML Library (WinUI) via [XAML islands](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<span data-ttu-id="117bb-159">Komponenta Windows Desktop je součástí Windows .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="117bb-159">The Windows Desktop component is part of the Windows .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="117bb-160">Můžete vytvořit novou aplikaci WPF nebo Windows Forms s následujícími `dotnet` příkazy:</span><span class="sxs-lookup"><span data-stu-id="117bb-160">You can create a new WPF or Windows Forms app with the following `dotnet` commands:</span></span>

```console
dotnet new wpf
dotnet new winforms
```

<span data-ttu-id="117bb-161">Můžete také otevřít, spuštění a ladění projektů .NET Core 3.0 WPF a Windows Forms v sadě Visual Studio. 2019 ve verzi Preview 1.</span><span class="sxs-lookup"><span data-stu-id="117bb-161">You can also open, launch, and debug .NET Core 3.0 WPF and Windows Forms projects in Visual Studio 2019 Preview 1.</span></span> <span data-ttu-id="117bb-162">Je aktuálně možné otevřít ve Visual Studio 2017 15.9, ale není podporovaný scénář (a je potřeba [povolit náhledy](https://blogs.msdn.microsoft.com/dotnet/2018/11/13/net-core-tooling-update-for-visual-studio-2017-version-15-9/)).</span><span class="sxs-lookup"><span data-stu-id="117bb-162">It's currently possible to open these projects in Visual Studio 2017 15.9, however, it isn't a supported scenario (and you need to [enable previews](https://blogs.msdn.microsoft.com/dotnet/2018/11/13/net-core-tooling-update-for-visual-studio-2017-version-15-9/)).</span></span>

<span data-ttu-id="117bb-163">Nové projekty jsou stejné jako existující projekty .NET Core, s několika doplňky.</span><span class="sxs-lookup"><span data-stu-id="117bb-163">The new projects are the same as existing .NET Core projects, with a couple additions.</span></span> <span data-ttu-id="117bb-164">Tady je porovnání základní projekt konzoly .NET Core a základního projektu Windows Forms a WPF.</span><span class="sxs-lookup"><span data-stu-id="117bb-164">Here is the comparison of the basic .NET Core console project and a basic Windows Forms and WPF project.</span></span>

<span data-ttu-id="117bb-165">V projektu aplikace konzoly .NET Core, že projekt používá `Microsoft.NET.Sdk` sady SDK a deklaruje závislost na rozhraní .NET Core 3.0 prostřednictvím `netcoreapp3.0` cílovou architekturu.</span><span class="sxs-lookup"><span data-stu-id="117bb-165">In a .NET Core console project, the project uses the `Microsoft.NET.Sdk` SDK and declares a dependency on .NET Core 3.0 via the `netcoreapp3.0` target framework.</span></span> <span data-ttu-id="117bb-166">K vytvoření aplikace pro Windows Desktop, použijte `Microsoft.NET.Sdk.WindowsDesktop` sady SDK a zvolte který uživatelského rozhraní framework použít:</span><span class="sxs-lookup"><span data-stu-id="117bb-166">To create a Windows Desktop app, use the `Microsoft.NET.Sdk.WindowsDesktop` SDK and choose which UI framework to use:</span></span>

```diff
-<Project Sdk="Microsoft.NET.Sdk">
+<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
+   <UseWPF>true</UseWPF>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="117bb-167">Chcete-li tlačítko Windows Forms přes WPF, nastavte `UseWindowsForms` místo `UseWPF`:</span><span class="sxs-lookup"><span data-stu-id="117bb-167">To choose Windows Forms over WPF, set `UseWindowsForms` instead of `UseWPF`:</span></span>

```diff
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
-   <UseWPF>true</UseWPF>
+   <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="117bb-168">Obě `UseWPF` a `UseWindowsForms` může být nastaven na `true` Pokud aplikace používá obě architektury, například když dialogové okno Windows Forms je hostování ovládacího prvku WPF.</span><span class="sxs-lookup"><span data-stu-id="117bb-168">Both `UseWPF` and `UseWindowsForms` can be set to `true` if the app uses both frameworks, for example when a Windows Forms dialog is hosting a WPF control.</span></span>

<span data-ttu-id="117bb-169">Podělte se prosím o svůj názor na [dotnet/winforms](https://github.com/dotnet/winforms/issues), [dotnet/wpf](https://github.com/dotnet/wpf/issues) a [dotnet/jádro](https://github.com/dotnet/core/issues) úložišť.</span><span class="sxs-lookup"><span data-stu-id="117bb-169">Please share your feedback on the [dotnet/winforms](https://github.com/dotnet/winforms/issues),  [dotnet/wpf](https://github.com/dotnet/wpf/issues) and [dotnet/core](https://github.com/dotnet/core/issues) repos.</span></span>

## <a name="fast-built-in-json-support"></a><span data-ttu-id="117bb-170">Rychlé integrovanou podporou JSON</span><span class="sxs-lookup"><span data-stu-id="117bb-170">Fast built-in JSON support</span></span>

<span data-ttu-id="117bb-171">`System.Text.Json.Utf8JsonReader` je vysoce výkonné, s nízkou přidělení, dopředné čtecí modul pro kódování UTF-8 kódovaný JSON čtení z textu `ReadOnlySpan<byte>`.</span><span class="sxs-lookup"><span data-stu-id="117bb-171">`System.Text.Json.Utf8JsonReader` is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>`.</span></span> <span data-ttu-id="117bb-172">`Utf8JsonReader` Je nízké úrovně, základní typ, který můžete využít k vytváření vlastních analyzátorů a deserializers.</span><span class="sxs-lookup"><span data-stu-id="117bb-172">The `Utf8JsonReader` is a foundational, low-level type, that can be leveraged to build custom parsers and deserializers.</span></span> <span data-ttu-id="117bb-173">Přečtení datovou část JSON pomocí nového `Utf8JsonReader` je 2 × rychleji než při použití reader od [Json.NET](https://www.newtonsoft.com/json).</span><span class="sxs-lookup"><span data-stu-id="117bb-173">Reading through a JSON payload using the new `Utf8JsonReader` is 2x faster than using the reader from [Json.NET](https://www.newtonsoft.com/json).</span></span> <span data-ttu-id="117bb-174">Nástroj nepřidělí dokud budete muset actualize tokeny JSON jako řetězce (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="117bb-174">It does not allocate until you need to actualize JSON tokens as (UTF-16) strings.</span></span>

<span data-ttu-id="117bb-175">Toto nové rozhraní API bude zahrnovat následující součásti:</span><span class="sxs-lookup"><span data-stu-id="117bb-175">This new API will include the following components:</span></span>

* <span data-ttu-id="117bb-176">Ve verzi Preview 1: Čtečka JSON (sekvenční přístup)</span><span class="sxs-lookup"><span data-stu-id="117bb-176">In Preview 1: JSON reader (sequential access)</span></span>
* <span data-ttu-id="117bb-177">Chystá: Zápis JSON, modelu DOM (RAM) objektů poco serializátor, objektů poco deserializátor</span><span class="sxs-lookup"><span data-stu-id="117bb-177">Coming next: JSON writer, DOM (random access), poco serializer, poco deserializer</span></span>

<span data-ttu-id="117bb-178">Tady je smyčka čtečku pro `Utf8JsonReader` , který může sloužit jako výchozí bod:</span><span class="sxs-lookup"><span data-stu-id="117bb-178">Here is the basic reader loop for the `Utf8JsonReader` that can be used as a starting point:</span></span>

```csharp
using System.Text.Json;

public static void Utf8JsonReaderLoop(ReadOnlySpan<byte> dataUtf8)
{
    var json = new Utf8JsonReader(dataUtf8, isFinalBlock: true, state: default);

    while (json.Read())
    {
        JsonTokenType tokenType = json.TokenType;
        ReadOnlySpan<byte> valueSpan = json.ValueSpan;
        switch (tokenType)
        {
            case JsonTokenType.StartObject:
            case JsonTokenType.EndObject:
                break;
            case JsonTokenType.StartArray:
            case JsonTokenType.EndArray:
                break;
            case JsonTokenType.PropertyName:
                break;
            case JsonTokenType.String:
                string valueString = json.GetStringValue();
                break;
            case JsonTokenType.Number:
                if (!json.TryGetInt32Value(out int valueInteger))
                {
                    throw new FormatException();
                }
                break;
            case JsonTokenType.True:
            case JsonTokenType.False:
                bool valueBool = json.GetBooleanValue();
                break;
            case JsonTokenType.Null:
                break;
            default:
                throw new ArgumentException();
        }
    }

    dataUtf8 = dataUtf8.Slice((int)json.BytesConsumed);
    JsonReaderState state = json.CurrentState;
}
```

<span data-ttu-id="117bb-179">Má spoléhat ekosystému .NET [Json.NET](https://www.newtonsoft.com/json) a dalších oblíbených knihoven JSON, které dál vhodná rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="117bb-179">The .NET ecosystem has relied on [Json.NET](https://www.newtonsoft.com/json) and other popular JSON libraries, which continue to be good choices.</span></span> <span data-ttu-id="117bb-180">JSON.NET používá .NET řetězce jako jeho základní datový typ, které jsou pod pokličkou UTF-16.</span><span class="sxs-lookup"><span data-stu-id="117bb-180">JSON.NET uses .NET strings as its base datatype, which are UTF-16 under the hood.</span></span> 

<span data-ttu-id="117bb-181">V rozhraní .NET Core 2.1 a 3.0, jsme přidali nová rozhraní API, která umožňuje zápis JSON API (například `Utf8JsonReader`), které vyžadují mnohem méně paměti, na základě `Span<T>` a řetězce UTF-8 a lepší sloužit potřebám vysoce propustné aplikace jako Kestrel ASP. .NET Core webový server.</span><span class="sxs-lookup"><span data-stu-id="117bb-181">In .NET Core 2.1 and 3.0, we added new APIs that makes it possible to write JSON APIs (such as `Utf8JsonReader`) that require much less memory, based on using `Span<T>` and UTF-8 strings, and better serve the needs of high-throughput applications like Kestrel, ASP.NET Core web server.</span></span>

## <a name="ranges-and-indices"></a><span data-ttu-id="117bb-182">Rozsahy a indexy</span><span class="sxs-lookup"><span data-stu-id="117bb-182">Ranges and indices</span></span>

<span data-ttu-id="117bb-183">Nové `Index` typ lze použít k indexování.</span><span class="sxs-lookup"><span data-stu-id="117bb-183">The new `Index` type can be used for indexing.</span></span> <span data-ttu-id="117bb-184">Můžete je vytvořit z `int` , které se počítá od začátku, nebo s předponou `^` – operátor (C#), které se počítá od konce:</span><span class="sxs-lookup"><span data-stu-id="117bb-184">You can create one from an `int` that counts from the beginning, or with a prefix `^` operator (C#) that counts from the end:</span></span>

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

<span data-ttu-id="117bb-185">K dispozici je také `Range` typ, který se skládá ze dvou `Index` hodnoty, jeden pro spuštění a jeden pro ukončení a může být zapsaný s `x..y` výrazu v rozsahu (C#).</span><span class="sxs-lookup"><span data-stu-id="117bb-185">There is also a `Range` type, which consists of two `Index` values, one for the start and one for the end, and can be written with a `x..y` range expression (C#).</span></span> <span data-ttu-id="117bb-186">Potom můžete index s využitím `Range` aby vytvářela řez:</span><span class="sxs-lookup"><span data-stu-id="117bb-186">You can then index with a `Range` in order to produce a slice:</span></span>

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

> [!NOTE]
> <span data-ttu-id="117bb-187">Pouze [ C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2018/11/12/building-c-8-0/) podporuje syntaxi pro `Range` a `Index`.</span><span class="sxs-lookup"><span data-stu-id="117bb-187">Only [C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2018/11/12/building-c-8-0/) supports syntax for `Range` and `Index`.</span></span>

## <a name="async-streams"></a><span data-ttu-id="117bb-188">Asynchronní datové proudy</span><span class="sxs-lookup"><span data-stu-id="117bb-188">Async streams</span></span>

<span data-ttu-id="117bb-189">`IAsyncEnumerable<T>` Typ je nový asynchronní verze `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="117bb-189">The `IAsyncEnumerable<T>` type is a new asynchronous version of `IEnumerable<T>`.</span></span> <span data-ttu-id="117bb-190">Jazyk umožňuje `await foreach` přes tyto využívat jejich prvky a `yield return` k nim pro produkci prvků.</span><span class="sxs-lookup"><span data-stu-id="117bb-190">The language lets you `await foreach` over these to consume their elements, and `yield return` to them to produce elements.</span></span>

<span data-ttu-id="117bb-191">Následující příklad ukazuje produkční scénáře i využití asynchronních streamů.</span><span class="sxs-lookup"><span data-stu-id="117bb-191">The following example demonstrates both production and consumption of async streams.</span></span> <span data-ttu-id="117bb-192">`foreach` Příkaz je asynchronní a sama používá `yield return` vytvoří na asynchronní datový proud pro volající.</span><span class="sxs-lookup"><span data-stu-id="117bb-192">The `foreach` statement is async and itself uses `yield return` to produce an async stream for callers.</span></span> <span data-ttu-id="117bb-193">Tento model (pomocí `yield return`) je doporučený model pro vytváření asynchronních streamů.</span><span class="sxs-lookup"><span data-stu-id="117bb-193">This pattern (using `yield return`) is the recommended model for producing async streams.</span></span>

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result; 
    }
}
```

> [!WARNING]
> <span data-ttu-id="117bb-194">.NET core 3.0 ve verzi Preview 1 nyní obsahuje chybu s `await foreach`.</span><span class="sxs-lookup"><span data-stu-id="117bb-194">.NET Core 3.0 Preview 1 currently has a bug with `await foreach`.</span></span> <span data-ttu-id="117bb-195">Místo toho použijte `GetEnumerator` a `MoveNext` prvkům procesu.</span><span class="sxs-lookup"><span data-stu-id="117bb-195">Instead, use `GetEnumerator` and `MoveNext` to process elements.</span></span> <span data-ttu-id="117bb-196">Další informace najdete v tématu [roslyn / #31268](https://github.com/dotnet/roslyn/issues/31268).</span><span class="sxs-lookup"><span data-stu-id="117bb-196">For more information, see [roslyn/#31268](https://github.com/dotnet/roslyn/issues/31268).</span></span>

<span data-ttu-id="117bb-197">Kromě toho, že možnost `await foreach`, můžete také vytvořit asynchronní iterátory, například iterátoru, který vrátí `IAsyncEnumerable/IAsyncEnumerator` , můžete obě `await` a `yield` v.</span><span class="sxs-lookup"><span data-stu-id="117bb-197">In addition to being able to `await foreach`, you can also create async iterators, for example, an iterator that returns an `IAsyncEnumerable/IAsyncEnumerator` that you can both `await` and `yield` in.</span></span> <span data-ttu-id="117bb-198">Pro objekty, které je potřeba se dá uvolnit, můžete použít `IAsyncDisposable`, které různé typy BCL implementovat jako `Stream` a `Timer`.</span><span class="sxs-lookup"><span data-stu-id="117bb-198">For objects that need to be disposed, you can use `IAsyncDisposable`, which various BCL types implement, such as `Stream` and `Timer`.</span></span>

> [!NOTE]
> <span data-ttu-id="117bb-199">Pouze [ C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2018/11/12/building-c-8-0/) podporuje `await foreach` syntaxe.</span><span class="sxs-lookup"><span data-stu-id="117bb-199">Only [C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2018/11/12/building-c-8-0/) supports `await foreach` syntax.</span></span>

## <a name="type-sequencereader"></a><span data-ttu-id="117bb-200">Zadejte: SequenceReader</span><span class="sxs-lookup"><span data-stu-id="117bb-200">Type: SequenceReader</span></span>

<span data-ttu-id="117bb-201">V rozhraní .NET Core 3.0 `System.Buffers.SequenceReader` se přidala, který může sloužit jako čtečku `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="117bb-201">In .NET Core 3.0, `System.Buffers.SequenceReader` has been added which can be used as a reader for `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="117bb-202">To umožňuje snadné, vysoký výkon s nízkou přidělení parsování `System.IO.Pipelines` data, která lze napříč více vyrovnávacích pamětí zálohování.</span><span class="sxs-lookup"><span data-stu-id="117bb-202">This allows easy, high performance, low allocation parsing of `System.IO.Pipelines` data that can cross multiple backing buffers.</span></span> 

<span data-ttu-id="117bb-203">Následující příklad přeruší vstup `Sequence` do platné `CR/LF` oddělených řádky:</span><span class="sxs-lookup"><span data-stu-id="117bb-203">The following example breaks an input `Sequence` into valid `CR/LF` delimited lines:</span></span>

```csharp
private static ReadOnlySpan<byte> CRLF => new byte[] { (byte)'\r', (byte)'\n' };

public static void ReadLines(ReadOnlySequence<byte> sequence)
{
    SequenceReader<byte> reader = new SequenceReader<byte>(sequence);

    while (!reader.End)
    {
        if (!reader.TryReadToAny(out ReadOnlySpan<byte> line, CRLF, advancePastDelimiter:false))
        {
            // Couldn't find another delimiter
            // ...
        }

        if (!reader.IsNext(CRLF, advancePast: true))
        {
            // Not a good CR/LF pair
            // ...
        }

        // line is valid, process
        ProcessLine(line);
    }
}
```

## <a name="type-metadataloadcontext"></a><span data-ttu-id="117bb-204">Zadejte: MetadataLoadContext</span><span class="sxs-lookup"><span data-stu-id="117bb-204">Type: MetadataLoadContext</span></span>

<span data-ttu-id="117bb-205">`MetadataLoadContext` Byl přidán typ, který umožňuje čtení sestavení metadat, aniž by to ovlivnilo doméně aplikace volajícího.</span><span class="sxs-lookup"><span data-stu-id="117bb-205">The `MetadataLoadContext` type has been added that enables reading assembly metadata without affecting the caller’s application domain.</span></span> <span data-ttu-id="117bb-206">Sestavení se číst jako data, včetně sestavení vytvořená pro rozdílné architektury a platformy než aktuální běhové prostředí.</span><span class="sxs-lookup"><span data-stu-id="117bb-206">Assemblies are read as data, including assemblies built for different architectures and platforms than the current runtime environment.</span></span> <span data-ttu-id="117bb-207">`MetadataLoadContext` se překrývá s <xref:System.Reflection.Assembly.ReflectionOnlyLoad*>, který je k dispozici pouze v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="117bb-207">`MetadataLoadContext` overlaps with the <xref:System.Reflection.Assembly.ReflectionOnlyLoad*>, which is only available in the .NET Framework.</span></span>

<span data-ttu-id="117bb-208">`MetdataLoadContext` je k dispozici v [System.Reflection.MetadataLoadContext balíčku](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext).</span><span class="sxs-lookup"><span data-stu-id="117bb-208">`MetdataLoadContext` is available in the [System.Reflection.MetadataLoadContext package](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext).</span></span> <span data-ttu-id="117bb-209">Jedná se o balíček rozhraní .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="117bb-209">It is a .NET Standard 2.0 package.</span></span>

<span data-ttu-id="117bb-210">`MetadataLoadContext` Zveřejňuje rozhraní API, podobně jako <xref:System.Runtime.Loader.AssemblyLoadContext> typu, ale není na základě tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="117bb-210">The `MetadataLoadContext` exposes APIs similar to the <xref:System.Runtime.Loader.AssemblyLoadContext> type, but is not based on that type.</span></span> <span data-ttu-id="117bb-211">Podobně jako <xref:System.Runtime.Loader.AssemblyLoadContext>, `MetadataLoadContext` povolí načítání sestavení v rámci izolovaného sestavení načítání universe.</span><span class="sxs-lookup"><span data-stu-id="117bb-211">Much like <xref:System.Runtime.Loader.AssemblyLoadContext>, the `MetadataLoadContext` enables loading assemblies within an isolated assembly loading universe.</span></span> <span data-ttu-id="117bb-212">`MetdataLoadContext` Rozhraní API vrací <xref:System.Reflection.Assembly> objekty povoluje použití známých reflexe rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="117bb-212">`MetdataLoadContext` APIs return <xref:System.Reflection.Assembly> objects, enabling the use of familiar reflection APIs.</span></span> <span data-ttu-id="117bb-213">Spuštění orientované rozhraní API, jako například [MethodBase.Invoke](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/src/System/Reflection/TypeLoading/Methods/RoMethod.cs#L127), nejsou povoleny a vyvolá výjimku InvalidOperationException.</span><span class="sxs-lookup"><span data-stu-id="117bb-213">Execution-oriented APIs, such as [MethodBase.Invoke](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/src/System/Reflection/TypeLoading/Methods/RoMethod.cs#L127), are not allowed and will throw InvalidOperationException.</span></span>

<span data-ttu-id="117bb-214">Následující příklad ukazuje, jak najít konkrétní typy v sestavení, který implementuje v příslušném rozhraní:</span><span class="sxs-lookup"><span data-stu-id="117bb-214">The following sample demonstrates how to find concrete types in an assembly that implements a given interface:</span></span>

```csharp
var paths = new string[] {@"C:\myapp\mscorlib.dll", @"C:\myapp\myapp.dll"};
var resolver = new PathAssemblyResolver(paths);
using (var lc = new MetadataLoadContext(resolver))
{
    Assembly a = lc.LoadFromAssemblyName("myapp");
    Type myInterface = a.GetType("MyApp.IPluginInterface");
    foreach (Type t in a.GetTypes())
    {
        if (t.IsClass && myInterface.IsAssignableFrom(t))
            Console.WriteLine($"Class {t.FullName} implements IPluginInterface");
    }
}
```

<span data-ttu-id="117bb-215">Scénáře pro `MetadataLoadContext` obsahují funkce návrhu, nástrojů, čas sestavení a funkce modulu runtime vytáčené světla, které je potřeba zkontrolovat sadu sestavení jako data a mít všech zámků souboru a probíhá po kontrole uvolněná paměť.</span><span class="sxs-lookup"><span data-stu-id="117bb-215">Scenarios for `MetadataLoadContext` include design-time features, build-time tooling, and runtime light-up features that need to inspect a set of assemblies as data and have all file locks and memory freed after inspection is performed.</span></span>

<span data-ttu-id="117bb-216">`MetadataLoadContext` Má třídu překladač předaný konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="117bb-216">The `MetadataLoadContext` has a resolver class passed to its constructor.</span></span> <span data-ttu-id="117bb-217">Úlohy překladače je načtení `Assembly` zadaný jeho `AssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="117bb-217">The resolver's job is to load an `Assembly` given its `AssemblyName`.</span></span> <span data-ttu-id="117bb-218">Překladač třída je odvozena z abstraktní `MetadataAssemblyResolver` třídy.</span><span class="sxs-lookup"><span data-stu-id="117bb-218">The resolver class derives from the abstract `MetadataAssemblyResolver` class.</span></span> <span data-ttu-id="117bb-219">Je součástí implementace překladače pro scénáře na základě cest `PathAssemblyResolver`.</span><span class="sxs-lookup"><span data-stu-id="117bb-219">An implementation of the resolver for path-based scenarios is provided with `PathAssemblyResolver`.</span></span>

<span data-ttu-id="117bb-220">[MetadataLoadContext testy](https://github.com/dotnet/corefx/tree/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests) ukazují, případy použití, mnoho.</span><span class="sxs-lookup"><span data-stu-id="117bb-220">The [MetadataLoadContext tests](https://github.com/dotnet/corefx/tree/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests) demonstrate many use cases.</span></span> <span data-ttu-id="117bb-221">[Sestavení testů](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests/Assembly/AssemblyTests.cs) jsou dobrým začátkem.</span><span class="sxs-lookup"><span data-stu-id="117bb-221">The [Assembly tests](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests/Assembly/AssemblyTests.cs) are a good place to start.</span></span>

## <a name="tls-13--openssl-111-on-linux"></a><span data-ttu-id="117bb-222">TLS verze 1.3 & OpenSSL 1.1.1 v Linuxu</span><span class="sxs-lookup"><span data-stu-id="117bb-222">TLS 1.3 & OpenSSL 1.1.1 on Linux</span></span>

<span data-ttu-id="117bb-223">.NET core se nově využít výhod [podpora protokolu TLS 1.3 v OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), až bude k dispozici v daném prostředí.</span><span class="sxs-lookup"><span data-stu-id="117bb-223">.NET Core will now take advantage of [TLS 1.3 support in OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), when it is available in a given environment.</span></span> <span data-ttu-id="117bb-224">Existuje více výhod TLS 1,3 za [OpenSSL týmu](https://www.openssl.org/blog/blog/2018/09/11/release111/):</span><span class="sxs-lookup"><span data-stu-id="117bb-224">There are multiple benefits of TLS 1.3, per the [OpenSSL team](https://www.openssl.org/blog/blog/2018/09/11/release111/):</span></span>

* <span data-ttu-id="117bb-225">Čas vylepšené připojení z důvodu snížení počet zpátečních cest vyžaduje mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="117bb-225">Improved connection times due to a reduction in the number of round trips required between the client and server.</span></span>

* <span data-ttu-id="117bb-226">Vyšší úroveň zabezpečení z důvodu odstranění různých zastaralé a nezabezpečené kryptografické algoritmy a šifrování větší metoda handshake připojení.</span><span class="sxs-lookup"><span data-stu-id="117bb-226">Improved security due to the removal of various obsolete and insecure cryptographic algorithms and encryption of more of the connection handshake.</span></span>

<span data-ttu-id="117bb-227">.NET core 3.0 ve verzi Preview 1 je schopen využitím **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, nebo **OpenSSL 1.0.2** (cokoli, co nejlepší nalezená verze se v systému Linux).</span><span class="sxs-lookup"><span data-stu-id="117bb-227">.NET Core 3.0 Preview 1 is capable of utilizing **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, or **OpenSSL 1.0.2** (whatever the best version found is, on a Linux system).</span></span>  <span data-ttu-id="117bb-228">Při **OpenSSL 1.1.1** je k dispozici bude používat typy SslStream a HttpClient **TLS 1.3** při použití `SslProtocols.None` (protokoly systému výchozí), za předpokladu, že klient i server podpory **TLS 1.3**.</span><span class="sxs-lookup"><span data-stu-id="117bb-228">When **OpenSSL 1.1.1** is available the SslStream and HttpClient types will use **TLS 1.3** when using `SslProtocols.None` (system default protocols), assuming both the client and server support **TLS 1.3**.</span></span>

<span data-ttu-id="117bb-229">Následující příklad ukazuje .NET Core 3.0 ve verzi Preview 1 na Ubuntu 18.10 propojíte <https://www.cloudflare.com>:</span><span class="sxs-lookup"><span data-stu-id="117bb-229">The following sample demonstrates .NET Core 3.0 Preview 1 on Ubuntu 18.10 connecting to <https://www.cloudflare.com>:</span></span>

```csharp
using System;
using System.Net.Security;
using System.Net.Sockets;
using System.Threading.Tasks;

namespace tlstest
{
    class Program
    {
        static async Task Main()
        {
            using (TcpClient tcpClient = new TcpClient())
            {
                string targetHost = "www.cloudflare.com";

                await tcpClient.ConnectAsync(targetHost, 443);

                using (SslStream sslStream = new SslStream(tcpClient.GetStream()))
                {
                    await sslStream.AuthenticateAsClientAsync(targetHost);
                    await Console.Out.WriteLineAsync($"Connected to {targetHost} with {sslStream.SslProtocol}");
                }
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/tlstest$ dotnet run
Connected to www.cloudflare.com with Tls13
user@comp-ubuntu1810:~/tlstest$ openssl version
OpenSSL 1.1.1  11 Sep 2018
```

>[!IMPORTANT]
><span data-ttu-id="117bb-230">Windows a macOS zatím ještě nepodporují **TLS 1.3**.</span><span class="sxs-lookup"><span data-stu-id="117bb-230">Windows and macOS do not yet support **TLS 1.3**.</span></span> <span data-ttu-id="117bb-231">Bude podporovat .NET core 3.0 **TLS 1.3** v těchto operačních systémech, jakmile je k dispozici podpora.</span><span class="sxs-lookup"><span data-stu-id="117bb-231">.NET Core 3.0 will support **TLS 1.3** on these operating systems when support becomes available.</span></span>

## <a name="cryptography"></a><span data-ttu-id="117bb-232">Kryptografie</span><span class="sxs-lookup"><span data-stu-id="117bb-232">Cryptography</span></span>

<span data-ttu-id="117bb-233">Byla přidána podpora pro **AES-GCM** a **AES-CCM** šifry, prostřednictvím rozhraní `System.Security.Cryptography.AesGcm` a `System.Security.Cryptography.AesCcm`.</span><span class="sxs-lookup"><span data-stu-id="117bb-233">Support has been added for **AES-GCM** and **AES-CCM** ciphers, implemented via `System.Security.Cryptography.AesGcm` and `System.Security.Cryptography.AesCcm`.</span></span> <span data-ttu-id="117bb-234">Tyto algoritmy jsou obě [ověření šifrování pomocí algoritmů přidružení dat (AEAD)](https://en.wikipedia.org/wiki/Authenticated_encryption)a první ověření šifrování (AE) algoritmy přidané do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="117bb-234">These algorithms are both [Authenticated Encryption with Association Data (AEAD) algorithms](https://en.wikipedia.org/wiki/Authenticated_encryption), and the first Authenticated Encryption (AE) algorithms added to .NET Core.</span></span>

<span data-ttu-id="117bb-235">Následující kód ukazuje použití **AesGcm** šifer k šifrování a dešifrování náhodná data.</span><span class="sxs-lookup"><span data-stu-id="117bb-235">The following code demonstrates using **AesGcm** cipher to encrypt and decrypt random data.</span></span>

<span data-ttu-id="117bb-236">Kód pro **AesCcm** by vypadalo téměř identické (pouze názvy tříd, které proměnné by lišit).</span><span class="sxs-lookup"><span data-stu-id="117bb-236">The code for **AesCcm** would look almost identical (only the class variable names would be different).</span></span>

```csharp
// key should be: pre-known, derived, or transported via another channel, such as RSA encryption
byte[] key = new byte[16];
RandomNumberGenerator.Fill(key);

byte[] nonce = new byte[12];
RandomNumberGenerator.Fill(nonce);

// normally this would be your data
byte[] dataToEncrypt = new byte[1234];
byte[] associatedData = new byte[333];
RandomNumberGenerator.Fill(dataToEncrypt);
RandomNumberGenerator.Fill(associatedData);

// these will be filled during the encryption
byte[] tag = new byte[16];
byte[] ciphertext = new byte[dataToEncrypt.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Encrypt(nonce, dataToEncrypt, ciphertext, tag, associatedData);
}

// tag, nonce, ciphertext, associatedData should be sent to the other part

byte[] decryptedData = new byte[ciphertext.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Decrypt(nonce, ciphertext, tag, decryptedData, associatedData);
}

// do something with the data
// this should always print that data is the same
Console.WriteLine($"AES-GCM: Decrypted data is{(dataToEncrypt.SequenceEqual(decryptedData) ? "the same as" : "different than")} original data.");
```

## <a name="cryptographic-key-importexport"></a><span data-ttu-id="117bb-237">Kryptografické klíče Import/Export</span><span class="sxs-lookup"><span data-stu-id="117bb-237">Cryptographic Key Import/Export</span></span>

<span data-ttu-id="117bb-238">.NET core 3.0 ve verzi Preview 1 podporuje import a export asymetrického veřejné a soukromé klíče ze standardní formáty, aniž by bylo nutné použít certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="117bb-238">.NET Core 3.0 Preview 1 supports the import and export of asymmetric public and private keys from standard formats, without needing to use an X.509 certificate.</span></span>

<span data-ttu-id="117bb-239">Všechny klíče podpora typy (RSA, DSA, ECDsa, ECDiffieHellman) **X.509 SubjectPublicKeyInfo** formát pro veřejné klíče a **PKCS #8 PrivateKeyInfo** a **PKCS #8 EncryptedPrivateKeyInfo**  formáty pro privátní klíče.</span><span class="sxs-lookup"><span data-stu-id="117bb-239">All key types (RSA, DSA, ECDsa, ECDiffieHellman) support the **X.509 SubjectPublicKeyInfo** format for public keys, and the **PKCS#8 PrivateKeyInfo** and **PKCS#8 EncryptedPrivateKeyInfo** formats for private keys.</span></span> <span data-ttu-id="117bb-240">Kromě toho podporuje RSA **PKCS #1 RSAPublicKey** a **PKCS #1 RSAPrivateKey**.</span><span class="sxs-lookup"><span data-stu-id="117bb-240">RSA additionally supports **PKCS#1 RSAPublicKey** and **PKCS#1 RSAPrivateKey**.</span></span> <span data-ttu-id="117bb-241">Všechny metody export vytvářejí kódování DER binární data, a metod importu očekávají, že stejné.</span><span class="sxs-lookup"><span data-stu-id="117bb-241">The export methods all produce DER-encoded binary data, and the import methods expect the same.</span></span> <span data-ttu-id="117bb-242">Pokud je klíč uložený ve formátu PEM popisný text, volajícího bude nutné base64 – dekódování obsahu před voláním metody importu.</span><span class="sxs-lookup"><span data-stu-id="117bb-242">If a key is stored in the text-friendly PEM format, the caller will need to base64-decode the content before calling an import method.</span></span>

```csharp
using System;
using System.IO;
using System.Security.Cryptography;

namespace rsakeyprint
{
    class Program
    {
        static void Main(string[] args)
        {
            using (RSA rsa = RSA.Create())
            {
                byte[] keyBytes = File.ReadAllBytes(args[0]);
                rsa.ImportRSAPrivateKey(keyBytes, out int bytesRead);
 
                Console.WriteLine($"Read {bytesRead} bytes, {keyBytes.Length-bytesRead} extra byte(s) in file.");
                RSAParameters rsaParameters = rsa.ExportParameters(true);
                Console.WriteLine(BitConverter.ToString(rsaParameters.D));
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/rsakeyprint$ echo Making a small key to save on screen space.
Making a small key to save on screen space.
user@comp-ubuntu1810:~/rsakeyprint$ openssl genrsa 768 | openssl rsa -outform der -out rsa.key
Generating RSA private key, 768 bit long modulus (2 primes)
..+++++++
........+++++++
e is 65537 (0x010001)
writing RSA key
user@comp-ubuntu1810:~/rsakeyprint$ dotnet run rsa.key
Read 461 bytes, 0 extra byte(s) in file.
0F-D0-82-34-F8-13-38-4A-7F-C7-52-4A-F6-93-F8-FB-6D-98-7A-6A-04-3B-BC-35-8C-7D-AC-A5-A3-6E-AD-C1-66-30-81-2C-2A-DE-DA-60-03-6A-2C-D9-76-15-7F-61-97-57-
79-E1-6E-45-62-C3-83-04-97-CB-32-EF-C5-17-5F-99-60-92-AE-B6-34-6F-30-06-03-AC-BF-15-24-43-84-EB-83-60-EF-4D-3B-BD-D9-5D-56-26-F0-51-CE-F1
user@comp-ubuntu1810:~/rsakeyprint$ openssl rsa -in rsa.key -inform der -text -noout | grep -A7 private
privateExponent:
    0f:d0:82:34:f8:13:38:4a:7f:c7:52:4a:f6:93:f8:
    fb:6d:98:7a:6a:04:3b:bc:35:8c:7d:ac:a5:a3:6e:
    ad:c1:66:30:81:2c:2a:de:da:60:03:6a:2c:d9:76:
    15:7f:61:97:57:79:e1:6e:45:62:c3:83:04:97:cb:
    32:ef:c5:17:5f:99:60:92:ae:b6:34:6f:30:06:03:
    ac:bf:15:24:43:84:eb:83:60:ef:4d:3b:bd:d9:5d:
    56:26:f0:51:ce:f1
```

<span data-ttu-id="117bb-243">Soubory PKCS č. 8 můžete prozkoumat pomocí `System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo` třídy.</span><span class="sxs-lookup"><span data-stu-id="117bb-243">PKCS#8 files can be inspected with the `System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo` class.</span></span>

<span data-ttu-id="117bb-244">Soubory PFX/PKCS #12, můžete ho zkontrolovat a manipulovat s `System.Security.Cryptography.Pkcs.Pkcs12Info` a `System.Security.Cryptography.Pkcs.Pkcs12Builder`v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="117bb-244">PFX/PKCS#12 files can be inspected and manipulated with `System.Security.Cryptography.Pkcs.Pkcs12Info` and `System.Security.Cryptography.Pkcs.Pkcs12Builder`, respectively.</span></span>

## <a name="serialport-for-linux"></a><span data-ttu-id="117bb-245">SerialPort pro Linux</span><span class="sxs-lookup"><span data-stu-id="117bb-245">SerialPort for Linux</span></span>

<span data-ttu-id="117bb-246">.NET core 3.0 nyní podporuje <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> v Linuxu.</span><span class="sxs-lookup"><span data-stu-id="117bb-246">.NET Core 3.0 now supports <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> on Linux.</span></span>

<span data-ttu-id="117bb-247">Dříve, .NET Core, které jsou podporovány pouze při použití `SerialPort` typu na Windows.</span><span class="sxs-lookup"><span data-stu-id="117bb-247">Previously, .NET Core only supported using the `SerialPort` type on Windows.</span></span>

## <a name="more-bcl-improvements"></a><span data-ttu-id="117bb-248">Další vylepšení BCL</span><span class="sxs-lookup"><span data-stu-id="117bb-248">More BCL Improvements</span></span>

<span data-ttu-id="117bb-249">`Span<T>`, `Memory<T>`, A souvisejících typů, které byly zavedeny v .NET Core 2.1, byly optimalizovány odstraněním v .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="117bb-249">The `Span<T>`, `Memory<T>`, and related types that were introduced in .NET Core 2.1, have been optimized in .NET Core 3.0.</span></span> <span data-ttu-id="117bb-250">Běžné operace, jako span konstrukce, dělení, analýzy a formátování nyní líp fungovat.</span><span class="sxs-lookup"><span data-stu-id="117bb-250">Common operations such as span construction, slicing, parsing, and formatting now perform better.</span></span> 

<span data-ttu-id="117bb-251">Kromě toho, jako jsou typy `String` viděli v rámci titulní vylepšení je zefektivňují při použití jako klíče s `Dictionary<TKey, TValue>` i další kolekce.</span><span class="sxs-lookup"><span data-stu-id="117bb-251">Additionally, types like `String` have seen under-the-cover improvements to make them more efficient when used as keys with `Dictionary<TKey, TValue>` and other collections.</span></span> <span data-ttu-id="117bb-252">Abyste využili výhod těchto vylepšení nevyžaduje žádné změny kódu.</span><span class="sxs-lookup"><span data-stu-id="117bb-252">No code changes are required to benefit from these improvements.</span></span>

<span data-ttu-id="117bb-253">Tato vylepšení jsou také nové v rozhraní .NET Core 3 Preview 1:</span><span class="sxs-lookup"><span data-stu-id="117bb-253">The following improvements are also new in .NET Core 3 Preview 1:</span></span>

* <span data-ttu-id="117bb-254">Podpora Brotli součástí HttpClient</span><span class="sxs-lookup"><span data-stu-id="117bb-254">Brotli support built in to HttpClient</span></span>
* <span data-ttu-id="117bb-255">ThreadPool.UnsafeQueueWorkItem(IThreadPoolWorkItem)</span><span class="sxs-lookup"><span data-stu-id="117bb-255">ThreadPool.UnsafeQueueWorkItem(IThreadPoolWorkItem)</span></span>
* <span data-ttu-id="117bb-256">Unsafe.Unbox</span><span class="sxs-lookup"><span data-stu-id="117bb-256">Unsafe.Unbox</span></span>
* <span data-ttu-id="117bb-257">CancellationToken.Unregister</span><span class="sxs-lookup"><span data-stu-id="117bb-257">CancellationToken.Unregister</span></span>
* <span data-ttu-id="117bb-258">Komplexní aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="117bb-258">Complex arithmetic operators</span></span>
* <span data-ttu-id="117bb-259">Zachování soketu rozhraní API pro protokol TCP</span><span class="sxs-lookup"><span data-stu-id="117bb-259">Socket APIs for TCP keep alive</span></span>
* <span data-ttu-id="117bb-260">StringBuilder.GetChunks</span><span class="sxs-lookup"><span data-stu-id="117bb-260">StringBuilder.GetChunks</span></span>
* <span data-ttu-id="117bb-261">IPEndPoint analýza kódu</span><span class="sxs-lookup"><span data-stu-id="117bb-261">IPEndPoint parsing</span></span>
* <span data-ttu-id="117bb-262">RandomNumberGenerator.GetInt32</span><span class="sxs-lookup"><span data-stu-id="117bb-262">RandomNumberGenerator.GetInt32</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="117bb-263">Vrstvené kompilace</span><span class="sxs-lookup"><span data-stu-id="117bb-263">Tiered compilation</span></span>

<span data-ttu-id="117bb-264">[Vrstvené kompilace](https://blogs.msdn.microsoft.com/dotnet/2018/08/02/tiered-compilation-preview-in-net-core-2-1/) je ve výchozím s .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="117bb-264">[Tiered compilation](https://blogs.msdn.microsoft.com/dotnet/2018/08/02/tiered-compilation-preview-in-net-core-2-1/) is on by default with .NET Core 3.0.</span></span> <span data-ttu-id="117bb-265">To je funkce, která umožňuje modulu runtime více Adaptivně pomocí kompilátor za běhu (JIT), můžete dosáhnout lepšího výkonu, jak při spuštění a maximalizuje propustnost.</span><span class="sxs-lookup"><span data-stu-id="117bb-265">It is a feature that enables the runtime to more adaptively use the Just-In-Time (JIT) compiler to get better performance, both at startup and to maximize throughput.</span></span>

<span data-ttu-id="117bb-266">Tato funkce byla přidána jako funkce opt-in v [.NET Core 2.1](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/) a potom byla povolená ve výchozím nastavení v [.NET Core 2.2 ve verzi Preview 2](https://blogs.msdn.microsoft.com/dotnet/2018/09/12/announcing-net-core-2-2-preview-2/).</span><span class="sxs-lookup"><span data-stu-id="117bb-266">This feature was added as an opt-in feature in [.NET Core 2.1](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/) and then was enabled by default in [.NET Core 2.2 Preview 2](https://blogs.msdn.microsoft.com/dotnet/2018/09/12/announcing-net-core-2-2-preview-2/).</span></span> <span data-ttu-id="117bb-267">Následně ji byl vrácen zpět do optimalizované pomocí verze rozhraní .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="117bb-267">Subsequently, it has been reverted back to opt in with the .NET Core 2.2 release.</span></span>

## <a name="arm64-linux-support"></a><span data-ttu-id="117bb-268">Podpora Linuxu ARM64</span><span class="sxs-lookup"><span data-stu-id="117bb-268">ARM64 Linux support</span></span>

<span data-ttu-id="117bb-269">Přidáváme podporu pro ARM64 pro tuto verzi systému Linux.</span><span class="sxs-lookup"><span data-stu-id="117bb-269">We are adding support for ARM64 for Linux this release.</span></span> <span data-ttu-id="117bb-270">Pro kontext přidali jsme podporu pro ARM32 pro Linux s .NET Core 2.1 a Windows s nástroji .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="117bb-270">For context, we added support for ARM32 for Linux with .NET Core 2.1 and Windows with .NET Core 2.2.</span></span> <span data-ttu-id="117bb-271">Případem primárního použití pro ARM64 je aktuálně s scénáře IoT.</span><span class="sxs-lookup"><span data-stu-id="117bb-271">The primary use case for ARM64 is currently with IoT scenarios.</span></span>

<span data-ttu-id="117bb-272">Nástroj Alpine, Debian a Ubuntu [imagí Dockeru, které jsou dostupné pro .NET Core pro ARM64](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="117bb-272">Alpine, Debian and Ubuntu [Docker images are available for .NET Core for ARM64](https://hub.docker.com/r/microsoft/dotnet/).</span></span>

<span data-ttu-id="117bb-273">Zkontrolujte prosím [.NET Core ARM64 stav](https://github.com/dotnet/announcements/issues/82) Další informace.</span><span class="sxs-lookup"><span data-stu-id="117bb-273">Please check [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82) for more information.</span></span>

>[!NOTE]
> <span data-ttu-id="117bb-274">**ARM64** podporu Windows ještě není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="117bb-274">**ARM64** Windows support isn't yet available.</span></span>
