---
title: Správa výkonu ve Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- battery states
- power states
ms.assetid: ad04a801-5682-4d88-92c5-26eb9cdb209a
ms.openlocfilehash: 845cc9c910d63dfc7460bba0d5368b5b1e63efcd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523488"
---
# <a name="power-management-in-windows-forms"></a>Správa výkonu ve Windows Forms
Aplikace Windows Forms můžete využít výhod funkce řízení spotřeby v operačním systému Windows. Aplikace můžete monitorovat stav napájení počítače a provést akci, když dojde ke změně stavu. Pokud vaše aplikace běží na přenosného počítače, můžete chtít zakázat některé funkce ve vaší aplikaci, když baterie počítače klesne pod určitou úroveň.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Poskytuje <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> událostí, ke kterému dochází vždy, když dojde ke změně power stav, například pokud uživatel pozastaví nebo obnoví operačního systému, nebo při změně stavu napájení ze sítě nebo stav baterie. <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> Vlastnost <xref:System.Windows.Forms.SystemInformation> třídy lze použít k dotazu na aktuální stav, jak je znázorněno v následujícím příkladu kódu.  
  
 [!code-csharp[PowerMode#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#1)]
 [!code-vb[PowerMode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#1)]  
  
 Kromě <xref:System.Windows.Forms.BatteryChargeStatus> výčty, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> vlastnost také obsahuje výčty týkajících se kapacity baterie (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) a baterie účtují procento (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>).  
  
 Můžete použít <xref:System.Windows.Forms.Application.SetSuspendState%2A> metodu <xref:System.Windows.Forms.Application> k přepnutí do počítače do režimu spánku nebo režimu spánku. Pokud `force` argument je nastaven na hodnotu `false`, operační systém bude vysílání události pro všechny aplikace, které žádá o oprávnění pozastavit. Pokud `disableWakeEvent` argument je nastaven na hodnotu `true`, operační systém zakáže všechny události probuzení.  
  
 Následující příklad kódu ukazuje, jak převést počítače do režimu hibernace.  
  
 [!code-csharp[PowerMode#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#2)]
 [!code-vb[PowerMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.Win32.SystemEvents.PowerModeChanged>  
 <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>  
 <xref:System.Windows.Forms.Application.SetSuspendState%2A>  
 <xref:Microsoft.Win32.SystemEvents.SessionSwitch>
