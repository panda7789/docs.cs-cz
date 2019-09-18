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
ms.openlocfilehash: c45ab03ec4577d88953b0e43531082a46c29e8fd
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053537"
---
# <a name="troubleshooting-service-application-wont-install"></a>Řešení potíží: Aplikace služby se nenainstaluje
Pokud nebude aplikace služby správně nainstalována, zkontrolujte, <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> zda je vlastnost pro třídu služby nastavena na stejnou hodnotu, jako je uvedena v instalačním programu této služby. Aby se služba správně nainstalovala, musí být tato hodnota v obou instancích stejná.  
  
> [!NOTE]
> Můžete se také podívat na protokoly instalace a získat zpětnou vazbu k procesu instalace.  
  
 Měli byste také ověřit, jestli už máte nainstalovanou jinou službu se stejným názvem. Aby instalace proběhla úspěšně, musí být názvy služby jedinečné.  
  
## <a name="see-also"></a>Viz také:

- [Úvod do aplikací služby systému Windows](introduction-to-windows-service-applications.md)
