---
title: 'Řešení potíží: Aplikace služby se nenainstaluje'
description: Řešení potíží, pokud se aplikace služby nenainstaluje Přesvědčte se, zda je správně nastavena vlastnost ServiceName pro třídu služby.
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
ms.openlocfilehash: 4a57fb6975a6ded48abf7c8fd7eacec16e4f94d8
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925524"
---
# <a name="troubleshooting-service-application-wont-install"></a>Řešení potíží: Aplikace služby se nenainstaluje
Pokud nebude aplikace služby správně nainstalována, zkontrolujte, zda je <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> vlastnost pro třídu služby nastavena na stejnou hodnotu, jako je uvedena v instalačním programu této služby. Aby se služba správně nainstalovala, musí být tato hodnota v obou instancích stejná.  
  
> [!NOTE]
> Můžete se také podívat na protokoly instalace a získat zpětnou vazbu k procesu instalace.  
  
 Měli byste také ověřit, jestli už máte nainstalovanou jinou službu se stejným názvem. Aby instalace proběhla úspěšně, musí být názvy služby jedinečné.  
  
## <a name="see-also"></a>Viz také

- [Představení aplikací spouštěných jako služby systému Windows](introduction-to-windows-service-applications.md)
