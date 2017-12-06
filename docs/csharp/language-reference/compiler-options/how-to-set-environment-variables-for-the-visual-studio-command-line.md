---
title: "Postup: Nastavení proměnných prostředí pro příkazový řádek sady Visual Studio"
ms.date: 09-29-2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: cs.build.commandline
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
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: afab503719f67cf7ad1762370ed3062e12ad88e9
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/06/2017
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a><span data-ttu-id="8eedb-102">Postup: Nastavení proměnných prostředí pro příkazový řádek sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8eedb-102">How to: Set Environment Variables for the Visual Studio Command Line</span></span>

<span data-ttu-id="8eedb-103">Soubor VsDevCmd.bat nastaví příslušné proměnné prostředí příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="8eedb-103">The VsDevCmd.bat file sets the appropriate environment variables to enable command-line builds.</span></span> <span data-ttu-id="8eedb-104">Další informace o VsDevCmd.bat najdete v tématu [článku znalostní báze Q248802](https://support.microsoft.com/help/248802/you-receive-the-out-of-environment-space-error-message-when-you-execut).</span><span class="sxs-lookup"><span data-stu-id="8eedb-104">For more information about VsDevCmd.bat, see [Knowledge Base article Q248802](https://support.microsoft.com/help/248802/you-receive-the-out-of-environment-space-error-message-when-you-execut).</span></span>  

> [!NOTE]
> <span data-ttu-id="8eedb-105">Soubor VsDevCmd.bat je nový soubor s Visual Studio 2017 doručit.</span><span class="sxs-lookup"><span data-stu-id="8eedb-105">The VsDevCmd.bat file is a new file delivered with Visual Studio 2017.</span></span> <span data-ttu-id="8eedb-106">Visual Studio 2015 a starší verze použít VSVARS32.bat k tomuto účelu.</span><span class="sxs-lookup"><span data-stu-id="8eedb-106">Visual Studio 2015 and earlier versions used VSVARS32.bat for the same purpose.</span></span> <span data-ttu-id="8eedb-107">Tento soubor byla uložená v sadě Visual Studio \Program Files\Microsoft\\*verze*\Common7\Tools nebo Program Files (x86) \Microsoft Visual Studio\\*verze*\Common7\Tools.</span><span class="sxs-lookup"><span data-stu-id="8eedb-107">This file was stored in \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.</span></span>
  
<span data-ttu-id="8eedb-108">Pokud je aktuální verze sady Visual Studio nainstalovaná na počítači, který má také starší verze sady Visual Studio, nespouštějte VsDevCmd.bat a VSVARS32. BAT z různých verzí ve stejném okně příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="8eedb-108">If the current version of Visual Studio is installed on a computer that also has an earlier version of Visual Studio, you should not run VsDevCmd.bat and VSVARS32.BAT from different versions in the same Command Prompt window.</span></span> <span data-ttu-id="8eedb-109">Místo toho byste měli spustit příkaz pro každou verzi v samostatném okně.</span><span class="sxs-lookup"><span data-stu-id="8eedb-109">Instead, you should run the command for each version in its own window.</span></span>
  
### <a name="to-run-vsdevcmdbat"></a><span data-ttu-id="8eedb-110">Ke spuštění VsDevCmd.BAT</span><span class="sxs-lookup"><span data-stu-id="8eedb-110">To run VsDevCmd.BAT</span></span>  
  
1.  <span data-ttu-id="8eedb-111">Z **spustit** nabídky, otevřete **příkazový řádek vývojáře pro VS 2017**.</span><span class="sxs-lookup"><span data-stu-id="8eedb-111">From the **Start** menu, open the **Developer Command Prompt for VS 2017**.</span></span>  <span data-ttu-id="8eedb-112">Je v **Visual Studio 2017** složky.</span><span class="sxs-lookup"><span data-stu-id="8eedb-112">It's in the **Visual Studio 2017** folder.</span></span>
  
2.  <span data-ttu-id="8eedb-113">Změnit na \Program Files\Microsoft Visual Studio\\*verze*\\*nabídky*\Common7\Tools nebo \Program soubory (x86) \Microsoft Visual Studio\\ *Verze*\\*nabídky*\Common7\Tools podadresáři instalace.</span><span class="sxs-lookup"><span data-stu-id="8eedb-113">Change to the \Program Files\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools or \Program Files (x86)\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools subdirectory of your installation.</span></span>  <span data-ttu-id="8eedb-114">(*Verze* je *2017* pro aktuální verzi.</span><span class="sxs-lookup"><span data-stu-id="8eedb-114">(*Version* is *2017* for the current version.</span></span> <span data-ttu-id="8eedb-115">*Nabídka* je jedním z *Enterprise*, *Professional* nebo *komunity*.)</span><span class="sxs-lookup"><span data-stu-id="8eedb-115">*Offering* is one of *Enterprise*, *Professional* or *Community*.)</span></span>
  
3.  <span data-ttu-id="8eedb-116">Spustit VsDevCmd.bat zadáním **VsDevCmd**.</span><span class="sxs-lookup"><span data-stu-id="8eedb-116">Run VsDevCmd.bat by typing **VsDevCmd**.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="8eedb-117">VsDevCmd.bat se může lišit od počítače na počítač.</span><span class="sxs-lookup"><span data-stu-id="8eedb-117">VsDevCmd.bat can vary from computer to computer.</span></span> <span data-ttu-id="8eedb-118">Nepřepisovat existující soubor nebo je poškozena VsDevCmd.bat s VsDevCmd.bat z jiného počítače.</span><span class="sxs-lookup"><span data-stu-id="8eedb-118">Do not replace a missing or damaged VsDevCmd.bat file with a VsDevCmd.bat from another computer.</span></span> <span data-ttu-id="8eedb-119">Namísto toho nahraďte chybějící soubor opětovným spuštěním instalačního programu.</span><span class="sxs-lookup"><span data-stu-id="8eedb-119">Instead, rerun setup to replace the missing file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eedb-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="8eedb-120">See Also</span></span>  
 [<span data-ttu-id="8eedb-121">Sestavování pomocí csc.exe</span><span class="sxs-lookup"><span data-stu-id="8eedb-121">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
