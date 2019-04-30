---
title: Počet neautorizovaných volání zabezpečení za sekundu
ms.date: 03/30/2017
ms.assetid: 0f189767-8c05-478a-8f0b-9228e5d351e5
ms.openlocfilehash: 15890506aece94a07d4b97101519007accf3570a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61915912"
---
# <a name="security-calls-not-authorized-per-second"></a>Počet neautorizovaných volání zabezpečení za sekundu
Název čítače: Počet neautorizovaných volání zabezpečení za sekundu.  
  
## <a name="description"></a>Popis  
 Počet volání, která se nezdařila autorizace pro tuto operaci za sekundu.  
  
 Tento čítač se zvyšuje při <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> vrátí metoda `false`. Označuje, že příchozí zprávu od platného uživatele a správně chráněný, ale uživatel nemá oprávnění k provádění konkrétních úkolů.  
  
 Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
