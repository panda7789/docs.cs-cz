---
title: "Počet odmítnutých zpráv zařazených do fronty za sekundu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77ea9aa3-b9e2-4a1d-a65e-5ca115ba0567
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ae182f63ad4c53d59700041d94ea0426cdff75c4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="queued-rejected-messages-per-second"></a>Počet odmítnutých zpráv zařazených do fronty za sekundu
Název čítače: Počet odmítnutých za sekundu zpráv zařazených do fronty.  
  
## <a name="description"></a>Popis  
 Počet zpráv, které jsou odmítnut zařazených do fronty přenosu v této služby za sekundu.  
  
 Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.  
  
 (NE 1 - N 0) / ((D 1 - D 0) / F)
