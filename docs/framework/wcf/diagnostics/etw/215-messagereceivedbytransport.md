---
title: 215 – MessageReceivedByTransport
ms.date: 03/30/2017
ms.assetid: bb32aa60-5207-4711-9f08-110e8ac327e5
ms.openlocfilehash: a8ba90b88ef8dbe3c8651bc565da61aae16a0a4a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781833"
---
# <a name="215---messagereceivedbytransport"></a>215 – MessageReceivedByTransport
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|215|  
|klíčová slova|Řešení potíží s ServiceModel|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Při přenosu protokolu TCP přijme zprávu dojde k této události. Všimněte si, že na úrovni přenosu, více zpráv nelze vyměňovat mezi klienty a služby pro jednu operaci. To může být způsobeno chování infrastrukturu, zabezpečení je dobrým příkladem. Proto, počet `MessageReceivedByTransport` události, které jsou emitovány lišit v závislosti na vaší služby vazby a jeho konfigurace.  
  
> [!NOTE]
>  Tato událost není aktivováno pro jednosměrnou přenosy.  
  
## <a name="message"></a>Zpráva  
 Přenos obdržel zprávu od '%1'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|Adresa naslouchání|`xs:string`|Adresa, která se zobrazila zpráva.|  
|HostReference|`xs:string`|Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby. Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName". Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".|  
|AppDomain|`xs:string`|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
