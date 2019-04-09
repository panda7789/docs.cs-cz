---
title: Přidání online a offline stavu
ms.date: 03/30/2017
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
ms.openlocfilehash: 15a963d4de0dcf1d7f0162b0a3266e17d4073ecd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147690"
---
# <a name="adding-online-and-offline-status"></a><span data-ttu-id="fe3f7-102">Přidání online a offline stavu</span><span class="sxs-lookup"><span data-stu-id="fe3f7-102">Adding Online and Offline Status</span></span>
<span data-ttu-id="fe3f7-103">V mnoha případech je důležité pro aplikaci pro sledování konkrétní podrobnosti o stavu připojení k protokolu Peer Channel.</span><span class="sxs-lookup"><span data-stu-id="fe3f7-103">In many cases, it is important for an application to monitor specific details about the status of a Peer Channel connection.</span></span> <span data-ttu-id="fe3f7-104">Tyto informace lze získat voláním `GetProperty` metodu na implementaci <xref:System.ServiceModel.IOnlineStatus> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fe3f7-104">You can obtain this information by calling the `GetProperty` method on an implementation of the <xref:System.ServiceModel.IOnlineStatus> interface.</span></span> <span data-ttu-id="fe3f7-105">Objekt se implementace tohoto rozhraní můžete monitorovat stav připojení nebo zaregistrujte obslužné rutiny událostí, jako například `OnOnline` a `OnOffline`a reagovat okamžitě jak dojde ke změnám do stavu online.</span><span class="sxs-lookup"><span data-stu-id="fe3f7-105">An object with an implementation of this interface can monitor connection status or register for event handlers, such as `OnOnline` and `OnOffline`, and react immediately as changes to online status occur.</span></span>  
  
 <span data-ttu-id="fe3f7-106">V infrastruktuře protokolu Peer Channel klient se považuje za online, pokud je připojen alespoň jeden další partnerské a offline jinak.</span><span class="sxs-lookup"><span data-stu-id="fe3f7-106">In the Peer Channel infrastructure, a client is considered to be online if it is connected to at least one other peer and offline otherwise.</span></span> <span data-ttu-id="fe3f7-107">To může být zvláště užitečné při ladění vývoj aplikací i zobrazení podrobných informací pro koncového uživatele.</span><span class="sxs-lookup"><span data-stu-id="fe3f7-107">This can be particularly useful in both debugging a developing applications or displaying detailed information to the end user.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fe3f7-108">Obslužná rutina události online by měly nejprve zkontrolujte, že uzel otevřít před odesláním jakýchkoli zpráv.</span><span class="sxs-lookup"><span data-stu-id="fe3f7-108">An online event handler should first ensure that the node is open before sending any messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe3f7-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fe3f7-109">See also</span></span>

- [<span data-ttu-id="fe3f7-110">Vytvoření aplikace rovnocenného kanálu</span><span class="sxs-lookup"><span data-stu-id="fe3f7-110">Building a Peer Channel Application</span></span>](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
