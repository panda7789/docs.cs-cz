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
ms.openlocfilehash: 172472cf9a2e1bc7bb81448dc8793a4eaeb12da4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546553"
---
# <a name="power-management-in-windows-forms"></a>Správa výkonu ve Windows Forms
Aplikace Windows Forms můžete využít výhod funkce řízení spotřeby v operačním systému Windows. Aplikace můžete monitorovat stav napájení počítače a provést akci, když dojde ke změně stavu. Pokud vaše aplikace běží na přenosný počítač, můžete chtít zakázat některé funkce ve vaší aplikaci, když baterie počítače klesne pod určitou úroveň.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Poskytuje <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> události, ke kterému dochází pokaždé, když dojde ke změně stavu napájení, například když uživatel pozastaví nebo obnoví operačního systému, nebo při změně stavu napájení AC nebo stav baterie. <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> Vlastnost <xref:System.Windows.Forms.SystemInformation> třída může být použito pro dotaz na aktuální stav, jak je znázorněno v následujícím příkladu kódu.  
  
 [!code-csharp[PowerMode#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#1)]
 [!code-vb[PowerMode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#1)]  
  
 Kromě <xref:System.Windows.Forms.BatteryChargeStatus> výčty, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> vlastnost už obsahuje výčty pro zjištění kapacity baterií (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) a účtovat procento baterie (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>).  
  
 Můžete použít <xref:System.Windows.Forms.Application.SetSuspendState%2A> metodu <xref:System.Windows.Forms.Application> k přepnutí do počítače do režimu spánku nebo režimu spánku. Pokud `force` argument je nastaven na `false`, operačního systému bude vysílat události do všech aplikací, které si vyžádá oprávnění k pozastavení. Pokud `disableWakeEvent` argument je nastaven na `true`, operační systém zakáže všechny funkce události.  
  
 Následující příklad kódu ukazuje, jak převést počítač do režimu spánku.  
  
 [!code-csharp[PowerMode#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#2)]
 [!code-vb[PowerMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#2)]  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.Win32.SystemEvents.PowerModeChanged>
- <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>
- <xref:System.Windows.Forms.Application.SetSuspendState%2A>
- <xref:Microsoft.Win32.SystemEvents.SessionSwitch>
