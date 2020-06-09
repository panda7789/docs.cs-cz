---
title: Scénáře rovnocenných kanálů
ms.date: 03/30/2017
ms.assetid: dae6e0f7-900c-45ee-8be9-3647698382fb
ms.openlocfilehash: c4c24a0bafa4f73760d02de6242a9ed438d7d60e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596874"
---
# <a name="peer-channel-scenarios"></a>Scénáře rovnocenných kanálů
Rozhraní API pro rovnocenné kanály podporují následující vývojové scénáře.  
  
## <a name="publicationsubscription-messaging"></a>Zasílání zpráv pro publikování a odběr  
 Společnosti, které sestavují aplikace pro publikování a odběry (například akcie akcií a vydavatelé novinek, sportovní skóre a sestavy počasí), můžou používat rovnocenný kanál na aplikace bez serveru. Uživatelé můžou například získat nejnovější sportovní skóre připojením ke společné síti (nebo skupině klientů) a rozšířit velké množství aktuálních herních dat bez zvýšení zatížení serveru. To pomáhá poskytovateli dat poskytovat vyšší kvalitu služeb, aniž by došlo k výraznému nárůstu investic do technologií založených na serveru.  
  
## <a name="collaboration"></a>Spolupráce  
 Nezávislí výrobci softwaru (ISV) mohou vytvářet aplikace, které lidem umožňují vytvářet těsné skupiny pro účast v aktivitách peer-to-peer. To může například zahrnovat týmy pracující na projektech pro spolupráci, sdílení obrázků mezi přáteli, aktivitami plánování strany a další. Tradičně tyto aktivity vždy zahrnují servery. Nicméně rovnocenný kanál poskytuje takový způsob, jak to provést tak, že umožníte scénářům offline přístupu, které nejsou tak snadno implementované v tradičním modelu serverového klienta.  
  
## <a name="distributed-processing-and-compute-clusters"></a>Distribuované zpracování a výpočetní clustery  
 Výpočetní clustery a distribuované zpracování se obvykle používají pro rozsáhlé výpočty, jako je například finanční nebo povětrnostní modelování a dekódování lidského DNA. Obvykle je to provedeno tím, že servery přiřadí úkoly všem klientům účastnícím se výpočetního clusteru. Tyto servery můžou mít taky další požadavky. Například může být nutné dokončit všechny úlohy v určité době, což vyžaduje více než jeden počítač pro každý úkol. Navíc platí, že pokud některý z klientů, kteří úlohu spouštějí, přestane fungovat, jiný klient musí být schopný převzít tuto úlohu a na ní provádět práci. Podobně více než jeden klient bude muset spustit stejný úkol, aby zajistil konzistenci výsledků. I když můžou servery spustit tento typ koordinace klientů, můžete vytvořit řešení peer-to-peer, kde klienti dostávají úlohu nezávisle na tom, že na tomto úkolu určíte požadavky na server a pomocí výpočetní sítě určíte, jak tuto úlohu dokončit.  
  
## <a name="gaming"></a>Hry  
 Pomocí rovnocenného kanálu můžou vývojáři aplikací vytvářet verze svých her bez serveru, kde se hra přesouvá a synchronizuje s jinými hráči pomocí mechanismu peer-to-peer, nikoli prostřednictvím centrálního serveru. Pro malé nezávislé výrobce softwaru to pomáhá odebrat provozní náklady spojené s nasazením, údržbou a centrálními servery. Hry napsané pomocí architektury peer-to-peer lze přehrát přes Internet nebo v drátových nebo bezdrátových místních sítích. Sekundární herní aktivity, jako jsou třeba předsálí a konverzace, se dají vyvíjet pomocí sítě peer-to-peer.  
  
## <a name="see-also"></a>Viz také

- [Koncepce protokolu Peer Channel](peer-channel-concepts.md)
