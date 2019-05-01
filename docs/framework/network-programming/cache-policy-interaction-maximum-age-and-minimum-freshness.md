---
title: Interakce zásad mezipaměti – minimální stáří a minimální novost
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
ms.openlocfilehash: 93136d4c87463db7128a68957b243c1ef13a90eb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62036351"
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a>Interakce zásad mezipaměti – minimální stáří a minimální novost
K zajištění, že nejčerstvější obsah se vrátí do klientské aplikace, interakce vždy klienta mezipaměti zásad serveru opětovné ověření požadavků a výsledkem nejrestriktivnější zásady ukládání do mezipaměti. Všechny příklady v tomto tématu ilustrují zásady ukládání do mezipaměti pro prostředek, který se uloží do mezipaměti na 1. ledna a končí 4. ledna.  
  
 Následující příklady znázorňují zásady ukládání do mezipaměti, která je výsledkem interakce maximální stáří (`maxAge`) a minimální novost (`minFresh`) hodnoty.  
  
- Pokud zásady ukládání do mezipaměti nastaví `maxAge` = 2 dny a `minFresh` není zadaný obsah je ověřit 3. ledna.  
  
- Pokud zásady ukládání do mezipaměti nastaví `maxAge` = 2 dny a `minFresh` = 1 den, podle `maxAge`, až do ledna 3 je nový obsah. Podle `minFresh`, až do ledna 3 je nový obsah. Proto se musí ověřit obsah 3. ledna.  
  
- Pokud zásady ukládání do mezipaměti nastaví `maxAge` = 2 dny a `minFresh` = 2 dny podle `maxAge`, až do ledna 3 je nový obsah. Podle `minFresh` až do ledna 2 je nový obsah. Proto musíte ověřit obsah na 2. ledna.  
  
## <a name="see-also"></a>Viz také:

- [Správa mezipaměti pro síťové aplikace](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [Zásady mezipaměti](../../../docs/framework/network-programming/cache-policy.md)
- [Zásady mezipaměti na základě místa](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [Zásady mezipaměti na základě času](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [Konfigurace mezipaměti v síťových aplikacích](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)
- [Interakce zásad mezipaměti – maximální stáří a maximální neaktuálnost](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)
