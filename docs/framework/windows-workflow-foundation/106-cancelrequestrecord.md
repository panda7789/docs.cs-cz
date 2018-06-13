---
title: 106 - CancelRequestRecord
ms.date: 03/30/2017
ms.assetid: f72a59aa-8093-4a8e-94df-40acaffb1ffb
ms.openlocfilehash: 4d2e9bd271c04a9e26150e7dddffc33963dfe0a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515131"
---
# <a name="106---cancelrequestrecord"></a>106 - CancelRequestRecord
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|106|  
|Klíčová slova|EndToEndMonitoring, řešení potíží, HealthMonitoring, WFTracking|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerované účastníkem sledování, trasování událostí pro Windows, když aktivita v rámci instance pracovního postupu vysílá cancelrequestedrecord.  
  
## <a name="message"></a>Zpráva  
 TrackRecord = CancelRequestedRecord, ID instance = %1, RecordNumber = %2, EventTime = %3, název = %4, ID = %5, ActivityInstanceId = %6, ActivityTypeName = %7, ChildActivityName = %8, ChildActivityId = %9, ChildActivityInstanceId = % 10, ChildActivityTypeName = % 11, poznámky = ProfileName 12, % = % 13  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|identifikátor instanceId|xs:GUID|Id instance pracovního postupu|  
|RecordNumber|xs:Long|Pořadové číslo emitovaného záznamu|  
|eventTime|xs|Čas v UTC při byl vygenerované události|  
|Název|xs:String|Název aktivity, která požadována operace zrušení|  
|ID aktivity|xs:String|Id aktivity, která požadována operace zrušení|  
|ActivityInstanceId|xs:String|Id instance aktivity, která požadována operace zrušení|  
|ActivityTypeName|xs:String|Typ aktivity, která požadována operace zrušení|  
|ChildActivityName|xs:String|Název aktivity probíhá její zrušení|  
|ChildActivityId|xs:String|Id aktivity probíhá její zrušení|  
|ChildActivityInstanceId|xs:String|Id instance aktivity probíhá její zrušení|  
|ChildActivityTypeName|xs:String|Typ aktivity probíhá její zrušení|  
|Poznámky|xs:String|Poznámky, které byly přidány k této události.  Hodnoty jsou uloženy v elementu xml ve formátu \<položky >\< název položky = "annotationName" type="System.String" > annotationValue\</bodu > \< /položky >.  Pokud nejsou zadány žádné poznámky, pak řetězec obsahuje \<položky / >. Velikost události trasování událostí pro Windows je omezena velikost vyrovnávací paměti ETW nebo maximální datová část pro událost trasování událostí pro Windows. Pokud velikost události překročila omezení trasování událostí pro Windows, pak tato událost je rozdělená do odstranit poznámky a nahraďte hodnoty anotace s \<položky >...  \< /položky >.|  
|ProfileName|xs:String|Název nebo sledování profil, který způsobil v tomto případě se vygenerované|  
|HostReference|xs:String|Webové hostované služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.  Formát je definován jako ' virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName' Příklad: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
