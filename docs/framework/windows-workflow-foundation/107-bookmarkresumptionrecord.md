---
title: 107 – BookmarkResumptionRecord
ms.date: 03/30/2017
ms.assetid: aa2d37ed-2bfa-439b-89e8-a9354027f155
ms.openlocfilehash: 860ed7cc065a862d100b0a8c6a88458e61930b9b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052843"
---
# <a name="107----bookmarkresumptionrecord"></a>107 – BookmarkResumptionRecord
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|107|  
|klíčová slova|EndToEndMonitoring, řešení potíží, HealthMonitoring, WFTracking|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerován pomocí účastník sledování ETW při instance pracovního postupu vysílá BookmarkResumptionRecord.  
  
## <a name="message"></a>Zpráva  
 Záznam sledování = BookmarkResumptionRecord, ID instance = %1, číslo záznamu = %2, čas události = %3, název = %4, SubInstanceID = %5, hodnota vlastnosti OwnerActivityName = %6, OwnerActivityId = %7, OwnerActivityInstanceId = %8, OwnerActivityTypeName = %9, poznámky = % 10, název profilu = % 11  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|Id instance pracovního postupu|  
|Číslo záznamu|xs:long|Pořadové číslo emitovaný záznamu|  
|čas události|xs:dateTime|Čas ve standardu UTC, kdy události, protože ho|  
|Název|xs:string|Název záložky, který byl obnoven|  
|SubInstanceID|xs:GUID|Id rozsah záložky|  
|OwnerActivityName|xs:string|Název aktivity záložku|  
|OwnerActivityId|xs:string|Id aktivity záložku|  
|OwnerActivityInstanceId|xs:string|Id instance aktivity záložku|  
|OwnerActivityTypeName|xs:string|Typ aktivity záložku|  
|Poznámky|xs:string|Poznámky, které byly přidány k této události.  Hodnoty jsou uloženy v elementu xml ve formátu \<položky >\< název položky = "annotationName" type="System.String" > annotationValue\</položky > \< /položky >.  Pokud nejsou zadány žádné poznámky, pak řetězec obsahuje \<položky / >. Velikost události ETW je omezená velikost vyrovnávací paměti trasování událostí pro Windows nebo max datovou část události trasování událostí pro Windows. Pokud velikost události větší než omezení trasování událostí pro Windows, pak události je rozdělená do odstranit poznámky a nahraďte hodnoty anotace s \<položky >...  \< /položky >.|  
|ProfileName|xs:string|Název nebo sledování profil, který je v tomto případě probíhá emitovány|  
|HostReference|xs:string|Hostované webové služby Toto pole jednoznačně identifikuje v hierarchii webové služby.  Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName' Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
