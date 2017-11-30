---
title: "Postupy: určení, které rozhraní .NET Framework bezpečnostní aktualizace a opravy hotfix jsou nainstalovány."
description: "Zjistěte, jak určit, které aktualizace zabezpečení rozhraní .NET Framework a opravy hotfix jsou nainstalovány v počítači."
ms.date: 11/27/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9ff10928b87834f9b8e74e269082919f49497023
ms.sourcegitcommit: 39b65a49271e082add68cb737b48fdbe09d24718
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/30/2017
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a><span data-ttu-id="47ff2-103">Postupy: určení, které rozhraní .NET Framework bezpečnostní aktualizace a opravy hotfix jsou nainstalovány.</span><span class="sxs-lookup"><span data-stu-id="47ff2-103">How to: Determine which .NET Framework security updates and hotfixes are installed</span></span>

<span data-ttu-id="47ff2-104">Tento článek ukazuje, jak zjistit zabezpečení rozhraní .NET Framework, které aktualizace a opravy hotfix jsou nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="47ff2-104">This article shows you how to find out which .NET Framework security updates and hotfixes are installed on a computer.</span></span>

> [!NOTE]
> <span data-ttu-id="47ff2-105">Všechny postupy uvedené v tomto článku vyžadují účet s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="47ff2-105">All the techniques shown in this article require an account with administrative privileges.</span></span>

## <a name="to-find-installed-updates-using-the-registry"></a><span data-ttu-id="47ff2-106">Najít nainstalované aktualizace pomocí klíče registru</span><span class="sxs-lookup"><span data-stu-id="47ff2-106">To find installed updates using the registry</span></span>

<span data-ttu-id="47ff2-107">Aktualizace nainstalované zabezpečení a opravy hotfix pro každou verzi rozhraní .NET Framework, který je nainstalován v počítači jsou uvedeny v registru systému Windows.</span><span class="sxs-lookup"><span data-stu-id="47ff2-107">The installed security updates and hotfixes for each version of the .NET Framework installed on a computer are listed in the Windows registry.</span></span> <span data-ttu-id="47ff2-108">Můžete použít Editor registru (*regedit.exe*) programu, který chcete zobrazit tyto informace.</span><span class="sxs-lookup"><span data-stu-id="47ff2-108">You can use the Registry Editor (*regedit.exe*) program to view this information.</span></span>

1. <span data-ttu-id="47ff2-109">Otevřete program **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="47ff2-109">Open the program **regedit.exe**.</span></span> <span data-ttu-id="47ff2-110">Ve Windows 8 a novější verze, klikněte pravým tlačítkem na **spustit** ![s logem Windows](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo"), pak vyberte **spustit**.</span><span class="sxs-lookup"><span data-stu-id="47ff2-110">In Windows 8 and later versions, right-click **Start** ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo"), then select **Run**.</span></span> <span data-ttu-id="47ff2-111">V **otevřete** zadejte **regedit** a vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="47ff2-111">In the **Open** box, enter **regedit** and select **OK**.</span></span>

2. <span data-ttu-id="47ff2-112">V editoru registru otevřete následující podklíč:</span><span class="sxs-lookup"><span data-stu-id="47ff2-112">In the Registry Editor, open the following subkey:</span></span>

     `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates`

     <span data-ttu-id="47ff2-113">Nainstalované aktualizace jsou uvedeny v podklíčích, které určují verzi rozhraní .NET Framework, na kterou se vztahují.</span><span class="sxs-lookup"><span data-stu-id="47ff2-113">The installed updates are listed under subkeys that identify the .NET Framework version they apply to.</span></span> <span data-ttu-id="47ff2-114">Jednotlivé aktualizace jsou označeny číslem znalostní báze Knowledge Base (KB).</span><span class="sxs-lookup"><span data-stu-id="47ff2-114">Each update is identified by a Knowledge Base (KB) number.</span></span>

<span data-ttu-id="47ff2-115">V editoru registru jsou verze rozhraní .NET Framework a nainstalované aktualizace pro jednotlivé verze uloženy v různých podklíčích.</span><span class="sxs-lookup"><span data-stu-id="47ff2-115">In the Registry Editor, the .NET Framework versions and installed updates for each version are stored in different subkeys.</span></span> <span data-ttu-id="47ff2-116">Informace o zjišťování čísla nainstalovaná verze najdete v tématu [postupy: zjištění nainstalovaných verzí rozhraní .NET Framework](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="47ff2-116">For information about detecting the installed version numbers, see [How to: Determine which .NET Framework versions are installed](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span>

## <a name="to-find-installed-updates-by-querying-the-registry-in-code"></a><span data-ttu-id="47ff2-117">Najít nainstalované aktualizace dotazováním registru v kódu</span><span class="sxs-lookup"><span data-stu-id="47ff2-117">To find installed updates by querying the registry in code</span></span>

<span data-ttu-id="47ff2-118">Následující příklad určuje prostřednictvím kódu programu rozhraní .NET Framework bezpečnostní aktualizace a opravy hotfix, které jsou nainstalovány v počítači:</span><span class="sxs-lookup"><span data-stu-id="47ff2-118">The following example programmatically determines the .NET Framework security updates and hotfixes that are installed on a computer:</span></span>

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

<span data-ttu-id="47ff2-119">Tento příklad vytvoří výstupu, který je podobné následující:</span><span class="sxs-lookup"><span data-stu-id="47ff2-119">The example produces an output that's similar to the following one:</span></span>

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

## <a name="to-find-installed-updates-by-querying-the-registry-in-powershell"></a><span data-ttu-id="47ff2-120">Najít nainstalované aktualizace dotazováním registru v prostředí PowerShell</span><span class="sxs-lookup"><span data-stu-id="47ff2-120">To find installed updates by querying the registry in PowerShell</span></span>

<span data-ttu-id="47ff2-121">Následující příklad ukazuje, jak určit rozhraní .NET Framework bezpečnostní aktualizace a opravy hotfix, které jsou nainstalovány v počítači pomocí prostředí PowerShell:</span><span class="sxs-lookup"><span data-stu-id="47ff2-121">The following example shows how to determine the .NET Framework security updates and hotfixes that are installed on a computer using PowerShell:</span></span>

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

<span data-ttu-id="47ff2-122">Tento příklad vytvoří výstupu, který je podobné následující:</span><span class="sxs-lookup"><span data-stu-id="47ff2-122">The example produces an output that's similar to the following one:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="47ff2-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="47ff2-123">See also</span></span>

[<span data-ttu-id="47ff2-124">Postupy: zjištění nainstalovaných verzí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="47ff2-124">How to: Determine which .NET Framework versions are installed</span></span>](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)  
[<span data-ttu-id="47ff2-125">Nainstalujte rozhraní .NET Framework pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="47ff2-125">Install the .NET Framework for developers</span></span>](../../../docs/framework/install/guide-for-developers.md)  
[<span data-ttu-id="47ff2-126">Verze a závislosti</span><span class="sxs-lookup"><span data-stu-id="47ff2-126">Versions and dependencies</span></span>](../../../docs/framework/migration-guide/versions-and-dependencies.md)
