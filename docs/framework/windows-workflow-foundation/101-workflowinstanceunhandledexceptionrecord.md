---
title: 101 – WorkflowInstanceUnhandledExceptionRecord
ms.date: 03/30/2017
ms.assetid: ab7d50a0-5347-4390-8445-1def4dfdff6a
ms.openlocfilehash: af7f471e135ed7ec782f7d9a5c7cee3de09e7187
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924602"
---
# <a name="101---workflowinstanceunhandledexceptionrecord"></a>101 – WorkflowInstanceUnhandledExceptionRecord
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|101|  
|klíčová slova|EndToEndMonitoring, řešení potíží, HealthMonitoring, WFTracking|  
|úroveň|Chyba|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerován pomocí účastník sledování ETW při instance pracovního postupu vysílá WorkflowInstanceUnhandledExceptionRecord.  
  
## <a name="message"></a>Zpráva  
 Záznam sledování = WorkflowInstanceUnhandledExceptionRecord, ID instance = %1, číslo záznamu = %2, čas události = %3, ID definice aktivity = %4, název zdroje = %5, ID zdroje = %6, ID instance zdroje = %7, název typu zdroje = %8, výjimka = %9, poznámky = % 10, název profilu = % 11  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|Id instance pracovního postupu|  
|Číslo záznamu|xs:long|Pořadové číslo emitovaný záznamu|  
|čas události|xs:dateTime|Čas ve standardu UTC, kdy události, protože ho|  
|ActivityDefinitionId|xs:string|Název kořenové aktivity v pracovním postupu|  
|Název zdroje|xs:string|Název zdrojové aktivity, které k chybě, což vede unhandledException|  
|SourceId|xs:string|Id aktivity zdrojová aktivita selhání|  
|SourceInstanceId|xs:string|Id instance aktivity zdrojová aktivita selhání|  
|SourceTypeName|xs:string|Název typu zdroje aktivity došlo k chybě, což vede unhandledException|  
|Výjimka|xs:string|Podrobnosti o výjimce pro neošetřené výjimky|  
|Poznámky|xs:string|Poznámky, které byly přidány k této události.  Hodnoty jsou uloženy v elementu xml ve formátu \<položky >\< název položky = "annotationName" type="System.String" > annotationValue\</položky > \< /položky >.  Pokud nejsou zadány žádné poznámky, pak řetězec obsahuje \<položky / >. Velikost události ETW je omezená velikost vyrovnávací paměti trasování událostí pro Windows nebo max datovou část události trasování událostí pro Windows. Pokud velikost události větší než omezení trasování událostí pro Windows, pak události je rozdělená do odstranit poznámky a nahraďte hodnoty anotace s \<položky >...  \< /položky >.|  
|ProfileName|xs:string|Název nebo sledování profil, který je v tomto případě probíhá emitovány|  
|HostReference|xs:string|Hostované webové služby Toto pole jednoznačně identifikuje v hierarchii webové služby.  Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName' Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
