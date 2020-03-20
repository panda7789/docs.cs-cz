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
ms.openlocfilehash: 0edde8e716d5ce3b1444e994234def5835341475
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047129"
---
# <a name="time-based-cache-policies"></a>Zásady mezipaměti na základě času
Zásada mezipaměti založená na čase definuje aktuálnost položek uložených v mezipaměti pomocí času, kdy byl prostředek načten, záhlaví vrácená s prostředkem a aktuální čas. Při nastavování zásad mezipaměti založených na <xref:System.Net.Cache.HttpRequestCacheLevel.Default> čase můžete buď použít zásady založené na čase, nebo vytvořit vlastní zásady založené na čase. Při použití výchozí zásady založené na čase pro prostředky získané pomocí protokolu HTTP (HYPERTEXT Transfer Protocol) je přesné chování mezipaměti určeno záhlavími obsaženými v odpovědi uložené v mezipaměti a chováním uvedeným i v oddílech 13 a 14 protokolu RFC 2616, které jsou k dispozici na webu [IETF (Internet Engineering Task Force).](https://www.ietf.org/) Příklad kódu, který ukazuje nastavení výchozí zásady založené na čase pro prostředky HTTP, naleznete v [tématu Postup: Nastavení výchozízásady mezipaměti založené na čase pro aplikaci](how-to-set-the-default-time-based-cache-policy-for-an-application.md). Příklady kódu, které ukazují vytváření a používání zásad mezipaměti, naleznete [v tématu Konfigurace ukládání do mezipaměti v síťových aplikacích](configuring-caching-in-network-applications.md).  
  
## <a name="criteria-to-determine-freshness-of-cached-entries"></a>Kritéria pro určení čerstvosti položek uložených v mezipaměti  
 Chcete-li přizpůsobit zásady mezipaměti založené na čase, můžete určit, že k určení čerstvosti položek uložených v mezipaměti se použije jedno nebo více z následujících kritérií:  
  
- Maximální věk  
  
- Maximální neaktuálnost  
  
- Minimální čerstvost  
  
- Datum synchronizace mezipaměti  
  
> [!NOTE]
> Použití výchozí zásady mezipaměti založené na čase by nemělo být zaměňováno s nastavením výchozí zásady mezipaměti pro vaši aplikaci. Výchozí zásady založené na čase je konkrétní zásady, které lze použít na úrovni požadavku nebo aplikace. Výchozí zásady mezipaměti pro vaši aplikaci jsou zásady (založené na umístění nebo na základě času), které se projeví, když není nastavena žádná zásada na základě požadavku. Podrobnosti o nastavení výchozí zásady mezipaměti pro vaši aplikaci naleznete v tématu <xref:System.Net.WebRequest.DefaultCachePolicy%2A>.  
  
### <a name="maximum-age"></a>Maximální věk  
 Kritérium zásad maximálního věku určuje dobu, po kterou lze použít kopii prostředku uloženou v mezipaměti. Pokud je kopie prostředku uložená v mezipaměti starší než zadaná doba, musí být prostředek znovu ověřen a zkontrolován proti obsahu na serveru. Pokud maximální stáří by umožnilo prostředek, který má být použit po vypršení jeho platnosti, tato kritéria není dodržena, pokud není zadána také maximální hodnota neaktuálnosti.  
  
### <a name="maximum-staleness"></a>Maximální neaktuálnost  
 Kritérium zásad maximální neaktuálnosti určuje dobu po vypršení platnosti obsahu, po kterou lze použít kopii prostředku uloženou v mezipaměti. Toto je jediné kritérium zásad mezipaměti, které umožňuje použití prostředků po vypršení jejich platnosti.  
  
### <a name="minimum-freshness"></a>Minimální čerstvost  
 Kritérium zásad minimální čerstvosti určuje dobu před vypršením platnosti obsahu, po kterou lze použít kopii prostředku uloženou v mezipaměti. Tato zásada má za následek příčinou vypršení platnosti položky mezipaměti před datem vypršení platnosti. proto se vzájemně vylučují minimální čerstvost a nastavení maximální neaktuálnosti.  
  
## <a name="cache-synchronization-date"></a>Datum synchronizace mezipaměti  
 Kritérium zásady data synchronizace mezipaměti určuje, kdy musí být kopie prostředku uložená v mezipaměti znovu ověřena kontrolou obsahu na serveru. Pokud se obsah od uložení položky do mezipaměti změnil, je načten ze serveru, uložen v mezipaměti a vrácen do aplikace. Pokud se obsah nezměnil, jeho časové razítko se aktualizuje a aplikace získá obsah uložený v mezipaměti.  
  
 Datum synchronizace mezipaměti umožňuje určit absolutní datum, kdy musí být obsah uložený v mezipaměti znovu ověřen. Pokud byla nová položka mezipaměti naposledy znovu ověřena před datem synchronizace mezipaměti, dojde k opětovnému ověření se serverem. Pokud byla položka mezipaměti po datu synchronizace mezipaměti znovu ověřena a neexistují žádné další požadavky na čerstvost nebo opětovné ověření serveru, které by zneplatňovaly položku uloženou v mezipaměti, bude použita položka z mezipaměti. Pokud je datum synchronizace mezipaměti nastaveno na budoucí datum, bude položka při každém požadavku znovu ověřena, dokud datum synchronizace mezipaměti neprojde.  
  
 Následující témata obsahují informace o účincích kombinování kritérií zásad mezipaměti založených na čase:  
  
- [Interakce zásad mezipaměti – maximální stáří a maximální neaktuálnost](cache-policy-interaction-maximum-age-and-maximum-staleness.md)  
  
- [Interakce zásad mezipaměti – minimální stáří a minimální novost](cache-policy-interaction-maximum-age-and-minimum-freshness.md)  
  
## <a name="see-also"></a>Viz také

- [Správa mezipaměti pro síťové aplikace](cache-management-for-network-applications.md)
- [Zásady mezipaměti](cache-policy.md)
- [Zásady mezipaměti na základě místa](location-based-cache-policies.md)
- [Konfigurace ukládání do mezipaměti v síťových aplikacích](configuring-caching-in-network-applications.md)
- [\<requestCaching> Element (Nastavení sítě)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
