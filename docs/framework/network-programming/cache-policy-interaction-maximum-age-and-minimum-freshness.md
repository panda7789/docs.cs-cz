---
title: "Interakce zásad do mezipaměti – maximální stáří a minimální aktuálnosti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time-based cache policies
- Revalidate policy
- cache [.NET Framework], time-based policies
- freshness of cached resources
- maximum age policy
- minimum freshness policy
- age of cached resources
ms.assetid: 6567d451-ecec-496c-95a3-a415b99ba52a
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 75729fc92c6a4bfa0f5ad73b8bbd4b28456f21e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a><span data-ttu-id="d79bc-102">Interakce zásad do mezipaměti – maximální stáří a minimální aktuálnosti</span><span class="sxs-lookup"><span data-stu-id="d79bc-102">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>
<span data-ttu-id="d79bc-103">K zajištění, že nejčerstvější obsah se vrátí do klientské aplikace, výsledkem interakce klienta mezipaměti zásad a server opětovné ověření požadavků vždy nejvíce konzervativní zásady ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="d79bc-103">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="d79bc-104">V příkladech v tomto tématu ilustrují zásady ukládání do mezipaměti pro prostředek, který se uloží do mezipaměti na 1. ledna a jeho platnost vyprší v lednu 4.</span><span class="sxs-lookup"><span data-stu-id="d79bc-104">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="d79bc-105">Následující příklady ilustrují zásady mezipaměti, která je výsledkem interakci maximální stáří (`maxAge`) a minimální aktuálnosti (`minFresh`) hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d79bc-105">The following examples illustrate the cache policy that results from the interaction of the maximum age (`maxAge`) and minimum freshness (`minFresh`) values.</span></span>  
  
-   <span data-ttu-id="d79bc-106">Pokud je nastaví zásady ukládání do mezipaměti `maxAge` = 2 dny a `minFresh` není zadaný obsah je znovu ověřeny na 3.</span><span class="sxs-lookup"><span data-stu-id="d79bc-106">If the cache policy sets `maxAge` = 2 days and `minFresh` is not specified, the content is revalidated on January 3.</span></span>  
  
-   <span data-ttu-id="d79bc-107">Pokud je nastaví zásady ukládání do mezipaměti `maxAge` = 2 dny a `minFresh` = 1 den, podle `maxAge`, obsah je novou dokud datum 3.</span><span class="sxs-lookup"><span data-stu-id="d79bc-107">If the cache policy sets `maxAge` = 2 days and `minFresh` = 1 day, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="d79bc-108">Podle `minFresh`, obsah je novou dokud datum 3.</span><span class="sxs-lookup"><span data-stu-id="d79bc-108">According to `minFresh`, the content is fresh until January 3.</span></span> <span data-ttu-id="d79bc-109">Proto musí být znovu obsah ověřeny na 3.</span><span class="sxs-lookup"><span data-stu-id="d79bc-109">Therefore, the content must be revalidated on January 3.</span></span>  
  
-   <span data-ttu-id="d79bc-110">Pokud je nastaví zásady ukládání do mezipaměti `maxAge` = 2 dny a `minFresh` = 2 dní, podle `maxAge`, obsah je novou dokud datum 3.</span><span class="sxs-lookup"><span data-stu-id="d79bc-110">If the cache policy sets `maxAge` = 2 days and `minFresh` = 2 days, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="d79bc-111">Podle `minFresh` dokud leden 2 je novou obsah.</span><span class="sxs-lookup"><span data-stu-id="d79bc-111">According to `minFresh` the content is fresh until January 2.</span></span> <span data-ttu-id="d79bc-112">Proto musí být znovu obsah ověřeny v lednu 2.</span><span class="sxs-lookup"><span data-stu-id="d79bc-112">Therefore, the content must be revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d79bc-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="d79bc-113">See Also</span></span>  
 [<span data-ttu-id="d79bc-114">Správa mezipaměti pro síťové aplikace</span><span class="sxs-lookup"><span data-stu-id="d79bc-114">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="d79bc-115">Zásady mezipaměti</span><span class="sxs-lookup"><span data-stu-id="d79bc-115">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 [<span data-ttu-id="d79bc-116">Na základě umístění mezipaměti zásad</span><span class="sxs-lookup"><span data-stu-id="d79bc-116">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [<span data-ttu-id="d79bc-117">Zásady založené na čase mezipaměti</span><span class="sxs-lookup"><span data-stu-id="d79bc-117">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [<span data-ttu-id="d79bc-118">Konfigurace ukládání do mezipaměti v síťových aplikací</span><span class="sxs-lookup"><span data-stu-id="d79bc-118">Configuring Caching in Network Applications</span></span>](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [<span data-ttu-id="d79bc-119">Interakce zásad do mezipaměti – maximální stáří a maximální typu Prošlostí</span><span class="sxs-lookup"><span data-stu-id="d79bc-119">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)
