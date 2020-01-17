---
title: 'Koncový bod: Počet plynoucích transakcí za sekundu'
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: 39458dcb6ac033fd5084b5f2e760e0e26c345da7
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163550"
---
# <a name="endpoint-transactions-flowed-per-second"></a>Koncový bod: Počet plynoucích transakcí za sekundu
Název čítače: počet toků transakcí za sekundu.  
  
## <a name="description"></a>Popis  
 Počet transakcí, které byly v tomto koncovém bodu převedeny do operací za sekundu. Tento čítač se zvyšuje vždy, když se ve zprávě odeslané do koncového bodu nachází ID transakce.  
  
 Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), jehož hodnota se počítá pomocí následujícího vzorce.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
