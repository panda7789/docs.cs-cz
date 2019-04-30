---
title: Přidání online a offline stavu
ms.date: 03/30/2017
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
ms.openlocfilehash: 15a963d4de0dcf1d7f0162b0a3266e17d4073ecd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857737"
---
# <a name="adding-online-and-offline-status"></a>Přidání online a offline stavu
V mnoha případech je důležité pro aplikaci pro sledování konkrétní podrobnosti o stavu připojení k protokolu Peer Channel. Tyto informace lze získat voláním `GetProperty` metodu na implementaci <xref:System.ServiceModel.IOnlineStatus> rozhraní. Objekt se implementace tohoto rozhraní můžete monitorovat stav připojení nebo zaregistrujte obslužné rutiny událostí, jako například `OnOnline` a `OnOffline`a reagovat okamžitě jak dojde ke změnám do stavu online.  
  
 V infrastruktuře protokolu Peer Channel klient se považuje za online, pokud je připojen alespoň jeden další partnerské a offline jinak. To může být zvláště užitečné při ladění vývoj aplikací i zobrazení podrobných informací pro koncového uživatele.  
  
> [!NOTE]
>  Obslužná rutina události online by měly nejprve zkontrolujte, že uzel otevřít před odesláním jakýchkoli zpráv.  
  
## <a name="see-also"></a>Viz také:

- [Vytvoření aplikace protokolu Peer Channel](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
