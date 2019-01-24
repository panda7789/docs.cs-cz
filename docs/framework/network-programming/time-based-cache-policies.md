---
title: Zásady mezipaměti na základě času
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
ms.openlocfilehash: fa99806510bac8102478cc21e0782067f7bdff86
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54497413"
---
# <a name="time-based-cache-policies"></a>Zásady mezipaměti na základě času
Zásady mezipaměti na základě času definuje aktuálnosti položek v mezipaměti pomocí čas, kdy byla načtena prostředek, vrátí hlavičky prostředku a aktuální čas. Při nastavování zásad mezipaměti na základě času, můžete použít <xref:System.Net.Cache.HttpRequestCacheLevel.Default> podle času zásady nebo vytvořte vlastní zásadu podle času. Při použití výchozí zásady na základě času pro prostředky získané s použitím protokolu HTTP (Hypertext Transfer), chování přesné mezipaměti se určuje podle záhlaví zahrnutá v odpovědi v mezipaměti a chování zadané v části 13 a 14 dokumentu RFC 2616 k dispozici na [Engineering Task Force IETF (Internet)](https://www.ietf.org/) webu. Příklad kódu, který ukazuje nastavení výchozí zásady podle času pro HTTP prostředky, najdete v části [jak: Nastavení výchozích zásad mezipaměti na základě času pro aplikaci](../../../docs/framework/network-programming/how-to-set-the-default-time-based-cache-policy-for-an-application.md). Příklady kódu, které ukazují, vytváření a používání mezipaměti zásad, najdete v části [konfiguraci ukládání do mezipaměti v síťových aplikacích](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md).  
  
## <a name="criteria-to-determine-freshness-of-cached-entries"></a>Kritéria k určení aktuálnosti položek v mezipaměti  
 Přizpůsobení zásad mezipaměti na základě času, můžete určit, že jedna nebo více z následujících kritérií použít k určení aktuálnosti položek v mezipaměti:  
  
-   Maximální stáří  
  
-   Maximální neaktuálnost  
  
-   Minimální novost  
  
-   Datum synchronizace mezipaměti  
  
> [!NOTE]
>  Pomocí výchozích zásad mezipaměti na základě času, neměly by být zaměňovány s nastavení zásad mezipaměti výchozí pro vaši aplikaci. Výchozí zásady podle času je konkrétní zásady, které lze použít na úrovni požadavku nebo aplikace. Zásady ukládání do mezipaměti výchozí pro vaši aplikaci se zásady (založená na poloze nebo založená na čase), které se projeví, když nejsou nastavené žádné zásady na vyžádání. Podrobnosti o nastavení mezipaměti výchozí zásady pro vaši aplikaci najdete v tématu <xref:System.Net.WebRequest.DefaultCachePolicy%2A>.  
  
### <a name="maximum-age"></a>Maximální stáří  
 Kritérium zásady maximální stáří určuje množství času, které lze použít v mezipaměti kopii prostředku. Pokud je starší než určený čas v mezipaměti kopie prostředku, prostředek musí ověřit kontrolou obsahu na serveru. Pokud prostředek, který se použije po vypršení její platnosti by umožnilo maximální stáří, tato kritéria není podporována, pokud je zadána také hodnota maximální neaktuálnost.  
  
### <a name="maximum-staleness"></a>Maximální Neaktuálnost  
 Kritérium zásady maximální neaktuálnost Určuje dobu, po vypršení platnosti obsahu je možné v mezipaměti kopie prostředku. Toto je pouze kritéria zásad mezipaměti, která umožňuje prostředky pro použití platnost vypršela.  
  
### <a name="minimum-freshness"></a>Minimální novost  
 Kritérium zásady minimální novost Určuje dobu před vypršení platnosti obsahu je možné v mezipaměti kopie prostředku. Tato zásada má efekt sestavení položka v mezipaměti vyprší před vypršením platnosti; proto aktuálnosti minimální a maximální neaktuálnost nastavení se vzájemně vylučují.  
  
## <a name="cache-synchronization-date"></a>Datum synchronizace mezipaměti  
 Kritérium mezipaměti synchronizace data zásad určuje, kdy kopii prostředku v mezipaměti musí ověřit kontrolou obsahu na serveru. Pokud obsah změnila, protože položka byla uložena do mezipaměti, je načtení ze serveru, uložená v mezipaměti a vrátí aplikaci. Pokud nedošlo ke změně obsahu, se aktualizuje její časové razítko a aplikace obdrží obsah uložený v mezipaměti.  
  
 Synchronizace data mezipaměti umožňuje zadat absolutní datum, kdy se musí ověřit obsah uložený v mezipaměti. Pokud se vytvoří nová položka byla naposledy ověřit před datem synchronizaci mezipaměti, opětovné ověření se serverem i přesto dochází ke. Pokud položka mezipaměti byla znovu po datu synchronizaci mezipaměti a neexistují žádné další aktuálnosti nebo opětovné ověření požadavků na server, které zneplatňují položka uložená v mezipaměti, použije se položky z mezipaměti. Pokud datum synchronizaci mezipaměti je nastaveno na datum v budoucnosti, položka je ověřit pokaždé, když je požadovaný dokud synchronizace data mezipaměti předá.  
  
 Následující témata obsahují informace o dopadech kombinací kritérií zásad mezipaměti na základě času:  
  
-   [Interakce zásad mezipaměti – maximální stáří a maximální neaktuálnost](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)  
  
-   [Interakce zásad mezipaměti – minimální stáří a minimální novost](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-minimum-freshness.md)  
  
## <a name="see-also"></a>Viz také:
- [Správa mezipaměti pro síťové aplikace](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [Zásady mezipaměti](../../../docs/framework/network-programming/cache-policy.md)
- [Zásady mezipaměti na základě místa](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [Konfigurace mezipaměti v síťových aplikacích](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)
- [\<requestCaching – > – Element (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
