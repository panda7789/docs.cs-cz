---
title: "Přidání online a offline stavu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: adb767d3b7a7b991ebcfd8c44e55edb8726cb627
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="adding-online-and-offline-status"></a><span data-ttu-id="eadf9-102">Přidání online a offline stavu</span><span class="sxs-lookup"><span data-stu-id="eadf9-102">Adding Online and Offline Status</span></span>
<span data-ttu-id="eadf9-103">V mnoha případech je důležité pro aplikaci monitorovat konkrétní podrobnosti o stavu připojení rovnocenného kanálu.</span><span class="sxs-lookup"><span data-stu-id="eadf9-103">In many cases, it is important for an application to monitor specific details about the status of a Peer Channel connection.</span></span> <span data-ttu-id="eadf9-104">Tyto informace můžete získat pomocí volání `GetProperty` metodu implementace <xref:System.ServiceModel.IOnlineStatus> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="eadf9-104">You can obtain this information by calling the `GetProperty` method on an implementation of the <xref:System.ServiceModel.IOnlineStatus> interface.</span></span> <span data-ttu-id="eadf9-105">Objekt s implementace tohoto rozhraní můžete monitorovat stav připojení nebo zaregistrovat pro obslužné rutiny událostí, jako například `OnOnline` a `OnOffline`a reagovat okamžitě, jsou prováděny změny online stavu.</span><span class="sxs-lookup"><span data-stu-id="eadf9-105">An object with an implementation of this interface can monitor connection status or register for event handlers, such as `OnOnline` and `OnOffline`, and react immediately as changes to online status occur.</span></span>  
  
 <span data-ttu-id="eadf9-106">V infrastruktuře rovnocenného kanálu klienta bude považován za online, pokud je připojený k alespoň jeden další sdílené a offline jinak.</span><span class="sxs-lookup"><span data-stu-id="eadf9-106">In the Peer Channel infrastructure, a client is considered to be online if it is connected to at least one other peer and offline otherwise.</span></span> <span data-ttu-id="eadf9-107">To může být obzvláště užitečná při ladění vývoj aplikací i zobrazení podrobné informace pro koncového uživatele.</span><span class="sxs-lookup"><span data-stu-id="eadf9-107">This can be particularly useful in both debugging a developing applications or displaying detailed information to the end user.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eadf9-108">Online obslužnou rutinu by měl nejdříve se ujistěte, že uzel je otevřen před odesláním všechny zprávy.</span><span class="sxs-lookup"><span data-stu-id="eadf9-108">An online event handler should first ensure that the node is open before sending any messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eadf9-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="eadf9-109">See Also</span></span>  
 [<span data-ttu-id="eadf9-110">Vytvoření aplikace protokolu Peer Channel</span><span class="sxs-lookup"><span data-stu-id="eadf9-110">Building a Peer Channel Application</span></span>](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
