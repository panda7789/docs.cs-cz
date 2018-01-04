---
title: 103 - ActivityStateRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57636a9a-561e-44aa-aef9-1f1894aaa6dd
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 62916de4d5077b8031ee353ca49a7d51a51ffd8d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="103---activitystaterecord"></a>103 - ActivityStateRecord
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|103|  
|Klíčová slova|EndToEndMonitoring, řešení potíží, HealthMonitoring, WFTracking|  
|úroveň|Informace o|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace nebo analytické|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerované účastníkem sledování, trasování událostí pro Windows, když aktivita v rámci instance pracovního postupu vysílá ActivityStateRecord  
  
## <a name="message"></a>Zpráva  
 TrackRecord = ActivityStateRecord, ID instance = %1, RecordNumber = %2, EventTime = %3, stav = %4, název = %5, ID = %6, ActivityInstanceId = %7, ActivityTypeName = %8, argumenty = %9, proměnné = % 10, poznámky = % 11, ProfileName = % 12  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|identifikátor instanceId|xs:GUID|Id instance pracovního postupu|  
|RecordNumber|xs:Long|Pořadové číslo emitovaného záznamu|  
|eventTime|xs|Čas v UTC při byl vygenerované události|  
|Stav|xs:String|Stav aktivity|  
|Název|xs:String|Zobrazovaný název aktivity, která vygenerované události|  
|ID aktivity|xs:String|Id aktivity aktivity generování.|  
|ActivityInstanceId|xs:String|Id instance aktivity aktivity generování.|  
|ActivityTypeName|xs:String|Název typu aktivity generování.|  
|Arguments|xs:String|Argumenty, které byly sledovány s touto událostí.  Hodnoty jsou uloženy v elementu xml ve formátu \<položky >\< název položky = "název argumentu argumentName" type="System.String" > argumentValue\</bodu > \< /položky >.  Pokud byly sledovány žádné argumenty. pak řetězec obsahuje \<položky / >. Velikost události trasování událostí pro Windows je omezena velikost vyrovnávací paměti ETW nebo maximální datová část pro událost trasování událostí pro Windows. Pokud velikost události překročila omezení trasování událostí pro Windows, pak tato událost je rozdělená do odstranit poznámky a nahraďte hodnoty anotace s \<položky >...  \< /položky >.  Následující typy jsou uloženy jako jejich hodnoty, jak ho vrátila ToString(); String,Char,BOOL,int,short,Long,uint,ushort,ulong,System.Single,float,Double,System.GUID,System.DateTimeOffset,System.DateTime.  Všechny ostatní typy jsou serializovanou pomocí System.Runtime.Serialization.NetDataContractSerializer.|  
|Proměnné|xs:String|Proměnné, které byly sledovány s touto událostí.  Hodnoty jsou uloženy v elementu xml ve formátu \<položky >\< název položky = "NázevProměnné" type="System.String" > variableValue\</bodu > \< /položky >.  Pokud byly sledovat žádné proměnné pak řetězec obsahuje \<položky / >. Velikost události trasování událostí pro Windows je omezena velikost vyrovnávací paměti ETW nebo maximální datová část pro událost trasování událostí pro Windows. Pokud velikost události překročila omezení trasování událostí pro Windows, pak tato událost je rozdělená do odstranit poznámky a nahrazení hodnoty proměnné s \<položky >...  \< /položky >.  Následující typy jsou uloženy jako jejich hodnoty, jak ho vrátila ToString(); String,Char,BOOL,int,short,Long,uint,ushort,ulong,System.Single,float,Double,System.GUID,System.DateTimeOffset,System.DateTime.  Všechny ostatní typy jsou serializovanou pomocí System.Runtime.Serialization.NetDataContractSerializer.|  
|Poznámky|xs:String|Poznámky, které byly přidány k této události.  Hodnoty jsou uloženy v elementu xml ve formátu \<položky >\< název položky = "annotationName" type="System.String" > annotationValue\</bodu > \< /položky >.  Pokud nejsou zadány žádné poznámky, pak řetězec obsahuje \<položky / >. Velikost události trasování událostí pro Windows je omezena velikost vyrovnávací paměti ETW nebo maximální datová část pro událost trasování událostí pro Windows. Pokud velikost události překročila omezení trasování událostí pro Windows, pak tato událost je rozdělená do odstranit poznámky a nahraďte hodnoty anotace s \<položky >...  \< /položky >.|  
|ProfileName|xs:String|Název nebo sledování profil, který způsobil v tomto případě se vygenerované|  
|HostReference|xs:String|Webové hostované služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.  Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName' Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
