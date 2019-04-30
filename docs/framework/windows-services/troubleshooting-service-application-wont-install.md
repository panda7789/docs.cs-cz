---
title: 'Řešení potíží: Aplikace služby se nenainstaluje'
ms.date: 03/30/2017
helpviewer_keywords:
- troubleshooting service applications
- services, troubleshooting
- services, debugging
- Windows NT services, troubleshooting
- troubleshooting NT services
- Windows Service applications, troubleshooting
ms.assetid: 45c48e2e-b97d-44bc-8896-14f328e0ce33
author: ghogen
ms.openlocfilehash: f75a2f33ecde408d2d8e2f2343197ba56c4b8c21
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925096"
---
# <a name="troubleshooting-service-application-wont-install"></a>Řešení potíží: Aplikace služby se nenainstaluje
Pokud vaše aplikace služby se nenainstaluje správně, zkontrolujte, ujistěte se, že <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> pro třídu služby je nastavena na stejnou hodnotu uvedené v instalačním programu pro danou službu. Hodnota musí být stejné v obou případech v pořadí pro vaši službu nenainstaluje správně.  
  
> [!NOTE]
>  Můžete se také podívat na protokoly instalace získat zpětnou vazbu týkající se procesu instalace.  
  
 Měli byste zkontrolovat také k určení, jestli máte jiné služby se stejným názvem už nainstalovaná. Názvy služeb musí být jedinečný pro aby byla instalace úspěšná.  
  
## <a name="see-also"></a>Viz také:

- [Úvod do aplikací služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
