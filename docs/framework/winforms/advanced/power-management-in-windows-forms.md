---
title: Řízení spotřeby
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- battery states
- power states
ms.assetid: ad04a801-5682-4d88-92c5-26eb9cdb209a
ms.openlocfilehash: 9ac39df43a08f62e50116c61c4bdeda4cd1c8281
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746865"
---
# <a name="power-management-in-windows-forms"></a>Správa výkonu ve Windows Forms
Vaše aplikace model Windows Forms můžou využít výhod funkcí řízení spotřeby v operačním systému Windows. Vaše aplikace mohou monitorovat stav napájení počítače a provádět akce, když dojde ke změně stavu. Například pokud vaše aplikace běží na přenosném počítači, možná budete chtít zakázat některé funkce v aplikaci, když je poplatek za baterii počítače mimo určitou úroveň.  
  
 .NET Framework poskytuje událost <xref:Microsoft.Win32.SystemEvents.PowerModeChanged>, ke které dochází, když dojde ke změně stavu napájení, například když uživatel pozastaví nebo obnoví operační systém nebo když se změní stav napájení nebo stav baterie. Vlastnost <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> třídy <xref:System.Windows.Forms.SystemInformation> lze použít k dotazování na aktuální stav, jak je znázorněno v následujícím příkladu kódu.  
  
 [!code-csharp[PowerMode#1](~/samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#1)]
 [!code-vb[PowerMode#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#1)]  
  
 Kromě výčtu <xref:System.Windows.Forms.BatteryChargeStatus> obsahuje vlastnost <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> také výčty pro určení kapacity baterie (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) a procento nabití baterie (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>).  
  
 K uvedení počítače do režimu hibernace nebo režimu spánku můžete použít metodu <xref:System.Windows.Forms.Application.SetSuspendState%2A> <xref:System.Windows.Forms.Application>. Je-li argument `force` nastaven na hodnotu `false`, bude operační systém vysílat událost všem aplikacím požadujícím oprávnění k pozastavení. Je-li argument `disableWakeEvent` nastaven na hodnotu `true`, operační systém zakáže všechny události probuzení.  
  
 Následující příklad kódu ukazuje, jak převést počítač do režimu hibernace.  
  
 [!code-csharp[PowerMode#2](~/samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#2)]
 [!code-vb[PowerMode#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#2)]  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.Win32.SystemEvents.PowerModeChanged>
- <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>
- <xref:System.Windows.Forms.Application.SetSuspendState%2A>
- <xref:Microsoft.Win32.SystemEvents.SessionSwitch>
