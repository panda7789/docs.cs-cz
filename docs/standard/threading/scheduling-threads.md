---
title: "Plánování vláken"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], scheduling
- scheduling threads
ms.assetid: 67e4a0eb-3095-4ea7-b20f-908faa476277
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6bb715c11cc0d9b07e4ea8805ace7680ca92097c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="scheduling-threads"></a>Plánování vláken
Každé vlákno má přiřazen prioritu přístup z více vláken. Vlákna v rámci modul common language runtime vytvořili původně přiřazené priority **ThreadPriority.Normal**. Vlákna vytvořen vně modulu runtime zachovat prioritu, kterou měla před jejich zadali spravovaném prostředí. Můžete získat nebo nastavit prioritu všech vlákno se **Thread.Priority** vlastnost.  
  
 Vláken je naplánováno spuštění na základě jejich priority. I když vláken jsou prováděny v modulu runtime, všechna vlákna přiřazené řezy čas procesoru v operačním systému. Podrobnosti o plánování algoritmus používaný k určení pořadí, ve kterém jsou prováděny vláken se liší podle každý operační systém. V některých operačních systémů je vždy vlákno s nejvyšší prioritou (z těchto vláken, které mohou být provedeny) naplánovat na spuštění první. Pokud více vláken se stejnou prioritou jsou všechny dostupné scheduler procházení vláken, na který tuto prioritu, udělíte každé vlákno pevné časovém intervalu, do kterého chcete provést. Tak dlouho, dokud je k dispozici pro spouštění vlákna s vyšší prioritou, nižší prioritu vláken Nezískávat provést. Když na uvedenou prioritou nejsou žádné další spustitelného vláken, Plánovač přesune na další nižší prioritu a plány vláken, na který tuto prioritu pro provedení. Pokud bude spustitelného vyšší priorita vlákna, nižší prioritu vlákno je zrušené a vyšší prioritu vlákno je povoleno spustit znovu. Nad všechny který operační systém můžete také upravit vlákno priority dynamicky jako uživatelské rozhraní aplikace jsou přesouvána mezi popředí a na pozadí. Jinými operačními systémy můžete použít jiný algoritmus plánování.  
  
## <a name="see-also"></a>Viz také  
 [Použití vláken a dělení na vlákna](../../../docs/standard/threading/using-threads-and-threading.md)  
 [Dělení na spravovaná a nespravovaná vlákna ve Windows](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)
