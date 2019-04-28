---
title: 303 – UserDefinedInformationEventOccured
ms.date: 03/30/2017
ms.assetid: 5ed5acaf-3755-4417-92c4-4ebc8e854ca1
ms.openlocfilehash: 0b782b5ac0527b5acb3ebf0bf11c117563042495
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61595774"
---
# <a name="303---userdefinedinformationeventoccured"></a>303 – UserDefinedInformationEventOccured
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|303|  
|klíčová slova|Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerován z uživatelského kódu. Vývojáři mohou vygenerovat tuto událost, pokud dojde k vlastní informační událost ve své službě. To lze provést pomocí <xref:System.Diagnostics.Eventing> rozhraní API. Kromě toho je Ukázky WCF, která zabalí toto rozhraní API a ukazuje, jak se správně generovat této události.  
  
## <a name="message"></a>Zpráva  
 Název: %1, odkaz: %2, vytížení: %3  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|Název|`xs:string`|Uživatelem definovaný název události|  
|HostReference|`xs:string`|Hostované webové služby Toto pole jednoznačně identifikuje v hierarchii webové služby. Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName". Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".|  
|datová část|`xs:string`|Uživatelem definované datové části události.|
