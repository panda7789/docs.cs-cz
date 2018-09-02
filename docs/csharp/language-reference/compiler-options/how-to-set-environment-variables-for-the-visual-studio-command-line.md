---
title: 'Postup: Nastavení proměnných prostředí pro příkazový řádek sady Visual Studio'
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
ms.openlocfilehash: 77375e428fe0563c0b533ca97abd21070e850682
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43466735"
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a>Postup: Nastavení proměnných prostředí pro příkazový řádek sady Visual Studio

Soubor VsDevCmd.bat nastaví příslušné proměnné prostředí povolit sestavení příkazového řádku. Další informace o VsDevCmd.bat najdete v tématu [článku Q248802 znalostní báze](https://support.microsoft.com/help/248802/you-receive-the-out-of-environment-space-error-message-when-you-execut).  

> [!NOTE]
> Soubor VsDevCmd.bat je nový soubor dodávají s Visual Studio 2017. Visual Studio 2015 a starší používala VSVARS32.bat ke stejnému účelu. Tento soubor byl uložen v sadě Visual Studio \Program Files\Microsoft\\*verze*\Common7\Tools nebo Program Files (x86) \Microsoft Visual Studio\\*verze*\Common7\Tools.
  
Pokud na počítači, který také používá starší verzi sady Visual Studio je nainstalovaná aktuální verze sady Visual Studio, byste neměli spouštět VsDevCmd.bat a VSVARS32. SPOLEHNUTÍ z různých verzí ve stejném okně příkazového řádku. Místo toho by měl spustit příkaz pro každou verzi v samostatném okně.
  
### <a name="to-run-vsdevcmdbat"></a>Ke spuštění VsDevCmd.BAT  
  
1.  Z **Start** nabídky, otevřete **Developer Command Prompt for VS 2017**.  Je **Visual Studio 2017** složky.
  
2.  Změňte na \Program Files\Microsoft Visual Studio\\*verze*\\*nabídky*\Common7\Tools nebo \Program soubory (x86) \Microsoft Visual Studio\\ *Verze*\\*nabídky*\Common7\Tools podadresář instalace.  (*Verze* je *2017* pro aktuální verzi. *Nabídka* je jedním z *Enterprise*, *Professional* nebo *komunity*.)
  
3.  Spusťte VsDevCmd.bat zadáním **VsDevCmd**.  
  
    > [!CAUTION]
    >  VsDevCmd.bat se může lišit od počítače na počítač. Nenahrazujte VsDevCmd.bat z jiného počítače VsDevCmd.bat soubor chybí nebo je poškozen. Namísto toho nahraďte chybějící soubor opětovným spuštěním instalačního programu.  
  
## <a name="see-also"></a>Viz také  

- [Sestavování pomocí programu csc.exe v příkazovém řádku](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
