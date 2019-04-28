---
title: Povolení dokončování pomocí tabulátoru
description: V tomto článku se naučíte, jak povolení dokončování pomocí tabulátoru pro rozhraní příkazového řádku .NET Core pro PowerShell, Bash a zsh.
author: thraka
ms.author: adegeo
ms.date: 12/17/2018
ms.openlocfilehash: 16574e02aa9f9167602401eef2ad7a73e07ad107
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61648214"
---
# <a name="how-to-enable-tab-completion-for-net-core-cli"></a><span data-ttu-id="9626a-103">Povolení dokončování pomocí TABULÁTORU pro rozhraní příkazového řádku .NET Core</span><span class="sxs-lookup"><span data-stu-id="9626a-103">How to enable TAB completion for .NET Core CLI</span></span>

<span data-ttu-id="9626a-104">Počínaje .NET Core 2.0 SDK, rozhraní příkazového řádku .NET Core podporuje dokončování pomocí tabulátoru.</span><span class="sxs-lookup"><span data-stu-id="9626a-104">Starting with .NET Core 2.0 SDK, the .NET Core CLI supports tab completion.</span></span> <span data-ttu-id="9626a-105">Tento článek popisuje, jak nakonfigurovat dokončování pomocí tabulátoru pro tři prostředí PowerShell, Bash a zsh.</span><span class="sxs-lookup"><span data-stu-id="9626a-105">This article describes how to configure tab completion for three shells, PowerShell, Bash, and zsh.</span></span> <span data-ttu-id="9626a-106">Další prostředí může mít podporu pro automatické dokončování.</span><span class="sxs-lookup"><span data-stu-id="9626a-106">Other shells may have support for auto completion.</span></span> <span data-ttu-id="9626a-107">Přečtěte si jejich dokumentaci o tom, jak nakonfigurovat automatické doplňování, kroky by měl být podobný postup popsaný v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="9626a-107">Refer to their documentation on how to configure auto completion, the steps should be similar to the steps described in this article.</span></span>

[!INCLUDE [topic-appliesto-net-core-2plus](~/includes/topic-appliesto-net-core-2plus.md)]

<span data-ttu-id="9626a-108">Po nastavení dokončování pomocí tabulátoru pro rozhraní příkazového řádku .NET Core se aktivuje zadáním `dotnet` příkazu v prostředí a potom stisknutím klávesy TAB.</span><span class="sxs-lookup"><span data-stu-id="9626a-108">Once setup, tab completion for the .NET Core CLI is triggered by typing a `dotnet` command in the shell, and then pressing the TAB key.</span></span> <span data-ttu-id="9626a-109">Aktuální příkaz řádek se odešle do `dotnet complete` příkazu a výsledky se zpracovávají ve vašem prostředí.</span><span class="sxs-lookup"><span data-stu-id="9626a-109">The current command line is sent to the `dotnet complete` command, and the results are processed by your shell.</span></span> <span data-ttu-id="9626a-110">Můžete testovat výsledky bez povolení dokončování pomocí tabulátoru odesláním něco přímo `dotnet complete` příkazu.</span><span class="sxs-lookup"><span data-stu-id="9626a-110">You can test the results without enabling tab completion by sending something directly to the `dotnet complete` command.</span></span> <span data-ttu-id="9626a-111">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9626a-111">For example:</span></span>

