---
title: 105 – FaultPropagationRecord
ms.date: 03/30/2017
ms.assetid: 168473b1-b1e5-4e9f-8a2a-35bbdb2ef531
ms.openlocfilehash: c48f42a91ad9a15b49aad8c1ab684f2348954174
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924199"
---
# <a name="105---faultpropagationrecord"></a>105 – FaultPropagationRecord
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|105|  
|klíčová slova|EndToEndMonitoring, řešení potíží, HealthMonitoring, WFTracking|  
|úroveň|Upozornění|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vyzařovaného účastník sledování ETW, když vysílá FaultPropagationRecord aktivitu s instancí pracovního postupu.  
  
## <a name="message"></a>Zpráva  
 Záznam sledování = FaultPropagationRecord, ID instance = %1, číslo záznamu = %2, čas události = %3, FaultSourceActivityName = %4, FaultSourceActivityId = %5, FaultSourceActivityInstanceId = %6, FaultSourceActivityTypeName = %7, FaultHandlerActivityName = %8,  FaultHandlerActivityId = %9, FaultHandlerActivityInstanceId = % 10, FaultHandlerActivityTypeName = % 11, chyby = % 12, IsFaultSource = % 13, poznámky = % 14, název profilu = % 15  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|Id instance pracovního postupu|  
|Číslo záznamu|xs:long|Pořadové číslo emitovaný záznamu|  
|čas události|xs:dateTime|Čas ve standardu UTC, kdy události, protože ho|  
|FaultSourceActivityName|xs:string|Název aktivity, která v době, protože ho|  
|FaultSourceActivityId|xs:string|Id aktivity, která v době, protože ho|  
|FaultSourceActivityInstanceId|xs:string|Id instance aktivity, která v době, protože ho|  
|FaultSourceActivityTypeName|xs:string|Typ aktivity, která v době, protože ho|  
|faultHandlerActivityName|xs:string|Zobrazovaný název aktivity obslužná rutina chyb|  
|FaultHandlerActivityId|xs:string|Id aktivity obslužná rutina chyb|  
|FaultHandlerActivityInstanceId|xs:string|Id instance aktivity obslužná rutina chyb|  
|FaultHandlerActivityTypeName|xs:string|Typ aktivity obslužná rutina chyb|  
|Selhání|xs:string|V podrobnostech o chybě|  
|IsFaultSource|xs:unsignedByte|Označuje, pokud událost, protože ho ze zdroje chyby|  
|Poznámky|xs:string|Poznámky, které byly přidány k této události.  Hodnoty jsou uloženy v elementu xml ve formátu \<položky >\< název položky = "annotationName" type="System.String" > annotationValue\</položky > \< /položky >.  Pokud nejsou zadány žádné poznámky, pak řetězec obsahuje \<položky / >. Velikost události ETW je omezená velikost vyrovnávací paměti trasování událostí pro Windows nebo max datovou část události trasování událostí pro Windows. Pokud velikost události větší než omezení trasování událostí pro Windows, pak události je rozdělená do odstranit poznámky a nahraďte hodnoty anotace s \<položky >...  \< /položky >.|  
|ProfileName|xs:string|Název nebo sledování profil, který je v tomto případě probíhá emitovány|  
|HostReference|xs:string|Hostované webové služby Toto pole jednoznačně identifikuje v hierarchii webové služby.  Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName' Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
