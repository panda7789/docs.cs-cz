---
title: "Zásady založené na čase mezipaměti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 1d4cfa67d7fba06140838e04bdbff71102a2a303
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="time-based-cache-policies"></a><span data-ttu-id="b78e1-102">Zásady založené na čase mezipaměti</span><span class="sxs-lookup"><span data-stu-id="b78e1-102">Time-Based Cache Policies</span></span>
<span data-ttu-id="b78e1-103">Zásady založené na čase mezipaměti definuje aktuálnosti položek v mezipaměti pomocí čas prostředku byl načteny, se k prostředku, vrácený hlavičky a aktuální čas.</span><span class="sxs-lookup"><span data-stu-id="b78e1-103">A time-based cache policy defines the freshness of cached entries using the time the resource was retrieved, the headers returned with the resource, and the current time.</span></span> <span data-ttu-id="b78e1-104">Při nastavení zásad založené na čase mezipaměti, můžete použít <xref:System.Net.Cache.HttpRequestCacheLevel.Default> zásady založené na čase nebo vytvořte vlastní zásadu založené na čase.</span><span class="sxs-lookup"><span data-stu-id="b78e1-104">When setting a time-based cache policy, you can either use the <xref:System.Net.Cache.HttpRequestCacheLevel.Default> time-based policy or create a customized time-based policy.</span></span> <span data-ttu-id="b78e1-105">Při použití výchozí zásady založené na čase prostředků získaných pomocí protokolu HTTP (Hypertext Transfer), přesný mezipaměti chování je určen podle hlavičky zahrnuty v odpovědi v mezipaměti a chování zadané v části 13 a 14 dokumentu RFC 2616 k dispozici na [http://www.ietf.org](http://www.ietf.org/). Příklad kódu, který ukazuje nastavení zásad založené na čase výchozí pro HTTP prostředky, najdete v části [postupy: nastavení zásady ukládání do mezipaměti Default Time-Based pro aplikaci](../../../docs/framework/network-programming/how-to-set-the-default-time-based-cache-policy-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="b78e1-105">When using the default time-based policy for resources obtained using Hypertext Transfer Protocol (HTTP), the exact cache behavior is determined by the headers included in the cached response and by the behaviors specified in sections 13 and 14 of RFC 2616, available at [http://www.ietf.org](http://www.ietf.org/). For a code example that demonstrates setting the default time-based policy for HTTP resources, see [How to: Set the Default Time-Based Cache Policy for an Application](../../../docs/framework/network-programming/how-to-set-the-default-time-based-cache-policy-for-an-application.md).</span></span> <span data-ttu-id="b78e1-106">Příklady kódu, které ukazují, vytvoření a použití zásady mezipaměti najdete v tématu [konfiguraci ukládání do mezipaměti v síťových aplikací](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md).</span><span class="sxs-lookup"><span data-stu-id="b78e1-106">For code examples that demonstrate creating and using cache policies, see [Configuring Caching in Network Applications](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md).</span></span>  
  
## <a name="criteria-to-determine-freshness-of-cached-entries"></a><span data-ttu-id="b78e1-107">Kritéria k určení aktuálnosti položek v mezipaměti</span><span class="sxs-lookup"><span data-stu-id="b78e1-107">Criteria to Determine Freshness of Cached Entries</span></span>  
 <span data-ttu-id="b78e1-108">Chcete-li přizpůsobit zásady založené na čase mezipaměti, můžete určit, že jedna nebo více z následujících kritérií použije k určení aktuálnosti položek v mezipaměti:</span><span class="sxs-lookup"><span data-stu-id="b78e1-108">To customize a time-based cache policy, you can specify that one or more of the following criteria be used to determine the freshness of cached entries:</span></span>  
  
-   <span data-ttu-id="b78e1-109">Maximální stáří</span><span class="sxs-lookup"><span data-stu-id="b78e1-109">Maximum age</span></span>  
  
-   <span data-ttu-id="b78e1-110">Maximální typu prošlostí</span><span class="sxs-lookup"><span data-stu-id="b78e1-110">Maximum staleness</span></span>  
  
-   <span data-ttu-id="b78e1-111">Minimální aktuálnosti</span><span class="sxs-lookup"><span data-stu-id="b78e1-111">Minimum freshness</span></span>  
  
-   <span data-ttu-id="b78e1-112">Datum synchronizace mezipaměti</span><span class="sxs-lookup"><span data-stu-id="b78e1-112">Cache synchronization date</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b78e1-113">Pomocí zásady ukládání do mezipaměti založené na čase výchozí Nezaměňujte za nastavení výchozí zásady mezipaměti pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b78e1-113">Using the default time-based cache policy should not be confused with setting a default cache policy for your application.</span></span> <span data-ttu-id="b78e1-114">Výchozí zásady založené na čase je konkrétní zásadu, která lze použít na úrovni požadavku nebo aplikace.</span><span class="sxs-lookup"><span data-stu-id="b78e1-114">The default time-based policy is a specific policy that can be used at the request or application level.</span></span> <span data-ttu-id="b78e1-115">Výchozí zásady mezipaměti pro vaši aplikaci je zásada (na základě polohy nebo založené na čase), která se projeví při žádná zásada nastavená na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="b78e1-115">The default cache policy for your application is a policy (location-based or time-based) that takes effect when no policy is set on a request.</span></span> <span data-ttu-id="b78e1-116">Podrobnosti o nastavení výchozí zásady mezipaměti pro vaši aplikaci najdete v tématu <xref:System.Net.WebRequest.DefaultCachePolicy%2A>.</span><span class="sxs-lookup"><span data-stu-id="b78e1-116">For details on setting a default cache policy for your application, see <xref:System.Net.WebRequest.DefaultCachePolicy%2A>.</span></span>  
  
### <a name="maximum-age"></a><span data-ttu-id="b78e1-117">Maximální stáří</span><span class="sxs-lookup"><span data-stu-id="b78e1-117">Maximum Age</span></span>  
 <span data-ttu-id="b78e1-118">Maximální stáří zásad kritérium určuje množství času, které lze použít v mezipaměti kopie prostředku.</span><span class="sxs-lookup"><span data-stu-id="b78e1-118">The maximum age policy criterion specifies the amount of time a cached copy of a resource can be used.</span></span> <span data-ttu-id="b78e1-119">Pokud je starší než množství času, zadaný v mezipaměti kopie prostředku, musí být prostředek znovu ověřeny, kontrolou obsahu na serveru.</span><span class="sxs-lookup"><span data-stu-id="b78e1-119">If the cached copy of the resource is older than the amount of time specified, the resource must be revalidated by checking it against the content on the server.</span></span> <span data-ttu-id="b78e1-120">Pokud maximální stáří by umožnilo prostředek, který se použije po vypršení platnosti, není tato kritéria dodržení, pokud je zadaná také hodnota maximální typu prošlostí.</span><span class="sxs-lookup"><span data-stu-id="b78e1-120">If the maximum age would allow the resource to be used after it expires, this criteria is not honored unless a maximum staleness value is also specified.</span></span>  
  
### <a name="maximum-staleness"></a><span data-ttu-id="b78e1-121">Maximální typu Prošlostí</span><span class="sxs-lookup"><span data-stu-id="b78e1-121">Maximum Staleness</span></span>  
 <span data-ttu-id="b78e1-122">Kritérium zásady maximální typu prošlostí Určuje dobu, po vypršení platnosti obsahu je možné v mezipaměti kopie prostředku.</span><span class="sxs-lookup"><span data-stu-id="b78e1-122">The maximum staleness policy criterion specifies the length of time after content expiration that the cached copy of the resource can be used.</span></span> <span data-ttu-id="b78e1-123">Toto je pouze kritérium zásady mezipaměti, která umožňuje prostředků, který se má použít po vypršení jejich platnosti.</span><span class="sxs-lookup"><span data-stu-id="b78e1-123">This is the only cache policy criterion that permits resources to be used after they have expired.</span></span>  
  
### <a name="minimum-freshness"></a><span data-ttu-id="b78e1-124">Minimální aktuálnosti</span><span class="sxs-lookup"><span data-stu-id="b78e1-124">Minimum Freshness</span></span>  
 <span data-ttu-id="b78e1-125">Kritérium minimální aktuálnosti zásady určuje dobu, před vypršení platnosti obsahu je možné v mezipaměti kopie prostředku.</span><span class="sxs-lookup"><span data-stu-id="b78e1-125">The minimum freshness policy criterion specifies the length of time before content expiration that the cached copy of the resource can be used.</span></span> <span data-ttu-id="b78e1-126">Tato zásada nemá vliv způsobit položky mezipaměti vyprší před vypršením platnosti; proto aktuálnosti minimální a maximální typu prošlostí nastavení se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="b78e1-126">This policy has the effect of causing a cache entry to expire before its expiration date; therefore, the minimum freshness and maximum staleness settings are mutually exclusive.</span></span>  
  
## <a name="cache-synchronization-date"></a><span data-ttu-id="b78e1-127">Datum synchronizace mezipaměti</span><span class="sxs-lookup"><span data-stu-id="b78e1-127">Cache Synchronization Date</span></span>  
 <span data-ttu-id="b78e1-128">Kritérium mezipaměti synchronizace data zásad určuje, kdy musí být uložené v mezipaměti kopii prostředku znovu ověřeny kontrolou obsahu na serveru.</span><span class="sxs-lookup"><span data-stu-id="b78e1-128">The cache synchronization date policy criterion determines when a cached copy of a resource must be revalidated by checking it against the content on the server.</span></span> <span data-ttu-id="b78e1-129">Pokud došlo ke změně obsahu vzhledem k tomu, že položka se ukládá do mezipaměti, je načíst ze serveru, uložené v mezipaměti a vrátí aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b78e1-129">If the content has changed since the item was cached, it is retrieved from the server, stored in the cache, and returned to the application.</span></span> <span data-ttu-id="b78e1-130">Pokud obsah se nezměnila, její časové razítko je aktualizovat a aplikace získá obsah v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="b78e1-130">If the content has not changed, its timestamp is updated and the application gets the cached content.</span></span>  
  
 <span data-ttu-id="b78e1-131">Datum mezipaměti synchronizace můžete zadat absolutní datum, kdy musí být znovu obsah uložený v mezipaměti ověřeny.</span><span class="sxs-lookup"><span data-stu-id="b78e1-131">The cache synchronization date allows you to specify an absolute date when cached contents must be revalidated.</span></span> <span data-ttu-id="b78e1-132">Pokud položku vytvoří nová mezipaměť byl poslední znovu ověřeny před datem mezipaměti synchronizace, dojde k stále opětovné ověření se serverem.</span><span class="sxs-lookup"><span data-stu-id="b78e1-132">If a fresh cache entry was last revalidated prior to the cache synchronization date, revalidation with the server still occurs.</span></span> <span data-ttu-id="b78e1-133">Pokud byl znovu položky mezipaměti ověřeny po datu synchronizace mezipaměti a neexistují žádné další aktuálnosti nebo požadavky opětovné ověření serveru, které zneplatnit položka v mezipaměti, použije se položku z mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="b78e1-133">If the cache entry was revalidated after the cache synchronization date and there are no additional freshness or server revalidation requirements that invalidate the cached entry, the entry from the cache is used.</span></span> <span data-ttu-id="b78e1-134">Pokud datum synchronizace mezipaměti je nastavené na datum v budoucnosti, položka je znovu ověřeny pokaždé, když se požaduje dokud předá datum synchronizace mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="b78e1-134">If the cache synchronization date is set to a future date, the entry is revalidated every time it is requested, until the cache synchronization date passes.</span></span>  
  
 <span data-ttu-id="b78e1-135">Následující témata obsahují informace o dopadech kombinace kritéria zásad založené na čase mezipaměti:</span><span class="sxs-lookup"><span data-stu-id="b78e1-135">The following topics provide information about the effects of combining time-based cache policy criteria:</span></span>  
  
-   [<span data-ttu-id="b78e1-136">Interakce zásad do mezipaměti – maximální stáří a maximální typu Prošlostí</span><span class="sxs-lookup"><span data-stu-id="b78e1-136">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)  
  
-   [<span data-ttu-id="b78e1-137">Interakce zásad do mezipaměti – maximální stáří a minimální aktuálnosti</span><span class="sxs-lookup"><span data-stu-id="b78e1-137">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-minimum-freshness.md)  
  
## <a name="see-also"></a><span data-ttu-id="b78e1-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="b78e1-138">See Also</span></span>  
 [<span data-ttu-id="b78e1-139">Správa mezipaměti pro síťové aplikace</span><span class="sxs-lookup"><span data-stu-id="b78e1-139">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="b78e1-140">Zásady mezipaměti</span><span class="sxs-lookup"><span data-stu-id="b78e1-140">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 [<span data-ttu-id="b78e1-141">Na základě umístění mezipaměti zásad</span><span class="sxs-lookup"><span data-stu-id="b78e1-141">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [<span data-ttu-id="b78e1-142">Konfigurace ukládání do mezipaměti v síťových aplikací</span><span class="sxs-lookup"><span data-stu-id="b78e1-142">Configuring Caching in Network Applications</span></span>](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [<span data-ttu-id="b78e1-143">\<requestCaching – > elementu (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="b78e1-143">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
