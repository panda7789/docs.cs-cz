---
title: "Postup: Nastavení proměnných prostředí pro příkazový řádek sady Visual Studio"
ms.date: 09/29/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
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
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 298006629bedf33e4d2521a88c010fcce824585c
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2018
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a>Postup: Nastavení proměnných prostředí pro příkazový řádek sady Visual Studio

Soubor VsDevCmd.bat nastaví příslušné proměnné prostředí příkazovém řádku. Další informace o VsDevCmd.bat najdete v tématu [článku znalostní báze Q248802](https://support.microsoft.com/help/248802/you-receive-the-out-of-environment-space-error-message-when-you-execut).  

> [!NOTE]
> Soubor VsDevCmd.bat je nový soubor s Visual Studio 2017 doručit. Visual Studio 2015 a starší verze použít VSVARS32.bat k tomuto účelu. Tento soubor byla uložená v sadě Visual Studio \Program Files\Microsoft\\*verze*\Common7\Tools nebo Program Files (x86) \Microsoft Visual Studio\\*verze*\Common7\Tools.
  
Pokud je aktuální verze sady Visual Studio nainstalovaná na počítači, který má také starší verze sady Visual Studio, nespouštějte VsDevCmd.bat a VSVARS32. BAT z různých verzí ve stejném okně příkazového řádku. Místo toho byste měli spustit příkaz pro každou verzi v samostatném okně.
  
### <a name="to-run-vsdevcmdbat"></a>Ke spuštění VsDevCmd.BAT  
  
1.  Z **spustit** nabídky, otevřete **příkazový řádek vývojáře pro VS 2017**.  Je v **Visual Studio 2017** složky.
  
2.  Změnit na \Program Files\Microsoft Visual Studio\\*verze*\\*nabídky*\Common7\Tools nebo \Program soubory (x86) \Microsoft Visual Studio\\ *Verze*\\*nabídky*\Common7\Tools podadresáři instalace.  (*Verze* je *2017* pro aktuální verzi. *Nabídka* je jedním z *Enterprise*, *Professional* nebo *komunity*.)
  
3.  Spustit VsDevCmd.bat zadáním **VsDevCmd**.  
  
    > [!CAUTION]
    >  VsDevCmd.bat se může lišit od počítače na počítač. Nepřepisovat existující soubor nebo je poškozena VsDevCmd.bat s VsDevCmd.bat z jiného počítače. Namísto toho nahraďte chybějící soubor opětovným spuštěním instalačního programu.  
  
## <a name="see-also"></a>Viz také  
 [Sestavování pomocí programu csc.exe v příkazovém řádku](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
