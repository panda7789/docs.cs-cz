---
title: Zásady mezipaměti na základě umístění
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
ms.openlocfilehash: e6896452fce89f69b40f1d03332355df72d93211
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047667"
---
# <a name="location-based-cache-policies"></a>Zásady mezipaměti na základě umístění
Zásada mezipaměti založená na umístění definuje čerstvost platných položek uložených v mezipaměti na základě toho, odkud lze požadovaný prostředek odebrat. Prostředek uložený v mezipaměti je platný, pokud jeho použití neporušuje požadavky na opětovné ověření zadané serverem. Zásady mezipaměti založené na umístění se <xref:System.Net.Cache.RequestCachePolicy> vytvářejí <xref:System.Net.Cache.HttpRequestCachePolicy> programově pomocí konstruktoru třídy nebo třídy. Typ zásady založené na umístění je předán <xref:System.Net.Cache.RequestCacheLevel> konstruktoru pomocí hodnoty nebo <xref:System.Net.Cache.HttpRequestCacheLevel> výčtu. Příklady kódu, které vytvářejí zásady mezipaměti založené na umístění, naleznete v [tématu Postup: Nastavení zásad mezipaměti založené na poloze pro aplikaci](how-to-set-a-location-based-cache-policy-for-an-application.md). Následující části vysvětlují každý typ zásad mezipaměti založených na umístění pro prostředky protokolu HTTP a https (HTTP a https).  
  
## <a name="cache-if-available-policy"></a>Mezipaměť, pokud jsou k dispozici zásady  
 Pokud je platný požadovaný prostředek v místní mezipaměti, použije se prostředek uložený v mezipaměti. v opačném případě je požadavek na prostředek odeslán na server. Pokud je požadovaný prostředek k dispozici v libovolné mezipaměti mezi klientem a serverem, může být požadavek splněn mezilehlou mezipamětí.  
  
## <a name="cache-only-policy"></a>Zásady pouze pro ukládání do mezipaměti  
 Pokud je platný požadovaný prostředek v místní mezipaměti, použije se prostředek uložený v mezipaměti. Pokud je zadána tato <xref:System.Net.WebException> úroveň zásad mezipaměti, je vyvolána výjimka, pokud položka není v místní mezipaměti.  
  
## <a name="cache-or-next-cache-only-policy"></a>Zásady pouze pro ukládání do mezipaměti nebo další mezipaměti  
 Pokud je platný požadovaný prostředek v místní mezipaměti nebo v mezipaměť v místní síti, použije se prostředek uložený v mezipaměti. V opačném <xref:System.Net.WebException> případě je vyvolána výjimka. V protokolu ukládání do mezipaměti HTTP je toho dosaženo pomocí direktivy řízení mezipaměti pouze v případě mezipaměti.  
  
## <a name="no-cache-no-store-policy"></a>Žádné zásady mezipaměti bez úložiště  
 Požadovaný prostředek se nikdy nepoužívá z žádné mezipaměti a nikdy není umístěn v žádné mezipaměti. Pokud je požadovaný prostředek přítomen v místní mezipaměti, je odebrán. Tato úroveň zásad označuje zprostředkující mezipaměti, které by měly také odebrat prostředek. V protokolu ukládání do mezipaměti HTTP je toho dosaženo pomocí direktivy řízení mezipaměti bez úložiště.  
  
## <a name="refresh-policy"></a>Aktualizovat zásady  
 Požadovaný prostředek lze použít, pokud je získán ze serveru nebo nalezen v jiné mezipaměti než v místní mezipaměti. Předtím, než může být požadavek splněn mezilehlou mezipamětí, musí tato mezipaměť znovu ověřit položku uloženou v mezipaměti se serverem. V protokolu ukládání do mezipaměti HTTP je toho dosaženo pomocí směrnice řízení mezipaměti max-age = 0 a hlavičky Pragma bez mezipaměti.  
  
## <a name="reload-policy"></a>Zásady opětovného načtení  
 Požadované prostředky musí být získány ze serveru. Odpověď může být uložena v místní mezipaměti. V protokolu ukládání do mezipaměti HTTP je toho dosaženo pomocí direktivy řízení mezipaměti bez mezipaměti a hlavičky Pragma bez mezipaměti.  
  
## <a name="revalidate-policy"></a>Znovu ověřit zásady  
 Porovná kopii prostředku v mezipaměti s kopií na serveru. Pokud je kopie na serveru novější, slouží k uspokojení požadavku a nahradí kopii v mezipaměti. Pokud je kopie v mezipaměti stejná jako kopie serveru, použije se kopie uložená v mezipaměti. V protokolu ukládání do mezipaměti HTTP je toho dosaženo pomocí podmíněného požadavku.  
  
## <a name="see-also"></a>Viz také

- [Správa mezipaměti pro síťové aplikace](cache-management-for-network-applications.md)
- [Zásady mezipaměti](cache-policy.md)
- [Zásady mezipaměti na základě času](time-based-cache-policies.md)
- [Konfigurace ukládání do mezipaměti v síťových aplikacích](configuring-caching-in-network-applications.md)
- [\<requestCaching> Element (Nastavení sítě)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
