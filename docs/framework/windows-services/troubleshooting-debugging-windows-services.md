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
# <a name="troubleshooting-debugging-windows-services"></a>Řešení potíží: Ladění služeb systému Windows
Při ladění aplikace služby Windows, služby a **Windows Service Manager** pracovat. **Portálu Service Manager** spustí vaši službu voláním <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody a poté počká 30 sekund <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda vrátí. Pokud metoda nevrací v tuto chvíli, vedoucí ukazuje chybu, že službu nelze spustit.  
  
 Při ladění <xref:System.ServiceProcess.ServiceBase.OnStart%2A> způsob, jak je popsáno v [postupy: ladění aplikace služby Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), je třeba upozornit 30sekundové období. Pokud umístíte zarážku v <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda a Nekrokovat s vnořením přes něj během 30 sekund, správce nelze spustit službu.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Ladění aplikací služby systému Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [Úvod do aplikací služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
