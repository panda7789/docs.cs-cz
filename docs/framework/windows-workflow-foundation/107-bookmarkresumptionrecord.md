---
title: 107 – BookmarkResumptionRecord
ms.date: 03/30/2017
ms.assetid: aa2d37ed-2bfa-439b-89e8-a9354027f155
ms.openlocfilehash: 860ed7cc065a862d100b0a8c6a88458e61930b9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513045"
---
# <a name="107----bookmarkresumptionrecord"></a>107 – BookmarkResumptionRecord
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|107|  
|Klíčová slova|EndToEndMonitoring, řešení potíží, HealthMonitoring, WFTracking|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vysílaných účastník sledování ETW při BookmarkResumptionRecord vysílá instanci pracovního postupu.  
  
## <a name="message"></a>Zpráva  
 TrackRecord = BookmarkResumptionRecord, ID instance = %1, RecordNumber = %2, EventTime = %3, název = %4, SubInstanceID = %5, hodnota vlastnosti OwnerActivityName = %6, OwnerActivityId = %7, OwnerActivityInstanceId = %8, OwnerActivityTypeName = %9, poznámky = % 10, ProfileName = % 11  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|identifikátor instanceId|xs:GUID|Id instance pracovního postupu|  
|RecordNumber|xs:Long|Pořadové číslo emitovaného záznamu|  
|eventTime|xs|Čas v UTC při byl vygenerované události|  
|Název|xs:String|Název záložka, která byla obnovena|  
|SubInstanceID|xs:GUID|Id oboru záložek|  
|Hodnota vlastnosti OwnerActivityName|xs:String|Název aktivity záložek|  
|OwnerActivityId|xs:String|Id aktivity záložek|  
|OwnerActivityInstanceId|xs:String|Id instance aktivity záložek|  
|OwnerActivityTypeName|xs:String|Typ aktivity záložek|  
|Poznámky|xs:String|Poznámky, které byly přidány k této události.  Hodnoty jsou uloženy v elementu xml ve formátu \<položky >\< název položky = "annotationName" type="System.String" > annotationValue\</bodu > \< /položky >.  Pokud nejsou zadány žádné poznámky, pak řetězec obsahuje \<položky / >. Velikost události trasování událostí pro Windows je omezena velikost vyrovnávací paměti ETW nebo maximální datová část pro událost trasování událostí pro Windows. Pokud velikost události překročila omezení trasování událostí pro Windows, pak tato událost je rozdělená do odstranit poznámky a nahraďte hodnoty anotace s \<položky >...  \< /položky >.|  
|ProfileName|xs:String|Název nebo sledování profil, který způsobil v tomto případě se vygenerované|  
|HostReference|xs:String|Webové hostované služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.  Formát je definován jako ' virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName' Příklad: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
