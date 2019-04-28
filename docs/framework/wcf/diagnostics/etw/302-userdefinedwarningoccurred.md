---
title: 302 – UserDefinedWarningOccurred
ms.date: 03/30/2017
ms.assetid: 8d1f0bf1-0151-45e6-be92-573d397b54de
ms.openlocfilehash: c70857951309ef54ba460e96e948c9320269d30f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61596749"
---
# <a name="302---userdefinedwarningoccurred"></a>302 – UserDefinedWarningOccurred
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|302|  
|klíčová slova|Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring|  
|úroveň|Upozornění|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerován z uživatelského kódu. Vývojáři můžou generování této události dojde-li uživatelem definované upozorňovací událost ve své službě. To lze provést pomocí <xref:System.Diagnostics.Eventing> rozhraní API. Kromě toho je Ukázky WCF, která zabalí toto rozhraní API a ukazuje, jak se správně generovat této události.  
  
## <a name="message"></a>Zpráva  
 Název: %1, odkaz: %2, vytížení: %3  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|Název|`xs:string`|Uživatelem definovaný název události.|  
|HostReference|`xs:string`|Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby. Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName". Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".|  
|datová část|`xs:string`|Uživatelem definované datové části události.|
