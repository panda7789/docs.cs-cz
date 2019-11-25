---
title: Postup nastavení proměnných prostředí pro příkazový řádek sady Visual Studio
ms.date: 09/29/2017
f1_keywords:
- cs.build.commandline
helpviewer_keywords:
- csc.exe, command-line builds
- Visual C#, command-line builds
- command-line compilers, Visual C#
- Vsvars32.bat
- builds [C#], command-line
- compilers, invoking from command line
- Vcvars32.bat file
- command line [C#], building from
- Visual C# compiler, enabling
- compiling source code, from command line
ms.assetid: 7ec09480-5612-4f6a-8d00-ad90ea9bca5d
ms.openlocfilehash: 3b69a92d28663bbbd34245435a69aea80d20fdc9
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73972833"
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a>Postup nastavení proměnných prostředí pro příkazový řádek sady Visual Studio

Soubor VsDevCmd. bat nastaví příslušné proměnné prostředí pro povolení sestavení příkazového řádku.

> [!NOTE]
> Soubor VsDevCmd. bat je nový soubor dodávaný se sadou Visual Studio 2017. Visual Studio 2015 a starší verze používaly VSVARS32. bat pro stejný účel. Tento soubor byl uložen ve složce \Program Files\Microsoft Visual Studio\\*verze*\Common7\Tools nebo Program Files (x86) \Microsoft visual Studio\\*verze*\Common7\Tools.

Pokud je aktuální verze sady Visual Studio nainstalována na počítači, který má také starší verzi sady Visual Studio, neměli byste spouštět VsDevCmd. bat a VSVARS32. BAT z různých verzí ve stejném okně příkazového řádku. Místo toho byste měli spustit příkaz pro každou verzi ve vlastním okně.

### <a name="to-run-vsdevcmdbat"></a>Spuštění VsDevCmd. BAT

1. V nabídce **Start** otevřete **Developer Command Prompt pro vs 2017**.  Je ve složce **Visual Studio 2017** .

2. Přejděte do složky \Program Files\Microsoft Visual Studio\\*verze*\\*nabídce*\Common7\Tools nebo \Program Files (x86) \Microsoft visual Studio\\*verze*\\*Nabídka*\Common7\Tools podadresář instalace.  (*Verze* je *2017* pro aktuální verzi. *Nabídka* je jedním z firem *Enterprise*, *Professional* nebo *Community*.)

3. Spusťte VsDevCmd. bat zadáním **VsDevCmd**.

    > [!CAUTION]
    > VsDevCmd. bat se může lišit od počítače k počítači. Neměňte chybějící nebo poškozený soubor VsDevCmd. bat s příponou VsDevCmd. bat z jiného počítače. Namísto toho nahraďte chybějící soubor opětovným spuštěním instalačního programu.

### <a name="available-options-for-vsdevcmdbat"></a>Dostupné možnosti pro VsDevCmd. BAT

Pokud chcete zobrazit dostupné možnosti pro VsDevCmd. BAT, spusťte příkaz s možností `-help`:

```console
VsDevCmd.bat -help
```

## <a name="see-also"></a>Viz také:

- [Sestavování pomocí programu csc.exe v příkazovém řádku](./command-line-building-with-csc-exe.md)
