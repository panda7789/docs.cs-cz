---
title: Zásady mezipaměti na základě polohy
ms.date: 03/30/2017
helpviewer_keywords:
- Cache If Available policy
- reload policy
- location-based cache policies
- Cache Only policy
- local cache
- intermediate cache
- No Cache No Store policy
- cache [.NET Framework], location-based policies
- Revalidate policy
- freshness of cached resources
- Cache Or Next Cache Only policy
- Refresh policy
ms.assetid: e41d7f1a-0a6a-4dee-97d1-c6a8b6a07fc2
ms.openlocfilehash: 1bbaf4fc85fe4d7e3d3737cf62cb63d8e09927cd
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194407"
---
# <a name="location-based-cache-policies"></a>Zásady mezipaměti na základě polohy
Zásady mezipaměti na základě umístění definují aktuálnosti platné položky uložené v mezipaměti založené na požadovaný prostředek mohou být odkud. Prostředek v mezipaměti je platný pokud jeho použití není porušovat požadavky na zadaný server opětovné ověření. Zásady mezipaměti na základě umístění je vytvořená prostřednictvím kódu programu pomocí <xref:System.Net.Cache.RequestCachePolicy> nebo <xref:System.Net.Cache.HttpRequestCachePolicy> konstruktoru třídy. Je předán typ zásady založená na poloze pomocí konstruktoru <xref:System.Net.Cache.RequestCacheLevel> nebo <xref:System.Net.Cache.HttpRequestCacheLevel> hodnota výčtu. Příklady kódu, které vytvářejí zásady mezipaměti na základě polohy, naleznete v tématu [postupy: nastavení zásad mezipaměti na základě umístění pro aplikaci](../../../docs/framework/network-programming/how-to-set-a-location-based-cache-policy-for-an-application.md). Následující části popisují jednotlivé typy zásad mezipaměti na základě umístění pro prostředky protokol HTTP (http a https).  
  
## <a name="cache-if-available-policy"></a>Pokud je k dispozici do mezipaměti zásad  
 Pokud platné požadovaný prostředek je v místní mezipaměti, se používá v mezipaměti prostředků; v opačném případě je vyslána žádost pro prostředek serveru. Pokud požadovaný prostředek je k dispozici v libovolné mezipaměti mezi klientem a serverem, je možné splnit žádost zprostředkující mezipaměti.  
  
## <a name="cache-only-policy"></a>Pouze zásady mezipaměti  
 Pokud platné požadovaný prostředek je v místní mezipaměti, se používá v mezipaměti prostředků. Pokud je zadána tato úroveň zásad mezipaměti, <xref:System.Net.WebException> je vyvolána výjimka, pokud položka se nenachází v místní mezipaměti.  
  
## <a name="cache-or-next-cache-only-policy"></a>Ukládat do mezipaměti nebo další mezipaměti pouze zásady  
 Pokud platné požadovaný prostředek je v místní mezipaměti nebo zprostředkující mezipaměti v místní síti, se používá v mezipaměti prostředků. V opačném případě <xref:System.Net.WebException> je vyvolána výjimka. Ukládání do mezipaměti protokolu HTTP toho můžete dosáhnout použitím direktivy ovládací prvek mezipaměti pouze if-do mezipaměti.  
  
## <a name="no-cache-no-store-policy"></a>Žádná mezipaměť ne Store zásad  
 Požadovaný prostředek se nikdy nepoužívá žádné mezipaměti a je umístěn všechny mezipaměti. Pokud požadovaný prostředek je k dispozici v místní mezipaměti, bude odebrán. Tato úroveň zásad označuje zprostředkující mezipamětí, že se mělo odstranit také na prostředek. Ukládání do mezipaměti protokolu HTTP toho můžete dosáhnout použitím direktivy no-store mezipaměti ovládacího prvku.  
  
## <a name="refresh-policy"></a>Aktualizovat zásady  
 Požadovaný prostředek je možné, je-li získat ze serveru nebo nalezených v mezipaměti, než v místní mezipaměti. Předtím, než je možné splnit žádost zprostředkující mezipaměti, musí tuto mezipaměť znovu ověřit jeho položka uložená v mezipaměti se serverem. Ukládání do mezipaměti protokolu HTTP, toho můžete dosáhnout použitím max-age = 0 mezipaměti ovládacího prvku směrnice a záhlaví – direktiva Pragma no-cache.  
  
## <a name="reload-policy"></a>Znovu načíst zásady  
 Požadované prostředky se musí získat od serveru. Odpověď může být uložen v místní mezipaměti. Ukládání do mezipaměti protokolu HTTP toho můžete dosáhnout použitím direktivy no-cache mezipaměti ovládacího prvku a záhlaví – direktiva Pragma no-cache.  
  
## <a name="revalidate-policy"></a>Znovu ověřit zásady  
 Porovná kopie prostředku v mezipaměti s kopií na serveru. Pokud je novější kopie na serveru, se používá ke zpracování požadavku a nahradí kopii v mezipaměti. Pokud je kopie v mezipaměti je stejný jako kopii na serveru, použije se kopie v mezipaměti. Ukládání do mezipaměti protokolu HTTP toho můžete dosáhnout použitím Podmíněný požadavek.  
  
## <a name="see-also"></a>Viz také  
 [Správa mezipaměti pro síťové aplikace](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Zásady mezipaměti](../../../docs/framework/network-programming/cache-policy.md)  
 [Zásady mezipaměti na základě času](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [Konfigurace mezipaměti v síťových aplikacích](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [\<requestCaching – > – Element (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
