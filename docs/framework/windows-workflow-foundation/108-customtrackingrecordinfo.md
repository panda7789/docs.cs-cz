---
title: 108 - CustomTrackingRecordInfo
ms.date: 03/30/2017
ms.assetid: 5bee501e-4e00-42cd-b949-e88009c3d4e8
ms.openlocfilehash: 7398693208ca09aa1f9f56ef5354b86bb67f26a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515353"
---
# <a name="108---customtrackingrecordinfo"></a>108 - CustomTrackingRecordInfo
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|108|  
|Klíčová slova|UserEvents, EndToEndMonitoring, řešení potíží, HealthMonitoring, WFTracking|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerované účastníkem sledování, trasování událostí pro Windows, když aktivita v rámci instance pracovního postupu vysílá CustomTrackingRecord s úrovni informacemi.  
  
## <a name="message"></a>Zpráva  
 TrackRecord = CustomTrackingRecord, ID instance = %1, RecordNumber = %2, EventTime = %3, název = %4, název aktivity ActivityName = %5, ID = %6, ActivityInstanceId = %7, ActivityTypeName = %8, Data = %9, poznámky = % 10, ProfileName = % 11  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|identifikátor instanceId|xs:GUID|Id instance pracovního postupu|  
|RecordNumber|xs:Long|Pořadové číslo emitovaného záznamu|  
|eventTime|xs|Čas v UTC při byl vygenerované události|  
|Název|xs:String|Název CustomTrackingRecord|  
|Název aktivity activityName|xs:String|Název aktivity, která vygenerované CustomTrackingRecord|  
|ID aktivity|xs:String|Id aktivity, která vygenerované CustomTrackingRecord|  
|ActivityInstanceId|xs:String|Id instance aktivity, která vygenerované CustomTrackingRecord|  
|ActivityTypeName|xs:String|Název aktivity, která vygenerované CustomTrackingRecord|  
|Data|xs:String|Data, která byla sledovat pomocí této události.  Hodnoty jsou uloženy v elementu xml ve formátu \<položky >\< název položky = "dataName" type="System.String" > dataValue\</bodu > \< /položky >.  Pokud byl sledován žádná data pak řetězec obsahuje \<položky / >. Velikost události trasování událostí pro Windows je omezena velikost vyrovnávací paměti ETW nebo maximální datová část pro událost trasování událostí pro Windows. Pokud velikost události překročila omezení trasování událostí pro Windows, pak tato událost je rozdělená do odstranit poznámky a nahraďte hodnotu dat s \<položky >...  \< /položky >.  Následující typy jsou uloženy jako jejich hodnoty, jak ho vrátila ToString(); String,Char,BOOL,int,short,Long,uint,ushort,ulong,System.Single,float,Double,System.GUID,System.DateTimeOffset,System.DateTime.  Všechny ostatní typy jsou serializovanou pomocí System.Runtime.Serialization.NetDataContractSerializer.|  
|Poznámky|xs:String|Poznámky, které byly přidány k této události.  Hodnoty jsou uloženy v elementu xml ve formátu \<položky >\< název položky = "annotationName" type="System.String" > annotationValue\</bodu > \< /položky >.  Pokud nejsou zadány žádné poznámky, pak řetězec obsahuje \<položky / >. Velikost události trasování událostí pro Windows je omezena velikost vyrovnávací paměti ETW nebo maximální datová část pro událost trasování událostí pro Windows. Pokud velikost události překročila omezení trasování událostí pro Windows, pak tato událost je rozdělená do odstranit poznámky a nahraďte hodnoty anotace s \<položky >...  \< /položky >.|  
|ProfileName|xs:String|Název nebo sledování profil, který způsobil v tomto případě se vygenerované|  
|HostReference|xs:String|Webové hostované služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.  Formát je definován jako ' virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName' Příklad: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
