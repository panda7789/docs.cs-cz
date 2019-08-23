---
title: Přidání online a offline stavu
ms.date: 03/30/2017
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
ms.openlocfilehash: 74b113d64003756982a6b5701d9601c3116a9046
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960650"
---
# <a name="adding-online-and-offline-status"></a><span data-ttu-id="b779d-102">Přidání online a offline stavu</span><span class="sxs-lookup"><span data-stu-id="b779d-102">Adding Online and Offline Status</span></span>
<span data-ttu-id="b779d-103">V mnoha případech je důležité, aby aplikace monitoroval konkrétní údaje o stavu připojení rovnocenného kanálu.</span><span class="sxs-lookup"><span data-stu-id="b779d-103">In many cases, it is important for an application to monitor specific details about the status of a Peer Channel connection.</span></span> <span data-ttu-id="b779d-104">Tyto informace lze získat voláním `GetProperty` metody v implementaci <xref:System.ServiceModel.IOnlineStatus> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b779d-104">You can obtain this information by calling the `GetProperty` method on an implementation of the <xref:System.ServiceModel.IOnlineStatus> interface.</span></span> <span data-ttu-id="b779d-105">Objekt s implementací tohoto rozhraní může sledovat stav připojení nebo zaregistrovat obslužné rutiny událostí, jako jsou `OnOnline` a `OnOffline`, a okamžitě reagovat na změny stavu online.</span><span class="sxs-lookup"><span data-stu-id="b779d-105">An object with an implementation of this interface can monitor connection status or register for event handlers, such as `OnOnline` and `OnOffline`, and react immediately as changes to online status occur.</span></span>  
  
 <span data-ttu-id="b779d-106">V infrastruktuře partnerského kanálu se klient považuje za online, pokud je připojený aspoň k jednomu druhému partnerovi a offline v opačném případě.</span><span class="sxs-lookup"><span data-stu-id="b779d-106">In the Peer Channel infrastructure, a client is considered to be online if it is connected to at least one other peer and offline otherwise.</span></span> <span data-ttu-id="b779d-107">To může být užitečné zejména při ladění vývoje aplikací nebo při zobrazení podrobných informací koncovému uživateli.</span><span class="sxs-lookup"><span data-stu-id="b779d-107">This can be particularly useful in both debugging a developing applications or displaying detailed information to the end user.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b779d-108">Online obslužná rutina události by před odesláním zpráv měla nejdřív zajistit, aby byl uzel otevřený.</span><span class="sxs-lookup"><span data-stu-id="b779d-108">An online event handler should first ensure that the node is open before sending any messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b779d-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b779d-109">See also</span></span>

- [<span data-ttu-id="b779d-110">Vytvoření aplikace protokolu Peer Channel</span><span class="sxs-lookup"><span data-stu-id="b779d-110">Building a Peer Channel Application</span></span>](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
