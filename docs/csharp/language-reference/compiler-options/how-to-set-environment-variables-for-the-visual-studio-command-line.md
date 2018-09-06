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
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43857846"
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a><span data-ttu-id="52682-102">Postup: Nastavení proměnných prostředí pro příkazový řádek sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="52682-102">How to: Set Environment Variables for the Visual Studio Command Line</span></span>

<span data-ttu-id="52682-103">Soubor VsDevCmd.bat nastaví příslušné proměnné prostředí povolit sestavení příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="52682-103">The VsDevCmd.bat file sets the appropriate environment variables to enable command-line builds.</span></span> <span data-ttu-id="52682-104">Další informace o VsDevCmd.bat najdete v tématu [článku Q248802 znalostní báze](https://support.microsoft.com/help/248802/you-receive-the-out-of-environment-space-error-message-when-you-execut).</span><span class="sxs-lookup"><span data-stu-id="52682-104">For more information about VsDevCmd.bat, see [Knowledge Base article Q248802](https://support.microsoft.com/help/248802/you-receive-the-out-of-environment-space-error-message-when-you-execut).</span></span>  

> [!NOTE]
> <span data-ttu-id="52682-105">Soubor VsDevCmd.bat je nový soubor dodávají s Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="52682-105">The VsDevCmd.bat file is a new file delivered with Visual Studio 2017.</span></span> <span data-ttu-id="52682-106">Visual Studio 2015 a starší používala VSVARS32.bat ke stejnému účelu.</span><span class="sxs-lookup"><span data-stu-id="52682-106">Visual Studio 2015 and earlier versions used VSVARS32.bat for the same purpose.</span></span> <span data-ttu-id="52682-107">Tento soubor byl uložen v sadě Visual Studio \Program Files\Microsoft\\*verze*\Common7\Tools nebo Program Files (x86) \Microsoft Visual Studio\\*verze*\Common7\Tools.</span><span class="sxs-lookup"><span data-stu-id="52682-107">This file was stored in \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.</span></span>
  
<span data-ttu-id="52682-108">Pokud na počítači, který také používá starší verzi sady Visual Studio je nainstalovaná aktuální verze sady Visual Studio, byste neměli spouštět VsDevCmd.bat a VSVARS32. SPOLEHNUTÍ z různých verzí ve stejném okně příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="52682-108">If the current version of Visual Studio is installed on a computer that also has an earlier version of Visual Studio, you should not run VsDevCmd.bat and VSVARS32.BAT from different versions in the same Command Prompt window.</span></span> <span data-ttu-id="52682-109">Místo toho by měl spustit příkaz pro každou verzi v samostatném okně.</span><span class="sxs-lookup"><span data-stu-id="52682-109">Instead, you should run the command for each version in its own window.</span></span>
  
### <a name="to-run-vsdevcmdbat"></a><span data-ttu-id="52682-110">Ke spuštění VsDevCmd.BAT</span><span class="sxs-lookup"><span data-stu-id="52682-110">To run VsDevCmd.BAT</span></span>  
  
1.  <span data-ttu-id="52682-111">Z **Start** nabídky, otevřete **Developer Command Prompt for VS 2017**.</span><span class="sxs-lookup"><span data-stu-id="52682-111">From the **Start** menu, open the **Developer Command Prompt for VS 2017**.</span></span>  <span data-ttu-id="52682-112">Je **Visual Studio 2017** složky.</span><span class="sxs-lookup"><span data-stu-id="52682-112">It's in the **Visual Studio 2017** folder.</span></span>
  
2.  <span data-ttu-id="52682-113">Změňte na \Program Files\Microsoft Visual Studio\\*verze*\\*nabídky*\Common7\Tools nebo \Program soubory (x86) \Microsoft Visual Studio\\ *Verze*\\*nabídky*\Common7\Tools podadresář instalace.</span><span class="sxs-lookup"><span data-stu-id="52682-113">Change to the \Program Files\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools or \Program Files (x86)\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools subdirectory of your installation.</span></span>  <span data-ttu-id="52682-114">(*Verze* je *2017* pro aktuální verzi.</span><span class="sxs-lookup"><span data-stu-id="52682-114">(*Version* is *2017* for the current version.</span></span> <span data-ttu-id="52682-115">*Nabídka* je jedním z *Enterprise*, *Professional* nebo *komunity*.)</span><span class="sxs-lookup"><span data-stu-id="52682-115">*Offering* is one of *Enterprise*, *Professional* or *Community*.)</span></span>
  
3.  <span data-ttu-id="52682-116">Spusťte VsDevCmd.bat zadáním **VsDevCmd**.</span><span class="sxs-lookup"><span data-stu-id="52682-116">Run VsDevCmd.bat by typing **VsDevCmd**.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="52682-117">VsDevCmd.bat se může lišit od počítače na počítač.</span><span class="sxs-lookup"><span data-stu-id="52682-117">VsDevCmd.bat can vary from computer to computer.</span></span> <span data-ttu-id="52682-118">Nenahrazujte VsDevCmd.bat z jiného počítače VsDevCmd.bat soubor chybí nebo je poškozen.</span><span class="sxs-lookup"><span data-stu-id="52682-118">Do not replace a missing or damaged VsDevCmd.bat file with a VsDevCmd.bat from another computer.</span></span> <span data-ttu-id="52682-119">Namísto toho nahraďte chybějící soubor opětovným spuštěním instalačního programu.</span><span class="sxs-lookup"><span data-stu-id="52682-119">Instead, rerun setup to replace the missing file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52682-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="52682-120">See Also</span></span>  

- [<span data-ttu-id="52682-121">Sestavování pomocí programu csc.exe v příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="52682-121">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
