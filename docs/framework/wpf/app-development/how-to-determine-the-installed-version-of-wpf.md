---
title: 'Postupy: Určení nainstalované verze WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- version [WPF], finding
ms.assetid: 99971cef-e218-4f9f-a4c1-350332741860
ms.openlocfilehash: ffbd9a4c7f66dff9c8773dff4259551e20aa963d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052453"
---
# <a name="how-to-determine-the-installed-version-of-wpf"></a><span data-ttu-id="da648-102">Postupy: Určení nainstalované verze WPF</span><span class="sxs-lookup"><span data-stu-id="da648-102">How to: Determine the Installed Version of WPF</span></span>
<span data-ttu-id="da648-103">Číslo verze pro aktuální nainstalovaná verze [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] se nachází v **registru**.</span><span class="sxs-lookup"><span data-stu-id="da648-103">The version number for the current installed version of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is located in the **Registry**.</span></span>  
  
 <span data-ttu-id="da648-104">Najít číslo verze:</span><span class="sxs-lookup"><span data-stu-id="da648-104">To find the version number:</span></span>  
  
1. <span data-ttu-id="da648-105">Na **Start** nabídky, klikněte na tlačítko **spustit**.</span><span class="sxs-lookup"><span data-stu-id="da648-105">On the **Start** menu, click **Run**.</span></span>  
  
2. <span data-ttu-id="da648-106">V **otevřít**, typ **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="da648-106">In **Open**, type **regedit.exe**.</span></span>  
  
3. <span data-ttu-id="da648-107">Otevřete následující klíč:</span><span class="sxs-lookup"><span data-stu-id="da648-107">Open the following key:</span></span>  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 <span data-ttu-id="da648-108">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Číslo verze je uloženo v **verze** hodnotu.</span><span class="sxs-lookup"><span data-stu-id="da648-108">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] version number is stored in the **Version** value.</span></span>
