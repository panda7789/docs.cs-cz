---
title: 100 – WorkflowInstanceRecord
ms.date: 03/30/2017
ms.assetid: ed4d1851-b378-489b-a22d-c1db09571fb4
ms.openlocfilehash: c7abb2c59c65e0b0f4c4f209e3c7c2d0cf4641d7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008665"
---
# <a name="100---workflowinstancerecord"></a>100 – WorkflowInstanceRecord
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|100|  
|klíčová slova|EndToEndMonitoring, řešení potíží, HealthMonitoring, WFTracking|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerován pomocí účastník sledování ETW při instance pracovního postupu vysílá WorkflowInstanceRecord pro stavy pracovního postupu: Spustí, pokračuje, jako trvalý, nečinný, odstraní, dokončena, zrušena uvolněna, nezruší.  
  
## <a name="message"></a>Zpráva  
 TrackRecord= WorkflowInstanceRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, State = %5, Annotations = %6, ProfileName = %7  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|Id instance pracovního postupu|  
|Číslo záznamu|xs:long|Pořadové číslo emitovaný záznamu|  
|čas události|xs:dateTime|Čas ve standardu UTC, kdy události, protože ho|  
|ActivityDefinitionId|xs:string|Název kořenové aktivity v pracovním postupu|  
|Stav|xs:string|Aktuální stav pracovního postupu.|  
|Poznámky|xs:string|Poznámky, které byly přidány k této události.  Hodnoty jsou uloženy v elementu xml ve formátu \<položky >\< název položky = "annotationName" type="System.String" > annotationValue\</položky > \< /položky >.  Pokud nejsou zadány žádné poznámky, pak řetězec obsahuje \<položky / >. Velikost události ETW je omezená velikost vyrovnávací paměti trasování událostí pro Windows nebo max datovou část události trasování událostí pro Windows. Pokud velikost události větší než omezení trasování událostí pro Windows, pak události je rozdělená do odstranit poznámky a nahraďte hodnoty anotace s \<položky >...  \< /položky >.|  
|ProfileName|xs:string|Název nebo sledování profil, který je v tomto případě probíhá emitovány|  
|HostReference|xs:string|Hostované webové služby Toto pole jednoznačně identifikuje v hierarchii webové služby.  Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName' Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
