---
title: Spolupráce peer-to-peer
ms.date: 03/30/2017
ms.assetid: b6216d88-bccb-4a59-9f1c-9f751708e811
ms.openlocfilehash: 7cf92f6bf3c269e584cb8b3cdcf910be5b89fd7e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047385"
---
# <a name="peer-to-peer-collaboration"></a>Spolupráce peer-to-peer

Sítě peer-to-peer je využití poměrně výkonných počítačů (osobní počítače), které existují na hranici Internetu, a to více než jenom pro výpočetní úlohy založené na klientech. Moderní osobní počítač (PC) má velmi rychlý procesor, rozsáhlou paměť a velký pevný disk, přičemž žádná z nich se při provádění běžných výpočetních úloh, jako je e-mail a procházení webu, nevyužívá úplně. Moderní počítač může snadno fungovat jako klient i server (partner) pro mnoho typů aplikací.  
  
Infrastruktura spolupráce peer-to-peer je zjednodušená implementace infrastruktury Microsoft Windows peer-to-peer, která využívá službu lidé v mém okolí v systému Windows Vista a novějších platformách. Je nejvhodnější pro aplikace s povoleným partnerským vztahem v podsíti, pro kterou funguje služba lidé v mém okolí, i když může obsluhovat také koncové body Internetu nebo kontakty. Zahrnuje společného správce kontaktů, který používá Live Messenger a další živé aplikace k určení koncových bodů, dostupnosti a přítomnosti kontaktů.  
  
## <a name="collaboration-applications"></a>Aplikace pro spolupráci

 Typická aplikace pro spolupráci Peer-to-peer se skládá z následujících kroků:  
  
- Partner Určuje identitu partnerského zařízení, která má zájem o hostování relace spolupráce.  
  
- Požadavek na hostování relace se pošle, a proto Partnerská strana souhlasí s tím, aby spravovala aktivitu spolupráce.  
  
- Hostitel pozve kontakty v podsíti (včetně žadatele) k relaci.  
  
- Všichni partneři, kteří chtějí spolupracovat, můžou hostitele přidat ke svým manažerům kontaktů.  
  
- Většina partnerských uzlů pošle odpovědi na pozvánky, ať už přijaté nebo odmítnuté, zpátky partnerovi hostitele včas.  
  
- Všichni partneři, kteří chtějí spolupracovat, se přihlásí k odběru partnerského uzlu hostitele.  
  
- I když partneři provádějí svou počáteční aktivitu spolupráce, hostitelská partner může do svého správce kontaktů přidat vzdálené partnerské uzly. Také zpracovává všechny reakce na pozvánky, které určují, kdo přijal, kdo odmítl a kdo na něj neodpověděl.  Může zrušit pozvánky na uživatele, kteří neodpověděli, nebo provést nějakou jinou aktivitu.  
  
- V tomto okamžiku může Partnerská strana hostitele spustit relaci spolupráce se všemi pozvanými partnery nebo zaregistrovat aplikaci s infrastrukturou pro spolupráci.  Aplikace P2P používají infrastrukturu spolupráce peer-to-peer a <xref:System.Net.PeerToPeer.Collaboration> obor názvů ke koordinaci komunikace pro hry, vývěsky, konference a další aplikace pro nepřítomnost serveru.  
  
## <a name="peer-to-peer-networking-security"></a>Zabezpečení sítě peer-to-peer  

 Řadiče domény v doméně služby Active Directory poskytují ověřovací služby pomocí protokolu Kerberos. V partnerském prostředí bez serveru musí partneři poskytnout své vlastní ověřování. Pro sítě peer-to-peer může kterýkoli uzel fungovat jako certifikační autorita a odebrat požadavek na kořenový certifikát v úložišti důvěryhodných kořenových certifikátů jednotlivých partnerských uzlů. Ověřování je poskytované pomocí certifikátů podepsaných svým držitelem, které jsou formátované jako certifikáty X. 509. Jedná se o certifikáty, které vytváří každý partner, který generuje pár veřejného klíče/privátního klíče a certifikát podepsaný pomocí privátního klíče. Certifikát podepsaný svým držitelem se používá k ověřování a poskytuje informace o partnerské entitě. Podobně jako u ověřování X. 509 závisí ověřování sítě rovnocenných sítí na základě řetězu certifikátů, které se vrátí k veřejnému klíči, který je důvěryhodný.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.PeerToPeer.Collaboration>
- [Obor názvů System.Net.PeerToPeer.Collaboration](about-the-system-net-peertopeer-collaboration-namespace.md)
