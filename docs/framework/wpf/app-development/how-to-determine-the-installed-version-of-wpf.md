---
title: "Postupy: Určení instalovatelné verze WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: version [WPF], finding
ms.assetid: 99971cef-e218-4f9f-a4c1-350332741860
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cf58e8e8ade7382d8a897a3ec59bef0c810a48bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-the-installed-version-of-wpf"></a>Postupy: Určení instalovatelné verze WPF
Číslo verze pro aktuální nainstalovaná verze [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] se nachází v **registru**.  
  
 Vyhledání číslo verze:  
  
1.  Na **spustit** nabídky, klikněte na tlačítko **spustit**.  
  
2.  V **otevřete**, typ **regedit.exe**.  
  
3.  Otevřete následující klíč:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Číslo verze je uložené v **verze** hodnotu.
