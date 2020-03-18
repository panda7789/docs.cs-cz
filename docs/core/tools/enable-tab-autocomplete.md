---
title: Povolení dokončování pomocí tabulátoru
description: Tento článek vás naučí, jak povolit dokončení karty pro rozhraní CLI jádra .NET pro Prostředí PowerShell, Bash a zsh.
author: thraka
ms.author: adegeo
ms.date: 11/03/2019
ms.openlocfilehash: 31328be14811760bc8d7fb527e0d55abfe6b1493
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156748"
---
# <a name="how-to-enable-tab-completion-for-the-net-core-cli"></a><span data-ttu-id="5a801-103">Povolení dokončování polí TAB pro rozhraní CLI jádra .NET</span><span class="sxs-lookup"><span data-stu-id="5a801-103">How to enable TAB completion for the .NET Core CLI</span></span>

<span data-ttu-id="5a801-104">**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="5a801-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="5a801-105">Tento článek popisuje, jak nakonfigurovat dokončení karty pro tři prostředí, PowerShell, Bash a zsh.</span><span class="sxs-lookup"><span data-stu-id="5a801-105">This article describes how to configure tab completion for three shells, PowerShell, Bash, and zsh.</span></span> <span data-ttu-id="5a801-106">Další prostředí naleznete v jejich dokumentaci o konfiguraci dokončení karty.</span><span class="sxs-lookup"><span data-stu-id="5a801-106">For other shells, refer to their documentation on how to configure tab completion.</span></span>

<span data-ttu-id="5a801-107">Po nastavení se dokončení karty pro rozhraní příkazového příkazu `dotnet` .NET Core spustí zadáním příkazu do prostředí a stisknutím klávesy TAB.</span><span class="sxs-lookup"><span data-stu-id="5a801-107">Once set up, tab completion for the .NET Core CLI is triggered by typing a `dotnet` command in the shell, and then pressing the TAB key.</span></span> <span data-ttu-id="5a801-108">Aktuální příkazový řádek je `dotnet complete` odeslán do příkazu a výsledky jsou zpracovány prostředím.</span><span class="sxs-lookup"><span data-stu-id="5a801-108">The current command line is sent to the `dotnet complete` command, and the results are processed by your shell.</span></span> <span data-ttu-id="5a801-109">Výsledky můžete otestovat bez povolení dokončení karty `dotnet complete` odesláním něco přímo do příkazu.</span><span class="sxs-lookup"><span data-stu-id="5a801-109">You can test the results without enabling tab completion by sending something directly to the `dotnet complete` command.</span></span> <span data-ttu-id="5a801-110">Například:</span><span class="sxs-lookup"><span data-stu-id="5a801-110">For example:</span></span>

