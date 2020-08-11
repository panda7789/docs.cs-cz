---
title: Povolení dokončování pomocí tabulátoru
description: V tomto článku se naučíte, jak povolit dokončování karet pro .NET Core CLI pro PowerShell, bash a zsh.
author: adegeo
ms.author: adegeo
ms.topic: how-to
ms.date: 11/03/2019
ms.openlocfilehash: cd46305b8cd82825671a3a1568e8b93de1bbab26
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062805"
---
# <a name="how-to-enable-tab-completion-for-the-net-core-cli"></a>Jak povolit dokončování karet pro .NET Core CLI

**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí

Tento článek popisuje, jak nakonfigurovat dokončování karet pro tři prostředí, PowerShell, bash a zsh. Další prostředí naleznete v dokumentaci ke konfiguraci dokončování karet.

Po nastavení se aktivuje doplňování tabulátoru pro .NET Core CLI zadáním `dotnet` příkazu do prostředí a následným stisknutím klávesy TAB. Do příkazu se pošle aktuální příkazový řádek `dotnet complete` a výsledky se zpracují ve vašem prostředí. Výsledky můžete testovat bez aktivace tabulátoru odesláním nějakého přímo do `dotnet complete` příkazu. Příklad:

```console
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

Pokud tento příkaz nefunguje, ujistěte se, že je nainstalovaná sada .NET Core 2,0 SDK nebo novější. Pokud je nainstalován, ale tento příkaz stále nefunguje, ujistěte se, že `dotnet` příkaz překládá na verzi .NET Core 2,0 SDK a vyšší. Pomocí `dotnet --version` příkazu zjistíte, která verze `dotnet` vaší aktuální cesty se překládá na. Další informace najdete v tématu [Výběr verze rozhraní .NET Core, která se má použít](../versions/selection.md).

### <a name="examples"></a>Příklady

Tady je několik příkladů, které doplňování karet nabízí:

Vstup                                | stane                                                                     | vzhledem k tomu, že klienti
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | `add`je první dílčí příkaz abecedně.
`dotnet add p⇥`                      | `dotnet add --help`                                                          | Doplňování tabulátoru odpovídá podřetězcům a je uvedeno `--help` první abecedně.
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | Další návrh zobrazíte stisknutím klávesy TAB a podruhé.
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | Výsledky se vrátí abecedně.
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | Dokončování karet je soubor projektu s podporou.

## <a name="powershell"></a>PowerShell

Pokud chcete do **PowerShellu** přidat doplňování tabulátoru pro .NET Core CLI, vytvořte nebo upravte profil uložený v proměnné `$PROFILE` . Další informace najdete v tématu [jak vytvořit profil](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) a profily a [zásady spouštění](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy).

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

Chcete-li do prostředí **bash** pro .NET Core CLI přidat doplňování tabulátoru, přidejte do souboru následující kód `.bashrc` :

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

Chcete-li do prostředí **ZSH** pro .NET Core CLI přidat doplňování tabulátoru, přidejte do souboru následující kód `.zshrc` :

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete()
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```
