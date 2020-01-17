---
title: 'Služba: Počet neautorizovaných volání zabezpečení za sekundu'
ms.date: 03/30/2017
ms.assetid: 1eeade5a-ea62-4757-b1f9-1b1b1746abd1
ms.openlocfilehash: 964eff97a58ab7d5a68dbc1891473ae8d04a50ad
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163875"
---
# <a name="service-security-calls-not-authorized-per-second"></a>Služba: Počet neautorizovaných volání zabezpečení za sekundu
Název čítače: počet neautorizovaných volání zabezpečení za sekundu  
  
## <a name="description"></a>Popis  
 Počet příchozích zpráv za sekundu, které jsou z platného uživatele a správně chráněny, ale uživatel není autorizovaný k provádění konkrétních úkolů.  
  
 Hodnota tohoto čítače se zvýší, když metoda <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> vrátí `false`.  
  
 Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), jehož hodnota se počítá pomocí následujícího vzorce.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
