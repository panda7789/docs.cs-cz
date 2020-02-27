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
# <a name="how-to-enable-tab-completion-for-the-net-core-cli"></a>Jak povolit dokončování karet pro .NET Core CLI

**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí

Tento článek popisuje, jak nakonfigurovat dokončování karet pro tři prostředí, PowerShell, bash a zsh. Další prostředí naleznete v dokumentaci ke konfiguraci dokončování karet.

Po nastavení se aktivace karty .NET Core CLI aktivuje zadáním příkazu `dotnet` v prostředí a následným stisknutím klávesy TAB. Aktuální příkazový řádek se odešle do příkazu `dotnet complete` a výsledky se zpracují ve vašem prostředí. Výsledky můžete testovat bez aktivace tabulátoru odesláním nějakého přímo do příkazu `dotnet complete`. Příklad:

```console
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

Pokud tento příkaz nefunguje, ujistěte se, že je nainstalovaná sada .NET Core 2,0 SDK nebo novější. Pokud je nainstalován, ale tento příkaz stále nefunguje, ujistěte se, že příkaz `dotnet` překládá na verzi .NET Core 2,0 SDK a vyšší. Pomocí příkazu `dotnet --version` můžete zjistit, jakou verzi `dotnet` vaše aktuální cesta překládá. Další informace najdete v tématu [Výběr verze rozhraní .NET Core, která se má použít](../versions/selection.md).

### <a name="examples"></a>Příklady

Tady je několik příkladů, které doplňování karet nabízí:

Vstup                                | stane                                                                     | tím
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | `add` je první dílčí příkaz abecedně.
`dotnet add p⇥`                      | `dotnet add --help`                                                          | Doplňování tabulátoru odpovídá podřetězcům a `--help` je první abecedně.
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | Další návrh zobrazíte stisknutím klávesy TAB a podruhé.      
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | Výsledky se vrátí abecedně.
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | Dokončování karet je soubor projektu s podporou.

## <a name="powershell"></a>PowerShell

Pokud chcete pro .NET Core CLI přidat do **PowerShellu** tabulátor, vytvořte nebo upravte profil uložený v proměnné `$PROFILE`. Další informace najdete v tématu [jak vytvořit profil](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) a profily a [zásady spouštění](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy). 

Do svého profilu přidejte následující kód:

```powershell
# PowerShell parameter completion shim for the dotnet CLI 
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock {
     param($commandName, $wordToComplete, $cursorPosition)
         dotnet complete --position $cursorPosition "$wordToComplete" | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
         }
 }
```

## <a name="bash"></a>bash

Chcete-li do prostředí **bash** pro .NET Core CLI přidat doplňování tabulátoru, přidejte do souboru `.bashrc` následující kód:

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

## <a name="zsh"></a>zsh

Chcete-li do prostředí **ZSH** pro .NET Core CLI přidat doplňování tabulátoru, přidejte do souboru `.zshrc` následující kód:

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete() 
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```
