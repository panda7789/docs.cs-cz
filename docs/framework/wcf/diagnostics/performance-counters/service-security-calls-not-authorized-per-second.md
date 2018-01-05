---
title: "Služba: Počet neautorizovaných volání zabezpečení za sekundu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1eeade5a-ea62-4757-b1f9-1b1b1746abd1
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: c6f03321ed77392342cbc5ee3c9cd5480f2d0455
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="service-security-calls-not-authorized-per-second"></a>Služba: Počet neautorizovaných volání zabezpečení za sekundu
Název čítače: zabezpečení volání není autorizovaný za sekundu  
  
## <a name="description"></a>Popis  
 Počet příchozích zpráv v sekundu, které jsou od platného uživatele a správně chráněný, ale uživatel není oprávněn provést určité úlohy.  
  
 Hodnota tohoto čítače se zvýší, když <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> metoda vrátí `false`.  
  
 Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkId=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.  
  
 (NE 1 - N 0) / ((D 1 - D 0) / F)