```console
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

<span data-ttu-id="5a801-111">Pokud tento příkaz nefunguje, ujistěte se, že je nainstalována sada .NET Core 2.0 SDK nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="5a801-111">If that command doesn't work, make sure that .NET Core 2.0 SDK or above is installed.</span></span> <span data-ttu-id="5a801-112">Pokud je nainstalován, ale tento příkaz stále nefunguje, `dotnet` ujistěte se, že příkaz překládá na verzi sady .NET Core 2.0 SDK a vyšší.</span><span class="sxs-lookup"><span data-stu-id="5a801-112">If it's installed, but that command still doesn't work, make sure that the `dotnet` command resolves to a version of .NET Core 2.0 SDK and above.</span></span> <span data-ttu-id="5a801-113">Pomocí `dotnet --version` příkazu můžete zjistit, na jakou `dotnet` verzi aktuální cesty se pracuje.</span><span class="sxs-lookup"><span data-stu-id="5a801-113">Use the `dotnet --version` command to see what version of `dotnet` your current path is resolving to.</span></span> <span data-ttu-id="5a801-114">Další informace naleznete [v tématu Select the .NET Core version to use](../versions/selection.md).</span><span class="sxs-lookup"><span data-stu-id="5a801-114">For more information, see [Select the .NET Core version to use](../versions/selection.md).</span></span>

### <a name="examples"></a><span data-ttu-id="5a801-115">Příklady</span><span class="sxs-lookup"><span data-stu-id="5a801-115">Examples</span></span>

<span data-ttu-id="5a801-116">Zde je několik příkladů, co poskytuje dokončení karty:</span><span class="sxs-lookup"><span data-stu-id="5a801-116">Here are some examples of what tab completion provides:</span></span>

<span data-ttu-id="5a801-117">Vstup</span><span class="sxs-lookup"><span data-stu-id="5a801-117">Input</span></span>                                | <span data-ttu-id="5a801-118">se stává</span><span class="sxs-lookup"><span data-stu-id="5a801-118">becomes</span></span>                                                                     | <span data-ttu-id="5a801-119">vzhledem k tomu, že klienti</span><span class="sxs-lookup"><span data-stu-id="5a801-119">because</span></span>
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | <span data-ttu-id="5a801-120">`add`je první podpříkaz, abecedně.</span><span class="sxs-lookup"><span data-stu-id="5a801-120">`add` is the first subcommand, alphabetically.</span></span>
`dotnet add p⇥`                      | `dotnet add --help`                                                          | <span data-ttu-id="5a801-121">Dokončení tabulátoru `--help` odpovídá podřetězcům a je na prvním místě abecedně.</span><span class="sxs-lookup"><span data-stu-id="5a801-121">Tab completion matches substrings and `--help` comes first alphabetically.</span></span>
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | <span data-ttu-id="5a801-122">Stisknutím klávesy tab podruhé vyvoláte další návrh.</span><span class="sxs-lookup"><span data-stu-id="5a801-122">Pressing tab a second time brings up the next suggestion.</span></span>
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | <span data-ttu-id="5a801-123">Výsledky jsou vráceny abecedně.</span><span class="sxs-lookup"><span data-stu-id="5a801-123">Results are returned alphabetically.</span></span>
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | <span data-ttu-id="5a801-124">Dokončení karty je vědoma souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="5a801-124">Tab completion is project file aware.</span></span>

## <a name="powershell"></a><span data-ttu-id="5a801-125">PowerShell</span><span class="sxs-lookup"><span data-stu-id="5a801-125">PowerShell</span></span>

<span data-ttu-id="5a801-126">Chcete-li do **prostředí PowerShell** přidat doplnění karty pro rozhraní PŘÍKAZOVÉHO `$PROFILE`PŘÍKAZU jádra rozhraní .NET, vytvořte nebo upravte profil uložený v proměnné .</span><span class="sxs-lookup"><span data-stu-id="5a801-126">To add tab completion to **PowerShell** for the .NET Core CLI, create or edit the profile stored in the variable `$PROFILE`.</span></span> <span data-ttu-id="5a801-127">Další informace naleznete v tématu [Jak vytvořit profil](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) a [profily a zásady provádění](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy).</span><span class="sxs-lookup"><span data-stu-id="5a801-127">For more information, see [How to create your profile](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) and [Profiles and execution policy](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy).</span></span>

<span data-ttu-id="5a801-128">Do svého profilu přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="5a801-128">Add the following code to your profile:</span></span>

```powershell
# PowerShell parameter completion shim for the dotnet CLI
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock {
     param($commandName, $wordToComplete, $cursorPosition)
         dotnet complete --position $cursorPosition "$wordToComplete" | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
         }
 }
```

## <a name="bash"></a><span data-ttu-id="5a801-129">bash</span><span class="sxs-lookup"><span data-stu-id="5a801-129">bash</span></span>

<span data-ttu-id="5a801-130">Chcete-li přidat dokompletování karty do **prostředí bash** pro rozhraní `.bashrc` příkazového příkazu .NET Core, přidejte do souboru následující kód:</span><span class="sxs-lookup"><span data-stu-id="5a801-130">To add tab completion to your **bash** shell for the .NET Core CLI, add the following code to your `.bashrc` file:</span></span>

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

## <a name="zsh"></a><span data-ttu-id="5a801-131">Zsh</span><span class="sxs-lookup"><span data-stu-id="5a801-131">zsh</span></span>

<span data-ttu-id="5a801-132">Chcete-li přidat doplnění karty do **prostředí zsh** pro rozhraní příkazového příkazu .NET Core, přidejte do `.zshrc` souboru následující kód:</span><span class="sxs-lookup"><span data-stu-id="5a801-132">To add tab completion to your **zsh** shell for the .NET Core CLI, add the following code to your `.zshrc` file:</span></span>

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete()
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```
