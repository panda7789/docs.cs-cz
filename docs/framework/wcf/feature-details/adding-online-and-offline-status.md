---
title: Přidání online a offline stavu
ms.date: 03/30/2017
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
ms.openlocfilehash: da170bbc22d04dcbf5f7cd4ac084a004bb4b026e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597680"
---
# <a name="adding-online-and-offline-status"></a><span data-ttu-id="e48b4-102">Přidání online a offline stavu</span><span class="sxs-lookup"><span data-stu-id="e48b4-102">Adding Online and Offline Status</span></span>
<span data-ttu-id="e48b4-103">V mnoha případech je důležité, aby aplikace monitoroval konkrétní údaje o stavu připojení rovnocenného kanálu.</span><span class="sxs-lookup"><span data-stu-id="e48b4-103">In many cases, it is important for an application to monitor specific details about the status of a Peer Channel connection.</span></span> <span data-ttu-id="e48b4-104">Tyto informace lze získat voláním `GetProperty` metody v implementaci <xref:System.ServiceModel.IOnlineStatus> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e48b4-104">You can obtain this information by calling the `GetProperty` method on an implementation of the <xref:System.ServiceModel.IOnlineStatus> interface.</span></span> <span data-ttu-id="e48b4-105">Objekt s implementací tohoto rozhraní může sledovat stav připojení nebo zaregistrovat obslužné rutiny událostí, jako jsou `OnOnline` a `OnOffline` , a okamžitě reagovat na změny stavu online.</span><span class="sxs-lookup"><span data-stu-id="e48b4-105">An object with an implementation of this interface can monitor connection status or register for event handlers, such as `OnOnline` and `OnOffline`, and react immediately as changes to online status occur.</span></span>  
  
 <span data-ttu-id="e48b4-106">V infrastruktuře partnerského kanálu se klient považuje za online, pokud je připojený aspoň k jednomu druhému partnerovi a offline v opačném případě.</span><span class="sxs-lookup"><span data-stu-id="e48b4-106">In the Peer Channel infrastructure, a client is considered to be online if it is connected to at least one other peer and offline otherwise.</span></span> <span data-ttu-id="e48b4-107">To může být užitečné zejména při ladění vývoje aplikací nebo při zobrazení podrobných informací koncovému uživateli.</span><span class="sxs-lookup"><span data-stu-id="e48b4-107">This can be particularly useful in both debugging a developing applications or displaying detailed information to the end user.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e48b4-108">Online obslužná rutina události by před odesláním zpráv měla nejdřív zajistit, aby byl uzel otevřený.</span><span class="sxs-lookup"><span data-stu-id="e48b4-108">An online event handler should first ensure that the node is open before sending any messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e48b4-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="e48b4-109">See also</span></span>

- [<span data-ttu-id="e48b4-110">Vytvoření aplikace protokolu Peer Channel</span><span class="sxs-lookup"><span data-stu-id="e48b4-110">Building a Peer Channel Application</span></span>](building-a-peer-channel-application.md)
