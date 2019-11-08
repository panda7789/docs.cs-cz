---
title: Které .NET Framework aktualizace zabezpečení a opravy hotfix jsou nainstalovány
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
ms.openlocfilehash: aad202e7c9df01c2893e74a39744f2c32783f1f0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735197"
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a><span data-ttu-id="491a2-103">Jak určit, které .NET Framework aktualizace zabezpečení a opravy hotfix jsou nainstalovány</span><span class="sxs-lookup"><span data-stu-id="491a2-103">How to determine which .NET Framework security updates and hotfixes are installed</span></span>

<span data-ttu-id="491a2-104">V tomto článku se dozvíte, jak zjistit, které .NET Framework aktualizace zabezpečení a opravy hotfix jsou nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="491a2-104">This article shows you how to find out which .NET Framework security updates and hotfixes are installed on a computer.</span></span>

> [!NOTE]
> <span data-ttu-id="491a2-105">Všechny techniky uvedené v tomto článku vyžadují účet s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="491a2-105">All the techniques shown in this article require an account with administrative privileges.</span></span>

## <a name="use-registry-editor"></a><span data-ttu-id="491a2-106">Použití Editoru registru</span><span class="sxs-lookup"><span data-stu-id="491a2-106">Use Registry Editor</span></span>

<span data-ttu-id="491a2-107">Nainstalované aktualizace zabezpečení a opravy hotfix pro každou verzi .NET Framework nainstalované na počítači jsou uvedené v registru Windows.</span><span class="sxs-lookup"><span data-stu-id="491a2-107">The installed security updates and hotfixes for each version of the .NET Framework installed on a computer are listed in the Windows registry.</span></span> <span data-ttu-id="491a2-108">K zobrazení těchto informací můžete použít program Editor registru (*Regedit. exe*).</span><span class="sxs-lookup"><span data-stu-id="491a2-108">You can use the Registry Editor (*regedit.exe*) program to view this information.</span></span>

1. <span data-ttu-id="491a2-109">Spusťte program **Regedit. exe**.</span><span class="sxs-lookup"><span data-stu-id="491a2-109">Open the program **regedit.exe**.</span></span> <span data-ttu-id="491a2-110">V systému Windows 8 a novějších verzích klikněte pravým tlačítkem myši na **Start** ![snímku loga Windows Key.](./media/how-to-determine-which-net-framework-updates-are-installed/windows-keyboard-logo.png "Windowskeyboardlogo")a pak vyberte **Spustit**.</span><span class="sxs-lookup"><span data-stu-id="491a2-110">In Windows 8 and later versions, right-click **Start** ![Screenshot of the Windows key logo.](./media/how-to-determine-which-net-framework-updates-are-installed/windows-keyboard-logo.png "Windowskeyboardlogo"), then select **Run**.</span></span> <span data-ttu-id="491a2-111">Do pole **otevřít** zadejte **Regedit** a vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="491a2-111">In the **Open** box, enter **regedit** and select **OK**.</span></span>

2. <span data-ttu-id="491a2-112">V editoru registru otevřete následující podklíč:</span><span class="sxs-lookup"><span data-stu-id="491a2-112">In the Registry Editor, open the following subkey:</span></span>

     <span data-ttu-id="491a2-113">**HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates**</span><span class="sxs-lookup"><span data-stu-id="491a2-113">**HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates**</span></span>

     <span data-ttu-id="491a2-114">Nainstalované aktualizace jsou uvedeny v podklíčích, které určují verzi rozhraní .NET Framework, na kterou se vztahují.</span><span class="sxs-lookup"><span data-stu-id="491a2-114">The installed updates are listed under subkeys that identify the .NET Framework version they apply to.</span></span> <span data-ttu-id="491a2-115">Jednotlivé aktualizace jsou označeny číslem znalostní báze Knowledge Base (KB).</span><span class="sxs-lookup"><span data-stu-id="491a2-115">Each update is identified by a Knowledge Base (KB) number.</span></span>

<span data-ttu-id="491a2-116">V editoru registru jsou verze rozhraní .NET Framework a nainstalované aktualizace pro jednotlivé verze uloženy v různých podklíčích.</span><span class="sxs-lookup"><span data-stu-id="491a2-116">In the Registry Editor, the .NET Framework versions and installed updates for each version are stored in different subkeys.</span></span> <span data-ttu-id="491a2-117">Informace o zjištění čísel nainstalovaných verzí najdete v tématu [Postup: určení, které verze .NET Framework jsou nainstalovány](how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="491a2-117">For information about detecting the installed version numbers, see [How to: Determine which .NET Framework versions are installed](how-to-determine-which-versions-are-installed.md).</span></span>

## <a name="query-the-registry-using-code"></a><span data-ttu-id="491a2-118">Dotazování registru pomocí kódu</span><span class="sxs-lookup"><span data-stu-id="491a2-118">Query the registry using code</span></span>

<span data-ttu-id="491a2-119">Následující příklad programově určuje .NET Framework aktualizace zabezpečení a opravy hotfix, které jsou nainstalovány v počítači:</span><span class="sxs-lookup"><span data-stu-id="491a2-119">The following example programmatically determines the .NET Framework security updates and hotfixes that are installed on a computer:</span></span>

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

<span data-ttu-id="491a2-120">Příklad vytvoří výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="491a2-120">The example produces an output that's similar to the following one:</span></span>

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

## <a name="use-powershell-to-query-the-registry"></a><span data-ttu-id="491a2-121">Použití PowerShellu k dotazování registru</span><span class="sxs-lookup"><span data-stu-id="491a2-121">Use PowerShell to query the registry</span></span>

<span data-ttu-id="491a2-122">Následující příklad ukazuje, jak určit .NET Framework aktualizace zabezpečení a opravy hotfix, které jsou nainstalovány na počítači pomocí prostředí PowerShell:</span><span class="sxs-lookup"><span data-stu-id="491a2-122">The following example shows how to determine the .NET Framework security updates and hotfixes that are installed on a computer using PowerShell:</span></span>

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

<span data-ttu-id="491a2-123">Příklad vytvoří výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="491a2-123">The example produces an output that's similar to the following one:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="491a2-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="491a2-124">See also</span></span>

- [<span data-ttu-id="491a2-125">Postupy: určení, které verze .NET Framework jsou nainstalovány</span><span class="sxs-lookup"><span data-stu-id="491a2-125">How to: Determine which .NET Framework versions are installed</span></span>](how-to-determine-which-versions-are-installed.md)
- [<span data-ttu-id="491a2-126">Instalace .NET Framework pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="491a2-126">Install the .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="491a2-127">Verze a závislosti</span><span class="sxs-lookup"><span data-stu-id="491a2-127">Versions and dependencies</span></span>](versions-and-dependencies.md)
