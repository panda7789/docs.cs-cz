---
title: "Na základě umístění mezipaměti zásad"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 7a1be9f377f9b241bf46ac67f4f3f08fc5a43821
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="location-based-cache-policies"></a>Na základě umístění mezipaměti zásad
Zásady na základě umístění mezipaměti definuje aktuálnosti platné položky v mezipaměti založené na požadovaný prostředek mohou odkud. Prostředek v mezipaměti je platný Pokud použití nemá není porušují požadavky na zadaný server opětovné ověření. Na základě umístění mezipaměti není vytvořená zásada, programově pomocí <xref:System.Net.Cache.RequestCachePolicy> nebo <xref:System.Net.Cache.HttpRequestCachePolicy> konstruktoru třídy. Typ zásady na základě polohy předaný konstruktoru pomocí <xref:System.Net.Cache.RequestCacheLevel> nebo <xref:System.Net.Cache.HttpRequestCacheLevel> hodnota výčtu. Příklady kódu, které vytvářejí na základě umístění mezipaměti zásady, najdete v části [postupy: nastavení zásady na základě umístění mezipaměti pro aplikaci](../../../docs/framework/network-programming/how-to-set-a-location-based-cache-policy-for-an-application.md). Následující části popisují jednotlivé typy zásad na základě umístění mezipaměti pro protokol HTTP (http a https) prostředky.  
  
## <a name="cache-if-available-policy"></a>Pokud je k dispozici do mezipaměti zásad  
 Pokud platný požadovaný prostředek je v místní mezipaměti, se používá v mezipaměti prostředků; žádost pro daný prostředek, jinak hodnota je odeslána na server. Pokud požadovaný prostředek k dispozici ve všech mezipaměti mezi klientem a serverem, požadavek můžete splnit zprostředkující mezipaměti.  
  
## <a name="cache-only-policy"></a>Pouze zásady mezipaměti  
 Pokud platný požadovaný prostředek je v místní mezipaměti, použije se v mezipaměti prostředků. Pokud je zadána tato úroveň zásady mezipaměti, <xref:System.Net.WebException> je vyvolána výjimka, pokud položka není v místní mezipaměti.  
  
## <a name="cache-or-next-cache-only-policy"></a>Ukládat do mezipaměti nebo další mezipaměti pouze zásady  
 Pokud platný požadovaný prostředek je v místní mezipaměti nebo zprostředkující mezipaměti v místní síti, se používá v mezipaměti prostředků. V opačném <xref:System.Net.WebException> je vyvolána výjimka. V ukládání do mezipaměti protokolu HTTP můžete toho dosáhnout pomocí direktiva ovládací prvek mezipaměti jen v případě mezipaměti.  
  
## <a name="no-cache-no-store-policy"></a>Žádné mezipaměti bez uložení zásady  
 Požadovaný prostředek se nikdy nepoužívá z jakékoli mezipaměti a nikdy je umístěn v jakékoli mezipaměti. Pokud požadovaný zdroj je k dispozici v místní mezipaměti, bude odebrán. Tato úroveň zásad označuje zprostředkující mezipamětí, že se mělo odstranit také prostředku. V ukládání do mezipaměti protokolu HTTP můžete toho dosáhnout pomocí direktiva ovládací prvek mezipaměti žádné úložiště.  
  
## <a name="refresh-policy"></a>Aktualizovat zásady  
 Požadovaný prostředek lze použít, je-li získat ze serveru nebo nalezených v mezipaměti než místní mezipaměti. Předtím, než požadavek můžete splnit zprostředkující mezipaměti, musí mezipaměť znovu ověřit jeho položka uložená v mezipaměti se serverem. V ukládání do mezipaměti protokolu HTTP, to je dosaženo pomocí maximální stáří = 0 mezipaměti ovládacího prvku směrnice a hlavičku – direktiva Pragma bez mezipaměti.  
  
## <a name="reload-policy"></a>Znovu načíst zásady  
 Požadované prostředky musí získat ze serveru. Odpověď je uložen v místní mezipaměti. V ukládání do mezipaměti protokolu HTTP můžete toho dosáhnout pomocí direktiva ovládací prvek mezipaměti ne mezipaměť a hlavičku – direktiva Pragma bez mezipaměti.  
  
## <a name="revalidate-policy"></a>Znovu ověřit zásad  
 Porovná kopie prostředku v mezipaměti s kopií na serveru. Pokud je kopie na serveru novější, se používá ke zpracování požadavku a nahradí kopie v mezipaměti. Pokud je kopie v mezipaměti stejná jako kopii na serveru, se používá kopie uložené v mezipaměti. V ukládání do mezipaměti protokolu HTTP můžete toho dosáhnout pomocí podmíněného žádosti.  
  
## <a name="see-also"></a>Viz také  
 [Správa mezipaměti pro síťové aplikace](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Zásady mezipaměti](../../../docs/framework/network-programming/cache-policy.md)  
 [Zásady založené na čase mezipaměti](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [Konfigurace ukládání do mezipaměti v síťových aplikací](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [\<requestCaching – > elementu (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
