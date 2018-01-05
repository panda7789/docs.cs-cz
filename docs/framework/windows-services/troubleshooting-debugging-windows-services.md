---
title: "Řešení potíží: Ladění služeb systému Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- troubleshooting service applications
- services, troubleshooting
- troubleshooting debugging, Windows Services
- Windows Service applications, debugging
- services, debugging
- Windows Service applications, troubleshooting
ms.assetid: cf859d4c-f04c-4cb7-81e3-bc7de8bea190
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: f38e65e93d4e6668795bf254573993d5100e2328
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-debugging-windows-services"></a><span data-ttu-id="2a7d2-102">Řešení potíží: Ladění služeb systému Windows</span><span class="sxs-lookup"><span data-stu-id="2a7d2-102">Troubleshooting: Debugging Windows Services</span></span>
<span data-ttu-id="2a7d2-103">Když ladíte aplikaci služby pro Windows, služby a **Windows Service Manager** komunikovat.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-103">When you debug a Windows service application, your service and the **Windows Service Manager** interact.</span></span> <span data-ttu-id="2a7d2-104">**Portálu Service Manager** spustí služby voláním <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda a potom počká 30 sekund <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda vrátí.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-104">The **Service Manager** starts your service by calling the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and then waits 30 seconds for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method to return.</span></span> <span data-ttu-id="2a7d2-105">Pokud metoda v tuto chvíli nezobrazí, správce ukazuje chybu, že službu nelze spustit.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-105">If the method does not return in this time, the manager shows an error that the service cannot be started.</span></span>  
  
 <span data-ttu-id="2a7d2-106">Když ladíte <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda, jak je popsáno v [postupy: ladění aplikace služby systému Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), musíte být vědomi tohoto období 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-106">When you debug the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method as described in [How to: Debug Windows Service Applications](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), you must be aware of this 30-second period.</span></span> <span data-ttu-id="2a7d2-107">Zadáte-li zarážka v <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda a není krok přes něj 30 sekund, správce nebude spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="2a7d2-107">If you place a breakpoint in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method and do not step through it in 30 seconds, the manager will not start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a7d2-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="2a7d2-108">See Also</span></span>  
 [<span data-ttu-id="2a7d2-109">Postupy: Ladění aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="2a7d2-109">How to: Debug Windows Service Applications</span></span>](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [<span data-ttu-id="2a7d2-110">Úvod do aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="2a7d2-110">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
