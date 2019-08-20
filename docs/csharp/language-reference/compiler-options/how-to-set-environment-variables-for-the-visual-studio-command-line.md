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
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a><span data-ttu-id="ab88f-102">Postupy: Nastavení proměnných prostředí pro příkazový řádek Visual Studia</span><span class="sxs-lookup"><span data-stu-id="ab88f-102">How to: Set Environment Variables for the Visual Studio Command Line</span></span>

<span data-ttu-id="ab88f-103">Soubor VsDevCmd. bat nastaví příslušné proměnné prostředí pro povolení sestavení příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="ab88f-103">The VsDevCmd.bat file sets the appropriate environment variables to enable command-line builds.</span></span>

> [!NOTE]
> <span data-ttu-id="ab88f-104">Soubor VsDevCmd. bat je nový soubor dodávaný se sadou Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="ab88f-104">The VsDevCmd.bat file is a new file delivered with Visual Studio 2017.</span></span> <span data-ttu-id="ab88f-105">Visual Studio 2015 a starší verze používaly VSVARS32. bat pro stejný účel.</span><span class="sxs-lookup"><span data-stu-id="ab88f-105">Visual Studio 2015 and earlier versions used VSVARS32.bat for the same purpose.</span></span> <span data-ttu-id="ab88f-106">Tento soubor byl uložen ve složce \Program Files\Microsoft Visual\\Studio*Version*\Common7\Tools nebo Program Files (x86) \Microsoft Visual\\Studio*verze*\Common7\Tools.</span><span class="sxs-lookup"><span data-stu-id="ab88f-106">This file was stored in \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.</span></span>

<span data-ttu-id="ab88f-107">Pokud je aktuální verze sady Visual Studio nainstalována na počítači, který má také starší verzi sady Visual Studio, neměli byste spouštět VsDevCmd. bat a VSVARS32. BAT z různých verzí ve stejném okně příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="ab88f-107">If the current version of Visual Studio is installed on a computer that also has an earlier version of Visual Studio, you should not run VsDevCmd.bat and VSVARS32.BAT from different versions in the same Command Prompt window.</span></span> <span data-ttu-id="ab88f-108">Místo toho byste měli spustit příkaz pro každou verzi ve vlastním okně.</span><span class="sxs-lookup"><span data-stu-id="ab88f-108">Instead, you should run the command for each version in its own window.</span></span>

### <a name="to-run-vsdevcmdbat"></a><span data-ttu-id="ab88f-109">Spuštění VsDevCmd. BAT</span><span class="sxs-lookup"><span data-stu-id="ab88f-109">To run VsDevCmd.BAT</span></span>

1. <span data-ttu-id="ab88f-110">V nabídce **Start** otevřete **Developer Command Prompt pro vs 2017**.</span><span class="sxs-lookup"><span data-stu-id="ab88f-110">From the **Start** menu, open the **Developer Command Prompt for VS 2017**.</span></span>  <span data-ttu-id="ab88f-111">Je ve složce **Visual Studio 2017** .</span><span class="sxs-lookup"><span data-stu-id="ab88f-111">It's in the **Visual Studio 2017** folder.</span></span>

2. <span data-ttu-id="ab88f-112">Přejděte na\\*verzi*\\\\\Program Files\Microsoft Visual Studio, která nabízí \Common7\Tools nebo \Program Files (x86) \Microsoft Visual Studio version nabídky\\\Common7\Tools podadresář instalace.</span><span class="sxs-lookup"><span data-stu-id="ab88f-112">Change to the \Program Files\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools or \Program Files (x86)\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools subdirectory of your installation.</span></span>  <span data-ttu-id="ab88f-113">(*Verze* je *2017* pro aktuální verzi.</span><span class="sxs-lookup"><span data-stu-id="ab88f-113">(*Version* is *2017* for the current version.</span></span> <span data-ttu-id="ab88f-114">*Nabídka* je jedním z firem *Enterprise*, *Professional* nebo *Community*.)</span><span class="sxs-lookup"><span data-stu-id="ab88f-114">*Offering* is one of *Enterprise*, *Professional* or *Community*.)</span></span>

3. <span data-ttu-id="ab88f-115">Spusťte VsDevCmd. bat zadáním **VsDevCmd**.</span><span class="sxs-lookup"><span data-stu-id="ab88f-115">Run VsDevCmd.bat by typing **VsDevCmd**.</span></span>

    > [!CAUTION]
    > <span data-ttu-id="ab88f-116">VsDevCmd. bat se může lišit od počítače k počítači.</span><span class="sxs-lookup"><span data-stu-id="ab88f-116">VsDevCmd.bat can vary from computer to computer.</span></span> <span data-ttu-id="ab88f-117">Neměňte chybějící nebo poškozený soubor VsDevCmd. bat s příponou VsDevCmd. bat z jiného počítače.</span><span class="sxs-lookup"><span data-stu-id="ab88f-117">Do not replace a missing or damaged VsDevCmd.bat file with a VsDevCmd.bat from another computer.</span></span> <span data-ttu-id="ab88f-118">Namísto toho nahraďte chybějící soubor opětovným spuštěním instalačního programu.</span><span class="sxs-lookup"><span data-stu-id="ab88f-118">Instead, rerun setup to replace the missing file.</span></span>

### <a name="available-options-for-vsdevcmdbat"></a><span data-ttu-id="ab88f-119">Dostupné možnosti pro VsDevCmd. BAT</span><span class="sxs-lookup"><span data-stu-id="ab88f-119">Available options for VsDevCmd.BAT</span></span>

<span data-ttu-id="ab88f-120">Pokud chcete zobrazit dostupné možnosti pro VsDevCmd. bat, spusťte příkaz s `-help` možností:</span><span class="sxs-lookup"><span data-stu-id="ab88f-120">To see the available options for VsDevCmd.BAT, run the command with the `-help` option:</span></span>

```console
VsDevCmd.bat -help
```

## <a name="see-also"></a><span data-ttu-id="ab88f-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ab88f-121">See also</span></span>

- [<span data-ttu-id="ab88f-122">Sestavování pomocí programu csc.exe v příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="ab88f-122">Command-line Building With csc.exe</span></span>](./command-line-building-with-csc-exe.md)
