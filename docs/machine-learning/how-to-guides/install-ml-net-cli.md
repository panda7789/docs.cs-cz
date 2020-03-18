---
title: Jak nainstalovat nástroj ML.NET rozhraní příkazového řádku (CLI)
description: Přečtěte si, jak nainstalovat, upgradovat, downgrade a odinstalovat nástroj cli rozhraní příkazového řádku (ML.NET.Learn, jak nainstalovat, upgradovat, downgrade a odinstalovat nástroj ML.NET rozhraní příkazového řádku (CLI).
ms.date: 12/18/2019
ms.custom: mlnet-tooling
ms.openlocfilehash: 9f678c7117d32bf817139951db7eef2c3d0f5eb2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78848636"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a><span data-ttu-id="b71e1-103">Jak nainstalovat nástroj ML.NET rozhraní příkazového řádku (CLI)</span><span class="sxs-lookup"><span data-stu-id="b71e1-103">How to install the ML.NET Command-Line Interface (CLI) tool</span></span>

<span data-ttu-id="b71e1-104">Přečtěte si, jak nainstalovat ML.NET rozhraní příkazového řádku (rozhraní příkazového řádku) do Windows, Macu nebo Linuxu.</span><span class="sxs-lookup"><span data-stu-id="b71e1-104">Learn how to install the ML.NET CLI (command-line interface) on Windows, Mac, or Linux.</span></span>

<span data-ttu-id="b71e1-105">ML.NET CLI generuje kvalitní ML.NET modely a zdrojový kód pomocí automatizovaného strojového učení (AutoML) a trénovací datové sady.</span><span class="sxs-lookup"><span data-stu-id="b71e1-105">The ML.NET CLI generates good quality ML.NET models and source code using automated machine learning (AutoML) and a training dataset.</span></span>

> [!NOTE]
> <span data-ttu-id="b71e1-106">Toto téma odkazuje na ML.NET cli a ML.NET AutoML, které jsou aktuálně ve verzi Preview, a materiál může být může být možné změnit.</span><span class="sxs-lookup"><span data-stu-id="b71e1-106">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="b71e1-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b71e1-107">Pre-requisites</span></span>

- [<span data-ttu-id="b71e1-108">.NET Jádro 2.2 SDK</span><span class="sxs-lookup"><span data-stu-id="b71e1-108">.NET Core 2.2 SDK</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)

- <span data-ttu-id="b71e1-109">(Nepovinné) [Visual Studio 2017 nebo 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="b71e1-109">(Optional) [Visual Studio 2017 or 2019](https://visualstudio.microsoft.com/vs/)</span></span>

<span data-ttu-id="b71e1-110">Vygenerované projekty kódu Jazyka C# můžete `F5` spustit pomocí `dotnet run` sady Visual Studio stisknutím klávesy nebo pomocí (.NET Core CLI).</span><span class="sxs-lookup"><span data-stu-id="b71e1-110">You can run the generated C# code projects with Visual Studio by pressing the `F5` key or with `dotnet run` (.NET Core CLI).</span></span>

<span data-ttu-id="b71e1-111">Poznámka: Pokud po instalaci [sady .NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) `dotnet tool` příkaz nefunguje, odhlaste se ze systému Windows a znovu se přihlaste.</span><span class="sxs-lookup"><span data-stu-id="b71e1-111">Note: If after installing [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) the `dotnet tool` command is not working, sign out from Windows and sign in again.</span></span>

## <a name="install"></a><span data-ttu-id="b71e1-112">Instalace</span><span class="sxs-lookup"><span data-stu-id="b71e1-112">Install</span></span>

<span data-ttu-id="b71e1-113">ML.NET CLI je nainstalován jako každý jiný dotnet Global Tool.</span><span class="sxs-lookup"><span data-stu-id="b71e1-113">The ML.NET CLI is installed like any other dotnet Global Tool.</span></span> <span data-ttu-id="b71e1-114">Použijete `dotnet tool install` příkaz příkazu PŘÍKAZ K PŘÍKAZU .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="b71e1-114">You use the `dotnet tool install` .NET Core CLI command.</span></span>

<span data-ttu-id="b71e1-115">Následující příklad ukazuje, jak nainstalovat ML.NET příkazového příkazového odpočinu do výchozího umístění informačního kanálu NuGet:</span><span class="sxs-lookup"><span data-stu-id="b71e1-115">The following example shows how to install the ML.NET CLI in the default NuGet feed location:</span></span>

```dotnetcli
dotnet tool install -g mlnet
```

<span data-ttu-id="b71e1-116">Pokud nástroj nelze nainstalovat (to znamená, pokud není k dispozici ve výchozím kanálu NuGet), zobrazí se chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="b71e1-116">If the tool can't be installed (that is, if it is not available at the default NuGet feed), error messages are displayed.</span></span> <span data-ttu-id="b71e1-117">Zkontrolujte, zda jsou kontrolovány zdroje, které jste očekávali.</span><span class="sxs-lookup"><span data-stu-id="b71e1-117">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="b71e1-118">Pokud je instalace úspěšná, zobrazí se zpráva s příkazem používaným k volání nástroje a nainstalovanou verzí, podobně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="b71e1-118">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

<span data-ttu-id="b71e1-119">Můžete potvrdit, že instalace byla úspěšná zadáním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="b71e1-119">You can confirm the installation was successful by typing the following command:</span></span>

```console
mlnet
```

<span data-ttu-id="b71e1-120">Měli byste vidět nápovědu pro dostupné příkazy pro nástroj mlnet, jako je příkaz "auto-train".</span><span class="sxs-lookup"><span data-stu-id="b71e1-120">You should see the help for available commands for the mlnet tool such as the 'auto-train' command.</span></span>

## <a name="install-a-specific-release-version"></a><span data-ttu-id="b71e1-121">Instalace konkrétní verze</span><span class="sxs-lookup"><span data-stu-id="b71e1-121">Install a specific release version</span></span>

<span data-ttu-id="b71e1-122">Pokud se pokoušíte nainstalovat předběžnou verzi nebo určitou verzi nástroje, můžete určit [architekturu](../../standard/frameworks.md) v následujícím formátu:</span><span class="sxs-lookup"><span data-stu-id="b71e1-122">If you're trying to install a pre-release version or a specific version of the tool, you can specify the [framework](../../standard/frameworks.md) using the following format:</span></span>

```dotnetcli
dotnet tool install -g mlnet --framework <FRAMEWORK>
```

<span data-ttu-id="b71e1-123">Můžete také zkontrolovat, zda je balíček správně nainstalován zadáním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="b71e1-123">You can also check if the package is properly installed by typing the following command:</span></span>

```dotnetcli
dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a><span data-ttu-id="b71e1-124">Odinstalace balíčku CLI</span><span class="sxs-lookup"><span data-stu-id="b71e1-124">Uninstall the CLI package</span></span>

<span data-ttu-id="b71e1-125">Chcete-li odinstalovat balíček z místního počítače, zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="b71e1-125">Type the following command to uninstall the package from your local machine:</span></span>

```dotnetcli
dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a><span data-ttu-id="b71e1-126">Aktualizace balíčku CLI</span><span class="sxs-lookup"><span data-stu-id="b71e1-126">Update the CLI package</span></span>

<span data-ttu-id="b71e1-127">Zadejte následující příkaz pro aktualizaci balíčku z místního počítače:</span><span class="sxs-lookup"><span data-stu-id="b71e1-127">Type the following command to update the package from your local machine:</span></span>

```dotnetcli
dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a><span data-ttu-id="b71e1-128">Nastavení návrhů zapisování zapisování (automatické dokončování na tabulátorech)</span><span class="sxs-lookup"><span data-stu-id="b71e1-128">Set up CLI suggestions (tab-based auto-completion)</span></span>

<span data-ttu-id="b71e1-129">Vzhledem k tomu, `System.CommandLine`že ML.NET cli je založena na , má vestavěnou podporu pro dokončení karty.</span><span class="sxs-lookup"><span data-stu-id="b71e1-129">Since the ML.NET CLI is based on `System.CommandLine`, it has built-in support for tab completion.</span></span>

<span data-ttu-id="b71e1-130">Příklad fungování automatického dokončování tabulátoru je uveden v následující animaci:</span><span class="sxs-lookup"><span data-stu-id="b71e1-130">An example of how tab auto completion works is shown in the following animation:</span></span>

![image](./media/cli-tab-completion.gif)

<span data-ttu-id="b71e1-132">'Tab-based auto-completion' (parametr suggestions) práce na *Windows PowerShell* a *macOS/Linux bash,* ale to nebude fungovat na *Windows CMD*.</span><span class="sxs-lookup"><span data-stu-id="b71e1-132">'Tab-based auto-completion' (parameter suggestions) works on *Windows PowerShell* and *macOS/Linux bash* but it won't work on *Windows CMD*.</span></span>

<span data-ttu-id="b71e1-133">Chcete-li jej povolit, musí koncový uživatel v aktuální verzi náhledu provést několik kroků jednou za prostředí, které je uvedeno níže.</span><span class="sxs-lookup"><span data-stu-id="b71e1-133">To enable it, in the current preview version, the end user has to take a few steps once per shell, outlined below.</span></span> <span data-ttu-id="b71e1-134">Jakmile to provedete, dokončení bude fungovat `System.CommandLine` pro všechny aplikace napsané pomocí například ML.NET CLI.</span><span class="sxs-lookup"><span data-stu-id="b71e1-134">Once this is done, completions will work for all apps written using `System.CommandLine` such as the ML.NET CLI.</span></span>

<span data-ttu-id="b71e1-135">Na počítači, kde chcete povolit dokončení, budete muset udělat dvě věci.</span><span class="sxs-lookup"><span data-stu-id="b71e1-135">On the machine where you'd like to enable completion, you'll need to do two things.</span></span>

1. <span data-ttu-id="b71e1-136">Nainstalujte `dotnet-suggest` globální nástroj spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="b71e1-136">Install the `dotnet-suggest` global tool by running the following command:</span></span>

    ```dotnetcli
    dotnet tool install dotnet-suggest -g
    ```

2. <span data-ttu-id="b71e1-137">Přidejte do profilu prostředí příslušný skript překrytí.</span><span class="sxs-lookup"><span data-stu-id="b71e1-137">Add the appropriate shim script to your shell profile.</span></span> <span data-ttu-id="b71e1-138">Pravděpodobně bude pravděpodobně muset vytvořit soubor profilu prostředí.</span><span class="sxs-lookup"><span data-stu-id="b71e1-138">You may have to create a shell profile file.</span></span> <span data-ttu-id="b71e1-139">Překrytí skript bude předávat požadavky na `dotnet-suggest` dokončení z prostředí do `System.CommandLine`nástroje, který deleguje na příslušnou aplikaci založenou na.</span><span class="sxs-lookup"><span data-stu-id="b71e1-139">The shim script will forward completion requests from your shell to the `dotnet-suggest` tool, which delegates to the appropriate `System.CommandLine`-based app.</span></span>

    - <span data-ttu-id="b71e1-140">Pro bash, přidejte obsah [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) na `~/.bash_profile`.</span><span class="sxs-lookup"><span data-stu-id="b71e1-140">For bash, add the contents of [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) to `~/.bash_profile`.</span></span>

    - <span data-ttu-id="b71e1-141">V prostředí PowerShell přidejte do profilu Prostředí PowerShell obsah [dotnet-suggest-shim.ps1.](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1)</span><span class="sxs-lookup"><span data-stu-id="b71e1-141">For PowerShell, add the contents of [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) to your PowerShell profile.</span></span> <span data-ttu-id="b71e1-142">Očekávanou cestu k profilu prostředí PowerShell najdete spuštěním následujícího příkazu v konzole:</span><span class="sxs-lookup"><span data-stu-id="b71e1-142">You can find the expected path to your PowerShell profile by running the following command in your console:</span></span>

    ```console
    echo $profile
    ```

<span data-ttu-id="b71e1-143">(U ostatních granátů [vyhledejte](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) nebo otevřete [problém](https://github.com/dotnet/System.CommandLine/issues).)</span><span class="sxs-lookup"><span data-stu-id="b71e1-143">(For other shells, [look for](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) or open an [issue](https://github.com/dotnet/System.CommandLine/issues).)</span></span>

## <a name="installation-directory"></a><span data-ttu-id="b71e1-144">Instalační adresář</span><span class="sxs-lookup"><span data-stu-id="b71e1-144">Installation directory</span></span>

<span data-ttu-id="b71e1-145">Rozhraní ML.NET cli lze nainstalovat do výchozího adresáře nebo do určitého umístění.</span><span class="sxs-lookup"><span data-stu-id="b71e1-145">The ML.NET CLI can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="b71e1-146">Výchozí adresáře jsou:</span><span class="sxs-lookup"><span data-stu-id="b71e1-146">The default directories are:</span></span>

| <span data-ttu-id="b71e1-147">Operační systém</span><span class="sxs-lookup"><span data-stu-id="b71e1-147">OS</span></span>          | <span data-ttu-id="b71e1-148">Cesta</span><span class="sxs-lookup"><span data-stu-id="b71e1-148">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="b71e1-149">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="b71e1-149">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="b71e1-150">Windows</span><span class="sxs-lookup"><span data-stu-id="b71e1-150">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="b71e1-151">Tato umístění jsou přidány do cesty uživatele při prvním spuštění sady SDK, takže globální nástroje nainstalované tam lze volat přímo.</span><span class="sxs-lookup"><span data-stu-id="b71e1-151">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="b71e1-152">Poznámka: Globální nástroje jsou specifické pro uživatele, nikoli globální počítače.</span><span class="sxs-lookup"><span data-stu-id="b71e1-152">Note: the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="b71e1-153">Být specifické pro uživatele znamená, že nelze nainstalovat globální nástroj, který je k dispozici všem uživatelům počítače.</span><span class="sxs-lookup"><span data-stu-id="b71e1-153">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="b71e1-154">Nástroj je k dispozici pouze pro každý profil uživatele, ve kterém byl nástroj nainstalován.</span><span class="sxs-lookup"><span data-stu-id="b71e1-154">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="b71e1-155">Globální nástroje lze také nainstalovat do určitého adresáře.</span><span class="sxs-lookup"><span data-stu-id="b71e1-155">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="b71e1-156">Při instalaci v určitém adresáři musí uživatel zajistit, aby byl příkaz k dispozici, a to zahrnutím tohoto adresáře do cesty, voláním příkazu se zadaným adresářem nebo voláním nástroje ze zadaného adresáře.</span><span class="sxs-lookup"><span data-stu-id="b71e1-156">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="b71e1-157">V tomto případě rozhraní CLI jádra .NET nepřidá toto umístění automaticky do proměnné prostředí PATH.</span><span class="sxs-lookup"><span data-stu-id="b71e1-157">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="b71e1-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="b71e1-158">See also</span></span>

- [<span data-ttu-id="b71e1-159">přehled ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="b71e1-159">ML.NET CLI overview</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="b71e1-160">Kurz: Analýza mínění pomocí ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="b71e1-160">Tutorial: Analyze sentiment with the ML.NET CLI</span></span>](../tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="b71e1-161">ML.NET referenční příručka příkazu automatického vlakového ústrojí ML.NET</span><span class="sxs-lookup"><span data-stu-id="b71e1-161">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="b71e1-162">Telemetrie v ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="b71e1-162">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
