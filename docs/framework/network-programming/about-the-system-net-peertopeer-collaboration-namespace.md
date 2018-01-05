---
title: O Namespace System.Net.PeerToPeer.Collaboration
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5d8c1c1-6844-4947-9759-c7f1b564bded
caps.latest.revision: "4"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 24571209673d7706955bdb9ffbe21ad6da98e18a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="about-the-systemnetpeertopeercollaboration-namespace"></a><span data-ttu-id="f6f83-102">O Namespace System.Net.PeerToPeer.Collaboration</span><span class="sxs-lookup"><span data-stu-id="f6f83-102">About the System.Net.PeerToPeer.Collaboration Namespace</span></span>
<span data-ttu-id="f6f83-103"><xref:System.Net.PeerToPeer.Collaboration> Obor názvů obsahuje třídy a rozhraní API, která slouží k implementaci aktivity spolupráce sdílené pomocí infrastruktury spolupráce Peer-to-Peer.</span><span class="sxs-lookup"><span data-stu-id="f6f83-103">The <xref:System.Net.PeerToPeer.Collaboration> namespace provides classes and APIs that are used to implement peer collaboration activities using the Peer-to-Peer Collaboration Infrastructure.</span></span>  
  
## <a name="classes"></a><span data-ttu-id="f6f83-104">Třídy</span><span class="sxs-lookup"><span data-stu-id="f6f83-104">Classes</span></span>  
 <span data-ttu-id="f6f83-105">Hlavní třídy používané při provádění aktivity spolupráce Peer-to-Peer jsou:</span><span class="sxs-lookup"><span data-stu-id="f6f83-105">The main classes used in the implementation of a Peer-to-Peer Collaboration activity are:</span></span>  
  
-   <span data-ttu-id="f6f83-106"><xref:System.Net.PeerToPeer.Collaboration.ContactManager>, Které lze použít k uložení sdílené kontakty.</span><span class="sxs-lookup"><span data-stu-id="f6f83-106">The <xref:System.Net.PeerToPeer.Collaboration.ContactManager>, which can be used to store peer contacts.</span></span>  
  
-   <span data-ttu-id="f6f83-107"><xref:System.Net.PeerToPeer.Collaboration.PeerApplication> Ve kterém chcete spolupracovat, jako je například hra, chatovací klienta nebo konference řešení.</span><span class="sxs-lookup"><span data-stu-id="f6f83-107">The <xref:System.Net.PeerToPeer.Collaboration.PeerApplication> in which to collaborate, such as a game, chat client, or conferencing solution.</span></span>  
  
-   <span data-ttu-id="f6f83-108">Partnerské uzly, které budou spolupracovat v aktivitě.</span><span class="sxs-lookup"><span data-stu-id="f6f83-108">The peers that will be collaborating in an activity.</span></span>  <span data-ttu-id="f6f83-109">Těchto partnerských uzlů může být reprezentován jako <xref:System.Net.PeerToPeer.Collaboration.PeerContact>, <xref:System.Net.PeerToPeer.Collaboration.PeerNearMe>, nebo <xref:System.Net.PeerToPeer.Collaboration.PeerEndPoint> objekty.</span><span class="sxs-lookup"><span data-stu-id="f6f83-109">These peers can be represented as <xref:System.Net.PeerToPeer.Collaboration.PeerContact>, <xref:System.Net.PeerToPeer.Collaboration.PeerNearMe>, or <xref:System.Net.PeerToPeer.Collaboration.PeerEndPoint> objects.</span></span>  
  
-   <span data-ttu-id="f6f83-110">Statické <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> třídy samostatně, která určuje, které aplikace jsou k dispozici a které partnerské uzly se účastní je.</span><span class="sxs-lookup"><span data-stu-id="f6f83-110">The static <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> class itself, which specifies which applications are available and which peers are participating in them.</span></span>  
  
 <span data-ttu-id="f6f83-111"><xref:System.Net.PeerToPeer.Collaboration.PeerContact.Invite%2A> Metody se používají k pozvat partnerské uzly k relaci spolupráce.</span><span class="sxs-lookup"><span data-stu-id="f6f83-111">The <xref:System.Net.PeerToPeer.Collaboration.PeerContact.Invite%2A> methods are used to invite peers to a collaboration session.</span></span>  <span data-ttu-id="f6f83-112">Volání sdílené může přihlásit k jiné sdílené pro události, signál aktualizace informací o aplikaci, objekt nebo přítomnosti přidružený relaci spolupráce.</span><span class="sxs-lookup"><span data-stu-id="f6f83-112">A calling peer can subscribe to another peer for events that signal updates to application, object, or presence information affiliated with the collaboration session.</span></span> <span data-ttu-id="f6f83-113">Zadejte přítomnosti třídy zda <xref:System.Net.PeerToPeer.Collaboration.Peer> je k dispozici pro spolupráci a <xref:System.Net.PeerToPeer.Collaboration.PeerScope> třída se používá k určení, kolik zapojení je povolen pro partnerský uzel: <xref:System.Net.PeerToPeer.Collaboration.PeerScope.Internet> (globální), <xref:System.Net.PeerToPeer.Collaboration.PeerScope.NearMe>, (podsítě) nebo <xref:System.Net.PeerToPeer.Collaboration.PeerScope.None>.</span><span class="sxs-lookup"><span data-stu-id="f6f83-113">Presence classes specify whether a <xref:System.Net.PeerToPeer.Collaboration.Peer> is available for collaboration, and the <xref:System.Net.PeerToPeer.Collaboration.PeerScope> class is used to specify how much participation is allowed for a peer:  <xref:System.Net.PeerToPeer.Collaboration.PeerScope.Internet> (global), <xref:System.Net.PeerToPeer.Collaboration.PeerScope.NearMe>, (subnet) or <xref:System.Net.PeerToPeer.Collaboration.PeerScope.None>.</span></span>  
  
 <span data-ttu-id="f6f83-114">Relaci spolupráce zahrnuje čtyři kroky:</span><span class="sxs-lookup"><span data-stu-id="f6f83-114">A collaboration session is comprised of four steps:</span></span>  
  
