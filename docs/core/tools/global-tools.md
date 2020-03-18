---
title: Nástroje .NET Core
description: Jak nainstalovat, používat, aktualizovat a odebírat nástroje .NET Core. Zahrnuje globální nástroje, nástroje pro cestu nástrojů a místní nástroje.
author: KathleenDollard
ms.date: 02/12/2020
ms.openlocfilehash: 2f0101c6385c41eda49bcb2458428c1f14552617
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847781"
---
# <a name="how-to-manage-net-core-tools"></a><span data-ttu-id="1b15b-104">Správa nástrojů .NET Core</span><span class="sxs-lookup"><span data-stu-id="1b15b-104">How to manage .NET Core tools</span></span>

<span data-ttu-id="1b15b-105">**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="1b15b-105">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="1b15b-106">Nástroj .NET Core je speciální balíček NuGet, který obsahuje konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1b15b-106">A .NET Core tool is a special NuGet package that contains a console application.</span></span> <span data-ttu-id="1b15b-107">Nástroj lze do počítače nainstalovat následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="1b15b-107">A tool can be installed on your machine in the following ways:</span></span>

* <span data-ttu-id="1b15b-108">Jako globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="1b15b-108">As a global tool.</span></span>

  <span data-ttu-id="1b15b-109">Binární soubory nástrojů jsou nainstalovány ve výchozím adresáři, který je přidán do proměnné prostředí PATH.</span><span class="sxs-lookup"><span data-stu-id="1b15b-109">The tool binaries are installed in a default directory that is added to the PATH environment variable.</span></span> <span data-ttu-id="1b15b-110">Nástroj můžete vyvolat z libovolného adresáře v počítači bez určení jeho umístění.</span><span class="sxs-lookup"><span data-stu-id="1b15b-110">You can invoke the tool from any directory on the machine without specifying its location.</span></span> <span data-ttu-id="1b15b-111">Jedna verze nástroje se používá pro všechny adresáře na stroji.</span><span class="sxs-lookup"><span data-stu-id="1b15b-111">One version of a tool is used for all directories on the machine.</span></span>

* <span data-ttu-id="1b15b-112">Jako globální nástroj ve vlastním umístění (označovaný také jako nástroj cesty nástroje).</span><span class="sxs-lookup"><span data-stu-id="1b15b-112">As a global tool in a custom location (also known as a tool-path tool).</span></span>

  <span data-ttu-id="1b15b-113">Binární soubory nástrojů jsou nainstalovány v zadaném umístění.</span><span class="sxs-lookup"><span data-stu-id="1b15b-113">The tool binaries are installed in a location that you specify.</span></span> <span data-ttu-id="1b15b-114">Nástroj můžete vyvolat z instalačního adresáře nebo poskytnutím názvu příkazu nebo přidáním adresáře do proměnné prostředí PATH.</span><span class="sxs-lookup"><span data-stu-id="1b15b-114">You can invoke the tool from the installation directory or by providing the directory with the command name or by adding the directory to the PATH environment variable.</span></span> <span data-ttu-id="1b15b-115">Jedna verze nástroje se používá pro všechny adresáře na stroji.</span><span class="sxs-lookup"><span data-stu-id="1b15b-115">One version of a tool is used for all directories on the machine.</span></span>

