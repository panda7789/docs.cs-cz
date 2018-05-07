---
title: 301 – UserDefinedErrorOccurred
ms.date: 03/30/2017
ms.assetid: a0285d1c-550f-4c14-9c36-a96e97f1c4e4
ms.openlocfilehash: 6eb80d6f0b20af9aae6e7de5248323088e352b26
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="301---userdefinederroroccurred"></a>301 – UserDefinedErrorOccurred
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|301|  
|Klíčová slova|Řešení potíží, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring|  
|úroveň|Chyba|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerované z uživatelského kódu. Vývojáři mohou emitování tuto událost, pokud dojde k chybě s vlastní ve své služby. To lze provést pomocí <xref:System.Diagnostics.Eventing> rozhraní API. Kromě toho je WCF vzorku, který zabalí toto rozhraní API a ukazuje, jak správně emitování této události.  
  
## <a name="message"></a>Zpráva  
 Název: %1, Reference: %2, datové části: % 3  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Název|`xs:string`|Název uživatelem definované události.|  
|HostReference|`xs:string`|Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby. Formát je definovaný jako "virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName'. Příklad: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|datová část|`xs:string`|Uživatelem definované datové části události.|