-   <span data-ttu-id="f6f83-115">Zjišťování.</span><span class="sxs-lookup"><span data-stu-id="f6f83-115">Discovery.</span></span> <span data-ttu-id="f6f83-116">Zjistit nebo publikovat aplikace, partnerech a informace o stavu.</span><span class="sxs-lookup"><span data-stu-id="f6f83-116">Discover or publish applications, peers, and presence information.</span></span>  <span data-ttu-id="f6f83-117">Například najít jiné osoby v místní podsíti, které mají stejné hry nainstalované.</span><span class="sxs-lookup"><span data-stu-id="f6f83-117">For instance, find other people on the local subnet that have the same games installed.</span></span>  
  
-   <span data-ttu-id="f6f83-118">Pozvánku.</span><span class="sxs-lookup"><span data-stu-id="f6f83-118">Invitation.</span></span> <span data-ttu-id="f6f83-119">Odesílat a přijímat zabezpečené pozvánky pro vzdálené peer(s) ke spuštění nebo připojení k <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> relací.</span><span class="sxs-lookup"><span data-stu-id="f6f83-119">Send and accept secure invitations for remote peer(s) to start or join <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> sessions.</span></span>  
  
-   <span data-ttu-id="f6f83-120">Obraťte se na správu.</span><span class="sxs-lookup"><span data-stu-id="f6f83-120">Contact Management.</span></span> <span data-ttu-id="f6f83-121">Přidat jako kontakt na zjištěné partnerské uzly <xref:System.Net.PeerToPeer.Collaboration.ContactManager>.</span><span class="sxs-lookup"><span data-stu-id="f6f83-121">Add discovered peers as a contact to a <xref:System.Net.PeerToPeer.Collaboration.ContactManager>.</span></span>  
  
-   <span data-ttu-id="f6f83-122">Komunikace.</span><span class="sxs-lookup"><span data-stu-id="f6f83-122">Communication.</span></span> <span data-ttu-id="f6f83-123">Po navázání komunikace použít <xref:System.Net> rozhraní API, <xref:System.Net.PeerToPeer> rozhraní API nebo třídy Windows Communication Foundation rovnocenného kanálu pro více stran komunikace.</span><span class="sxs-lookup"><span data-stu-id="f6f83-123">When communication is established, use the <xref:System.Net> APIs, the <xref:System.Net.PeerToPeer> API, or the Windows Communication Foundation Peer Channel classes for multiparty communications.</span></span>  
  
 <span data-ttu-id="f6f83-124">Například spustí relaci spolupráce sdílené hostitele a využívá <xref:System.Net.PeerToPeer.Collaboration.ContactManager.CreateContact%2A> metody přidat vzdálené sdílené a jeden z jeho místní partnerské počítače, obraťte se na správce partnerského uzlu hostitele.</span><span class="sxs-lookup"><span data-stu-id="f6f83-124">For example, the host peer starts a collaboration session, and utilizes the <xref:System.Net.PeerToPeer.Collaboration.ContactManager.CreateContact%2A> method to add a remote peer and one of its local peers to the Contact Manager of the host peer.</span></span>  <span data-ttu-id="f6f83-125">Tři uživatelé bude potom podílet na své vlastní relaci privátní spolupráce.</span><span class="sxs-lookup"><span data-stu-id="f6f83-125">The three users will then participate in their own private collaboration session.</span></span>  
  
 <span data-ttu-id="f6f83-126">Typické P2P aplikace jsou: konferenční hovory pro spolupráci poznámek nebo whiteboarding, bez serveru chatovací aplikace, interaktivní oznámení o inzerovaném programu a online herní relací.</span><span class="sxs-lookup"><span data-stu-id="f6f83-126">Typical P2P applications are: conference calls for collaborative note-taking or whiteboarding, serverless chat applications, interactive advertisements, and online gaming sessions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6f83-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="f6f83-127">See Also</span></span>  
 <xref:System.Net.PeerToPeer.Collaboration>
