---
title: Spolupráce peer-to-peer
ms.date: 03/30/2017
ms.assetid: b6216d88-bccb-4a59-9f1c-9f751708e811
ms.openlocfilehash: 7cf92f6bf3c269e584cb8b3cdcf910be5b89fd7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047385"
---
# <a name="peer-to-peer-collaboration"></a>Spolupráce mezi dvěma účastníky

Síť peer-to-peer je využití relativně výkonných počítačů (osobních počítačů), které existují na okraji Internetu pro více než jen klientské výpočetní úlohy. Moderní osobní počítač (PC) má velmi rychlý procesor, rozsáhlou paměť a velký pevný disk, z nichž žádný není plně využíván při provádění běžných výpočetních úloh, jako je e-mail a procházení webu. Moderní počítač může snadno fungovat jako klient i server (peer) pro mnoho typů aplikací.  
  
Infrastruktura spolupráce peer-to-peer je zjednodušená implementace infrastruktury Microsoft Windows Peer-to-Peer, která využívá službu Lidé v mém okolí v systému Windows Vista a novějších platformách. Nejlépe se používá pro aplikace s podporou rovnocenných zařízení v rámci podsítě, pro kterou služba People Near Me funguje, i když může také obsluhovat koncové body nebo kontakty v Internetu. Zahrnuje společný Správce kontaktů, který používá Live Messenger a další aplikace podporující živé vysílání k určení koncových bodů kontaktu, dostupnosti a přítomnosti.  
  
## <a name="collaboration-applications"></a>Aplikace pro spolupráci

 Typická aplikace pro spolupráci mezi dvěma účastníky se skládá z následujících kroků:  
  
- Peer určuje identitu partnera, který má zájem o hostování relace spolupráce  
  
- Žádost o hostování relace je odeslána, nějak a partner hostitele souhlasí se správou aktivity spolupráce.  
  
- Hostitel pozve kontakty v podsíti (včetně žadatele) do relace.  
  
- Všichni partneři, kteří chtějí spolupracovat, mohou přidat hostitele do svých správců kontaktů.  
  
- Většina partnerů odešle odpovědi na pozvánky, ať už přijaté nebo odmítnuté, zpět hostitelskému partnerovi včas.  
  
- Všichni partneři, kteří chtějí spolupracovat, se přihlásí k odběru partnerského partnera hostitele.  
  
- Zatímco partneři provádějí svou počáteční aktivitu spolupráce, partner hostitelského partnera může přidat vzdálené partnery do svého správce kontaktů. Zpracovává také všechny odpovědi na pozvánky, aby určil, kdo přijal, kdo odmítl a kdo neodpověděl.  Může zrušit pozvánky pro ty, kteří neodpověděli, nebo provést jinou činnost.  
  
- V tomto okamžiku může partner hostitele zahájit relaci spolupráce se všemi pozvanými partnery nebo zaregistrovat aplikaci s infrastrukturou pro spolupráci.  Aplikace P2P používají infrastrukturu spolupráce peer-to-peer a <xref:System.Net.PeerToPeer.Collaboration> obor názvů ke koordinaci komunikace pro hry, vývěsky, konference a další aplikace bez serveru.  
  
## <a name="peer-to-peer-networking-security"></a>Zabezpečení sítě mezi dvěma účastníky  

 V doméně služby Active Directory poskytují řadiče domény ověřovací služby pomocí protokolu Kerberos. V prostředí peer bez serveru musí partneři poskytovat vlastní ověřování. Pro peer-to-peer sítě může každý uzel fungovat jako certifikační autorita, odebrání požadavku kořenového certifikátu v úložišti důvěryhodných kořenových adresářů každého partnera. Ověřování je poskytováno pomocí certifikátů podepsaných svým držitelem, formátovaných jako certifikáty X.509. Jedná se o certifikáty, které jsou vytvořeny jednotlivými rovnocennými partnery, které generují dvojici veřejného klíče a soukromého klíče a certifikát, který je podepsán pomocí soukromého klíče. Certifikát podepsaný svým držitelem se používá k ověřování a k poskytování informací o entitě druhé strany. Stejně jako ověřování X.509, peer networking ověřování závisí na řetězci certifikátů, které se vracejí k důvěryhodnému veřejnému klíči.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Net.PeerToPeer.Collaboration>
- [Obor názvů System.Net.PeerToPeer.Collaboration](about-the-system-net-peertopeer-collaboration-namespace.md)
