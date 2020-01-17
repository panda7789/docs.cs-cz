---
title: 'Koncový bod: počet neautorizovaných volání zabezpečení za sekundu'
ms.date: 03/30/2017
ms.assetid: c8a1547b-986b-45c1-b302-dea0cd4b516d
ms.openlocfilehash: 8c287ef4c156bb0a76a4b1d08b0d70b40bd76229
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163173"
---
# <a name="endpoint-security-calls-not-authorized-per-second"></a>Koncový bod: počet neautorizovaných volání zabezpečení za sekundu
Název čítače: počet neautorizovaných volání zabezpečení za sekundu  
  
## <a name="description"></a>Popis  
 Počet příchozích zpráv za sekundu, které jsou z platného uživatele a správně chráněny, ale uživatel nemá oprávnění provádět konkrétní úkoly.  
  
 Hodnota tohoto čítače se zvýší, když metoda <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> vrátí `false`.  
  
 Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), jehož hodnota se počítá pomocí následujícího vzorce.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
