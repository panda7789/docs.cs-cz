---
title: Interakce zásad do mezipaměti – maximální stáří a minimální aktuálnosti
ms.date: 03/30/2017
helpviewer_keywords:
- time-based cache policies
- Revalidate policy
- cache [.NET Framework], time-based policies
- freshness of cached resources
- maximum age policy
- minimum freshness policy
- age of cached resources
ms.assetid: 6567d451-ecec-496c-95a3-a415b99ba52a
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d88ef1e736a16dddf156a1bc0e42f06d128d2c57
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394163"
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
 [Zásady mezipaměti na základě místa](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [Zásady mezipaměti na základě času](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [Konfigurace mezipaměti v síťových aplikacích](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [Interakce zásad mezipaměti – maximální stáří a maximální neaktuálnost](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)
