---
title: 117 – WorkflowInstanceTerminatedRecordWithId
ms.date: 03/30/2017
ms.assetid: e68539d0-5338-468a-9f75-7e5b09d39a3c
ms.openlocfilehash: d1d6930a08eeb513dbb017b6c9b409916e5b1a2c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009887"
---
# <a name="117---workflowinstanceterminatedrecordwithid"></a>117 – WorkflowInstanceTerminatedRecordWithId
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|117|  
|klíčová slova|HealthMonitoring WFTracking|  
|úroveň|Chyba|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerován pomocí účastník sledování ETW při instance pracovního postupu vysílá WorkflowInstanceTerminatedRecord.  
  
## <a name="message"></a>Zpráva  
 Záznam sledování = WorkflowInstanceTerminatedRecord, ID instance = %1, číslo záznamu = %2, čas události = %3, ID definice aktivity = %4, důvod = %5, poznámky = %6, název profilu = %7, identita definice pracovního postupu = %8  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|Id instance pracovního postupu|  
|Číslo záznamu|xs:long|Pořadové číslo emitovaný záznamu|  
|čas události|xs:dateTime|Čas ve standardu UTC, kdy události, protože ho|  
|ActivityDefinitionId|xs:string|Název kořenové aktivity v pracovním postupu|  
|Stav|xs:string|Aktuální stav pracovního postupu.|  
|Poznámky|xs:string|Poznámky, které byly přidány k této události. Hodnoty jsou uloženy v elementu xml ve formátu \<položky >\< název položky = "annotationName" type="System.String" > annotationValue\</položky > \< /položky >. Pokud nejsou zadány žádné poznámky, pak řetězec obsahuje \<položky / >. Velikost události ETW je omezená velikost vyrovnávací paměti trasování událostí pro Windows nebo max datovou část události trasování událostí pro Windows. Pokud velikost události větší než omezení trasování událostí pro Windows, pak události je rozdělená do odstranit poznámky a nahraďte hodnoty anotace s \<položky >...  \< /položky >.|  
|ProfileName|xs:string|Název nebo sledování profil, který je v tomto případě probíhá emitovány|  
|WorkflowDefinitionIdentity|xs:string|Id definice pracovního postupu|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
