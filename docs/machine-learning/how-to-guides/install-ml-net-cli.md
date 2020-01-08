---
title: Jak nainstalovat nástroj rozhraní příkazového řádku ML.NET (CLI)
description: Naučte se instalovat, upgradovat, downgradovat a odinstalovat nástroj rozhraní příkazového řádku ML.NET (CLI).
ms.date: 12/18/2019
ms.author: nakersha
author: natke
ms.openlocfilehash: 07b6e924ed9c6b0c278a86539ebe7d750f9ced37
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636585"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a><span data-ttu-id="f4f11-103">Jak nainstalovat nástroj rozhraní příkazového řádku ML.NET (CLI)</span><span class="sxs-lookup"><span data-stu-id="f4f11-103">How to install the ML.NET Command-Line Interface (CLI) tool</span></span>

<span data-ttu-id="f4f11-104">Naučte se, jak nainstalovat rozhraní příkazového řádku (ML.NET) CLI do systému Windows, Mac nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="f4f11-104">Learn how to install the ML.NET CLI (command-line interface) on Windows, Mac, or Linux.</span></span>

<span data-ttu-id="f4f11-105">ML.NET CLI generuje kvalitní ML.NET modely a zdrojový kód s využitím automatizovaného strojového učení (AutoML) a datové sady školení.</span><span class="sxs-lookup"><span data-stu-id="f4f11-105">The ML.NET CLI generates good quality ML.NET models and source code using automated machine learning (AutoML) and a training dataset.</span></span>

> [!NOTE]
> <span data-ttu-id="f4f11-106">Toto téma odkazuje na ML.NET CLI a ML.NET AutoML, které jsou momentálně ve verzi Preview, a materiál může být změněn.</span><span class="sxs-lookup"><span data-stu-id="f4f11-106">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="f4f11-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f4f11-107">Pre-requisites</span></span>

- [<span data-ttu-id="f4f11-108">Sada .NET Core 2,2 SDK</span><span class="sxs-lookup"><span data-stu-id="f4f11-108">.NET Core 2.2 SDK</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)

