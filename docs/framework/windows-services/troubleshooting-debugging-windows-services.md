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
ms.openlocfilehash: 0dbbebd14ce0ff5f69a12c256238c7e0a02494cb
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47110941"
---
# <a name="troubleshooting-debugging-windows-services"></a><span data-ttu-id="ed4be-102">Řešení potíží: Ladění služeb systému Windows</span><span class="sxs-lookup"><span data-stu-id="ed4be-102">Troubleshooting: Debugging Windows Services</span></span>
<span data-ttu-id="ed4be-103">Při ladění aplikace služby Windows, služby a **Windows Service Manager** pracovat.</span><span class="sxs-lookup"><span data-stu-id="ed4be-103">When you debug a Windows service application, your service and the **Windows Service Manager** interact.</span></span> <span data-ttu-id="ed4be-104">**Portálu Service Manager** spustí vaši službu voláním <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody a poté počká 30 sekund <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda vrátí.</span><span class="sxs-lookup"><span data-stu-id="ed4be-104">The **Service Manager** starts your service by calling the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and then waits 30 seconds for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method to return.</span></span> <span data-ttu-id="ed4be-105">Pokud metoda nevrací v tuto chvíli, vedoucí ukazuje chybu, že službu nelze spustit.</span><span class="sxs-lookup"><span data-stu-id="ed4be-105">If the method does not return in this time, the manager shows an error that the service cannot be started.</span></span>  
  
 <span data-ttu-id="ed4be-106">Při ladění <xref:System.ServiceProcess.ServiceBase.OnStart%2A> způsob, jak je popsáno v [postupy: ladění aplikace služby Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), je třeba upozornit 30sekundové období.</span><span class="sxs-lookup"><span data-stu-id="ed4be-106">When you debug the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method as described in [How to: Debug Windows Service Applications](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), you must be aware of this 30-second period.</span></span> <span data-ttu-id="ed4be-107">Pokud umístíte zarážku v <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda a Nekrokovat s vnořením přes něj během 30 sekund, správce nelze spustit službu.</span><span class="sxs-lookup"><span data-stu-id="ed4be-107">If you place a breakpoint in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method and do not step through it in 30 seconds, the manager will not start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed4be-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="ed4be-108">See Also</span></span>  
 [<span data-ttu-id="ed4be-109">Postupy: Ladění aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="ed4be-109">How to: Debug Windows Service Applications</span></span>](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [<span data-ttu-id="ed4be-110">Úvod do aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="ed4be-110">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
