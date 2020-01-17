---
title: Počet plynoucích transakcí za sekundu
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: 8b6077af3f98f7a205772b4883dc122374083e00
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163823"
---
# <a name="transactions-flowed-per-second"></a>Počet plynoucích transakcí za sekundu
Název čítače: počet toků transakcí za sekundu  
  
## <a name="description"></a>Popis  
 Počet transakcí, které byly do této operace předávány za sekundu. Tento čítač se zvyšuje pokaždé, když se ve zprávě, která se pošle do operace, nachází ID transakce.  
  
 Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), jehož hodnota se počítá pomocí následujícího vzorce.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