- <span data-ttu-id="f4f11-109">Volitelné [Visual Studio 2017 nebo 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="f4f11-109">(Optional) [Visual Studio 2017 or 2019](https://visualstudio.microsoft.com/vs/)</span></span>

<span data-ttu-id="f4f11-110">Vygenerované C# projekty kódu se sadou Visual Studio můžete spustit stisknutím klávesy `F5` nebo pomocí `dotnet run` (.NET Core CLI).</span><span class="sxs-lookup"><span data-stu-id="f4f11-110">You can run the generated C# code projects with Visual Studio by pressing the `F5` key or with `dotnet run` (.NET Core CLI).</span></span>

<span data-ttu-id="f4f11-111">Poznámka: když po instalaci [sady .NET Core 2,2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) nefunguje příkaz `dotnet tool`, odhlaste se z Windows a znovu se přihlaste.</span><span class="sxs-lookup"><span data-stu-id="f4f11-111">Note: If after installing [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) the `dotnet tool` command is not working, sign out from Windows and sign in again.</span></span>

## <a name="install"></a><span data-ttu-id="f4f11-112">Instalace produktu</span><span class="sxs-lookup"><span data-stu-id="f4f11-112">Install</span></span>

<span data-ttu-id="f4f11-113">Rozhraní příkazového řádku ML.NET je nainstalováno jako jakýkoli jiný globální nástroj dotnet.</span><span class="sxs-lookup"><span data-stu-id="f4f11-113">The ML.NET CLI is installed like any other dotnet Global Tool.</span></span> <span data-ttu-id="f4f11-114">Použijete příkaz `dotnet tool install` .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="f4f11-114">You use the `dotnet tool install` .NET Core CLI command.</span></span>

<span data-ttu-id="f4f11-115">Následující příklad ukazuje, jak nainstalovat rozhraní příkazového řádku ML.NET ve výchozím umístění informačního kanálu NuGet:</span><span class="sxs-lookup"><span data-stu-id="f4f11-115">The following example shows how to install the ML.NET CLI in the default NuGet feed location:</span></span>

```dotnetcli
dotnet tool install -g mlnet
```

<span data-ttu-id="f4f11-116">Pokud nástroj není možné nainstalovat (to znamená, pokud není k dispozici ve výchozím kanálu NuGet), zobrazí se chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="f4f11-116">If the tool can't be installed (that is, if it is not available at the default NuGet feed), error messages are displayed.</span></span> <span data-ttu-id="f4f11-117">Ověřte, zda jsou kontrolovány informační kanály, které jste očekávali.</span><span class="sxs-lookup"><span data-stu-id="f4f11-117">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="f4f11-118">Pokud je instalace úspěšná, zobrazí se zpráva s příkazem použitým pro volání nástroje a nainstalované verze, podobně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f4f11-118">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

<span data-ttu-id="f4f11-119">Instalaci můžete ověřit tak, že zadáte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="f4f11-119">You can confirm the installation was successful by typing the following command:</span></span>

```console
mlnet
```

<span data-ttu-id="f4f11-120">Měli byste vidět nápovědu k dostupným příkazům pro nástroj mlnet, jako je například příkaz Auto-vlak.</span><span class="sxs-lookup"><span data-stu-id="f4f11-120">You should see the help for available commands for the mlnet tool such as the 'auto-train' command.</span></span>

## <a name="install-a-specific-release-version"></a><span data-ttu-id="f4f11-121">Instalace konkrétní vydané verze</span><span class="sxs-lookup"><span data-stu-id="f4f11-121">Install a specific release version</span></span>

<span data-ttu-id="f4f11-122">Pokud se pokoušíte nainstalovat předběžnou verzi nebo konkrétní verzi nástroje, můžete určit [rozhraní](../../standard/frameworks.md) pomocí následujícího formátu:</span><span class="sxs-lookup"><span data-stu-id="f4f11-122">If you're trying to install a pre-release version or a specific version of the tool, you can specify the [framework](../../standard/frameworks.md) using the following format:</span></span>

```dotnetcli
dotnet tool install -g mlnet --framework <FRAMEWORK>
```

<span data-ttu-id="f4f11-123">Můžete také zjistit, jestli je balíček správně nainstalovaný, zadáním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="f4f11-123">You can also check if the package is properly installed by typing the following command:</span></span>

```dotnetcli
dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a><span data-ttu-id="f4f11-124">Odinstalace balíčku CLI</span><span class="sxs-lookup"><span data-stu-id="f4f11-124">Uninstall the CLI package</span></span>

<span data-ttu-id="f4f11-125">Zadejte následující příkaz pro odinstalaci balíčku z místního počítače:</span><span class="sxs-lookup"><span data-stu-id="f4f11-125">Type the following command to uninstall the package from your local machine:</span></span>

```dotnetcli
dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a><span data-ttu-id="f4f11-126">Aktualizace balíčku CLI</span><span class="sxs-lookup"><span data-stu-id="f4f11-126">Update the CLI package</span></span>

<span data-ttu-id="f4f11-127">Zadáním následujícího příkazu aktualizujete balíček z místního počítače:</span><span class="sxs-lookup"><span data-stu-id="f4f11-127">Type the following command to update the package from your local machine:</span></span>

```dotnetcli
dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a><span data-ttu-id="f4f11-128">Nastavení návrhů CLI (automatické dokončování založené na kartě)</span><span class="sxs-lookup"><span data-stu-id="f4f11-128">Set up CLI suggestions (tab-based auto-completion)</span></span>

<span data-ttu-id="f4f11-129">Vzhledem k tomu, že rozhraní příkazového řádku ML.NET je založené na `System.CommandLine`, má vestavěnou podporu pro dokončování karet.</span><span class="sxs-lookup"><span data-stu-id="f4f11-129">Since the ML.NET CLI is based on `System.CommandLine`, it has built-in support for tab completion.</span></span>

<span data-ttu-id="f4f11-130">Příklad toho, jak funguje automatické dokončování karet, je znázorněno v následující animaci:</span><span class="sxs-lookup"><span data-stu-id="f4f11-130">An example of how tab auto completion works is shown in the following animation:</span></span>

![obrázek](./media/cli-tab-completion.gif)

<span data-ttu-id="f4f11-132">Automatické dokončování na kartě (návrhy parametrů) funguje v *prostředí Windows PowerShell* a *MacOS/Linux bash* , ale nebude fungovat na *Windows CMD*.</span><span class="sxs-lookup"><span data-stu-id="f4f11-132">'Tab-based auto-completion' (parameter suggestions) works on *Windows PowerShell* and *macOS/Linux bash* but it won't work on *Windows CMD*.</span></span>

<span data-ttu-id="f4f11-133">Aby ho bylo možné povolit, musí koncový uživatel v aktuální verzi Preview pro každé prostředí provést několik kroků, které jsou uvedené níže.</span><span class="sxs-lookup"><span data-stu-id="f4f11-133">To enable it, in the current preview version, the end user has to take a few steps once per shell, outlined below.</span></span> <span data-ttu-id="f4f11-134">Až to uděláte, dokončování budou fungovat pro všechny aplikace napsané pomocí `System.CommandLine`, jako je ML.NET CLI.</span><span class="sxs-lookup"><span data-stu-id="f4f11-134">Once this is done, completions will work for all apps written using `System.CommandLine` such as the ML.NET CLI.</span></span>

<span data-ttu-id="f4f11-135">V počítači, ve kterém chcete povolit dokončování, budete muset provést dvě věci.</span><span class="sxs-lookup"><span data-stu-id="f4f11-135">On the machine where you'd like to enable completion, you'll need to do two things.</span></span>

1. <span data-ttu-id="f4f11-136">Pomocí následujícího příkazu nainstalujte nástroj `dotnet-suggest` Global:</span><span class="sxs-lookup"><span data-stu-id="f4f11-136">Install the `dotnet-suggest` global tool by running the following command:</span></span>

    ```dotnetcli
    dotnet tool install dotnet-suggest -g
    ```

2. <span data-ttu-id="f4f11-137">Přidejte příslušný skript pro překrytí do profilu prostředí.</span><span class="sxs-lookup"><span data-stu-id="f4f11-137">Add the appropriate shim script to your shell profile.</span></span> <span data-ttu-id="f4f11-138">Možná budete muset vytvořit soubor profilu prostředí.</span><span class="sxs-lookup"><span data-stu-id="f4f11-138">You may have to create a shell profile file.</span></span> <span data-ttu-id="f4f11-139">Skript překrytí přepošle žádosti o dokončení z vašeho prostředí na nástroj `dotnet-suggest`, který se deleguje na příslušnou aplikaci založenou na `System.CommandLine`.</span><span class="sxs-lookup"><span data-stu-id="f4f11-139">The shim script will forward completion requests from your shell to the `dotnet-suggest` tool, which delegates to the appropriate `System.CommandLine`-based app.</span></span>

    - <span data-ttu-id="f4f11-140">V případě bash přidejte obsah pole [dotnet-navrhuje-Shim. bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) do `~/.bash_profile`.</span><span class="sxs-lookup"><span data-stu-id="f4f11-140">For bash, add the contents of [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) to `~/.bash_profile`.</span></span>

    - <span data-ttu-id="f4f11-141">V případě PowerShellu přidejte do svého profilu PowerShellu obsah [dotnet-Suggest-Shim. ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) .</span><span class="sxs-lookup"><span data-stu-id="f4f11-141">For PowerShell, add the contents of [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) to your PowerShell profile.</span></span> <span data-ttu-id="f4f11-142">Očekávanou cestu k profilu PowerShellu můžete najít spuštěním následujícího příkazu v konzole:</span><span class="sxs-lookup"><span data-stu-id="f4f11-142">You can find the expected path to your PowerShell profile by running the following command in your console:</span></span>

    ```console
    echo $profile
    ```

<span data-ttu-id="f4f11-143">(Pro další prostředí [vyhledejte](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) nebo otevřete [problém](https://github.com/dotnet/System.CommandLine/issues).)</span><span class="sxs-lookup"><span data-stu-id="f4f11-143">(For other shells, [look for](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) or open an [issue](https://github.com/dotnet/System.CommandLine/issues).)</span></span>

## <a name="installation-directory"></a><span data-ttu-id="f4f11-144">Instalační adresář</span><span class="sxs-lookup"><span data-stu-id="f4f11-144">Installation directory</span></span>

<span data-ttu-id="f4f11-145">ML.NET CLI se dá nainstalovat do výchozího adresáře nebo do konkrétního umístění.</span><span class="sxs-lookup"><span data-stu-id="f4f11-145">The ML.NET CLI can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="f4f11-146">Výchozí adresáře jsou:</span><span class="sxs-lookup"><span data-stu-id="f4f11-146">The default directories are:</span></span>

| <span data-ttu-id="f4f11-147">OS</span><span class="sxs-lookup"><span data-stu-id="f4f11-147">OS</span></span>          | <span data-ttu-id="f4f11-148">Cesta</span><span class="sxs-lookup"><span data-stu-id="f4f11-148">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="f4f11-149">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="f4f11-149">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="f4f11-150">Windows</span><span class="sxs-lookup"><span data-stu-id="f4f11-150">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="f4f11-151">Tato umístění jsou přidána do cesty uživatele při prvním spuštění sady SDK, takže je možné nainstalovanou sadu globálních nástrojů volat přímo.</span><span class="sxs-lookup"><span data-stu-id="f4f11-151">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="f4f11-152">Poznámka: globální nástroje jsou specifické pro uživatele, ne jako globální počítač.</span><span class="sxs-lookup"><span data-stu-id="f4f11-152">Note: the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="f4f11-153">To znamená, že nemůžete nainstalovat globální nástroj, který je k dispozici pro všechny uživatele počítače.</span><span class="sxs-lookup"><span data-stu-id="f4f11-153">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="f4f11-154">Nástroj je k dispozici pouze pro každý profil uživatele, ve kterém byl nástroj nainstalován.</span><span class="sxs-lookup"><span data-stu-id="f4f11-154">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="f4f11-155">Globální nástroje je také možné nainstalovat do konkrétního adresáře.</span><span class="sxs-lookup"><span data-stu-id="f4f11-155">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="f4f11-156">Při instalaci do konkrétního adresáře musí uživatel ověřit, zda je příkaz k dispozici, zahrnutím tohoto adresáře do cesty, voláním příkazu se zadaným adresářem nebo voláním nástroje ze zadaného adresáře.</span><span class="sxs-lookup"><span data-stu-id="f4f11-156">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="f4f11-157">V takovém případě .NET Core CLI nepřidá toto umístění automaticky do proměnné prostředí PATH.</span><span class="sxs-lookup"><span data-stu-id="f4f11-157">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="f4f11-158">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f4f11-158">See also</span></span>

- [<span data-ttu-id="f4f11-159">ML.NET CLI – přehled</span><span class="sxs-lookup"><span data-stu-id="f4f11-159">ML.NET CLI overview</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="f4f11-160">Kurz: analýza mínění pomocí rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="f4f11-160">Tutorial: Analyze sentiment with the ML.NET CLI</span></span>](../tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="f4f11-161">Referenční příručka k příkazu ML.NET CLI pro automatické učení</span><span class="sxs-lookup"><span data-stu-id="f4f11-161">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="f4f11-162">Telemetrie v ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="f4f11-162">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
