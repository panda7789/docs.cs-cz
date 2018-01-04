---
title: "Služba: Počet volání za sekundu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0880ce3674f41367c46f4d0268a5391cfda210ab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="service-calls-per-second"></a>Služba: Počet volání za sekundu
Název čítače: Počet volání za sekundu.  
  
## <a name="description"></a>Popis  
 Počet volání k této službě za sekundu.  
  
 Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.  
  
 (Ne 1 - N 0) / ((D 1 -D 0) / F) kde čítači (ne) představuje počet operací prováděné během posledního ukázkového intervalu, představuje jmenovatel (D) během posledního ukázkového intervalu, uplynulý čas počet rysky a F je četnost o rysky.
