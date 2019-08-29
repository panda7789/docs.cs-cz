---
title: Jak nainstalovat nástroj rozhraní příkazového řádku ML.NET (CLI)
description: Přehled a instalace nástroje rozhraní příkazového řádku ML.NET (CLI).
ms.date: 04/16/2019
ms.custom: ''
ms.openlocfilehash: 8b6de466a6cf72b44a16c80fc024671bc4e975e8
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106897"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a><span data-ttu-id="0a9b9-103">Jak nainstalovat nástroj rozhraní příkazového řádku ML.NET (CLI)</span><span class="sxs-lookup"><span data-stu-id="0a9b9-103">How to install the ML.NET Command-Line Interface (CLI) tool</span></span>

<span data-ttu-id="0a9b9-104">ML.NET CLI (rozhraní příkazového řádku) je nástroj, který můžete spustit na jakémkoli příkazovém řádku (Windows, Mac nebo Linux) pro vytváření kvalitních ML.NET modelů a zdrojového kódu na základě školení datových sad, které poskytnete.</span><span class="sxs-lookup"><span data-stu-id="0a9b9-104">The ML.NET CLI (command-line interface) is a tool you can run on any command-prompt (Windows, Mac, or Linux) for generating good quality ML.NET models and source code based on training datasets you provide.</span></span>

> [!NOTE]
> <span data-ttu-id="0a9b9-105">Toto téma odkazuje na ML.NET CLI a ML.NET AutoML, které jsou momentálně ve verzi Preview, a materiál může být změněn.</span><span class="sxs-lookup"><span data-stu-id="0a9b9-105">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="0a9b9-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0a9b9-106">Pre-requisites</span></span>

- [<span data-ttu-id="0a9b9-107">Sada .NET Core 2,2 SDK</span><span class="sxs-lookup"><span data-stu-id="0a9b9-107">.NET Core 2.2 SDK</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)

