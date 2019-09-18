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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047129"
---
# <a name="time-based-cache-policies"></a>Zásady mezipaměti na základě času
Zásady mezipaměti založené na čase definují aktuálnost záznamů uložených v mezipaměti s využitím času, kdy byl prostředek načten, a záhlavími vrácenými zdrojem a aktuálním časem. Při nastavování zásad mezipaměti založeného na čase můžete buď použít <xref:System.Net.Cache.HttpRequestCacheLevel.Default> zásadu založenou na čase, nebo vytvořit vlastní zásadu založenou na čase. Když použijete výchozí zásadu založenou na čase pro prostředky získané pomocí protokolu HTTP (Hypertext Transfer Protocol), je přesné chování mezipaměti určeno hlavičkami zahrnutými v odpovědi v mezipaměti a chováním uvedeným v oddílech 13 a 14 v dokumentu RFC 2616. k dispozici na webu [IETF (Internet Engineering Task Force)](https://www.ietf.org/) . Příklad kódu, který ukazuje nastavení výchozích zásad založených na čase pro prostředky http, naleznete v [tématu How to: Nastavte výchozí zásady mezipaměti založené na čase pro aplikaci](how-to-set-the-default-time-based-cache-policy-for-an-application.md). Příklady kódu, které ukazují vytváření a používání zásad mezipaměti, najdete v tématu [Konfigurace ukládání do mezipaměti v síťových aplikacích](configuring-caching-in-network-applications.md).  
  
## <a name="criteria-to-determine-freshness-of-cached-entries"></a>Kritéria pro určení aktuálnosti položek v mezipaměti  
 Chcete-li přizpůsobit zásady mezipaměti založené na čase, můžete určit, že se má použít jedno nebo více následujících kritérií k určení aktuálnosti položek v mezipaměti:  
  
- Maximální stáří  
  
- Maximální neaktuálnost  
  
- Minimální aktuálnost  
  
- Datum synchronizace mezipaměti  
  
> [!NOTE]
> Použití výchozích zásad mezipaměti na základě času by nemělo být zaměněno s nastavením výchozích zásad mezipaměti pro vaši aplikaci. Výchozí zásada založená na čase je specifická zásada, kterou je možné použít na úrovni žádosti nebo aplikace. Výchozí zásada mezipaměti pro vaši aplikaci je zásada (založená na umístění nebo na základě času), která se projeví, když není u žádosti nastavena žádná zásada. Podrobnosti o nastavení výchozích zásad mezipaměti pro vaši aplikaci najdete v tématu <xref:System.Net.WebRequest.DefaultCachePolicy%2A>.  
  
### <a name="maximum-age"></a>Maximální stáří  
 Kritérium maximální věkové zásady určuje dobu, po kterou lze použít kopii prostředku uloženou v mezipaměti. Pokud je kopie tohoto prostředku v mezipaměti starší než zadaná doba, je nutné znovu ověřit prostředek tím, že ho zkontrolujete proti obsahu na serveru. Pokud maximální stáří umožní, aby se prostředek používal po vypršení platnosti, tato kritéria se neuplatňují, pokud není zadaná taky maximální hodnota zastaralosti.  
  
### <a name="maximum-staleness"></a>Maximální neaktuálnost  
 Kritérium maximální zásady zastaralosti určuje dobu, po jejíž uplynutí je možné použít kopii prostředku uloženou v mezipaměti. Toto je jediné kritérium zásady mezipaměti, které umožňuje, aby se prostředky používaly po vypršení platnosti.  
  
### <a name="minimum-freshness"></a>Minimální aktuálnost  
 Minimální zásada aktuálnosti určuje dobu, po jejímž uplynutí bude možné použít kopii prostředku uloženou v mezipaměti. Tato zásada má vliv na to, že vyprší platnost položky mezipaměti před datem vypršení platnosti. minimální aktuálnost a maximální aktuálnost nastavení se proto vzájemně vylučují.  
  
## <a name="cache-synchronization-date"></a>Datum synchronizace mezipaměti  
 Kritérium zásad pro datum synchronizace mezipaměti určuje, kdy je nutné znovu ověřit kopii prostředku v mezipaměti, a to tak, že zkontrolujete jeho obsah na serveru. Pokud se obsah změnil od chvíle, kdy byla položka uložena do mezipaměti, je načtena ze serveru, uložena v mezipaměti a vrácena do aplikace. Pokud se obsah nezměnil, je jeho časové razítko aktualizováno a aplikace získá obsah uložený v mezipaměti.  
  
 Datum synchronizace mezipaměti umožňuje zadat absolutní datum, kdy je nutné znovu ověřit obsah uložený v mezipaměti. Pokud byla poslední opětovně ověřena položka nové mezipaměti před datem synchronizace mezipaměti, dojde k opětovnému ověření se serverem. Pokud byla položka mezipaměti znovu ověřena po datu synchronizace mezipaměti a nejsou k dispozici žádné další požadavky na novou aktualizaci nebo revalidaci serveru, které zruší platnost položky uložené v mezipaměti, je položka z mezipaměti použita. Pokud je datum synchronizace mezipaměti nastaveno na datum v budoucnosti, bude položka znovu ověřena pokaždé, když je vyžádána, až do chvíle, kdy data synchronizace mezipaměti projde.  
  
 V následujících tématech najdete informace o účincích kombinování kritérií zásad mezipaměti na základě času:  
  
- [Interakce zásad mezipaměti – maximální stáří a maximální neaktuálnost](cache-policy-interaction-maximum-age-and-maximum-staleness.md)  
  
- [Interakce zásad mezipaměti – minimální stáří a minimální novost](cache-policy-interaction-maximum-age-and-minimum-freshness.md)  
  
## <a name="see-also"></a>Viz také:

- [Správa mezipaměti pro síťové aplikace](cache-management-for-network-applications.md)
- [Zásady mezipaměti](cache-policy.md)
- [Zásady mezipaměti na základě místa](location-based-cache-policies.md)
- [Konfigurace mezipaměti v síťových aplikacích](configuring-caching-in-network-applications.md)
- [\<requestCaching – element > (nastavení sítě)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
