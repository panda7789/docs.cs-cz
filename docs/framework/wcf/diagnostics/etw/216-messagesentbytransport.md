---
title: 216 - MessageSentByTransport
ms.date: 03/30/2017
ms.assetid: 150c3167-4154-4225-8d94-57cc94341233
ms.openlocfilehash: fa21568e4c8c38eefe359c417d47ec0a9d30a7c4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781807"
---
# <a name="216---messagesentbytransport"></a>216 - MessageSentByTransport
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|216|  
|klíčová slova|Řešení potíží s ServiceModel|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Při přenosu protokolu TCP odešle zprávu dojde k této události. Všimněte si, že na úrovni přenosu více zpráv nelze vyměňovat mezi klienty a služby pro jednu operaci. To může být způsobeno chování infrastrukturu, zabezpečení je dobrým příkladem. Proto, počet **MessageSentByTransport** události, které jsou emitovány lišit v závislosti na vaší služby vazby a jeho konfigurace.  
  
## <a name="message"></a>Zpráva  
 Přenos odeslal zprávu na '%1'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|DestinationAddress|`xs:string`|Adresa, která byla zaslána zpráva požadavku.|  
|HostReference|xs:string|Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby. Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName". Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".|  
|AppDomain|`xs:string`|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
