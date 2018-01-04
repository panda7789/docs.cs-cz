---
title: "Řešení potíží: Won aplikace služby & č. 39; t instalace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- troubleshooting service applications
- services, troubleshooting
- services, debugging
- Windows NT services, troubleshooting
- troubleshooting NT services
- Windows Service applications, troubleshooting
ms.assetid: 45c48e2e-b97d-44bc-8896-14f328e0ce33
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 43c973d83d2d1b614cf0ce49ba8d4af24123b47e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-service-application-won39t-install"></a>Řešení potíží: Won aplikace služby & č. 39; t instalace
Pokud vaše aplikace služby se nenainstaluje správně, zkontrolujte, ujistěte se, že <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> pro třídu služby je nastavena na stejnou hodnotu znázorněné v instalačním programu pro danou službu. Hodnota musí být stejný v obou případech v pořadí pro vaši službu se správně nainstalovat.  
  
> [!NOTE]
>  Můžete také prohlédnout v protokolech instalace k získání zpětné vazby v procesu instalace.  
  
 Také byste měli zkontrolovat zjistit, jestli máte jiné služby se stejným názvem již nainstalován. Názvy služby musí být jedinečný pro instalace úspěšná.  
  
## <a name="see-also"></a>Viz také  
 [Úvod do aplikací služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
