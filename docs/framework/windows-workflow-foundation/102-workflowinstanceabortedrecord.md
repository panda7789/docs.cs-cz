---
title: 102 - WorkflowInstanceAbortedRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bde4378d-4eea-4907-aaf2-c1a2bc770a37
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f47d94f41880e3463df883f94c2ff43e927a1001
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="102---workflowinstanceabortedrecord"></a>102 - WorkflowInstanceAbortedRecord
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|102|  
|Klíčová slova|EndToEndMonitoring, řešení potíží, HealthMonitoring, WFTracking|  
|úroveň|Upozornění|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace nebo analytické|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerované účastníkem sledování, trasování událostí pro Windows, když WorkflowInstanceAbortedRecord vysílá instanci pracovního postupu.  
  
## <a name="message"></a>Zpráva  
 TrackRecord = WorkflowInstanceAbortedRecord, ID instance = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, důvod = %5, poznámky = %6, ProfileName = %7  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|identifikátor instanceId|xs:GUID|Id instance pracovního postupu|  
|RecordNumber|xs:Long|Pořadové číslo emitovaného záznamu|  
|eventTime|xs|Čas v UTC při byl vygenerované události|  
|ActivityDefinitionId|xs:String|Název kořenové aktivity v pracovním postupu|  
|Důvod|xs:String|Byla přerušena z důvodu pracovního postupu|  
|Poznámky|xs:String|Poznámky, které byly přidány k této události.  Hodnoty jsou uloženy v elementu xml ve formátu \<položky >\< název položky = "annotationName" type="System.String" > annotationValue\</bodu > \< /položky >.  Pokud nejsou zadány žádné poznámky, pak řetězec obsahuje \<položky / >. Velikost události trasování událostí pro Windows je omezena velikost vyrovnávací paměti ETW nebo maximální datová část pro událost trasování událostí pro Windows. Pokud velikost události překročila omezení trasování událostí pro Windows, pak tato událost je rozdělená do odstranit poznámky a nahraďte hodnoty anotace s \<položky >...  \< /položky >.|  
|ProfileName|xs:String|Název nebo sledování profil, který způsobil v tomto případě se vygenerované|  
|HostReference|xs:String|Webové hostované služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.  Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName' Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
