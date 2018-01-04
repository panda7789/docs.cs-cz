---
title: "Interakce zásad do mezipaměti – maximální stáří a maximální typu Prošlostí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maximum staleness
- freshness of cached resources
- time, cached resources
- maximum age policy
- staleness of cached resources
- age of cached resources
ms.assetid: 7f775925-89a1-4956-ba90-c869c1749a94
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 2fc28f120b76e51cd285f9b7d6a446f4835113a7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cache-policy-interactionmaximum-age-and-maximum-staleness"></a><span data-ttu-id="04a39-102">Interakce zásad do mezipaměti – maximální stáří a maximální typu Prošlostí</span><span class="sxs-lookup"><span data-stu-id="04a39-102">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>
<span data-ttu-id="04a39-103">K zajištění, že nejčerstvější obsah se vrátí do klientské aplikace, výsledkem interakce klienta mezipaměti zásad a server opětovné ověření požadavků vždy nejvíce konzervativní zásady ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="04a39-103">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="04a39-104">V příkladech v tomto tématu ilustrují zásady ukládání do mezipaměti pro prostředek, který se uloží do mezipaměti na 1. ledna a jeho platnost vyprší v lednu 4.</span><span class="sxs-lookup"><span data-stu-id="04a39-104">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="04a39-105">V následujících příkladech, hodnota maximální typu prošlostí (`maxStale`) se používá ve spojení s maximální stáří (`maxAge`):</span><span class="sxs-lookup"><span data-stu-id="04a39-105">In the following examples, the maximum staleness value (`maxStale`) is used in conjunction with a maximum age (`maxAge`):</span></span>  
  
-   <span data-ttu-id="04a39-106">Pokud je nastaví zásady ukládání do mezipaměti `maxAge` = 5 dní a neurčuje `maxStale` hodnoty, podle `maxAge` hodnota, obsah je až 6 leden použitelné.</span><span class="sxs-lookup"><span data-stu-id="04a39-106">If the cache policy sets `maxAge` = 5 days and does not specify a `maxStale` value, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="04a39-107">V souladu s požadavky opětovné ověření serveru, ale obsah vyprší na leden 4.</span><span class="sxs-lookup"><span data-stu-id="04a39-107">However, according to the server's revalidation requirements, the content expires on January 4.</span></span> <span data-ttu-id="04a39-108">Protože datum vypršení platnosti obsahu je více konzervativní (dříve), pak má přednost před `maxAge` zásad.</span><span class="sxs-lookup"><span data-stu-id="04a39-108">Because the content expiration date is more conservative (sooner), it takes precedence over the `maxAge` policy.</span></span> <span data-ttu-id="04a39-109">Obsah, tedy vyprší na leden 4 a musí být obnoveny, i když nedosáhla své maximální stáří.</span><span class="sxs-lookup"><span data-stu-id="04a39-109">Therefore, the content expires on January 4 and must be revalidated even though its maximum age has not been reached.</span></span>  
  
-   <span data-ttu-id="04a39-110">Pokud je nastaví zásady ukládání do mezipaměti `maxAge` = 5 dní a `maxStale` = 3 dny, podle požadavků `maxAge` hodnota, obsah je až 6 leden použitelné.</span><span class="sxs-lookup"><span data-stu-id="04a39-110">If the cache policy sets `maxAge` = 5 days and `maxStale` = 3 days, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="04a39-111">Podle požadavků `maxStale` hodnota, obsah je až 7 leden použitelné.</span><span class="sxs-lookup"><span data-stu-id="04a39-111">According to the `maxStale` value, the content is usable until January 7.</span></span> <span data-ttu-id="04a39-112">Proto získá obsahu obnoveny v lednu 6.</span><span class="sxs-lookup"><span data-stu-id="04a39-112">Therefore, the content gets revalidated on January 6.</span></span>  
  
