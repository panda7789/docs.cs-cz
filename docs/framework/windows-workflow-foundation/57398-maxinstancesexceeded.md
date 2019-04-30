---
title: 57398 – MaxInstancesExceeded
ms.date: 03/30/2017
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
ms.openlocfilehash: d644c25ec2dee06eea4a5fb66c30792bb650f252
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945961"
---
# <a name="57398---maxinstancesexceeded"></a>57398 – MaxInstancesExceeded
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|57398|  
|klíčová slova|WFServices|  
|úroveň|Upozornění|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Označuje, že systém dosáhl limitu nastaveného pro omezení "MaxConcurrentInstances".  
  
## <a name="message"></a>Zpráva  
 Systém dosáhl limitu nastaveného pro omezení "MaxConcurrentInstances". Limit pro toto omezení byl nastaven na hodnotu %1. Hodnotu omezení lze změnit úpravou atributu "maxConcurrentInstances' v elementu serviceThrottle nebo upravením vlastnosti 'MaxConcurrentInstances' v třídě chování ServiceThrottlingBehavior.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|Název|xs:string|Název položky.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
