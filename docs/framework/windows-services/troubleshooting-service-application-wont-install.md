---
title: 'Řešení potíží: Služby aplikace Won&#39;t instalace'
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
manager: douge
ms.openlocfilehash: 1f3e5674f9a52627efdc24d6c70c0ab16dcdbbbd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509657"
---
# <a name="troubleshooting-service-application-won39t-install"></a>Řešení potíží: Služby aplikace Won&#39;t instalace
Pokud vaše aplikace služby se nenainstaluje správně, zkontrolujte, ujistěte se, že <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> pro třídu služby je nastavena na stejnou hodnotu znázorněné v instalačním programu pro danou službu. Hodnota musí být stejný v obou případech v pořadí pro vaši službu se správně nainstalovat.  
  
> [!NOTE]
>  Můžete také prohlédnout v protokolech instalace k získání zpětné vazby v procesu instalace.  
  
 Také byste měli zkontrolovat zjistit, jestli máte jiné služby se stejným názvem již nainstalován. Názvy služby musí být jedinečný pro instalace úspěšná.  
  
## <a name="see-also"></a>Viz také  
 [Úvod do aplikací služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
