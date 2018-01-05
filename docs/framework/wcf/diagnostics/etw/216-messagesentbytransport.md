---
title: 216 - MessageSentByTransport
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 150c3167-4154-4225-8d94-57cc94341233
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ad2b32b8d1386f6cc0754070cba2b1a556219b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="216---messagesentbytransport"></a>216 - MessageSentByTransport
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|216|  
|Klíčová slova|Řešení potíží s ServiceModel|  
|úroveň|Informace o|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace nebo analytické|  
  
## <a name="description"></a>Popis  
 K této události dojde, když přenos protokolu TCP odešle zprávu. Všimněte si, že na úrovni přenosu může být více zpráv vyměňují mezi klienty a služby pro jednu operaci. Může to být způsobeno chování infrastruktury, je dobrým příkladem zabezpečení. Proto počet **MessageSentByTransport** události, které jsou vygenerované lišit v závislosti na vaší služby vazby a jeho konfigurace.  
  
## <a name="message"></a>Zpráva  
 Přenos neodeslal zprávu na '%1'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|DestinationAddress|`xs:string`|Adresa, který vám byl zaslán zprávu požadavku.|  
|HostReference|xs:String|Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby. Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}. Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.|  
|Domény aplikace|`xs:string`|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
