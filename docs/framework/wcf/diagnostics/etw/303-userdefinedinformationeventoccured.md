---
title: 303 – UserDefinedInformationEventOccured
ms.date: 03/30/2017
ms.assetid: 5ed5acaf-3755-4417-92c4-4ebc8e854ca1
ms.openlocfilehash: 0b782b5ac0527b5acb3ebf0bf11c117563042495
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459137"
---
# <a name="303---userdefinedinformationeventoccured"></a>303 – UserDefinedInformationEventOccured
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|303|  
|Klíčová slova|Řešení potíží, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerované z uživatelského kódu. Vývojáři mohou emitování Tato událost při výskytu vlastní informační události ve své služby. To lze provést pomocí <xref:System.Diagnostics.Eventing> rozhraní API. Kromě toho je WCF vzorku, který zabalí toto rozhraní API a ukazuje, jak správně emitování této události.  
  
## <a name="message"></a>Zpráva  
 Název: %1, Reference: %2, datové části: % 3  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Název|`xs:string`|Uživatelem definovaný název události|  
|HostReference|`xs:string`|Webové hostované služby v tomto poli jednoznačně identifikuje v hierarchii webové služby. Formát je definovaný jako "virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName'. Příklad: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|datová část|`xs:string`|Uživatelem definované datové části události.|
