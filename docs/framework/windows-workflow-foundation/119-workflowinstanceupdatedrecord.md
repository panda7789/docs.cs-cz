---
title: 119 – WorkflowInstanceUpdatedRecord
ms.date: 03/30/2017
ms.assetid: 32485d0a-dcdb-45bc-b1e3-79fa9ad9439b
ms.openlocfilehash: 5bbda72208dd9cf38e7b8765d324129beaf3fa0c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924069"
---
# <a name="119---workflowinstanceupdatedrecord"></a>119 – WorkflowInstanceUpdatedRecord
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|119|  
|klíčová slova|HealthMonitoring WFTracking|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerován pomocí účastník sledování ETW po dokončení aktualizace instance pracovního postupu.  
  
## <a name="message"></a>Zpráva  
 Záznam sledování = WorkflowInstanceUpdatedRecord, ID instance = %1, číslo záznamu = %2, čas události = %3, ID definice aktivity = %4, stav = %5, původní Identita definice = %6, aktualizovaná Identita definice = %7, poznámky = %8, název profilu = %9  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|Id instance pracovního postupu|  
|Číslo záznamu|xs:long|Pořadové číslo emitovaný záznamu|  
|čas události|xs:dateTime|Čas ve standardu UTC, kdy události, protože ho|  
|ActivityDefinitionId|xs:string|Název kořenové aktivity v pracovním postupu|  
|Stav|xs:string|Aktuální stav pracovního postupu.|  
|OriginalDefinitionIdentity|xs:string|Původní id definice pracovního postupu|  
|UpdatedDefinitionIdentity|xs:string|Id definice aktualizovaný pracovní postup|  
|Poznámky|xs:string|Poznámky, které byly přidány k této události. Hodnoty jsou uloženy v elementu xml ve formátu \<položky >\< název položky = "annotationName" type="System.String" > annotationValue\</položky > \< /položky >. Pokud nejsou zadány žádné poznámky, pak řetězec obsahuje \<položky / >. Velikost události ETW je omezená velikost vyrovnávací paměti trasování událostí pro Windows nebo max datovou část události trasování událostí pro Windows. Pokud velikost události větší než omezení trasování událostí pro Windows, pak události je rozdělená do odstranit poznámky a nahraďte hodnoty anotace s \<položky >...  \< /položky >.|  
|ProfileName|xs:string|Název nebo sledování profil, který je v tomto případě probíhá emitovány|  
|WorkflowDefinitionIdentity|xs:string|Id definice pracovního postupu|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
