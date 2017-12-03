---
title: "Koncový bod: Počet nezdařených volání za sekundu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8b41a1fba1c1630532524bb4d6bc759ec21e2865
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="endpoint-calls-failed-per-second"></a>Koncový bod: Počet nezdařených volání za sekundu
Název čítače: Počet nezdařených volání za sekundu.  
  
## <a name="description"></a>Popis  
 Počet volání, které mají neošetřené výjimky a tento koncový bod přijatých za sekundu.  
  
 Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.  
  
 (NE 1 - N 0) / ((D 1 - D 0) / F)  
  
 Hodnota tohoto čítače se zvýší pokaždé, když dojde k neošetřené výjimce na tento koncový bod.  
  
## <a name="see-also"></a>Viz také  
 [Určování a zpracování chyb v kontraktech a službách](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
