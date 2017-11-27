---
title: "Postupy: Zjištění nainstalovaných aktualizací rozhraní .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ba734dd3a9585b52b96cb2d27743da6190961126
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-determine-which-net-framework-updates-are-installed"></a><span data-ttu-id="43d2d-102">Postupy: Zjištění nainstalovaných aktualizací rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="43d2d-102">How to: Determine Which .NET Framework Updates Are Installed</span></span>
<span data-ttu-id="43d2d-103">Nainstalované aktualizace pro jednotlivé verze rozhraní .NET Framework nainstalované v počítači jsou uvedeny v registru systému Windows.</span><span class="sxs-lookup"><span data-stu-id="43d2d-103">The installed updates for each version of the .NET Framework installed on a computer are listed in the Windows registry.</span></span> <span data-ttu-id="43d2d-104">Chcete-li zobrazit tyto informace, můžete použít editor registru (regedit.exe).</span><span class="sxs-lookup"><span data-stu-id="43d2d-104">You can use the Registry Editor (regedit.exe) to view this information.</span></span>  
  
 <span data-ttu-id="43d2d-105">V editoru registru jsou verze rozhraní .NET Framework a nainstalované aktualizace pro jednotlivé verze uloženy v různých podklíčích.</span><span class="sxs-lookup"><span data-stu-id="43d2d-105">In the Registry Editor, the .NET Framework versions and installed updates for each version are stored in different subkeys.</span></span> <span data-ttu-id="43d2d-106">Informace o zjišťování čísla nainstalovaná verze najdete v tématu [postupy: určení rozhraní .NET Framework verze jsou nainstalované](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="43d2d-106">For information about detecting the installed version numbers, see [How to: Determine Which .NET Framework Versions Are Installed](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span> <span data-ttu-id="43d2d-107">Informace o instalaci rozhraní .NET Framework najdete v tématu [instalaci rozhraní .NET Framework pro vývojáře](../../../docs/framework/install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="43d2d-107">For information about installing the .NET Framework, see [Install the .NET Framework for developers](../../../docs/framework/install/guide-for-developers.md).</span></span>  
  
### <a name="to-find-installed-updates"></a><span data-ttu-id="43d2d-108">Vyhledání nainstalovaných aktualizací</span><span class="sxs-lookup"><span data-stu-id="43d2d-108">To find installed updates</span></span>  
  
1.  <span data-ttu-id="43d2d-109">Otevřete program **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="43d2d-109">Open the program **regedit.exe**.</span></span> <span data-ttu-id="43d2d-110">V systému Windows 8 a vyšší otevření obrazovky Start a zadejte název.</span><span class="sxs-lookup"><span data-stu-id="43d2d-110">In Windows 8 and higher open the Start screen and type the name.</span></span> <span data-ttu-id="43d2d-111">V dřívějších verzích systému Windows na **spustit** nabídce zvolte **spustit** a pak na **otevřete** zadejte **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="43d2d-111">In earlier versions of Windows, on the **Start** menu, choose **Run** and then, in the **Open** box, enter **regedit.exe**.</span></span>  
  
     <span data-ttu-id="43d2d-112">Ke spuštění souboru regedit.exe musíte mít oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="43d2d-112">You must have administrative credentials to run regedit.exe.</span></span>  
  
2.  <span data-ttu-id="43d2d-113">V editoru registru otevřete následující podklíč:</span><span class="sxs-lookup"><span data-stu-id="43d2d-113">In the Registry Editor, open the following subkey:</span></span>  
  
     <span data-ttu-id="43d2d-114">HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates</span><span class="sxs-lookup"><span data-stu-id="43d2d-114">HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates</span></span>  
  
     <span data-ttu-id="43d2d-115">Nainstalované aktualizace jsou uvedeny v podklíčích, které určují verzi rozhraní .NET Framework, na kterou se vztahují.</span><span class="sxs-lookup"><span data-stu-id="43d2d-115">The installed updates are listed under subkeys that identify the .NET Framework version they apply to.</span></span> <span data-ttu-id="43d2d-116">Jednotlivé aktualizace jsou označeny číslem znalostní báze Knowledge Base (KB).</span><span class="sxs-lookup"><span data-stu-id="43d2d-116">Each update is identified by a Knowledge Base (KB) number.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43d2d-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="43d2d-117">Example</span></span>  
 <span data-ttu-id="43d2d-118">Následující kód programově určuje aktualizace rozhraní .NET Framework, které jsou v počítači nainstalovány.</span><span class="sxs-lookup"><span data-stu-id="43d2d-118">The following code programmatically determines the .NET Framework updates that are installed on a computer.</span></span> <span data-ttu-id="43d2d-119">Chcete-li spustit tento příklad, musíte mít pověření správce.</span><span class="sxs-lookup"><span data-stu-id="43d2d-119">You must have administrative credentials to run this example.</span></span>  
  
 [!code-csharp[ListUpdates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs#1)]
 [!code-vb[ListUpdates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb#1)]  
  
 <span data-ttu-id="43d2d-120">Vzorové postupy budou mít výstup podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="43d2d-120">The example produces output that's similar to the following:</span></span>  
  
```  
Microsoft .NET Framework 3.5 SP1  
  KB953595  Hotfix for Microsoft .NET Framework 3.5 SP1 (KB953595)  
  SP1  
    KB2657424  Security Update for Microsoft .NET Framework 3.5 SP1 (KB2657424)  
    KB958484  Hotfix for Microsoft .NET Framework 3.5 SP1 (KB958484)  
    KB963707  Update for Microsoft .NET Framework 3.5 SP1 (KB963707)  
Microsoft .NET Framework 4 Client Profile  
  KB2160841  Security Update for Microsoft .NET Framework 4 Client Profile (KB2160841)  
  KB2446708  Security Update for Microsoft .NET Framework 4 Client Profile (KB2446708)  
  KB2468871  Update for Microsoft .NET Framework 4 Client Profile (KB2468871)  
  KB2478663  Security Update for Microsoft .NET Framework 4 Client Profile (KB2478663)  
  KB2518870  Security Update for Microsoft .NET Framework 4 Client Profile (KB2518870)  
  KB2533523  Update for Microsoft .NET Framework 4 Client Profile (KB2533523)  
  KB2539636  Security Update for Microsoft .NET Framework 4 Client Profile (KB2539636)  
  KB2572078  Security Update for Microsoft .NET Framework 4 Client Profile (KB2572078)  
  KB2633870  Security Update for Microsoft .NET Framework 4 Client Profile (KB2633870)  
  KB2656351  Security Update for Microsoft .NET Framework 4 Client Profile (KB2656351)  
Microsoft .NET Framework 4 Extended  
  KB2416472  Security Update for Microsoft .NET Framework 4 Extended (KB2416472)  
  KB2468871  Update for Microsoft .NET Framework 4 Extended (KB2468871)  
  KB2487367  Security Update for Microsoft .NET Framework 4 Extended (KB2487367)  
  KB2533523  Update for Microsoft .NET Framework 4 Extended (KB2533523)  
  KB2656351  Security Update for Microsoft .NET Framework 4 Extended (KB2656351)  
```  
  
## <a name="see-also"></a><span data-ttu-id="43d2d-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="43d2d-121">See also</span></span>

<span data-ttu-id="43d2d-122">[Postupy: zjištění nainstalovaných verzí rozhraní .NET Framework](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md) </span><span class="sxs-lookup"><span data-stu-id="43d2d-122">[How to: Determine Which .NET Framework Versions Are Installed](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md) </span></span>  
<span data-ttu-id="43d2d-123">[Instalace rozhraní .NET Framework](../../../docs/framework/install/guide-for-developers.md) </span><span class="sxs-lookup"><span data-stu-id="43d2d-123">[Installing the .NET Framework](../../../docs/framework/install/guide-for-developers.md) </span></span>  
[<span data-ttu-id="43d2d-124">Verze a závislosti</span><span class="sxs-lookup"><span data-stu-id="43d2d-124">Versions and Dependencies</span></span>](../../../docs/framework/migration-guide/versions-and-dependencies.md)
