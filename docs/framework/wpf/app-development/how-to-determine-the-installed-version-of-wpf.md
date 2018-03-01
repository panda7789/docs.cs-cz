---
title: "Postupy: Určení instalovatelné verze WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- version [WPF], finding
ms.assetid: 99971cef-e218-4f9f-a4c1-350332741860
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cf58e8e8ade7382d8a897a3ec59bef0c810a48bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-the-installed-version-of-wpf"></a><span data-ttu-id="fdbaa-102">Postupy: Určení instalovatelné verze WPF</span><span class="sxs-lookup"><span data-stu-id="fdbaa-102">How to: Determine the Installed Version of WPF</span></span>
<span data-ttu-id="fdbaa-103">Číslo verze pro aktuální nainstalovaná verze [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] se nachází v **registru**.</span><span class="sxs-lookup"><span data-stu-id="fdbaa-103">The version number for the current installed version of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is located in the **Registry**.</span></span>  
  
 <span data-ttu-id="fdbaa-104">Vyhledání číslo verze:</span><span class="sxs-lookup"><span data-stu-id="fdbaa-104">To find the version number:</span></span>  
  
1.  <span data-ttu-id="fdbaa-105">Na **spustit** nabídky, klikněte na tlačítko **spustit**.</span><span class="sxs-lookup"><span data-stu-id="fdbaa-105">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="fdbaa-106">V **otevřete**, typ **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="fdbaa-106">In **Open**, type **regedit.exe**.</span></span>  
  
3.  <span data-ttu-id="fdbaa-107">Otevřete následující klíč:</span><span class="sxs-lookup"><span data-stu-id="fdbaa-107">Open the following key:</span></span>  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 <span data-ttu-id="fdbaa-108">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Číslo verze je uložené v **verze** hodnotu.</span><span class="sxs-lookup"><span data-stu-id="fdbaa-108">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] version number is stored in the **Version** value.</span></span>
