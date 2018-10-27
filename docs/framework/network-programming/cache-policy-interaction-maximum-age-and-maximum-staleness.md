---
title: Interakce zásad mezipaměti – maximální stáří a maximální Neaktuálnost
ms.date: 03/30/2017
helpviewer_keywords:
- maximum staleness
- freshness of cached resources
- time, cached resources
- maximum age policy
- staleness of cached resources
- age of cached resources
ms.assetid: 7f775925-89a1-4956-ba90-c869c1749a94
ms.openlocfilehash: 7a066f403e526c50054b58a099bb7978ef57e74d
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50181144"
---
# <a name="cache-policy-interactionmaximum-age-and-maximum-staleness"></a>Interakce zásad mezipaměti – maximální stáří a maximální Neaktuálnost
K zajištění, že nejčerstvější obsah se vrátí do klientské aplikace, interakce vždy klienta mezipaměti zásad serveru opětovné ověření požadavků a výsledkem nejrestriktivnější zásady ukládání do mezipaměti. Všechny příklady v tomto tématu ilustrují zásady ukládání do mezipaměti pro prostředek, který se uloží do mezipaměti na 1. ledna a končí 4. ledna.  
  
 V následujících příkladech hodnota maximální neaktuálnost (`maxStale`) se používá ve spojení s maximální stáří (`maxAge`):  
  
-   Pokud zásady ukládání do mezipaměti nastaví `maxAge` = 5 dní a nemá `maxStale` hodnoty, podle `maxAge` hodnotu, je obsah použitelné až do ledna 6. Nicméně podle požadavků na opětovné ověření serveru, platnost obsahu vyprší dne od 4. Protože datum vypršení platnosti obsahu je konzervativnější (dřív), má přednost před `maxAge` zásad. Proto obsahu vyprší dne 4 a musí ověřit, i když nedosáhla své maximální stáří.  
  
-   Pokud zásady ukládání do mezipaměti nastaví `maxAge` = 5 dní a `maxStale` = 3 dny, podle `maxAge` hodnotu, je obsah použitelné až do ledna 6. Podle `maxStale` hodnotu, je obsah použitelné až do ledna 7. Proto získá obsah ověřit v lednu 6.  
  
-   Pokud zásady ukládání do mezipaměti nastaví `maxAge` = 5 dní a `maxStale` = 1 den, podle `maxAge` hodnotu, je obsah použitelné až do ledna 6. Podle `maxStale` hodnotu, je obsah použitelné až do ledna 5. Proto získá ověřit obsah na 5. ledna.  
  
 Při maximální stáří je menší než datum vypršení platnosti obsahu, vždycky existuje konzervativnější chování ukládání do mezipaměti a maximální neaktuálnost hodnota nemá žádný vliv. Následující příklady znázorňují účinek nastavení maximální neaktuálnost (`maxStale`) hodnotu v případě maximální stáří (`maxAge`) je dosažen předtím, než vyprší platnost obsahu:  
  
-   Pokud zásady ukládání do mezipaměti nastaví `maxAge` = 1 den a nemá hodnotu `maxStale` hodnotu, obsah je ověřit na 2. ledna i v případě, že nevypršela jeho platnost.  
  
-   Pokud zásady ukládání do mezipaměti nastaví `maxAge` = 1 den a `maxStale` = 3 dny, obsah je ověřit na 2. ledna konzervativnější nastavení zásad vynucovat.  
  
-   Pokud zásady ukládání do mezipaměti nastaví `maxAge` = 1 den a `maxStale` = 1 den, obsah je ověřit na 2. ledna.  
  
## <a name="see-also"></a>Viz také  
 [Správa mezipaměti pro síťové aplikace](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Zásady mezipaměti](../../../docs/framework/network-programming/cache-policy.md)  
 [Zásady mezipaměti na základě místa](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [Zásady mezipaměti na základě času](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [Konfigurace mezipaměti v síťových aplikacích](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [Interakce zásad mezipaměti – minimální stáří a minimální novost](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-minimum-freshness.md)