```
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

<span data-ttu-id="9626a-112">Pokud tento příkaz nefunguje, ujistěte se, že sada .NET Core 2.0 SDK nebo vyšší než je nainstalována.</span><span class="sxs-lookup"><span data-stu-id="9626a-112">If that command doesn't work, make sure that .NET Core 2.0 SDK or above is installed.</span></span> <span data-ttu-id="9626a-113">Pokud je nainstalovaná, ale tohoto příkazu stále nefunguje, ujistěte se, že `dotnet` příkaz překládá na verzi .NET Core 2.0 SDK a vyšší.</span><span class="sxs-lookup"><span data-stu-id="9626a-113">If it's installed, but that command still doesn't work, make sure that the `dotnet` command resolves to a version of .NET Core 2.0 SDK and above.</span></span> <span data-ttu-id="9626a-114">Použití `dotnet --version` příkazu zobrazte jakou verzi `dotnet` správně směřuje aktuální cestě.</span><span class="sxs-lookup"><span data-stu-id="9626a-114">Use the `dotnet --version` command to see what version of `dotnet` your current path is resolving to.</span></span> <span data-ttu-id="9626a-115">Další informace najdete v tématu [vyberte verzi .NET Core používat](../versions/selection.md).</span><span class="sxs-lookup"><span data-stu-id="9626a-115">For more information, see [Select the .NET Core version to use](../versions/selection.md).</span></span>

### <a name="examples"></a><span data-ttu-id="9626a-116">Příklady</span><span class="sxs-lookup"><span data-stu-id="9626a-116">Examples</span></span>

<span data-ttu-id="9626a-117">Tady je několik příkladů poskytuje jaké tab k dokončování příkazů:</span><span class="sxs-lookup"><span data-stu-id="9626a-117">Here are some examples of what tab completion provides:</span></span>

<span data-ttu-id="9626a-118">Vstup</span><span class="sxs-lookup"><span data-stu-id="9626a-118">Input</span></span>                                | <span data-ttu-id="9626a-119">změní</span><span class="sxs-lookup"><span data-stu-id="9626a-119">becomes</span></span>                                                                     | <span data-ttu-id="9626a-120">protože</span><span class="sxs-lookup"><span data-stu-id="9626a-120">because</span></span>
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | <span data-ttu-id="9626a-121">`add` je první podpříkaz podle abecedy.</span><span class="sxs-lookup"><span data-stu-id="9626a-121">`add` is the first subcommand, alphabetically.</span></span>
`dotnet add p⇥`                      | `dotnet add --help`                                                          | <span data-ttu-id="9626a-122">Karta dokončení shody podřetězců a `--help` je první podle abecedy.</span><span class="sxs-lookup"><span data-stu-id="9626a-122">Tab completion matches substrings and `--help` comes first alphabetically.</span></span>
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | <span data-ttu-id="9626a-123">Stisknutím klávesy tab podruhé zobrazí další návrh.</span><span class="sxs-lookup"><span data-stu-id="9626a-123">Pressing tab a second time brings up the next suggestion.</span></span>      
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | <span data-ttu-id="9626a-124">Výsledky jsou vráceny podle abecedy.</span><span class="sxs-lookup"><span data-stu-id="9626a-124">Results are returned alphabetically.</span></span>
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | <span data-ttu-id="9626a-125">Dokončování pomocí tabulátoru je soubor projektu vědět.</span><span class="sxs-lookup"><span data-stu-id="9626a-125">Tab completion is project file aware.</span></span>

## <a name="powershell"></a><span data-ttu-id="9626a-126">PowerShell</span><span class="sxs-lookup"><span data-stu-id="9626a-126">PowerShell</span></span>

<span data-ttu-id="9626a-127">Chcete-li přidat tab k dokončování příkazů do **PowerShell** pro rozhraní příkazového řádku .NET Core vytvořit nebo upravit profil uložen v proměnné `$PROFILE`.</span><span class="sxs-lookup"><span data-stu-id="9626a-127">To add tab completion to **PowerShell** for the .NET Core CLI, create or edit the profile stored in the variable `$PROFILE`.</span></span> <span data-ttu-id="9626a-128">Další informace najdete v tématu [postup vytvoření profilu](/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-6#how-to-create-a-profile) a [profily a zásady spouštění](/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-6#profiles-and-execution-policy).</span><span class="sxs-lookup"><span data-stu-id="9626a-128">For more information, see [How to create your profile](/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-6#how-to-create-a-profile) and [Profiles and execution policy](/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-6#profiles-and-execution-policy).</span></span> 

<span data-ttu-id="9626a-129">Přidejte následující kód k vašemu profilu:</span><span class="sxs-lookup"><span data-stu-id="9626a-129">Add the following code to your profile:</span></span>

```powershell
# PowerShell parameter completion shim for the dotnet CLI 
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock {
     param($commandName, $wordToComplete, $cursorPosition)
         dotnet complete --position $cursorPosition "$wordToComplete" | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
         }
 }
```

## <a name="bash"></a><span data-ttu-id="9626a-130">Bash</span><span class="sxs-lookup"><span data-stu-id="9626a-130">Bash</span></span>

<span data-ttu-id="9626a-131">Přidání dokončování pomocí tabulátoru pro vaše **bash** prostředí pro rozhraní příkazového řádku .NET Core, přidejte následující kód, který vaše `.bashrc` souboru:</span><span class="sxs-lookup"><span data-stu-id="9626a-131">To add tab completion to your **bash** shell for the .NET Core CLI, add the following code to your `.bashrc` file:</span></span>

```bash
# bash parameter completion for the dotnet CLI

_dotnet_bash_complete()
{
  local word=${COMP_WORDS[COMP_CWORD]}

  local completions
  completions="$(dotnet complete --position "${COMP_POINT}" "${COMP_LINE}")"

  COMPREPLY=( $(compgen -W "$completions" -- "$word") )
}

complete -f -F _dotnet_bash_complete dotnet
```

## <a name="zsh"></a><span data-ttu-id="9626a-132">Zsh</span><span class="sxs-lookup"><span data-stu-id="9626a-132">Zsh</span></span>

<span data-ttu-id="9626a-133">Přidání dokončování pomocí tabulátoru pro vaše **zsh** prostředí pro rozhraní příkazového řádku .NET Core, přidejte následující kód, který vaše `.zshrc` souboru:</span><span class="sxs-lookup"><span data-stu-id="9626a-133">To add tab completion to your **zsh** shell for the .NET Core CLI, add the following code to your `.zshrc` file:</span></span>

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete() 
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```
