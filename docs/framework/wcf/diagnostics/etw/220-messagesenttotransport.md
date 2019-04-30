---
title: 220 – MessageSentToTransport
ms.date: 03/30/2017
ms.assetid: aef4e781-240b-45bc-bff8-400053037e71
ms.openlocfilehash: 92ec664aead15470fbed576bf157d64d984ddebf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781742"
---
# <a name="220---messagesenttotransport"></a>220 – MessageSentToTransport
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|220|  
|klíčová slova|EndToEndMonitoring, řešení potíží s ServiceModel|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Tato událost je vygenerován Model služby odešle zprávu přenosu.  
  
> [!NOTE]
>  Tato událost nebude se emitovat pro jednosměrnou přenosy.  
  
## <a name="message"></a>Zpráva  
 Dispečer odeslal zprávu přenosu. ID korelace == '%1'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|ID korelace|`xs:GUID`|Aktivita ID použít ke korelaci `MessageSentToTransport` událostí ze služby ani klienta k jeho odpovídajícím `MessageReceivedFromTransport` na druhém konci.|  
|HostReference|`xs:string`|Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby. Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName". Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".|  
|AppDomain|`xs:string`|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
