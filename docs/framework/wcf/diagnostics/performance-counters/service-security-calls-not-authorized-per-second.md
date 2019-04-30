---
title: 'Služba: Počet neautorizovaných volání zabezpečení za sekundu'
ms.date: 03/30/2017
ms.assetid: 1eeade5a-ea62-4757-b1f9-1b1b1746abd1
ms.openlocfilehash: 523e5182ca661e170e5cba01d5221b5c38251959
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773324"
---
# <a name="service-security-calls-not-authorized-per-second"></a>Služba: Počet neautorizovaných volání zabezpečení za sekundu
Název čítače: Počet neautorizovaných volání zabezpečení za sekundu  
  
## <a name="description"></a>Popis  
 Počet příchozích zpráv v jedné sekundy, které jsou z platného uživatele a správně chráněný, ale uživatel nemá oprávnění k provádění konkrétních úkolů.  
  
 Tento čítač se zvyšuje při <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> vrátí metoda `false`.  
  
 Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkId=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
