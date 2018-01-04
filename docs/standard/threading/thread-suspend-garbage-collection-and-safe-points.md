---
title: "Thread.Suspend, kolekce paměti a bezpečné body"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- suspending threads
- safe points
- threading [.NET Framework], suspending
- threading [.NET Framework], garbage collection
- garbage collection, threads
ms.assetid: e8f58e17-2714-4821-802a-f8eb3b2baa62
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fdd56763712dee9c6fa1f292eb3bbb2f0ccbf505
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="threadsuspend-garbage-collection-and-safe-points"></a>Thread.Suspend, kolekce paměti a bezpečné body
Při volání <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> na vlákno, poznámky k systému, pozastavení vláken požaduje a umožňuje vlákno k provedení dokud nedosáhne bod bezpečné než ve skutečnosti pozastavení vlákno. Bod bezpečné pro vlákna je bod v jeho spuštění v paměti, které lze provést kolekce.  
  
 Jakmile bude dosaženo bod bezpečné, modul runtime zaručuje, že pozastavené vlákno nebude provádět žádné další průběh ve spravovaném kódu. Podproces provádění mimo spravovaný kód je vždy bezpečné pro uvolňování paměti a vykonávání pokračuje, dokud se pokusí pokračovat v provádění spravovaného kódu.  
  
> [!NOTE]
>  Chcete-li provést uvolnění paměti, musí modulu runtime pozastavit všechny vláken s výjimkou vláken provádění kolekce. Každé vlákno musí být převeden do bezpečného bodu předtím, než se může pozastavit.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.Thread>  
 <xref:System.GC>  
 [Dělení na vlákna](../../../docs/standard/threading/index.md)  
 [Automatická správa paměti](../../../docs/standard/automatic-memory-management.md)
