---
title: 'Koncový bod: Počet neautorizovaných volání zabezpečení za sekundu'
ms.date: 03/30/2017
ms.assetid: c8a1547b-986b-45c1-b302-dea0cd4b516d
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 4cefdd7480c7d0e9475b1883e603d9db1f287d4a
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44186328"
---
# <a name="endpoint-security-calls-not-authorized-per-second"></a>Koncový bod: Počet neautorizovaných volání zabezpečení za sekundu
Název čítače: Zabezpečení počet neautorizovaných volání za sekundu.  
  
## <a name="description"></a>Popis  
 Počet příchozích zpráv v sekundy, které se od platného uživatele a správně chráněný, ale uživatel nemá oprávnění k provádění konkrétních úkolů.  
  
 Tento čítač se zvyšuje při <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> vrátí metoda `false`.  
  
 Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.  
  
 (N 1 - N 0) / ((D 1 - D 0) / F)
