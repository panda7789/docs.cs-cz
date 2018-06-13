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
# <a name="adding-online-and-offline-status"></a>Přidání online a offline stavu
V mnoha případech je důležité pro aplikaci monitorovat konkrétní podrobnosti o stavu připojení rovnocenného kanálu. Tyto informace můžete získat pomocí volání `GetProperty` metodu implementace <xref:System.ServiceModel.IOnlineStatus> rozhraní. Objekt s implementace tohoto rozhraní můžete monitorovat stav připojení nebo zaregistrovat pro obslužné rutiny událostí, jako například `OnOnline` a `OnOffline`a reagovat okamžitě, jsou prováděny změny online stavu.  
  
 V infrastruktuře rovnocenného kanálu klienta bude považován za online, pokud je připojený k alespoň jeden další sdílené a offline jinak. To může být obzvláště užitečná při ladění vývoj aplikací i zobrazení podrobné informace pro koncového uživatele.  
  
> [!NOTE]
>  Online obslužnou rutinu by měl nejdříve se ujistěte, že uzel je otevřen před odesláním všechny zprávy.  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření aplikace protokolu Peer Channel](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
