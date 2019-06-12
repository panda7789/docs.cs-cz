---
title: Postup instalace nástroje ML.NET rozhraní příkazového řádku (CLI)
description: Přehled a instalace nástroje ML.NET rozhraní příkazového řádku (CLI).
ms.date: 04/16/2019
ms.custom: ''
ms.openlocfilehash: 4888acd10570318ef53dc4b1a5a4ff5d8dc0c99b
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2019
ms.locfileid: "66832923"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a><span data-ttu-id="2dc65-103">Postup instalace nástroje ML.NET rozhraní příkazového řádku (CLI)</span><span class="sxs-lookup"><span data-stu-id="2dc65-103">How to install the ML.NET Command-Line Interface (CLI) tool</span></span>

<span data-ttu-id="2dc65-104">ML.NET CLI (rozhraní příkazového řádku) je nástroj, který můžete spustit na libovolné příkazového řádku (Windows, Mac nebo Linux) pro vytváření kvalitní ML.NET modely a zdrojový kód podle cvičných datových sad, které zadáte.</span><span class="sxs-lookup"><span data-stu-id="2dc65-104">The ML.NET CLI (command-line interface) is a tool you can run on any command-prompt (Windows, Mac, or Linux) for generating good quality ML.NET models and source code based on training datasets you provide.</span></span>

> [!NOTE]
> <span data-ttu-id="2dc65-105">Toto téma odkazuje na ML.NET rozhraní příkazového řádku a ML.NET AutoML, které jsou aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit.</span><span class="sxs-lookup"><span data-stu-id="2dc65-105">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="2dc65-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2dc65-106">Pre-requisites</span></span>

- [<span data-ttu-id="2dc65-107">.NET Core 2.2 SDK</span><span class="sxs-lookup"><span data-stu-id="2dc65-107">.NET Core 2.2 SDK</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)

