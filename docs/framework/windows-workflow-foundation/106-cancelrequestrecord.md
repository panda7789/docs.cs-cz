---
title: 106 – CancelRequestRecord
ms.date: 03/30/2017
ms.assetid: f72a59aa-8093-4a8e-94df-40acaffb1ffb
ms.openlocfilehash: 4d2e9bd271c04a9e26150e7dddffc33963dfe0a5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924173"
---
# <a name="106---cancelrequestrecord"></a>106 – CancelRequestRecord
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|106|  
|klíčová slova|EndToEndMonitoring, řešení potíží, HealthMonitoring, WFTracking|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vyzařovaného účastník sledování ETW, když vysílá cancelrequestedrecord aktivitu v rámci instance pracovního postupu.  
  
## <a name="message"></a>Zpráva  
 Záznam sledování = CancelRequestedRecord, ID instance = %1, číslo záznamu = %2, čas události = %3, název = %4, ID aktivity = %5, ActivityInstanceId = %6, ActivityTypeName = %7, ChildActivityName = %8, ChildActivityId = %9, ChildActivityInstanceId = % 10 ChildActivityTypeName = % 11, poznámky = % 12, název profilu = % 13  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|Id instance pracovního postupu|  
|Číslo záznamu|xs:long|Pořadové číslo emitovaný záznamu|  
|čas události|xs:dateTime|Čas ve standardu UTC, kdy události, protože ho|  
|Název|xs:string|Název aktivity, která požadovanou operaci zrušení|  
|ID aktivity|xs:string|Id aktivity, která požadovanou operaci zrušení|  
|ActivityInstanceId|xs:string|Id instance aktivity, která požadovanou operaci zrušení|  
|ActivityTypeName|xs:string|Typ aktivity, která požadovanou operaci zrušení|  
|ChildActivityName|xs:string|Název aktivity rušení|  
|ChildActivityId|xs:string|Id aktivity rušení|  
|ChildActivityInstanceId|xs:string|Id instance aktivity rušení|  
|ChildActivityTypeName|xs:string|Typ aktivity rušení|  
|Poznámky|xs:string|Poznámky, které byly přidány k této události.  Hodnoty jsou uloženy v elementu xml ve formátu \<položky >\< název položky = "annotationName" type="System.String" > annotationValue\</položky > \< /položky >.  Pokud nejsou zadány žádné poznámky, pak řetězec obsahuje \<položky / >. Velikost události ETW je omezená velikost vyrovnávací paměti trasování událostí pro Windows nebo max datovou část události trasování událostí pro Windows. Pokud velikost události větší než omezení trasování událostí pro Windows, pak události je rozdělená do odstranit poznámky a nahraďte hodnoty anotace s \<položky >...  \< /položky >.|  
|ProfileName|xs:string|Název nebo sledování profil, který je v tomto případě probíhá emitovány|  
|HostReference|xs:string|Hostované webové služby Toto pole jednoznačně identifikuje v hierarchii webové služby.  Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName' Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
