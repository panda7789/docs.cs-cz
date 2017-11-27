---
title: "Zásady mezipaměti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time-based cache policies
- location-based cache policies
- cache [.NET Framework], policies
- request cache policies
- freshness of cached resources
- content cache policies
- expired content
ms.assetid: 1a7e04ec-7872-41c2-96c6-52566dcb412b
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 375c3b44f505a9bf36ce721c5ccde9b888114309
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="cache-policy"></a>Zásady mezipaměti
Zásady mezipaměti definuje pravidla, které se používají k určení, zda požadavek můžete splnit pomocí uložené v mezipaměti kopie požadovaný prostředek. Aplikace, zadejte požadavky na mezipaměti klienta pro aktuálnosti, ale zásady efektivní mezipaměti je určen podle požadavků mezipaměti klienta, serveru vypršení platnosti obsahu požadavky a požadavky na opětovné ověření serveru. Požadavky na zásady a server mezipaměti klienta interakci vždy výsledkem nejvíce konzervativní zásady ukládání do mezipaměti, aby bylo zajištěno, že nejčerstvější obsah se vrátí do klientské aplikace.  
  
 Zásady mezipaměti jsou buď na základě umístění nebo založené na čase. Zásady na základě umístění mezipaměti definuje aktuálnosti položek v mezipaměti založené na požadovaný prostředek mohou odkud. Zásady založené na čase mezipaměti definuje aktuálnosti položek v mezipaměti pomocí době, kdy byla načtena prostředku, vrátí hlavičky s prostředek a aktuální čas. Většina aplikací můžete použít výchozí časové zásady ukládání do mezipaměti, která implementuje zásady ukládání do mezipaměti, zadané v dokumentu RFC 2616, k dispozici na [http://www.ietf.org](http://www.ietf.org/).  
  
 Třídy popsané v následující tabulce se používají k určení zásady mezipaměti.  
  
|Název třídy|Popis|  
|----------------|-----------------|  
|<xref:System.Net.Cache.HttpRequestCachePolicy>|Představuje zásady na základě polohy a založené na čase mezipaměti pro prostředky požadováno pomocí <xref:System.Net.HttpWebRequest> objekty.|  
|<xref:System.Net.Cache.RequestCachePolicy>|Představuje zásady na základě umístění mezipaměti nebo <xref:System.Net.Cache.RequestCacheLevel.Default> zásady založené na čase mezipaměti pro prostředky požadováno pomocí <xref:System.Net.WebRequest> objekty.|  
|<xref:System.Net.Cache.HttpCacheAgeControl>|Určuje hodnoty použité k vytvoření založené na čase <xref:System.Net.Cache.HttpRequestCachePolicy> objekty.|  
|<xref:System.Net.Cache.HttpRequestCacheLevel>|Určuje hodnoty použité k vytvoření na základě polohy a založené na čase <xref:System.Net.Cache.HttpRequestCachePolicy> objekty.|  
|<xref:System.Net.Cache.RequestCacheLevel>|Určuje hodnoty použité k vytvoření, na základě polohy nebo <xref:System.Net.Cache.RequestCacheLevel.Default> založené na čase <xref:System.Net.Cache.RequestCachePolicy> objekty.|  
  
 Můžete definovat zásady mezipaměti pro všechny požadavky vytvořené v aplikaci nebo pro jednotlivé požadavky. Když zadáte zásadu mezipaměti na úrovni aplikace a zásady úrovni požadavků mezipaměti, zásada úrovni požadavků se používá. Můžete zadat zásady úrovni aplikace mezipaměti prostřednictvím kódu programu, nebo pomocí aplikace nebo počítač – konfigurační soubory. Další informace najdete v tématu [ \<requestCaching – > elementu (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md).  
  
 Pokud chcete vytvořit zásadu mezipaměti, musíte vytvořit objekt zásad tak, že vytvoříte instanci <xref:System.Net.Cache.RequestCachePolicy> nebo <xref:System.Net.Cache.HttpRequestCachePolicy> třídy. Určení zásad na vyžádání, nastavení žádosti <xref:System.Net.WebRequest.CachePolicy%2A> vlastnost u objektu zásad. Při nastavení zásad úrovni aplikace prostřednictvím kódu programu, nastavte <xref:System.Net.HttpWebRequest.DefaultCachePolicy%2A> vlastnost u objektu zásad.  
  
 Příklady kódu, které ukazují, vytvoření a použití zásady mezipaměti najdete v tématu [konfiguraci ukládání do mezipaměti v síťových aplikací](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md).  
  
## <a name="see-also"></a>Viz také  
 [Správa mezipaměti pro síťové aplikace](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Na základě umístění mezipaměti zásad](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [Zásady založené na čase mezipaměti](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [Konfigurace ukládání do mezipaměti v síťových aplikací](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)
