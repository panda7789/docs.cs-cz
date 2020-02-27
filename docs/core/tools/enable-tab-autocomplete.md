---
title: Povolení dokončování pomocí tabulátoru
description: V tomto článku se naučíte, jak povolit dokončování karet pro .NET Core CLI pro PowerShell, bash a zsh.
author: thraka
ms.author: adegeo
ms.date: 11/03/2019
ms.openlocfilehash: 6614f11a9c4eb1b1aac4dd8dac8d05d15262bd0c
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626005"
---
# <a name="how-to-enable-tab-completion-for-the-net-core-cli"></a><span data-ttu-id="4738c-103">Jak povolit dokončování karet pro .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="4738c-103">How to enable TAB completion for the .NET Core CLI</span></span>

<span data-ttu-id="4738c-104">**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="4738c-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="4738c-105">Tento článek popisuje, jak nakonfigurovat dokončování karet pro tři prostředí, PowerShell, bash a zsh.</span><span class="sxs-lookup"><span data-stu-id="4738c-105">This article describes how to configure tab completion for three shells, PowerShell, Bash, and zsh.</span></span> <span data-ttu-id="4738c-106">Další prostředí naleznete v dokumentaci ke konfiguraci dokončování karet.</span><span class="sxs-lookup"><span data-stu-id="4738c-106">For other shells, refer to their documentation on how to configure tab completion.</span></span>

<span data-ttu-id="4738c-107">Po nastavení se aktivace karty .NET Core CLI aktivuje zadáním příkazu `dotnet` v prostředí a následným stisknutím klávesy TAB.</span><span class="sxs-lookup"><span data-stu-id="4738c-107">Once set up, tab completion for the .NET Core CLI is triggered by typing a `dotnet` command in the shell, and then pressing the TAB key.</span></span> <span data-ttu-id="4738c-108">Aktuální příkazový řádek se odešle do příkazu `dotnet complete` a výsledky se zpracují ve vašem prostředí.</span><span class="sxs-lookup"><span data-stu-id="4738c-108">The current command line is sent to the `dotnet complete` command, and the results are processed by your shell.</span></span> <span data-ttu-id="4738c-109">Výsledky můžete testovat bez aktivace tabulátoru odesláním nějakého přímo do příkazu `dotnet complete`.</span><span class="sxs-lookup"><span data-stu-id="4738c-109">You can test the results without enabling tab completion by sending something directly to the `dotnet complete` command.</span></span> <span data-ttu-id="4738c-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4738c-110">For example:</span></span>

