---
title: 203 – ClientParameterInspectorAfterCallInvoked
ms.date: 03/30/2017
ms.assetid: b9592212-07e2-43e0-8b00-affd195cf55a
ms.openlocfilehash: 57192b44a0c3babc77fcca13ad4a1433b85bfdd7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781937"
---
# <a name="203---clientparameterinspectoraftercallinvoked"></a>203 – ClientParameterInspectorAfterCallInvoked
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|203|  
|klíčová slova|Řešení potíží s ServiceModel|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerován po má Model služby `AfterCall` metodu na inspektoru parametru klienta.  
  
## <a name="message"></a>Zpráva  
 Dispečer vyvolal metodu 'AfterCall"na třídě ClientParameterInspector typu '%1'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|TypeName|`xs:string`|Celý název CLR typu vyvolaný inspector.|  
|HostReference|`xs:string`|Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby. Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName". Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".|  
|AppDomain|`xs:string`|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
