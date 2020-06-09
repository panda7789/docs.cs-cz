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
# <a name="adding-online-and-offline-status"></a>Přidání online a offline stavu
V mnoha případech je důležité, aby aplikace monitoroval konkrétní údaje o stavu připojení rovnocenného kanálu. Tyto informace lze získat voláním `GetProperty` metody v implementaci <xref:System.ServiceModel.IOnlineStatus> rozhraní. Objekt s implementací tohoto rozhraní může sledovat stav připojení nebo zaregistrovat obslužné rutiny událostí, jako jsou `OnOnline` a `OnOffline` , a okamžitě reagovat na změny stavu online.  
  
 V infrastruktuře partnerského kanálu se klient považuje za online, pokud je připojený aspoň k jednomu druhému partnerovi a offline v opačném případě. To může být užitečné zejména při ladění vývoje aplikací nebo při zobrazení podrobných informací koncovému uživateli.  
  
> [!NOTE]
> Online obslužná rutina události by před odesláním zpráv měla nejdřív zajistit, aby byl uzel otevřený.  
  
## <a name="see-also"></a>Viz také

- [Vytvoření aplikace protokolu Peer Channel](building-a-peer-channel-application.md)