-   <span data-ttu-id="04a39-113">Pokud je nastaví zásady ukládání do mezipaměti `maxAge` = 5 dní a `maxStale` = 1 den, podle požadavků `maxAge` hodnota, obsah je až 6 leden použitelné.</span><span class="sxs-lookup"><span data-stu-id="04a39-113">If the cache policy sets `maxAge` = 5 days and `maxStale` = 1 day, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="04a39-114">Podle požadavků `maxStale` hodnota, obsah je až 5 leden použitelné.</span><span class="sxs-lookup"><span data-stu-id="04a39-114">According to the `maxStale` value, the content is usable until January 5.</span></span> <span data-ttu-id="04a39-115">Proto získá obsahu obnoveny v lednu 5.</span><span class="sxs-lookup"><span data-stu-id="04a39-115">Therefore, the content gets revalidated on January 5.</span></span>  
  
 <span data-ttu-id="04a39-116">Když maximální stáří je menší než datum vypršení platnosti obsahu, mají vždycky přednost více konzervativní chování ukládání do mezipaměti a hodnota typu maximální prošlostí nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="04a39-116">When the maximum age is less than the content expiration date, the more conservative caching behavior always prevails and the maximum staleness value has no effect.</span></span> <span data-ttu-id="04a39-117">Následující příklady ilustrují účinek nastavení maximální typu prošlostí (`maxStale`) hodnotu v případě maximální stáří (`maxAge`) je dosažen předtím, než vyprší platnost obsahu:</span><span class="sxs-lookup"><span data-stu-id="04a39-117">The following examples illustrate the effect of setting a maximum staleness (`maxStale`) value when the maximum age (`maxAge`) is reached before the content expires:</span></span>  
  
-   <span data-ttu-id="04a39-118">Pokud je nastaví zásady ukládání do mezipaměti `maxAge` = 1 den a neurčuje hodnotu `maxStale` hodnotu, obsah je znovu ověřeny v lednu 2, i když nevypršela platnost.</span><span class="sxs-lookup"><span data-stu-id="04a39-118">If the cache policy sets `maxAge` = 1 day and does not specify a value for `maxStale` value, the content is revalidated on January 2 even though it has not expired.</span></span>  
  
-   <span data-ttu-id="04a39-119">Pokud je nastaví zásady ukládání do mezipaměti `maxAge` = 1 den a `maxStale` = 3 dny, obsah je znovu ověřeny v lednu 2 k vynucení více konzervativní nastavení zásad.</span><span class="sxs-lookup"><span data-stu-id="04a39-119">If the cache policy sets `maxAge` = 1 day and `maxStale` = 3 days, the content is revalidated on January 2 to enforce the more conservative policy setting.</span></span>  
  
-   <span data-ttu-id="04a39-120">Pokud je nastaví zásady ukládání do mezipaměti `maxAge` = 1 den a `maxStale` = 1 den, obsah je znovu ověřeny v lednu 2.</span><span class="sxs-lookup"><span data-stu-id="04a39-120">If the cache policy sets `maxAge` = 1 day and `maxStale` = 1 day, the content is revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04a39-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="04a39-121">See Also</span></span>  
 [<span data-ttu-id="04a39-122">Správa mezipaměti pro síťové aplikace</span><span class="sxs-lookup"><span data-stu-id="04a39-122">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="04a39-123">Zásady mezipaměti</span><span class="sxs-lookup"><span data-stu-id="04a39-123">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 [<span data-ttu-id="04a39-124">Zásady mezipaměti na základě místa</span><span class="sxs-lookup"><span data-stu-id="04a39-124">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [<span data-ttu-id="04a39-125">Zásady mezipaměti na základě času</span><span class="sxs-lookup"><span data-stu-id="04a39-125">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [<span data-ttu-id="04a39-126">Konfigurace mezipaměti v síťových aplikacích</span><span class="sxs-lookup"><span data-stu-id="04a39-126">Configuring Caching in Network Applications</span></span>](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [<span data-ttu-id="04a39-127">Interakce zásad mezipaměti – minimální stáří a minimální novost</span><span class="sxs-lookup"><span data-stu-id="04a39-127">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-minimum-freshness.md)
