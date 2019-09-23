---
title: Povolit dokončování karet
description: V tomto článku se naučíte, jak povolit dokončování karet pro .NET Core CLI pro PowerShell, bash a zsh.
author: thraka
ms.author: adegeo
ms.date: 12/17/2018
ms.openlocfilehash: 0f29ba2ef1d419339a0e2dc44f67c93b326eb40d
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182457"
---
# <a name="how-to-enable-tab-completion-for-net-core-cli"></a><span data-ttu-id="302a9-103">Jak povolit dokončování karet pro .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="302a9-103">How to enable TAB completion for .NET Core CLI</span></span>

<span data-ttu-id="302a9-104">Počínaje rozhraním .NET Core 2,0 SDK .NET Core CLI podporuje dokončování karet.</span><span class="sxs-lookup"><span data-stu-id="302a9-104">Starting with .NET Core 2.0 SDK, the .NET Core CLI supports tab completion.</span></span> <span data-ttu-id="302a9-105">Tento článek popisuje, jak nakonfigurovat dokončování karet pro tři prostředí, PowerShell, bash a zsh.</span><span class="sxs-lookup"><span data-stu-id="302a9-105">This article describes how to configure tab completion for three shells, PowerShell, Bash, and zsh.</span></span> <span data-ttu-id="302a9-106">Další prostředí můžou podporovat automatické dokončování.</span><span class="sxs-lookup"><span data-stu-id="302a9-106">Other shells may have support for auto completion.</span></span> <span data-ttu-id="302a9-107">Informace o tom, jak nakonfigurovat automatické dokončování, najdete v dokumentaci, jak postupovat podle kroků popsaných v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="302a9-107">Refer to their documentation on how to configure auto completion, the steps should be similar to the steps described in this article.</span></span>

[!INCLUDE [topic-appliesto-net-core-2plus](~/includes/topic-appliesto-net-core-2plus.md)]

<span data-ttu-id="302a9-108">Po dokončení instalace se aktivuje doplňování tabulátoru pro .NET Core CLI zadáním `dotnet` příkazu do prostředí a následným stisknutím klávesy TAB.</span><span class="sxs-lookup"><span data-stu-id="302a9-108">Once setup, tab completion for the .NET Core CLI is triggered by typing a `dotnet` command in the shell, and then pressing the TAB key.</span></span> <span data-ttu-id="302a9-109">Do `dotnet complete` příkazu se pošle aktuální příkazový řádek a výsledky se zpracují ve vašem prostředí.</span><span class="sxs-lookup"><span data-stu-id="302a9-109">The current command line is sent to the `dotnet complete` command, and the results are processed by your shell.</span></span> <span data-ttu-id="302a9-110">Výsledky můžete testovat bez aktivace tabulátoru odesláním nějakého přímo do `dotnet complete` příkazu.</span><span class="sxs-lookup"><span data-stu-id="302a9-110">You can test the results without enabling tab completion by sending something directly to the `dotnet complete` command.</span></span> <span data-ttu-id="302a9-111">Příklad:</span><span class="sxs-lookup"><span data-stu-id="302a9-111">For example:</span></span>

