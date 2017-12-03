---
title: 104 - ActivityScheduledRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae202178-8fb1-4646-a3aa-18beeda8ff93
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 36196f6814081a059e4a04de0ee9f0dd42d79bbe
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="104---activityscheduledrecord"></a>104 - ActivityScheduledRecord
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|104|  
|Klíčová slova|EndToEndMonitoring, řešení potíží, HealthMonitoring, WFTracking|  
|úroveň|Informace o|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace nebo analytické|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerované účastníkem sledování, trasování událostí pro Windows, když aktivita v rámci instance pracovního postupu vysílá ActivityScheduledRecord  
  
## <a name="message"></a>Zpráva  
 TrackRecord = ActivityScheduledRecord, ID instance = %1, RecordNumber = %2, EventTime = %3, název = %4, ID = %5, ActivityInstanceId = %6, ActivityTypeName = %7, ChildActivityName = %8, ChildActivityId = %9, ChildActivityInstanceId = % 10, ChildActivityTypeName = % 11, poznámky = ProfileName 12, % = % 13  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|identifikátor instanceId|xs:GUID|Id instance pracovního postupu|  
|RecordNumber|xs:Long|Pořadové číslo emitovaného záznamu|  
|eventTime|xs|Čas v UTC při byl vygenerované události|  
|Název|xs:String|Název aktivity, která naplánované podřízené aktivity|  
|ID aktivity|xs:String|Id aktivity, která naplánované podřízené aktivity|  
|ActivityInstanceId|xs:String|Id instance aktivity, která naplánované podřízené aktivity|  
|ActivityTypeName|xs:String|Typ aktivity, která požadována operace zrušení|  
|ChildActivityName|xs:String|Název naplánované aktivity|  
|ChildActivityId|xs:String|Id naplánované aktivity|  
|ChildActivityInstanceId|xs:String|Id instance naplánované aktivity|  
|ChildActivityTypeName|xs:String|Typ naplánované aktivity|  
|Poznámky|xs:String|Poznámky, které byly přidány k této události.  Hodnoty jsou uloženy v elementu xml ve formátu \<položky >\< název položky = "annotationName" type="System.String" > annotationValue\</bodu > \< /položky >.  Pokud nejsou zadány žádné poznámky, pak řetězec obsahuje \<položky / >. Velikost události trasování událostí pro Windows je omezena velikost vyrovnávací paměti ETW nebo maximální datová část pro událost trasování událostí pro Windows. Pokud velikost události překročila omezení trasování událostí pro Windows, pak tato událost je rozdělená do odstranit poznámky a nahraďte hodnoty anotace s \<položky >...  \< /položky >.|  
|ProfileName|xs:String|Název nebo sledování profil, který způsobil v tomto případě se vygenerované|  
|HostReference|xs:String|Webové hostované služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.  Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName' Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
