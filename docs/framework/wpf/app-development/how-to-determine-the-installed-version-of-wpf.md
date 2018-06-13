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
# <a name="how-to-determine-the-installed-version-of-wpf"></a>Postupy: Určení instalovatelné verze WPF
Číslo verze pro aktuální nainstalovaná verze [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] se nachází v **registru**.  
  
 Vyhledání číslo verze:  
  
1.  Na **spustit** nabídky, klikněte na tlačítko **spustit**.  
  
2.  V **otevřete**, typ **regedit.exe**.  
  
3.  Otevřete následující klíč:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Číslo verze je uložené v **verze** hodnotu.