```console
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

<span data-ttu-id="302a9-112">Pokud tento příkaz nefunguje, ujistěte se, že je nainstalovaná sada .NET Core 2,0 SDK nebo novější.</span><span class="sxs-lookup"><span data-stu-id="302a9-112">If that command doesn't work, make sure that .NET Core 2.0 SDK or above is installed.</span></span> <span data-ttu-id="302a9-113">Pokud je nainstalován, ale tento příkaz stále nefunguje, ujistěte se, že `dotnet` příkaz překládá na verzi .NET Core 2,0 SDK a vyšší.</span><span class="sxs-lookup"><span data-stu-id="302a9-113">If it's installed, but that command still doesn't work, make sure that the `dotnet` command resolves to a version of .NET Core 2.0 SDK and above.</span></span> <span data-ttu-id="302a9-114">Pomocí příkazu zjistíte, která `dotnet` verze vaší aktuální cesty se překládá na. `dotnet --version`</span><span class="sxs-lookup"><span data-stu-id="302a9-114">Use the `dotnet --version` command to see what version of `dotnet` your current path is resolving to.</span></span> <span data-ttu-id="302a9-115">Další informace najdete v tématu [Výběr verze rozhraní .NET Core, která se má použít](../versions/selection.md).</span><span class="sxs-lookup"><span data-stu-id="302a9-115">For more information, see [Select the .NET Core version to use](../versions/selection.md).</span></span>

### <a name="examples"></a><span data-ttu-id="302a9-116">Příklady</span><span class="sxs-lookup"><span data-stu-id="302a9-116">Examples</span></span>

<span data-ttu-id="302a9-117">Tady je několik příkladů, které doplňování karet nabízí:</span><span class="sxs-lookup"><span data-stu-id="302a9-117">Here are some examples of what tab completion provides:</span></span>

<span data-ttu-id="302a9-118">Vstup</span><span class="sxs-lookup"><span data-stu-id="302a9-118">Input</span></span>                                | <span data-ttu-id="302a9-119">stane</span><span class="sxs-lookup"><span data-stu-id="302a9-119">becomes</span></span>                                                                     | <span data-ttu-id="302a9-120">tím</span><span class="sxs-lookup"><span data-stu-id="302a9-120">because</span></span>
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | <span data-ttu-id="302a9-121">`add`je první dílčí příkaz abecedně.</span><span class="sxs-lookup"><span data-stu-id="302a9-121">`add` is the first subcommand, alphabetically.</span></span>
`dotnet add p⇥`                      | `dotnet add --help`                                                          | <span data-ttu-id="302a9-122">Doplňování tabulátoru odpovídá podřetězcům a `--help` je uvedeno první abecedně.</span><span class="sxs-lookup"><span data-stu-id="302a9-122">Tab completion matches substrings and `--help` comes first alphabetically.</span></span>
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | <span data-ttu-id="302a9-123">Další návrh zobrazíte stisknutím klávesy TAB a podruhé.</span><span class="sxs-lookup"><span data-stu-id="302a9-123">Pressing tab a second time brings up the next suggestion.</span></span>      
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | <span data-ttu-id="302a9-124">Výsledky se vrátí abecedně.</span><span class="sxs-lookup"><span data-stu-id="302a9-124">Results are returned alphabetically.</span></span>
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | <span data-ttu-id="302a9-125">Dokončování karet je soubor projektu s podporou.</span><span class="sxs-lookup"><span data-stu-id="302a9-125">Tab completion is project file aware.</span></span>

## <a name="powershell"></a><span data-ttu-id="302a9-126">PowerShell</span><span class="sxs-lookup"><span data-stu-id="302a9-126">PowerShell</span></span>

<span data-ttu-id="302a9-127">Pokud chcete do **PowerShellu** přidat doplňování tabulátoru pro .NET Core CLI, vytvořte nebo upravte profil uložený `$PROFILE`v proměnné.</span><span class="sxs-lookup"><span data-stu-id="302a9-127">To add tab completion to **PowerShell** for the .NET Core CLI, create or edit the profile stored in the variable `$PROFILE`.</span></span> <span data-ttu-id="302a9-128">Další informace najdete v tématu [jak vytvořit profil](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) a profily a [zásady spouštění](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy).</span><span class="sxs-lookup"><span data-stu-id="302a9-128">For more information, see [How to create your profile](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) and [Profiles and execution policy](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy).</span></span> 

<span data-ttu-id="302a9-129">Do svého profilu přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="302a9-129">Add the following code to your profile:</span></span>

```powershell
# PowerShell parameter completion shim for the dotnet CLI 
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock {
     param($commandName, $wordToComplete, $cursorPosition)
         dotnet complete --position $cursorPosition "$wordToComplete" | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
         }
 }
```

## <a name="bash"></a><span data-ttu-id="302a9-130">Bash</span><span class="sxs-lookup"><span data-stu-id="302a9-130">Bash</span></span>

<span data-ttu-id="302a9-131">Chcete-li do prostředí **bash** pro .NET Core CLI přidat doplňování tabulátoru, přidejte do `.bashrc` souboru následující kód:</span><span class="sxs-lookup"><span data-stu-id="302a9-131">To add tab completion to your **bash** shell for the .NET Core CLI, add the following code to your `.bashrc` file:</span></span>

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

## <a name="zsh"></a><span data-ttu-id="302a9-132">zsh</span><span class="sxs-lookup"><span data-stu-id="302a9-132">Zsh</span></span>

<span data-ttu-id="302a9-133">Chcete-li do prostředí **ZSH** pro .NET Core CLI přidat doplňování tabulátoru, přidejte do `.zshrc` souboru následující kód:</span><span class="sxs-lookup"><span data-stu-id="302a9-133">To add tab completion to your **zsh** shell for the .NET Core CLI, add the following code to your `.zshrc` file:</span></span>

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete() 
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```
