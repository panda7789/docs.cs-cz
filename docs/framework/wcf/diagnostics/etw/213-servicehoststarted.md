---
title: 213 – ServiceHostStarted
ms.date: 03/30/2017
ms.assetid: a6f7facc-342f-46bb-9d52-a470178ba6bb
ms.openlocfilehash: 819efa2e13c94e2c7a16c24f6ba9c7ef2b87ef8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458471"
---
# <a name="213---servicehoststarted"></a>213 – ServiceHostStarted
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|213|  
|Klíčová slova|EndToEndMonitoring, HealthMonitoring, řešení potíží s ServiceHost|  
|úroveň|LogAlways|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerované při spuštění hostitele webové hostované služby. Obvykle se to stane, když služba je aktivován zprávu. Může také dojít, pokud služba je nakonfigurována na automatické spuštění.  
  
## <a name="message"></a>Zpráva  
 Hostitel služby spuštění: '%1'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Název typu služby|`xs:string`|Položka FullName CLR typu implementace služby.|  
|HostReference|`xs:string`|Webové hostované služby v tomto poli jednoznačně identifikuje v hierarchii webové služby. Formát je definovaný jako "virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName'. Příklad: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|Domény aplikace|`xs:string`|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
