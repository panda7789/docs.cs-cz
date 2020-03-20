---
title: Obor názvů System.Net.PeerToPeer.Collaboration
ms.date: 03/30/2017
ms.assetid: b5d8c1c1-6844-4947-9759-c7f1b564bded
ms.openlocfilehash: f0c9ecaacc1d875aac8eed61a85ca7579f5cb8a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "64649529"
---
# <a name="about-the-systemnetpeertopeercollaboration-namespace"></a>Obor názvů System.Net.PeerToPeer.Collaboration
Obor <xref:System.Net.PeerToPeer.Collaboration> názvů poskytuje třídy a api, které se používají k implementaci aktivit spolupráce rovnocenných prostorů pomocí infrastruktury spolupráce peer-to-peer.  
  
## <a name="classes"></a>Třídy  
 Hlavní třídy používané při implementaci aktivity peer-to-peer spolupráce jsou:  
  
- <xref:System.Net.PeerToPeer.Collaboration.ContactManager>, který lze použít k uložení kontaktů mezi stranami.  
  
- Spolupráce, <xref:System.Net.PeerToPeer.Collaboration.PeerApplication> například herní, chatovací klient nebo konferenční řešení.  
  
- Partneři, kteří budou spolupracovat na aktivitě.  Tyto partnery mohou <xref:System.Net.PeerToPeer.Collaboration.PeerContact> <xref:System.Net.PeerToPeer.Collaboration.PeerNearMe>být <xref:System.Net.PeerToPeer.Collaboration.PeerEndPoint> reprezentovány jako , nebo objekty.  
  
- Samotná <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> statická třída, která určuje, které aplikace jsou k dispozici a které partnerské strany se jich účastní.  
  
 Metody <xref:System.Net.PeerToPeer.Collaboration.PeerContact.Invite%2A> se používají k pozvání partnerů do relace spolupráce.  Volající partner se může přihlásit k jinému partnerovi pro události, které signalizují aktualizace informací o aplikaci, objektu nebo stavu přidružených k relaci spolupráce. Třídy přítomnosti <xref:System.Net.PeerToPeer.Collaboration.Peer> určují, zda je <xref:System.Net.PeerToPeer.Collaboration.PeerScope> a k dispozici pro spolupráci a třída <xref:System.Net.PeerToPeer.Collaboration.PeerScope.Internet> se <xref:System.Net.PeerToPeer.Collaboration.PeerScope.NearMe>používá k určení, <xref:System.Net.PeerToPeer.Collaboration.PeerScope.None>kolik účasti je povoleno pro druhou stranou: (globální), , (podsíť) nebo .  
  
 Zasedání spolupráce se skládá ze čtyř kroků:  
  
- Zjišťování: Objevte nebo publikujte aplikace, partnery a informace o stavu.  Například najít další osoby v místní podsíti, které mají nainstalovány stejné hry.  
  
- Pozvání. Odesílat a přijímat zabezpečené pozvánky pro vzdálené <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> partnery ke spuštění nebo připojení relací.  
  
- Správa kontaktů. Přidejte zjištěné partnery <xref:System.Net.PeerToPeer.Collaboration.ContactManager>jako kontakt do .  
  
- Komunikace. Při navázání komunikace <xref:System.Net> použijte rozhraní <xref:System.Net.PeerToPeer> API, rozhraní API nebo třídy Peer Channel platformy Windows Communication Foundation pro vícestrannou komunikaci.  
  
 Například partner hostitele spustí relaci spolupráce a <xref:System.Net.PeerToPeer.Collaboration.ContactManager.CreateContact%2A> použije metodu k přidání vzdáleného partnera a jednoho z jeho místních partnerů do Správce kontaktů hostitelského partnera.  Tři uživatelé se pak zúčastní vlastní relace soukromé spolupráce.  
  
 Typické P2P aplikace jsou: konferenční hovory pro kolaborativní pořizování poznámek nebo whiteboarding, aplikace bez serveru chat, interaktivní reklamy a online herní relace.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Net.PeerToPeer.Collaboration>
