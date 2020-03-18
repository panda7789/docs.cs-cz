---
title: Jak nastavit proměnné prostředí pro příkazový řádek sady Visual Studio
ms.date: 12/20/2019
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
ms.openlocfilehash: 99e2a837877494dd4c7e0106047bce3cc39a9282
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75342368"
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a><span data-ttu-id="cde15-102">Jak nastavit proměnné prostředí pro příkazový řádek sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cde15-102">How to set environment variables for the Visual Studio Command Line</span></span>

<span data-ttu-id="cde15-103">Soubor VsDevCmd.bat nastaví příslušné proměnné prostředí pro povolení sestavení příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="cde15-103">The VsDevCmd.bat file sets the appropriate environment variables to enable command-line builds.</span></span>

> [!NOTE]
> <span data-ttu-id="cde15-104">Visual Studio 2015 a starší verze používají VSVARS32.bat, ne VsDevCmd.bat pro stejný účel.</span><span class="sxs-lookup"><span data-stu-id="cde15-104">Visual Studio 2015 and earlier versions used VSVARS32.bat, not VsDevCmd.bat for the same purpose.</span></span> <span data-ttu-id="cde15-105">Tento soubor byl uložen v \Program\\Files\Microsoft Visual Studio*Version*\Common7\Tools or\\Program Files (x86)\Microsoft Visual Studio*Version*\Common7\Tools.</span><span class="sxs-lookup"><span data-stu-id="cde15-105">This file was stored in \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.</span></span>

<span data-ttu-id="cde15-106">Pokud je aktuální verze sady Visual Studio nainstalována v počítači, který má také starší verzi sady Visual Studio, neměli byste spouštět VsDevCmd.bat a VSVARS32. BAT z různých verzí ve stejném okně příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="cde15-106">If the current version of Visual Studio is installed on a computer that also has an earlier version of Visual Studio, you should not run VsDevCmd.bat and VSVARS32.BAT from different versions in the same Command Prompt window.</span></span> <span data-ttu-id="cde15-107">Místo toho byste měli spustit příkaz pro každou verzi ve vlastním okně.</span><span class="sxs-lookup"><span data-stu-id="cde15-107">Instead, you should run the command for each version in its own window.</span></span>

### <a name="to-run-vsdevcmdbat"></a><span data-ttu-id="cde15-108">Spuštění souboru VsDevCmd.BAT</span><span class="sxs-lookup"><span data-stu-id="cde15-108">To run VsDevCmd.BAT</span></span>

1. <span data-ttu-id="cde15-109">V nabídce **Start** otevřete **příkazový řádek pro vývojáře pro VS 2019**.</span><span class="sxs-lookup"><span data-stu-id="cde15-109">From the **Start** menu, open the **Developer Command Prompt for VS 2019**.</span></span>  <span data-ttu-id="cde15-110">Je ve složce **Visual Studio 2019.**</span><span class="sxs-lookup"><span data-stu-id="cde15-110">It's in the **Visual Studio 2019** folder.</span></span>

2. <span data-ttu-id="cde15-111">Změňte na \Program Files\Microsoft\\Visual Studio*Version*\\*Offering*\Common7\Tools or \Program\\Files (x86)\Microsoft Visual Studio*Version*\\*Offering*\Common7\Tools subdirectory aplikace Installation.</span><span class="sxs-lookup"><span data-stu-id="cde15-111">Change to the \Program Files\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools or \Program Files (x86)\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools subdirectory of your installation.</span></span>  <span data-ttu-id="cde15-112">(*Verze* je *2019* pro aktuální verzi.</span><span class="sxs-lookup"><span data-stu-id="cde15-112">(*Version* is *2019* for the current version.</span></span> <span data-ttu-id="cde15-113">*Nabídka* je jedním z *Enterprise*, *Professional* nebo *Společenství*.)</span><span class="sxs-lookup"><span data-stu-id="cde15-113">*Offering* is one of *Enterprise*, *Professional* or *Community*.)</span></span>

3. <span data-ttu-id="cde15-114">Spusťte VsDevCmd.bat zadáním **VsDevCmd**.</span><span class="sxs-lookup"><span data-stu-id="cde15-114">Run VsDevCmd.bat by typing **VsDevCmd**.</span></span>

    > [!CAUTION]
    > <span data-ttu-id="cde15-115">VsDevCmd.bat se může lišit od počítače k počítači.</span><span class="sxs-lookup"><span data-stu-id="cde15-115">VsDevCmd.bat can vary from computer to computer.</span></span> <span data-ttu-id="cde15-116">Nenahrazujte chybějící nebo poškozený soubor VsDevCmd.bat souborem VsDevCmd.bat z jiného počítače.</span><span class="sxs-lookup"><span data-stu-id="cde15-116">Do not replace a missing or damaged VsDevCmd.bat file with a VsDevCmd.bat from another computer.</span></span> <span data-ttu-id="cde15-117">Namísto toho nahraďte chybějící soubor opětovným spuštěním instalačního programu.</span><span class="sxs-lookup"><span data-stu-id="cde15-117">Instead, rerun setup to replace the missing file.</span></span>

### <a name="available-options-for-vsdevcmdbat"></a><span data-ttu-id="cde15-118">Dostupné možnosti pro VsDevCmd.BAT</span><span class="sxs-lookup"><span data-stu-id="cde15-118">Available options for VsDevCmd.BAT</span></span>

<span data-ttu-id="cde15-119">Chcete-li zobrazit dostupné možnosti pro VsDevCmd.BAT, spusťte příkaz s `-help` možností:</span><span class="sxs-lookup"><span data-stu-id="cde15-119">To see the available options for VsDevCmd.BAT, run the command with the `-help` option:</span></span>

```console
VsDevCmd.bat -help
```

## <a name="see-also"></a><span data-ttu-id="cde15-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="cde15-120">See also</span></span>

- [<span data-ttu-id="cde15-121">Sestavování pomocí programu csc.exe v příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="cde15-121">Command-line Building With csc.exe</span></span>](./command-line-building-with-csc-exe.md)
