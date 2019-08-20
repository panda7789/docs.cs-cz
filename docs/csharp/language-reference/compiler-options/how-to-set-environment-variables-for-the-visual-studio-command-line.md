---
title: 'Postupy: Nastavení proměnných prostředí pro příkazový řádek Visual Studia'
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
ms.openlocfilehash: 9b26f6b80488ad4043054cd23f0f351773e8d6d1
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602852"
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a>Postupy: Nastavení proměnných prostředí pro příkazový řádek Visual Studia

Soubor VsDevCmd. bat nastaví příslušné proměnné prostředí pro povolení sestavení příkazového řádku.

> [!NOTE]
> Soubor VsDevCmd. bat je nový soubor dodávaný se sadou Visual Studio 2017. Visual Studio 2015 a starší verze používaly VSVARS32. bat pro stejný účel. Tento soubor byl uložen ve složce \Program Files\Microsoft Visual\\Studio*Version*\Common7\Tools nebo Program Files (x86) \Microsoft Visual\\Studio*verze*\Common7\Tools.

Pokud je aktuální verze sady Visual Studio nainstalována na počítači, který má také starší verzi sady Visual Studio, neměli byste spouštět VsDevCmd. bat a VSVARS32. BAT z různých verzí ve stejném okně příkazového řádku. Místo toho byste měli spustit příkaz pro každou verzi ve vlastním okně.

### <a name="to-run-vsdevcmdbat"></a>Spuštění VsDevCmd. BAT

1. V nabídce **Start** otevřete **Developer Command Prompt pro vs 2017**.  Je ve složce **Visual Studio 2017** .

2. Přejděte na\\*verzi*\\\\\Program Files\Microsoft Visual Studio, která nabízí \Common7\Tools nebo \Program Files (x86) \Microsoft Visual Studio version nabídky\\\Common7\Tools podadresář instalace.  (*Verze* je *2017* pro aktuální verzi. *Nabídka* je jedním z firem *Enterprise*, *Professional* nebo *Community*.)

3. Spusťte VsDevCmd. bat zadáním **VsDevCmd**.

    > [!CAUTION]
    > VsDevCmd. bat se může lišit od počítače k počítači. Neměňte chybějící nebo poškozený soubor VsDevCmd. bat s příponou VsDevCmd. bat z jiného počítače. Namísto toho nahraďte chybějící soubor opětovným spuštěním instalačního programu.

### <a name="available-options-for-vsdevcmdbat"></a>Dostupné možnosti pro VsDevCmd. BAT

Pokud chcete zobrazit dostupné možnosti pro VsDevCmd. bat, spusťte příkaz s `-help` možností:

```console
VsDevCmd.bat -help
```

## <a name="see-also"></a>Viz také:

- [Sestavování pomocí programu csc.exe v příkazovém řádku](./command-line-building-with-csc-exe.md)
