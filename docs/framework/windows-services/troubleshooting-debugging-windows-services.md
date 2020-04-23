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
ms.openlocfilehash: cbedb0051cbb08c2875e145a2bad35ae4d02a74e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053500"
---
# <a name="troubleshooting-debugging-windows-services"></a><span data-ttu-id="e38eb-102">Řešení potíží: Ladění služeb systému Windows</span><span class="sxs-lookup"><span data-stu-id="e38eb-102">Troubleshooting: Debugging Windows Services</span></span>
<span data-ttu-id="e38eb-103">Když ladíte aplikaci služby systému Windows, vaše služba a **Windows Service Manager** interakci.</span><span class="sxs-lookup"><span data-stu-id="e38eb-103">When you debug a Windows service application, your service and the **Windows Service Manager** interact.</span></span> <span data-ttu-id="e38eb-104">**Service Manager** spustí vaši službu voláním <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody a potom počká 30 sekund, než se <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda vrátí.</span><span class="sxs-lookup"><span data-stu-id="e38eb-104">The **Service Manager** starts your service by calling the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and then waits 30 seconds for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method to return.</span></span> <span data-ttu-id="e38eb-105">Pokud se metoda v tomto čase nevrátí, správce zobrazí chybu, kterou nelze spustit.</span><span class="sxs-lookup"><span data-stu-id="e38eb-105">If the method does not return in this time, the manager shows an error that the service cannot be started.</span></span>  
  
 <span data-ttu-id="e38eb-106">Při ladění <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody, jak je popsáno v tématu [Postupy: ladění aplikací služby systému Windows](how-to-debug-windows-service-applications.md), je třeba si uvědomit toto 30 sekundové období.</span><span class="sxs-lookup"><span data-stu-id="e38eb-106">When you debug the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method as described in [How to: Debug Windows Service Applications](how-to-debug-windows-service-applications.md), you must be aware of this 30-second period.</span></span> <span data-ttu-id="e38eb-107">Pokud zaškrtnete zarážku v <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodě a nechcete ji krokovat během 30 sekund, správce službu nespustí.</span><span class="sxs-lookup"><span data-stu-id="e38eb-107">If you place a breakpoint in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method and do not step through it in 30 seconds, the manager will not start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e38eb-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="e38eb-108">See also</span></span>

- [<span data-ttu-id="e38eb-109">Postupy: Ladění aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="e38eb-109">How to: Debug Windows Service Applications</span></span>](how-to-debug-windows-service-applications.md)
- [<span data-ttu-id="e38eb-110">Úvod do aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="e38eb-110">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
