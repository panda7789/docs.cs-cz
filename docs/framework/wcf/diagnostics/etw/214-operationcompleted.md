---
title: 214 – OperationCompleted
ms.date: 03/30/2017
ms.assetid: a6287eef-023f-4816-813c-1802c82366df
ms.openlocfilehash: da1021b674b555b683f8f745f5a2a0073c9567e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967996"
---
# <a name="214---operationcompleted"></a>214 – OperationCompleted
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|214|  
|klíčová slova|HealthMonitoring EndToEndMonitoring, řešení potíží s ServiceModel|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerován při výchozím modelu služby `OperationInvoker` volání metody byla dokončena bez metody došlo k výjimce.  
  
## <a name="message"></a>Zpráva  
 Třída OperationInvoker dokončila volání metody '%1'. Délka volání metody byla ms '%2'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|Název metody|`xs:string`|Název CLR metody, která byla vyvolána pomocí `OperationInvoker`.|  
|Doba trvání|`xs:long`|Doba v milisekundách, jakou trvalo `OperationInvoker` k vyvolání metody.|  
|HostReference|`xs:string`|Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby. Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName". Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".|  
|AppDomain|`xs:string`|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
