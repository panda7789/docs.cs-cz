---
title: Skupiny partnerských uzlů
ms.date: 03/30/2017
ms.assetid: d93e312e-ac04-40f8-baea-5da1cacb546e
ms.openlocfilehash: afd9eae36f28c28b33b74c4456feb4ba8c91314d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="peer-meshes"></a>Skupiny partnerských uzlů
A *OK sítě* je pojmenovaná kolekce partnerské uzly, který dokáže komunikovat mezi sebou a které jsou určeny OK jedinečné ID (vzájemně propojena graf) Každý uzel je připojen k více dalších uzlů. V dobře propojené mřížku je mezi dvěma uzly, s relativně malý počet směrování mezi uzly ve nejvzdálenější okrajů oka, cestu a OK zůstanou připojené i v případě, že některé uzly nebo připojení vyřadit. Aktivní uzly v mřížce publikovaly své informace o koncový bod s odpovídajícím ID mřížky, aby ostatní partnerské uzly najít.  
  
## <a name="characteristics-of-a-mesh-created-using-peer-channel"></a>Vlastnosti vytvořený rovnocenného kanálu oka sítě  
  
#### <a name="uniquely-identified"></a>Jednoznačně identifikuje  
  
-   Jedinečné ID identifikuje každého OK. Název OK (nebo OK ID) je ve stejném formátu jako název hostitele systému DNS (Domain Name). Toto ID OK jako takový musí být jedinečný pro určený klientský aplikace v rámci oboru překladač používá. Běžný název, například "MyFamilysPeers" nebo "KevinsPokerTable", může snadno dojít ke konfliktu s další uživatelská jména a může vracet neúmyslným sdílené informace koncového bodu, což může způsobit problémy ochrany osobních údajů nebo zvýšení latence připojení. Jedním ze způsobů, abyste se těmto problémům může být k přidání jedinečné ID jako operátory Přezdívka pro síť (například "KevinsPokerTable90210").  
  
#### <a name="message-flooding"></a>Zpráva zahlcení  
  
-   OK umožňuje zprávy, které mají být předány z jednoho nebo více odesílatelů všechny ostatní partnerské uzly stejné v mřížce. Zprávy zaplněn partnerské uzly použít záhlaví zadaná v oboru názvů v `http://schemas.microsoft.com/net/2006/05/peer`.  
  
#### <a name="optimized-connections"></a>Optimalizované připojení  
  
-   Pokud uzly připojení nebo odpojení, zajistíte, že všechny uzly mají dobré připojení s menší riziko vytváření oddílů (skupiny uzly navzájem izolované) automaticky upraví rovnocenného kanálu oka. Připojení v mřížce jsou také dynamicky optimalizované podle aktuální vzory přenosů dat tak, aby latence zprávu od odesílatele k příjemce je co nejmenší.  
  
#### <a name="popular-network-features-that-peer-channel-does-not-provide"></a>Oblíbené síťové funkce, které neposkytuje rovnocenného kanálu  
 Je důležité si uvědomit oblíbených síťové funkce, které neposkytuje rovnocenného kanálu. Tyto funkce, které může všechny být postavená na rovnocenného kanálu, patří:  
  
-   **Řazení zpráv:** zprávy pocházející z jednoho zdroje nemusí dorazí na všech jiných stran ve stejném pořadí, nebo v pořadí, odeslaný zdroji. Aplikace, které vyžadují zprávy být dodávány v určitém pořadí musí vytvořit ji do svých aplikací (například zahrnutím monotónně se zvyšující ID s všechny zprávy).  
  
-   **Spolehlivé zasílání zpráv:** rovnocenného kanálu nezahrnuje mechanismus zajistit příjem zpráv ve všech partnerských uzlů. Pokud chcete zajistit doručení zpráv, musíte napsat spolehlivost vrstvu nad rovnocenného kanálu.
