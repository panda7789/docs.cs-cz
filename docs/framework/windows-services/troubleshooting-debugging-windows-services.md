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
# <a name="troubleshooting-debugging-windows-services"></a>Řešení potíží: Ladění služeb systému Windows
Když ladíte aplikaci služby pro Windows, služby a **Windows Service Manager** komunikovat. **Portálu Service Manager** spustí služby voláním <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda a potom počká 30 sekund <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda vrátí. Pokud metoda v tuto chvíli nezobrazí, správce ukazuje chybu, že službu nelze spustit.  
  
 Když ladíte <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda, jak je popsáno v [postupy: ladění aplikace služby systému Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), musíte být vědomi tohoto období 30 sekund. Zadáte-li zarážka v <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda a není krok přes něj 30 sekund, správce nebude spuštění služby.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Ladění aplikací služby systému Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [Úvod do aplikací služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
