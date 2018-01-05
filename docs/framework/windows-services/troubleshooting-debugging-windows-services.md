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
# <a name="troubleshooting-debugging-windows-services"></a>Řešení potíží: Ladění služeb systému Windows
Když ladíte aplikaci služby pro Windows, služby a **Windows Service Manager** komunikovat. **Portálu Service Manager** spustí služby voláním <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda a potom počká 30 sekund <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda vrátí. Pokud metoda v tuto chvíli nezobrazí, správce ukazuje chybu, že službu nelze spustit.  
  
 Když ladíte <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda, jak je popsáno v [postupy: ladění aplikace služby systému Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), musíte být vědomi tohoto období 30 sekund. Zadáte-li zarážka v <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda a není krok přes něj 30 sekund, správce nebude spuštění služby.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Ladění aplikací služby systému Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [Úvod do aplikací služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
