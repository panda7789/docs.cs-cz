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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048843"
---
# <a name="cache-policy-interactionmaximum-age-and-maximum-staleness"></a>Interakce zásad mezipaměti – maximální stáří a maximální neaktuálnost
Chcete-li zajistit, že nejčerstvější obsah je vrácena do klientské aplikace, interakce zásad mezipaměti klienta a požadavky na opětovné ověření serveru vždy za následek nejkonzervativnější zásady mezipaměti. Všechny příklady v tomto tématu ilustrují zásady mezipaměti pro prostředek, který je uložen do mezipaměti 1.  
  
 V následujících příkladech se používá maximální`maxStale`hodnota neaktuálnosti (`maxAge`) ve spojení s maximálním věkem ( ):  
  
- Pokud sada zásad `maxAge` mezipaměti = 5 `maxStale` dní a neurčuje hodnotu, podle `maxAge` hodnoty je obsah použitelný až do 6. Podle požadavků serveru na prodloužení platnosti však platnost obsahu vyprší 4. Vzhledem k tomu, že datum vypršení platnosti `maxAge` obsahu je konzervativnější (dříve), má přednost před zásadou. Obsah proto vyprší 4.  
  
- Pokud jsou zásady mezipaměti nastaví `maxAge` = 5 dní a `maxStale` = 3 dny, podle `maxAge` hodnoty, obsah je použitelný až do 6. Podle `maxStale` hodnoty je obsah použitelný až do 7. Proto bude obsah obnoven 6.  
  
- Pokud jsou zásady mezipaměti nastaví `maxAge` = 5 dní a `maxStale` = 1 den, podle `maxAge` hodnoty, obsah je použitelný až do 6. Podle `maxStale` hodnoty je obsah použitelný až do 5. Proto bude obsah obnoven 5.  
  
 Pokud je maximální stáří menší než datum vypršení platnosti obsahu, vždy převládá konzervativnější chování ukládání do mezipaměti a maximální hodnota neaktuálnosti nemá žádný vliv. Následující příklady ilustrují účinek nastavení`maxStale`maximální hodnoty neaktuálnosti ( ) při dosažení maximálního stáří (`maxAge`) před vypršením platnosti obsahu:  
  
- Pokud zásady `maxAge` mezipaměti nastaví = 1 `maxStale` den a neurčuje hodnotu pro hodnotu, obsah je obnovena na 2 ledna, i když jeho platnost nevypršela.  
  
- Pokud sady zásad `maxAge` mezipaměti `maxStale` = 1 den a = 3 dny, obsah je obnovena na 2 ledna vynutit konzervativnější nastavení zásad.  
  
- Pokud sady zásad `maxAge` mezipaměti `maxStale` = 1 den a = 1 den, obsah je obnovena na 2 ledna.  
  
## <a name="see-also"></a>Viz také

- [Správa mezipaměti pro síťové aplikace](cache-management-for-network-applications.md)
- [Zásady mezipaměti](cache-policy.md)
- [Zásady mezipaměti na základě místa](location-based-cache-policies.md)
- [Zásady mezipaměti na základě času](time-based-cache-policies.md)
- [Konfigurace ukládání do mezipaměti v síťových aplikacích](configuring-caching-in-network-applications.md)
- [Interakce zásad mezipaměti – minimální stáří a minimální novost](cache-policy-interaction-maximum-age-and-minimum-freshness.md)
