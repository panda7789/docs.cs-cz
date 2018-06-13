---
title: Přidání online a offline stavu
ms.date: 03/30/2017
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
ms.openlocfilehash: fb19614c1975c5634a81ca2f40edb145b724cd1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488101"
---
# <a name="adding-online-and-offline-status"></a><span data-ttu-id="65458-102">Přidání online a offline stavu</span><span class="sxs-lookup"><span data-stu-id="65458-102">Adding Online and Offline Status</span></span>
<span data-ttu-id="65458-103">V mnoha případech je důležité pro aplikaci monitorovat konkrétní podrobnosti o stavu připojení rovnocenného kanálu.</span><span class="sxs-lookup"><span data-stu-id="65458-103">In many cases, it is important for an application to monitor specific details about the status of a Peer Channel connection.</span></span> <span data-ttu-id="65458-104">Tyto informace můžete získat pomocí volání `GetProperty` metodu implementace <xref:System.ServiceModel.IOnlineStatus> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="65458-104">You can obtain this information by calling the `GetProperty` method on an implementation of the <xref:System.ServiceModel.IOnlineStatus> interface.</span></span> <span data-ttu-id="65458-105">Objekt s implementace tohoto rozhraní můžete monitorovat stav připojení nebo zaregistrovat pro obslužné rutiny událostí, jako například `OnOnline` a `OnOffline`a reagovat okamžitě, jsou prováděny změny online stavu.</span><span class="sxs-lookup"><span data-stu-id="65458-105">An object with an implementation of this interface can monitor connection status or register for event handlers, such as `OnOnline` and `OnOffline`, and react immediately as changes to online status occur.</span></span>  
  
 <span data-ttu-id="65458-106">V infrastruktuře rovnocenného kanálu klienta bude považován za online, pokud je připojený k alespoň jeden další sdílené a offline jinak.</span><span class="sxs-lookup"><span data-stu-id="65458-106">In the Peer Channel infrastructure, a client is considered to be online if it is connected to at least one other peer and offline otherwise.</span></span> <span data-ttu-id="65458-107">To může být obzvláště užitečná při ladění vývoj aplikací i zobrazení podrobné informace pro koncového uživatele.</span><span class="sxs-lookup"><span data-stu-id="65458-107">This can be particularly useful in both debugging a developing applications or displaying detailed information to the end user.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="65458-108">Online obslužnou rutinu by měl nejdříve se ujistěte, že uzel je otevřen před odesláním všechny zprávy.</span><span class="sxs-lookup"><span data-stu-id="65458-108">An online event handler should first ensure that the node is open before sending any messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65458-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="65458-109">See Also</span></span>  
 [<span data-ttu-id="65458-110">Vytvoření aplikace protokolu Peer Channel</span><span class="sxs-lookup"><span data-stu-id="65458-110">Building a Peer Channel Application</span></span>](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