* <span data-ttu-id="1b15b-116">Jako místní nástroj (platí pro .NET Core SDK 3.0 a novější).</span><span class="sxs-lookup"><span data-stu-id="1b15b-116">As a local tool (applies to .NET Core SDK 3.0 and later).</span></span>

  <span data-ttu-id="1b15b-117">Binární soubory nástrojů jsou nainstalovány ve výchozím adresáři.</span><span class="sxs-lookup"><span data-stu-id="1b15b-117">The tool binaries are installed in a default directory.</span></span> <span data-ttu-id="1b15b-118">Nástroj vyvoláte z instalačního adresáře nebo některého z jeho podadresářů.</span><span class="sxs-lookup"><span data-stu-id="1b15b-118">You invoke the tool from the installation directory or any of its subdirectories.</span></span> <span data-ttu-id="1b15b-119">Různé adresáře mohou používat různé verze stejného nástroje.</span><span class="sxs-lookup"><span data-stu-id="1b15b-119">Different directories can use different versions of the same tool.</span></span>
  
  <span data-ttu-id="1b15b-120">Rozhraní .NET CLI používá soubory manifestu ke sledování, které nástroje jsou nainstalovány jako místní do adresáře.</span><span class="sxs-lookup"><span data-stu-id="1b15b-120">The .NET CLI uses manifest files to keep track of which tools are installed as local to a directory.</span></span> <span data-ttu-id="1b15b-121">Když je soubor manifestu uložen v kořenovém adresáři úložiště zdrojového kódu, může přispěvatel naklonovat úložiště a vyvolat jeden příkaz ROZHRANÍ PŘÍKAZU .NET Core, který nainstaluje všechny nástroje uvedené v souborech manifestu.</span><span class="sxs-lookup"><span data-stu-id="1b15b-121">When the manifest file is saved in the root directory of a source code repository, a contributor can clone the repository and invoke a single .NET Core CLI command that installs all of the tools listed in the manifest files.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1b15b-122">Nástroje .NET Core jsou spuštěny v plném vztahu důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="1b15b-122">.NET Core tools run in full trust.</span></span> <span data-ttu-id="1b15b-123">Neinstalujte nástroj .NET Core, pokud autorovi nedůvěřujete.</span><span class="sxs-lookup"><span data-stu-id="1b15b-123">Do not install a .NET Core tool unless you trust the author.</span></span>

## <a name="find-a-tool"></a><span data-ttu-id="1b15b-124">Nalezení nástroje</span><span class="sxs-lookup"><span data-stu-id="1b15b-124">Find a tool</span></span>

<span data-ttu-id="1b15b-125">V současné době rozhraní .NET Core nemá funkci vyhledávání nástrojů.</span><span class="sxs-lookup"><span data-stu-id="1b15b-125">Currently, .NET Core doesn't have a tool search feature.</span></span> <span data-ttu-id="1b15b-126">Zde je několik způsobů, jak najít nástroje:</span><span class="sxs-lookup"><span data-stu-id="1b15b-126">Here are some ways to find tools:</span></span>

