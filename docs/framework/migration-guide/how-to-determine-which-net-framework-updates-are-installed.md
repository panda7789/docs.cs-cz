---
title: 'Postupy: Zjistit, které aktualizace zabezpečení a opravy hotfix jsou nainstalované .NET Framework'
description: Zjistěte, jak určit, které .NET Framework aktualizace zabezpečení a opravy hotfix jsou nainstalovány v počítači.
ms.date: 11/27/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c4c505c679c46494f7dc2534c2bbe9f50243a7dd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790063"
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a><span data-ttu-id="bfa64-103">Postupy: Zjistit, které aktualizace zabezpečení a opravy hotfix jsou nainstalované .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bfa64-103">How to: Determine which .NET Framework security updates and hotfixes are installed</span></span>

<span data-ttu-id="bfa64-104">V tomto článku se dozvíte, jak zjistit, které .NET Framework aktualizace zabezpečení a opravy hotfix jsou nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="bfa64-104">This article shows you how to find out which .NET Framework security updates and hotfixes are installed on a computer.</span></span>

> [!NOTE]
> <span data-ttu-id="bfa64-105">Všechny techniky uvedené v tomto článku vyžadují účet s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="bfa64-105">All the techniques shown in this article require an account with administrative privileges.</span></span>

## <a name="to-find-installed-updates-using-the-registry"></a><span data-ttu-id="bfa64-106">Vyhledání nainstalovaných aktualizací pomocí registru</span><span class="sxs-lookup"><span data-stu-id="bfa64-106">To find installed updates using the registry</span></span>

<span data-ttu-id="bfa64-107">Nainstalované aktualizace zabezpečení a opravy hotfix pro každou verzi .NET Framework nainstalované na počítači jsou uvedené v registru Windows.</span><span class="sxs-lookup"><span data-stu-id="bfa64-107">The installed security updates and hotfixes for each version of the .NET Framework installed on a computer are listed in the Windows registry.</span></span> <span data-ttu-id="bfa64-108">K zobrazení těchto informací můžete použít program Editor registru (*Regedit. exe*).</span><span class="sxs-lookup"><span data-stu-id="bfa64-108">You can use the Registry Editor (*regedit.exe*) program to view this information.</span></span>

1. <span data-ttu-id="bfa64-109">Spusťte program **Regedit. exe**.</span><span class="sxs-lookup"><span data-stu-id="bfa64-109">Open the program **regedit.exe**.</span></span> <span data-ttu-id="bfa64-110">V systému Windows 8 a novějších verzích klikněte pravým tlačítkem myši na **Start** ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo")a pak vyberte **Spustit**.</span><span class="sxs-lookup"><span data-stu-id="bfa64-110">In Windows 8 and later versions, right-click **Start** ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo"), then select **Run**.</span></span> <span data-ttu-id="bfa64-111">Do pole **otevřít** zadejte **Regedit** a vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="bfa64-111">In the **Open** box, enter **regedit** and select **OK**.</span></span>

2. <span data-ttu-id="bfa64-112">V editoru registru otevřete následující podklíč:</span><span class="sxs-lookup"><span data-stu-id="bfa64-112">In the Registry Editor, open the following subkey:</span></span>

     `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates`

     <span data-ttu-id="bfa64-113">Nainstalované aktualizace jsou uvedeny v podklíčích, které určují verzi rozhraní .NET Framework, na kterou se vztahují.</span><span class="sxs-lookup"><span data-stu-id="bfa64-113">The installed updates are listed under subkeys that identify the .NET Framework version they apply to.</span></span> <span data-ttu-id="bfa64-114">Jednotlivé aktualizace jsou označeny číslem znalostní báze Knowledge Base (KB).</span><span class="sxs-lookup"><span data-stu-id="bfa64-114">Each update is identified by a Knowledge Base (KB) number.</span></span>

