---
title: 210 - MessageThrottleExceeded
ms.date: 03/30/2017
ms.assetid: 24ca08ea-c11c-4753-946e-98aa820f8711
ms.openlocfilehash: 7ba5948b36642085ef44661b3d580e7f1c4102cb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781876"
---
# <a name="210---messagethrottleexceeded"></a>210 - MessageThrottleExceeded
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|210|  
|klíčová slova|EndToEndMonitoring HealthMonitoring, řešení potíží s ServiceModel|  
|úroveň|Upozornění|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerován v případě, že jedna tři hlavní služby byly překročeny omezení. Všimněte si, že tato událost je vygenerován pouze při počátečním překročení limitu omezení. Například pokud limit omezovače pro souběžných volání je 10, 11 souběžných volání výsledky `MessageThrottleExceeded` událostí. 12. volání nemá za následek další události. Kromě toho se pokud chcete vyhnout datového proudu hlučného událostí, aktivity, která kolem limit nemá za následek další události. V tomto příkladu je-li dokončit několik volání pak existují 9 souběžných volání. Pokud následně dvě další volání budou přicházet, aktuální hodnota je znovu 11. To nemá za následek další události. Pokud aktuální hodnota spadá do 70 procent společností z žebříčku limit omezovače je vygenerován různé události, která označuje, že má aktivita zpomalit. Budoucí aktivity, která překračuje limit výsledků v jiném `MessageThrottleExceeded` je vyvolána událost. V tomto příkladu, pokud objem souběžných volání spadá do 7 a poté opět dosáhne 11 a druhý `MessageThrottleExceeded` událostí je vygenerován.  
  
## <a name="message"></a>Zpráva  
 Bylo dosaženo limitu omezení '%1' z '%2'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|Název omezení|`xs:string`|Název omezení, která byla překročena. Buď `MaxConcurrentCalls`, `MaxConcurrentInstances`, nebo `MaxConcurrentSessions`,|  
|Omezení|`xs:long`|Aktuálně nakonfigurovaný limit omezení.|  
|HostReference|`xs:string`|Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby. Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName". Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".|  
|AppDomain|`xs:string`|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
