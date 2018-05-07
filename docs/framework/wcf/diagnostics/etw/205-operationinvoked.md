---
title: 205 – OperationInvoked
ms.date: 03/30/2017
ms.assetid: 9c8d6c90-dfa5-4ae0-a589-96679a8fb3ba
ms.openlocfilehash: e95b6923d21307b2ef68d4a5369b3cee86540239
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="205---operationinvoked"></a>205 – OperationInvoked
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|205|  
|Klíčová slova|Řešení potíží s ServiceModel|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerované těsně před výchozí Model služby `OperationInvoker` zahájí volání metody.  
  
## <a name="message"></a>Zpráva  
 OperationInvoker volá metodu '%1'. Informace o subjektu volajícím: '%2'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Název metody|`xs:string`|CLR název metody, který byl vyvolán `OperationInvoker`.|  
|Informace o volajícím|`xs:string`|IP adresa a port číslo klienta ve formátu 'IPAddress:PortNumber'. Tyto dvě hodnoty se načítají z vlastnosti 'System.ServiceModel.Channels.RemoteEndpointMessageProperty' zprávy v rámci operace. Všimněte si, že se u vazeb mimo TCP tuto hodnotu `null`.|  
|HostReference|`xs:string`|Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby. Formát je definovaný jako "virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName'. Příklad: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|Domény aplikace|`xs:string`|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
