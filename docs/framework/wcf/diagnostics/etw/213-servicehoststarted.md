---
title: 213 – ServiceHostStarted
ms.date: 03/30/2017
ms.assetid: a6f7facc-342f-46bb-9d52-a470178ba6bb
ms.openlocfilehash: 819efa2e13c94e2c7a16c24f6ba9c7ef2b87ef8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781820"
---
# <a name="213---servicehoststarted"></a>213 – ServiceHostStarted
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|213|  
|klíčová slova|EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceHost|  
|úroveň|LogAlways|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerován při spuštění hostitele webové hostované služby. Obvykle se to stane, když je služba aktivovaná zpráva. Může také dojít, pokud služba je nakonfigurována na automatické spuštění.  
  
## <a name="message"></a>Zpráva  
 Třída ServiceHost byla spuštěna: '%1'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|Název typu služby|`xs:string`|Celý název CLR typu implementace služby.|  
|HostReference|`xs:string`|Hostované webové služby Toto pole jednoznačně identifikuje v hierarchii webové služby. Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName". Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".|  
|AppDomain|`xs:string`|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
