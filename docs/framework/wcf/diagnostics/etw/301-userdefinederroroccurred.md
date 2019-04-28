---
title: 301 – UserDefinedErrorOccurred
ms.date: 03/30/2017
ms.assetid: a0285d1c-550f-4c14-9c36-a96e97f1c4e4
ms.openlocfilehash: 6eb80d6f0b20af9aae6e7de5248323088e352b26
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61596476"
---
# <a name="301---userdefinederroroccurred"></a>301 – UserDefinedErrorOccurred
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|301|  
|klíčová slova|Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring|  
|úroveň|Chyba|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerován z uživatelského kódu. Vývojáři mohou vygenerovat tuto událost, pokud dojde k chybě s uživatelem definované ve své službě. To lze provést pomocí <xref:System.Diagnostics.Eventing> rozhraní API. Kromě toho je Ukázky WCF, která zabalí toto rozhraní API a ukazuje, jak se správně generovat této události.  
  
## <a name="message"></a>Zpráva  
 Název: %1, odkaz: %2, vytížení: %3  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|Název|`xs:string`|Uživatelem definovaný název události.|  
|HostReference|`xs:string`|Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby. Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName". Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".|  
|datová část|`xs:string`|Uživatelem definované datové části události.|
