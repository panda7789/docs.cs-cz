---
title: Interakce zásad mezipaměti – maximální stáří a maximální neaktuálnost
ms.date: 03/30/2017
helpviewer_keywords:
- maximum staleness
- freshness of cached resources
- time, cached resources
- maximum age policy
- staleness of cached resources
- age of cached resources
ms.assetid: 7f775925-89a1-4956-ba90-c869c1749a94
ms.openlocfilehash: e21cfc28407ba67afdce8d72e5e52c12ab359059
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048843"
---
# <a name="cache-policy-interactionmaximum-age-and-maximum-staleness"></a>Interakce zásad mezipaměti – maximální stáří a maximální neaktuálnost
Aby bylo zajištěno, že se obsah vrátí do klientské aplikace, interakce zásad mezipaměti klienta a požadavky na revalidy serveru vždy vede k nejzávažnějším zásadám mezipaměti. Všechny příklady v tomto tématu ilustrují zásady mezipaměti pro prostředek, který je uložen v mezipaměti od 1. ledna do 4. ledna.  
  
 V následujících příkladech je maximální hodnota neaktuálnosti (`maxStale`) použita ve spojení s maximálním stářím (`maxAge`):  
  
- Pokud zásada cache nastaví `maxAge` = 5 dní a `maxStale` neurčuje `maxAge` hodnotu podle hodnoty, bude obsah použitelný až do 6. ledna. V souladu s požadavky na revalidy serveru ale platnost obsahu vyprší 4. ledna. Vzhledem k tomu, že datum vypršení platnosti obsahu je více konzervativní (dřív), `maxAge` má přednost před zásadou. Platnost obsahu proto vyprší 4. ledna a musí se znovu ověřit, i když jeho maximální stáří nebylo dosaženo.  
  
- Pokud zásady mezipaměti nastaví `maxAge` = 5 dní a `maxStale` = 3 `maxAge` dny, podle hodnoty, bude obsah použitelný až do 6. ledna. `maxStale` Podle hodnoty je možné obsah použít až do 7. ledna. Proto se obsah znovu ověří 6. ledna.  
  
- Pokud zásady mezipaměti nastaví `maxAge` = 5 dní a `maxStale` = 1 `maxAge` den, podle hodnoty, bude obsah použitelný až do 6. ledna. `maxStale` Podle hodnoty je možné obsah použít do 5. ledna. Proto se obsah znovu ověří 5. ledna.  
  
 Pokud je maximální stáří menší než datum vypršení platnosti obsahu, podrobnější chování při ukládání do mezipaměti je vždycky stejné a maximální hodnota zastaralosti nemá žádný vliv. Následující příklady ilustrují efekt nastavení maximální hodnoty neaktuálnosti (`maxStale`), pokud je dosaženo maximálního stáří (`maxAge`), než vyprší platnost obsahu:  
  
- Pokud zásady mezipaměti nastaví `maxAge` 1 den a neurčuje hodnotu pro `maxStale` hodnotu, bude se obsah znovu ověřit 2. ledna, i když nevypršela jeho platnost.  
  
- Pokud zásady mezipaměti nastaví `maxAge` hodnotu 1 den a `maxStale` = 3 dny, dojde k jejímu ověření znovu v lednu 2, aby se vynutilo více konzervativních zásad.  
  
- Pokud jsou zásady mezipaměti nastaveny `maxAge` na 1 den a `maxStale` = 1 den, obsah se znovu ověří 2. ledna.  
  
## <a name="see-also"></a>Viz také:

- [Správa mezipaměti pro síťové aplikace](cache-management-for-network-applications.md)
- [Zásady mezipaměti](cache-policy.md)
- [Zásady mezipaměti na základě místa](location-based-cache-policies.md)
- [Zásady mezipaměti na základě času](time-based-cache-policies.md)
- [Konfigurace mezipaměti v síťových aplikacích](configuring-caching-in-network-applications.md)
- [Interakce zásad mezipaměti – minimální stáří a minimální novost](cache-policy-interaction-maximum-age-and-minimum-freshness.md)
