---
title: 'Řešení potíží: Aplikace služby se nenainstaluje.'
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
ms.openlocfilehash: ecbaa3b2fb0e0fc85ed383385368617bf361f497
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55289424"
---
# <a name="troubleshooting-service-application-wont-install"></a>Řešení potíží: Aplikace služby se nenainstaluje.
Pokud vaše aplikace služby se nenainstaluje správně, zkontrolujte, ujistěte se, že <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> pro třídu služby je nastavena na stejnou hodnotu uvedené v instalačním programu pro danou službu. Hodnota musí být stejné v obou případech v pořadí pro vaši službu nenainstaluje správně.  
  
> [!NOTE]
>  Můžete se také podívat na protokoly instalace získat zpětnou vazbu týkající se procesu instalace.  
  
 Měli byste zkontrolovat také k určení, jestli máte jiné služby se stejným názvem už nainstalovaná. Názvy služeb musí být jedinečný pro aby byla instalace úspěšná.  
  
## <a name="see-also"></a>Viz také:
- [Úvod do aplikací služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
