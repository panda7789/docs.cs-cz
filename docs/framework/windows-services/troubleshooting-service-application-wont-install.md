---
title: 'Řešení potíží: Služba aplikace získané&#39;t instalace'
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
ms.openlocfilehash: 998c7a3f5ca405b3bd66b877d027126f6c76cc15
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494415"
---
# <a name="troubleshooting-service-application-won39t-install"></a>Řešení potíží: Služba aplikace získané&#39;t instalace
Pokud vaše aplikace služby se nenainstaluje správně, zkontrolujte, ujistěte se, že <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> pro třídu služby je nastavena na stejnou hodnotu uvedené v instalačním programu pro danou službu. Hodnota musí být stejné v obou případech v pořadí pro vaši službu nenainstaluje správně.  
  
> [!NOTE]
>  Můžete se také podívat na protokoly instalace získat zpětnou vazbu týkající se procesu instalace.  
  
 Měli byste zkontrolovat také k určení, jestli máte jiné služby se stejným názvem už nainstalovaná. Názvy služeb musí být jedinečný pro aby byla instalace úspěšná.  
  
## <a name="see-also"></a>Viz také:
- [Úvod do aplikací služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
