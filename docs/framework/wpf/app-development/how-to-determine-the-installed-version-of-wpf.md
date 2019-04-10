---
title: 'Postupy: Určení nainstalované verze WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- version [WPF], finding
ms.assetid: 99971cef-e218-4f9f-a4c1-350332741860
ms.openlocfilehash: ffbd9a4c7f66dff9c8773dff4259551e20aa963d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59305673"
---
# <a name="how-to-determine-the-installed-version-of-wpf"></a>Postupy: Určení nainstalované verze WPF
Číslo verze pro aktuální nainstalovaná verze [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] se nachází v **registru**.  
  
 Najít číslo verze:  
  
1. Na **Start** nabídky, klikněte na tlačítko **spustit**.  
  
2. V **otevřít**, typ **regedit.exe**.  
  
3. Otevřete následující klíč:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Číslo verze je uloženo v **verze** hodnotu.
