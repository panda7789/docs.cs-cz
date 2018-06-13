---
title: 'Postupy: Určení instalovatelné verze WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- version [WPF], finding
ms.assetid: 99971cef-e218-4f9f-a4c1-350332741860
ms.openlocfilehash: c59fa0d0a4d94c6e6a2ab72a4cd7a3c066649fb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545848"
---
# <a name="how-to-determine-the-installed-version-of-wpf"></a><span data-ttu-id="28e11-102">Postupy: Určení instalovatelné verze WPF</span><span class="sxs-lookup"><span data-stu-id="28e11-102">How to: Determine the Installed Version of WPF</span></span>
<span data-ttu-id="28e11-103">Číslo verze pro aktuální nainstalovaná verze [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] se nachází v **registru**.</span><span class="sxs-lookup"><span data-stu-id="28e11-103">The version number for the current installed version of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is located in the **Registry**.</span></span>  
  
 <span data-ttu-id="28e11-104">Vyhledání číslo verze:</span><span class="sxs-lookup"><span data-stu-id="28e11-104">To find the version number:</span></span>  
  
1.  <span data-ttu-id="28e11-105">Na **spustit** nabídky, klikněte na tlačítko **spustit**.</span><span class="sxs-lookup"><span data-stu-id="28e11-105">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="28e11-106">V **otevřete**, typ **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="28e11-106">In **Open**, type **regedit.exe**.</span></span>  
  
3.  <span data-ttu-id="28e11-107">Otevřete následující klíč:</span><span class="sxs-lookup"><span data-stu-id="28e11-107">Open the following key:</span></span>  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 <span data-ttu-id="28e11-108">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Číslo verze je uložené v **verze** hodnotu.</span><span class="sxs-lookup"><span data-stu-id="28e11-108">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] version number is stored in the **Version** value.</span></span>
