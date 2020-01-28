---
title: Určení nainstalované verze WPF
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- version [WPF], finding
ms.assetid: 99971cef-e218-4f9f-a4c1-350332741860
ms.openlocfilehash: 8fc5c380779891b44b7c4f7f8aeb5ed119d8b768
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735691"
---
# <a name="how-to-determine-the-installed-version-of-wpf"></a>Postupy: Určení instalovatelné verze WPF
Číslo verze pro aktuálně nainstalovanou verzi [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] se nachází v **registru**.  
  
 Číslo verze zjistíte takto:  
  
1. V nabídce **Start** klikněte na **Spustit**.  
  
2. V **otevřeném**zadejte **Regedit. exe**.  
  
3. Otevřete následující klíč:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 Číslo verze [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je uloženo v hodnotě **verze** .
