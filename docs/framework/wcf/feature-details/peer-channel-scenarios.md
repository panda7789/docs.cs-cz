---
title: Scénáře rovnocenných kanálů
ms.date: 03/30/2017
ms.assetid: dae6e0f7-900c-45ee-8be9-3647698382fb
ms.openlocfilehash: 610668e5f3625c638fc1e814e0116df87970773b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62046381"
---
# <a name="peer-channel-scenarios"></a>Scénáře rovnocenných kanálů
Rozhraní API kanálu Peer podporují následující scénáře vývoje.  
  
## <a name="publicationsubscription-messaging"></a>Publikování/odběr pro zasílání zpráv  
 Společnosti, kteří vytvářejí aplikace publikace nebo odběru (pro příklad, akcií a vydavatelé titulky, sportovní skóre a zprávy o počasí) mohou pomocí protokolu Peer Channel a aplikace bez serveru. Uživatelům například můžete získat nejnovější sportovní výsledky díky připojení ke službě common sítě (nebo skupiny klientů) a šířit velké množství aktuální herní data bez zvýšeného zatížení serveru. To pomáhá zprostředkovatele dat poskytnout vyšší kvality služeb bez podstatně zvyšuje investice do technologie založené na serveru.  
  
## <a name="collaboration"></a>Spolupráce  
 Nezávislí výrobci softwaru (ISV) můžete vytvářet aplikace, které umožní uživatelům vytvořit úzké skupiny pro zapojení do aktivit peer-to-peer. Například to může zahrnovat týmy pracující na projektech, obrázek sdílení mezi přáteli, plánování stran aktivity a další. Tradičně tyto aktivity vždy zahrnovat serverů. protokolu Peer Channel však nabízí způsob, jak to cenově výhodnější způsobem tím, že umožňuje přístup v režimu offline scénáře, které nejsou implementované stejně snadno, v rámci modelu tradiční klient server.  
  
## <a name="distributed-processing-and-compute-clusters"></a>Distribuované zpracování a výpočetních clusterů  
 Výpočetní clustery a distribuované zpracování jsou obvykle používány pro výpočty ve velkém měřítku, jako jsou finanční/počasí modelování a dekódování lidské DNA. Obvykle je to tím, že servery jednotlivě na všechny klienty v rámci výpočtu clusteru přiřazuje jim úlohy. Tyto servery mohou mít i další požadavky; všechny úlohy možná muset dokončit v určitou dobu, které vyžadují více než jeden počítač pro každý úkol. Kromě toho pokud jakýkoli klient spuštění úlohy ocitne mimo provoz, jiného klienta musí být schopen převzít kontrolu nad tento úkol a provedení práce na něm. Více než jednoho klienta, může být nutné spustit stejný úkol dosahovat konzistentních výsledků. Přestože servery můžete spustit tento typ spolupráce klienta, můžete vytvořit řešení peer-to-peer, kde klienti přijímající úlohu nezávisle na sobě určit požadavky na server kolem úkolu a používat výpočetní sítě určit, jak tento úkol provést.  
  
## <a name="gaming"></a>Hry  
 Pomocí protokolu Peer Channel, vývojáři aplikací můžete vytvořit bez serveru verze své hry, kde získat her přesune předávány společnosti a synchronizovat s jinými hráči mechanismem peer-to-peer, a nikoli prostřednictvím centrální server. Pro malé nezávislým výrobcům softwaru díky tomu odebrat provozní náklady spojené s nasazením, údržbu a obsluze centrální servery. Hry napsané s využitím architektury peer-to-peer možné přehrát, přes Internet, nebo pevné nebo bezdrátové místní sítě. Sekundární herní aktivity, například s informacemi a konverzace ve hře může být vyvinuto s použitím sítě peer-to-peer.  
  
## <a name="see-also"></a>Viz také:

- [Koncepce protokolu Peer Channel](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)
