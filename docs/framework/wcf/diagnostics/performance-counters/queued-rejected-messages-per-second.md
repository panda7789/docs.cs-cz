---
title: Počet odmítnutých zpráv zařazených do fronty za sekundu
ms.date: 03/30/2017
ms.assetid: 77ea9aa3-b9e2-4a1d-a65e-5ca115ba0567
ms.openlocfilehash: 096e2188b13d0fd5a9be35e5e6473107a58c5566
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916184"
---
# <a name="queued-rejected-messages-per-second"></a>Počet odmítnutých zpráv zařazených do fronty za sekundu
Název čítače: Počet odmítnutých zpráv fronty za sekundu.  
  
## <a name="description"></a>Popis  
 Počet zpráv, které jsou odmítnuty zařazených do fronty přenosu v této službě za sekundu.  
  
 Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