<span data-ttu-id="bfa64-115">V editoru registru jsou verze rozhraní .NET Framework a nainstalované aktualizace pro jednotlivé verze uloženy v různých podklíčích.</span><span class="sxs-lookup"><span data-stu-id="bfa64-115">In the Registry Editor, the .NET Framework versions and installed updates for each version are stored in different subkeys.</span></span> <span data-ttu-id="bfa64-116">Informace o zjištění čísel nainstalovaných verzí najdete v tématu [How to: Určete, které verze .NET Framework jsou](how-to-determine-which-versions-are-installed.md)nainstalovány.</span><span class="sxs-lookup"><span data-stu-id="bfa64-116">For information about detecting the installed version numbers, see [How to: Determine which .NET Framework versions are installed](how-to-determine-which-versions-are-installed.md).</span></span>

## <a name="to-find-installed-updates-by-querying-the-registry-in-code"></a><span data-ttu-id="bfa64-117">Vyhledání nainstalovaných aktualizací pomocí dotazování registru v kódu</span><span class="sxs-lookup"><span data-stu-id="bfa64-117">To find installed updates by querying the registry in code</span></span>

<span data-ttu-id="bfa64-118">Následující příklad programově určuje .NET Framework aktualizace zabezpečení a opravy hotfix, které jsou nainstalovány v počítači:</span><span class="sxs-lookup"><span data-stu-id="bfa64-118">The following example programmatically determines the .NET Framework security updates and hotfixes that are installed on a computer:</span></span>

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

<span data-ttu-id="bfa64-119">Příklad vytvoří výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="bfa64-119">The example produces an output that's similar to the following one:</span></span>

```console
Microsoft .NET Framework 4 Client Profile
  KB2468871
  KB2468871v2
  KB2478063
  KB2533523
  KB2544514
  KB2600211
  KB2600217
Microsoft .NET Framework 4 Extended
  KB2468871
  KB2468871v2
  KB2478063
  KB2533523
  KB2544514
  KB2600211
  KB2600217
```

## <a name="to-find-installed-updates-by-querying-the-registry-in-powershell"></a><span data-ttu-id="bfa64-120">Vyhledání nainstalovaných aktualizací pomocí dotazování registru v PowerShellu</span><span class="sxs-lookup"><span data-stu-id="bfa64-120">To find installed updates by querying the registry in PowerShell</span></span>

<span data-ttu-id="bfa64-121">Následující příklad ukazuje, jak určit .NET Framework aktualizace zabezpečení a opravy hotfix, které jsou nainstalovány na počítači pomocí prostředí PowerShell:</span><span class="sxs-lookup"><span data-stu-id="bfa64-121">The following example shows how to determine the .NET Framework security updates and hotfixes that are installed on a computer using PowerShell:</span></span>

```powershell
$DotNetVersions = Get-ChildItem HKLM:\SOFTWARE\WOW6432Node\Microsoft\Updates | Where-Object {$_.name -like
 "*.NET Framework*"}

ForEach($Version in $DotNetVersions){
    
   $Updates = Get-ChildItem $Version.PSPath
    $Version.PSChildName
    ForEach ($Update in $Updates){
       $Update.PSChildName
       }
}
```

<span data-ttu-id="bfa64-122">Příklad vytvoří výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="bfa64-122">The example produces an output that's similar to the following one:</span></span>

```console
Microsoft .NET Framework 4 Client Profile
KB2468871
KB2468871v2
KB2478063
KB2533523
KB2544514
KB2600211
KB2600217
Microsoft .NET Framework 4 Extended
KB2468871
KB2468871v2
KB2478063
KB2533523
KB2544514
KB2600211
KB2600217
```

## <a name="see-also"></a><span data-ttu-id="bfa64-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bfa64-123">See also</span></span>

- [<span data-ttu-id="bfa64-124">Postupy: Určit, které verze .NET Framework jsou nainstalovány</span><span class="sxs-lookup"><span data-stu-id="bfa64-124">How to: Determine which .NET Framework versions are installed</span></span>](how-to-determine-which-versions-are-installed.md)
- [<span data-ttu-id="bfa64-125">Instalace .NET Framework pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="bfa64-125">Install the .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="bfa64-126">Verze a závislosti</span><span class="sxs-lookup"><span data-stu-id="bfa64-126">Versions and dependencies</span></span>](versions-and-dependencies.md)
