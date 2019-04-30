---
title: 'Postupy: Zjistit, které rozhraní .NET Framework bezpečnostní aktualizace a opravy hotfix jsou nainstalované.'
description: Zjistěte, jak určit, které rozhraní .NET Framework bezpečnostní aktualizace a opravy hotfix jsou nainstalovány v počítači.
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
ms.openlocfilehash: e11b2588471e95b4e47fd0efaf41757430b9bb39
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61872921"
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a><span data-ttu-id="d1502-103">Postupy: Zjistit, které rozhraní .NET Framework bezpečnostní aktualizace a opravy hotfix jsou nainstalované.</span><span class="sxs-lookup"><span data-stu-id="d1502-103">How to: Determine which .NET Framework security updates and hotfixes are installed</span></span>

<span data-ttu-id="d1502-104">V tomto článku se dozvíte, jak zjistit aktualizace zabezpečení, které rozhraní .NET Framework a opravy hotfix jsou nainstalované v počítači.</span><span class="sxs-lookup"><span data-stu-id="d1502-104">This article shows you how to find out which .NET Framework security updates and hotfixes are installed on a computer.</span></span>

> [!NOTE]
> <span data-ttu-id="d1502-105">Všechny postupy uvedené v tomto článku vyžadovat účet s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="d1502-105">All the techniques shown in this article require an account with administrative privileges.</span></span>

## <a name="to-find-installed-updates-using-the-registry"></a><span data-ttu-id="d1502-106">Vyhledání nainstalovaných aktualizací pomocí registru</span><span class="sxs-lookup"><span data-stu-id="d1502-106">To find installed updates using the registry</span></span>

<span data-ttu-id="d1502-107">Nainstalované aktualizace a opravy hotfix pro každou verzi rozhraní .NET Framework nainstalované v počítači jsou uvedeny v registru Windows.</span><span class="sxs-lookup"><span data-stu-id="d1502-107">The installed security updates and hotfixes for each version of the .NET Framework installed on a computer are listed in the Windows registry.</span></span> <span data-ttu-id="d1502-108">Můžete použít Editor registru (*regedit.exe*) program, chcete-li zobrazit tyto informace.</span><span class="sxs-lookup"><span data-stu-id="d1502-108">You can use the Registry Editor (*regedit.exe*) program to view this information.</span></span>

1. <span data-ttu-id="d1502-109">Otevřete program **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="d1502-109">Open the program **regedit.exe**.</span></span> <span data-ttu-id="d1502-110">V systému Windows 8 a novějších verzích, klikněte pravým tlačítkem na **Start** ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo")a pak vyberte **spustit**.</span><span class="sxs-lookup"><span data-stu-id="d1502-110">In Windows 8 and later versions, right-click **Start** ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo"), then select **Run**.</span></span> <span data-ttu-id="d1502-111">V **otevřít** zadejte **regedit** a vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="d1502-111">In the **Open** box, enter **regedit** and select **OK**.</span></span>

2. <span data-ttu-id="d1502-112">V editoru registru otevřete následující podklíč:</span><span class="sxs-lookup"><span data-stu-id="d1502-112">In the Registry Editor, open the following subkey:</span></span>

     `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates`

     <span data-ttu-id="d1502-113">Nainstalované aktualizace jsou uvedeny v podklíčích, které určují verzi rozhraní .NET Framework, na kterou se vztahují.</span><span class="sxs-lookup"><span data-stu-id="d1502-113">The installed updates are listed under subkeys that identify the .NET Framework version they apply to.</span></span> <span data-ttu-id="d1502-114">Jednotlivé aktualizace jsou označeny číslem znalostní báze Knowledge Base (KB).</span><span class="sxs-lookup"><span data-stu-id="d1502-114">Each update is identified by a Knowledge Base (KB) number.</span></span>

<span data-ttu-id="d1502-115">V editoru registru jsou verze rozhraní .NET Framework a nainstalované aktualizace pro jednotlivé verze uloženy v různých podklíčích.</span><span class="sxs-lookup"><span data-stu-id="d1502-115">In the Registry Editor, the .NET Framework versions and installed updates for each version are stored in different subkeys.</span></span> <span data-ttu-id="d1502-116">Informace o způsobu zjištění čísel nainstalovaných verzí, naleznete v tématu [jak: Určete, jaké verze rozhraní .NET Framework jsou nainstalovány](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="d1502-116">For information about detecting the installed version numbers, see [How to: Determine which .NET Framework versions are installed](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span>

## <a name="to-find-installed-updates-by-querying-the-registry-in-code"></a><span data-ttu-id="d1502-117">Chcete-li najít nainstalované aktualizace dotazem na registr v kódu</span><span class="sxs-lookup"><span data-stu-id="d1502-117">To find installed updates by querying the registry in code</span></span>

<span data-ttu-id="d1502-118">Následující příklad programově určuje aktualizace rozhraní .NET Framework zabezpečení a opravy hotfix, které jsou nainstalovány v počítači:</span><span class="sxs-lookup"><span data-stu-id="d1502-118">The following example programmatically determines the .NET Framework security updates and hotfixes that are installed on a computer:</span></span>

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

<span data-ttu-id="d1502-119">Vzorové postupy výstupu, který je podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="d1502-119">The example produces an output that's similar to the following one:</span></span>

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

## <a name="to-find-installed-updates-by-querying-the-registry-in-powershell"></a><span data-ttu-id="d1502-120">Chcete-li najít nainstalované aktualizace dotazem na registr v prostředí PowerShell</span><span class="sxs-lookup"><span data-stu-id="d1502-120">To find installed updates by querying the registry in PowerShell</span></span>

<span data-ttu-id="d1502-121">Následující příklad ukazuje, jak určit rozhraní .NET Framework aktualizací a oprav hotfix, které jsou nainstalovány v počítači pomocí Powershellu:</span><span class="sxs-lookup"><span data-stu-id="d1502-121">The following example shows how to determine the .NET Framework security updates and hotfixes that are installed on a computer using PowerShell:</span></span>

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

<span data-ttu-id="d1502-122">Vzorové postupy výstupu, který je podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="d1502-122">The example produces an output that's similar to the following one:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d1502-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d1502-123">See also</span></span>

- [<span data-ttu-id="d1502-124">Postupy: Zjištění nainstalovaných verzí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d1502-124">How to: Determine which .NET Framework versions are installed</span></span>](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)
- [<span data-ttu-id="d1502-125">Instalace rozhraní .NET Framework pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="d1502-125">Install the .NET Framework for developers</span></span>](../../../docs/framework/install/guide-for-developers.md)
- [<span data-ttu-id="d1502-126">Verze a závislosti</span><span class="sxs-lookup"><span data-stu-id="d1502-126">Versions and dependencies</span></span>](../../../docs/framework/migration-guide/versions-and-dependencies.md)
