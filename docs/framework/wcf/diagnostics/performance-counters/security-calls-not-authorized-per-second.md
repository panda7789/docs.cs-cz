---
title: Počet neautorizovaných volání zabezpečení za sekundu
ms.date: 03/30/2017
ms.assetid: 0f189767-8c05-478a-8f0b-9228e5d351e5
ms.openlocfilehash: 2986ba241ef9b6c110a4742f77320469cdf5f07a
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163927"
---
# <a name="security-calls-not-authorized-per-second"></a>Počet neautorizovaných volání zabezpečení za sekundu
Název čítače: počet neautorizovaných volání zabezpečení za sekundu  
  
## <a name="description"></a>Popis  
 Počet volání, jejichž autorizace v této operaci se nezdařila, za sekundu.  
  
 Hodnota tohoto čítače se zvýší, když metoda <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> vrátí `false`. Indikuje, že příchozí zpráva pochází z platného uživatele a je správně chráněna, ale uživatel není autorizovaný k provádění konkrétních úkolů.  
  
 Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), jehož hodnota se počítá pomocí následujícího vzorce.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
