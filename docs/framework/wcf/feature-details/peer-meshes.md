---
title: Skupiny partnerských uzlů
ms.date: 03/30/2017
ms.assetid: d93e312e-ac04-40f8-baea-5da1cacb546e
ms.openlocfilehash: 9113fab13da8503e6ce0335e5bb19a2634973dad
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64654503"
---
# <a name="peer-meshes"></a>Skupiny partnerských uzlů
A *mřížky* je pojmenované kolekci (propojených graf) partnerské uzly, který dokáže komunikovat mezi sebou a které jsou označeny identifikátorem sítě jedinečné ID. Každý uzel je připojen k více uzlech. V dobře propojené sítě cesty mezi dvěma uzly, s relativně malý počet segmentů směrování mezi uzly v nejvzdálenější okraji sítě, a síť zůstanou připojené i v případě, že některé uzly nebo připojení vyřadit navýšení kapacity. Aktivní uzlům v síti publikovaly své informace koncový bod s odpovídajícím ID sítě, takže je můžete najít další partnerské uzly.  
  
## <a name="characteristics-of-a-mesh-created-using-peer-channel"></a>Charakteristiky sítě vytvořené pomocí protokolu Peer Channel  
  
#### <a name="uniquely-identified"></a>Jednoznačně identifikují  
  
- Jedinečné ID identifikuje každou síť. Název sítě (nebo ID sítě) je ve stejném formátu jako název hostitele systému DNS (Domain Name). Toto ID sítě v důsledku toho musí být jedinečný pro určený klientský aplikace v rámci oboru překladač používá. Běžný název jako "MyFamilysPeers" nebo "KevinsPokerTable," může snadno kolidují s názvy jiných uživatelů a může vrátit neúmyslnému sdílené informace o koncovém bodu, což může způsobit problémy ochrany osobních údajů nebo zvýšit latenci připojení. Jedním ze způsobů, abyste se těmto problémům může být přidat jedinečné ID příponový pojmenování pro sítě (například "KevinsPokerTable90210").  
  
#### <a name="message-flooding"></a>Zahlcení zprávy  
  
- Síť umožňuje zprávy rozšířit z jednoho nebo více uživatelů pro všechny další partnerské uzly ve stejné síti. Zprávy budete zaplaveni podle partnerské uzly používají hlavičky zadané v oboru názvů na `http://schemas.microsoft.com/net/2006/05/peer`.  
  
#### <a name="optimized-connections"></a>Optimalizované připojení  
  
- Sítě protokolu Peer Channel automaticky přizpůsobí při uzly Zúčastněte se dvoudenního a, ověříte, že všechny uzly máte dobré připojení s malou riziko vytváření oddílů (skupiny uzlů navzájem izolované). Připojení v síť se také dynamicky optimalizují podle aktuální vzory provozu tak, aby byla co nejmenší latenci zprávu od odesílatele příjemci.  
  
#### <a name="popular-network-features-that-peer-channel-does-not-provide"></a>Oblíbené síťové funkce, které neposkytuje protokolu Peer Channel  
 Je důležité znát oblíbených síťové funkce, které neposkytuje rovnocenného kanálu. Tyto funkce, které mohou všechny být postavená na protokolu Peer Channel, patří:  
  
- **Pořadí zpráv:** Zprávy pocházející z jednoho zdroje nemusí přijetí u všech ostatních strany ve stejném pořadí, nebo v pořadí, ve kterém odeslané zdroji. Aplikace, které vyžadují zprávy doručit v určitém pořadí musíte ho integrovat do svých aplikací (třeba podle monotónně se zvyšující ID se všechny zprávy včetně).  
  
- **Spolehlivé zasílání zpráv:** Rovnocenný kanál neobsahuje mechanismus pro zajištění příjem zpráv pomocí všechny partnerské uzly. Zaručit doručování zpráv, musíte napsat spolehlivost vrstvu nad rovnocenného kanálu.
