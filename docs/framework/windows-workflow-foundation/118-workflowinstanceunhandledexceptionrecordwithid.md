---
title: 118 - WorkflowInstanceUnhandledExceptionRecordWithId
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ce4b193-e141-4cc4-86a3-2e8c984c110d
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a1c20182b5f53a188e95a31124e30f04418eb909
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="118---workflowinstanceunhandledexceptionrecordwithid"></a>118 - WorkflowInstanceUnhandledExceptionRecordWithId
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|118|  
|Klíčová slova|HealthMonitoring WFTracking|  
|úroveň|Chyba|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace nebo analytické|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerované účastníkem sledování, trasování událostí pro Windows, když WorkflowInstanceUnhandledExceptionRecord vysílá instanci pracovního postupu.  
  
## <a name="message"></a>Zpráva  
 TrackRecord = WorkflowInstanceUnhandledExceptionRecord, ID instance = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, název = %5, SourceId = %6, SourceInstanceId = %7, SourceTypeName = %8, výjimka = %9, poznámky = % 10, ProfileName = % 11, WorkflowDefinitionIdentity = % 12  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|identifikátor instanceId|xs:GUID|Id instance pracovního postupu|  
|RecordNumber|xs:Long|Pořadové číslo emitovaného záznamu|  
|eventTime|xs|Čas v UTC při byl vygenerované události|  
|ActivityDefinitionId|xs:String|Název kořenové aktivity v pracovním postupu|  
|SourceName|xs:String|Název zdrojového aktivity, který s chybou, výsledkem unhandledException|  
|ID zdroje|xs:String|Id aktivity aktivity zdroje chyby|  
|SourceInstanceId|xs:String|Id instance aktivity selhání zdrojové aktivity|  
|SourceTypeName|xs:String|Název typu aktivity zdroj, který s chybou, výsledkem unhandledException|  
|Výjimka|xs:String|Podrobnosti výjimky neošetřené výjimky|  
|Stav|xs:String|Aktuální stav pracovního postupu.|  
|Poznámky|xs:String|Poznámky, které byly přidány k této události. Hodnoty jsou uloženy v elementu xml ve formátu \<položky >\< název položky = "annotationName" type="System.String" > annotationValue\</bodu > \< /položky >. Pokud nejsou zadány žádné poznámky, pak řetězec obsahuje \<položky / >. Velikost události trasování událostí pro Windows je omezena velikost vyrovnávací paměti ETW nebo maximální datová část pro událost trasování událostí pro Windows. Pokud velikost události překročila omezení trasování událostí pro Windows, pak tato událost je rozdělená do odstranit poznámky a nahraďte hodnoty anotace s \<položky >...  \< /položky >.|  
|ProfileName|xs:String|Název nebo sledování profil, který způsobil v tomto případě se vygenerované|  
|WorkflowDefinitionIdentity|xs:String|Id definice pracovního postupu|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
