---
title: Spolupráce peer-to-Peer
ms.date: 03/30/2017
ms.assetid: b6216d88-bccb-4a59-9f1c-9f751708e811
author: mcleblanc
ms.author: markl
ms.openlocfilehash: c81300d160e2ec175f61f286047fa92015345942
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47198147"
---
# <a name="peer-to-peer-collaboration"></a>Spolupráce peer-to-Peer
Sítě peer-to-peer je využití poměrně efektivní počítačů (počítače), které existují na hraničních zařízeních Internetu pro více než jen klientské výpočetní úlohy. Moderní osobního počítače (PC) má velmi rychlý procesor, obrovské paměti a velký pevný disk, z nichž žádnou jsou plně využívá při provádění běžných výpočetní úlohy, jako je například e-mailu a procházení webu. Moderní počítač může snadno fungovat jako klient i server (sdílené) pro mnoho typů aplikací.  
  
-   Infrastruktura spolupráce Peer-to-Peer je zjednodušenou implementaci Peer-to-Peer infrastruktury Microsoft Windows, které využívá připojení lidé v okolí mi služby v systémech Windows Vista a novější platformy. To je nejvhodnější pro aplikace pro práci s sdílené v rámci podsítě pro kterou lidé téměř mě service funguje, sice může obsluhovat internetové koncové body nebo kontakty i. To zahrnuje běžné správce kontaktovat, který slouží k určení kontaktů koncové body, dostupnosti a přítomnost Live Messenger a dalších aplikací pracujících s Live.  
  
-  
  
## <a name="collaboration-applications"></a>Aplikace pro spolupráci  
 Typické spolupráci peer-to-peer aplikace se skládá z následujících kroků:  
  
-   Peer určuje identitu partnerského uzlu, kteří chtějí hostování relaci spolupráce  
  
-   Je odeslána žádost o hostiteli relace, nějakým způsobem, a partnerským zařízením hostitele souhlasí, že ke správě aktivity spolupráce.  
  
-   Hostitel vyzvat kontakty v podsíti (včetně žadatel) k relaci.  
  
-   Všechny partnerské uzly, kteří potřebují spolupracovat může přidat hostitele tak, aby jejich kontaktujte správce.  
  
-   Většina partnerské uzly pošle odpovědi na pozvánku, zda přijata nebo odmítnuta zpět na hostitele partnera včas.  
  
-   Všechny partnerské uzly, kteří potřebují spolupracovat se přihlásit k partnerským zařízením hostitele.  
  
-   Zatímco partnerské uzly provádíte jejich aktivita počáteční spolupráce, partnerský uzel hostitele přidat vzdálených partnerských uzlů jeho kontaktujte správce. Také zpracuje všechny odpovědi na pozvánku k určení kteří přijali, kdo odmítl a kdo nebyl odpovědi.  Může zrušit pozvánky všem uživatelům, kteří neodpověděli, nebo provést nějakou aktivitu.  
  
-   Sdílené hostitele v tomto okamžiku můžete spustit relaci spolupráci se všemi pozvaný partnery nebo registrace aplikace s vaší stávající infrastrukturou spolupráci.  P2P aplikací používat infrastrukturu spolupráci Peer-to-Peer a <xref:System.Net.PeerToPeer.Collaboration> obor názvů pro koordinaci komunikace pro hry, BBS, konference a další aplikace bez serveru přítomnost.  
  
-  
  
## <a name="peer-to-peer-networking-security"></a>Zabezpečení sítě peer-to-Peer  
 V doméně služby Active Directory řadiče domény poskytovaly služby ověřování pomocí protokolu Kerberos. V prostředí bez serveru peer partnerské uzly musíte zadat své vlastní ověřování. Pro Peer-to-Peer sítě může fungovat libovolný uzel jako certifikační Autorita, odebírání požadavek kořenového certifikátu v každé partnerské důvěryhodného kořenového úložiště. Ověřování je prováděno pomocí certifikátů podepsaných svým držitelem, formátovaný jako certifikáty X.509. Toto jsou certifikáty, které jsou vytvořeny pomocí každého partnera, který vygeneruje veřejný klíč/privátní klíčový pár a certifikát, který je podepsaný pomocí soukromého klíče. Certifikát podepsaný svým držitelem slouží k ověřování a k poskytnutí informací o entitě peer. Jako je například ověřování X.509 rovnocenné ověřování sítě závisí na službě řetěz certifikátů trasování zpět na veřejný klíč, který je důvěryhodný.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.PeerToPeer.Collaboration>  
 [Obor názvů System.Net.PeerToPeer.Collaboration](../../../docs/framework/network-programming/about-the-system-net-peertopeer-collaboration-namespace.md)
