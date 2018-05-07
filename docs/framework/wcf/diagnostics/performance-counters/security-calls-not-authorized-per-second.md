---
title: Počet neautorizovaných volání zabezpečení za sekundu
ms.date: 03/30/2017
ms.assetid: 0f189767-8c05-478a-8f0b-9228e5d351e5
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: d8f04abc46a85f151108653b399c238e0275bf7d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="security-calls-not-authorized-per-second"></a>Počet neautorizovaných volání zabezpečení za sekundu
Název čítače: Zabezpečení počet neautorizovaných volání za sekundu.  
  
## <a name="description"></a>Popis  
 Počet volání, která se nezdařila autorizace v této operaci za sekundu.  
  
 Hodnota tohoto čítače se zvýší, když <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> metoda vrátí `false`. Znamená příchozí zprávu od platného uživatele a správně chráněný, ale uživatel není autorizovaný k provést určité úlohy.  
  
 Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.  
  
 (NE 1 - N 0) / ((D 1 - D 0) / F)
