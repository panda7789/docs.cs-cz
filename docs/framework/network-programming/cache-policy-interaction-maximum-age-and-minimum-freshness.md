---
title: "Interakce zásad do mezipaměti – maximální stáří a minimální aktuálnosti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time-based cache policies
- Revalidate policy
- cache [.NET Framework], time-based policies
- freshness of cached resources
- maximum age policy
- minimum freshness policy
- age of cached resources
ms.assetid: 6567d451-ecec-496c-95a3-a415b99ba52a
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 75729fc92c6a4bfa0f5ad73b8bbd4b28456f21e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a>Interakce zásad do mezipaměti – maximální stáří a minimální aktuálnosti
K zajištění, že nejčerstvější obsah se vrátí do klientské aplikace, výsledkem interakce klienta mezipaměti zásad a server opětovné ověření požadavků vždy nejvíce konzervativní zásady ukládání do mezipaměti. V příkladech v tomto tématu ilustrují zásady ukládání do mezipaměti pro prostředek, který se uloží do mezipaměti na 1. ledna a jeho platnost vyprší v lednu 4.  
  
 Následující příklady ilustrují zásady mezipaměti, která je výsledkem interakci maximální stáří (`maxAge`) a minimální aktuálnosti (`minFresh`) hodnoty.  
  
-   Pokud je nastaví zásady ukládání do mezipaměti `maxAge` = 2 dny a `minFresh` není zadaný obsah je znovu ověřeny na 3.  
  
-   Pokud je nastaví zásady ukládání do mezipaměti `maxAge` = 2 dny a `minFresh` = 1 den, podle `maxAge`, obsah je novou dokud datum 3. Podle `minFresh`, obsah je novou dokud datum 3. Proto musí být znovu obsah ověřeny na 3.  
  
-   Pokud je nastaví zásady ukládání do mezipaměti `maxAge` = 2 dny a `minFresh` = 2 dní, podle `maxAge`, obsah je novou dokud datum 3. Podle `minFresh` dokud leden 2 je novou obsah. Proto musí být znovu obsah ověřeny v lednu 2.  
  
## <a name="see-also"></a>Viz také  
 [Správa mezipaměti pro síťové aplikace](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Zásady mezipaměti](../../../docs/framework/network-programming/cache-policy.md)  
 [Na základě umístění mezipaměti zásad](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [Zásady založené na čase mezipaměti](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [Konfigurace ukládání do mezipaměti v síťových aplikací](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [Interakce zásad do mezipaměti – maximální stáří a maximální typu Prošlostí](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)
