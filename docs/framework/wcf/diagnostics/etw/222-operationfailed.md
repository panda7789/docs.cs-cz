---
title: 222 – OperationFailed
ms.date: 03/30/2017
ms.assetid: 6b530ded-8f20-4d78-8bfe-1875276df6ba
ms.openlocfilehash: c49aad0f93ce47b66306d75741267530dc6d3fe5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460732"
---
# <a name="222---operationfailed"></a>222 – OperationFailed
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|222|  
|Klíčová slova|EndToEndMonitoring, HealthMonitoring, řešení potíží s ServiceModel|  
|úroveň|Upozornění|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerované při výchozí Model služby `OperationInvoker` došlo k výjimce při volání její metody. Poznámka: Tento výjimky, které jsou odvozeny od `FaultException` způsobit tuto událost, chcete-li nebyla vygenerované.  
  
## <a name="message"></a>Zpráva  
 Metoda "%1, došlo k neošetřené výjimce při vyvolané OperationInvoker. Doba trvání volání metoda byla ms '%2'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Název metody|`xs:string`|CLR název metody, který byl vyvolán `OperationInvoker`.|  
|Doba trvání|`xs:long`|Čas v milisekundách, po které trvalo `OperationInvoker` k vyvolání metody.|  
|HostReference|`xs:string`|Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby. Formát je definovaný jako "virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName'. Příklad: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|Domény aplikace|`xs:string`|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
