---
title: 'Řešení potíží: Ladění služeb systému Windows'
ms.date: 03/30/2017
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
author: ghogen
manager: douge
ms.openlocfilehash: 77a0c19c2da2d1886beaf396650fa024fc1243a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="troubleshooting-debugging-windows-services"></a><span data-ttu-id="a9934-102">Řešení potíží: Ladění služeb systému Windows</span><span class="sxs-lookup"><span data-stu-id="a9934-102">Troubleshooting: Debugging Windows Services</span></span>
<span data-ttu-id="a9934-103">Když ladíte aplikaci služby pro Windows, služby a **Windows Service Manager** komunikovat.</span><span class="sxs-lookup"><span data-stu-id="a9934-103">When you debug a Windows service application, your service and the **Windows Service Manager** interact.</span></span> <span data-ttu-id="a9934-104">**Portálu Service Manager** spustí služby voláním <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda a potom počká 30 sekund <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda vrátí.</span><span class="sxs-lookup"><span data-stu-id="a9934-104">The **Service Manager** starts your service by calling the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and then waits 30 seconds for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method to return.</span></span> <span data-ttu-id="a9934-105">Pokud metoda v tuto chvíli nezobrazí, správce ukazuje chybu, že službu nelze spustit.</span><span class="sxs-lookup"><span data-stu-id="a9934-105">If the method does not return in this time, the manager shows an error that the service cannot be started.</span></span>  
  
 <span data-ttu-id="a9934-106">Když ladíte <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda, jak je popsáno v [postupy: ladění aplikace služby systému Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), musíte být vědomi tohoto období 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="a9934-106">When you debug the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method as described in [How to: Debug Windows Service Applications](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), you must be aware of this 30-second period.</span></span> <span data-ttu-id="a9934-107">Zadáte-li zarážka v <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda a není krok přes něj 30 sekund, správce nebude spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="a9934-107">If you place a breakpoint in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method and do not step through it in 30 seconds, the manager will not start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9934-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="a9934-108">See Also</span></span>  
 [<span data-ttu-id="a9934-109">Postupy: Ladění aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="a9934-109">How to: Debug Windows Service Applications</span></span>](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [<span data-ttu-id="a9934-110">Úvod do aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="a9934-110">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
