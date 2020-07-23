---
title: 'Řešení potíží: Ladění služeb systému Windows'
description: Začněte s laděním služeb systému Windows. Když ladíte aplikaci služby systému Windows, vaše služba a Windows Service Manager interakci.
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
ms.openlocfilehash: 935f5dcbd369ba5d723cc0e947ba708afdd590ea
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925537"
---
# <a name="troubleshooting-debugging-windows-services"></a><span data-ttu-id="a667c-104">Řešení potíží: Ladění služeb systému Windows</span><span class="sxs-lookup"><span data-stu-id="a667c-104">Troubleshooting: Debugging Windows Services</span></span>
<span data-ttu-id="a667c-105">Když ladíte aplikaci služby systému Windows, vaše služba a **Windows Service Manager** interakci.</span><span class="sxs-lookup"><span data-stu-id="a667c-105">When you debug a Windows service application, your service and the **Windows Service Manager** interact.</span></span> <span data-ttu-id="a667c-106">**Service Manager** spustí vaši službu voláním <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody a potom počká 30 sekund, než se <xref:System.ServiceProcess.ServiceBase.OnStart%2A> Metoda vrátí.</span><span class="sxs-lookup"><span data-stu-id="a667c-106">The **Service Manager** starts your service by calling the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and then waits 30 seconds for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method to return.</span></span> <span data-ttu-id="a667c-107">Pokud se metoda v tomto čase nevrátí, správce zobrazí chybu, kterou nelze spustit.</span><span class="sxs-lookup"><span data-stu-id="a667c-107">If the method does not return in this time, the manager shows an error that the service cannot be started.</span></span>  
  
 <span data-ttu-id="a667c-108">Při ladění <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody, jak je popsáno v tématu [Postupy: ladění aplikací služby systému Windows](how-to-debug-windows-service-applications.md), je třeba si uvědomit toto 30 sekundové období.</span><span class="sxs-lookup"><span data-stu-id="a667c-108">When you debug the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method as described in [How to: Debug Windows Service Applications](how-to-debug-windows-service-applications.md), you must be aware of this 30-second period.</span></span> <span data-ttu-id="a667c-109">Pokud zaškrtnete zarážku v <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodě a nechcete ji krokovat během 30 sekund, správce službu nespustí.</span><span class="sxs-lookup"><span data-stu-id="a667c-109">If you place a breakpoint in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method and do not step through it in 30 seconds, the manager will not start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a667c-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="a667c-110">See also</span></span>

- [<span data-ttu-id="a667c-111">Postupy: Ladění aplikací spouštěných jako služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="a667c-111">How to: Debug Windows Service Applications</span></span>](how-to-debug-windows-service-applications.md)
- [<span data-ttu-id="a667c-112">Představení aplikací spouštěných jako služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="a667c-112">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
