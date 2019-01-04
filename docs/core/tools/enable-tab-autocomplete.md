---
title: Povolení dokončování pomocí tabulátoru
description: V tomto článku se naučíte, jak povolení dokončování pomocí tabulátoru pro rozhraní příkazového řádku .NET Core pro PowerShell, Bash a zsh.
author: thraka
ms.author: adegeo
ms.date: 12/17/2018
ms.openlocfilehash: 783868fb8300dd4a25c62a108c1c0f7a485721df
ms.sourcegitcommit: 3b9b7ae6771712337d40374d2fef6b25b0d53df6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/04/2019
ms.locfileid: "54029603"
---
# <a name="how-to-enable-tab-completion-for-net-core-cli"></a>Povolení dokončování pomocí TABULÁTORU pro rozhraní příkazového řádku .NET Core

Počínaje .NET Core 2.0 SDK, rozhraní příkazového řádku .NET Core podporuje dokončování pomocí tabulátoru. Tento článek popisuje, jak nakonfigurovat dokončování pomocí tabulátoru pro tři prostředí PowerShell, Bash a zsh. Další prostředí může mít podporu pro automatické dokončování. Přečtěte si jejich dokumentaci o tom, jak nakonfigurovat automatické doplňování, kroky by měl být podobný postup popsaný v tomto článku.

[!INCLUDE [topic-appliesto-net-core-2plus](~/includes/topic-appliesto-net-core-2plus.md)]

Po nastavení dokončování pomocí tabulátoru pro rozhraní příkazového řádku .NET Core se aktivuje zadáním `dotnet ` příkazu v prostředí a potom stisknutí klávesy TAB. Aktuální příkaz řádek se odešle do `dotnet complete` příkazu a výsledky se zpracovávají ve vašem prostředí. Můžete testovat výsledky bez povolení dokončování pomocí tabulátoru odesláním něco přímo `dotnet complete` příkazu. Příklad:

```
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

Pokud tento příkaz nefunguje, ujistěte se, že sada .NET Core 2.0 SDK nebo vyšší než je nainstalována. Pokud je nainstalovaná, ale tohoto příkazu stále nefunguje, ujistěte se, že `dotnet` příkaz překládá na verzi .NET Core 2.0 SDK a vyšší. Použití `dotnet --version` příkazu zobrazte jakou verzi `dotnet` správně směřuje aktuální cestě. Další informace najdete v tématu [vyberte verzi .NET Core používat](../versions/selection.md).

### <a name="examples"></a>Příklady

Tady je několik příkladů poskytuje jaké tab k dokončování příkazů:

Vstup                                | změní                                                                     | protože
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | `add` je první podpříkaz podle abecedy.
`dotnet add p⇥`                      | `dotnet add --help`                                                          | Karta dokončení shody podřetězců a `--help` je první podle abecedy.
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | Stisknutím klávesy tab podruhé zobrazí další návrh.      
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | Výsledky jsou vráceny podle abecedy.
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | Dokončování pomocí tabulátoru je soubor projektu vědět.

## <a name="powershell"></a>PowerShell

Chcete-li přidat tab k dokončování příkazů do **PowerShell** pro rozhraní příkazového řádku .NET Core vytvořit nebo upravit profil uložen v proměnné `$PROFILE`. Další informace najdete v tématu [postup vytvoření profilu](/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-6#how-to-create-a-profile) a [profily a zásady spouštění](/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-6#profiles-and-execution-policy). 

Přidejte následující kód k vašemu profilu:

```powershell
# PowerShell parameter completion shim for the dotnet CLI 
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock {
     param($commandName, $wordToComplete, $cursorPosition)
         dotnet complete --position $cursorPosition "$wordToComplete" | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
         }
 }
```

## <a name="bash"></a>Bash

Přidání dokončování pomocí tabulátoru pro vaše **bash** prostředí pro rozhraní příkazového řádku .NET Core, přidejte následující kód, který vaše `.bashrc` souboru:

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

## <a name="zsh"></a>zsh

Přidání dokončování pomocí tabulátoru pro vaše **zsh** prostředí pro rozhraní příkazového řádku .NET Core, přidejte následující kód, který vaše `.zshrc` souboru:

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete() 
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```
