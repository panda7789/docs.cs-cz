---
title: 224 – MessageThrottleAtSeventyPercent
ms.date: 03/30/2017
ms.assetid: 82bbbfd7-10d2-41fd-805d-2443b0c1b96b
ms.openlocfilehash: f70dc235e037b4f490a25866940fe2bccceae2a1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916302"
---
# <a name="224---messagethrottleatseventypercent"></a>224 – MessageThrottleAtSeventyPercent
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|224|  
|klíčová slova|EndToEndMonitoring HealthMonitoring, řešení potíží s ServiceModel|  
|úroveň|Upozornění|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Pokud jeden z omezení hlavní služby došlo k překročení, `MessageThrottleExceeded` událostí je vygenerován. Když zpomaluje zásobníku aktivit a aktuální hodnotu omezení je na 70 procent společností z žebříčku aktuální limit pak tato událost je vygenerován. Všimněte si, že tato událost je vygenerován pouze po zpomaluje jako aktivity. Pokud aktuální hodnota nějakou dobu umístěn na značce 70 procent, (například 70,69,70,71,70,69), pouze první výskyt 70 procent výsledků v události. Po této události je vygenerován, opakování v budoucnu bude omezovač překročení omezení vést `MessageThrottleExceeded` událostí.  
  
## <a name="message"></a>Zpráva  
 Limit omezení '%1' z '%2' je na 70 %%.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|Název omezení|`xs:string`|Název omezení, která byla překročena. Buď `MaxConcurrentCalls`, `MaxConcurrentInstances`, nebo `MaxConcurrentSessions`,|  
|Omezení|`xs:long`|Aktuálně nakonfigurovaný limit omezení.|  
|HostReference|`xs:string`|Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby. Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName". Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".|  
|AppDomain|`xs:string`|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
