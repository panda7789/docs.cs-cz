---
title: 'Služba: Počet neautorizovaných volání zabezpečení za sekundu'
ms.date: 03/30/2017
ms.assetid: 1eeade5a-ea62-4757-b1f9-1b1b1746abd1
author: BrucePerlerMS
ms.openlocfilehash: 17da19e88dfa837cc1e45d0b6af2ebdbfd00182c
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47198251"
---
# <a name="service-security-calls-not-authorized-per-second"></a>Služba: Počet neautorizovaných volání zabezpečení za sekundu
Název čítače: zabezpečení volání není autorizovaný za sekundu  
  
## <a name="description"></a>Popis  
 Počet příchozích zpráv v jedné sekundy, které jsou z platného uživatele a správně chráněný, ale uživatel nemá oprávnění k provádění konkrétních úkolů.  
  
 Tento čítač se zvyšuje při <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> vrátí metoda `false`.  
  
 Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkId=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.  
  
 (N 1 - N 0) / ((D 1 - D 0) / F)
