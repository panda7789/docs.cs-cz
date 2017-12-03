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
ms.openlocfilehash: 5d5b6c858b5aa5918498ba8fccee41f7392ac32e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="adding-online-and-offline-status"></a>Přidání online a offline stavu
V mnoha případech je důležité pro aplikaci monitorovat konkrétní podrobnosti o stavu připojení rovnocenného kanálu. Tyto informace můžete získat pomocí volání `GetProperty` metodu implementace <xref:System.ServiceModel.IOnlineStatus> rozhraní. Objekt s implementace tohoto rozhraní můžete monitorovat stav připojení nebo zaregistrovat pro obslužné rutiny událostí, jako například `OnOnline` a `OnOffline`a reagovat okamžitě, jsou prováděny změny online stavu.  
  
 V infrastruktuře rovnocenného kanálu klienta bude považován za online, pokud je připojený k alespoň jeden další sdílené a offline jinak. To může být obzvláště užitečná při ladění vývoj aplikací i zobrazení podrobné informace pro koncového uživatele.  
  
> [!NOTE]
>  Online obslužnou rutinu by měl nejdříve se ujistěte, že uzel je otevřen před odesláním všechny zprávy.  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření aplikace rovnocenného kanálu](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
