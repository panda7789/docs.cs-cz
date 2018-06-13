---
title: O Namespace System.Net.PeerToPeer.Collaboration
ms.date: 03/30/2017
ms.assetid: b5d8c1c1-6844-4947-9759-c7f1b564bded
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 5d23fe51249df53b3874a8fd6fda60377f7366ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394040"
---
# <a name="about-the-systemnetpeertopeercollaboration-namespace"></a>O Namespace System.Net.PeerToPeer.Collaboration
<xref:System.Net.PeerToPeer.Collaboration> Obor názvů obsahuje třídy a rozhraní API, která slouží k implementaci aktivity spolupráce sdílené pomocí infrastruktury spolupráce Peer-to-Peer.  
  
## <a name="classes"></a>Třídy  
 Hlavní třídy používané při provádění aktivity spolupráce Peer-to-Peer jsou:  
  
-   <xref:System.Net.PeerToPeer.Collaboration.ContactManager>, Které lze použít k uložení sdílené kontakty.  
  
-   <xref:System.Net.PeerToPeer.Collaboration.PeerApplication> Ve kterém chcete spolupracovat, jako je například hra, chatovací klienta nebo konference řešení.  
  
-   Partnerské uzly, které budou spolupracovat v aktivitě.  Těchto partnerských uzlů může být reprezentován jako <xref:System.Net.PeerToPeer.Collaboration.PeerContact>, <xref:System.Net.PeerToPeer.Collaboration.PeerNearMe>, nebo <xref:System.Net.PeerToPeer.Collaboration.PeerEndPoint> objekty.  
  
-   Statické <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> třídy samostatně, která určuje, které aplikace jsou k dispozici a které partnerské uzly se účastní je.  
  
 <xref:System.Net.PeerToPeer.Collaboration.PeerContact.Invite%2A> Metody se používají k pozvat partnerské uzly k relaci spolupráce.  Volání sdílené může přihlásit k jiné sdílené pro události, signál aktualizace informací o aplikaci, objekt nebo přítomnosti přidružený relaci spolupráce. Zadejte přítomnosti třídy zda <xref:System.Net.PeerToPeer.Collaboration.Peer> je k dispozici pro spolupráci a <xref:System.Net.PeerToPeer.Collaboration.PeerScope> třída se používá k určení, kolik zapojení je povolen pro partnerský uzel: <xref:System.Net.PeerToPeer.Collaboration.PeerScope.Internet> (globální), <xref:System.Net.PeerToPeer.Collaboration.PeerScope.NearMe>, (podsítě) nebo <xref:System.Net.PeerToPeer.Collaboration.PeerScope.None>.  
  
 Relaci spolupráce zahrnuje čtyři kroky:  
  
-   Zjišťování. Zjistit nebo publikovat aplikace, partnerech a informace o stavu.  Například najít jiné osoby v místní podsíti, které mají stejné hry nainstalované.  
  
-   Pozvánku. Odesílat a přijímat zabezpečené pozvánky pro vzdálené peer(s) ke spuštění nebo připojení k <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> relací.  
  
-   Obraťte se na správu. Přidat jako kontakt na zjištěné partnerské uzly <xref:System.Net.PeerToPeer.Collaboration.ContactManager>.  
  
-   Komunikace. Po navázání komunikace použít <xref:System.Net> rozhraní API, <xref:System.Net.PeerToPeer> rozhraní API nebo třídy Windows Communication Foundation rovnocenného kanálu pro více stran komunikace.  
  
 Například spustí relaci spolupráce sdílené hostitele a využívá <xref:System.Net.PeerToPeer.Collaboration.ContactManager.CreateContact%2A> metody přidat vzdálené sdílené a jeden z jeho místní partnerské počítače, obraťte se na správce partnerského uzlu hostitele.  Tři uživatelé bude potom podílet na své vlastní relaci privátní spolupráce.  
  
 Typické P2P aplikace jsou: konferenční hovory pro spolupráci poznámek nebo whiteboarding, bez serveru chatovací aplikace, interaktivní oznámení o inzerovaném programu a online herní relací.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.PeerToPeer.Collaboration>
