---
title: 210 - MessageThrottleExceeded
ms.date: 03/30/2017
ms.assetid: 24ca08ea-c11c-4753-946e-98aa820f8711
ms.openlocfilehash: 7ba5948b36642085ef44661b3d580e7f1c4102cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="210---messagethrottleexceeded"></a>210 - MessageThrottleExceeded
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|210|  
|Klíčová slova|EndToEndMonitoring, HealthMonitoring, řešení potíží s ServiceModel|  
|úroveň|Upozornění|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerované, pokud jeden tři hlavní služby se překročila omezení. Všimněte si, že tato událost je jenom vygenerované při počátečním překročení limitu omezení. Například pokud limit omezovače pro souběžných volání 10, 11 souběžných volání výsledky v `MessageThrottleExceeded` událostí. 12. volání nevede jinou událost. Kromě toho abyste se vyhnuli datového proudu aktivní událostí, aktivity, která bude umístěn kolem limit nevede jinou událost. V tomto příkladu je-li dokončit několik volání pak existují 9 souběžných volání. Pokud následně dva další volání mohou, aktuální hodnota je znovu 11. Výsledkem není jinou událost. Když aktuální hodnota klesne na 70 procent limit omezovače jsou vydávány jinou událost označující, že má zpomalení aktivity. Budoucí aktivity, která překračuje limit výsledků v jiném `MessageThrottleExceeded` se vygenerované události. V tomto příkladu, pokud množství souběžných volání spadá do 7 a poté opět dosáhne 11 a druhý `MessageThrottleExceeded` je vygenerované události.  
  
## <a name="message"></a>Zpráva  
 Bylo dosaženo limitu omezení '%1' z '%2'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Název omezení.|`xs:string`|Název omezení, která byla překročena. Buď `MaxConcurrentCalls`, `MaxConcurrentInstances`, nebo `MaxConcurrentSessions`,|  
|Limit|`xs:long`|Aktuálně nakonfigurovaný limit omezení.|  
|HostReference|`xs:string`|Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby. Formát je definovaný jako "virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName'. Příklad: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|Domény aplikace|`xs:string`|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
