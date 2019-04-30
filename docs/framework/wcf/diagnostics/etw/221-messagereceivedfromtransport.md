---
title: 221 – MessageReceivedFromTransport
ms.date: 03/30/2017
ms.assetid: 4995f0d5-c182-4d97-981f-6951da6df1fb
ms.openlocfilehash: 98dbf2728242fa73b3e54b7cf32f9e227e5251b2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781716"
---
# <a name="221---messagereceivedfromtransport"></a>221 – MessageReceivedFromTransport
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|221|  
|klíčová slova|EndToEndMonitoring, řešení potíží s ServiceModel|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerován, když modelu služby obdrží zprávu od přenosu.  
  
## <a name="message"></a>Zpráva  
 Dispečer obdržel zprávu od přenosu. ID korelace == '%1'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|ID korelace|`xs:GUID`|Aktivita ID použít ke korelaci `MessageSentToTransport` událostí ze služby ani klienta k jeho odpovídajícím `MessageReceivedFromTransport` na druhém konci.|  
|HostReference|`xs:string`|Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby. Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName". Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".|  
|AppDomain|`xs:string`|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
