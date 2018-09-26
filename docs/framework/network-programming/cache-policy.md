---
title: Zásady mezipaměti
ms.date: 03/30/2017
helpviewer_keywords:
- time-based cache policies
- location-based cache policies
- cache [.NET Framework], policies
- request cache policies
- freshness of cached resources
- content cache policies
- expired content
ms.assetid: 1a7e04ec-7872-41c2-96c6-52566dcb412b
author: mcleblanc
ms.author: markl
ms.openlocfilehash: afaa4389940bd16ee2685c2ed64fbec4626d96e1
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47089906"
---
# <a name="cache-policy"></a>Zásady mezipaměti
Zásady mezipaměti definuje pravidla, která se používají k určení, zda požadavek, je možné splnit pomocí kopie v mezipaměti požadovaný prostředek. Aplikace určit požadavky klienta mezipaměti na aktuálnosti, ale efektivní mezipaměti zásad se určuje podle požadavků mezipaměti klienta, požadavky na vypršení platnosti obsahu serveru a požadavky na opětovné ověření serveru. Interakce požadavky na zásady a server mezipaměti klienta vždy výsledkem nejrestriktivnější zásady ukládání do mezipaměti, abyste zajistili, že nejčerstvější obsah se vrátí do klientské aplikace.  
  
 Zásady mezipaměti jsou založená na poloze nebo založená na čase. Zásady mezipaměti na základě umístění definuje aktuálnosti založené na požadovaný prostředek mohou být odkud položek v mezipaměti. Zásady mezipaměti na základě času definuje aktuálnosti položek v mezipaměti pomocí času, který prostředek se načetla, záhlaví vrátila zdroj a aktuální čas. Většina aplikací můžete použít výchozí zásady mezipaměti na základě času, který implementuje zásady ukládání do mezipaměti, zadané v dokumentu RFC 2616, k dispozici na [ http://www.ietf.org ](http://www.ietf.org/).  
  
 Třídy jsou popsané v následující tabulce se používají k určení mezipaměti zásad.  
  
|Název třídy|Popis|  
|----------------|-----------------|  
|<xref:System.Net.Cache.HttpRequestCachePolicy>|Představuje zásad mezipaměti podle umístění a podle času pro prostředky požadované pomocí <xref:System.Net.HttpWebRequest> objekty.|  
|<xref:System.Net.Cache.RequestCachePolicy>|Představuje zásad mezipaměti na základě umístění nebo <xref:System.Net.Cache.RequestCacheLevel.Default> zásad mezipaměti na základě času pro prostředky požadované pomocí <xref:System.Net.WebRequest> objekty.|  
|<xref:System.Net.Cache.HttpCacheAgeControl>|Určuje hodnoty použité k vytvoření podle času <xref:System.Net.Cache.HttpRequestCachePolicy> objekty.|  
|<xref:System.Net.Cache.HttpRequestCacheLevel>|Určuje hodnoty použité k vytvoření podle umístění a podle času <xref:System.Net.Cache.HttpRequestCachePolicy> objekty.|  
|<xref:System.Net.Cache.RequestCacheLevel>|Určuje hodnoty použité k vytvoření založená na poloze nebo <xref:System.Net.Cache.RequestCacheLevel.Default> podle času <xref:System.Net.Cache.RequestCachePolicy> objekty.|  
  
 Můžete definovat zásady mezipaměti pro všechny požadavky vytvořené v aplikaci nebo pro jednotlivé požadavky. Když zadáte zásady mezipaměti na úrovni aplikace a zásad mezipaměti na úrovni požadavků, se používá žádosti o zásady. Zásady mezipaměti na úrovni aplikace můžete programově nebo prostřednictvím aplikace nebo konfigurační soubory. Další informace najdete v tématu [ \<requestCaching – > – Element (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md).  
  
 Vytvoření mezipaměti zásad, musíte vytvořit objekt zásad tak, že vytvoříte instanci <xref:System.Net.Cache.RequestCachePolicy> nebo <xref:System.Net.Cache.HttpRequestCachePolicy> třídy. Chcete-li zadat zásady na vyžádání, nastavte žádosti <xref:System.Net.WebRequest.CachePolicy%2A> vlastnost na objekt zásady. Při nastavování zásad úrovni aplikace prostřednictvím kódu programu, nastavte <xref:System.Net.HttpWebRequest.DefaultCachePolicy%2A> vlastnost na objekt zásady.  
  
 Příklady kódu, které ukazují, vytváření a používání mezipaměti zásad, najdete v části [konfiguraci ukládání do mezipaměti v síťových aplikacích](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md).  
  
## <a name="see-also"></a>Viz také  
 [Správa mezipaměti pro síťové aplikace](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Zásady mezipaměti na základě místa](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [Zásady mezipaměti na základě času](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [Konfigurace mezipaměti v síťových aplikacích](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)
