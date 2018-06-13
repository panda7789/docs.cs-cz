---
title: Scénáře rovnocenných kanálů
ms.date: 03/30/2017
ms.assetid: dae6e0f7-900c-45ee-8be9-3647698382fb
ms.openlocfilehash: 42b16ea394b9375be14aed4b2792d306fcb62f2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492981"
---
# <a name="peer-channel-scenarios"></a>Scénáře rovnocenných kanálů
Rozhraní API kanálu Peer podporují následující scénáře vývoj.  
  
## <a name="publicationsubscription-messaging"></a>Publikování/odběr pro zasílání zpráv  
 Společností, které vytvářet aplikace, publikování/odběr (pro příklad, kurzů akcií a vydavatele titulky zpráv sportovní skóre a hlásí počasí) slouží k serveru bez aplikace rovnocenného kanálu. Například uživatelé získat nejnovější skóre sportu díky připojení ke službě běžné OK (nebo skupiny klientů) a přenos velké množství aktuální herní dat i bez zvýšení zatížení serveru. To pomáhá zprostředkovatele dat umožňuje vyšší kvality služby bez podstatně zvýšení investice do technologie založené na serveru.  
  
## <a name="collaboration"></a>Spolupráce  
 Nezávislí dodavatelé softwaru (ISV) můžete vytvořit aplikace, které uživatelé mohou vytvořit úzkou skupiny pro účast v aktivitách peer-to-peer. Například to může zahrnovat týmy práci na projektech obrázek sdílení mezi přátel, strany plánování aktivit a další. Obvyklým tyto aktivity vždy zahrnovat servery; Rovnocenného kanálu však poskytuje způsob, jakým způsobem cenově výhodnější způsobem povolením offline přístup scénáře, které nejsou implementované jako snadno v rámci modelu tradiční klient server.  
  
## <a name="distributed-processing-and-compute-clusters"></a>Distribuované zpracování a výpočetní clustery  
 Výpočetní clustery a distribuované zpracování jsou obvykle používány pro rozsáhlých výpočtů, třeba finanční nebo počasí modelování a dekódování lidského DNA. Obvykle to se provádí tak, že servery jednotlivě na všechny klienty účastní výpočetní cluster přiřazovat úlohy. Tyto servery mohou mít i další požadavky; všechny úlohy možná muset být dokončeny v rámci určitou dobu, které vyžadují více než jeden počítač pro každou úlohu. Kromě toho pokud libovolného klienta spuštěním úlohy přestane fungovat, jiného klienta musí být může převzít kontrolu nad tuto úlohu a práci v něm. Více než jednoho klienta, může být nutné spustit pro stejnou úlohu dosahovat konzistentních výsledků. I když servery můžete spustit tento typ koordinaci klienta, můžete vytvořit řešení peer-to-peer, kde klienti přijetí úlohu nezávisle určit požadavky na server kolem úlohy a pomocí výpočetní OK můžete určit, jak tuto úlohu dokončit.  
  
## <a name="gaming"></a>Herní  
 Pomocí rovnocenného kanálu, vývojáři aplikace můžete vytvořit verze serveru bez jejich her, kde získat herní přesune předaných a synchronizované s ostatními hráči mechanismem peer-to-peer, a nikoli prostřednictvím centrální server. Pro malé ISV pomůžete odebrat provozní náklady spojené s nasazením, údržbu a údržby centrální servery. Hry napsané pomocí architektury peer-to-peer je možné přehrát přes Internet, nebo pevné nebo bezdrátové místní sítě. Sekundární herní aktivity, jako je s informacemi a ve hře chat mohou být vytvořeny pomocí sítě peer-to-peer.  
  
## <a name="see-also"></a>Viz také  
 [Koncepce protokolu Peer Channel](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)