- <span data-ttu-id="0a9b9-108">Volitelné [Visual Studio 2017 nebo 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="0a9b9-108">(Optional) [Visual Studio 2017 or 2019](https://visualstudio.microsoft.com/vs/)</span></span>

<span data-ttu-id="0a9b9-109">Můžete buď spustit vygenerované C# projekty kódu v aplikaci Visual Studio F5 nebo with `dotnet run` (.NET Core CLI).</span><span class="sxs-lookup"><span data-stu-id="0a9b9-109">You can either run the generated C# code projects with Visual Studio F5 or with `dotnet run` (.NET Core CLI).</span></span>

<span data-ttu-id="0a9b9-110">Poznámka: Pokud po instalaci [sady .NET Core 2,2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) `dotnet tool` nefunguje příkaz, odhlaste se z Windows a znovu se přihlaste.</span><span class="sxs-lookup"><span data-stu-id="0a9b9-110">Note: If after installing [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) the `dotnet tool` command is not working, sign out from Windows and sign in again.</span></span>

## <a name="install"></a><span data-ttu-id="0a9b9-111">Instalace</span><span class="sxs-lookup"><span data-stu-id="0a9b9-111">Install</span></span>

<span data-ttu-id="0a9b9-112">Rozhraní příkazového řádku ML.NET je nainstalováno jako jakýkoli jiný globální nástroj dotnet.</span><span class="sxs-lookup"><span data-stu-id="0a9b9-112">The ML.NET CLI is installed like any other dotnet Global Tool.</span></span> <span data-ttu-id="0a9b9-113">Použijete `dotnet tool install` příkaz .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="0a9b9-113">You use the `dotnet tool install` .NET Core CLI command.</span></span> 

<span data-ttu-id="0a9b9-114">Následující příklad ukazuje, jak nainstalovat rozhraní příkazového řádku ML.NET ve výchozím umístění informačního kanálu NuGet:</span><span class="sxs-lookup"><span data-stu-id="0a9b9-114">The following example shows how to install the ML.NET CLI in the default NuGet feed location:</span></span>

```console
dotnet tool install -g mlnet
```

<span data-ttu-id="0a9b9-115">Pokud nástroj není možné nainstalovat (to znamená, pokud není k dispozici ve výchozím kanálu NuGet), zobrazí se chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="0a9b9-115">If the tool can't be installed (that is, if it is not available at the default NuGet feed), error messages are displayed.</span></span> <span data-ttu-id="0a9b9-116">Ověřte, zda jsou kontrolovány informační kanály, které jste očekávali.</span><span class="sxs-lookup"><span data-stu-id="0a9b9-116">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="0a9b9-117">Pokud je instalace úspěšná, zobrazí se zpráva s příkazem použitým pro volání nástroje a nainstalované verze, podobně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="0a9b9-117">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

<span data-ttu-id="0a9b9-118">Instalaci můžete ověřit tak, že zadáte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="0a9b9-118">You can confirm the installation was successful by typing the following command:</span></span>

```console
mlnet
```

<span data-ttu-id="0a9b9-119">Měli byste vidět nápovědu k dostupným příkazům pro nástroj mlnet, jako je například příkaz Auto-vlak.</span><span class="sxs-lookup"><span data-stu-id="0a9b9-119">You should see the help for available commands for the mlnet tool such as the 'auto-train' command.</span></span>

## <a name="install-a-specific-release-version"></a><span data-ttu-id="0a9b9-120">Instalace konkrétní vydané verze</span><span class="sxs-lookup"><span data-stu-id="0a9b9-120">Install a specific release version</span></span>

<span data-ttu-id="0a9b9-121">Pokud se pokoušíte nainstalovat předběžnou verzi nebo konkrétní verzi nástroje, můžete určit [rozhraní](../../standard/frameworks.md) pomocí následujícího formátu:</span><span class="sxs-lookup"><span data-stu-id="0a9b9-121">If you're trying to install a pre-release version or a specific version of the tool, you can specify the [framework](../../standard/frameworks.md) using the following format:</span></span>

```console
dotnet tool install -g mlnet --framework <FRAMEWORK>
```

<span data-ttu-id="0a9b9-122">Můžete také zjistit, jestli je balíček správně nainstalovaný, zadáním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="0a9b9-122">You can also check if the package is properly installed by typing the following command:</span></span>

```console
dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a><span data-ttu-id="0a9b9-123">Odinstalace balíčku CLI</span><span class="sxs-lookup"><span data-stu-id="0a9b9-123">Uninstall the CLI package</span></span>

<span data-ttu-id="0a9b9-124">Zadejte následující příkaz pro odinstalaci balíčku z místního počítače:</span><span class="sxs-lookup"><span data-stu-id="0a9b9-124">Type the following command to uninstall the package from your local machine:</span></span>

```console
dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a><span data-ttu-id="0a9b9-125">Aktualizace balíčku CLI</span><span class="sxs-lookup"><span data-stu-id="0a9b9-125">Update the CLI package</span></span>

<span data-ttu-id="0a9b9-126">Zadáním následujícího příkazu aktualizujete balíček z místního počítače:</span><span class="sxs-lookup"><span data-stu-id="0a9b9-126">Type the following command to update the package from your local machine:</span></span>

```console
dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a><span data-ttu-id="0a9b9-127">Nastavení návrhů CLI (automatické dokončování založené na kartě)</span><span class="sxs-lookup"><span data-stu-id="0a9b9-127">Set up CLI suggestions (tab-based auto-completion)</span></span>

<span data-ttu-id="0a9b9-128">Vzhledem k tomu, že rozhraní příkazového řádku ml.NET je založené na `System.CommandLine`, má vestavěnou podporu pro dokončování karet.</span><span class="sxs-lookup"><span data-stu-id="0a9b9-128">Since the ML.NET CLI is based on `System.CommandLine`, it has built-in support for tab completion.</span></span>

<span data-ttu-id="0a9b9-129">Příklad toho, jak funguje automatické dokončování karet, je znázorněno v následující animaci:</span><span class="sxs-lookup"><span data-stu-id="0a9b9-129">An example of how tab auto completion works is shown in the following animation:</span></span>

![obrázek](./media/cli-tab-completion.gif)

<span data-ttu-id="0a9b9-131">Automatické dokončování na kartě (návrhy parametrů) funguje v *prostředí Windows PowerShell* a *MacOS/Linux bash* , ale nebude fungovat na *Windows CMD*.</span><span class="sxs-lookup"><span data-stu-id="0a9b9-131">'Tab-based auto-completion' (parameter suggestions) works on *Windows PowerShell* and *macOS/Linux bash* but it won't work on *Windows CMD*.</span></span>

<span data-ttu-id="0a9b9-132">Aby ho bylo možné povolit, musí koncový uživatel v aktuální verzi Preview pro každé prostředí provést několik kroků, které jsou uvedené níže.</span><span class="sxs-lookup"><span data-stu-id="0a9b9-132">To enable it, in the current preview version, the end user has to take a few steps once per shell, outlined below.</span></span> <span data-ttu-id="0a9b9-133">Až to uděláte, dokončování budou fungovat pro všechny aplikace napsané pomocí `System.CommandLine` , jako je ml.NET CLI.</span><span class="sxs-lookup"><span data-stu-id="0a9b9-133">Once this is done, completions will work for all apps written using `System.CommandLine` such as the ML.NET CLI.</span></span>

<span data-ttu-id="0a9b9-134">V počítači, ve kterém chcete povolit dokončování, budete muset provést dvě věci.</span><span class="sxs-lookup"><span data-stu-id="0a9b9-134">On the machine where you'd like to enable completion, you'll need to do two things.</span></span>

1. <span data-ttu-id="0a9b9-135">`dotnet-suggest` Globální nástroj nainstalujete spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="0a9b9-135">Install the `dotnet-suggest` global tool by running the following command:</span></span>

    ```console
    dotnet tool install dotnet-suggest -g
    ```

2. <span data-ttu-id="0a9b9-136">Přidejte příslušný skript pro překrytí do profilu prostředí.</span><span class="sxs-lookup"><span data-stu-id="0a9b9-136">Add the appropriate shim script to your shell profile.</span></span> <span data-ttu-id="0a9b9-137">Možná budete muset vytvořit soubor profilu prostředí.</span><span class="sxs-lookup"><span data-stu-id="0a9b9-137">You may have to create a shell profile file.</span></span> <span data-ttu-id="0a9b9-138">Skript překrytí přepošle žádosti o dokončení z vašeho `dotnet-suggest` prostředí do nástroje, který deleguje na `System.CommandLine`příslušnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0a9b9-138">The shim script will forward completion requests from your shell to the `dotnet-suggest` tool, which delegates to the appropriate `System.CommandLine`-based app.</span></span>

    - <span data-ttu-id="0a9b9-139">Pro bash přidejte obsah pole [dotnet-navrhuje-Shim. bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) `~/.bash_profile`.</span><span class="sxs-lookup"><span data-stu-id="0a9b9-139">For bash, add the contents of [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) to `~/.bash_profile`.</span></span>

    - <span data-ttu-id="0a9b9-140">V případě PowerShellu přidejte do svého profilu PowerShellu obsah [dotnet-Suggest-Shim. ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) .</span><span class="sxs-lookup"><span data-stu-id="0a9b9-140">For PowerShell, add the contents of [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) to your PowerShell profile.</span></span> <span data-ttu-id="0a9b9-141">Očekávanou cestu k profilu PowerShellu můžete najít spuštěním následujícího příkazu v konzole:</span><span class="sxs-lookup"><span data-stu-id="0a9b9-141">You can find the expected path to your PowerShell profile by running the following command in your console:</span></span>

    ```console
    echo $profile
    ``` 

<span data-ttu-id="0a9b9-142">(Pro další prostředí [vyhledejte](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) nebo otevřete [problém](https://github.com/dotnet/System.CommandLine/issues).)</span><span class="sxs-lookup"><span data-stu-id="0a9b9-142">(For other shells, [look for](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) or open an [issue](https://github.com/dotnet/System.CommandLine/issues).)</span></span>

## <a name="installation-directory"></a><span data-ttu-id="0a9b9-143">Instalační adresář</span><span class="sxs-lookup"><span data-stu-id="0a9b9-143">Installation directory</span></span>

<span data-ttu-id="0a9b9-144">ML.NET CLI se dá nainstalovat do výchozího adresáře nebo do konkrétního umístění.</span><span class="sxs-lookup"><span data-stu-id="0a9b9-144">The ML.NET CLI can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="0a9b9-145">Výchozí adresáře jsou:</span><span class="sxs-lookup"><span data-stu-id="0a9b9-145">The default directories are:</span></span>

| <span data-ttu-id="0a9b9-146">OS</span><span class="sxs-lookup"><span data-stu-id="0a9b9-146">OS</span></span>          | <span data-ttu-id="0a9b9-147">Cesta</span><span class="sxs-lookup"><span data-stu-id="0a9b9-147">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="0a9b9-148">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="0a9b9-148">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="0a9b9-149">Windows</span><span class="sxs-lookup"><span data-stu-id="0a9b9-149">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="0a9b9-150">Tato umístění jsou přidána do cesty uživatele při prvním spuštění sady SDK, takže je možné nainstalovanou sadu globálních nástrojů volat přímo.</span><span class="sxs-lookup"><span data-stu-id="0a9b9-150">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="0a9b9-151">Poznámka: globální nástroje jsou specifické pro uživatele, ne jako globální počítač.</span><span class="sxs-lookup"><span data-stu-id="0a9b9-151">Note: the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="0a9b9-152">To znamená, že nemůžete nainstalovat globální nástroj, který je k dispozici pro všechny uživatele počítače.</span><span class="sxs-lookup"><span data-stu-id="0a9b9-152">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="0a9b9-153">Nástroj je k dispozici pouze pro každý profil uživatele, ve kterém byl nástroj nainstalován.</span><span class="sxs-lookup"><span data-stu-id="0a9b9-153">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="0a9b9-154">Globální nástroje je také možné nainstalovat do konkrétního adresáře.</span><span class="sxs-lookup"><span data-stu-id="0a9b9-154">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="0a9b9-155">Při instalaci do konkrétního adresáře musí uživatel ověřit, zda je příkaz k dispozici, zahrnutím tohoto adresáře do cesty, voláním příkazu se zadaným adresářem nebo voláním nástroje ze zadaného adresáře.</span><span class="sxs-lookup"><span data-stu-id="0a9b9-155">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="0a9b9-156">V takovém případě .NET Core CLI nepřidá toto umístění automaticky do proměnné prostředí PATH.</span><span class="sxs-lookup"><span data-stu-id="0a9b9-156">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="0a9b9-157">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0a9b9-157">See also</span></span>

- [<span data-ttu-id="0a9b9-158">Kurz k Začínáme pomocí nástroje CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="0a9b9-158">Tutorial on 'Getting Started with ML.NET CLI tool'</span></span>](../tutorials/mlnet-cli.md)
- [<span data-ttu-id="0a9b9-159">Automatické učení modelů pomocí nástroje CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="0a9b9-159">How to automatically train models with the ML.NET CLI tool</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="0a9b9-160">Referenční příručka k příkazu ML.NET CLI pro automatické učení</span><span class="sxs-lookup"><span data-stu-id="0a9b9-160">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md) 
- [<span data-ttu-id="0a9b9-161">Telemetrie v ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="0a9b9-161">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
