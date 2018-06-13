---
title: 223 - OperationFaulted
ms.date: 03/30/2017
ms.assetid: 2f7d89d7-3a6a-40fe-9610-5424eb6bbf61
ms.openlocfilehash: cf4a455d80a1a0ac09e99bad967c1feba3653842
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459415"
---
# <a name="223---operationfaulted"></a>223 - OperationFaulted
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|223|  
|Klíčová slova|EndToEndMonitoring, HealthMonitoring, řešení potíží s ServiceModel|  
|úroveň|Upozornění|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerované při výchozí Model služby `OperationInvoker` došlo k výjimce odvozování z `FaultException` při vyvolání příslušnou metodu.  
  
## <a name="message"></a>Zpráva  
 Metoda "%1" způsobila FaultException při vyvolané OperationInvoker. Doba trvání volání metoda byla ms '%2'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|MethodName|`xs:string`|CLR název metody, který byl vyvolán `OperationInvoker`.|  
|Doba trvání|`xs:long`|Čas v milisekundách, po které trvalo `OperationInvoker` k vyvolání metody.|  
|HostReference|`xs:string`|Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby. Formát je definovaný jako "virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName'. Příklad: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|Domény aplikace|`xs:string`|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