```console
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

<span data-ttu-id="4738c-111">Pokud tento příkaz nefunguje, ujistěte se, že je nainstalovaná sada .NET Core 2,0 SDK nebo novější.</span><span class="sxs-lookup"><span data-stu-id="4738c-111">If that command doesn't work, make sure that .NET Core 2.0 SDK or above is installed.</span></span> <span data-ttu-id="4738c-112">Pokud je nainstalován, ale tento příkaz stále nefunguje, ujistěte se, že příkaz `dotnet` překládá na verzi .NET Core 2,0 SDK a vyšší.</span><span class="sxs-lookup"><span data-stu-id="4738c-112">If it's installed, but that command still doesn't work, make sure that the `dotnet` command resolves to a version of .NET Core 2.0 SDK and above.</span></span> <span data-ttu-id="4738c-113">Pomocí příkazu `dotnet --version` můžete zjistit, jakou verzi `dotnet` vaše aktuální cesta překládá.</span><span class="sxs-lookup"><span data-stu-id="4738c-113">Use the `dotnet --version` command to see what version of `dotnet` your current path is resolving to.</span></span> <span data-ttu-id="4738c-114">Další informace najdete v tématu [Výběr verze rozhraní .NET Core, která se má použít](../versions/selection.md).</span><span class="sxs-lookup"><span data-stu-id="4738c-114">For more information, see [Select the .NET Core version to use](../versions/selection.md).</span></span>

### <a name="examples"></a><span data-ttu-id="4738c-115">Příklady</span><span class="sxs-lookup"><span data-stu-id="4738c-115">Examples</span></span>

<span data-ttu-id="4738c-116">Tady je několik příkladů, které doplňování karet nabízí:</span><span class="sxs-lookup"><span data-stu-id="4738c-116">Here are some examples of what tab completion provides:</span></span>

<span data-ttu-id="4738c-117">Vstup</span><span class="sxs-lookup"><span data-stu-id="4738c-117">Input</span></span>                                | <span data-ttu-id="4738c-118">stane</span><span class="sxs-lookup"><span data-stu-id="4738c-118">becomes</span></span>                                                                     | <span data-ttu-id="4738c-119">tím</span><span class="sxs-lookup"><span data-stu-id="4738c-119">because</span></span>
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | <span data-ttu-id="4738c-120">`add` je první dílčí příkaz abecedně.</span><span class="sxs-lookup"><span data-stu-id="4738c-120">`add` is the first subcommand, alphabetically.</span></span>
`dotnet add p⇥`                      | `dotnet add --help`                                                          | <span data-ttu-id="4738c-121">Doplňování tabulátoru odpovídá podřetězcům a `--help` je první abecedně.</span><span class="sxs-lookup"><span data-stu-id="4738c-121">Tab completion matches substrings and `--help` comes first alphabetically.</span></span>
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | <span data-ttu-id="4738c-122">Další návrh zobrazíte stisknutím klávesy TAB a podruhé.</span><span class="sxs-lookup"><span data-stu-id="4738c-122">Pressing tab a second time brings up the next suggestion.</span></span>      
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | <span data-ttu-id="4738c-123">Výsledky se vrátí abecedně.</span><span class="sxs-lookup"><span data-stu-id="4738c-123">Results are returned alphabetically.</span></span>
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | <span data-ttu-id="4738c-124">Dokončování karet je soubor projektu s podporou.</span><span class="sxs-lookup"><span data-stu-id="4738c-124">Tab completion is project file aware.</span></span>

## <a name="powershell"></a><span data-ttu-id="4738c-125">PowerShell</span><span class="sxs-lookup"><span data-stu-id="4738c-125">PowerShell</span></span>

<span data-ttu-id="4738c-126">Pokud chcete pro .NET Core CLI přidat do **PowerShellu** tabulátor, vytvořte nebo upravte profil uložený v proměnné `$PROFILE`.</span><span class="sxs-lookup"><span data-stu-id="4738c-126">To add tab completion to **PowerShell** for the .NET Core CLI, create or edit the profile stored in the variable `$PROFILE`.</span></span> <span data-ttu-id="4738c-127">Další informace najdete v tématu [jak vytvořit profil](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) a profily a [zásady spouštění](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy).</span><span class="sxs-lookup"><span data-stu-id="4738c-127">For more information, see [How to create your profile](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) and [Profiles and execution policy](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy).</span></span> 

<span data-ttu-id="4738c-128">Do svého profilu přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="4738c-128">Add the following code to your profile:</span></span>

```powershell
# PowerShell parameter completion shim for the dotnet CLI 
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock {
     param($commandName, $wordToComplete, $cursorPosition)
         dotnet complete --position $cursorPosition "$wordToComplete" | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
         }
 }
```

## <a name="bash"></a><span data-ttu-id="4738c-129">bash</span><span class="sxs-lookup"><span data-stu-id="4738c-129">bash</span></span>

<span data-ttu-id="4738c-130">Chcete-li do prostředí **bash** pro .NET Core CLI přidat doplňování tabulátoru, přidejte do souboru `.bashrc` následující kód:</span><span class="sxs-lookup"><span data-stu-id="4738c-130">To add tab completion to your **bash** shell for the .NET Core CLI, add the following code to your `.bashrc` file:</span></span>

```bash
# bash parameter completion for the dotnet CLI

_dotnet_bash_complete()
{
  local word=${COMP_WORDS[COMP_CWORD]}

  local completions
  completions="$(dotnet complete --position "${COMP_POINT}" "${COMP_LINE}" 2>/dev/null)"
  if [ $? -ne 0 ]; then
    completions=""
  fi

  COMPREPLY=( $(compgen -W "$completions" -- "$word") )
}

complete -f -F _dotnet_bash_complete dotnet
```

## <a name="zsh"></a><span data-ttu-id="4738c-131">zsh</span><span class="sxs-lookup"><span data-stu-id="4738c-131">zsh</span></span>

<span data-ttu-id="4738c-132">Chcete-li do prostředí **ZSH** pro .NET Core CLI přidat doplňování tabulátoru, přidejte do souboru `.zshrc` následující kód:</span><span class="sxs-lookup"><span data-stu-id="4738c-132">To add tab completion to your **zsh** shell for the .NET Core CLI, add the following code to your `.zshrc` file:</span></span>

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete() 
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```
