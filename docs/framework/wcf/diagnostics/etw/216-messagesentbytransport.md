---
title: 216 - MessageSentByTransport
ms.date: 03/30/2017
ms.assetid: 150c3167-4154-4225-8d94-57cc94341233
ms.openlocfilehash: fa21568e4c8c38eefe359c417d47ec0a9d30a7c4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="216---messagesentbytransport"></a>216 - MessageSentByTransport
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|216|  
|Klíčová slova|Řešení potíží s ServiceModel|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 K této události dojde, když přenos protokolu TCP odešle zprávu. Všimněte si, že na úrovni přenosu může být více zpráv vyměňují mezi klienty a služby pro jednu operaci. Může to být způsobeno chování infrastruktury, je dobrým příkladem zabezpečení. Proto počet **MessageSentByTransport** události, které jsou vygenerované lišit v závislosti na vaší služby vazby a jeho konfigurace.  
  
## <a name="message"></a>Zpráva  
 Přenos neodeslal zprávu na '%1'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|DestinationAddress|`xs:string`|Adresa, který vám byl zaslán zprávu požadavku.|  
|HostReference|xs:String|Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby. Formát je definovaný jako "virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName'. Příklad: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|Domény aplikace|`xs:string`|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
