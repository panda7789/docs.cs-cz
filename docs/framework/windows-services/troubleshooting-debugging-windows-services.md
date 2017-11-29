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
ms.openlocfilehash: 51c28f6e9b6fa2974fb9861716b2c9fc2a38fe1a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-debugging-windows-services"></a>Řešení potíží: Ladění služeb systému Windows
Když ladíte aplikaci služby pro Windows, služby a **Windows Service Manager** komunikovat. **Portálu Service Manager** spustí služby voláním <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda a potom počká 30 sekund <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda vrátí. Pokud metoda v tuto chvíli nezobrazí, správce ukazuje chybu, že službu nelze spustit.  
  
 Když ladíte <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda, jak je popsáno v [postupy: ladění aplikace služby systému Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), musíte být vědomi tohoto období 30 sekund. Zadáte-li zarážka v <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda a není krok přes něj 30 sekund, správce nebude spuštění služby.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: ladění aplikace služby systému Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [Úvod do aplikace služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
