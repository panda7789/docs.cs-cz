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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047667"
---
# <a name="location-based-cache-policies"></a>Zásady mezipaměti na základě umístění
Zásady mezipaměti založené na umístění definují aktuálnost platných položek v mezipaměti podle toho, kde se dá požadovaný prostředek považovat. Prostředek v mezipaměti je platný, pokud ho používáte, není v rozporu s požadavky na revalidy zadané serverem. Zásady mezipaměti založené na umístění se vytvářejí programově pomocí <xref:System.Net.Cache.RequestCachePolicy> konstruktoru třídy nebo. <xref:System.Net.Cache.HttpRequestCachePolicy> Typ zásady na základě umístění je předán konstruktoru pomocí <xref:System.Net.Cache.RequestCacheLevel> hodnoty nebo <xref:System.Net.Cache.HttpRequestCacheLevel> výčtu. Příklady kódu, které vytvářejí zásady mezipaměti na základě umístění, naleznete [v tématu How to: Nastavte zásady mezipaměti na základě umístění pro aplikaci](how-to-set-a-location-based-cache-policy-for-an-application.md). Následující části popisují jednotlivé typy zásad mezipaměti založené na umístění pro prostředky http a HTTPS (Hypertext Transfer Protocol).  
  
## <a name="cache-if-available-policy"></a>Ukládat do mezipaměti, pokud jsou k dispozici zásady  
 Pokud je platný požadovaný prostředek v místní mezipaměti, použije se prostředek uložený v mezipaměti. v opačném případě se požadavek na prostředek pošle na server. Pokud je požadovaný prostředek k dispozici v jakékoli mezipaměti mezi klientem a serverem, může být žádost splněna mezipamětí.  
  
## <a name="cache-only-policy"></a>Zásada pouze pro ukládání do mezipaměti  
 Pokud je platný požadovaný prostředek v místní mezipaměti, bude použit prostředek uložený v mezipaměti. Je- <xref:System.Net.WebException> li tato úroveň zásad mezipaměti zadána, je vyvolána výjimka, pokud položka není v místní mezipaměti.  
  
## <a name="cache-or-next-cache-only-policy"></a>Zásada cache nebo Next cache Only  
 Pokud je platný požadovaný prostředek v místní mezipaměti nebo mezilehlá mezipaměť v místní síti, použije se prostředek uložený v mezipaměti. V opačném případě je vyvolána výjimka.<xref:System.Net.WebException> V protokolu HTTP cache je to dosaženo pomocí direktivy řízení mezipaměti pouze if-cache.  
  
## <a name="no-cache-no-store-policy"></a>Žádná zásada úložiště bez mezipaměti  
 Požadovaný prostředek se nikdy nepoužije z žádné mezipaměti a nikdy se neuloží do žádné mezipaměti. Pokud se požadovaný prostředek nachází v místní mezipaměti, odebere se. Tato úroveň zásady označuje mezipamětí, které by měly také odebrat prostředek. V protokolu HTTP cache je to dosaženo pomocí direktivy řízení mezipaměti No-Store.  
  
## <a name="refresh-policy"></a>Aktualizovat zásady  
 Požadovaný prostředek se dá použít, pokud je získaný ze serveru nebo se nachází v jiné mezipaměti než v místní mezipaměti. Aby bylo možné požadavek vyhovět mezilehlou mezipamětí, musí tato mezipaměť znovu ověřit položku uloženou v mezipaměti se serverem. V protokolu HTTP cache se dá dosáhnout pomocí direktivy řízení mezipaměti max-age = 0 a hlavičky pragma no-cache.  
  
## <a name="reload-policy"></a>Znovu načíst zásadu  
 Ze serveru se musí získat požadované prostředky. Odpověď může být uložena v místní mezipaměti. V protokolu HTTP cache se dá dosáhnout pomocí direktivy řízení mezipaměti no-cache a hlavičky pragma no-cache.  
  
## <a name="revalidate-policy"></a>Znovu ověřit zásadu  
 Porovná kopii prostředku v mezipaměti s kopií na serveru. Pokud je kopie na serveru novější, slouží k uspokojení žádosti a k nahrazení kopie v mezipaměti. Pokud je kopie v mezipaměti stejná jako kopie serveru, je použita kopie uložená v mezipaměti. V protokolu HTTP Caching se to dosáhne pomocí podmíněného požadavku.  
  
## <a name="see-also"></a>Viz také:

- [Správa mezipaměti pro síťové aplikace](cache-management-for-network-applications.md)
- [Zásady mezipaměti](cache-policy.md)
- [Zásady mezipaměti na základě času](time-based-cache-policies.md)
- [Konfigurace mezipaměti v síťových aplikacích](configuring-caching-in-network-applications.md)
- [\<requestCaching – element > (nastavení sítě)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
