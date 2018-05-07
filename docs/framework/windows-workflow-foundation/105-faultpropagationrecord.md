---
title: 105 - FaultPropagationRecord
ms.date: 03/30/2017
ms.assetid: 168473b1-b1e5-4e9f-8a2a-35bbdb2ef531
ms.openlocfilehash: c48f42a91ad9a15b49aad8c1ab684f2348954174
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="105---faultpropagationrecord"></a>105 - FaultPropagationRecord
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|105|  
|Klíčová slova|EndToEndMonitoring, řešení potíží, HealthMonitoring, WFTracking|  
|úroveň|Upozornění|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerované účastníkem sledování, trasování událostí pro Windows, pokud aktivitu se k instanci pracovního postupu vysílá FaultPropagationRecord.  
  
## <a name="message"></a>Zpráva  
 TrackRecord = FaultPropagationRecord, ID instance = %1, RecordNumber = %2, EventTime = %3, FaultSourceActivityName = %4, FaultSourceActivityId = %5, FaultSourceActivityInstanceId = %6, FaultSourceActivityTypeName = %7, FaultHandlerActivityName = %8  FaultHandlerActivityId = %9, FaultHandlerActivityInstanceId = % 10, FaultHandlerActivityTypeName = % 11, chyby = % 12, IsFaultSource = 13, poznámky % = % 14, ProfileName = % 15  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|identifikátor instanceId|xs:GUID|Id instance pracovního postupu|  
|RecordNumber|xs:Long|Pořadové číslo emitovaného záznamu|  
|eventTime|xs|Čas v UTC při byl vygenerované události|  
|FaultSourceActivityName|xs:String|Název aktivity, která vygenerované poruchy|  
|FaultSourceActivityId|xs:String|Id aktivity, která vygenerované poruchy|  
|FaultSourceActivityInstanceId|xs:String|Id instance aktivity, která vygenerované poruchy|  
|FaultSourceActivityTypeName|xs:String|Typ aktivity, která vygenerované poruchy|  
|FaultHandlerActivityName|xs:String|Zobrazovaný název aktivity obslužnou rutinu chyby|  
|FaultHandlerActivityId|xs:String|Id aktivity obslužnou rutinu chyby|  
|FaultHandlerActivityInstanceId|xs:String|Id instance aktivity obslužnou rutinu chyby|  
|FaultHandlerActivityTypeName|xs:String|Typ aktivity obslužnou rutinu chyby|  
|Selhání|xs:String|V podrobnostech o chybě|  
|IsFaultSource|xs:unsignedByte|Označuje, pokud byl události vygenerované ze zdroje chyby|  
|Poznámky|xs:String|Poznámky, které byly přidány k této události.  Hodnoty jsou uloženy v elementu xml ve formátu \<položky >\< název položky = "annotationName" type="System.String" > annotationValue\</bodu > \< /položky >.  Pokud nejsou zadány žádné poznámky, pak řetězec obsahuje \<položky / >. Velikost události trasování událostí pro Windows je omezena velikost vyrovnávací paměti ETW nebo maximální datová část pro událost trasování událostí pro Windows. Pokud velikost události překročila omezení trasování událostí pro Windows, pak tato událost je rozdělená do odstranit poznámky a nahraďte hodnoty anotace s \<položky >...  \< /položky >.|  
|ProfileName|xs:String|Název nebo sledování profil, který způsobil v tomto případě se vygenerované|  
|HostReference|xs:String|Webové hostované služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.  Formát je definován jako ' virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName' Příklad: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
