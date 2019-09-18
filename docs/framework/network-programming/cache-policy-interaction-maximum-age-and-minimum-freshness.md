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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048815"
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a>Interakce zásad mezipaměti – minimální stáří a minimální novost
Aby bylo zajištěno, že se obsah vrátí do klientské aplikace, interakce zásad mezipaměti klienta a požadavky na revalidy serveru vždy vede k nejzávažnějším zásadám mezipaměti. Všechny příklady v tomto tématu ilustrují zásady mezipaměti pro prostředek, který je uložen v mezipaměti od 1. ledna do 4. ledna.  
  
 Následující příklady ilustrují zásady mezipaměti, které jsou výsledkem interakce s maximálním stářím (`maxAge`) a minimálními hodnotami aktuálnosti (`minFresh`).  
  
- Pokud zásada cache nastaví `maxAge` hodnotu = 2 dny a `minFresh` není zadána, bude obnovena platnost obsahu 3. ledna.  
  
- Pokud zásady mezipaměti nastaví `maxAge` = 2 dny a `minFresh` = `maxAge`1 den, podle toho, bude obsah až do 3. ledna. `minFresh`Podle toho je obsah až do 3. ledna v čerstvém stavu. Proto se obsah musí znovu ověřit 3. ledna.  
  
- Pokud zásady mezipaměti nastaví `maxAge` hodnotu = 2 dny a `minFresh` = 2 dny, je obsah v závislosti na `maxAge`začátku až do 3. ledna. `minFresh` Podle obsahu je až do 2. ledna. Proto se obsah musí znovu ověřit 2. ledna.  
  
## <a name="see-also"></a>Viz také:

- [Správa mezipaměti pro síťové aplikace](cache-management-for-network-applications.md)
- [Zásady mezipaměti](cache-policy.md)
- [Zásady mezipaměti na základě místa](location-based-cache-policies.md)
- [Zásady mezipaměti na základě času](time-based-cache-policies.md)
- [Konfigurace mezipaměti v síťových aplikacích](configuring-caching-in-network-applications.md)
- [Interakce zásad mezipaměti – maximální stáří a maximální neaktuálnost](cache-policy-interaction-maximum-age-and-maximum-staleness.md)
