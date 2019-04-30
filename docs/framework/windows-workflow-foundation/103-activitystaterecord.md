---
title: 103 – ActivityStateRecord
ms.date: 03/30/2017
ms.assetid: 57636a9a-561e-44aa-aef9-1f1894aaa6dd
ms.openlocfilehash: 38cec570cffebf6af6d35df481cbec8c7dca8cd1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924381"
---
# <a name="103---activitystaterecord"></a>103 – ActivityStateRecord
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|103|  
|klíčová slova|EndToEndMonitoring, řešení potíží, HealthMonitoring, WFTracking|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vyzařovaného účastník sledování ETW, když vysílá ActivityStateRecord aktivitu v rámci instance pracovního postupu  
  
## <a name="message"></a>Zpráva  
 Záznam sledování = ActivityStateRecord, ID instance = %1, číslo záznamu = %2, čas události = %3, stav = %4, název = %5, ID aktivity = %6, ActivityInstanceId = %7, ActivityTypeName = %8, argumenty = %9, proměnných = % 10, poznámky = % 11, název profilu = % 12  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|Id instance pracovního postupu|  
|Číslo záznamu|xs:long|Pořadové číslo emitovaný záznamu|  
|čas události|xs:dateTime|Čas ve standardu UTC, kdy události, protože ho|  
|Stav|xs:string|Stav aktivity|  
|Název|xs:string|Zobrazovaný název aktivity, která událost, protože ho|  
|ID aktivity|xs:string|Id aktivity generování aktivity|  
|ActivityInstanceId|xs:string|Id instance aktivity generování aktivity|  
|ActivityTypeName|xs:string|Název typu generování aktivity|  
|Arguments|xs:string|Argumenty, které byly sledovány s touto událostí.  Hodnoty jsou uloženy v elementu xml ve formátu \<položky >\< název položky = "název argumentu argumentName" type="System.String" > argumentValue\</položky > \< /položky >.  Pokud byly sledovány žádné argumenty, řetězec obsahuje \<položky / >. Velikost události ETW je omezená velikost vyrovnávací paměti trasování událostí pro Windows nebo max datovou část události trasování událostí pro Windows. Pokud velikost události větší než omezení trasování událostí pro Windows, pak události je rozdělená do odstranit poznámky a nahraďte hodnoty anotace s \<položky >...  \< /položky >.  Tyto typy jsou uloženy jako jejich hodnoty vrácené ToString(); String,Char,BOOL,int,short,Long,uint,ushort,ulong,System.Single,float,Double,System.GUID,System.DateTimeOffset,System.DateTime.  Všechny ostatní typy se serializují pomocí System.Runtime.Serialization.NetDataContractSerializer.|  
|Proměnné|xs:string|Proměnné, které byly sledovány s touto událostí.  Hodnoty jsou uloženy v elementu xml ve formátu \<položky >\< název položky = "NázevProměnné" type="System.String" > variableValue\</položky > \< /položky >.  Pokud byly sledovány žádné proměnné, řetězec obsahuje \<položky / >. Velikost události ETW je omezená velikost vyrovnávací paměti trasování událostí pro Windows nebo max datovou část události trasování událostí pro Windows. Pokud velikost události větší než omezení trasování událostí pro Windows, pak události je rozdělená do odstranit poznámky a že nahradíte hodnotu proměnné s \<položky >...  \< /položky >.  Tyto typy jsou uloženy jako jejich hodnoty vrácené ToString(); String,Char,BOOL,int,short,Long,uint,ushort,ulong,System.Single,float,Double,System.GUID,System.DateTimeOffset,System.DateTime.  Všechny ostatní typy se serializují pomocí System.Runtime.Serialization.NetDataContractSerializer.|  
|Poznámky|xs:string|Poznámky, které byly přidány k této události.  Hodnoty jsou uloženy v elementu xml ve formátu \<položky >\< název položky = "annotationName" type="System.String" > annotationValue\</položky > \< /položky >.  Pokud nejsou zadány žádné poznámky, pak řetězec obsahuje \<položky / >. Velikost události ETW je omezená velikost vyrovnávací paměti trasování událostí pro Windows nebo max datovou část události trasování událostí pro Windows. Pokud velikost události větší než omezení trasování událostí pro Windows, pak události je rozdělená do odstranit poznámky a nahraďte hodnoty anotace s \<položky >...  \< /položky >.|  
|ProfileName|xs:string|Název nebo sledování profil, který je v tomto případě probíhá emitovány|  
|HostReference|xs:string|Hostované webové služby Toto pole jednoznačně identifikuje v hierarchii webové služby.  Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName' Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
