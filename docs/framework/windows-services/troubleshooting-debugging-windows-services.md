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
# <a name="troubleshooting-debugging-windows-services"></a>Řešení potíží: Ladění služeb systému Windows
Když ladíte aplikaci služby systému Windows, vaše služba a **Windows Service Manager** interakci. **Service Manager** spustí vaši službu voláním <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody a potom počká 30 sekund, než se <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda vrátí. Pokud se metoda v tomto čase nevrátí, správce zobrazí chybu, kterou nelze spustit.  
  
 Při ladění <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody, jak je popsáno v tématu [Postupy: ladění aplikací služby systému Windows](how-to-debug-windows-service-applications.md), je třeba si uvědomit toto 30 sekundové období. Pokud zaškrtnete zarážku v <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodě a nechcete ji krokovat během 30 sekund, správce službu nespustí.  
  
## <a name="see-also"></a>Viz také

- [Postupy: Ladění aplikací služby systému Windows](how-to-debug-windows-service-applications.md)
- [Úvod do aplikací služby systému Windows](introduction-to-windows-service-applications.md)
