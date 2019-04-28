---
title: 223 - OperationFaulted
ms.date: 03/30/2017
ms.assetid: 2f7d89d7-3a6a-40fe-9610-5424eb6bbf61
ms.openlocfilehash: cf4a455d80a1a0ac09e99bad967c1feba3653842
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61596529"
---
# <a name="223---operationfaulted"></a>223 - OperationFaulted
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|223|  
|klíčová slova|EndToEndMonitoring HealthMonitoring, řešení potíží s ServiceModel|  
|úroveň|Upozornění|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerován při výchozím modelu služby `OperationInvoker` došlo k výjimce odvozený od `FaultException` při vyvolání jeho metody.  
  
## <a name="message"></a>Zpráva  
 Metoda '%1' generovala výjimku FaultException při vyvolání třídou OperationInvoker. Délka volání metody byla ms '%2'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|methodName|`xs:string`|Název CLR metody, která byla vyvolána pomocí `OperationInvoker`.|  
|Doba trvání|`xs:long`|Doba v milisekundách, jakou trvalo `OperationInvoker` k vyvolání metody.|  
|HostReference|`xs:string`|Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby. Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName". Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".|  
|AppDomain|`xs:string`|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