* <span data-ttu-id="1b15b-127">Podívejte se na seznam nástrojů v úložišti GitHub [natemcmaster/dotnet-tools.](https://github.com/natemcmaster/dotnet-tools)</span><span class="sxs-lookup"><span data-stu-id="1b15b-127">See the list of tools in the [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub repository.</span></span>
* <span data-ttu-id="1b15b-128">Pomocí [nástroje ToolGet](https://www.toolget.net/) vyhledejte nástroje rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="1b15b-128">Use [ToolGet](https://www.toolget.net/) to search for .NET tools.</span></span>
* <span data-ttu-id="1b15b-129">Podívejte se na zdrojový kód nástrojů vytvořených týmem ASP.NET Core v [adresáři Tools úložiště GitHub dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/tree/master/src/Tools).</span><span class="sxs-lookup"><span data-stu-id="1b15b-129">See the source code for the tools created by the ASP.NET Core team in the [Tools directory of the dotnet/aspnetcore GitHub repository](https://github.com/dotnet/aspnetcore/tree/master/src/Tools).</span></span>
* <span data-ttu-id="1b15b-130">Informace o diagnostických nástrojích naleznete v [diagnostických nástrojích .NET Core dotnet](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools).</span><span class="sxs-lookup"><span data-stu-id="1b15b-130">Learn about diagnostic tools at [.NET Core dotnet diagnostic tools](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools).</span></span>
* <span data-ttu-id="1b15b-131">Prohledejte web [NuGet.](https://www.nuget.org)</span><span class="sxs-lookup"><span data-stu-id="1b15b-131">Search the [NuGet](https://www.nuget.org) website.</span></span> <span data-ttu-id="1b15b-132">Web NuGet však ještě nemá funkci, která umožňuje vyhledávat pouze balíčky nástrojů.</span><span class="sxs-lookup"><span data-stu-id="1b15b-132">However, the NuGet site doesn't yet have a feature that lets you search only for tool packages.</span></span>

## <a name="check-the-author-and-statistics"></a><span data-ttu-id="1b15b-133">Podívejte se na autora a statistiky</span><span class="sxs-lookup"><span data-stu-id="1b15b-133">Check the author and statistics</span></span>

<span data-ttu-id="1b15b-134">Vzhledem k tomu, že nástroje .NET Core běží v plné důvěryhodnosti a globální nástroje jsou přidány do proměnné prostředí PATH, mohou být velmi výkonné.</span><span class="sxs-lookup"><span data-stu-id="1b15b-134">Since .NET Core tools run in full trust, and global tools are added to the PATH environment variable, they can be very powerful.</span></span> <span data-ttu-id="1b15b-135">Nestahujte nástroje od lidí, kterým nedůvěřujete.</span><span class="sxs-lookup"><span data-stu-id="1b15b-135">Don't download tools from people you don't trust.</span></span>

<span data-ttu-id="1b15b-136">Pokud je nástroj hostován na NuGet, můžete zkontrolovat autora a statistiky hledáním nástroje.</span><span class="sxs-lookup"><span data-stu-id="1b15b-136">If the tool is hosted on NuGet, you can check the author and statistics by searching for the tool.</span></span>

## <a name="install-a-global-tool"></a><span data-ttu-id="1b15b-137">Instalace globálního nástroje</span><span class="sxs-lookup"><span data-stu-id="1b15b-137">Install a global tool</span></span>

<span data-ttu-id="1b15b-138">Chcete-li nainstalovat nástroj jako globální `-g` `--global` nástroj, použijte možnost nebo [instalaci nástroje dotnet](dotnet-tool-install.md), jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="1b15b-138">To install a tool as a global tool, use the `-g` or `--global` option of [dotnet tool install](dotnet-tool-install.md), as shown in the following example:</span></span>

```dotnetcli
dotnet tool install -g dotnetsay
```

<span data-ttu-id="1b15b-139">Výstup zobrazuje příkaz použitý k vyvolání nainstalovaného nástroje a nainstalované verze, podobně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="1b15b-139">The output shows the command used to invoke the tool and the version installed, similar to the following example:</span></span>

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
```

<span data-ttu-id="1b15b-140">Výchozí umístění binárních souborů nástroje závisí na operačním systému:</span><span class="sxs-lookup"><span data-stu-id="1b15b-140">The default location for a tool's binaries depends on the operating system:</span></span>

| <span data-ttu-id="1b15b-141">Operační systém</span><span class="sxs-lookup"><span data-stu-id="1b15b-141">OS</span></span>          | <span data-ttu-id="1b15b-142">Cesta</span><span class="sxs-lookup"><span data-stu-id="1b15b-142">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="1b15b-143">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="1b15b-143">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="1b15b-144">Windows</span><span class="sxs-lookup"><span data-stu-id="1b15b-144">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="1b15b-145">Toto umístění je přidáno do cesty uživatele při prvním spuštění sady SDK, takže globální nástroje lze vyvolat z libovolného adresáře bez určení umístění nástroje.</span><span class="sxs-lookup"><span data-stu-id="1b15b-145">This location is added to the user's path when the SDK is first run, so global tools can be invoked from any directory without specifying the tool location.</span></span>

<span data-ttu-id="1b15b-146">Přístup k nástrojům je specifický pro uživatele, nikoli globální počítač.</span><span class="sxs-lookup"><span data-stu-id="1b15b-146">Tool access is user-specific, not machine global.</span></span> <span data-ttu-id="1b15b-147">Globální nástroj je k dispozici pouze uživateli, který nástroj nainstaloval.</span><span class="sxs-lookup"><span data-stu-id="1b15b-147">A global tool is only available to the user that installed the tool.</span></span>

### <a name="install-a-global-tool-in-a-custom-location"></a><span data-ttu-id="1b15b-148">Instalace globálního nástroje do vlastního umístění</span><span class="sxs-lookup"><span data-stu-id="1b15b-148">Install a global tool in a custom location</span></span>

<span data-ttu-id="1b15b-149">Chcete-li nainstalovat nástroj jako globální nástroj do `--tool-path` vlastního umístění, použijte možnost [instalace nástroje dotnet](dotnet-tool-install.md), jak je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="1b15b-149">To install a tool as a global tool in a custom location, use the `--tool-path` option of [dotnet tool install](dotnet-tool-install.md), as shown in the following examples.</span></span>

<span data-ttu-id="1b15b-150">Ve Windows:</span><span class="sxs-lookup"><span data-stu-id="1b15b-150">On Windows:</span></span>

```dotnetcli
dotnet tool install dotnetsay --tool-path c:\dotnet-tools
```

<span data-ttu-id="1b15b-151">Na Linuxu nebo macOS:</span><span class="sxs-lookup"><span data-stu-id="1b15b-151">On Linux or macOS:</span></span>

```dotnetcli
dotnet tool install dotnetsay --tool-path ~/bin
```

<span data-ttu-id="1b15b-152">Sada .NET Core SDK nepřidá toto umístění automaticky do proměnné prostředí PATH.</span><span class="sxs-lookup"><span data-stu-id="1b15b-152">The .NET Core SDK doesn't add this location automatically to the PATH environment variable.</span></span> <span data-ttu-id="1b15b-153">[Chcete-li vyvolat nástroj cesty nástroje](#invoke-a-tool-path-tool), musíte se ujistit, že příkaz je k dispozici pomocí jedné z následujících metod:</span><span class="sxs-lookup"><span data-stu-id="1b15b-153">To [invoke a tool-path tool](#invoke-a-tool-path-tool), you have to make sure the command is available by using one of the following methods:</span></span>

* <span data-ttu-id="1b15b-154">Přidejte instalační adresář do proměnné prostředí PATH.</span><span class="sxs-lookup"><span data-stu-id="1b15b-154">Add the installation directory to the PATH environment variable.</span></span>
* <span data-ttu-id="1b15b-155">Určete úplnou cestu k nástroji, když ho vyvoláte.</span><span class="sxs-lookup"><span data-stu-id="1b15b-155">Specify the full path to the tool when you invoke it.</span></span>
* <span data-ttu-id="1b15b-156">Vyvolat nástroj z instalačního adresáře.</span><span class="sxs-lookup"><span data-stu-id="1b15b-156">Invoke the tool from within the installation directory.</span></span>

## <a name="install-a-local-tool"></a><span data-ttu-id="1b15b-157">Instalace místního nástroje</span><span class="sxs-lookup"><span data-stu-id="1b15b-157">Install a local tool</span></span>

<span data-ttu-id="1b15b-158">**Platí pro .NET Core 3.0 SDK a novější.**</span><span class="sxs-lookup"><span data-stu-id="1b15b-158">**Applies to .NET Core 3.0 SDK and later.**</span></span>

<span data-ttu-id="1b15b-159">Chcete-li nainstalovat nástroj pouze pro místní přístup (pro aktuální adresář a podadresáře), musí být přidán do souboru manifestu nástroje.</span><span class="sxs-lookup"><span data-stu-id="1b15b-159">To install a tool for local access only (for the current directory and subdirectories), it has to be added to a tool manifest file.</span></span> <span data-ttu-id="1b15b-160">Chcete-li vytvořit soubor manifestu nástroje, spusťte `dotnet new tool-manifest` příkaz:</span><span class="sxs-lookup"><span data-stu-id="1b15b-160">To create a tool manifest file, run the `dotnet new tool-manifest` command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="1b15b-161">Tento příkaz vytvoří soubor manifestu s názvem *dotnet-tools.json* pod adresářem *.config.*</span><span class="sxs-lookup"><span data-stu-id="1b15b-161">This command creates a manifest file named *dotnet-tools.json* under the *.config* directory.</span></span> <span data-ttu-id="1b15b-162">Chcete-li do souboru manifestu přidat místní nástroj, použijte příkaz `--global` instalace `--tool-path` [nástroje dotnet](dotnet-tool-install.md) a **vynechejte** volby a, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="1b15b-162">To add a local tool to the manifest file, use the [dotnet tool install](dotnet-tool-install.md) command and **omit** the `--global` and `--tool-path` options, as shown in the following example:</span></span>

```dotnetcli
dotnet tool install dotnetsay
```

<span data-ttu-id="1b15b-163">Výstup příkazu ukazuje, ve kterém souboru manifestu se nově nainstalovaný nástroj nachází, podobně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="1b15b-163">The command output shows which manifest file the newly installed tool is in, similar to the following example:</span></span>

```console
You can invoke the tool from this directory using the following command:
dotnet tool run dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
Entry is added to the manifest file /home/name/botsay/.config/dotnet-tools.json.
```

<span data-ttu-id="1b15b-164">Následující příklad ukazuje soubor manifestu se dvěma nainstalovanými místními nástroji:</span><span class="sxs-lookup"><span data-stu-id="1b15b-164">The following example shows a manifest file with two local tools installed:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "botsay": {
      "version": "1.0.0",
      "commands": [
        "botsay"
      ]
    },
    "dotnetsay": {
      "version": "2.1.3",
      "commands": [
        "dotnetsay"
      ]
    }
  }
}
```

<span data-ttu-id="1b15b-165">Obvykle přidáte místní nástroj do kořenového adresáře úložiště.</span><span class="sxs-lookup"><span data-stu-id="1b15b-165">You typically add a local tool to the root directory of the repository.</span></span> <span data-ttu-id="1b15b-166">Po vrácení souboru manifestu do úložiště se vývojáři, kteří z úložiště získají kód, získají nejnovější soubor manifestu.</span><span class="sxs-lookup"><span data-stu-id="1b15b-166">After you check in the manifest file to the repository, developers who check out code from the repository get the latest manifest file.</span></span> <span data-ttu-id="1b15b-167">Chcete-li nainstalovat všechny nástroje uvedené v souboru manifestu, `dotnet tool restore` spustí příkaz:</span><span class="sxs-lookup"><span data-stu-id="1b15b-167">To install all of the tools listed in the manifest file, they run the `dotnet tool restore` command:</span></span>

```dotnetcli
dotnet tool restore
```

<span data-ttu-id="1b15b-168">Výstup označuje, které nástroje byly obnoveny:</span><span class="sxs-lookup"><span data-stu-id="1b15b-168">The output indicates which tools were restored:</span></span>

```console
Tool 'botsay' (version '1.0.0') was restored. Available commands: botsay
Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
Restore was successful.
```

## <a name="install-a-specific-tool-version"></a><span data-ttu-id="1b15b-169">Instalace konkrétní verze nástroje</span><span class="sxs-lookup"><span data-stu-id="1b15b-169">Install a specific tool version</span></span>

<span data-ttu-id="1b15b-170">Chcete-li nainstalovat předběžnou verzi nebo určitou verzi nástroje, zadejte číslo verze pomocí `--version` této možnosti, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="1b15b-170">To install a pre-release version or a specific version of a tool, specify the version number by using the `--version` option, as shown in the following example:</span></span>

```dotnetcli
dotnet tool install dotnetsay --version 2.1.3
```

## <a name="use-a-tool"></a><span data-ttu-id="1b15b-171">Použití nástroje</span><span class="sxs-lookup"><span data-stu-id="1b15b-171">Use a tool</span></span>

<span data-ttu-id="1b15b-172">Příkaz, který použijete k vyvolání nástroje, se může lišit od názvu balíčku, který nainstalujete.</span><span class="sxs-lookup"><span data-stu-id="1b15b-172">The command that you use to invoke a tool may be different from the name of the package that you install.</span></span> <span data-ttu-id="1b15b-173">Chcete-li zobrazit všechny nástroje aktuálně nainstalované v počítači pro aktuálního uživatele, použijte příkaz [seznam nástrojů dotnet:](dotnet-tool-list.md)</span><span class="sxs-lookup"><span data-stu-id="1b15b-173">To display all of the tools currently installed on the machine for the current user, use the [dotnet tool list](dotnet-tool-list.md) command:</span></span>

```dotnetcli
dotnet tool list
```

<span data-ttu-id="1b15b-174">Výstup zobrazuje verzi a příkaz každého nástroje, podobně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="1b15b-174">The output shows each tool's version and command, similar to the following example:</span></span>

```console
Package Id      Version      Commands       Manifest
-------------------------------------------------------------------------------------------
botsay          1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
dotnetsay       2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
```

<span data-ttu-id="1b15b-175">Jak je znázorněno v tomto příkladu, seznam zobrazuje místní nástroje.</span><span class="sxs-lookup"><span data-stu-id="1b15b-175">As shown in this example, the list shows local tools.</span></span> <span data-ttu-id="1b15b-176">Chcete-li zobrazit globální `--global` nástroje, použijte tuto možnost a `--tool-path` nástroje cesty nástroje, použijte ji.</span><span class="sxs-lookup"><span data-stu-id="1b15b-176">To see global tools, use the `--global` option, and to see tool-path tools, use the `--tool-path` option.</span></span>

### <a name="invoke-a-global-tool"></a><span data-ttu-id="1b15b-177">Vyvolání globálního nástroje</span><span class="sxs-lookup"><span data-stu-id="1b15b-177">Invoke a global tool</span></span>

<span data-ttu-id="1b15b-178">Pro globální nástroje použijte příkaz nástroje sám o sobě.</span><span class="sxs-lookup"><span data-stu-id="1b15b-178">For global tools, use the tool command by itself.</span></span> <span data-ttu-id="1b15b-179">Například pokud je `dotnetsay` příkaz `dotnet-doc`nebo , to je to, co používáte k vyvolání příkazu:</span><span class="sxs-lookup"><span data-stu-id="1b15b-179">For example, if the command is `dotnetsay` or `dotnet-doc`, that's what you use to invoke the command:</span></span>

```console
dotnetsay
dotnet-doc
```

<span data-ttu-id="1b15b-180">Pokud příkaz začíná předponou `dotnet-`, alternativním způsobem vyvolání nástroje `dotnet` je použití příkazu a vynechání předpony příkazu nástroje.</span><span class="sxs-lookup"><span data-stu-id="1b15b-180">If the command begins with the prefix `dotnet-`, an alternative way to invoke the tool is to use the `dotnet` command and omit the tool command prefix.</span></span> <span data-ttu-id="1b15b-181">Pokud je `dotnet-doc`například příkaz , následující příkaz vyvolá nástroj:</span><span class="sxs-lookup"><span data-stu-id="1b15b-181">For example, if the command is `dotnet-doc`, the following command invokes the tool:</span></span>

```dotnetcli
dotnet doc
```

<span data-ttu-id="1b15b-182">V následujícím scénáři však nelze `dotnet` použít příkaz k vyvolání globálního nástroje:</span><span class="sxs-lookup"><span data-stu-id="1b15b-182">However, in the following scenario you can't use the `dotnet` command to invoke a global tool:</span></span>

* <span data-ttu-id="1b15b-183">Globální nástroj a místní nástroj mají stejný `dotnet-`příkaz předponou .</span><span class="sxs-lookup"><span data-stu-id="1b15b-183">A global tool and a local tool have the same command prefixed by `dotnet-`.</span></span>
* <span data-ttu-id="1b15b-184">Chcete vyvolat globální nástroj z adresáře, který je v oboru pro místní nástroj.</span><span class="sxs-lookup"><span data-stu-id="1b15b-184">You want to invoke the global tool from a directory that is in scope for the local tool.</span></span>

<span data-ttu-id="1b15b-185">V tomto `dotnet doc` scénáři a `dotnet dotnet-doc` vyvolat místní nástroj.</span><span class="sxs-lookup"><span data-stu-id="1b15b-185">In this scenario, `dotnet doc` and `dotnet dotnet-doc` invoke the local tool.</span></span> <span data-ttu-id="1b15b-186">Chcete-li vyvolat globální nástroj, použijte příkaz sám o sobě:</span><span class="sxs-lookup"><span data-stu-id="1b15b-186">To invoke the global tool, use the command by itself:</span></span>

```dotnetcli
dotnet-doc
```

### <a name="invoke-a-tool-path-tool"></a><span data-ttu-id="1b15b-187">Vyvolání nástroje cesty nástroje</span><span class="sxs-lookup"><span data-stu-id="1b15b-187">Invoke a tool-path tool</span></span>

<span data-ttu-id="1b15b-188">Chcete-li vyvolat globální nástroj, `tool-path` který je nainstalován pomocí této možnosti, ujistěte se, že příkaz je k dispozici, jak je vysvětleno [dříve v tomto článku](#install-a-global-tool-in-a-custom-location).</span><span class="sxs-lookup"><span data-stu-id="1b15b-188">To invoke a global tool that is installed by using the `tool-path` option, make sure the command is available, as explained [earlier in this article](#install-a-global-tool-in-a-custom-location).</span></span>

### <a name="invoke-a-local-tool"></a><span data-ttu-id="1b15b-189">Vyvolání místního nástroje</span><span class="sxs-lookup"><span data-stu-id="1b15b-189">Invoke a local tool</span></span>

<span data-ttu-id="1b15b-190">Chcete-li vyvolat místní nástroj, `dotnet` musíte použít příkaz z instalačního adresáře.</span><span class="sxs-lookup"><span data-stu-id="1b15b-190">To invoke a local tool, you have to use the `dotnet` command from within the installation directory.</span></span> <span data-ttu-id="1b15b-191">Můžete použít dlouhý formulář`dotnet tool run <COMMAND_NAME>`( ) nebo`dotnet <COMMAND_NAME>`krátký formulář ( ), jak je znázorněno v následujících příkladech:</span><span class="sxs-lookup"><span data-stu-id="1b15b-191">You can use the long form (`dotnet tool run <COMMAND_NAME>`) or the short form (`dotnet <COMMAND_NAME>`), as shown in the following examples:</span></span>

```dotnetcli
dotnet tool run dotnetsay
dotnet dotnetsay
```

<span data-ttu-id="1b15b-192">Pokud je příkaz předponou , `dotnet-`můžete při vyvolání nástroje zahrnout nebo vynechat předponu.</span><span class="sxs-lookup"><span data-stu-id="1b15b-192">If the command is prefixed by `dotnet-`, you can include or omit the prefix when you invoke the tool.</span></span> <span data-ttu-id="1b15b-193">Pokud je `dotnet-doc`například příkaz , některý z následujících příkladů vyvolá místní nástroj:</span><span class="sxs-lookup"><span data-stu-id="1b15b-193">For example, if the command is `dotnet-doc`, any of the following examples invokes the local tool:</span></span>

```dotnetcli
dotnet tool run dotnet-doc
dotnet dotnet-doc
dotnet doc
```

## <a name="update-a-tool"></a><span data-ttu-id="1b15b-194">Aktualizace nástroje</span><span class="sxs-lookup"><span data-stu-id="1b15b-194">Update a tool</span></span>

<span data-ttu-id="1b15b-195">Aktualizace nástroje zahrnuje odinstalaci a přeinstalaci pomocí nejnovější stabilní verze.</span><span class="sxs-lookup"><span data-stu-id="1b15b-195">Updating a tool involves uninstalling and reinstalling it with the latest stable version.</span></span> <span data-ttu-id="1b15b-196">Chcete-li nástroj aktualizovat, použijte příkaz [aktualizace nástroje dotnet](dotnet-tool-update.md) se stejnou možností, kterou jste použili k instalaci nástroje:</span><span class="sxs-lookup"><span data-stu-id="1b15b-196">To update a tool, use the [dotnet tool update](dotnet-tool-update.md) command with the same option that you used to install the tool:</span></span>

```dotnetcli
dotnet tool update --global <packagename>
dotnet tool update --tool-path <packagename>
dotnet tool update <packagename>
```

<span data-ttu-id="1b15b-197">Pro místní nástroj sada SDK vyhledá první soubor manifestu, který obsahuje ID balíčku, vyhledáním v aktuálním adresáři a nadřazených adresářích.</span><span class="sxs-lookup"><span data-stu-id="1b15b-197">For a local tool, the SDK finds the first manifest file that contains the package ID by looking in the current directory and parent directories.</span></span> <span data-ttu-id="1b15b-198">Pokud není žádné takové ID balíčku v libovolném souboru manifestu, sada SDK přidá novou položku do nejbližšího souboru manifestu.</span><span class="sxs-lookup"><span data-stu-id="1b15b-198">If there is no such package ID in any manifest file, the SDK adds a new entry to the closest manifest file.</span></span>

## <a name="uninstall-a-tool"></a><span data-ttu-id="1b15b-199">Odinstalace nástroje</span><span class="sxs-lookup"><span data-stu-id="1b15b-199">Uninstall a tool</span></span>

<span data-ttu-id="1b15b-200">Odstraňte nástroj pomocí příkazu [odinstalovat nástroj dotnet](dotnet-tool-uninstall.md) se stejnou možností, kterou jste použili k instalaci nástroje:</span><span class="sxs-lookup"><span data-stu-id="1b15b-200">Remove a tool by using the [dotnet tool uninstall](dotnet-tool-uninstall.md) command with the same option that you used to install the tool:</span></span>

```dotnetcli
dotnet tool uninstall --global <packagename>
dotnet tool uninstall --tool-path<packagename>
dotnet tool uninstall <packagename>
```

<span data-ttu-id="1b15b-201">Pro místní nástroj sada SDK vyhledá první soubor manifestu, který obsahuje ID balíčku, vyhledáním v aktuálním adresáři a nadřazených adresářích.</span><span class="sxs-lookup"><span data-stu-id="1b15b-201">For a local tool, the SDK finds the first manifest file that contains the package ID by looking in the current directory and parent directories.</span></span>

## <a name="get-help-and-troubleshoot"></a><span data-ttu-id="1b15b-202">Získání nápovědy a řešení potíží</span><span class="sxs-lookup"><span data-stu-id="1b15b-202">Get help and troubleshoot</span></span>

<span data-ttu-id="1b15b-203">Chcete-li získat `dotnet tool` seznam dostupných příkazů, zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="1b15b-203">To get a list of available `dotnet tool` commands, enter the following command:</span></span>

```dotnetcli
dotnet tool --help
```

<span data-ttu-id="1b15b-204">Chcete-li získat pokyny k použití nástroje, zadejte jeden z následujících příkazů nebo se podívejte na web nástroje:</span><span class="sxs-lookup"><span data-stu-id="1b15b-204">To get tool usage instructions, enter one of the following commands or see the tool's website:</span></span>

```dotnetcli
<command> --help
dotnet <command> --help
```

<span data-ttu-id="1b15b-205">Pokud se nepodaří nainstalovat nebo spustit nástroj, [přečtěte si článek Poradce při potížích s používáním nástroje .NET Core](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="1b15b-205">If a tool fails to install or run, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1b15b-206">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b15b-206">See also</span></span>

- [<span data-ttu-id="1b15b-207">Kurz: Vytvoření nástroje .NET Core pomocí rozhraní CLI jádra .NET</span><span class="sxs-lookup"><span data-stu-id="1b15b-207">Tutorial: Create a .NET Core tool using the .NET Core CLI</span></span>](global-tools-how-to-create.md)
- [<span data-ttu-id="1b15b-208">Kurz: Instalace a použití globálního nástroje .NET Core pomocí rozhraní CLI jádra .NET</span><span class="sxs-lookup"><span data-stu-id="1b15b-208">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="1b15b-209">Kurz: Instalace a použití místního nástroje .NET Core pomocí rozhraní CLI jádra .NET</span><span class="sxs-lookup"><span data-stu-id="1b15b-209">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
