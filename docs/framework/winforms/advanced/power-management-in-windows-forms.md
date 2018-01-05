---
title: "Správa výkonu ve Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- battery states
- power states
ms.assetid: ad04a801-5682-4d88-92c5-26eb9cdb209a
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7600ae42194b3333c404d217c2605a226df99e7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="power-management-in-windows-forms"></a><span data-ttu-id="e84b0-102">Správa výkonu ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e84b0-102">Power Management in Windows Forms</span></span>
<span data-ttu-id="e84b0-103">Aplikace Windows Forms můžete využít výhod funkce řízení spotřeby v operačním systému Windows.</span><span class="sxs-lookup"><span data-stu-id="e84b0-103">Your Windows Forms applications can take advantage of the power management features in the Windows operating system.</span></span> <span data-ttu-id="e84b0-104">Aplikace můžete monitorovat stav napájení počítače a provést akci, když dojde ke změně stavu.</span><span class="sxs-lookup"><span data-stu-id="e84b0-104">Your applications can monitor the power status of a computer and take action when a status change occurs.</span></span> <span data-ttu-id="e84b0-105">Pokud vaše aplikace běží na přenosného počítače, můžete chtít zakázat některé funkce ve vaší aplikaci, když baterie počítače klesne pod určitou úroveň.</span><span class="sxs-lookup"><span data-stu-id="e84b0-105">For example, if your application is running on a portable computer, you might want to disable certain features in your application when the computer's battery charge falls under a certain level.</span></span>  
  
 <span data-ttu-id="e84b0-106">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Poskytuje <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> událostí, ke kterému dochází vždy, když dojde ke změně power stav, například pokud uživatel pozastaví nebo obnoví operačního systému, nebo při změně stavu napájení ze sítě nebo stav baterie.</span><span class="sxs-lookup"><span data-stu-id="e84b0-106">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] provides a <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> event that occurs whenever there is a change in power status, such as when a user suspends or resumes the operating system, or when the AC power status or battery status changes.</span></span> <span data-ttu-id="e84b0-107"><xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> Vlastnost <xref:System.Windows.Forms.SystemInformation> třídy lze použít k dotazu na aktuální stav, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="e84b0-107">The <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> property of the <xref:System.Windows.Forms.SystemInformation> class can be used to query for the current status, as shown in the following code example.</span></span>  
  
 [!code-csharp[PowerMode#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#1)]
 [!code-vb[PowerMode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#1)]  
  
 <span data-ttu-id="e84b0-108">Kromě <xref:System.Windows.Forms.BatteryChargeStatus> výčty, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> vlastnost také obsahuje výčty týkajících se kapacity baterie (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) a baterie účtují procento (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>).</span><span class="sxs-lookup"><span data-stu-id="e84b0-108">Besides the <xref:System.Windows.Forms.BatteryChargeStatus> enumerations, the <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> property also contains enumerations for determining battery capacity (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) and battery charge percentage (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>).</span></span>  
  
 <span data-ttu-id="e84b0-109">Můžete použít <xref:System.Windows.Forms.Application.SetSuspendState%2A> metodu <xref:System.Windows.Forms.Application> k přepnutí do počítače do režimu spánku nebo režimu spánku.</span><span class="sxs-lookup"><span data-stu-id="e84b0-109">You can use the <xref:System.Windows.Forms.Application.SetSuspendState%2A> method of the <xref:System.Windows.Forms.Application> to put a computer into hibernation or suspend mode.</span></span> <span data-ttu-id="e84b0-110">Pokud `force` argument je nastaven na hodnotu `false`, operační systém bude vysílání události pro všechny aplikace, které žádá o oprávnění pozastavit.</span><span class="sxs-lookup"><span data-stu-id="e84b0-110">If the `force` argument is set to `false`, the operating system will broadcast an event to all applications requesting permission to suspend.</span></span> <span data-ttu-id="e84b0-111">Pokud `disableWakeEvent` argument je nastaven na hodnotu `true`, operační systém zakáže všechny události probuzení.</span><span class="sxs-lookup"><span data-stu-id="e84b0-111">If the `disableWakeEvent` argument is set to `true`, the operating system disables all wake events.</span></span>  
  
 <span data-ttu-id="e84b0-112">Následující příklad kódu ukazuje, jak převést počítače do režimu hibernace.</span><span class="sxs-lookup"><span data-stu-id="e84b0-112">The following code example demonstrates how to put a computer into hibernation.</span></span>  
  
 [!code-csharp[PowerMode#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#2)]
 [!code-vb[PowerMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="e84b0-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="e84b0-113">See Also</span></span>  
 <xref:Microsoft.Win32.SystemEvents.PowerModeChanged>  
 <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>  
 <xref:System.Windows.Forms.Application.SetSuspendState%2A>  
 <xref:Microsoft.Win32.SystemEvents.SessionSwitch>
