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
# <a name="how-to-enable-tab-completion-for-the-net-core-cli"></a>Povolení dokončování polí TAB pro rozhraní CLI jádra .NET

**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze

Tento článek popisuje, jak nakonfigurovat dokončení karty pro tři prostředí, PowerShell, Bash a zsh. Další prostředí naleznete v jejich dokumentaci o konfiguraci dokončení karty.

Po nastavení se dokončení karty pro rozhraní příkazového příkazu `dotnet` .NET Core spustí zadáním příkazu do prostředí a stisknutím klávesy TAB. Aktuální příkazový řádek je `dotnet complete` odeslán do příkazu a výsledky jsou zpracovány prostředím. Výsledky můžete otestovat bez povolení dokončení karty `dotnet complete` odesláním něco přímo do příkazu. Například:

```console
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

Pokud tento příkaz nefunguje, ujistěte se, že je nainstalována sada .NET Core 2.0 SDK nebo vyšší. Pokud je nainstalován, ale tento příkaz stále nefunguje, `dotnet` ujistěte se, že příkaz překládá na verzi sady .NET Core 2.0 SDK a vyšší. Pomocí `dotnet --version` příkazu můžete zjistit, na jakou `dotnet` verzi aktuální cesty se pracuje. Další informace naleznete [v tématu Select the .NET Core version to use](../versions/selection.md).

### <a name="examples"></a>Příklady

Zde je několik příkladů, co poskytuje dokončení karty:

Vstup                                | se stává                                                                     | vzhledem k tomu, že klienti
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | `add`je první podpříkaz, abecedně.
`dotnet add p⇥`                      | `dotnet add --help`                                                          | Dokončení tabulátoru `--help` odpovídá podřetězcům a je na prvním místě abecedně.
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | Stisknutím klávesy tab podruhé vyvoláte další návrh.
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | Výsledky jsou vráceny abecedně.
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | Dokončení karty je vědoma souboru projektu.

## <a name="powershell"></a>PowerShell

Chcete-li do **prostředí PowerShell** přidat doplnění karty pro rozhraní PŘÍKAZOVÉHO `$PROFILE`PŘÍKAZU jádra rozhraní .NET, vytvořte nebo upravte profil uložený v proměnné . Další informace naleznete v tématu [Jak vytvořit profil](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) a [profily a zásady provádění](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy).

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

Chcete-li přidat dokompletování karty do **prostředí bash** pro rozhraní `.bashrc` příkazového příkazu .NET Core, přidejte do souboru následující kód:

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

## <a name="zsh"></a>Zsh

Chcete-li přidat doplnění karty do **prostředí zsh** pro rozhraní příkazového příkazu .NET Core, přidejte do `.zshrc` souboru následující kód:

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete()
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```
