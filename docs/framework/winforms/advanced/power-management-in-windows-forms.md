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
# <a name="power-management-in-windows-forms"></a><span data-ttu-id="cfd20-102">Správa výkonu ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cfd20-102">Power Management in Windows Forms</span></span>
<span data-ttu-id="cfd20-103">Vaše aplikace model Windows Forms můžou využít výhod funkcí řízení spotřeby v operačním systému Windows.</span><span class="sxs-lookup"><span data-stu-id="cfd20-103">Your Windows Forms applications can take advantage of the power management features in the Windows operating system.</span></span> <span data-ttu-id="cfd20-104">Vaše aplikace mohou monitorovat stav napájení počítače a provádět akce, když dojde ke změně stavu.</span><span class="sxs-lookup"><span data-stu-id="cfd20-104">Your applications can monitor the power status of a computer and take action when a status change occurs.</span></span> <span data-ttu-id="cfd20-105">Například pokud vaše aplikace běží na přenosném počítači, možná budete chtít zakázat některé funkce v aplikaci, když je poplatek za baterii počítače mimo určitou úroveň.</span><span class="sxs-lookup"><span data-stu-id="cfd20-105">For example, if your application is running on a portable computer, you might want to disable certain features in your application when the computer's battery charge falls under a certain level.</span></span>  
  
 <span data-ttu-id="cfd20-106">.NET Framework poskytuje událost <xref:Microsoft.Win32.SystemEvents.PowerModeChanged>, ke které dochází, když dojde ke změně stavu napájení, například když uživatel pozastaví nebo obnoví operační systém nebo když se změní stav napájení nebo stav baterie.</span><span class="sxs-lookup"><span data-stu-id="cfd20-106">The .NET Framework provides a <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> event that occurs whenever there is a change in power status, such as when a user suspends or resumes the operating system, or when the AC power status or battery status changes.</span></span> <span data-ttu-id="cfd20-107">Vlastnost <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> třídy <xref:System.Windows.Forms.SystemInformation> lze použít k dotazování na aktuální stav, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="cfd20-107">The <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> property of the <xref:System.Windows.Forms.SystemInformation> class can be used to query for the current status, as shown in the following code example.</span></span>  
  
 [!code-csharp[PowerMode#1](~/samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#1)]
 [!code-vb[PowerMode#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#1)]  
  
 <span data-ttu-id="cfd20-108">Kromě výčtu <xref:System.Windows.Forms.BatteryChargeStatus> obsahuje vlastnost <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> také výčty pro určení kapacity baterie (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) a procento nabití baterie (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>).</span><span class="sxs-lookup"><span data-stu-id="cfd20-108">Besides the <xref:System.Windows.Forms.BatteryChargeStatus> enumerations, the <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> property also contains enumerations for determining battery capacity (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) and battery charge percentage (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>).</span></span>  
  
 <span data-ttu-id="cfd20-109">K uvedení počítače do režimu hibernace nebo režimu spánku můžete použít metodu <xref:System.Windows.Forms.Application.SetSuspendState%2A> <xref:System.Windows.Forms.Application>.</span><span class="sxs-lookup"><span data-stu-id="cfd20-109">You can use the <xref:System.Windows.Forms.Application.SetSuspendState%2A> method of the <xref:System.Windows.Forms.Application> to put a computer into hibernation or suspend mode.</span></span> <span data-ttu-id="cfd20-110">Je-li argument `force` nastaven na hodnotu `false`, bude operační systém vysílat událost všem aplikacím požadujícím oprávnění k pozastavení.</span><span class="sxs-lookup"><span data-stu-id="cfd20-110">If the `force` argument is set to `false`, the operating system will broadcast an event to all applications requesting permission to suspend.</span></span> <span data-ttu-id="cfd20-111">Je-li argument `disableWakeEvent` nastaven na hodnotu `true`, operační systém zakáže všechny události probuzení.</span><span class="sxs-lookup"><span data-stu-id="cfd20-111">If the `disableWakeEvent` argument is set to `true`, the operating system disables all wake events.</span></span>  
  
 <span data-ttu-id="cfd20-112">Následující příklad kódu ukazuje, jak převést počítač do režimu hibernace.</span><span class="sxs-lookup"><span data-stu-id="cfd20-112">The following code example demonstrates how to put a computer into hibernation.</span></span>  
  
 [!code-csharp[PowerMode#2](~/samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#2)]
 [!code-vb[PowerMode#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="cfd20-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cfd20-113">See also</span></span>

- <xref:Microsoft.Win32.SystemEvents.PowerModeChanged>
- <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>
- <xref:System.Windows.Forms.Application.SetSuspendState%2A>
- <xref:Microsoft.Win32.SystemEvents.SessionSwitch>
