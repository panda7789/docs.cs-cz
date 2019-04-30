---
title: 205 – OperationInvoked
ms.date: 03/30/2017
ms.assetid: 9c8d6c90-dfa5-4ae0-a589-96679a8fb3ba
ms.openlocfilehash: e95b6923d21307b2ef68d4a5369b3cee86540239
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781976"
---
# <a name="205---operationinvoked"></a>205 – OperationInvoked
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|205|  
|klíčová slova|Řešení potíží s ServiceModel|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerován těsně před výchozím modelu služby `OperationInvoker` zahájí volání metody.  
  
## <a name="message"></a>Zpráva  
 Třída OperationInvoker vyvolala metodu '%1'. Informace o volajícím: '%2'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|Název metody|`xs:string`|Název CLR metody, která byla vyvolána pomocí `OperationInvoker`.|  
|Informace o volajícím|`xs:string`|IP adresu a číslo portu klienta ve formátu "IPAddress:PortNumber". Tyto dvě hodnoty jsou načten z vlastnosti zprávy "System.ServiceModel.Channels.RemoteEndpointMessageProperty" v rámci operace. Všimněte si, že u vazeb mimo TCP tuto hodnotu `null`.|  
|HostReference|`xs:string`|Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby. Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName". Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".|  
|AppDomain|`xs:string`|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
