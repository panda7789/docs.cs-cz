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
# <a name="how-to-determine-the-installed-version-of-wpf"></a>Postupy: Určení nainstalované verze WPF
Číslo verze pro aktuální nainstalovaná verze [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] se nachází v **registru**.  
  
 Najít číslo verze:  
  
1. Na **Start** nabídky, klikněte na tlačítko **spustit**.  
  
2. V **otevřít**, typ **regedit.exe**.  
  
3. Otevřete následující klíč:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Číslo verze je uloženo v **verze** hodnotu.
