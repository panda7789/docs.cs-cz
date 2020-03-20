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
ms.openlocfilehash: 2ec958cc035ac62086cdd3e2844811accc181d47
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048815"
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a>Interakce zásad mezipaměti – minimální stáří a minimální novost
Chcete-li zajistit, že nejčerstvější obsah je vrácena do klientské aplikace, interakce zásad mezipaměti klienta a požadavky na opětovné ověření serveru vždy za následek nejkonzervativnější zásady mezipaměti. Všechny příklady v tomto tématu ilustrují zásady mezipaměti pro prostředek, který je uložen do mezipaměti 1.  
  
 Následující příklady ilustrují zásady mezipaměti, které`maxAge`jsou výsledkem`minFresh`interakce maximálního stáří ( ) a minimální čerstvosti ( ).  
  
- Pokud sady zásad `maxAge` mezipaměti `minFresh` = 2 dny a není zadán, obsah je obnovena na 3.ledna.  
  
- Pokud jsou zásady mezipaměti nastaví `maxAge` = 2 dny a `minFresh` = 1 den, podle `maxAge`, obsah je čerstvé až do 3.ledna. Podle `minFresh`, obsah je čerstvý až do 3.ledna. Proto musí být obsah obnoven a 3.  
  
- Pokud jsou zásady mezipaměti nastaví `maxAge` = 2 dny a `minFresh` = 2 dny, podle `maxAge`, obsah je čerstvé až do 3.ledna. Podle `minFresh` obsahu je čerstvé až do 2.ledna. Proto musí být obsah obnoven a 2.  
  
## <a name="see-also"></a>Viz také

- [Správa mezipaměti pro síťové aplikace](cache-management-for-network-applications.md)
- [Zásady mezipaměti](cache-policy.md)
- [Zásady mezipaměti na základě místa](location-based-cache-policies.md)
- [Zásady mezipaměti na základě času](time-based-cache-policies.md)
- [Konfigurace ukládání do mezipaměti v síťových aplikacích](configuring-caching-in-network-applications.md)
- [Interakce zásad mezipaměti – maximální stáří a maximální neaktuálnost](cache-policy-interaction-maximum-age-and-maximum-staleness.md)
