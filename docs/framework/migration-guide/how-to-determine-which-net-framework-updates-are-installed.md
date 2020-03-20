---
title: Viz nainstalované aktualizace zabezpečení rozhraní .NET Framework a opravy hotfix
description: Přečtěte si, jak určit, které aktualizace zabezpečení rozhraní .NET Framework a opravy hotfix jsou v počítači nainstalovány.
ms.date: 11/27/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
ms.openlocfilehash: 5c7bf48d5786530a9bcb69fb7cf605ac2c80a4eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181272"
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a><span data-ttu-id="945b9-103">Jak zjistit, které aktualizace zabezpečení rozhraní .NET Framework a opravy hotfix jsou nainstalovány</span><span class="sxs-lookup"><span data-stu-id="945b9-103">How to determine which .NET Framework security updates and hotfixes are installed</span></span>

<span data-ttu-id="945b9-104">V tomto článku se dozvíte, které aktualizace zabezpečení rozhraní .NET Framework a opravy hotfix jsou v počítači nainstalovány.</span><span class="sxs-lookup"><span data-stu-id="945b9-104">This article shows you how to find out which .NET Framework security updates and hotfixes are installed on a computer.</span></span>

> [!NOTE]
> <span data-ttu-id="945b9-105">Všechny techniky uvedené v tomto článku vyžadují účet s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="945b9-105">All the techniques shown in this article require an account with administrative privileges.</span></span>

## <a name="use-registry-editor"></a><span data-ttu-id="945b9-106">Použít Editor registru</span><span class="sxs-lookup"><span data-stu-id="945b9-106">Use Registry Editor</span></span>

<span data-ttu-id="945b9-107">Nainstalované aktualizace zabezpečení a opravy hotfix pro každou verzi rozhraní .NET Framework nainstalovaných v počítači jsou uvedeny v registru systému Windows.</span><span class="sxs-lookup"><span data-stu-id="945b9-107">The installed security updates and hotfixes for each version of the .NET Framework installed on a computer are listed in the Windows registry.</span></span> <span data-ttu-id="945b9-108">K zobrazení těchto informací můžete použít program Editor registru (*regedit.exe*).</span><span class="sxs-lookup"><span data-stu-id="945b9-108">You can use the Registry Editor (*regedit.exe*) program to view this information.</span></span>

1. <span data-ttu-id="945b9-109">Otevřete program **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="945b9-109">Open the program **regedit.exe**.</span></span> <span data-ttu-id="945b9-110">Ve Windows 8 a novějších verzích klikněte pravým tlačítkem **Run**myši na **položku Spustit** ![snímek obrazovky loga klíče systému Windows.](./media/how-to-determine-which-net-framework-updates-are-installed/windows-keyboard-logo.png "Windowskeyboardlogo")</span><span class="sxs-lookup"><span data-stu-id="945b9-110">In Windows 8 and later versions, right-click **Start** ![Screenshot of the Windows key logo.](./media/how-to-determine-which-net-framework-updates-are-installed/windows-keyboard-logo.png "Windowskeyboardlogo"), then select **Run**.</span></span> <span data-ttu-id="945b9-111">Do pole **Otevřít** zadejte **regedit** a vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="945b9-111">In the **Open** box, enter **regedit** and select **OK**.</span></span>

2. <span data-ttu-id="945b9-112">V editoru registru otevřete následující podklíč:</span><span class="sxs-lookup"><span data-stu-id="945b9-112">In the Registry Editor, open the following subkey:</span></span>

     <span data-ttu-id="945b9-113">**HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates**</span><span class="sxs-lookup"><span data-stu-id="945b9-113">**HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates**</span></span>

     <span data-ttu-id="945b9-114">Nainstalované aktualizace jsou uvedeny v podklíčích, které určují verzi rozhraní .NET Framework, na kterou se vztahují.</span><span class="sxs-lookup"><span data-stu-id="945b9-114">The installed updates are listed under subkeys that identify the .NET Framework version they apply to.</span></span> <span data-ttu-id="945b9-115">Jednotlivé aktualizace jsou označeny číslem znalostní báze Knowledge Base (KB).</span><span class="sxs-lookup"><span data-stu-id="945b9-115">Each update is identified by a Knowledge Base (KB) number.</span></span>

<span data-ttu-id="945b9-116">V editoru registru jsou verze rozhraní .NET Framework a nainstalované aktualizace pro jednotlivé verze uloženy v různých podklíčích.</span><span class="sxs-lookup"><span data-stu-id="945b9-116">In the Registry Editor, the .NET Framework versions and installed updates for each version are stored in different subkeys.</span></span> <span data-ttu-id="945b9-117">Informace o zjišťování nainstalovaných čísel verzí naleznete v [tématu Postup: Určení, které verze rozhraní .NET Framework jsou nainstalovány](how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="945b9-117">For information about detecting the installed version numbers, see [How to: Determine which .NET Framework versions are installed](how-to-determine-which-versions-are-installed.md).</span></span>

## <a name="query-the-registry-using-code"></a><span data-ttu-id="945b9-118">Dotaz na registr pomocí kódu</span><span class="sxs-lookup"><span data-stu-id="945b9-118">Query the registry using code</span></span>

<span data-ttu-id="945b9-119">Následující příklad programově určuje aktualizace zabezpečení rozhraní .NET Framework a opravy hotfix nainstalované v počítači:</span><span class="sxs-lookup"><span data-stu-id="945b9-119">The following example programmatically determines the .NET Framework security updates and hotfixes that are installed on a computer:</span></span>

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

<span data-ttu-id="945b9-120">Příklad vytvoří výstup, který je podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="945b9-120">The example produces an output that's similar to the following one:</span></span>

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

## <a name="use-powershell-to-query-the-registry"></a><span data-ttu-id="945b9-121">Použití prostředí PowerShell k dotazování registru</span><span class="sxs-lookup"><span data-stu-id="945b9-121">Use PowerShell to query the registry</span></span>

<span data-ttu-id="945b9-122">Následující příklad ukazuje, jak určit aktualizace zabezpečení rozhraní .NET Framework a opravy hotfix nainstalované v počítači pomocí prostředí PowerShell:</span><span class="sxs-lookup"><span data-stu-id="945b9-122">The following example shows how to determine the .NET Framework security updates and hotfixes that are installed on a computer using PowerShell:</span></span>

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

<span data-ttu-id="945b9-123">Příklad vytvoří výstup, který je podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="945b9-123">The example produces an output that's similar to the following one:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="945b9-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="945b9-124">See also</span></span>

- [<span data-ttu-id="945b9-125">Postup: Určení nainstalovaných verzí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="945b9-125">How to: Determine which .NET Framework versions are installed</span></span>](how-to-determine-which-versions-are-installed.md)
- [<span data-ttu-id="945b9-126">Instalace rozhraní .NET Framework pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="945b9-126">Install the .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="945b9-127">Verze a závislosti</span><span class="sxs-lookup"><span data-stu-id="945b9-127">Versions and dependencies</span></span>](versions-and-dependencies.md)
