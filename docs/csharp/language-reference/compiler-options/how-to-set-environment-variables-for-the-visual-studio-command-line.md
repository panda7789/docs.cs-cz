---
description: Jak nastavit proměnné prostředí pro příkazový řádek sady Visual Studio
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
ms.openlocfilehash: b985c85e2fddce459ed68b3d07ba7d54a8b2d0a7
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125602"
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a><span data-ttu-id="95ca2-103">Jak nastavit proměnné prostředí pro příkazový řádek sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="95ca2-103">How to set environment variables for the Visual Studio Command Line</span></span>

<span data-ttu-id="95ca2-104">VsDevCmd.bat soubor nastaví příslušné proměnné prostředí pro povolení sestavení příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="95ca2-104">The VsDevCmd.bat file sets the appropriate environment variables to enable command-line builds.</span></span>

> [!NOTE]
> <span data-ttu-id="95ca2-105">V aplikaci Visual Studio 2015 a starších verzích se používá VSVARS32.bat, nikoli VsDevCmd.bat pro stejný účel.</span><span class="sxs-lookup"><span data-stu-id="95ca2-105">Visual Studio 2015 and earlier versions used VSVARS32.bat, not VsDevCmd.bat for the same purpose.</span></span> <span data-ttu-id="95ca2-106">Tento soubor byl uložen ve složce \Program Files\Microsoft Visual Studio \\ *Version*\Common7\Tools nebo Program Files (x86) \Microsoft Visual Studio \\ *verze*\Common7\Tools.</span><span class="sxs-lookup"><span data-stu-id="95ca2-106">This file was stored in \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.</span></span>

<span data-ttu-id="95ca2-107">Pokud je aktuální verze sady Visual Studio nainstalována na počítači, který má také starší verzi sady Visual Studio, neměli byste spouštět VsDevCmd.bat a VSVARS32.BAT z různých verzí v jednom okně příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="95ca2-107">If the current version of Visual Studio is installed on a computer that also has an earlier version of Visual Studio, you should not run VsDevCmd.bat and VSVARS32.BAT from different versions in the same Command Prompt window.</span></span> <span data-ttu-id="95ca2-108">Místo toho byste měli spustit příkaz pro každou verzi ve vlastním okně.</span><span class="sxs-lookup"><span data-stu-id="95ca2-108">Instead, you should run the command for each version in its own window.</span></span>

### <a name="to-run-vsdevcmdbat"></a><span data-ttu-id="95ca2-109">Spuštění VsDevCmd.BAT</span><span class="sxs-lookup"><span data-stu-id="95ca2-109">To run VsDevCmd.BAT</span></span>

1. <span data-ttu-id="95ca2-110">V nabídce **Start** otevřete **Developer Command Prompt pro vs 2019**.</span><span class="sxs-lookup"><span data-stu-id="95ca2-110">From the **Start** menu, open the **Developer Command Prompt for VS 2019**.</span></span>  <span data-ttu-id="95ca2-111">Je ve složce **Visual Studio 2019** .</span><span class="sxs-lookup"><span data-stu-id="95ca2-111">It's in the **Visual Studio 2019** folder.</span></span>

2. <span data-ttu-id="95ca2-112">Přejděte do složky \Program Files\Microsoft Visual Studio \\ *verze*, která \\ *nabízí*\Common7\Tools nebo \Program Files (x86) \Microsoft Visual Studio \\ *Version* \\ , která*nabízí*\Common7\Tools podadresář instalace.</span><span class="sxs-lookup"><span data-stu-id="95ca2-112">Change to the \Program Files\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools or \Program Files (x86)\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools subdirectory of your installation.</span></span>  <span data-ttu-id="95ca2-113">(*Verze* je *2019* pro aktuální verzi.</span><span class="sxs-lookup"><span data-stu-id="95ca2-113">(*Version* is *2019* for the current version.</span></span> <span data-ttu-id="95ca2-114">*Nabídka* je jedním z firem *Enterprise*, *Professional* nebo *Community*.)</span><span class="sxs-lookup"><span data-stu-id="95ca2-114">*Offering* is one of *Enterprise*, *Professional* or *Community*.)</span></span>

3. <span data-ttu-id="95ca2-115">Spusťte VsDevCmd.bat zadáním **VsDevCmd**.</span><span class="sxs-lookup"><span data-stu-id="95ca2-115">Run VsDevCmd.bat by typing **VsDevCmd**.</span></span>

    > [!CAUTION]
    > <span data-ttu-id="95ca2-116">VsDevCmd.bat se může v počítači lišit.</span><span class="sxs-lookup"><span data-stu-id="95ca2-116">VsDevCmd.bat can vary from computer to computer.</span></span> <span data-ttu-id="95ca2-117">Neměňte chybějící nebo poškozený soubor VsDevCmd.bat s VsDevCmd.bat z jiného počítače.</span><span class="sxs-lookup"><span data-stu-id="95ca2-117">Do not replace a missing or damaged VsDevCmd.bat file with a VsDevCmd.bat from another computer.</span></span> <span data-ttu-id="95ca2-118">Namísto toho nahraďte chybějící soubor opětovným spuštěním instalačního programu.</span><span class="sxs-lookup"><span data-stu-id="95ca2-118">Instead, rerun setup to replace the missing file.</span></span>

### <a name="available-options-for-vsdevcmdbat"></a><span data-ttu-id="95ca2-119">Dostupné možnosti pro VsDevCmd.BAT</span><span class="sxs-lookup"><span data-stu-id="95ca2-119">Available options for VsDevCmd.BAT</span></span>

<span data-ttu-id="95ca2-120">Pokud chcete zobrazit dostupné možnosti pro VsDevCmd.BAT, spusťte příkaz s `-help` možností:</span><span class="sxs-lookup"><span data-stu-id="95ca2-120">To see the available options for VsDevCmd.BAT, run the command with the `-help` option:</span></span>

```console
VsDevCmd.bat -help
```

## <a name="see-also"></a><span data-ttu-id="95ca2-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="95ca2-121">See also</span></span>

- [<span data-ttu-id="95ca2-122">Sestavování pomocí programu csc.exe v příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="95ca2-122">Command-line Building With csc.exe</span></span>](./command-line-building-with-csc-exe.md)