- <span data-ttu-id="2dc65-108">(Volitelné) [Visual Studio 2017 nebo 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="2dc65-108">(Optional) [Visual Studio 2017 or 2019](https://visualstudio.microsoft.com/vs/)</span></span>

<span data-ttu-id="2dc65-109">Můžete spustit buď generované C# projekty s Visual Studio F5 nebo pomocí kódu `dotnet run` (.NET Core CLI).</span><span class="sxs-lookup"><span data-stu-id="2dc65-109">You can either run the generated C# code projects with Visual Studio F5 or with `dotnet run` (.NET Core CLI).</span></span>

<span data-ttu-id="2dc65-110">Poznámka: Pokud po instalaci [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) `dotnet tool` příkaz nefunguje, odhlásit z Windows a znovu se přihlaste.</span><span class="sxs-lookup"><span data-stu-id="2dc65-110">Note: If after installing [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) the `dotnet tool` command is not working, sign out from Windows and sign in again.</span></span>

## <a name="install"></a><span data-ttu-id="2dc65-111">Instalace</span><span class="sxs-lookup"><span data-stu-id="2dc65-111">Install</span></span>

<span data-ttu-id="2dc65-112">Rozhraní příkazového řádku ML.NET je nainstalována jako jakékoli jiné dotnet globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="2dc65-112">The ML.NET CLI is installed like any other dotnet Global Tool.</span></span> <span data-ttu-id="2dc65-113">Můžete použít `dotnet tool install` rozhraní příkazového řádku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2dc65-113">You use the `dotnet tool install` .NET Core CLI command.</span></span> 

<span data-ttu-id="2dc65-114">Následující příklad ukazuje, jak nainstalovat rozhraní příkazového řádku ML.NET výchozí umístění kanál NuGet:</span><span class="sxs-lookup"><span data-stu-id="2dc65-114">The following example shows how to install the ML.NET CLI in the default NuGet feed location:</span></span>

```console
dotnet tool install -g mlnet
```

<span data-ttu-id="2dc65-115">Pokud nástroj nejde nainstalovat, (tj. Pokud není k dispozici na výchozím nastavení informačního kanálu NuGet), zobrazí se chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="2dc65-115">If the tool can't be installed (that is, if it is not available at the default NuGet feed), error messages are displayed.</span></span> <span data-ttu-id="2dc65-116">Zkontrolujte, že se kontroluje informační kanály, které jste očekávali.</span><span class="sxs-lookup"><span data-stu-id="2dc65-116">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="2dc65-117">Pokud je instalace úspěšná, zobrazí se zpráva zobrazující příkazu používaný k volání nástroje a verze nainstalovaná, podobně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="2dc65-117">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

<span data-ttu-id="2dc65-118">Můžete potvrdit, že instalace proběhla úspěšně tak, že zadáte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="2dc65-118">You can confirm the installation was successful by typing the following command:</span></span>

```console
mlnet
```

<span data-ttu-id="2dc65-119">Měli byste vidět nápovědy pro příkazy dostupné pro nástroj mlnet například příkaz "Automatické – train".</span><span class="sxs-lookup"><span data-stu-id="2dc65-119">You should see the help for available commands for the mlnet tool such as the 'auto-train' command.</span></span>

## <a name="install-a-specific-release-version"></a><span data-ttu-id="2dc65-120">Instalace konkrétní verze</span><span class="sxs-lookup"><span data-stu-id="2dc65-120">Install a specific release version</span></span>

<span data-ttu-id="2dc65-121">Pokud se snažíte nainstalovat předběžné verzi nebo konkrétní verzi nástroje, můžete zadat [framework](../../standard/frameworks.md) v následujícím formátu:</span><span class="sxs-lookup"><span data-stu-id="2dc65-121">If you're trying to install a pre-release version or a specific version of the tool, you can specify the [framework](../../standard/frameworks.md) using the following format:</span></span>

```console
dotnet tool install -g mlnet --framework <FRAMEWORK>
```

<span data-ttu-id="2dc65-122">Můžete také zkontrolovat, pokud je tak, že zadáte následující příkaz správně nainstalován balíček:</span><span class="sxs-lookup"><span data-stu-id="2dc65-122">You can also check if the package is properly installed by typing the following command:</span></span>

```console
dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a><span data-ttu-id="2dc65-123">Odinstalovat balíček rozhraní příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="2dc65-123">Uninstall the CLI package</span></span>

<span data-ttu-id="2dc65-124">Zadejte následující příkaz pro odinstalaci balíčku z místního počítače:</span><span class="sxs-lookup"><span data-stu-id="2dc65-124">Type the following command to uninstall the package from your local machine:</span></span>

```console
dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a><span data-ttu-id="2dc65-125">Aktualizovat balíček rozhraní příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="2dc65-125">Update the CLI package</span></span>

<span data-ttu-id="2dc65-126">Zadejte následující příkaz k aktualizaci balíčku z místního počítače:</span><span class="sxs-lookup"><span data-stu-id="2dc65-126">Type the following command to update the package from your local machine:</span></span>

```console
dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a><span data-ttu-id="2dc65-127">Nastavení rozhraní příkazového řádku návrhy (založené na kartě Automatické dokončování)</span><span class="sxs-lookup"><span data-stu-id="2dc65-127">Set up CLI suggestions (tab-based auto-completion)</span></span>

<span data-ttu-id="2dc65-128">Vzhledem k tomu, že rozhraní příkazového řádku ML.NET vychází `System.CommandLine`, obsahuje integrovanou podporu dokončování pomocí tabulátoru.</span><span class="sxs-lookup"><span data-stu-id="2dc65-128">Since the ML.NET CLI is based on `System.CommandLine`, it has built-in support for tab completion.</span></span>

<span data-ttu-id="2dc65-129">V následující animaci je uveden příklad toho, jak funguje automatické dokončování pomocí tabulátoru:</span><span class="sxs-lookup"><span data-stu-id="2dc65-129">An example of how tab auto completion works is shown in the following animation:</span></span>

![obrázek](./media/cli-tab-completion.gif)

<span data-ttu-id="2dc65-131">"Založené na kartě Automatické dokončování" (parametr návrhy) funguje na *prostředí Windows PowerShell* a *bash v systému macOS nebo Linux* ale nebudou fungovat ve *Windows CMD*.</span><span class="sxs-lookup"><span data-stu-id="2dc65-131">'Tab-based auto-completion' (parameter suggestions) works on *Windows PowerShell* and *macOS/Linux bash* but it won't work on *Windows CMD*.</span></span>

<span data-ttu-id="2dc65-132">Ho Pokud chcete povolit, v aktuální verzi preview, musí koncový uživatel provést několik kroků jednou pro každé prostředí, které jsou uvedené níže.</span><span class="sxs-lookup"><span data-stu-id="2dc65-132">To enable it, in the current preview version, the end user has to take a few steps once per shell, outlined below.</span></span> <span data-ttu-id="2dc65-133">Až to uděláte, budou fungovat dokončování pro všechny aplikace napsané s využitím `System.CommandLine` například ML.NET rozhraní příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="2dc65-133">Once this is done, completions will work for all apps written using `System.CommandLine` such as the ML.NET CLI.</span></span>

<span data-ttu-id="2dc65-134">Na počítači, kde byste chtěli povolit dokončení budete muset udělat dvě věci.</span><span class="sxs-lookup"><span data-stu-id="2dc65-134">On the machine where you'd like to enable completion, you'll need to do two things.</span></span>

1. <span data-ttu-id="2dc65-135">Nainstalujte `dotnet-suggest` globální nástroj spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="2dc65-135">Install the `dotnet-suggest` global tool by running the following command:</span></span>

    ```console
    dotnet tool install dotnet-suggest -g
    ```

2. <span data-ttu-id="2dc65-136">Přidáte skript odpovídající překrytí k vašemu profilu prostředí.</span><span class="sxs-lookup"><span data-stu-id="2dc65-136">Add the appropriate shim script to your shell profile.</span></span> <span data-ttu-id="2dc65-137">Budete muset vytvořit prostředí soubor profilu.</span><span class="sxs-lookup"><span data-stu-id="2dc65-137">You may have to create a shell profile file.</span></span> <span data-ttu-id="2dc65-138">Skript překrytí bude předávat dokončení požadavků z vašeho prostředí `dotnet-suggest` nástroj, který deleguje na příslušné `System.CommandLine`– na základě aplikace.</span><span class="sxs-lookup"><span data-stu-id="2dc65-138">The shim script will forward completion requests from your shell to the `dotnet-suggest` tool, which delegates to the appropriate `System.CommandLine`-based app.</span></span>

    * <span data-ttu-id="2dc65-139">Pro prostředí bash, přidejte obsah [dotnet navrhnout shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) k `~/.bash_profile`.</span><span class="sxs-lookup"><span data-stu-id="2dc65-139">For bash, add the contents of [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) to `~/.bash_profile`.</span></span>

    * <span data-ttu-id="2dc65-140">Pro PowerShell, přidejte obsah [dotnet navrhnout shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) k vašemu profilu prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2dc65-140">For PowerShell, add the contents of [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) to your PowerShell profile.</span></span> <span data-ttu-id="2dc65-141">Můžete najít očekávanou cestou k vašemu profilu prostředí PowerShell spuštěním následujícího příkazu v konzole:</span><span class="sxs-lookup"><span data-stu-id="2dc65-141">You can find the expected path to your PowerShell profile by running the following command in your console:</span></span>

    ```console
    echo $profile
    ``` 

<span data-ttu-id="2dc65-142">(Pro další prostředí [vyhledejte](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) nebo otevřete [problém](https://github.com/dotnet/System.CommandLine/issues).)</span><span class="sxs-lookup"><span data-stu-id="2dc65-142">(For other shells, [look for](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) or open an [issue](https://github.com/dotnet/System.CommandLine/issues).)</span></span>

## <a name="installation-directory"></a><span data-ttu-id="2dc65-143">Instalační adresář</span><span class="sxs-lookup"><span data-stu-id="2dc65-143">Installation directory</span></span>

<span data-ttu-id="2dc65-144">Rozhraní příkazového řádku ML.NET mohou být nainstalovány ve výchozím adresáři nebo v konkrétním umístění.</span><span class="sxs-lookup"><span data-stu-id="2dc65-144">The ML.NET CLI can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="2dc65-145">Výchozí adresáře jsou:</span><span class="sxs-lookup"><span data-stu-id="2dc65-145">The default directories are:</span></span>

| <span data-ttu-id="2dc65-146">Operační systém</span><span class="sxs-lookup"><span data-stu-id="2dc65-146">OS</span></span>          | <span data-ttu-id="2dc65-147">Cesta</span><span class="sxs-lookup"><span data-stu-id="2dc65-147">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="2dc65-148">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="2dc65-148">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="2dc65-149">Windows</span><span class="sxs-lookup"><span data-stu-id="2dc65-149">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="2dc65-150">Tato místa jsou přidány do cesty uživatele při prvním spuštění sady SDK, tak že nainstalované nástroje pro globální mohou být volány.</span><span class="sxs-lookup"><span data-stu-id="2dc65-150">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="2dc65-151">Poznámka: globální nástroje jsou specifické pro uživatele, počítače nejsou globální.</span><span class="sxs-lookup"><span data-stu-id="2dc65-151">Note: the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="2dc65-152">Jsou specifické pro uživatele znamená, že nemůžete nainstalovat globální nástroj, který je k dispozici pro všechny uživatele počítače.</span><span class="sxs-lookup"><span data-stu-id="2dc65-152">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="2dc65-153">Nástroj je k dispozici pouze pro každý uživatelský profil ve kterém byl nainstalován nástroj.</span><span class="sxs-lookup"><span data-stu-id="2dc65-153">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="2dc65-154">Globální nástroje můžete také nainstalovat v konkrétní adresář.</span><span class="sxs-lookup"><span data-stu-id="2dc65-154">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="2dc65-155">Při instalaci v konkrétní adresář, uživatel musí zajistit příkaz je k dispozici, včetně tohoto adresáře v cestě, voláním příkazu se do adresáře určeného, nebo zavolání nástroj v rámci zadaného adresáře.</span><span class="sxs-lookup"><span data-stu-id="2dc65-155">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="2dc65-156">Rozhraní příkazového řádku .NET Core nepodporuje toto umístění v tomto případě automaticky přidat do proměnné prostředí PATH.</span><span class="sxs-lookup"><span data-stu-id="2dc65-156">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="2dc65-157">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2dc65-157">See also</span></span>

- [<span data-ttu-id="2dc65-158">Kurz: Začínáme s ML.NET rozhraní příkazového řádku nástroje.</span><span class="sxs-lookup"><span data-stu-id="2dc65-158">Tutorial on 'Getting Started with ML.NET CLI tool'</span></span>](../tutorials/mlnet-cli.md)
- [<span data-ttu-id="2dc65-159">Automaticky trénování modelů pomocí nástroje příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="2dc65-159">How to automatically train models with the ML.NET CLI tool</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="2dc65-160">Rozhraní příkazového řádku ML.NET automaticky trénování příkaz referenční příručka</span><span class="sxs-lookup"><span data-stu-id="2dc65-160">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md) 
- [<span data-ttu-id="2dc65-161">Telemetrie v rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="2dc65-161">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
