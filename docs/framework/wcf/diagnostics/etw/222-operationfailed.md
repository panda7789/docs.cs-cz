---
title: 222 – OperationFailed
ms.date: 03/30/2017
ms.assetid: 6b530ded-8f20-4d78-8bfe-1875276df6ba
ms.openlocfilehash: c49aad0f93ce47b66306d75741267530dc6d3fe5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781638"
---
# <a name="222---operationfailed"></a>222 – OperationFailed
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|222|  
|klíčová slova|EndToEndMonitoring HealthMonitoring, řešení potíží s ServiceModel|  
|úroveň|Upozornění|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerován při výchozím modelu služby `OperationInvoker` došlo k výjimce při vyvolání jeho metody. Poznámka: Tento výjimky, které jsou odvozeny z `FaultException` způsobit, že tato událost nebude vygenerován.  
  
## <a name="message"></a>Zpráva  
 Metoda '%1' došlo k neošetřené výjimce při vyvolání třídou OperationInvoker. Délka volání metody byla ms '%2'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|Název metody|`xs:string`|Název CLR metody, která byla vyvolána pomocí `OperationInvoker`.|  
|Doba trvání|`xs:long`|Doba v milisekundách, jakou trvalo `OperationInvoker` k vyvolání metody.|  
|HostReference|`xs:string`|Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby. Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName". Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".|  
|AppDomain|`xs:string`|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
