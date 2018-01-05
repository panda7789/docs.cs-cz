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
# <a name="adding-online-and-offline-status"></a>Přidání online a offline stavu
V mnoha případech je důležité pro aplikaci monitorovat konkrétní podrobnosti o stavu připojení rovnocenného kanálu. Tyto informace můžete získat pomocí volání `GetProperty` metodu implementace <xref:System.ServiceModel.IOnlineStatus> rozhraní. Objekt s implementace tohoto rozhraní můžete monitorovat stav připojení nebo zaregistrovat pro obslužné rutiny událostí, jako například `OnOnline` a `OnOffline`a reagovat okamžitě, jsou prováděny změny online stavu.  
  
 V infrastruktuře rovnocenného kanálu klienta bude považován za online, pokud je připojený k alespoň jeden další sdílené a offline jinak. To může být obzvláště užitečná při ladění vývoj aplikací i zobrazení podrobné informace pro koncového uživatele.  
  
> [!NOTE]
>  Online obslužnou rutinu by měl nejdříve se ujistěte, že uzel je otevřen před odesláním všechny zprávy.  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření aplikace protokolu Peer Channel](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
