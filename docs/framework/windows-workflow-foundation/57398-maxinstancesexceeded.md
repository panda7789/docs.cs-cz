---
title: 57398 - MaxInstancesExceeded
ms.date: 03/30/2017
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
ms.openlocfilehash: d644c25ec2dee06eea4a5fb66c30792bb650f252
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="57398---maxinstancesexceeded"></a>57398 - MaxInstancesExceeded
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|57398|  
|Klíčová slova|WFServices|  
|úroveň|Upozornění|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Označuje, že systém dosáhl limit nastavený pro omezení 'MaxConcurrentInstances'.  
  
## <a name="message"></a>Zpráva  
 Systém dosáhl limit nastavený pro omezení 'MaxConcurrentInstances'. Limit pro toto omezení byla nastavena na %1. Hodnota omezení lze změnit úpravou atribut 'maxConcurrentInstances' v omezení ServiceThrottle s hodnotou elementu nebo úpravou vlastnosti 'MaxConcurrentInstances' na chování třídy ServiceThrottlingBehavior.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Název|xs:String|Název položky.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
