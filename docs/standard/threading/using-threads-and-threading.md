---
title: "Použití vláken a dělení na vlákna"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5bed13950a29cfa787ef8c9eb2608c6d74dfd49f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="using-threads-and-threading"></a>Použití vláken a dělení na vlákna
Témata v této části popisují vytváření a správu spravovaných vláknech, jak předat data do spravovaných vláknech a získat výsledky zpět a zrušení vláken a zpracování <xref:System.Threading.ThreadAbortException>.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vytváření vláken a předávání dat při spuštění](../../../docs/standard/threading/creating-threads-and-passing-data-at-start-time.md)  
 Popisuje a předvádí vytvoření spravovaných vláknech, včetně jak předat data do nové vláken a jak data nelze vrátit zpět.  
  
 [Pozastavování a obnovování vláken](../../../docs/standard/threading/pausing-and-resuming-threads.md)  
 Popisuje následky pozastavení a obnovení spravovaných vláken.  
  
 [Zničení vláken](../../../docs/standard/threading/destroying-threads.md)  
 Popisuje strukturu zničení spravovaných vláknech a jak bude zpracováván <xref:System.Threading.ThreadAbortException>.  
  
 [Plánování vláken](../../../docs/standard/threading/scheduling-threads.md)  
 Popisuje priority přístup z více vláken a jejich vliv na plánování přístup z více vláken.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Threading.Thread>  
 Poskytuje referenční dokumentaci pro <xref:System.Threading.Thread> třídy, která představuje spravované vlákno, v tom, zda pochází nespravovaného kódu nebo byl vytvořen ve spravované aplikaci.  
  
 <xref:System.Threading.ThreadStart>  
 Poskytuje referenční dokumentaci pro <xref:System.Threading.ThreadStart> delegáta, který představuje postupy vlákno bez parametrů.  
  
 <xref:System.Threading.ParameterizedThreadStart>  
 Poskytuje snadný způsob, jak předat data do postup přístup z více vláken, i když bez silného typování.  
  
## <a name="related-sections"></a>Související oddíly  
 [Vlákna a dělení na vlákna](../../../docs/standard/threading/threads-and-threading.md)  
 Poskytuje úvod do spravovaného dělení na vlákna.
