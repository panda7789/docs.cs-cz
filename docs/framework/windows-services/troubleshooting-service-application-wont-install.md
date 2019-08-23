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
ms.openlocfilehash: d04a0ddcef9ff7c31abd422f7f9fba34e804d2b1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935417"
---
# <a name="troubleshooting-service-application-wont-install"></a>Řešení potíží: Aplikace služby se nenainstaluje
Pokud nebude aplikace služby správně nainstalována, zkontrolujte, <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> zda je vlastnost pro třídu služby nastavena na stejnou hodnotu, jako je uvedena v instalačním programu této služby. Aby se služba správně nainstalovala, musí být tato hodnota v obou instancích stejná.  
  
> [!NOTE]
> Můžete se také podívat na protokoly instalace a získat zpětnou vazbu k procesu instalace.  
  
 Měli byste také ověřit, jestli už máte nainstalovanou jinou službu se stejným názvem. Aby instalace proběhla úspěšně, musí být názvy služby jedinečné.  
  
## <a name="see-also"></a>Viz také:

- [Úvod do aplikací služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
