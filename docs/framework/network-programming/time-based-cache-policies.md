---
title: Zásady založené na čase mezipaměti
ms.date: 03/30/2017
helpviewer_keywords:
- time-based cache policies
- cache synchronization date policy
- cache [.NET Framework], time-based policies
- freshness of cached resources
- time, cached resources
- maximum age policy
- synchronization, cache
- staleness of cached resources
- default time-based cache policy
- maximum staleness policy
- content cache policies
- expired content
- minimum freshness policy
- age of cached resources
ms.assetid: 74f0bcaf-5c95-40c1-9967-f3bbf1d2360a
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f25f04a144fa806297b018bf3548b8feb506f67d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392548"
---
# <a name="time-based-cache-policies"></a>Zásady založené na čase mezipaměti
Zásady založené na čase mezipaměti definuje aktuálnosti položek v mezipaměti pomocí čas prostředku byl načteny, se k prostředku, vrácený hlavičky a aktuální čas. Při nastavení zásad založené na čase mezipaměti, můžete použít <xref:System.Net.Cache.HttpRequestCacheLevel.Default> zásady založené na čase nebo vytvořte vlastní zásadu založené na čase. Při použití výchozí zásady založené na čase prostředků získaných pomocí protokolu HTTP (Hypertext Transfer), přesný mezipaměti chování je určen podle hlavičky zahrnuty v odpovědi v mezipaměti a chování zadané v části 13 a 14 dokumentu RFC 2616 k dispozici na [ http://www.ietf.org ](http://www.ietf.org/). Příklad kódu, který ukazuje nastavení zásad založené na čase výchozí pro HTTP prostředky, najdete v části [postupy: nastavení zásady ukládání do mezipaměti Default Time-Based pro aplikaci](../../../docs/framework/network-programming/how-to-set-the-default-time-based-cache-policy-for-an-application.md). Příklady kódu, které ukazují, vytvoření a použití zásady mezipaměti najdete v tématu [konfiguraci ukládání do mezipaměti v síťových aplikací](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md).  
  
## <a name="criteria-to-determine-freshness-of-cached-entries"></a>Kritéria k určení aktuálnosti položek v mezipaměti  
 Chcete-li přizpůsobit zásady založené na čase mezipaměti, můžete určit, že jedna nebo více z následujících kritérií použije k určení aktuálnosti položek v mezipaměti:  
  
-   Maximální stáří  
  
-   Maximální typu prošlostí  
  
-   Minimální aktuálnosti  
  
-   Datum synchronizace mezipaměti  
  
> [!NOTE]
>  Pomocí zásady ukládání do mezipaměti založené na čase výchozí Nezaměňujte za nastavení výchozí zásady mezipaměti pro vaši aplikaci. Výchozí zásady založené na čase je konkrétní zásadu, která lze použít na úrovni požadavku nebo aplikace. Výchozí zásady mezipaměti pro vaši aplikaci je zásada (na základě polohy nebo založené na čase), která se projeví při žádná zásada nastavená na vyžádání. Podrobnosti o nastavení výchozí zásady mezipaměti pro vaši aplikaci najdete v tématu <xref:System.Net.WebRequest.DefaultCachePolicy%2A>.  
  
### <a name="maximum-age"></a>Maximální stáří  
 Maximální stáří zásad kritérium určuje množství času, které lze použít v mezipaměti kopie prostředku. Pokud je starší než množství času, zadaný v mezipaměti kopie prostředku, musí být prostředek znovu ověřeny, kontrolou obsahu na serveru. Pokud maximální stáří by umožnilo prostředek, který se použije po vypršení platnosti, není tato kritéria dodržení, pokud je zadaná také hodnota maximální typu prošlostí.  
  
### <a name="maximum-staleness"></a>Maximální typu Prošlostí  
 Kritérium zásady maximální typu prošlostí Určuje dobu, po vypršení platnosti obsahu je možné v mezipaměti kopie prostředku. Toto je pouze kritérium zásady mezipaměti, která umožňuje prostředků, který se má použít po vypršení jejich platnosti.  
  
### <a name="minimum-freshness"></a>Minimální aktuálnosti  
 Kritérium minimální aktuálnosti zásady určuje dobu, před vypršení platnosti obsahu je možné v mezipaměti kopie prostředku. Tato zásada nemá vliv způsobit položky mezipaměti vyprší před vypršením platnosti; proto aktuálnosti minimální a maximální typu prošlostí nastavení se vzájemně vylučují.  
  
## <a name="cache-synchronization-date"></a>Datum synchronizace mezipaměti  
 Kritérium mezipaměti synchronizace data zásad určuje, kdy musí být uložené v mezipaměti kopii prostředku znovu ověřeny kontrolou obsahu na serveru. Pokud došlo ke změně obsahu vzhledem k tomu, že položka se ukládá do mezipaměti, je načíst ze serveru, uložené v mezipaměti a vrátí aplikaci. Pokud obsah se nezměnila, její časové razítko je aktualizovat a aplikace získá obsah v mezipaměti.  
  
 Datum mezipaměti synchronizace můžete zadat absolutní datum, kdy musí být znovu obsah uložený v mezipaměti ověřeny. Pokud položku vytvoří nová mezipaměť byl poslední znovu ověřeny před datem mezipaměti synchronizace, dojde k stále opětovné ověření se serverem. Pokud byl znovu položky mezipaměti ověřeny po datu synchronizace mezipaměti a neexistují žádné další aktuálnosti nebo požadavky opětovné ověření serveru, které zneplatnit položka v mezipaměti, použije se položku z mezipaměti. Pokud datum synchronizace mezipaměti je nastavené na datum v budoucnosti, položka je znovu ověřeny pokaždé, když se požaduje dokud předá datum synchronizace mezipaměti.  
  
 Následující témata obsahují informace o dopadech kombinace kritéria zásad založené na čase mezipaměti:  
  
-   [Interakce zásad mezipaměti – maximální stáří a maximální neaktuálnost](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)  
  
-   [Interakce zásad mezipaměti – minimální stáří a minimální novost](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-minimum-freshness.md)  
  
## <a name="see-also"></a>Viz také  
 [Správa mezipaměti pro síťové aplikace](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Zásady mezipaměti](../../../docs/framework/network-programming/cache-policy.md)  
 [Zásady mezipaměti na základě místa](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [Konfigurace mezipaměti v síťových aplikacích](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [\<requestCaching – > elementu (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
