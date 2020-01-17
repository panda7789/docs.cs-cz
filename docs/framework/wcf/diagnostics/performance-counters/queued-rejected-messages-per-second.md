---
title: Počet odmítnutých zpráv zařazených do fronty za sekundu
ms.date: 03/30/2017
ms.assetid: 77ea9aa3-b9e2-4a1d-a65e-5ca115ba0567
ms.openlocfilehash: 805b4f5d1e7882f38cfcc76ad63451d735389d5f
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163966"
---
# <a name="queued-rejected-messages-per-second"></a>Počet odmítnutých zpráv zařazených do fronty za sekundu
Název čítače: odmítnuté zprávy zařazené do fronty za sekundu.  
  
## <a name="description"></a>Popis  
 Počet zpráv, které byly v této službě odmítnuty přenosem ve frontě za sekundu.  
  
 Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), jehož hodnota se počítá pomocí následujícího vzorce.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
