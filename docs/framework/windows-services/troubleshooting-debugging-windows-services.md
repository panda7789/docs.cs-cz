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
# <a name="troubleshooting-debugging-windows-services"></a>Řešení potíží: Ladění služeb systému Windows
Když ladíte aplikaci služby systému Windows, vaše služba a **Windows Service Manager** interakci. **Service Manager** spustí vaši službu voláním <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody a potom počká 30 sekund, než se <xref:System.ServiceProcess.ServiceBase.OnStart%2A> Metoda vrátí. Pokud se metoda v tomto čase nevrátí, správce zobrazí chybu, kterou nelze spustit.  
  
 Při ladění <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody, jak je popsáno v tématu [Postupy: ladění aplikací služby systému Windows](how-to-debug-windows-service-applications.md), je třeba si uvědomit toto 30 sekundové období. Pokud zaškrtnete zarážku v <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodě a nechcete ji krokovat během 30 sekund, správce službu nespustí.  
  
## <a name="see-also"></a>Viz také

- [Postupy: Ladění aplikací spouštěných jako služby systému Windows](how-to-debug-windows-service-applications.md)
- [Představení aplikací spouštěných jako služby systému Windows](introduction-to-windows-service-applications.md)
