---
title: Obor názvů System.Net.PeerToPeer.Collaboration
ms.date: 03/30/2017
ms.assetid: b5d8c1c1-6844-4947-9759-c7f1b564bded
ms.openlocfilehash: f0c9ecaacc1d875aac8eed61a85ca7579f5cb8a1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649529"
---
# <a name="about-the-systemnetpeertopeercollaboration-namespace"></a>Obor názvů System.Net.PeerToPeer.Collaboration
<xref:System.Net.PeerToPeer.Collaboration> Obor názvů obsahuje třídy a rozhraní API, která slouží k implementaci aktivity spolupráce peer pomocí infrastruktury spolupráci Peer-to-Peer.  
  
## <a name="classes"></a>Třídy  
 Hlavní třídy použitý v implementaci aktivity spolupráce Peer-to-Peer jsou:  
  
- <xref:System.Net.PeerToPeer.Collaboration.ContactManager>, Který slouží k ukládání partnerské kontakty.  
  
- <xref:System.Net.PeerToPeer.Collaboration.PeerApplication> Ve kterém chcete spolupracovat, jako jsou hry, klienta nebo konference řešení.  
  
- Partnerské uzly, které budete spolupracovat v nějaké aktivitě.  Těchto partnerských uzlů může být reprezentován jako <xref:System.Net.PeerToPeer.Collaboration.PeerContact>, <xref:System.Net.PeerToPeer.Collaboration.PeerNearMe>, nebo <xref:System.Net.PeerToPeer.Collaboration.PeerEndPoint> objekty.  
  
- Statické <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> třídu, která určuje, které aplikace jsou dostupné a které partnerské uzly se účastní programu je.  
  
 <xref:System.Net.PeerToPeer.Collaboration.PeerContact.Invite%2A> Metody se používají k pozvat kolegy k relaci spolupráci.  Volání peer můžete přihlásit k odběru jiného partnera pro události, signál aktualizace informací o aplikaci, objekt nebo přítomnosti přidruženého relaci spolupráce. Přítomnost třídy určují, jestli <xref:System.Net.PeerToPeer.Collaboration.Peer> je k dispozici pro spolupráci a <xref:System.Net.PeerToPeer.Collaboration.PeerScope> třída se používá k určení, kolik účast je povolený pro partnerský uzel: <xref:System.Net.PeerToPeer.Collaboration.PeerScope.Internet> (globální), <xref:System.Net.PeerToPeer.Collaboration.PeerScope.NearMe>, (podsítě) nebo <xref:System.Net.PeerToPeer.Collaboration.PeerScope.None>.  
  
 Relaci spolupráce se skládá ze čtyř kroků:  
  
- Zjišťování. Podívejte se na nebo publikování aplikace, partnerech a informace o stavu.  Například vyhledejte jiní lidé v místní podsíti, která mají stejné hry nainstalované.  
  
- Pozvání. Odesílat a přijímat zabezpečené pozvánky pro vzdálené peer(s) ke spuštění nebo připojení <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> relace.  
  
- Obraťte se na správu. Přidat zjištěné partnerských uzlů jako kontakt <xref:System.Net.PeerToPeer.Collaboration.ContactManager>.  
  
- Komunikace. Při komunikaci se naváže, použijte <xref:System.Net> rozhraní API, <xref:System.Net.PeerToPeer> rozhraní API nebo Windows Communication Foundation protokolu Peer Channel třídy pro éře komunikace.  
  
 Například spustí relaci spolupráci peer hostitele a využívá <xref:System.Net.PeerToPeer.Collaboration.ContactManager.CreateContact%2A> způsob, jak přidat vzdáleném partnerském a jeden z jeho místní partnerské počítače, kontaktujte správce partnerského uzlu hostitele.  Tři uživatele se pak účastní relace jejich vlastní privátní spolupráci.  
  
 Typická aplikace P2P: konferenční hovory pro spolupráci pořizování nebo využití tabulí, aplikace bez serveru chatu, interaktivní oznámení o inzerovaných programech a hraní online relace.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.PeerToPeer.Collaboration>
